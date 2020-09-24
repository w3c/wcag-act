# WCAG Ruleset Review Process

This document describes a process for reviewing, approving, and maintaining Accessibility Conformance Testing (ACT) Rules contributed to the W3C Accessibility Guidelines Working Group (AGWG) for formal publication. Such a commonly agreed upon **WCAG Ruleset** contributes to more consistent interpretation of how to test conformance to the W3C Web Content Accessibility Guidelines (WCAG), more consistent results from conformance testing, and more transparency and documentation of the testing process.

Much of the tasks in this process are delegated to ACT Task Force, which is a sub-group of AGWG. ACT TF carries out initial review and prepares proposals for AGWG, which has the final say as the maintainer of WCAG and the authoritative body for interpretation.

Organizations and individuals, **rule providers**, can submit rules to be added to the WCAG Ruleset. Submitted rules must conform to the ACT Rules Format 1.0 specification and be accompanied by real-life implementations (specific criteria detailed later in this document). **Rule providers are expected to only contribute complete rules, as accurate as the rule providers can possibly make them.**

## Rule Review

When proposing a new rule, or an update to a rule, there are four steps to go through:

1. **Submitting**: The rule provider submits a rule to ACT Task Force
2. **Surveying**: The ACT Task Force reviews the rule through a survey
3. **Approving**: The ACT Task Force prepares a proposal for AGWG

The ACT Task Force will not edit rule contents. This is to avoid creating forks, where two versions of a rule are worked on in parallel, potentially with conflicts. Where necessary, the ACT Task Force will propose changes to the rule but not put those changes in.

### Submitting

