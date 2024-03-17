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

When software engineers work on developing a new software or incorporate new functions into a program, they often lack the certainty of testing that function. Additionally, the unpredictability of whether test ases effectively assess the program's correctness poses a challenge. Mutation testing is a systematic approach involving the intentional introduction of defects into a program, followed by multiple runs of the test suits. If the test suite fails to identify seeded defects, it indicates ineffectiveness. However, despite its informativeness, mutation testing is computationally expensive, leading to the limitation of effective test suite.

Recognizing this gap in practice, there is a need for a tool that can predict the likely mutation score soon after implementing a test case for a function. This project aims to empirically investigate the relationship between code quality anti-patterns and mutation scores in programs implemented in the Python programming language.

## Literature Review

The empirical investigation into the relationship between code quality anti-patterns and mutaion scores for Python projects builds upon a rich body of literature within software engineering, particularly in the omains of code quality assessment, mutation testing, and maching learning. This section provides an overview of key studies and findings that contextualize the current research project and highlighs its significance within the broader academic discourse.

[Zhu2021.pdf](https://www.sciencedirect.com/science/article/pii/S0164121220302545)

[Van-Nho Do, Quang-Vu Nguyen & Thanh-Binh Nguyen (2023)](https://www.tandfonline.com/doi/full/10.1080/24751839.2023.2252186)

[Jia, Y., & Harman, M. (2011)](https://ieeexplore.ieee.org/abstract/document/5487526)

[Davide Spadini, Palomba, F., Zaidman, A., Magiel Bruntink, & Bacchelli, A. (2018)‌](https://ieeexplore.ieee.org/abstract/document/8529832)

[Virginio(2019)](https://dl.acm.org/doi/abs/10.1145/3350768.3350775)


## Methods

TODO: Discuss the methods of the project to be able to answer the `how` question (`how was this project completed?`). The methods section in an academic research outlines the specific procedures, techniques, and methodologies employed to conduct the study, offering a transparent and replicable framework for the research. It details the resources behind the work, in terms of, for example, the design of the algorithm and the experiment(s), data collection methods, applied software libraries, required tools, the types of statistical analyses and models which are applied to ensure the rigor and validity of the study. This section provides clarity for other researchers to understand and potentially replicate the study, contributing to the overall reliability and credibility of the research findings.

(modify this)
Basically, the mutation testing process is started when the programme under test is confirmed to be bug-free, through execution on the test suite which has been built specifically for that programme. And then , the mutation testin process has the following three main steps:

* Step 1: Proceed to generate mutants, which are variations of the origina programmer. Each of these variants has one modification or multiple modifications from the original programme
* Step 2: Execcute, in turn, the original programe and all its mutats against a given set of test cases. The computational cost of mutation testing is very high due to the executions in this step.
* Step 3: Calculate the mutation score (MS or MSI) and then evaluate the quality of the given set of test cases based on the mutation score. The mutation score value lies from 0 to 1. A mutation score of 1 is ideal, meaning that all changing in the original programme are detected.

In this paper [Van-Nho Do, Quang-Vu Nguyen & Thanh-Binh Nguyen (2023)](https://www.tandfonline.com/doi/full/10.1080/24751839.2023.2252186), they propose the research problem as to how can calculate (predict the mutation score) without performing the above-mentioned second step. This will lead to a reduction in execution time and computational cost but still ensure the effectiveness of mutation testing as expected.

The study use Mutpy for mutation testing for software written in Python langauge. Besides, Scikit-learn library is aslo used in the experiement since it is considered as the most powerful library for machine learning algorithms written by Python progrmaming language.
In the experiment, they used the following algorithms to train the model and predict which mutants will be killed. Logistic Regression algoritm, Random Forest, XGBoost, LightGBM

## Using the Artifact

TODO: The result of your work will be the delivery of some type of artifact which will likely contain software programming solutions (i.e., Python code, HTML pages, or similar). To allow the user to experience and execute your artifact, you must first explain how to set up the initial conditions to run or use the artifact. Be sure to offer explicit details and instructions regarding the installation of the necessary foundational libraries, drivers, external software projects, containers and similar types of tertiary software which are involved in executing your artifact. Once these initial software installations have been completed, then you are asked to offer the necessary instructions for actually executing the artifact. For this, please provide all command line parameters or associated bash commands for execution. Please remember that users are unwilling to "figure-out" how to use code in absence of the essential instructions concerning the execution of project artifacts.

## Results and Outcomes

TODO: Discuss the outcomes of your project in this section. Depending on the project type, the presented results and outcomes will vary. In some projects, you will be asked to present a theoretical analysis, and in others your experimental study and its results. In this section, you are also to demonstrate an enhanced version of your artifact by showing its capabilities and applications, in light of the evaluation metrics for assessing the artifact

---

## Exemplar Projects Discussions

The department's project descriptions can be found at [https://github.com/ReadyResearchers-2023-24/cmpsc-580-exemplar-projects](https://github.com/ReadyResearchers-2023-24/cmpsc-580-exemplar-projects)

## Schedule

The schedule for this work can be found at [https://github.com/CMPSC-580-Allegheny-College-Spring-2024/classDocs?tab=readme-ov-file#schedule](https://github.com/CMPSC-580-Allegheny-College-Spring-2024/classDocs?tab=readme-ov-file#schedule)