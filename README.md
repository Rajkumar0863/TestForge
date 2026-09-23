# TestForge

TestForge is an experimental software testing framework for evaluating
LLM-generated unit tests using mutation testing.

The project investigates whether large language models can generate effective
JUnit test suites for Java programs and measures their ability to detect
artificially introduced faults using mutation testing.

## Motivation

Large language models can generate unit tests quickly, but generating tests is
not the same as generating effective tests.

TestForge evaluates generated test suites using mutation testing rather than
relying only on test execution or code coverage. Mutations are introduced into
the target program and the generated tests are evaluated based on their ability
to detect those changes.

This project also serves as a prototype for my MSc Software Development
dissertation research on the empirical evaluation of large language models for
automated software test generation.

## Planned Workflow

Java Source Code
        |
        v
LLM Test Generation
        |
        v
Generated JUnit 5 Tests
        |
        v
Test Execution
        |
        v
PIT Mutation Testing
        |
        v
Mutation Results
        |
        v
Evaluation & Comparison

## Technology Stack

- Java
- JUnit 5
- PIT Mutation Testing
- Maven
- Python
- Large Language Model APIs
- Git & GitHub

## Evaluation Metrics

The experimental framework is planned to collect metrics including:

- Generated test compilation success
- Test execution success
- Number of generated tests
- Mutation score
- Mutants killed
- Mutants survived
- Test generation time

These metrics will allow different generated test suites and LLM configurations
to be compared empirically.

## Project Structure

```text
TestForge/
├── java-project/
│   ├── src/
│   │   ├── main/java/
│   │   └── test/java/
│   └── pom.xml
│
├── generator/
│   └── LLM test-generation pipeline
│
├── experiments/
│   └── Experimental configurations
│
├── results/
│   └── Mutation-testing results
│
├── scripts/
│   └── Experiment automation
│
└── README.md
