---
authors:
- "monotykamary"
date: "2024-11-14"
description: "An in-depth look at Dwarves' monthly Project Reports system - a lean, efficient system that transforms communication data into actionable intelligence for Operations teams. This case study explores how we orchestrate multiple data streams into comprehensive project insights while maintaining enterprise-grade security and cost efficiency."
tags:
- "data-engineering"
- "project-management"
- "case-study"
title: "Project reports system: a case study"
---

At Dwarves, we've developed a monthly Project Reports system - a lean, efficient system that transforms our communication data into actionable intelligence for our Operations team. This system orchestrates multiple data streams into comprehensive project insights while maintaining enterprise-grade security and cost efficiency.

## The need for orchestrated intelligence

Our engineering teams generate thousands of Discord messages daily across multiple projects. These messages contain critical technical discussions, architectural decisions, and implementation details that traditionally remained trapped in chat histories. While Discord excels as a communication platform, its real-time nature makes it challenging to track project progress against client requirements or ensure alignment between ongoing discussions and formal documentation.

This challenge sparked the development of our Project Reports system. Like a skilled conductor bringing order to complex musical pieces, our system coordinates multiple data streams into clear, actionable project intelligence

## The foundation: Data architecture

Our architecture follows a simple yet powerful approach to data management, emphasizing efficiency and practicality over complexity. We've built our system on three core principles:

1. **Lean Storage**: S3 serves as our primary data lake and warehouse, using Parquet and CSV files to optimize for both cost and performance
2. **Efficient Processing**: DuckDB and Polars provide high-performance querying without the overhead of traditional data warehouses
3. **Secure Access**: Modal orchestrates our serverless functions, ensuring secure and efficient data processing

### Data Flow Overview

```mermaid
graph TB
    subgraph Data Sources ["Data Sources (Raw)"]
        D1[Discord Messages]
        D2[Git Activity]
        D3[JIRA Tickets]
        D4[Google Docs]
        D5[Notion Pages]
        D6[...]
    end

    subgraph Data Engineering
        L1[Landing Zone - S3]
        G1[Gold Zone - S3]
        DQ[Data Quality Checks]
        
        D1 & D2 & D3 & D4 & D5 & D6 --> L1
        L1 --> DQ
        DQ --> G1
    end

    subgraph Platform Engineering
        API[REST API]
        SEC[Security Layer]
        MON[Monitoring]
        ORCH[Modal Orchestration]
        
        G1 --> API
        API --> SEC
        SEC --> MON
        MON --> ORCH
    end

    subgraph AI Engineering
        LLM[LLM Processing]
        AGG[Aggregations]
        SUM[Summarization]
        
        ORCH --> LLM
        LLM --> AGG
        AGG --> SUM
    end

    subgraph Operations Usage
        R1[Monthly Reports]
        R2[Progress Tracking]
        R3[Resource Planning]
        
        SUM --> R1 & R2 & R3
    end

    classDef data fill:#d4ebf2,stroke:#1b70a6,color:#000
    classDef platform fill:#fdf1d5,stroke:#d4a017,color:#000
    classDef ai fill:#e8f5e8,stroke:#2d862d,color:#000
    classDef ops fill:#ffe6e6,stroke:#cc0000,color:#000
    
    class D1,D2,D3,D4,D5,D6 data
    class L1,G1,DQ platform
    class API,SEC,MON,ORCH platform
    class LLM,AGG,SUM,VEC ai
    class R1,R2,R3 ops
```

The system begins with raw data collection from various sources, primarily Discord at present, with planned expansion to Git, JIRA, Google Docs, and Notion. This data moves through our S3-based landing and gold zones, where it undergoes quality checks and transformations before feeding into our platform and AI engineering layers.

### Detailed Processing Pipeline

```mermaid
graph LR
    subgraph Data Collection
        DC1[Discord Collector]
        DC2[Git Collector]
        DC3[JIRA Collector]
        SCHEDULE[Weekly Schedule]
        
        SCHEDULE --> DC1 & DC2 & DC3
    end

    subgraph Processing Pipeline
        B1[Message Buffer]
        B2[Git Buffer]
        B3[Ticket Buffer]
        
        P1[PII Scrubber]
        P2[Data Validator]
        P3[Schema Enforcer]
        
        DC1 --> B1
        DC2 --> B2
        DC3 --> B3
        
        B1 & B2 & B3 --> P1
        P1 --> P2
        P2 --> P3
    end

    subgraph Storage Layer
        S1[S3 - Parquet Files]
        S2[S3 - CSV Files]
        
        P3 --> S1
        P3 --> S2
    end

    subgraph Query Layer
        Q1[DuckDB Engine]
        Q2[Polars Engine]
        Q3[Report Generator]
        
        S1 --> Q1
        S2 --> Q2
        Q1 & Q2 --> Q3
    end

    style DC1 fill:#d4ebf2,stroke:#1b70a6,color:#000
    style DC2 fill:#d4ebf2,stroke:#1b70a6,color:#000
    style DC3 fill:#d4ebf2,stroke:#1b70a6,color:#000
    
    style P1 fill:#fdf1d5,stroke:#d4a017,color:#000
    style P2 fill:#fdf1d5,stroke:#d4a017,color:#000
    style P3 fill:#fdf1d5,stroke:#d4a017,color:#000
    
    style Q1 fill:#e8f5e8,stroke:#2d862d,color:#000
    style Q2 fill:#e8f5e8,stroke:#2d862d,color:#000
    style Q3 fill:#e8f5e8,stroke:#2d862d,color:#000
```

Our processing pipeline emphasizes efficiency and security:

