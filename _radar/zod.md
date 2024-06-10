---
tags: null
title: Zod
date: null
description: null
authors: null
confidence: Moderate
assign: Luke Huynh Thanh Hai
priority: null
status: Trial
quadrant: Tools
tag: Frontend
---

<!-- table_of_contents 340a9a4e-3845-4ace-ab75-f99b83ced0dc -->

### Description
Zod is a TypeScript-first schema declaration and validation library. I'm using the term "schema" to broadly refer to any data type, from a simple `string` to a complex nested object.

Zod is designed to be as developer-friendly as possible. The goal is to eliminate duplicative type declarations. With Zod, you declare a validator *once* and Zod will automatically infer the static TypeScript type. It's easy to compose simpler types into complex data structures.

### What’s better about this method or library
Some other great aspects:

* Zero dependencies
* Works in Node.js and all modern browsers
* Tiny: 8kb minified + zipped
* Immutable: methods (e.g. `.optional()`) return a new instance
* Concise, chainable interface
* Functional approach: **[parse, don't validate](https://lexi-lambda.github.io/blog/2019/11/05/parse-don-t-validate/)**
* Works with plain JavaScript too! You don't need to use TypeScript.

### What can we do with it
With Zod, we can perform a variety of tasks related to data validation and type inference in TypeScript. Here are some common use cases and functionalities provided by Zod:

1. Schema Validation: Zod allows you to define schemas that specify the expected structure, types, and constraints of your data. We can validate data against these schemas to ensure it conforms to your defined rules. Zod provides numerous built-in validators, including string length, number range, object shape, array length, regular expressions, and more.
1. Type Inference: Zod leverages TypeScript's type system to provide static type checking and inference. It can automatically infer the types of validated data, allowing us to access the validated values with the correct TypeScript types. This helps catch potential type errors at compile time and improves the reliability of your code.
1. Custom Validators: In addition to the built-in validators, Zod allows us to define custom validators for complex data validation scenarios. You can create custom validation functions and combine them with the existing validators to handle specific validation requirements.
1. Schema Composition: Zod supports schema composition, enabling you to build complex schemas by combining and nesting simpler schemas. You can reuse and combine existing schemas to create more comprehensive validations for your data structures.
1. Transformation and Parsing: Zod provides methods to transform and parse data based on the defined schema. You can modify and sanitize the data during the validation process to ensure it meets your specific requirements. Zod also offers methods like `**pick()**` and `**omit()**` to select or exclude specific properties from the validated data.
1. Error Handling: When validation fails, Zod provides detailed error messages with information about the validation failures, including the specific paths and reasons for the errors. You can handle and customize these error messages to provide meaningful feedback to users or log them for debugging purposes.
1. Serialization and Deserialization: Zod supports serialization and deserialization of data by providing methods like `**JSON.stringify**` and `**JSON.parse**`. These methods ensure that the serialized data conforms to the defined schema, allowing you to safely exchange data between different systems or store it persistently.

<!-- child_database b17a43f1-bed4-4fe9-8186-529b79179e7c -->

