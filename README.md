[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/Y4rZMh1t)

# Junior Seminar (CMPSC 580) Exemplar Project Repository

## Semester: Spring 2024

## GitHub Handle: jaclynpqc

## Name: Jaclyn Pham

## Major: Software Engineering

## Project Name: COMMA (Chasten Output Mutmut Mutation Analysis)

---

## Overview

Software testing is a critical aspect of software development, yet the effectiveness of test suites in ensuring program correctness remains uncertain. Mutation testing offers a systematic approach to evaluating test suite effectiveness by intentionally introducing defects into a program and assessing whether tests detect these faults.However, despite its informativeness, mutation testing is computationally expensive, leading to the limitation of effective test suite.

This research project addresses the challenge of enhancing mutation testing efficiency by investigating the relationship between code quality anti-patterns and muation scores in Python programs. By analyzing how specific coding practices impact kmutation scores, this study aims to develop predictive models that anticipate mutation scores shortly after test case implementation. Such models promise to streamline software testing processes, providing early insights into test suite effectiveness and guiding developers in prioritizing testing efforts.
This project aims to empirically investigate the relationship between code quality anti-patterns and mutation scores in programs implemented in the Python programming language. Ultimately the findings of this study have the potential to revolutionize software testing methodologies, enabling more efficient and reliable assessment of program correctness in Python projects.

## Literature Review

The empirical investigation into the relationship between code quality anti-patterns and mutaion scores for Python projects builds upon a rich body of literature within software engineering, particularly in the omains of code quality assessment, mutation testing, and maching learning. This section provides an overview of key studies and findings that contextualize the current research project and highlighs its significance within the broader academic discourse.