1. **Collection Layer**: Weekly scheduled collectors gather data from various sources
2. **Processing Pipeline**: Data undergoes PII scrubbing, validation, and schema enforcement
3. **Storage Layer**: Processed data is stored in S3 using Parquet and CSV formats
4. **Query Layer**: DuckDB and Polars engines provide fast, efficient data analysis

## Dify - Operational Intelligence through Low-code Workflows

We use Dify to transform our raw data streams into intelligent insights through low-code workflows. This process bridges the gap between our data collection pipeline and the operational insights needed by our team.

![](assets/project-report-use-case-dify.png)

```mermaid
graph LR
    subgraph "Input Collection"
        START[Start] --> |channel_id/dates| PE1[Parameter Extractor 1]
        START --> |git_token| PE2[Parameter Extractor 2]
        START --> |condition check| IE{IF/ELSE}
    end

    subgraph "Data Extraction"
        PE1 --> |Map| LE[Links Extraction]
        PE2 --> |Map| GE[Git Extraction]
        IE --> |dialogue_count ≤ 1| DM[Discord Messages]
    end

    subgraph "Parallel Processing"
        LE --> |Iterate| IT[Link Iterator]
        IT --> |Map| FSP[Fetch Single Page]
        GE --> |Map| GT[Git Traverser]
        DM --> |Map| VA[Variable Aggregator]
    end

    subgraph "Reduction & Output"
        FSP --> |Reduce| RED[Template Transform]
        GT --> |Reduce| RED
        VA --> |Reduce| RED
        RED --> LLM[Monthly Reporter LLM]
        LLM --> ANS[Answer]
    end

    style START fill:#f9f,stroke:#333,color:#000
    style IT fill:#bbf,stroke:#333,color:#000
    style RED fill:#bfb,stroke:#333,color:#000
    style ANS fill:#fbf,stroke:#333,color:#000

```

Our Dify implementation provides a few key advantages:

- **Rapid Iteration**
The low-code nature of Dify allows us to quickly adjust workflows based on operational feedback. When our operations team needs new types of insights, we can modify templates and processing logic without extensive development cycles.
- **Flexible Integration**
The workflow system easily integrates with our existing data pipeline, pulling from our S3 storage and utilizing DuckDB/Polars for efficient data processing before applying intelligence templates.
- **Maintainable Intelligence**
Templates and workflows are version-controlled and documented, making it easy for team members to understand and modify the intelligence generation process. This ensures our reporting system can evolve with our organizational needs.

## Operational Impact

The Project Reports system serves as the foundation for our Operations team's project oversight. It provides:

- **Real-time Project Visibility**: Operations can track progress across multiple projects through consolidated communication data, enabling early identification of potential issues or bottlenecks.
- **Data-Driven Decision Making**: By analyzing communication patterns and project discussions, we can make informed decisions about resource allocation and project timelines.
- **Automated Reporting**: The system generates comprehensive monthly reports, reducing manual effort and ensuring consistent project tracking across the organization.

## Technical Implementation

### Secure Data Collection

The cornerstone of our system is a robust collection pipeline built on Modal. Our collection process runs weekly, automatically processing Discord messages through a sophisticated filtering system that preserves critical technical discussions while ensuring security and privacy.

```python
@app.function(
    schedule=modal.Cron("0 1 * * 1"),  # Weekly Monday collection
    secrets=[secrets],
)
def weekly_discord_collection():
    category_id = get_category_id.local()
    channels = get_category_channels.remote(category_id)
    channel_args = [(channel, year, month) for channel in channels]
    saved_files = process_channel_monthly_data.starmap(channel_args)

```

Through Modal's serverless architecture, we've implemented separate landing zones for different project data, ensuring granular access control and comprehensive audit trails. Each message undergoes content filtering and PII scrubbing before being transformed into optimized Parquet format, providing both storage efficiency and query performance.

### Query Interface

The system provides a flexible API for accessing processed data:

```python
@app.function(
    volumes={MOUNT_PATH: modal.CloudBucketMount("dwarvesf-discord", secret=secrets)},
    secrets=[secrets],
)
@modal.web_endpoint(method="POST")
def query_messages(item: QueryRequest, token: str = Depends(verify_token)) -> Dict:
    parquet_files = get_relevant_files.remote(
        channel_id=item.channel_id,
        category_id=item.category_id,
        start_date=item.start_date,
        end_date=item.end_date,
    )

```

## Measured Impact

The implementation of Project Reports has fundamentally transformed our project management approach. Our operations team now have greater visibility into project progress, with tracking and early issue identification becoming the norm rather than the exception. The automated documentation of key decisions has significantly reduced meeting overhead, while the correlation between discussions and deliverables ensures nothing falls through the cracks.

## Future Development

We're expanding the system's capabilities in several key areas:

- **Additional Data Sources**: Integration with Git metrics, JIRA tickets, and documentation platforms will provide a more comprehensive view of project health.
- **Enhanced Analytics**: Implementation of advanced pattern recognition and trend analysis will improve our predictive capabilities.
- **Automated Insights**: Deeper AI integration will enable more sophisticated report generation and context understanding.

We also don’t plan to be vendor-locked using entirely Modal. The foundations we’ve layed out to create our landing zones and data lake makes it very easy to swap in-and-out query and API architectures.

## Conclusion

At Dwarves, our Project Reports system demonstrates the power of thoughtful data engineering in transforming raw communication into strategic project intelligence. By combining secure data collection, efficient processing, and AI-powered analysis, we've created a system that doesn't just track progress – it actively contributes to project success.

The system continues to coordinate our project data streams with precision and purpose, ensuring that every piece of information contributes to a clear picture of project health. Through this systematic approach, we're setting new standards for data-driven project management in software development, one report at a time.
