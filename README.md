[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/Y4rZMh1t)
# Junior Seminar (CMPSC 580) Exemplar Project Repository

## Semester: Spring 2024

This repository contains student project materials, including project report, data, code, and references to literature for this departmentally-sponsored project. __As you complete each of the below sections in this document, please be sure to remove the preamble text so that it does not appear in your work.__ Please work with your first reader to answer any questions or concerns that you may have.

## GitHub Handle: jaclynpqc

## Name: Jaclyn Pham

## Major: Software Engineering

## Project Name: SEERS: Empirically Studying the Relationship between Code Quality Aniti-Patterns and Mutation Score for Python Projects

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

TODO: Discuss the methods of the project to be able to answer the `how` question (`how was this project completed?`). The methods section in an academic research outlines the specific procedures, techniques, and methodologies employed to conduct the study, offering a transparent and replicable framework for the research. It details the resources behind the work, in terms of, for example, the design of the algorithm and the experiment(s), data collection methods, applied software libraries, required tools, the types of statistical analyses and models which are applied to ensure the rigor and validity of the study. This section provides clarity for other researchers to understand and potentially replicate the study, contributing to the overall reliability and credibility of the research findings.

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

While the statistical correlation provided initial insights, the subsequent step involved training and evaluating maching learning models to predict mutation scores based on code quality anti-patterns. H



## Using the Artifact

TODO: The result of your work will be the delivery of some type of artifact which will likely contain software programming solutions (i.e., Python code, HTML pages, or similar). To allow the user to experience and execute your artifact, you must first explain how to set up the initial conditions to run or use the artifact. Be sure to offer explicit details and instructions regarding the installation of the necessary foundational libraries, drivers, external software projects, containers and similar types of tertiary software which are involved in executing your artifact. Once these initial software installations have been completed, then you are asked to offer the necessary instructions for actually executing the artifact. For this, please provide all command line parameters or associated bash commands for execution. Please remember that users are unwilling to "figure-out" how to use code in absence of the essential instructions concerning the execution of project artifacts.

## Results and Outcomes

TODO: Discuss the outcomes of your project in this section. Depending on the project type, the presented results and outcomes will vary. In some projects, you will be asked to present a theoretical analysis, and in others your experimental study and its results. In this section, you are also to demonstrate an enhanced version of your artifact by showing its capabilities and applications, in light of the evaluation metrics for assessing the artifact

---

## Exemplar Projects Discussions

The department's project descriptions can be found at [https://github.com/ReadyResearchers-2023-24/cmpsc-580-exemplar-projects](https://github.com/ReadyResearchers-2023-24/cmpsc-580-exemplar-projects)

## Schedule

The schedule for this work can be found at [https://github.com/CMPSC-580-Allegheny-College-Spring-2024/classDocs?tab=readme-ov-file#schedule](https://github.com/CMPSC-580-Allegheny-College-Spring-2024/classDocs?tab=readme-ov-file#schedule)