Code quality assessment has long been a focus of research within software engineering, with academic scholars exploring various metrics and techniques to evaluate software code. [Jia, Y., & Harman, M. (2011)](https://ieeexplore.ieee.org/abstract/document/5487526)conducted an extensive analysis and survey of the development of mutation testing, contributing a comprehensive set of approaches and tools to mutation testing, introducing Mutation Score for code quality evaluation. Their studies laid the groundwork for ongoing research in mutation testing methodologies.

[Davide Spadini, Palomba, F., Zaidman, A., Magiel Bruntink, & Bacchelli, A. (2018)‌](https://ieeexplore.ieee.org/abstract/document/8529832) examined the relationship between test smells and software code quality, emphasizing the impact of code smells on program maintainability and reliability. Building upon this work, [Virginio et al.(2019)](https://dl.acm.org/doi/abs/10.1145/3350768.3350775) investigated the influence of test smells on test coverage, revealing insights into the inerplay between code quality issues and test effectiveness. These studies underscore the importance of identifying and addressing code quality anti-patterns to enhance overall software quality.

[Zhu et al.(2021)](https://www.sciencedirect.com/science/article/pii/S0164121220302545) conducted an exploratory study on the impact of code observability on mutation testing, highlighting the significance of code visibility on mutation testing, highlighting the significance of code visibility in detecting faults through mutation testing. Their findings offer valuatble insights into the factores influencing mutation score outcomes and the effectiveness of mutation testing techniques.

The research by [Van-Nho Do, Quang-Vu Nguyen & Thanh-Binh Nguyen (2023)](https://www.tandfonline.com/doi/full/10.1080/24751839.2023.2252186) addresses the challenge of predicting mutation scores without the need for extensive mutation eesting, emphasizing the potential for predictive modeling to streamline the testing process. Their work aligns closely with the objectives of the current research project, demonstrating the growing interest in leveraging machine learning techniques for mutation score predictions.

## Methods

### Subject Program Selection

Python programs meeting the following criteria were selected from Github repositories: (i)Python 3.11 or higher, (ii)dependency management using poetry, (iii)test automation with Pytest, (iv)compatible with static analysis tools ([Chasten](https://github.com/AstuteSource/chasten/tree/master) and/or [Symbex](https://github.com/simonw/symbex)) and mutation testing tools ([Mutmut](https://github.com/boxed/mutmut) or [Mutatest](https://github.com/EvanKepner/mutatest)).

### Detection of Code Quality Anti-Pattern and Mutation testing

A custom program, referred to as `analyzer`, was developed within [SEERS](https://github.com/AstuteSource/SEERS), to execute static analysis tools, notably `Chasten` and mutation tool `Mutmut` on the selected subject programs (we tested this program significantly on [lazytracker](https://github.com/AstuteSource/lazytracker)). The `analyzer` program scanned the source code segments for specific anti-patterns known for their association with low code quality, collected from `Zhu et al.(2021)`. Subsequently, it parsed the Abstract Syntax Tree (AST) of the programs to correlate detected anti-patterns within the scope of individual functions.
Additionally, the `analyzer` program scanned thorugh the mutants generated by `Mutmut`, correlating them within the function scope extracted from the AST.This approach enabled a more granualar analysis of mutation scores at the function level, overcoming the limitation of per-line mutants returned by `Mutmut`.

### Unification of Data Sources

Following the execution of the `analyzer` program, the output data from `Chasten` and `Mutmut` was structured and unified into a cohesive dataset. This unified dataset, organized in a "tidy data format", included all relevant mata values essential for improving the accuracy of subsequent machine learning models.Each entry in the dataset was associated with a specific function within the subject program, and correlating mutants inserted in the function. The program then collecting `failure` mutants to return `mutation score`, per the methodology stated in the `Harman et al. (2011)` paper.

### Calculation of Statistical Correlations

The unified dataset facilitated the calculation of statistical correlations, particularly at the function level, between the count of detected code quality anti-patterns and the corresponding mutation scores. Utilizing methodologies outlined in `Zhu et al.(2021)`, correlation coefficients such as Spearman's rank correlation coefficient were computed and integrated into the unified dataset for further analysis.

### Machine Learning Model Training and Evalutation

While the statistical correlation provided initial insights, the subsequent step involved training and evaluating maching learning models to predict mutation scores based on code quality anti-patterns. However, due to time constraints, this step could not be sompleted within the timeframe of the research project. Future iterations of the study involve leveraging automated maching learning (AutoML) framewords and implementing k-fold cross-validation techniques to assess model accuracy, precision, and effectiveness using metrics such as the F1-score and Matthews correlation coefficient(MCC).

## Using the Artifact

The guide to installation and using this program exist on [SEERS/README.md](https://github.com/AstuteSource/SEERS).

**Installation**

Follow these steps to install the `chasten` program:

- Install Python 3.11 for your operating system
- Clone this repository:  `git@github.com:AstuteSource/SEERS.git`

**Analysis**

To analyze code using Comma:

1. Place the desired projects to test in the `demo` folder. Navigate into the `demo` folder in a terminal and use `git clone` to clone the desired project repositories.

2. Return to the `analyzer` folder and run the following command to install dependencies using Poetry `poetry install`

3. Once the installation is complete, execute the following command to run the analysis:

```bash
poetry run analyzer --search-path demo --save-directory subject-data --chasten-config-path Config

```

Replace the options --search-path, --save-directory, and --chasten-config-path with the desired paths where the project will be searched, files will be saved, and configuration files will be located, respectively. These should be Path objects passed in a manner similar to the example command provided above.

Once the analysis and unfication complete, the following message will pop up

```script
Code analysis and mutation complete!
Result is stored in file named combined_result.json
🧹 Final sweeping, saved to new_output_with_functions.json
```

## Results and Outcomes

The complete data exists in `new_output_with_functions.json`

The user can scan the ouput to confirm that, for instance, the mutation score for pattern named `add_files` that was inserted 3 mutants (01 survived, 02 killed) has a mutation score of roughly 66.6/100. This calculation is based on the formula `mutation_score = killed_mutants/total_mutants(both killed and survived) * 100`

```json
{
    "file": "/Users/jaclynpham/AstuteSource/SEERS/scripts/analyzer/demo/lazytracker/lazytracker/lazytracker.py",
    "pattern": {
      "lineno": 29,
      "coloffset": 4,
      "linematch": "def add_files(self, filepaths: List[str], chunk_num_blocks=128):",
      "context": "        files_to_check = sorted(files_to_check)\n\n        self.add_files(files_to_check, chunk_num_blocks)\n\n    def add_files(self, filepaths: List[str], chunk_num_blocks=128):\n        \"\"\"Include hash of files\n\n        Args:\n            filepaths (List[str]): List of paths to files\n            chunk_num_blocks (int, optional): How many chunks to read at once. Defaults to 128.",
      "min": 1,
      "max": 10,
      "pattern": ".//FunctionDef",
      "check_id": "F001",
      "check_name": "all-function-definition",
      "description": "Ensure the presence of function definitions in the codebase."
    },
    "function_name": "add_files",
    "function_scope": "29-42",
    "mutants": [
      {
        "name": "Mutant #6",
        "line": 29,
        "description": [
          "    def add_files(self, filepaths: List[str], chunk_num_blocks=128):"
        ],
        "failure": [
          {
            "inner": "--- lazytracker/lazytracker.py\n+++ lazytracker/lazytracker.py\n@@ -26,7 +26,7 @@\n \n         self.add_files(files_to_check, chunk_num_blocks)\n \n-    def add_files(self, filepaths: List[str], chunk_num_blocks=128):\n+    def add_files(self, filepaths: List[str], chunk_num_blocks=129):\n         \"\"\"Include hash of files\n \n         Args:\n",
            "type": "failure",
            "message": "bad_survived"
          }
        ]
      },
      {
        "name": "Mutant #7",
        "line": 38,
        "description": [
          "                with open(p, \"rb\") as f:"
        ],
        "failure": []
      },
      {
        "name": "Mutant #8",
        "line": 39,
        "description": [
          "                    while chunk := f.read(chunk_num_blocks * self._hasher.block_size):"
        ],
        "failure": []
      }
    ],
    "mutation_score": 66.66666666666666
}
```

This json snippet demonstrates the analysis from running `comma` on the file `lazytracker/lazytracker.py`, detecting the function name `add_files` that exist on function scope `29-42`. Mutants #6,#7,#8 were inserted in this function and one of them failed, raising this message:

```json
"failure": [
          {
            "inner": "--- lazytracker/lazytracker.py\n+++ lazytracker/lazytracker.py\n@@ -26,7 +26,7 @@\n \n         self.add_files(files_to_check, chunk_num_blocks)\n \n-    def add_files(self, filepaths: List[str], chunk_num_blocks=128):\n+    def add_files(self, filepaths: List[str], chunk_num_blocks=129):\n         \"\"\"Include hash of files\n \n         Args:\n",
            "type": "failure",
            "message": "bad_survived"
          }
        ]
```

---

## Exemplar Projects Discussions

The department's project descriptions can be found at [https://github.com/ReadyResearchers-2023-24/cmpsc-580-exemplar-projects](https://github.com/ReadyResearchers-2023-24/cmpsc-580-exemplar-projects)

## Schedule

The schedule for this work can be found at [https://github.com/CMPSC-580-Allegheny-College-Spring-2024/classDocs?tab=readme-ov-file#schedule](https://github.com/CMPSC-580-Allegheny-College-Spring-2024/classDocs?tab=readme-ov-file#schedule)