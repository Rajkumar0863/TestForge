# TestForge

**LLM-Assisted Automated Test Generation and Mutation Testing for Java**

TestForge is an experimental software engineering framework for generating unit
tests for Java programs using Large Language Models (LLMs) and evaluating their
effectiveness using mutation testing.

Rather than measuring generated tests only by whether they compile or achieve
code coverage, TestForge uses **mutation testing** to examine whether generated
test suites can detect deliberately introduced faults in the source code.

> **Status:** 🚧 Under active development

---

## Overview

Large Language Models can generate unit tests quickly, but generating a test
that compiles is not necessarily the same as generating a test that effectively
detects faults.

TestForge provides an experimental pipeline for investigating this problem.

The framework takes Java source code as input, generates JUnit 5 test cases,
executes the generated tests, applies mutation testing using PIT, and records
metrics describing the effectiveness of the generated test suite.

The project is also being developed as an engineering prototype supporting my
MSc Software Development dissertation research at the University of Limerick.

---

## Research Question

**How effective are Large Language Models at automatically generating unit tests
for Java programs when test quality is evaluated using mutation testing?**

TestForge provides the infrastructure required to investigate this question
through repeatable experiments.

---

## Workflow

```text
┌──────────────────────┐
│   Java Source Code   │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│  LLM Test Generator  │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│ Generated JUnit Tests│
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│    Test Execution    │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│ PIT Mutation Testing │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│   Mutation Results   │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│ Evaluation & Analysis│
└──────────────────────┘
```

---

## Technology Stack

| Component | Technology |
|---|---|
| Target language | Java |
| Unit testing | JUnit 5 |
| Mutation testing | PIT |
| Build system | Maven |
| Experiment orchestration | Python |
| Test generation | Large Language Model APIs |
| Version control | Git & GitHub |

---

## Evaluation Metrics

TestForge is designed to collect experimental metrics including:

- **Compilation success rate** — whether generated tests compile successfully.
- **Test execution success rate** — whether generated tests execute without errors.
- **Number of generated tests** — number of test cases produced during an experiment.
- **Mutation score** — proportion of generated mutants detected by the test suite.
- **Mutants killed** — faults successfully detected by generated tests.
- **Mutants survived** — faults that remain undetected.
- **Generation time** — time required to generate the test suite.

A central metric is the mutation score:

```text
Mutation Score = Killed Mutants / Total Executed Mutants × 100
```

These measurements will allow test suites generated under different experimental
configurations to be compared.

---

## Planned Project Structure

```text
TestForge/
│
├── java-project/
│   ├── pom.xml
│   └── src/
│       ├── main/
│       │   └── java/
│       └── test/
│           └── java/
│
├── generator/
│   ├── prompts/
│   └── test_generator.py
│
├── experiments/
│   └── experiment_config/
│
├── scripts/
│   └── run_experiment.py
│
├── results/
│   └── .gitkeep
│
├── .gitignore
├── LICENSE
└── README.md
```

The structure above represents the planned architecture and will evolve as the
implementation develops.

---

## Development Roadmap

### Phase 1 — Mutation Testing Baseline

- [ ] Create benchmark Java classes
- [ ] Configure Maven project
- [ ] Add JUnit 5
- [ ] Write baseline unit tests
- [ ] Integrate PIT
- [ ] Generate the first mutation report

### Phase 2 — LLM Test Generation

- [ ] Build the Python test-generation pipeline
- [ ] Read Java source files automatically
- [ ] Construct test-generation prompts
- [ ] Connect an LLM API
- [ ] Generate JUnit 5 test classes
- [ ] Validate generated Java code

### Phase 3 — Automated Evaluation

- [ ] Compile generated tests automatically
- [ ] Execute generated test suites
- [ ] Run PIT automatically
- [ ] Parse mutation reports
- [ ] Calculate experiment metrics
- [ ] Export results to CSV/JSON

### Phase 4 — Experimental Evaluation

- [ ] Create a benchmark dataset
- [ ] Define controlled prompt configurations
- [ ] Run repeated experiments
- [ ] Compare generated test suites
- [ ] Analyse surviving mutants
- [ ] Produce reproducible experimental results

---

## Example Experiment

A future TestForge experiment will follow a process similar to:

```text
Input
  └── Calculator.java

Test Generation
  └── LLM generates CalculatorTest.java

Execution
  └── Maven + JUnit execute generated tests

Mutation Testing
  └── PIT creates mutations in Calculator.java

Evaluation
  ├── Mutants generated
  ├── Mutants killed
  ├── Mutants survived
  └── Mutation score

Output
  └── Structured experiment results
```

This provides a repeatable way to evaluate whether an LLM-generated test suite
actually detects behavioural changes in the target program.

---

## Reproducibility

Reproducibility is an important goal of TestForge.

Experimental runs are planned to record information such as:

- Target Java program
- Model used for generation
- Prompt configuration
- Generation parameters
- Generated test suite
- Test execution result
- Mutation testing result
- Experiment timestamp

This will allow experimental configurations and their outputs to be compared
systematically.

---

## Research Context

TestForge supports the MSc dissertation:

**An Empirical Evaluation of Large Language Models for Automated Software Test
Generation Using Mutation Testing**

The repository focuses on the engineering implementation required to conduct
controlled experiments. The dissertation will separately address research
methodology, literature review, experimental design, statistical analysis and
interpretation of results.

---

## Current Status

TestForge is currently in the **initial implementation stage**.

The immediate development milestone is to establish a working Java testing
baseline using:

```text
Java → JUnit 5 → PIT → Mutation Report
```

LLM-based test generation will be integrated after the baseline mutation-testing
pipeline is operational.

---

## Author

**Rajkumar Vijayan**

MSc Software Development (International Systems)  
University of Limerick, Ireland

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Rajkumar%20Vijayan-blue?logo=linkedin)](https://www.linkedin.com/in/rajkumar-vijayan-0135a8338/)
[![GitHub](https://img.shields.io/badge/GitHub-Rajkumar0863-black?logo=github)](https://github.com/Rajkumar0863)

---

## License

A project licence will be added as the project develops.
