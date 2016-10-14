ACT Framework Requirements
==========================

Abstract
--------

The Accessibility Conformance Testing Framework will be a W3C Recommendation, developed by the ACT Taskforce, lead by the WCAG Working Group. This document outlines the requirements for the ACT Framework. The ACT Framework is one part of the deliverables of the ACT Taskforce, for more details on this read [[ACT Deliverables]].

Status of This Document
-----------------------

This is the first draft of this document. It has not yet been submitted for formal review to the WCAG Working Group.

1. Introduction
---------------

The Accessibility Conformance Testing (ACT) Framework will be a recommendation on how to write rules for accessibility conformance testing. For an introduction on Accessibility Conformance Testing, read [What is ACT](https://www.w3.org/WAI/GL/task-forces/conformance-testing/wiki/ACT_Overview_-_What_is_ACT).

The ACT Framework is developed by the [ACT Taskforce](https://www.w3.org/WAI/GL/task-forces/conformance-testing/), lead by the [WCAG Working Group](https://www.w3.org/WAI/GL/). The ACT Framework will standardize those aspects all rules have in common that ensure them to be reliable, implementable by different ATTs and transparent for the users of this tool. By standardizing this, the ACT Taskforce aims to promote a common understanding of how accessibility can be tested for certain technologies.

Development and implementation of ACT Rules are outside the scope of the ACT Framework. This work is currently done within the [Auto-WCAG Community Group](https://www.w3.org/community/auto-wcag/). The ACT Taskforce support the Auto-WCAG Community group in the development of the first set of ACT Rules.

2. Requirements
---------------

### 2.1 Ensure Readability

The ACT Framework ensures that the rules are readable by both tool developers and less-technical users. For instance, the ACT Framework may discourage the use of pseudo code in favor of plain English.

### 2.2 Ensure Justification

The ACT Framework ensures that sufficient documentation is provided, to justify that it's claims are a valid interpretation of the accessibility requirement.

### 2.3 Ensure Consistency

The ACT Framework ensures that ACT Rules can be implemented in a way that produces consistent results. An ACT Rule must include a way to test the implementation of that rule.

### 2.4 Ensure Measurable Accuracy

The ACT Framework provides criteria and a benchmarking mechanism to validate and measure the accuracy of test rules. Note: Accuracy is difference of actual test results to expected results.

### 2.5 Ensure Evolution

The ACT Framework provides a mechanism to manage updates to rules as technologies change. Rules should be dated and / or versioned to enable users to figure out if new issues are caused by a rule change or a change of content. A possible approach to this could be semantic versioning.

### 2.6 Existing Rulesets can be Transformed to ACT Rules

The ACT Framework provides support for different organizations and vendors to migrate their test rules into the required format. This may include mappings to other formats, and tolerance for different test rules structures and parameters where possible

### 2.7 Accessibility Support

The ACT Framework ensures that ACT Rules consider difference in assistive technologies. ACT Rules can be configured to use or ignore accessibility features that are not consistently implemented. Accessibility support data is input for a rule, and is not part of the rule's design.

### 2.8 Rules Test for Failures

The ACT Framework results in negative feature tests, meaning that ACT Rules test for violations instead of compliance. ACT Rules should map to [WCAG 2.0 Failure Techniques](https://www.w3.org/TR/WCAG20-TECHS/failures.html) where possible to avoid duplication of work. In some cases absence of violations may be proof of compliance, if rules are available to test all possible violations.

### 2.9 Provide a Common Output Format

The ACT Framework ensures that results from ACT Rules can be aggregated to gain higher level insight. This must be possible across tools, so that the output of different tools can complement each other.

### 2.10 Rules Not Included

The ACT Framework is a recommendation on how to write rules. It does not include any ACT Rules, with the possible exception of rule examples.

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
