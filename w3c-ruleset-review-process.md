# ACT Review Process

This ACT Rules Format is intended to enable a consistent interpretation of how to test conformance to WCAG and other accessibility requirements documents. The W3C is looking to establish a commonly agreed upon set of ACT Rules, to help organisations across the field of web accessibility to produce consistent test results. This is the W3C Ruleset, which is maintained by the ACT Task Force.

Organisations looking to contribute rules to the WCAG Ruleset can submit rules to the ACT Task Force. The ACT Task Force will review any rules that have been proposed, and decided whether or not it can be included in W3C Ruleset.

When a rule is submitted to the ACT Task Force, the Task Force expects for that rule to be as complete and as accurate as the rule author can possibly make it. Organisations creating rules are expected to have their own review and quality assurance processes in place. 

## Proposing And Updating A Rule

When proposing a new rule, or an update to a rule, there are four steps to go through:

1. **Proposal**: The rule author creates an issue
2. **Screening**: The ACT Task Force chairs do an initial review
3. **Survey**: The ACT Task Forces reviews the rule through a survey
5. **Publication**: The ACT Task Force submits an updated to the complete ruleset to AG

Updates to rules can only be done by the original rule author. This is to avoid creating forks, where two versions of a rule are worked on independently, potentially with irreconcilable conflicts. This also applies to the ACT Task Force, which will not be updating rules, leaving this work up to the original author.

### Proposal

The rule author creates an issue on the [ACT Github repository](https://github.com/w3c/wcag-act/issues). The issue must include the following information:

1. A URL to the rule
2. A summary of the rule
3. License of the rule (rules MUST be in the public domain)
4. Information about any [implementations](#implementations)

### Screening

One member of the ACT Task Force, usually the editor or facilitator, reviews the proposal for any major inaccuracies in the rule. The purpose is to avoid spending reviewer time on obvious oversights. The person screening the rule can not be involved in the original creation of the rule.

If the rule does not pass this step, one of the ACT facilitators send the feedback to the rule author. The rule author will have 5 work days to correct any reported issues. If not, the issue will be closed. Issues can always be reopened, which will restart the process from step 1.

### Survey

The facilitators of the ACT Task Force create a survey for the rule, in which members are asked the following questions:

- Does the rule follow the ACT Rules Format 1.0?
- Are the assumptions acceptable?
- Is the implementation data correct?
- Is the rule consistent with existing WCAG documents?
- Are there any remaining open issues for this rule that were opened prior to this review?
- Do you have any further questions or concerns about this rule?
- Do you think this rule is ready to be published?

This survey will be open for at least 5 work days, to give ACT Task Force members sufficient time to review the rule. No more than three rule surveys will be open at the same time.

If the rule does not pass this step, one of the ACT facilitators send the feedback to the rule author. The rule author will have 5 work days to correct any reported issues. If not, the issue will be closed. Issues can always be reopened, which will restart the process from step 1.

### Publication

When a rule makes it passed the review stage, it is included in a draft version of the WCAG Ruleset. Depending on the types of changes, the ACT Task Force decided on a timeline for releasing updates to the WCAG Ruleset. This timeline is coordinated with the AG Working Group. To update the WCAG Ruleset, the ACT Task Force requests approval from the AG Working Group.

## Implementations

An implementation is either an accessibility testing tool, or a testing methodology. Implementations show that the ACT rule works in practice, and that the interpretation made by the rule is one that is used in real-world accessibility testing. Because of this, having more implementations, or having an implementation that has a lot of users weighs heavily in demonstrating that the assumptions and interpretation in the rule are acceptable to the accessibility community.

For an implementation to be considered, it must be "correct". This is determined by running the tool or methodology on the test cases provided in the rule. Acknowledging that not all implementors distinguish between "passed" and "inapplicable", and that semi-automated tools can return "cantTell" as a result, an implementation is considered correct when it gets one of the allowed outcomes for all of the test cases:

| Test Case Type | Allowed outcomes                        |
| -------------- | --------------------------------------- |
| Passed         | `passed`, `cantTell`, or `inapplicable` |
| Failed         | `failed` or `cantTell`                  |
| Inapplicable   | `inapplicable`, `cantTell`, or `passed` |

## Public Feedback

Public feedback received about the W3C ruleset will be processed by the ACT Task Force. These questions can either be submitted directly into the Github repository, or can be copied into Gihtub issues from questions to the ACT public mailing list.

Questions the ACT Task Force can answer will be responded to directly. Questions that may require updates to a rule will be forwarded to the original rule author, including a recommendation from the ACT Task Force about to resolve the question. If the proposed update is taken over, the rule will be updated without having to go through the review process. If a different solution is taken, or additional changes are made, the update will have to go through the review process.

For the ACT Task Force agenda, public feedback will be prioritised over rule reviewing. This ensures responsiveness to the wider community. The ACT Task Force should respond to questions within 1 week. This may be a reply in which they defer to the original rule author for a solution.

## Rule Author Questions

Often when writing rules, questions come up about the intended meaning of WCAG success criteria. The ACT Task Force will keep track of such questions coming from rule authors using Github issues. The ACT Task Force will work with the AG Working Group to come up with answers for such questions. As response to such questions is dictated by the availability of AG, there is no target time frame for a response.

## Annual Review

Since technologies and standards frequently change, rules require regular maintenance. To ensure quality over time, the ACT Task Force will review every rule in the W3C Ruleset at least once a year, to ensure it is still current and correct. If any changes are deemed necessary, the ACT Task Force proposes an update to the rule to the original rule author. If the change is taken up without further updates, the update is accepted without further review.

## Orphaned Rules

If a request for change is not responded two within two months, either from public feedback or an annual review, the ACT Task Force will assume the rule is no longer actively maintained, and will look for another organisation who might be willing to maintain the rule. If the original author wishes to resume maintenance of the rule, this will only be accepted with the permission of the current rule author.

If noone can be found to maintain a rule within a month, the rule will be labelled as "outdated". Outdated rules will be removed from the ruleset after 1 year.
