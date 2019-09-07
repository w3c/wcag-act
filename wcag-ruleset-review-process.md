# WCAG Ruleset Review Process

The Accessibility Conformance Testing (ACT) Rules Format 1.0 is intended to enable a consistent interpretation of how to test conformance to the Web Content Accessibility Guidelines (WCAG) and other accessibility requirements documents. The W3C is working to establish a commonly agreed upon set of ACT Rules for WCAG, called the **WCAG Ruleset**, to help organizations produce more consistent results for testing WCAG conformance. The **WCAG Ruleset** is published by the Accessibility Conformance Working Group (AGWG) through the efforts of the ACT Task Force.

Organizations can contribute rules to the WCAG Ruleset by submitting them to the ACT Task Force. These organizations are called **rule providers**. The ACT Task Force reviews rules proposed by rule providers to decide whether or not the rules are good candidates to be included in the WCAG Ruleset. The AGWG is the final approver of the rules and, once approved, the rules are published in the WCAG supporting documentation.

When a rule is submitted to the ACT Task Force, the Task Force expects it to be as complete and as accurate as the rule provider can possibly make it. **Rule providers are expected to have their own review and quality assurance processes in place.**

## Proposing And Updating A Rule

When proposing a new rule, or an update to a rule, there are four steps to go through:

1. **Proposal**: The rule provider creates an issue
2. **Screening**: The ACT Task Force facilitators do an initial review
3. **Survey**: The ACT Task Force reviews the rule through a survey
4. **Publication**: The ACT Task Force submits the updated rule to the AG WG for publication

Updates to rules can only be done by the rule provider. This is to avoid creating forks, where two versions of a rule are worked on independently, potentially with conflicts. This also applies to the ACT Task Force, which can propose changes to the rule, but not put those changes in.

### Proposal

The rule provider creates an issue in the [ACT GitHub repository](https://github.com/w3c/wcag-act/issues). The issue must include the following information:

1. URL of the rule
2. License of the rule
3. Information about any [implementations](#implementations)

### Screening

One member of the ACT Task Force, usually an editor or facilitator, reviews the proposal for major inaccuracies in the rule. The purpose is to avoid spending reviewer time on obvious oversights. The person screening the rule can not be involved in the original creation of the rule.

If the rule does not pass this step, one of the ACT TF facilitators will send the feedback to the rule provider. If changes are editorial in nature, and the rule provider can resolve those within 5 work days, the rule will be screened again straight away. If not, the proposal will be closed. Proposals can always be resubmitted, which restarts the process from step 1. This puts the rule proposal on the bottom of the backlog.

### Survey

A facilitator of the ACT Task Force creates a survey for the rule, in which Task Force members are asked the following questions:

- Does the rule follow the ACT Rules Format 1.0?
- Are the assumptions acceptable?
- Is the implementation data correct?
- Is the rule consistent with existing WCAG documents?
- Are there any remaining open issues for this rule that were opened prior to this review?
- Do you have any further questions or concerns about this rule?
- Do you think this rule is ready to be published?

This survey will be open for at least 5 work days, to give ACT Task Force members sufficient time to review the rule. No more than 5 rule surveys will be due in the same week.

If the rule does not pass this step, one of the ACT facilitators will send the feedback to the rule provider. If changes are editorial in nature, and the rule provider can resolve those within 5 work days, the rule will be surveyed again straight away. If not, the proposal will be closed. Proposals can always be resubmitted, which will restart the process from step 1. This puts the proposal on the bottom of the backlog.

### Publication

When a rule passes the review stage, it is included in a draft version of the WCAG Ruleset. Depending on the types of changes and the availability of the Accessibility Guidelines (AG) Working Group, the ACT Task Force decides on a timeline for releasing updates to the WCAG Ruleset. To update the WCAG Ruleset, the ACT Task Force requests approval from the AG Working Group. The AG Working Group will have its own process for deciding whether or not to publish the next version of the WCAG Ruleset. For example, AG may decide to have Call For Concensus e-mail or send out a survey.

## Public Feedback

Public feedback received on the WCAG Ruleset is processed by the ACT Task Force. Questions or issues can either be submitted directly into the ACT Task Force GitHub repository, or be copied into GitHub issues from questions sent to the ACT public mailing list.

Questions the ACT Task Force can answer will be responded to directly. Questions that may require updates to a rule will be forwarded to the rule provider, including a proposal from the ACT Task Force on how to resolve the question. If the rule provider uses the proposal without additional changes, the rule will be updated without having to go through the review process. The rule provider should still apply their own review process to the change. If a different solution is taken, or additional changes are made, the update will have to go through the review process.

For the ACT Task Force agenda, public feedback will be prioritised over review of proposed rules. This ensures responsiveness to the wider community. The ACT Task Force should respond to questions within 5 work days. This may be a reply in which they defer to the rule provider for a solution.

## Annual Review

Since technologies and standards frequently change, rules require regular maintenance. To ensure quality over time, the ACT Task Force will review every rule in the WCAG Ruleset at least once a year, to ensure it is still current and correct. If any changes are deemed necessary, the ACT Task Force proposes an update to the rule to the original rule provider. If the change is taken up without further updates, the update is accepted without review.

## Orphaned Rules

The ACT Task force will send a request for change to a rule provider as a result of either public feedback or an annual review. If the rule provider does not respond within two months, the ACT Task Force will assume the rule is no longer actively maintained. The ACT Task Force will send at least 2 reminders before concluding the rule is not maintained. If a rule is not maintained, the ACT Task Force will look for another organization who might be willing to maintain the rule. If the original rule provider wishes to resume maintenance of the rule, this will only be accepted with the permission of the active rule provider.

If no one can be found to maintain a rule within a month, the rule will be labelled as "outdated". Outdated rules will be removed from the ruleset after 1 year.

## Rule Provider Questions

Often when writing rules, rule providers have questions about the intended meaning of WCAG success criteria. The ACT Task Force will keep track of such questions coming from rule providers using GitHub issues and will work with the AG Working Group to come up with answers to them. Response to questions is subject to the availability of AG, therefore, so there is no target time frame for a response.

## Implementations

An implementation is either an accessibility testing tool, or a testing methodology. Implementations show that the ACT rule works in practice, and that the interpretation made by the rule is one that is used in real-world accessibility testing. Because of this, having more implementations, or having an implementation that has a lot of users weighs heavily in demonstrating that the assumptions and interpretation in the rule are acceptable to the accessibility community.

An implementation must be correct. This is determined by running the tool or methodology on the test cases provided in the rule. Acknowledging that not all implementors distinguish between "passed" and "inapplicable", and that semi-automated tools can return "cantTell" as a result, an implementation is considered correct when it gets one of the allowed outcomes for all of the test cases:

| Test Case Type | Allowed outcomes                        |
| -------------- | --------------------------------------- |
| Passed         | `passed`, `cantTell`, or `inapplicable` |
| Failed         | `failed` or `cantTell`                  |
| Inapplicable   | `inapplicable`, `cantTell`, or `passed` |
