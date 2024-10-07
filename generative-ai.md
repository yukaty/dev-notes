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
- [Course 3](#course-3)

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

## Course 3
AI-Powered Software and System Design