The rule provider creates an issue in the [ACT GitHub repository](https://github.com/w3c/wcag-act/issues). The issue must include the following information:

1. URL of the rule
2. License of the rule
3. Information about any [implementations](#implementations)

### Surveying

A facilitator of the ACT Task Force creates a survey for the rule, in which Task Force members are asked the following questions:

- Does the rule follow the ACT Rules Format 1.0?
- Is the rule up to date?
- Are the assumptions acceptable?
- Is the implementation data correct?
- Is the rule consistent with existing WCAG documents?
- Are there any remaining open issues for this rule that were opened prior to this review?
- Do you have any further questions or concerns about this rule?
- Do you think this rule is ready to be published?

This survey will be open for at least 5 work days, to give ACT Task Force members sufficient time to review the rule. No more than 5 rule surveys will be due in the same week.

If the rule does not pass this step, the liaison has 5 work days to put the feedback in the issue for the proposal using the template in appendix 1. If changes are editorial in nature, and the rule provider can resolve those within 5 work days, the rule will be surveyed again straight away. If not, the proposal will be closed by a TF facilitator. Proposals can always be resubmitted, which will restart the process from step 1. This puts the proposal on the bottom of the backlog.

### Approving

When a rule passes the review stage, it is included in a draft version of the WCAG Ruleset. Depending on the types of changes and the availability of the Accessibility Guidelines (AG) Working Group, the ACT Task Force decides on a timeline for releasing updates to the WCAG Ruleset. To update the WCAG Ruleset, the ACT Task Force requests approval from the AG Working Group. The AG Working Group will have its own process for deciding whether or not to publish the next version of the WCAG Ruleset. For example, AG may decide to have Call For Concensus e-mail or send out a survey.

## Minor Updates

Once a rule has been included in the (draft) WCAG ruleset, the rule provider can submit minor changes in a pull request directly to the draft. The ACT Task Force must decide on a call whether the changes need to be surveyed, following the [rule review process](#rule-review), or if it can be merged directly into the draft ruleset. This requires a 48 hour call for concensus, except if the update is purely editorial.

## Public Feedback

Public feedback received on the WCAG Ruleset is processed by the ACT Task Force. Questions or issues can either be submitted directly into the ACT Task Force GitHub repository, or be copied into GitHub issues from questions sent to the ACT public mailing list.

Questions the ACT Task Force can answer will be responded to directly. Questions that may require updates to a rule will be forwarded to the rule provider, including a proposal from the ACT Task Force on how to resolve the question. If the rule provider uses the proposal without additional changes, the rule will be updated without having to go through the review process. The rule provider should still apply their own review process to the change. If a different solution is taken, or additional changes are made, the update will have to go through the review process.

For the ACT Task Force agenda, public feedback will be prioritised over review of proposed rules. This ensures responsiveness to the wider community. The ACT Task Force should respond to questions within 5 work days. This may be a reply in which they defer to the rule provider for a solution.

## Annual Review

Since technologies and standards frequently change, rules require regular maintenance. To ensure quality over time, the ACT Task Force will review every rule in the WCAG Ruleset at least once a year, to ensure it is still current and correct. If any changes are deemed necessary, the ACT Task Force proposes an update to the rule to the original rule provider. If the change is taken up without further updates, the update is accepted without review.

Every time a rule is surveyed, it is checked to make sure it is up to date. This survey counts as an annual review, so that only rules that have not been surveyed in 12 months need to go through a separate review. If a rule has not been reviewed for 12 months, an ACT facilitator opens an issue for it, and assigns it to that rule's liaison. The liason is has 10 work days to review if the rule needs to be updated. If the rule needs to be updated, the liaison has another 10 work days to propose any necessary changes to the rule provider.

## Orphaned Rules

The ACT Task Force will send a request for change to a rule provider as a result of either public feedback or an annual review. If the rule provider does not respond within two months, the ACT Task Force will assume the rule is no longer actively maintained. The ACT Task Force will send at least 2 reminders before concluding the rule is not maintained. If a rule is not maintained, the ACT Task Force will look for another organization who might be willing to maintain the rule. If the original rule provider wishes to resume maintenance of the rule, this will only be accepted with the permission of the active rule provider.

If no one can be found to maintain a rule within a month, the rule will be labelled as "outdated". Outdated rules will be removed from the ruleset after 1 year.

## Rule Provider Questions

Often when writing rules, rule providers have questions about the intended meaning of WCAG success criteria. The ACT Task Force will keep track of such questions coming from rule providers using GitHub issues and will work with the AG Working Group to come up with answers to them. Response to questions is subject to the availability of AG, therefore, so there is no target time frame for a response.

## Implementations

An implementation is either a rule in an accessibility testing tool, or a procedure in a testing methodology. Implementations show that the ACT rule works in practice, and that the interpretation made by the rule is one that is used in real-world accessibility testing. Because of this, having more implementations, or having an implementation that has a lot of users weighs heavily in demonstrating that the assumptions and interpretation in the rule are acceptable to the accessibility community.

An implementation must be correct. This is determined by running the tool or methodology on the test cases provided in the rule. Acknowledging that not all implementors distinguish between "passed" and "inapplicable", and that semi-automated tools can return "cantTell" as a result, an implementation is considered correct when it gets one of the allowed outcomes for all of the test cases:

| Test Case Type | Allowed outcomes                        |
| -------------- | --------------------------------------- |
| Passed         | `passed`, `cantTell`, or `inapplicable` |
| Failed         | `failed` or `cantTell`                  |
| Inapplicable   | `inapplicable`, `cantTell`, or `passed` |

Before the ACT Task Force can publish rules, at minimum one full implementation is required. Rule authors that want their ACT rules considered for publication by the Accessibility Guidelines Working Group must provide the following information for at least one accessibility testing tool or testing methodology:

1. An overview of the expected and actual outcomes when the tool / methodology is used on the test cases in the rule.

2. The test mode of the implementation of the rule. A test mode can be one of the following:
    - **fully automated**: The outcome of all test cases in the rule was derived without human input
    - **semi-automated**: The outcome of some test cases in the rule was derived without human input
    - **manual**: The outcome of all of the test cases in the rule was derived with human input

3. If the test mode of the implementation was _manual_ or _semi-automated_, a declaration of the implementor that these manual outcomes are the result of a documented step by step test procedure included in the implementation.

Additionally, when submitting the rule, the following requirements must be met:

1. There must be at least one implementation that for all passed and inapplicable test cases reports a pass or inapplicable outcome, and that for all failed test cases reports a failed outcome.

2. All input rules of a composite rule must also have at least one implementation for which the previous requirement is true.


## Apendix 1: Feedback template

The liaison must curate the feedback. Ensure it is clear and remove any duplicates.

```md
[link to the survey results](...)
[link to the minutes from TF](...)

## {{ name of TF member }}

- [ ] {{ Text from survey }}
- [ ] {{ Text from survey }}

## {{ name of TF member }}
 
- [ ] ...
```
