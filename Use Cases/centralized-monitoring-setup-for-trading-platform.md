---
authors:
  - 'thanh'
  - 'quang'
date: '2024-11-21'
description: 'A technical case study for implementing centralized monitoring for a trading platform using Grafana and Prometheus, focusing on real-time alerts, data integrity, and resource optimization to prevent financial losses.'
tags:
  - 'platform'
  - 'monitoring'
  - 'case-study'
title: 'Setup centralized monitoring system for Nghenhan Trading Platform'
---

Nghenhan is a privately-owned trading platform used by a select group of traders. Given the high-stakes nature of trading and the significant financial implications of system failures, it is crucial for Nghenhan to implement a robust, centralized monitoring system. This system must ensure platform reliability, minimize downtime, and prevent data loss to protect traders from substantial monetary losses.

## Understanding the unique challenges

As a privately-owned platform with a limited user base, Nghenhan faces unique challenges:

1. **High-Stakes Trading**: Each user represents a significant portion of the platform's trading volume. Any system failure or data loss can lead to substantial financial losses for these traders.
2. **Reputational Risk**: With a smaller user base, any issues with the platform can quickly erode trust and lead to user attrition. Maintaining a stellar reputation is essential for Nghenhan's long-term success.
3. **Resource Allocation**: While the user base is limited, the platform must still be equipped to handle peak usage times and spikes. Efficient resource allocation is critical to ensure reliable performance without overspending on infrastructure.

## Mitigating financial losses through proactive monitoring

To address these challenges, Nghenhan must implement a proactive monitoring strategy that focuses on:

1. **Real-time Alerts**: The monitoring system must provide instant notifications for any anomalies or threshold breaches. This allows the team to react swiftly and minimize the duration and impact of any issues.
2. **Data Integrity**: Ensuring the accuracy and synchronization of trading data is paramount. Any data loss or discrepancies can trigger false alarms or missed opportunities, leading to financial losses for traders.
3. **Resource Optimization**: Monitoring resource utilization helps Nghenhan allocate resources effectively during peak times while avoiding over-provisioning during normal usage.

## Implementing Grafana and Prometheus for robust monitoring

Integrating Grafana and Prometheus provides Nghenhan with a powerful centralized monitoring solution. Let's dive deeper into how these tools work together and examine the system diagram:

![](assets/nghenhan-monitoring-system-diagram.webp)

- **Backend Services**: The backend services of Nghenhan's trading platform expose metrics through an HTTP endpoint, which Prometheus scrapes at regular intervals.
- **Prometheus Server**: The Prometheus server scrapes the metrics from the backend services and stores them as time series data. It also handles the querying and alerting functionality.
- **Alert Manager**: The Alert Manager is a component of Prometheus that handles the routing and management of alerts. It receives alerts from Prometheus and sends notifications to the configured receivers, such as the admin or notification channels.
- **Grafana**: Grafana fetches data from Prometheus to create visualizations and dashboards. It also allows users to set up alerts and explore historical data.
- **Notification Receivers**: The notification receivers are the endpoints or channels where alerts are sent, such as email, Discord, or custom webhooks. The admin can also receive notifications and take appropriate actions based on the alerts.

### **Prometheus as Data Collector**

Prometheus serves as the primary data collection and monitoring tool, scraping metrics from various services and recording health and performance information. The setup involves configuring Prometheus to gather data on key metrics, including:

**CPU and Memory usage**

Making sure that system resources are not reaching critical thresholds.

![](assets/nghenhan-cpu-usage.webp)

**Error rates**

Tracking the number of errors in real time to quickly detect discrepancies.

![](assets/nghenhan-error-rate.webp)

**Data synchronization status**

Monitoring the synchronization of data from Binance to ensure its latest version without any data loss.

![](assets/data-sync-status.webp)

**Binance rate limit monitoring**

Implementing a rate limit monitoring system to ensure that requests to Binance are still compliant with the rate limits. This will prevent data loss during periods of high network traffic.

![](assets/nghenhan-binance-rate-limit.webp)

**Service back-off restarting**

due to multiple issues, such as resource limits, configuration errors, or dependency failures.

![](assets/nghenhan-service-back-off-restarting.webp)

### **Grafana as Data Visualizer for insightful observations**

Grafana complements Prometheus by providing robust data visualization capabilities. With Grafana, Nghenhan can create dynamic dashboards that display real-time data on service performance. These dashboards include:

**Real-time alerts**

Configured alerts notify our team of any anomalies, such as sudden increases in CPU usage or error rates, etc. that exceed established thresholds.

Here’s an example of how we configured conditions on Grafana to trigger an alert using the Alert Manager

![](assets/nghenhan-real-time-alert.webp)

The setup above will trigger an alert if data exceeds the threshold, and the Alert Manager will send it to Discord by webhook.

![](assets/nghenhan-discord-alert.webp)

**Interactive graphs**

We utilize visual representations of data that help us easily identify trends during peak trading times and spikes.

![](assets/nghenhan-interactive-graph.webp)

**Historical data analysis**

Grafana’s capabilities allow us to analyze historical data to understand system behavior and improve resource allocation strategies.

![](assets/nghenhan-historical-analytics.webp)

## Conclusion

To sum up, Nghenhan's decision to adopt a centralized monitoring system powered by Grafana and Prometheus is a testament to its dedication to providing a reliable and efficient trading platform. By focusing on real-time monitoring and ensuring data synchronization, Nghenhan can proactively identify and resolve potential issues, minimizing downtime and financial losses for its users. This monitoring system not only bolsters Nghenhan's operational capabilities but also serves as a foundation for future growth.
