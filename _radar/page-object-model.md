---
tags: null
title: Page Object Model
date: null
description: null
authors: null
confidence: High
assign: Steve Huynh
priority: null
status: Adopt
quadrant: Techniques
tag: Testing, Automation
---

<!-- table_of_contents 363bb8b8-0aa2-423d-b1bc-f59606aa4ddf -->

### Description
Page Object Model (POM) is a popular design pattern used in test automation for creating object repositories for web UI elements. It helps in creating a modular framework and provides a clear separation between test code and page-specific code, making the automation scripts more maintainable and reusable. In POM, each web page is represented as a class, and its elements are defined as variables in that class, along with their respective actions. The test cases interact with these web elements through the methods defined in their respective page classes, making the code more readable and understandable. POM enables testers to easily manage large test suites and ensure better code quality and test coverage, ultimately leading to better software quality.

### What’s better about this method or library
1. Improves Code Reusability: With the help of Page Object Model, you can reuse the code and create different test cases for the same page. This saves time and effort, as you don't have to write the same code again and again.
1. Enhances Code Maintenance: When you implement Page Object Model, the code is organized in a structured manner as per the functionality of the page. Hence, it becomes easier to maintain and modify the code. Even if the UI changes, the corresponding changes can be done in the Page Object Model, and the rest of the code remains unchanged.
1. Efficient Collaboration: With Page Object Model, developers and testers can work together efficiently, as each can focus on their respective roles. Developers can create the page objects, and testers can write test cases using them.
1. Increases Test Case Scalability: As the complexity of the application increases, the number of test cases also increases. With Page Object Model, you can create test cases for each page element and make the test case scalable.
1. Reduces Test Case Development Time: Page Object Model is a time-efficient approach that reduces the test case development time as the page objects are created in advance, and testers can focus on writing the test cases.

### What can we do with it
Page Object Model (POM) is a design pattern used in automation testing that helps to create reusable test code and make tests more maintainable. With POM, we can:

1. Create a separate class for each page or screen of the application, and define all the elements and actions that can be performed on the page.
1. Use these classes in the test code to access and interact with the elements on each page without having to repeat the same code every time.
1. Change or update the UI of the application without affecting the test code, as the page classes will handle all the interactions with the UI.
1. Improve the readability and maintainability of the test code by separating the page elements and actions from the test logic.
1. Share the page classes across multiple tests and test suites, which makes it easier to manage and scale the automation effort.

### How we adopted it
Since this is the common structure which is applying by every Automation Quality Assurance Engineering at the moment. So basically, everytime we initiate and implement the Automation’s source, we should follow up with this structure to work on the automation testing.

<!-- child_database 131eda97-51b4-48a0-8499-fab88a1a36ad -->

