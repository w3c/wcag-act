# ACT Publication Process

This document describes a process for writing, reviewing, approving, and maintaining Accessibility Conformance Testing (ACT) Rules for formal publication by the W3C Accessibility Guidelines Working Group (AGWG). Such a commonly agreed upon WCAG Ruleset contributes to more consistent interpretation of how to test conformance to the W3C Web Content Accessibility Guidelines (WCAG), more consistent results from conformance testing, and more transparency and documentation of the testing process.

Much of the tasks in this process are delegated to ACT Task Force (ACT TF), which is a sub-group of AGWG. ACT TF carries out initial review and prepares proposals for AGWG, which has the final say as the maintainer of WCAG and the authoritative body for interpretation.

Rule writing, reviewing, approving, and maintaining is a joint work between the ACT TF and the ACT Rules Community Group through regular joint meetings. Any other groups interested in contributing rules to the WCAG ruleset should contact the co-facilitator(s) of the ACT Task Force. The ACT publication process is designed to publish high-quality ACT rules to the W3C website. 

## ACT Publication steps

When creating a new rule, or updating a rule, there are five steps to go through. This process involves the combined effort of the ACT Task Force and the ACT Rules Community Group. 

1. Draft proposal
2. Call for review
3. Call for implementation
4. Validation
5. Publication approval

### 1. Draft proposal

New rules, and changes to rules are made through GitHub pull requests. Any member of either ACT group can author such a pull request. A pull request must have approval from three independent reviewers before it can proceed to step 2. These reviewers can not work for the same organization, and must not have been involved in writing the pull request. 

The pull request description must include information on the type of change the pull request makes and what happens in the "call for review" phase. There are three options:

1. New rules and significant changes that impact multiple rules should have a **two week** call for review.
2. Updates to rules, and changes to definitions used in a small number of rules have a **one week** call for review.
3. Editorial changes, including minor changes to test cases can **skip** call for review.

### 2. Call for review

Once a pull request has the necessary approvals, the author of the pull request sends an e-mail to the ACT Rules Community Group mailing list with the text "[for review]" in the subject. The e-mail must include a link to the pull request, and an indication of the duration and end date of the call for review. 

