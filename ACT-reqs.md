ACT Framework Requirements
==========================

Abstract
--------

The Accessibility Conformance Testing Framework will be a W3C specification, developed by the ACT Taskforce, lead by the WCAG Working Group. This document outlines the requirements for the ACT Framework. The ACT Framework is one part of the deliverables of the ACT Taskforce, for more details on this read [[ACT Deliverables]].

Status of This Document
-----------------------

This is the first draft of this document, it has not yet had the full review of the ACT Taskforce. It is therefore likely to change significantly.


1. Introduction
---------------

There are many accessibility test tools (ATTs). These can be fully automatic, or can prompt a user for specific actions, in order to discover accessibility issues of some digital product. Each of these tools will run one, or a serie of tests to come to some result. These test procedures may be designed to look for violations of WCAG 2.0, or some other accessibility standard, and for some that are highly customizable they can even be used in testing an organization's own accessibility policy. The test procedures used by ATT are often called 'rules'.

The ACT Framework will standardize those aspects all rules have in common that ensure them to be reliable, implementable by different ATTs and transparent for the users of this tool. By standardizing this, the ACT Taskforce aims to promote a common understanding of how accessibility can be tested for certain technologies.

Simply put, the ACT Framework is a standard on how to write test rules. Rules written in conformance to the ACT Framework specification are referred to as ACT Rules. These in turn are test procedures for accessibility, that can be implemented by ATTs or used for testing of accessibility.

2. Requirements
---------------

### 2.1 Ensure Readability

The ACT Framework should ensure that the rules are readable by both tool developers and less-technical users. For instance, the ACT Framework may discourage the use of pseudo code in favor of plain English.

### 2.2 Ensure Justification

The ACT Framework should ensure that ACT Rules are well grounded in the requirements they test. It is insufficient for an ACT Rule to merely claim something violates a requirement. The ACT Framework has to ensure that ACT Rules document why its claims are a valid interpretation of the requirement.

### 2.3 Ensure Consistency

The ACT Framework has to ensure that ACT Rules can be implemented in a way that provides consistent results. An ACT Rule must include a way to test the implementation of that rule.

### 2.4 Ensure Measurable Accuracy

The ACT Framework ensures that ACT Rules can be tested for real world accuracy. False positives happen in every rule, as there are endless different ways to use web technologies. The ACT Framework ensures that common false positives can be identified and resolved. This also gives insight into how often a rule may give incorrect results.

### 2.5 Ensure Evolution

As web technologies change, the rules for testing them should change as well. Because of this it is important that ACT Framework outlines a way to deal with that. Rules should be dated and versioned, so that users of rules can understand that a rule needs to be updated. A possible approach to this could be semantic versioning, although there are many other possibilities.

### 2.6 Existing Rulesets can be Transformed to ACT Rules

The ACT Framework must ensure that existing rulesets can be updated to meet the ACT Framework. Existing work in this field should be the bases for the ACT Framework to ease the adoption. At least one ruleset must be adopted to the ACT Framework during the development process.

### 2.7 Accessibility Support

The ACT Framework ensures that ACT Rules consider difference in assistive technologies. ACT Rules can be configured to use or ignore accessibility features that are not consistently implemented. Gathering accessibility support data is outside the scope of ACT Rule design.

### 2.8 Run As Negative Feature Tests

ACT Rules are negative feature tests. Meaning they can test if some accessibility requirement is not met. Testing if such requirement was met is outside the scope of ACT Rules and should be left up to expert accessibility evaluators.


### 2.9 Provide a common output format

The ACT Framework must ensure that results from ACT Rules can be aggregated to gain higher level insight. This must be possible across tools, so that the output of different tools can complement each other. This could be particularly useful to aggregate accessibility for different technologies.

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
