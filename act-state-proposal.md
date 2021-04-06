The committee on "States in ACT rules" considered the following.

- The ACT Rules Community Group identified multiple situations where the "state" an element is in impacts the applicability or expectation of an ACT Rule 

- The "state" an element is in can be the result of many factors: CSS styling (including media queries); ARIA attributes; DOM manipulations originated from Javascript; instruments (pointer, keyboard, etc.) manipulated by the user.

- Many (but not all) of the aforementioned factors are reflected by the CSS pseudo-classes that can be used to select an element.

- CSS pseudo-classes are well-defined and easy to refer to.

- Javascript manipulations of the DOM that are not reflected in the CSS pseudo-class selectors are ill defined and extremely hard to specify in the objective manner that is requested for ACT rules. 

- We found that transitions also need to be addressed, since the "State A" of an element is often a concern only when it changes, that is, it transitions from State A to some State B. 


The committee on "States in ACT rules" proposes the following.

- The states to be considered are the ones that can be specified using CSS pseudo-class selectors.

- PROPOSAL: A state is defined as the set of all CSS pseudo-classes matching an element.
    For example, an element is in the hovered state if it matches the :hover pseudo-class (irrespectively of it matching any other pseudo-class)

- States might be declared for the applicability of an ACT rule and/or for the expectation of an ACT rule. 

- Transition between states might be declared for the applicability of an ACT rule and/or for the expectation of an ACT rule.

- PROPOSAL: Add a subheading to the "Applicability" section of a rule, that reads "Applicable States and Transitions"
    If states are relevant to the applicability of the rule, this section should enumerate at least one of the following:
    - the specific combinations of CSS pseudo-classes that the test target must match to be applicable (This rule applies if the "element specified in the applicability" is in any/all states matching/not matching [list of pseudo-classes])
    - any transitions between matching or not matching specific combinations of CSS pseudo-classes for the test target to be applicable (This rule applies if any/all of the following is true/false: [list of transitions between pseudo-classes]). 
    If states are not relevant to the applicability of the rule, this section should be absent.

- PROPOSAL: Add a subheading to each "Expectation" section of a rule, that reads "Expected States and Transitions"
    If states are relevant to the expectation of the rule, this section should enumerate at least one of the following:
    - the specific combinations of CSS pseudo-classes for which the expectation must hold that the test target must match (The expectation must hold when the test target is in any/all of the following states: [list of pseudo-classes]),
    - any transitions between matching or not matching specific combinations of CSS pseudo-classes for the test target to meet the expectation (The expectation must hold while any/all of the following are true/false: [list of transitions between pseudo-classes]).  
    If states are not relevant to an expectation of the rule, this section should be absent.

- Some rules are applicable in all states (e.g. "Inline link in paragraph is distinguishable" should be applicable when the link is hovered and not hovered) but there are states more important to test than others (e.g. it should be tested both in the hovered and not hovered state, while it is not as relevant to test in the active or not active state). In these instances, the committee recommends adding an item to the Background section specifying the most relevant states to test the rule in. Additionally, the rule should include test cases that ensure testing the most relevant states.

- The test cases need not test every combination of states, but it should be expected that the rules include a reasonable number of test cases handling most combinations of states. 


Committee on "States in ACT Rules"
- Carlos Duarte
- Jean-Yves Moyen
- Lionel Wolberger
- Trevor Bostic
- Will Creedle 

Meeting dates:
- February 2, 2021
- February 9, 2021
- February 16, 2021
- February 23, 2021
- March 2, 2021