1. If no changes are requested on the pull request during the review period, the author is free to merge the pull request. 
2. Otherwise, the author must resolve the requested changes. A comment is resolved when the updated pull request is  approved by the original commenter, and at least two other reviewers. This can happen during or after the call for review. Depending on the change, one of the following happens:
    1. If the changes are editorial, the pull request can be merged any time after the review period.
    2. If the changes are not editorial, create a new [draft proposal](#1-draft-proposal), followed by a **one week** call for review.

### 3. Call for implementation

When a pull request is merged, the rule is published on the WAI website with a clear indicator that the rule, or the update to the rule is a "proposal". Additionally, metadata for the rule is published, so that implementors of ACT rules can create an implementation report for the proposed rule.

When there is at least **one complete implementation** of the rule, the proposal can proceed to the validation phase. See [complete implementations](#complete-implementations).

### 4. Validation

Once the proposal has a complete implementation, a facilitator of the ACT Task Force creates a survey for the rule, in which Task Force and Community Group members are asked the following questions:

- Does the rule follow the ACT Rules Format 1.0?
- Is the rule up to date?
- Are the assumptions acceptable?
- Is the rule consistent with existing accessibility standards?
- Are there any remaining open issues for this rule that were opened prior to this review?
- Do you have any further questions or concerns about this rule?
- Do you think this rule is ready to be published?

This survey will be open for at least 5 work days, to give ACT Task Force members sufficient time to review the rule. No more than 5 rule surveys will be due in the same week.

To go to the next step, the survey must include 5 approvals to publish, and no objections. If the survey shows changes are needed to the rule, a liaison is picked for the rule, who is responsible for drafting a proposal (step 1) to update the rule. If available, the liaison for a rule is one of the rule's authors. The liaison has 5 work days to create a [draft proposal](#1-draft-proposal) that is ready for reviewers.

If the precise changes are editorial (to be approved in step 1), and are pre-agreed on by all participants in the survey, the updated change will skip the validation stage. This has to be recorded as a decision in meeting minutes of the ACT Task Force.

### 5. Publication Approval

Once a rule is validated, an ACT TF facilitator will request that AG approve the rule. These requests can be grouped, and handled as a batch. This is decided between the ACT facilitator(s) and the AG chairs. The AG Working Group will have its own process for deciding whether or not to publish updates to the WCAG Ruleset. For example, AG may decide to have Call For Consensus e-mail or send out a survey.

Based on the feedback from AG, one of three things can happen:

1. If AG approves the changes, the rule is republished on the WAI website with the "proposal" indicator removed (i.e. it is published as an approved rule).

2. If AG requests editorial changes, a [draft proposal](#1-draft-proposal) is created by an ACT facilitator. Once merged, the updated rule is republished on the WAI website with the "proposal" indicator removed. This skips the implementations or validation steps.

3. If AG requests non-editorial, the liaison is tasked to create a [draft proposal](#1-draft-proposal).

## Public Feedback

Public feedback received on the WCAG Ruleset is processed by the ACT Task Force. Questions or issues can either be submitted directly into the ACT Task Force GitHub repository, or be copied into GitHub issues from questions sent to the ACT public mailing list.

Wherever possible, the ACT Task Force will work with the ACT Rules Community Group to come up with a joint answer to the questions. If the comment is about a proposed rule, or a proposed change to a rule a public issue is created, and an answer is sent referencing the issue. If the comment is on an approved rule and changes are necessary, a liaison is picked, and the change request is handled as survey feedback, starting in the [validation](#4-validation) step. 

For the ACT Task Force agenda, public feedback will be prioritised over review of proposed rules. This ensures responsiveness to the wider community. The ACT Task Force should respond to questions within 5 work days. This may be a brief reply that indicates when a full response is expected.

## Annual Review

Since technologies and standards frequently change, rules require regular maintenance. To ensure quality over time, the ACT Task Force will review every **approved rule** in the WCAG Ruleset at least once a year, to ensure it is still current and correct. If any changes are deemed necessary, a liaison is picked and the change request is handled as survey feedback, starting in the [validation](#4-validation) step. 

Every time a rule is [validated](#4-validation), it is checked to make sure it is up to date. This counts as an annual review, so that only rules that have not been surveyed in 12 months need to go through a separate review. If a rule has not been reviewed for 12 months, an ACT facilitator opens an issue for it, and assigns it to that rule's liaison. The liaison has 10 work days to review if the rule needs to be updated. If the rule needs to be updated, the liaison has another 10 work days to create a [draft proposal](#1-draft-proposal).

## Implementations

An implementation is either a rule in an accessibility testing tool, or a procedure in a testing methodology. Implementations show that the ACT rule works in practice, and that the interpretation made by the rule is one that is used in real-world accessibility testing. Because of this, having more implementations, or having an implementation that has a lot of users weighs heavily in demonstrating that the assumptions and interpretation in the rule are acceptable to the accessibility community.

An implementation must be correct. This is determined by running the tool or methodology on the test cases provided in the rule. Acknowledging that not all implementors distinguish between "passed" and "inapplicable", and that semi-automated tools can return "cantTell" as a result, an implementation is considered correct when it gets one of the allowed outcomes for all of the test cases:

| Test Case Type | Allowed outcomes                        |
| -------------- | --------------------------------------- |
| Passed         | `passed`, `cantTell`, or `inapplicable` |
| Failed         | `failed` or `cantTell`                  |
| Inapplicable   | `inapplicable`, `cantTell`, or `passed` |

Before an ACT rule is approved, at minimum one full implementation is required. The following information must be provided for at least one accessibility testing tool or testing methodology:

1. An overview of the expected and actual outcomes when the tool / methodology is used on the test cases in the rule.

2. The test mode of the implementation of the rule. A test mode can be one of the following:
    - **fully automated**: The outcome of all test cases in the rule was derived without human input
    - **semi-automated**: The outcome of some test cases in the rule was derived without human input
    - **manual**: The outcome of all of the test cases in the rule was derived with human input

3. If the test mode of the implementation was _manual_ or _semi-automated_, a declaration of the implementor that these manual outcomes are the result of a documented step by step test procedure included in the implementation.

## Complete implementations

An implementation is considered to be "complete" when the following requirements are met:

1. There must be at least one implementation that for all passed and inapplicable test cases reports a pass or inapplicable outcome, and that for all failed test cases reports a failed outcome.

2. All input rules of a composite rule must also have at least one implementation for which the previous requirement is true.

## Editorial Changes

Parts of the process can be bypassed when changes are editorial. If the author believes a change is editorial, this must be indicated in the pull request description. If there is disagreement with the reviewers about this, a change should not be considered editorial. Use the following indicators to decide if a change is editorial:

- An editorial change does not add new content. New expectations, test cases, assumptions, accessibility support cases, background info, etc. are not editorial.
- Editorial changes do not change the meaning of the rule, except if for issues where the intended meaning is obvious, such as typos in role names
- Test cases are not changed, except for trivial fixes that are unlikely to impact an implementation.

## Liaisons

A liaison is a member of the ACT TF or CG, appointed to for specific rule maintenance activities. Preferably this is one of the authors of the rule.
