ACT Framework Requirements
==========================

Abstract
--------

The Accessibility Conformance Testing (ACT) Framework is intended to become a W3C Recommendation. It is developed by the [WCAG Working Group](https://www.w3.org/WAI/GL/) through its [ACT Task Force](https://www.w3.org/WAI/GL/task-forces/conformance-testing/). This document outlines the requirements for the ACT Framework. An overview of ACT efforts including complimentary deliverables is described in [What is ACT](https://www.w3.org/WAI/GL/task-forces/conformance-testing/wiki/ACT_Overview_-_What_is_ACT).

Status of This Document
-----------------------

This is the first draft of the ACT Framework Requirements document. It has not yet been reviewed or approved by the WCAG Working Group. At this stage, input on the following aspects is requested:

- Completeness: Are there missing requirements?
- Clarity: Are the described requirements clear?
- Cohesion: Are there requirement contradictions?

1. Introduction
---------------

The Accessibility Conformance Testing (ACT) Framework will define how to write rules for accessibility conformance testing. It will standardize aspects that are common across different rules, to contribute to the development of rules that produce reliable results, are implementable by different testing and quality assurance tools, and that provide transparency and comparability for tool users. This should contribute to greater consistency of results across different tools, and avoid confusion on accessibility.

The development and implementation of ACT Rules is complementary effort to the development of this ACT Framework. ACT Rules are currently developed through the [Auto-WCAG Community Group](https://www.w3.org/community/auto-wcag/). Feedback from the development of these ACT Rules will refine the ACT Framework during its development. Over time it is expected that other organizations will develop or make their rules available in the format defined by the ACT Framework, to facilitate a scalable approach for ACT Rules development.

More background on ACT efforts and deliverables is provided in [What is ACT](https://www.w3.org/WAI/GL/task-forces/conformance-testing/wiki/ACT_Overview_-_What_is_ACT).

2. Requirements
---------------

### 2.1 Ensure Readability

The ACT Framework ensures that ACT Rules are readable by both tool developers and less-technical users. For instance, the ACT Framework may discourage the use of pseudo code in favor of plain English.

### 2.2 Ensure Justification

The ACT Framework ensures that sufficient documentation is provided, to justify that ACT Rule results are valid interpretation of the accessibility requirements.

### 2.3 Ensure Consistency

The ACT Framework ensures that ACT Rules can be implemented in a way that produces consistent results. An ACT Rule must include a way to test the implementation of that rule.

### 2.4 Ensure Measurable Accuracy

The ACT Framework provides criteria and a benchmarking mechanism to validate and measure the accuracy of ACT Rules. Note: Accuracy is difference of actual test results to expected results.

### 2.5 Ensure Evolution

The ACT Framework provides a mechanism to manage updates to ACT Rules as technologies change. ACT Rules should be dated and / or versioned to enable users to figure out if new issues are caused by a rule change or a change of content. A possible approach to this could be semantic versioning.

### 2.6 Existing Rulesets can be Transformed to ACT Rules

The ACT Framework provides support for different organizations and vendors to migrate their test rules into the required format. This may include mappings to other formats, and tolerance for different test rules structures and parameters, where possible

### 2.7 Accessibility Support

The ACT Framework ensures that ACT Rules consider difference in assistive technologies. ACT Rules can be configured to use or ignore accessibility features that are not consistently implemented. Accessibility support data is input for a rule, and is not part of the rule's design.

### 2.8 Rules Test for Failures

The ACT Framework results in negative feature tests, meaning that ACT Rules test for violations instead of compliance. ACT Rules should map to [WCAG 2.0 Failure Techniques](https://www.w3.org/TR/WCAG20-TECHS/failures.html) where possible to avoid duplication of work. In some cases absence of violations may be proof of compliance, if rules are available to test all possible violations for a requirement.

### 2.9 Provide a Common Output Format

The ACT Framework ensures that results from ACT Rules can be aggregated to gain higher level insights. This must be consistent across tools, so that the output of different tools can complement each other.

### 2.10 Rules Not Included

The ACT Framework is a W3C Recommendation on how to write rules. It does not include any ACT Rules, with the possible exception of rule examples.

### 2.11 No New Accessibility Requirements

The ACT Framework does not add or change accessibility requirements. It's purpose is to standardize the way requirements are tested. The method of testing must never change the actual requirement.

### 2.12 Automation and Manual Rules

The ACT Framework provides mechanisms to develop rules that are:

- Automated: A completely automatic process, no user is involved in the test
- Manual: A process that can only be done by a user
- Semi-automated: A test combining automated testing and manual testing

### 2.13 Useable With Different Accessibility Requirements

The ACT Framework provides mechanisms for the development of rules to test conformance to popular accessibility requirements, including but not limited to: WCAG 2.0, WCAG 2.1, UAAG 2.0 and ATAG 2.0.

### 2.14 Applicable to Web and Digital Publishing Technologies

The ACT Framework provides mechanisms for the development of rules to test current web and digital publishing technologies, including but not limited to: HTML, CSS, ARIA and EPUB.

Definitions
-----------

### Rule

A rule is the description of the procedure used to evaluate the status (pass or fail) of one ore more conditions of a requirement in a given context.

The rule defines:

* the context in which it is applicable (e.g. a set of elements in a DOM)
* a set of assumptions about the environment (e.g. the way in which technologies are used)
* a set of logical steps to carry out the procedure
* a set of possible results

### Test

A test is the application of a rule.

### Requirement

A requirement is a statement of necessity in a given domain (e.g. accessbility). It can be broken down into a set of conditions.
