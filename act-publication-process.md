# ACT Publication Process

The ACT publication process is designed to publish high-quality ACT rules to the W3C website. This goes through five phases. This process involves the combined effort of the ACT Task Force, and the ACT Rules Community Group. 

1. Draft proposal
2. Call for review
3. Call for implementation
4. Validation
5. Publish approval

## ACT Publication steps

### 1. Draft proposal

New rules, and changes to rules are made through GitHub pull requests. Any member of either ACT group can author such a pull request. When a pull request is ready for review the author must give it the "ready for review" label.

Before going to the next step, a pull request must have approval from three independent reviewers. These reviewers can not work for the same organization, and must not have been involved in writing the pull request. 

The pull request description must include information on the type of change the pull request makes, and what happens in the "call for review" phase. There are three options:

1. New rules, and significant changes that impact multiple rules should have a **two week** call for review. 
2. Updates to rules, and changes to definitions used in a small number of rules have a **one week** call for review.
3. Editorial changes, including minor changes to test cases can **skip** call for review.

### 2. Call for review

Once a pull request has the necessary approvals, the author of the pull request sends an e-mail to the ACT Rules community group mailing list with the text "[for review]" in the subject. The e-mail must include a link to the pull request, and an indication of the duration and end date of the call for review. 

1. If no changes are requested on the pull request during the review period, the author is free to merge the pull request. 
2. Otherwise, the author must resolve the requested changes and;
  1. If the changes are editorial, the pull request can be merged at the end of the review period
  2. If the changes are not editorial, repeat step 1, followed by a **one week** call for review.

When a pull request is merged, the rule is published on the WAI website with a clear indicator that the rule, or the update to the rule is a "proposal". Additionally, metadata for the rule is published, so that implementors of ACT rules can create an implementation report for the proposed rule.

### 3. Call for implementation

When there is at least one complete implementation of the rule, the proposal can proceed to the validation phase. An implementation is considered "complete" when the outcome of the test cases are the same as the expected outcome. Inapplicable and passed are considered interchangeable.

### 4. Validation

Once the proposal has a complete implementation, a survey is created. This survey asks questions to ensure the rule is valid, consistent with WCAG, and up to date. This survey is shared with participants in the weekly TF/CG call.

To go to the next step, the survey must include 5 approvals to publish, and no objections. If the based on results in the survey, changes are needed, a liaison is picked for the rule, who is responsible for drafting a proposal (step 1) to update the rule.

### 5. Publish Approval

Once a rule is validated by the ACT TF / CG, one of the ACT chairs will request that AG approve the rule. How AG does this is left up to the AG chairs to decide. Commonly this is done through a survey and a quick conversation on one of the weekly AG calls.

Based on the feedback from AG, one of three things can happen:

1. If AG approves the changes, the rule is republished on w3.org with the "proposal" indicator removed.
2. If AG requests editorial changes, a draft proposal is created (step 1). Once merged, the updated rule is republished on w3.org with the "proposal" indicator removed.
3. If AG requests non-editorical, the liaison is tasked to draft a proposal as in step 1.
