# Generative AI for Software Development
Study note for Generative AI for Software Development Skill Certificate offered by DeepLearning.AI.

- [Course 1: Introduction to GenAI](#course-1-introduction-to-genai)
  - [Setting up Jupyter environment](#setting-up-jupyter-environment)
    - [NOTE: `%%timeit`](#note-timeit)
  - [AI/ML](#aiml)
  - [Supervised Learning](#supervised-learning)
  - [Transformer](#transformer)
    - [Key concept 1: Attention mechanism](#key-concept-1-attention-mechanism)
    - [Key concept 2: Encoders and Decoders](#key-concept-2-encoders-and-decoders)
  - [Prompt best practices](#prompt-best-practices)
    - [Prompt Sample to generate code](#prompt-sample-to-generate-code)
    - [Prompt Samples with role assignment](#prompt-samples-with-role-assignment)
  - [Useful Verbs for Prompts](#useful-verbs-for-prompts)
- [Course 2-1: Testing and Debugging](#course-2-1-testing-and-debugging)
  - [Exploratory Testing](#exploratory-testing)
  - [Functional Testing](#functional-testing)
  - [Automated Testing](#automated-testing)
    - [Pytest](#pytest)
  - [Software Performance Testing](#software-performance-testing)
  - [Security Testing](#security-testing)
- [Course 2-2: Documentation](#course-2-2-documentation)
  - [Principles of good documentation](#principles-of-good-documentation)
  - [Inline \& Documentation comments](#inline--documentation-comments)
  - [Automated documentation tools](#automated-documentation-tools)
- [Course 2-3: Dependency Management](#course-2-3-dependency-management)
  - [Examples Prompts](#examples-prompts)
  - [Managing dependency conflicts](#managing-dependency-conflicts)
  - [Researching Dependencies and Security](#researching-dependencies-and-security)
- [Course 3-1: Data Serialization and CDD](#course-3-1-data-serialization-and-cdd)
  - [Brainstorming design paradigms](#brainstorming-design-paradigms)
  - [Configuration-Driven Development (CDD)](#configuration-driven-development-cdd)
  - [Configuration File Format for CDD](#configuration-file-format-for-cdd)
  - [Data Serialization](#data-serialization)
  - [DALL-E API \[dolly\]](#dall-e-api-dolly)
- [Course 3-2: Database](#course-3-2-database)
  - [Example Prompt 1: General Database Schema Design](#example-prompt-1-general-database-schema-design)
  - [Example Prompt 2: E-commerce Database Schema Design](#example-prompt-2-e-commerce-database-schema-design)
  - [Example Prompt 3: Creating a New Record](#example-prompt-3-creating-a-new-record)
  - [Example: Database optimization](#example-database-optimization)
  - [Debugging](#debugging)
- [Course 3-3: Software Design Patterns](#course-3-3-software-design-patterns)
  - [What are design patterns?](#what-are-design-patterns)
  - [The Gang of Four Design Patterns](#the-gang-of-four-design-patterns)
    - [1. Creational Patterns](#1-creational-patterns)
    - [2. Structural Patterns](#2-structural-patterns)
    - [3. Behavioral Patterns](#3-behavioral-patterns)
  - [Singleton Pattern](#singleton-pattern)
    - [Prompt Templates for Singleton](#prompt-templates-for-singleton)
  - [Factory Pattern](#factory-pattern)
    - [Factory pattern elements](#factory-pattern-elements)
  - [Template Method Pattern](#template-method-pattern)
    - [Example Use Cases](#example-use-cases)
  - [Strategy Pattern](#strategy-pattern)
    - [Steps to Implement the Strategy Pattern](#steps-to-implement-the-strategy-pattern)

## Course 1: Introduction to GenAI
Introduction to Generative AI for Software Development

### Setting up Jupyter environment
1. Install Anaconda distribution

    Anaconda distribution includes Python, the Jupyter Notebook, and other commonly used packages for data science.

    Download the installer: [Anaconda website](https://www.anaconda.com/products/distribution)

2. Start the Jupyter Notebook server
    ```
    jupyter notebook
    ```

#### NOTE: `%%timeit`
`%%timeit` is a magic command in Jupyter Notebook that is used to measure the execution time of code.

`%%timeit` is written at the top of a code cell, and it will measure the execution time of **the entire cell**.

`%timeit` measures the execution time of **a single line** of code.

### AI/ML
- **AI** is the broader concept of intelligent machines
- **Machine learning** is a method within AI that focuses on learning from data

### Supervised Learning
Supervised learning involves training models on labeled data, similar to teaching with flashcards.

**Large language models (LLMs)** like ChatGPT are trained using supervised learning on vast amounts of text, learning relationships between words to generate coherent text.


### Transformer
The transformer model, which were first introduced in 2017, significantly improved how AI processes text, making it possible to develop advanced large language models (LLMs) like GPT.

Transformers build on supervised learning. The attention mechanism within transformers allows the model to focus on important words or tokens in a sequence, improving contextual understanding.

#### Key concept 1: Attention mechanism

Allows the model to focus on specific words when predicting the next word.

**Example**: In "my little white fluffy dog," attention highlights "little," "white," and "fluffy" to better understand "dog."

**Tokens and Embeddings**:

Text is split into **tokens**, each assigned a vector (**embedding**) that represents its meaning. Attention refines these embeddings based on surrounding words for better context understanding.

#### Key concept 2: Encoders and Decoders

Encoders analyze the entire input at once, and decoders generate new content from the processed context.

### Prompt best practices
- Be specific
- Use clear language
- Provide context
- Assign roles
- Give feedback iteratively


#### Prompt Sample to generate code
```
Write a Python function named calculate_area that takes an argument radius.

The function should calculate the area of a circle given the radius. Ensure that the function handles non-numeric inputs by raising a ValueError with the message 'Input must be a numeric value.'

Include comments in the code explaining each step.
```
#### Prompt Samples with role assignment
```
As a backend developer with expertise in Java, review this API code and suggest performance improvements and code optimizations.

As a frontend developer specializing in accessibility, assess this web page for accessibility issues and recommend improvements.

As a DevOps engineer, evaluate this CI/CD pipeline for potential bottlenecks and suggest optimization strategies.

As a software tester, analyze this function for potential edge cases and suggest robust handling strategies.

As a cybersecurity expert, review this code for vulnerabilities and propose security hardening measures.

As a Python tutor speaking to a very novice programmer, explain how loops work in Python.

As a cloud architect, assess this infrastructure setup and provide recommendations for scalability and cost efficiency.

As a technical writer, improve the clarity and structure of this code documentation for developers.

As an AI specialist, evaluate this machine learning model for training efficiency and suggest optimization techniques.

As a data engineer, review this ETL pipeline for data processing efficiency and suggest areas of improvement.

As both a software architect and a security expert, evaluate this Python script for a web application and suggest architectural improvements and security enhancements.

As a project manager, assess this development plan and suggest any adjustments to improve delivery timelines and team efficiency.

As a product manager, evaluate this feature implementation and suggest changes to improve the user experience.

As a contributor to open-source Python projects, critique this Python library for data visualization and suggest enhancements.

You stricktly have to convert from py2 to py3 without any change in logic and focusing on the division handling difference.
```

### Useful Verbs for Prompts

1. **Profile**: Analyze performance aspects (e.g., memory, CPU usage, execution time).
2. **Analyze**: Examine in detail to understand functionality, performance, or issues.
3. **Optimize**: Improve the efficiency of code (e.g., reduce time complexity or memory usage).
4. **Refactor**: Modify code structure without changing its external behavior to improve readability or maintainability.
5. **Debug**: Identify and fix errors or issues in the code.
6. **Evaluate**: Assess code or an algorithm for correctness, efficiency, or suitability.
7. **Validate**: Check the correctness or validity of input, output, or logic.
8. **Benchmark**: Measure the performance of code or an algorithm under specific conditions.
9. **Test**: Run and verify the functionality of code under different scenarios.
10. **Document**: Generate explanations or comments to improve code readability and maintainability.
11. **Simulate**: Model the code execution or system behavior under specific conditions.
12. **Audit**: Review code for security vulnerabilities or compliance with best practices.
13. **Automate**: Streamline tasks by writing scripts or workflows to reduce manual effort.
14. **Generate**: Automatically produce code, documentation, or tests from given inputs.
15. **Modify**: Make changes to the existing code or system to alter its behavior or structure.
16. **Update**: Apply changes or improvements, often in the context of keeping code or dependencies current.


## Course 2-1: Testing and Debugging
```
As an expert software tester who's teaching a new person how to write test cases, analyze this code and provide a set of test cases explaining each one.
```

### Exploratory Testing
- Exploratory testing is an informal testing method where you explore an application without predefined test cases.
- The goal is to discover bugs by using the app in a user-like way.
- Highly useful for identifying edge cases and unexpected behavior early in the development process.

**Using LLM for Testing**:
- Assign **roles** to the LLM to guide its analysis.
- Provide detailed **context** and **specific problems**.
- Brainstorm and identify **edge cases** early on.
- LLM can suggest improvements, such as using **thread locks** to ensure safety in a multi-user environment.

```
You are a software engineer and tester who likes to go through code looking for edge cases. Please explore the Python code and find any issues that might causes bugs or poor functionality.
```

### Functional Testing

Functional testing checks if an application works according to **predefined requirements**.

- LLMs can help structure exploratory tests into functional tests.
- You can specify tools like the `unittest` package in your prompt.
- LLMs can help maintain test cases by suggesting updates based on the latest code.

```
As an expert software tester, write code that converts the output of the exploratory testing into functional tests using the unittest module in Python.
```

### Automated Testing
  - Extension of **functional testing**, reducing manual effort, human error, and ensuring consistency.
  - Automated tests run frequently, providing quick feedback and catching issues early.

- LLMs can:
  - Write test scripts in a **consistent style**, which helps teams collaborate efficiently.
  - Adapt to different programming languages (e.g., converting Python code to JavaScript).
  - Suggest relevant testing frameworks in other languages, such as **Jest** for JavaScript.


```
You are an expert in PyTest for automated testing. Create a comprehensive set of tests in Pytest to find bugs or other issues in this code below.
```

#### Pytest
  - **Pytest** is a powerful and flexible testing framework for Python.
  - Pytest automatically discovers and runs tests prefixed with `test_`.

- **Colab Specifics**:
  When working in Colab, tasks.py files can be created and saved using `%%file tasks.py`. Tests can then be run using `pytest`.

### Software Performance Testing

Performance testing ensures that your applications run efficiently and can handle expected user loads in production environments.

**Measuring Execution Time**:
  - Python's `timeit`, `time`, and `cProfile` libraries are useful for measuring how long functions take to execute.

**Identifying Bottlenecks**:
  - The `cProfile` library can measure how much time each function consumes, helping you locate bottlenecks.

**Using LLM to Improve Code**:
```
How can I measure how long it takes to call this function in Python?

Rewrite this function below to be more optimized. Below the code is the output from a cProfile analysis of the function.
```

### Security Testing

Security testing is essential for identifying vulnerabilities that could expose applications to malicious attacks, especially when dealing with public APIs.

While LLMs can assist in understanding security concepts, their utility in this area is limited due to their **knowledge cutoff** and lack of real-time updates on emerging threats.

```
You are an expert in web security and in creating API endpoints. Can you create some test cases that test against  potential vulnerabilities in the following code?
```

Repeat:
1. Create and run test cases for potential security issues
2. Improve your code to mitigate issues found in testing

Remember, code is never finished because code will always be under attack!

## Course 2-2: Documentation
The better your documentation, the easier everybody's job well be.

- Good documentation can improve code readability.
- Bad documentation can lead to inconsistencies, user errors, and difficulty in maintaining documents.

### Principles of good documentation
- Be clear and concise
- Avoid redundancy
- Think of your audience
- Follow language—specific conventions
- Keep documentation up to date

### Inline & Documentation comments
```
Add inline comments to this Python function:

Critique the comments in this code, and offer suggestions for improvement:
```

**Documentation comments** is speicial comments to explain purspose and usage of code
```
Add a documentation comment for the Python function:

Add clear and extensive comments in JSDocs format to the following code:

Provide Javadoc comments for the following code that are clear, extensive and relevant:

Refactor the documentation comment into the ReST style.
```

### Automated documentation tools

Automated documentation tools help generate, manage, and maintain documentation for codebases automatically, based on the code structure, comments, and annotations.

- Javadoc (Java): Javadoc is a tool for generating HTML documentation from Java source code.
- Sphinx (Python): Sphinx is widely used in the Python ecosystem.

**Docs as Code** treats documentation like code. It keep docs up-to-date with the software using tools like version control (Git) and CI. Docs are written in formats like Markdown.


## Course 2-3: Dependency Management

- Brainstorm Libraries and Packages
- Learn More About a Dependency
- Identify Dependency Conflicts
- Suggest Solutions for Dependencies

### Examples Prompts

 - Brainstorming
  ```
  I am starting a data science project in Python and am looking to create some visualizations. Which libraries would allow me to create those?
  ```

- Setting Up Virtual Environments
  ```
  You're an expert in Python programming and dependency management. How do I set up a virtual environment using venv on Mac?
  ```

- Summarizing Dependencies
  ```
  For each dependency in my Python project, provide a summary of what it does and whether it is secure.
  ```

### Managing dependency conflicts

1. Identifiying conflicts: Determine which dependencies are causing the issue.
2. Check compatibility: Lock for versions that are compatible with all packages.
3. Update dependencies: Uppdate or modify your dependencies to resolve the conflict.

### Researching Dependencies and Security
- Checking for Known Issues
  ```
  How can I check the following `package.json` file for known dependency issues?”
  ```

- Verifying Security of Packages

  Dependency Audit Tools help audit and monitor dependencies for security and stability, such as `pip-audit` (Python) or `npm audit` (JavaScript).
  ```
  When I run `pip-audit`, I got a warning: '***'. Can you explain this?
  ```

- Research Security Issues
  ```
  Are there any known security issues for these libraries?
  ```

## Course 3-1: Data Serialization and CDD

### Brainstorming design paradigms
```
You are an expert an software design paradigms. I am working on building a simple Python-based app that will make calls to the DALL-E API and generate images for users.

The application will be deployed in many different contexts and configurations depending on the end users, and I want my less technical colleagues to be able to do some customization without editing the code itself.

What high level software design paradigms should I consider for this project?
```

### Configuration-Driven Development (CDD)

1. Design Paradigms in Software:
   - Software paradigms guide development and solve common challenges.
   - Examples include OOP, MVC, microservices, and TDD.

2. What is Configuration-Driven Development?
   - Definition: CDD uses external files (e.g., JSON, YAML) to define app configurations like API keys and settings.
   - Implementation: The app reads configuration files to adjust behavior, allowing easy customization without changing the source code.

3. Benefits of CDD:
   - Customization: Non-technical users can modify settings via configuration files.
   - Flexibility: The same codebase can be used in different environments.
   - Reduced bugs: Configuration changes don’t alter source code.

4. Drawbacks of CDD:
   - Complexity: Managing many configuration files can be difficult.
   - Debugging: Troubleshooting is harder when issues arise from configuration files.
   - Security risks: Sensitive data in configuration files can be exposed.

Use CDD when you need easy configuration, your team includes non-technical users, or you need scalability and flexibility. Consider security when sensitive data is involved.

### Configuration File Format for CDD

1. **JSON (JavaScript Object Notation):**
  - Support across many languages
  - No comment support
  - Verbose

2. **YAML (YAML Ain't Markup Language):**
  - More readable
  - Supports comments
  - Potentially error-prone due to indentation

### Data Serialization
- Convert data into format that allows for easy storage, movement, and reconstruction.
- Different serialization formats used depending on project requirements.
- Pickle is a popular format used to serialize and deserialize data types in Python.

### DALL-E API [dolly]
**DALL-E API** allows developers to generate images from text prompts by integrating DALL-E’s powerful image generation model into applications.

- The DALL-E API requires multiple parameters, including model-specific parameters (e.g., image prompts) and application-specific parameters (e.g., API keys, file locations).
- Successful API calls return a JSON object containing URLs for the generated images.

```
Please create easy to read, easy to follow code that will call DALL-E to generate an image. The code should be in Python, and all parameters should be in an external file that the Python code reads. Use the most up-to-date design pattern.

I have this code that calls the REST endpoint for DALL-E to generate an image. Can you externalize the hardcoded parameters in a separate file?

Suggest additional settings I could add to the configuration file and explain what behaviors in my app they would help control.

Update the configuration file and the app code to include a timeout for the API coles.
```

## Course 3-2: Database

```
Suggest a lightweight but powerful python setup that uses a file-based database so that I can practice working with databases. I want the code to be able to run in google corab.
```

### Example Prompt 1: General Database Schema Design
```
I need to develop a database for [application type, e.g., a social network].

- The database will manage [describe the types of data you want to store, e.g., user profiles, posts, comments, likes, etc.].
- Suggest a schema that would work for this, including tables, relationships, and key attributes.
```

### Example Prompt 2: E-commerce Database Schema Design
```
Design a database schema for an e-commerce application. The schema should include tables for users, products, orders, and order_items.

- I am using a SQLite database with SQLAlchemy in Python. Help me implement the following schema, including relationships between tables.
- Suggest keys and attributes for each table.
```

### Example Prompt 3: Creating a New Record
SQLAlchemy is a widely-used Python library for interacting with SQL databases. You can prompt an LLM to help with writing CRUD operations.

```
I have a users table in my SQLite database set up with SQLAlchemy.

- How can I create a Python function to add a new user to the users table?
- The function should handle common security issues like SQL injection.
```

```
Write a SQLAlchemy query to find all orders placed by a specific user in the e-commerce database.
```

### Example: Database optimization
Start with high-level prompts such as:
```
What are the best practices to improve the performance of this database?
```
Use follow-up prompts to dig deeper into specific topics like indexing, caching, or schema optimization.

- Indexing:
  - Smart indexing significantly speeds up data retrieval but should be used cautiously.
  ```
  What are the best practices for indexing in a SQL database?
  ```

- Caching:
  - Caching reduces database load by storing results from expensive queries and reusing them for subsequent requests.

  ```
  How can I implement basic query caching in SQLAlchemy?
  ```

- Schema optimization
  - Schema design is fundamental to database performance, but revisiting and optimizing column data types post-design is also crucial.
  ```
  What are the best practices for choosing data types in a SQL database?
  ```

### Debugging
```
- How do I handle database connection errors?
- What are best practices for enabling query logging?
- How can I debug query performance?
```

## Course 3-3: Software Design Patterns

```
Analyze  this code and then suggest how to improve it using software design patterns from the Gang of For.
```

### What are design patterns?
- Reusable solutions to common problems in software design.
- Outline standard ways to structure and organize code, enhancing code readability, reusability, and maintainability.
- Design patterns help developers communicate their ideas efficiently.

### The Gang of Four Design Patterns
- The term "Gang of Four" refers to Erich Gamma, Richard Helm, Ralph Johnson, and John Vlissides, authors of the 1994 book *Design Patterns: Elements of Reusable Object-Oriented Software*.
- This book influenced the design of many programming languages and shaping modern software architecture.

#### 1. Creational Patterns
Deal with object creation mechanisms, aiming to make object creation more flexible and efficient.

- **Singleton**: Ensures a class has only one instance and provides global access to it.
- **Builder**: Separates object construction from its representation, enabling different outputs from the same process.
- **Prototype**: Creates new objects by copying a prototypical instance.
- **Factory Method**: Provides an interface for creating objects, allowing subclasses to decide which class to instantiate.
- **Abstract Factory**: Defines an interface for creating families of related objects without specifying their concrete classes.

#### 2. Structural Patterns
Focus on the composition of classes and objects, ensuring that larger structures are created from smaller objects efficiently.

You may recognize the **Decorator** pattern in Python and have seen **Adapter** and **Facade** in various other contexts.


- **Adapter**: Allows classes with incompatible interfaces to work together by wrapping one interface around another.
- **Bridge**: Decouples abstraction from implementation, allowing both to evolve independently.
- **Composite**: Composes objects into tree structures to represent part-whole hierarchies, treating individual objects and compositions uniformly.
- **Decorator**: Dynamically adds functionality to objects by wrapping them in special objects.
- **Facade**: Provides a simplified interface to a complex body of code.
- **Flyweight**: Minimizes memory usage by sharing data among similar objects.
- **Proxy**: Controls access to an object, reducing complexity and costs.


#### 3. Behavioral Patterns
Define how classes and objects interact, and how responsibilities are assigned.

These patterns facilitate communication between objects and enable complex interactions.

- **Iterator**: Provides a way to access elements of a collection sequentially without exposing its internal structure.
- **Strategy**: Defines a family of algorithms and encapsulates each, allowing them to be used interchangeably.
- **Template Method**: Defines the basic structure of an algorithm while allowing subclasses to override certain steps.


### Singleton Pattern

- **Singleton** ensures that only one instance of a class is created, making it ideal for managing global resources like **database connections** or **configuration settings**.
- It prevents redundancy and ensures that all parts of an application access the same instance, which simplifies code management and resource usage.
- **Singletons** are common for managing global state and shared data, but they should be used with caution to avoid potential bottlenecks or unintended consequences.

#### Prompt Templates for Singleton

1. **Basic Singleton Creation:**
   - "How can I implement a singleton pattern in Python?"
   - "Show me how to create a class that can only be instantiated once."

2. **Enhancing Singleton with Data:**
   - "How do I add configuration data to a singleton class in Python?"
   - "Can you extend a singleton pattern to hold shared data globally?"

3. **Testing Singleton:**
   - "How can I test if two instances of a singleton class are the same?"
   - "Write code to verify the correct implementation of the singleton pattern."

### Factory Pattern

- The **Factory Pattern** provides an interface for creating objects, but allows subclasses to alter the type of objects that are created.
- The main goal is to **decouple** the process of object creation from the code that uses the objects. This adds flexibility to the design, allowing different variations of objects to be created without modifying the core application logic.

#### Factory pattern elements
- **A Factory class**: Handles overall production of objects
- **Concrete classes**: Provide specific instructions to make variations of those objects


### Template Method Pattern
The Template Method pattern defines the skeleton of an algorithm in a base class, allowing subclasses to override specific steps without changing the overall structure.

This pattern is useful for scenarios where you want to define a common process but allow specific parts of that process to be customized by different subclasses.

- It **reduces code duplication** by centralizing the shared logic in the base class.
- **Subclasses can customize** specific steps (e.g., post‐processing data for different countries or time zones) without altering the general data processing workflo


#### Example Use Cases
- If a company operates in the EU and US, you might need to convert the stock price from Euros to USD for comparison with domestic companies.
- You may need to adjust the timestamps to match the time zone of the company.


### Strategy Pattern
The **Strategy Pattern** is particularly powerful in software that needs to adapt to changing requirements or environments without significant refactoring of the core code.

This pattern can be applied in various domains, such as sorting algorithms, payment processing, or route planning in applications.

#### Steps to Implement the Strategy Pattern
1. Define a Common Interface: Create an interface shared by all strategies, defining a method that each strategy will implement differently.
2. Implement Concrete Strategies: Inherit from the interface and provide a concrete implementation of the defined method for each specific strategy.
3. Using the Strategy: In the client code, select and apply different strategies based on the context. Strategies can be easily swapped without modifying the core code.

NOTE: **Client Code** refers to the part of the program that selects and applies a specific strategy (algorithm) from the options provided by the Strategy Pattern.


