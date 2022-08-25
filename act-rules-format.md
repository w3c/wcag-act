<pre class='metadata'>
Title: Accessibility Conformance Testing (ACT) Rules Format
Shortname: ACT-Rules-Format
URL: https://w3c.github.io/wcag-act/act-rules-format.html
Previous Version: https://w3c.github.io/wcag-act/archive_act-format/2019-07-12.html
Level: 1.0
Status: w3c/ED
Group: act-rules-format
Editor: Wilco Fiers, Deque Systems
Editor: Maureen Kraft, IBM Corp.
Editor: Mary Jo Mueller, IBM Corp.
Editor: Shadi Abou-Zahra, W3C
Abstract: The Accessibility Conformance Testing (ACT) Rules Format 1.0 defines a format for writing accessibility test rules. These test rules can be used for developing automated testing tools and manual testing methodologies. It provides a common format that allows any party involved in accessibility testing to document and share their testing procedures in a robust and understandable manner. This enables transparency and harmonization of testing methods, including methods implemented by accessibility test tools.
Markup Shorthands: markdown yes
</pre>
<style>
  .rfc2119 {
    text-transform: uppercase;
  }
  pre.highlight {
    background: white !important;
    border: solid 1px #ded390;
    border-radius: 2px;
  }
  pre.highlight c-[s],
  pre.highlight c-[u] {
    color: #79532e;
  }
  pre.highlight c-[f] {
    color: #578201;
  }
  pre.highlight c-[p] {
    color: #757575;
  }
</style>

Introduction {#intro}
=====================

There are currently many test procedures and tools available which aid their users in testing web content for conformance to accessibility standards such as the [Web Content Accessibility Guidelines](https://www.w3.org/WAI/standards-guidelines/wcag/) [[WCAG]]. As the Web develops in both size and complexity, these procedures and tools are essential for managing the accessibility of resources available on the Web.

This format is intended to enable a consistent interpretation of how to test conformance to WCAG and other [=accessibility requirements documents=] and promote consistent results in accessibility testing. The rules format is designed to describe both manual accessibility tests, as well as automated tests as performed by accessibility testing tools.

Documenting how to test [=accessibility requirements=] will result in accessibility tests that are transparent, with test results that are reproducible. The Accessibility Conformance Testing (ACT) Rules Format defines the requirements for these test descriptions, known as Accessibility Conformance Testing Rules (ACT Rules).

An ACT Rule is a plain language description of how to test a specific type of content for a specific aspect of an accessibility requirement. An ACT Rule describes what kind of content it applies to and which conditions are true about the applicable elements for them to meet all expectations of the rule. In the context of WCAG, ACT Rules test for failures in satisfying Success Criteria. Such failures are often described in [common failures](https://www.w3.org/TR/WCAG21/#wcag-2-layers-of-guidance) documented for WCAG. ACT Rules are written for the testing process and are usually more specific than common failures.

The ACT Rules Format defines the requirements and rule structure for the types of information each rule needs to include to be called an ACT Rule. The structure of the ACT rule is defined in the [ACT Rule Structure](#act-rule-structure) section. Each ACT Rule also contains a plain language description of the type of content under test, the test to perform, and the expected result.  Where the test result affects conformance, the rule documents the particular requirement being tested. The resulting outcomes from the test can be used to help determine conformance or non-conformance to the requirement. Test cases are also written as part of the ACT rule to provide a way to verify that implementations of the rule can successfully determine the expected outcomes.


Scope {#scope}
==============

The ACT Rules Format defined in this specification is designed for rules that can be used in testing content created using web technologies, such as [Hypertext Markup Language](https://www.w3.org/TR/html/) [[HTML]], [Cascading Style Sheets](https://www.w3.org/TR/CSS/) [[css-2018]], [Accessible Rich Internet Applications](https://www.w3.org/WAI/standards-guidelines/aria/) [[WAI-ARIA]], [Scalable Vector Graphics](https://www.w3.org/TR/SVG/) [[SVG2]], [EPUB 3](http://www.idpf.org/epub3/latest/), and more. The ACT Rules Format is designed to be technology agnostic, meaning that it can conceivably be used to describe test rules for other technologies.

The ACT Rules Format can be used to describe ACT Rules dedicated to testing the [=accessibility requirements=] defined in the Web Content Accessibility Guidelines [[WCAG]], which are specifically designed for web content. Other accessibility requirements applicable to web technologies can also be testable with ACT Rules. For example, ACT Rules could be developed to test the conformance of web-based user agents to the [User Agent Accessibility Guidelines](https://www.w3.org/WAI/standards-guidelines/uaag/) [[UAAG20]]. The ACT Rules Format might not always be suitable to describe tests for other types of accessibility requirements.


ACT Rule Types {#rule-types}
============================

In accessibility, there are often different technical solutions to make the same type of content accessible. For example, there are multiple methods for giving an `img` element in HTML an accessible name. Multiple solutions could be tested in a single rule; however, such a rule tends to be quite complex, making it difficult to understand and maintain. The ACT Rules Format solves this by providing two types of rules:

- <dfn>Atomic rules</dfn> describe how to test a specific type of solution. It contains a precise definition of what elements, nodes or other "parts" of a [=test subject=] are to be tested, and when those test targets are considered to pass or fail the rule. These rules are to be kept small and *atomic*. This means that atomic rules test a single "condition" and do so without using the [=outcomes=] from other rules.

- <dfn>Composite rules</dfn> describe how the [=outcomes=] of multiple [=atomic rules=] can be combined into a single outcome for each [=test target=]. A composite rule can have multiple "conditions", each of these tested in a separate atomic rule. The logic in the composite rule describes how any one of these satisfying conditions, or some combination of them, is used to determine a single outcome.

Composite rules cannot contain other composite rules. Any time a nested composite rule would be needed, all of the relevant atomic rules can be combined directly into the new composite rule.

<aside class="example">
  <header>Example of using multiple input rules in a composite rule:</header>
  <blockquote><p>Each HTML `video` element meets all expectations from at least one of the following rules:</p>
  <ul>
    <li>Video elements have a transcript</li>
    <li>Video elements have an audio description</li>
    <li>Video elements have a description track</li>
  </ul></blockquote>
</aside>

Not all atomic rules have to be part of a composite rule. Composite rules are used when the [=outcomes=] of multiple atomic rules need to be combined to determine if a [=test subject=] does not satisfy an [=accessibility requirement=].

The separation between atomic rules and composite rules creates a division of responsibilities. Atomic rules test if web content is correctly implemented in a particular solution. Composite rules can test if a combination of [=outcomes=] from other atomic rules satisfy the accessibility requirement, in part or as a whole.


ACT Rule Structure {#act-rule-structure}
===============================

An ACT Rule <em class="rfc2119">must</em> consist of at least the following items:

* <dfn>Descriptive Title</dfn>
* [Rule Identifier](#rule-identifier)
* [Rule Description](#rule-description)
* [Rule Type](#rule-type)
* [Accessibility Requirements Mapping](#accessibility-requirements-mapping)
* [Rule Input](#input), which is one of the following:
    * [Input Aspects](#input-aspects) (for atomic rules) OR
    * [Input Rules](#input-rules) (for composite rules)
* [Applicability](#applicability)
* [Expectations](#expectations)
* [Assumptions](#assumptions)
* [Accessibility Support](#accessibility-support)
* [Test Cases](#test-cases)
* [Change Log](#change-log)
* [Glossary](#glossary)

An ACT Rule MAY also contain:

* [Issues List](#issues-list) (optional)
* [Background](#background) (optional)
* [Acknowledgments](#acknowldgements) (optional)

The ACT Rules format does not prescribe what format ACT Rules can be written in (e.g. HTML, DOCX, PDF, etc.). However, ACT Rules <em class="rfc2119">must</em> be written in a document that conforms to the Web Content Accessibility Guidelines [[WCAG]] or a comparable accessibility standard. This ensures that ACT Rules are accessible to people with disabilities. ACT Rule [test cases](#test-cases) are allowed to contain inaccessible content. If any test case contains accessibility issues listed in [WCAG 2.1 Section 5.2.5 Non-Interference](https://www.w3.org/TR/WCAG21/#cc5), users <em class="rfc2119">must</em> be warned of this in advance. In addition to supporting people with disabilities, using an accessible format also makes internationalization of ACT Rules easier.


Rule Identifier {#rule-identifier}
----------------------------------

An ACT Rule <em class="rfc2119">must</em> have an identifier. This identifier <em class="rfc2119">must</em> be unique when the rule is part of a ruleset. The identifier can be any text, such as plain text, URL, or a database identifier.

<aside class=example>
  <header>Example of identifiers that are also used as filenames; They include a technology directory, followed by a handle that includes an element name or attribute:</header>
  <blockquote><ul>
    <li>html+svg/video-alternative</li>
    <li>html+svg/meta-no-refresh</li>
    <li>html+svg/unique-id</li>
  </ul></blockquote>
</aside>

In addition to the identifier, each new release of an ACT Rule <em class="rfc2119">must</em> be versioned with either a date or a number. A reference to the previous version of that rule <em class="rfc2119">must</em> be available. The identifier <em class="rfc2119">must not</em> be changed when the rule is updated. For substantial changes, a new rule <em class="rfc2119">should</em> be created with a new identifier, and the old rule <em class="rfc2119">should</em> be deprecated.

<aside class=example>
  <header>Example situation of updating a rule:</header>
  <blockquote><p>When updating a rule that is about buttons, to now also be about links, menu items and tabs, the buttons rule is deprecated. As a replacement, a new rule is created that is applicable to all those elements.</p></blockquote>
</aside>


Rule Description {#rule-description}
------------------------------------

An ACT Rule <em class="rfc2119">must</em> have a description that is in plain language which provides a brief explanation of what the rule does.

<aside class=example>
  <header>Example of a rule description:</header>
  <blockquote><p>This rule checks that the HTML page has a title</p></blockquote>
</aside>


Rule Type {#rule-type}
------------------------------------

An ACT Rule <em class="rfc2119">must</em> have a rule type which is one of the following:
<ul>
  <li>Atomic rule</li>
  <li>Composite rule</li>
</ul>

Refer to the [Rule Type](#rule-types) section for detailed definitions of the rule types.


Accessibility Requirements Mapping {#accessibility-requirements-mapping}
------------------------------------------------------------------------

When an ACT Rule is designed to test conformance to one or more [=Accessibility requirements documents=], the rule <em class="rfc2119">must</em> list all [=accessibility requirements=] from those documents that are not satisfied when one or more of the [=outcomes=] of the rule is `failed`. 

Each [=accessibility requirement=] in the mapping <em class="rfc2119">must</em> include the following:

1. either the name, title, identifier or summary of the accessibility requirement, and
2. the name of the [=accessibility requirements document=], and
3. a link or reference to the [=accessibility requirements document=] if one exists, and
4. the conformance level associated with the accessibility requirement, if one exists.


### Mapping Conformance Requirements ### {#mapping-conformance-requirements}

An ACT Rule <em class="rfc2119">must</em> indicate what the [=outcomes=] of the rule mean for satisfying an accessibility requirement for that [=test subject=]. A conformance requirement mapped in a rule is an accessibility requirement that is <dfn>not satisfied</dfn> when all of the outcomes for a test target in failed test cases is `failed`. When all of the outcomes for passed test cases or inapplicable test cases are `passed` or `inapplicable`, respectively, the mapped conformance requirement could be <dfn>satisfied</dfn> or <dfn>further testing is needed</dfn>. Rules that can be used to determine if an accessibility requirement is *satisfied* are called <dfn>satisfying tests</dfn>.

<div class=note>
  <p>**Note:** In the [Web Content Accessibility Guidelines](https://www.w3.org/WAI/standards-guidelines/wcag/) [[WCAG]], success criteria do not evaluate to `passed`, `failed` or `inapplicable`. Rather they can be *satisfied* (or not). (See the [WCAG 2.1 definition: satisfies a success criterion](https://www.w3.org/TR/WCAG21/#dfn-satisfies).) If a success criterion is *not satisfied*, a web page can only conform if there is a conforming alternative version, as described in [WCAG 2.1 Conformance Requirement 1](https://www.w3.org/TR/WCAG21/#cc1).</p>
</div>

When a `failed` outcome of the rule can determine that an accessibility requirement is <dfn>not satisfied</dfn>, the accessibility requirement must be listed as a Conformance Requirement. That ACT Rule will list each success criteria in its accessibility requirements mapping as **Required for Conformance**.

<aside class=example>
  <header>Example accessibility requirements mapping for a rule that tests if an image button has an accessible name maps conformance requirements to success criteria 1.1.1 Non-text content and 4.1.2 Name, Role, Value:</header>
  <blockquote><ul>
    <li>
      [Success criterion 1.1.1: Non-text content](https://www.w3.org/TR/WCAG21/#non-text-content)
      <ul>
        <li>**Required for conformance** to WCAG 2.0 and WCAG 2.1 level A and higher</li>
        <li>Outcome mapping: <ul>
          <li>Any `failed` outcomes: not satisfied</li>
          <li>All `passed` outcomes: further testing is needed</li>
          <li>An `inapplicable` outcome: further testing is needed</li>
        </ul></li>
      </ul>
    </li>
    <li>
      [Success criterion 4.1.2: Name, Role, Value](https://www.w3.org/TR/WCAG21/#name-role-value)
      <ul>
        <li>**Required for conformance** to WCAG 2.0 and WCAG 2.1 level A and higher</li>
        <li>Outcome mapping:<ul>
          <li>Any `failed` outcomes: not satisfied</li>
          <li>All `passed` outcomes: further testing is needed</li>
          <li>An `inapplicable` outcome: further testing is needed</li>
        </ul></li>
      </ul>
    </li>
  </ul></blockquote>
</aside>

### Mapping Associated/Affiliated/Secondary Requirements ###
When an ACT Rule is designed to test conformance to an [=accessibility requirement=], the rule <em class="rfc2119">may</em> have outcomes for other [=accessibility requirements=] that are not consistent with the rule and do not meet the criteria to be mapped as Conformance Requirements.
An ACT Rule <em class="rfc2119">may</em> have outcomes for secondary [=accessibility requirements=] for that test subject. Accessibility requirements must be mapped as secondary if one or more of the following is true: 

- <dfn>further testing is needed</dfn> when one or more of the outcomes for a test target is `failed`, or 
- the accessibility requirement can be <dfn>satisfied</dfn>, <dfn>further testing is needed</dfn>, or <dfn>not satisfied</dfn>when all the outcomes are `passed`.

The rule must explain the secondary relationship of the accessibility requirement in the Background section of the rule. 

<aside class=example>
  <header>Example accessibility requirements mapping for a rule that tests if text has minimum contrast maps to conformance requirement SC 1.4.3 Contrast (Minimum). It maps to secondary requirement SC 1.4.6 Contrast (Enhanced) because all passed test cases did not pass:</header>
  <blockquote><ul>
    <li>
      [Success criterion 1.4.3 Contrast Minimum (AA)](https://www.w3.org/TR/WCAG21/#contrast-minimum)
      <ul>
        <li>**Required for conformance** to WCAG 2.0 and WCAG 2.1 level A and higher</li>
        <li>Outcome mapping:<ul>
          <li>Any `failed` outcomes: not satisfied</li>
          <li>All `passed` outcomes: further testing is needed</li>
          <li>An `inapplicable` outcome: further testing is needed</li>
        </ul></li>
      </ul>
    </li>
    <li>
      [Success Criterion 1.4.6 Contrast (Enhanced) (Level AAA)](https://www.w3.org/TR/WCAG21/#contrast-enhanced)
      <ul>
        <li>**Secondary** to WCAG 2.0 and WCAG 2.1 level A and higher</li>
        <li>Outcome mapping:<ul>
          <li>Any `failed` outcomes: not satisfied</li>
          <li>All `passed` outcomes: further testing is needed; some passed test cases did not pass. SC 1.4.6 requires higher contrast ratios than SC 1.4.3</li>
          <li>An `inapplicable` outcome: further testing is needed</li>
        </ul></li>
      </ul>
    </li>
  </ul></blockquote>
</aside>

<aside class=example>
  <header>Example accessibility requirements mapping for a rule that tests if a focusable element has no keyboard trap via standard navigation maps to secondary requirement SC 2.1.2 No Keyboard Trap because non-standard navigation is not tested:</header>
  <blockquote><ul>
    <li>
      [Success Criterion 2.1.2: No Keyboard Trap](https://www.w3.org/TR/WCAG21/#no-keyboard-trap)
      <ul>
        <li>**Secondary** to WCAG 2.0 and WCAG 2.1 level A and higher</li>
        <li>Outcome mapping:<ul>
          <li>Any `failed` outcomes: further testing is needed; SC 2.1.2 permits use of non-standard navigation to exit a keyboard trap</li>
          <li>All `passed` outcomes: further testing is needed</li>
          <li>An `inapplicable` outcome: further testing is needed</li>
        </ul></li>
      </ul>
    </li>
  </ul></blockquote>
</aside>

### Mapping for Atomic Rules ### {mapping-for-atomic-rules}
Atomic rules may map to conformance requirements, secondary accessibility requirements, or no accessibility requirements.

### Mapping for Composite Rules ### {mapping-for-composite-rules}
The Accessibility Requirements mapping for Composite Rules must include all mapped requirements in atomic rules.

### Mapping Outside WCAG ### {#mapping-outside-wcag}

ACT Rules can be used to test accessibility requirements that are not part of a W3C accessibility standard, such as accessibility requirements in [Hypertext Markup Language](https://www.w3.org/TR/html/) [[HTML]], or tests in a methodology like [RGAA 3 2016](https://disic.github.io/rgaa_referentiel_en/criteria.html). An ACT Rule <em class="rfc2119">must</em> indicate whether or not the [=accessibility requirement=] it maps to is required for conformance in its [=accessibility requirements document=]. Examples of accessibility requirements that are not required for conformance are WCAG sufficient techniques, or a company style guide that includes both requirements and optional "best practices". The distinction between what is required and what is optional has to be clear.

<aside class=example>
  <header>Example accessibility requirements mapping for a rule that tests that each `img` element has an `alt` attribute:</header>
  <blockquote><ul>
    <li>
      [Technique H37: Using alt attributes on img elements](https://www.w3.org/TR/WCAG20-TECHS/H37.html)
      <ul>
        <li>**Not required** for conformance to WCAG 2.0 and WCAG 2.1 at any level</li>
        <li>Outcome mapping: <ul>
          <li>Any `failed` outcomes: not satisfied</li>
          <li>All `passed` outcomes: satisfied</li>
          <li>An `inapplicable` outcome: satisfied</li>
        </ul></li>
      </ul>
    </li>
    <li>
      [RGAA 3, Test 1.1.1: Does each image have a text alternative](https://disic.github.io/rgaa_referentiel_en/criteria.html#test-1-1-1)
      <ul>
        <li>**Required for conformance** to RGAA 3 level A and higher</li>
        <li>Outcome mapping: <ul>
          <li>Any `failed` outcomes: not satisfied</li>
          <li>All `passed` outcomes: satisfied</li>
          <li>An `inapplicable` outcome: satisfied</li>
        </ul></li>
      </ul>
    </li>
  </ul></blockquote>
</aside>


### Rules Without Accessibility Requirements ### {#rules-without-accessibility-requirements}

If the rule does not map to any [=accessibility requirement=], the accessibility requirement mapping will only contain the explainer that it is not required for conformance to the [=accessibility requirements document=]. This is common with atomic rules used in composite rules.

<aside class=example>
  <header>Example of a rule that tests if `role=alert` is used to satisfy [WCAG 2.1 success criterion 4.1.3 Status Messages](https://www.w3.org/TR/WCAG21/#status-messages):</header>
  <blockquote>
    <p>This rule is **not required** for conformance to WCAG 2.1 at any level.</p>
  </blockquote>
</aside>

If the `failed` [=outcome=] cannot be mapped to an [=accessibility requirement=], there <em class="rfc2119">must not</em> be an accessibility requirement in the accessibility requirements mapping. The optional [Background section](#background) could be used to list [=accessibility requirements documents=] when they are thematically related, but for which the rule is not a failure test.


### External Accessibility Requirements Mapping ### {#external-accessibility-requirements-mapping}

This section is *non-normative*.

While rules are often designed for one, or possibly a small collection of [=accessibility requirements documents=], it is likely that other accessibility requirements documents also map to those ACT Rules. For example, rules can be written for the [Web Content Accessibility Guidelines](https://www.w3.org/WAI/standards-guidelines/wcag/) [[WCAG]], but many of those could also map to a company's internal accessibility policy. In such a scenario, an external accessibility requirements mapping could be created. An external accessibility requirements mapping amends the accessibility requirements mapping of an ACT rule by adding mapping to a different accessibility requirements document. An external accessibility requirements mapping avoids duplication of a rule for the sole purpose of changing the mapping.


Rule Input {#input}
-------------------

To evaluate content using an ACT Rule, the rule requires some information from the [=test subject=]. This is the input for the rule. What input is required is made explicit, to help testers understand what capabilities are required to use a rule. [=Atomic rules=] and [=composite rules=] have different input.

- Atomic rules have [Input Aspects](#input-aspects)
- Composite rules have [Input Rules](#input-rules)


### Input Aspects (Atomic rules only) ### {#input-aspects}

An input aspect is a distinct part of the [=test subject=]. Rendering a particular piece of content to an end user commonly involves different technologies, some or all of which are required as input for an [=atomic rule=]. For example, some rules need to operate directly on the [Hypertext Transfer Protocol](https://tools.ietf.org/html/rfc7230) [[http11]] messages exchanged between a server and a client, while others need to operate on the [Document Object Model](https://dom.spec.whatwg.org) [[DOM]] tree exposed by a web browser.

[=Atomic rules=] <em class="rfc2119">must</em> list the aspects used as input for the [applicability](#applicability-atomic) and [expectations](#expectations-atomic) of the atomic rule. Rules can operate on several aspects simultaneously, such as both the HTTP messages and the DOM tree.

Some input aspects are well defined in a formal specification, such as HTTP messages, the DOM tree, and CSS styling [[css-2018]]. For these, a reference to the corresponding section in the [Common Input Aspects note](https://www.w3.org/TR/act-rules-aspects/) is sufficient as a description of the aspect. For input aspects that are not well defined, an ACT Rule <em class="rfc2119">must</em> include either a detailed description of the aspect in question, or a reference to a well defined description.

<aside class=example>
  <header>Example input aspects for a rule that checks if a transcript is available for videos:</header>
  <blockquote><ul>
    <li>DOM Tree</li>
    <li>CSS Styling</li>
    <li>Audio output</li>
    <li>Visual output</li>
  </ul></blockquote>
</aside>

<aside class=example>
  <header>Example input aspects for a rule that checks for use of (language specific) generic link texts like "click here" and "more":</header>
  <blockquote><ul>
    <li>DOM Tree</li>
    <li>CSS Styling</li>
    <li>Language</li>
  </ul></blockquote>
</aside>

 The method through which an input aspect is served is not relevant. For example a DOM tree can be served through HTTP as HTML, it can be bundled as several pages in an [EPUB publication](http://www.idpf.org/epub3/latest/), or it can be inferred from a [JSX source file](https://facebook.github.io/jsx/). All rules that have only DOM tree as an input aspect can be applied to those technologies.


### Input Rules (Composite rules only) ### {#input-rules}

A [=composite rule=] uses [=outcomes=] from [=atomic rules=] and applies logic to them so that a single outcome can be determined for each [=test target=]. The [identifier](#rule-identifier) and [=descriptive title=] of all the atomic rules used in the [expectations](#expectations-composite) <em class="rfc2119">must</em> be listed in the composite rule. The input rules describe the input for composite rules, similar to how [input aspects](#input-aspects) describe the input for atomic rules.


Applicability {#applicability}
------------------------------

The applicability describes what parts of the [=test subject=] are tested.


### Applicability for Atomic Rules ### {#applicability-atomic}

The applicability section is a required part of an [=atomic rule=]. It <em class="rfc2119">must</em> contain a precise description of the parts of the [=test subject=] to which the rule applies. For example, specific nodes in the DOM [[DOM]] tree, or tags that are incorrectly closed in an HTML [[HTML]] document. These are known as the [=test targets=]. The applicability <em class="rfc2119">must</em> only use information made available through the listed [input aspects](#input-aspects) in the rule. No other information can be used in the applicability. Applicability <em class="rfc2119">must</em> be described objectively, unambiguously and in plain language.

An objective description is one that can be resolved without uncertainty, in a given technology. Examples of objective properties in HTML are tag names, their computed role, the distance between two elements, etc. Subjective properties on the other hand, are concepts like decorative, navigation mechanism and pre-recorded.

Even concepts like headings and images can be misunderstood. These terms could refer to the tag name, the semantic role, or the element's purpose on the web page because they are ambiguous. The latter of which is almost impossible to define objectively. When used in applicability, potentially ambiguous concepts <em class="rfc2119">must</em> be defined objectively. Definitions can be put in the rule [glossary](#glossary), or they can be defined in the section where they are used.

<aside class=example>
  <header>Example applicability of an atomic rule testing [WCAG 2.1 success criterion 1.4.2 Audio Control](https://www.w3.org/WAI/WCAG21/quickref/#audio-control):</header>
  <blockquote>
    <p>Each `video` or `audio` element with the `autoplay` attribute, as well as each `object` element that is used for automatically playing video or audio when the web page loads.</p>
    <p>Note: A web page is considered "loaded" when the `document.readyState` is set to `complete`.</p>
  </blockquote>
</aside>

<aside class=example>
  <header>Example applicability of a rule with the page as a test target</header>
  <blockquote>
    <p>The rule applies to any page where the document element is an `html` element, and the `html` element is rendered in a top-level context (i.e. the `html` element is not embedded in another page, such as through `iframe` or `object` elements). </p>
  </blockquote>
</aside>

<aside class=example>
  <header>Example applicability of a rule with a DOM attribute as a test target</header>
  <blockquote>
    <p>The rule applies to any `role` attribute that is specified on an HTML or SVG element.</p>
  </blockquote>
</aside>

### Applicability for Composite Rules ### {#applicability-composite}

The applicability of a composite rule is defined as the union of all applicability definitions from the rules listed in the [input rules](#input-rules). Rule authors <em class="rfc2119">may</em> omit a description of the applicability for composite rules. This can be useful if it is difficult to express the combined applicability in plain language. If the composite rule includes applicability, it <em class="rfc2119">must</em> be the union of all the applicability in the [input rules](#input-rules).

Note that input rules in a composite rule <em class="rfc2119">may</em> have different applicability. Because of this, not every test target applicable within the composite rule is tested by every input rule.

<aside class=example>
  <header>Example of the union of applicability of input rules in a composite rule:</header>
  <blockquote>
    <p>**Input applicability:**</p>
    <ul>
      <li>**Input Rule 1:** All `img` element <em>with</em> an `alt` attribute</li>
      <li>**Input Rule 2:** All `img` element <em>without</em> an `alt` attribute</li>
    </ul>
    <p>**Combined applicability:**</p>
    <p>All `img` elements.</p>
  </blockquote>
</aside>


Expectations {#expectations}
----------------------------

An ACT Rule <em class="rfc2119">must</em> contain one or more expectations. The expectations describe what the requirements are for the [=test targets=] derived from the [applicability](#applicability). An expectation is an assertion about a [=test target=]. When a test target meets all expectations, the test target `passed` the rule. If the test target does not meet all expectations, the test target `failed` the rule. If there are no test targets, the [=outcome=] for the rule is `inapplicable`.

Each expectation <em class="rfc2119">must</em> be distinct, unambiguous, and be written in plain language.


### Expectations for Atomic Rules ### {#expectations-atomic}

All expectations of an [=atomic rule=] <em class="rfc2119">must</em> describe the logic that is used to determine a single `passed` or `failed` [=outcome=] for a [=test target=]. The expectation <em class="rfc2119">must</em> only use information available in the [input aspects](#input-aspects), from the applicability, and other expectations of the same rule. No other information can be used in the expectation. So for instance, an expectation could be "Expectation 1 is true and ...", but it can't be "Rule XYZ passed and ...". This ensures that atomic rules are encapsulated.

<aside class=example>
  <header>Example expectations of a rule to test for accessible names of HTML `input` elements:</header>
  <blockquote><ol>
    <li>Each HTML `input` element has an accessible name (as described in [Accessible Name and Description: Computation and API Mappings 1.1](https://www.w3.org/TR/accname-aam-1.1/#mapping_additional_nd_te)). [[accname-aam-1.1]]</li>
    <li>The accessible name describes the purpose of each HTML `input` element.</li>
  </ol></blockquote>
</aside>

<aside class=example>
  <header>Example expectation of a rule to test if a `role` attribute is valid:</header>
  <blockquote><ol>
    <li>Each `role` attribute has a value that corresponds to a non-abstract [WAI-ARIA 1.1](https://www.w3.org/TR/wai-aria/) role.</li></blockquote>
  </ol>
</aside>

<div class="note">
  <p>**Note:** Sometimes there is the need for rules with more complex aggregation, for example that X% of all images on a web page are expected to have text alternatives. In this case, the page itself needs to become the test target. The expectation would then be "The test target (the page) has a text alternative for X% of all img elements". The logic for calculating the expectations in such rules is left to the implementations, to avoid over-complexity of this rules format.</p>
</div>

### Expectations for Composite Rules ### {#expectations-composite}

All expectations of a [=composite rule=] <em class="rfc2119">must</em> describe the logic that is used to determine a single `passed` or `failed` [=outcome=] for a [=test target=], based on the outcomes of rules in its [input rules](#input-rules). A composite rule expectation <em class="rfc2119">must not</em> use information from [input aspects](#input-aspects). The outcome for a composite rule is `inapplicable` when all input rules are inapplicable.

<aside class="example">
  <header>Example expectations for the composite rule 'video elements have an audio description or media alternative' ([WCAG 2.1 success criterion 1.2.3 Audio Description or Media Alternative](https://www.w3.org/WAI/WCAG21/quickref/#audio-description-or-media-alternative-prerecorded)):</header>
  <blockquote><p>Each HTML `video` element meets all expectations from at least one of the following rules:</p>
  <ul>
    <li>video elements have a transcript</li>
    <li>video elements have an audio description</li>
    <li>video elements have a description track</li>
  </ul></blockquote>
</aside>

<aside class="example">
  <header>Example expectations for a composite rule that checks if a mechanism is available to escape a keyboard trap; Either through a standard mechanism, or one for which instructions are available:</header>
  <blockquote><p>For each focusable element, the outcome of one of the following rules is `passed`:</p>
  <ul>
    <li>Keyboard trap with standard escape mechanism</li>
    <li>Keyboard trap with escape instructions</li>
  </ul></blockquote>
</aside>


Assumptions {#assumptions}
--------------------------

An ACT Rule <em class="rfc2119">must</em> list any known assumptions, limitations or any exceptions for the evaluation, the test environment, technologies being used or the subject being tested. For example, a rule that would partially test [WCAG 2.1 success criterion 1.4.3 Contrast (Minimum)](https://www.w3.org/WAI/WCAG21/quickref/#contrast-minimum) based on the inspection of CSS properties could state that it is only applicable to HTML text content styleable with CSS, and that the rule does not support images of text.

Sometimes there are multiple plausible ways that an accessibility requirement can be interpreted. For instance, it is not immediately obvious if emoji characters are "text" or "non-text content" in the [Web Content Accessibility Guidelines](https://www.w3.org/WAI/standards-guidelines/wcag/) [[WCAG]]. Whatever the interpretation is, this <em class="rfc2119">must</em> be documented in the rule.

While the assumptions <em class="rfc2119">must</em> be included in the ACT Rule, it <em class="rfc2119">may</em> be empty when there are no known assumptions, limitations or exceptions.


Accessibility Support {#accessibility-support}
----------------------------------------------

Content can be designed to rely on the support for particular accessibility features by different assistive technologies and user agents. For example, content using a particular [WAI-ARIA 1.1](https://www.w3.org/TR/wai-aria/) feature relies on that feature to be supported by assistive technologies and user agents. This content would not work for assistive technologies and user agents that do not support WAI-ARIA. See the WCAG definition for [accessibility supported](https://www.w3.org/TR/WCAG21/#dfn-accessibility-supported) use of a web technology.

An ACT Rule <em class="rfc2119">must</em> include known limitations on accessibility support.

<aside class=example>
  <header>Example of a rule that checks if `aria-errormessage` is used to satisfy [WCAG 2.1 success criterion 4.1.3 Status messages](https://www.w3.org/TR/WCAG21/#status-messages):</header>
  <blockquote><p>
    The `aria-errormessage` property is known to have limited support with several major screen readers. This method cannot be relied on for support. Alternatives, like using live regions, could serve as fallback. (January 2019)
  </p></blockquote>
</aside>

While an accessibility support section <em class="rfc2119">must</em> be included in the ACT Rule, it <em class="rfc2119">may</em> be empty when there are no known accessibility support issues.

<div class=note>
  <p>**Note:** The Website Accessibility Conformance Evaluation Methodology (WCAG-EM) provides guidance on defining an [accessibility support baseline](https://www.w3.org/TR/WCAG-EM/#step1c) for test scenarios, which can help users of ACT Rules to select the appropriate rules for their own circumstance.</p>
</div>


Test Cases {#test-cases}
------------------------

Test cases are (snippets of) content that can be used to validate the implementation of ACT Rules. Each rule <em class="rfc2119">must</em> have one or more test cases for `passed`, `failed`, and `inapplicable` [=outcomes=]. A test case consists of two pieces of data, a snippet of each [input aspect](#input-aspects) for a rule, and the expected outcome for that rule. Test cases serve two functions, firstly as example scenarios for readers to understand when the outcome of a rule is `passed`, `failed`, or `inapplicable`. It also serves developers and users of accessibility testing tools and methodologies to validate that a rule is correctly implemented.

<aside class="example">
  <header>Example of HTML test cases for a rule that checks if `img` elements have a text alternative:</header>
  <blockquote>
    <p>Example of a `passed` outcome:</p>
    ```html
<img alt="W3C Logo" src="image/w3c.png">
    ```
    <p>Example of a `failed` outcome:</p>
    ```html
<img src="image/w3c.png">
    ```
    <p>Example of an `inapplicable` outcome:</p>
    ```html
<input type="image" alt="W3C Logo" src="image/w3c.png">
    ```
  </blockquote>
</aside>


Change Log {#change-log}
------------------------

It is important to keep track of changes to the ACT Rules so that users of the rules can understand if changes in test results are due to changes in the rules used when performing the tests, or from changes in the content itself. All changes to an ACT Rule that can change the [=outcomes=] of an evaluation <em class="rfc2119">must</em> be recorded in a change log. The change log can either be part of the rule document itself or be referenced from it.


Glossary {#glossary}
--------------------

ACT Rules <em class="rfc2119">must</em> have a glossary section. The glossary <em class="rfc2119">must</em> contain the [=outcome=] definition, as well as any definitions used in [applicability](#applicability) and [expectations](#expectations) sections in the rule. Since changes to the definition change the rule, those definitions cannot be maintained independently of the rule. If a shared glossary is used for rules, any definition changes <em class="rfc2119">must</em> be included in the [change log](#change-log) of all rules that use that definition.


Issues List (optional) {#issues-list}
-------------------------------------

An ACT Rule <em class="rfc2119">may</em> include a list or a reference to a list of any known issues. The issues list would be used to record cases where an [=outcome=] of an ACT Rule was `failed` where it ought to have been `passed` or `inapplicable`, or vice versa. There are several reasons why this might occur. See [rule accuracy](#rule-accuracy) for more information.

The issues list serves two purposes. For users of ACT Rules, the issues list gives insight into why an inaccurate result occurred, as well as provide confidence in the result of that rule. For the designer of the rule, the issues list is also useful to plan future updates to the rule. In a new version of the rule, resolved issues would be moved to the change log.


Background (optional) {#background}
-----------------------------------

An ACT Rule <em class="rfc2119">may</em> contain information about the background for the development of the rule, or references to relevant reading. The background information is optional, but whenever it is included in the rule, the relationship to the relevant reading can be specified. Examples of relevant background references for a rule for a [Web Content Accessibility Guidelines](https://www.w3.org/WAI/standards-guidelines/wcag/) [[WCAG]] success criterion could be [WCAG 2.1 Understanding documents](https://www.w3.org/WAI/WCAG21/Understanding/), [WCAG 2.1 Techniques](https://www.w3.org/WAI/WCAG21/Techniques/), or [WAI-ARIA 1.1](https://www.w3.org/TR/wai-aria/), CSS [[css-2018]], or HTML [[HTML]] specifications.


Acknowledgments (optional) {#acknowledgments}
-----------------------------------------------

An ACT Rule <em class="rfc2119">may</em> contain acknowledgments. This can include, but is not limited to:
* List of rule authors
* List of rule reviewers/contributors
* Funding or other support


Rule Accuracy {#rule-accuracy}
=========================

This section is *non-normative*.

While [test cases](#test-cases) can be used to determine if an ACT Rule was correctly implemented, they do not guarantee that implementations will never produce incorrect results. When writing ACT Rules, it is almost inevitable that edge cases will be overlooked. Technologies are always evolving, and content authors are constantly coming up with new and unexpected ways to use them. Some examples of causes for inaccuracy are:

- [Assumptions](#assumptions) were made about the test subject that turned out to be untrue
- Technologies were used in an unusual and difficult to predict manner
- Technologies have changes, or aspects of the technologies were overlooked
- The accessibility requirement was not correctly interpreted

There are two types of inaccuracies that can produce incorrect results. Inaccuracies in the **implementation** can be addressed with test cases, but inaccuracies in the **ACT Rule itself** cannot. After all, rule inaccuracies come from the rule author being unaware of a particular edge case.

When a test result incorrectly indicates non-conformance to an accessibility requirement, this is known as a false positive. Opposite, when a rule incorrectly indicates conformance, this is a false negative. A percentage of false positives and false negatives can be calculated by comparing it to results from an accessibility audit:

- **False positives:** This is the percentage of [=test targets=], that were `failed` by the rule, but satisfy the [=accessibility requirements=].

- **False negatives:** This is the percentage of [=test targets=], that were `passed` by the rule, but do not satisfy the [=accessibility requirements=].

The ever present possibility of false positives and false negatives with ACT Rules means they will likely require ongoing maintenance. Designing a process for maintaining ACT Rules is outside the scope of the ACT Rules Format, which is limited to the rules themselves. Nevertheless, it is suggested that rule authors work out a process for maintaining their rules.


Harmonization {#harmonization}
==============================

This section is *non-normative*.

While the ACT Rules Format is designed to stimulate harmonization, there are no direct requirement in the ACT Rules Format that prevent a rule author from writing rules inconsistent with already established ACT Rules. Neither are there requirements for ACT Rules to have a certain number of implementations, or to have a certain level of accuracy. This allows quality requirements to be different for different rulesets, and allows them to develop over time.

Harmonization occurs when a group of rule implementors collectively accept the validity of an ACT Rule. For example, a community group of accessibility testing tool vendors could declare they have harmonized on a particular set of ACT Rules. Such a group can set acceptance criteria for rules, and have quality requirements that go beyond the ACT Rules Format.

<aside class=example>
  <header>Example of acceptance criteria for a group working on EPUB rules:</header>
  <blockquote><ul>
    <li>An ACT EPUB Rule is harmonized when it is approved by members of 3 organizations, AND</li>
    <li>An ACT EPUB Rule is harmonized when it has 2 independent implementations</li>
  </ul></blockquote>
</aside>

An example of such a process is the [WCAG ACT Review Process](https://w3c.github.io/wcag-act-rules/review-process.html).


Definitions {#definitions}
==========================

<dl>
  <dt><dfn>Accessibility requirement</dfn><dt>
  <dd>
    <p>An accessibility requirement is a requirement aimed at improving access for people with disabilities to an ICT product. In the context of ACT rules mapping, a requirement can be compulsory or advisory. When compulsory, it has to be satisfied in order to conform to a standard, or to comply with a contract, policy or regulation. When advisory, it is recommended, but not satisfying it does not lead to non-conformance or non-compliance.</p>
    <p>A common example of accessibility requirements are the WCAG success criteria. There are other standards, including W3C standards, that have recommendations for accessibility, such as WAI-ARIA and HTML. Accessibility requirements are also often found in company policies, regional standards or in legislation.</p>
  </dd>

  <dt><dfn>Accessibility requirements document</dfn><dt>
  <dd>
    <p>A document, such as a standard, contract, policy or regulation, that includes [=accessibility requirements=]. For example, WCAG 2.1, WAI-ARIA 1.1, HTML 5.2, EPUB Accessibility 1.0, BBC HTML Accessibility Standards v2.0</p>
  </dd>

  <dt><dfn>Outcome</dfn></dt>
  <dd>
    <p>A conclusion that comes from evaluating an ACT Rule on a [=test subject=] or one of its constituent [=test target=]. An outcome can be one of the three following types:</p>
    <ul>
      <li>**Inapplicable:** No part of the test subject matches the applicability</li>
      <li>**Passed:** A [=test target=] meets all expectations</li>
      <li>**Failed:** A [=test target=] does not meet all expectations</li>
    </ul>
    <div class="note">
      <p>**Note:** A rule has one `passed` or `failed` outcome for every [=test target=]. When there are no test targets the rule has one `inapplicable` outcome. This means that each [=test subject=] will have one or more outcomes.</p>
    </div>
    <div class="note">
      <p>**Note:** Implementers using the [[EARL10-Schema]] can express the outcome with the [outcome property](https://www.w3.org/TR/EARL10-Schema/#outcome). In addition to `passed`, `failed` and `inapplicable`, EARL 1.0 also defined an `incomplete` outcome. While this cannot be the outcome of an ACT Rule when applied in its entirety, it often happens that rules are only partially evaluated. For example, when applicability was automated, but the expectations have to be evaluated manually. Such "interim" results can be expressed with the `incomplete` outcome.
    </div>
  </dd>

  <dt><dfn>Test Subject</dfn></dt>
  <dd>
    <p>A resource or collection of resources that can be evaluated by an ACT Rule.</p>
    <aside class=example>
      <header>Example of test subjects:</header>
      <blockquote><ul>
        <li>An HTML page, including all embedded scripts, style and images</li>
        <li>An EPUB publication</li>
        <li>A web component file</li>
      </ul></blockquote>
    </aside>
    <div class=note>
      <p>**Note:** Implementers using the [[EARL10-Schema]] can express the test subject with the [subject property](https://www.w3.org/TR/EARL10-Schema/#subject)</p>
    </div>
  </dd>

  <dt><dfn>Test Target</dfn></dt>
  <dd>
    <p>A distinct part of the [=test subject=], as defined by the [applicability](#applicability).</p>
    <aside class=example>
      <header>Example of test targets:</header>
      <blockquote><ul>
        <li>Nodes within an HTML page</li>
        <li>A period of time within a video</li>
        <li>A range of characters within a text document</li>
      </ul></blockquote>
    </aside>
    <div class=note>
      <p>**Note:** Implementers using the [[EARL10-Schema]] can express the test target with the [pointer property](https://www.w3.org/TR/EARL10-Schema/#pointer)</p>
    </div>
  </dd>
</dl>


Appendix 1: Expressing ACT Rule results with JSON-LD and EARL {#appendix-data-example}
=================================================================================

This section is *non-normative*.

This section provides examples of expressing results from carrying out ACT Rules using EARL and JSON-LD (See [Evaluation and Report Language](https://www.w3.org/WAI/standards-guidelines/earl/) and [A JSON-based Serialization for Linked Data (JSON-LD)](https://www.w3.org/TR/json-ld/)). More examples and background is proivided on the [JSON-LD serialization of EARL](https://github.com/w3c/earl) GitHub repository.

Examples in this section include:

- Example 1: Minimal outcome from one 'Assertion'
- Example 2: Results from more than one 'Assertion'
- Example 3: Aggregating based on 'Requirement'
- Example 4: Aggregating based on 'Test Subject'
- Example 5: Assumed 'Context' for this section

**Example 1:** Minimal outcome for one 'Assertion'

```javascript
{
  "@context": "context.json",
  "@type": "Assertion",
  "assertedBy": "https://example.org/MyTool",
  "subject": "https://example.org/page1.html",
  "test": "ACT-CG:rules/23a2a8",
  "result": {
    "outcome": "earl:failed",
    "pointer": "html > body > h1:first-child"
  }
}
```

**Example 2:** Results for more than one 'Assertion'

```javascript
{
  "@context": "context.json",
  "@graph": [{
    "@type": "Assertion",
    "assertedBy": "https://example.org/MyTool",
    "subject": "https://example.org/page1.html",
    "test": "ACT-CG:rules/23a2a8",
    "result": {
      "outcome": "earl:failed",
      "pointer": "html > body > h1:first-child"
    }
  }, {
    "@type": "Assertion",
    "assertedBy": "https://example.org/AnotherTool",
    "subject": "https://example.org/page1.html",
    "test": "ACT-CG:rules/23a2a8",
    "result": {
      "outcome": "earl:passed",
      "pointer": "html > body > h1:nth-child(2)"
    }
  }]
}
```

**Example 3:** Aggregating based on 'Requirement' (eg. WCAG Success Criteria)

```javascript
{
  "@context": "context.json",
  "@type": "Assertion",
  "assertedBy": "https://example.org/MyTool",
  "subject": "https://example.org/page1.html",
  "test": {
    "@type": "earl:TestRequirement",
    "@id": "WCAG21:non-text-content"
  },
  "result": {
    "outcome": "earl:failed",
    "source": [{
      "test": "ACT-CG:rules/23a2a8",
      "result": {
        "outcome": "earl:failed",
        "pointer": "html > body > h1:first-child"
      }
    }, {
      "test": "ACT-RULES-CG:rules/23a2a8",
      "result" : {
        "outcome": "earl:passed",
        "pointer": "html > body > h1:nth-child(2)"
      }
    }]
  }
}
```

**Example 4:** Aggregating based on 'Test Subject' (eg. for a website)

```javascript
{
  "@context": "context.json",
  "@type": "Assertion",
  "assertedBy": {
    "@type": "Organization",
    "@id": "_:myOrg",
    "title": "My Organization",
    "description" : "Accessibility testing service",
    "homepage" : "http://example.org/myOrg/"
  },
  "subject": {
    "@type": ["WebSite", "TestSubject"],
    "@id": "https://example.org/"
  },
  "test": {
    "@type": "earl:TestRequirement",
    "@id": "http://www.w3.org/WAI/WCAG2A-Conformance"
  },
  "result": {
    "outcome": "earl:failed",
    "source": [{
      "test": {
        "@type": "earl:TestRequirement",
        "@id": "WCAG21:non-text-content"
      },
      "result": {
        "outcome": "earl:failed",
        "source": [ … ]
      }
    }, {
      "test": {
        "@type": "earl:TestRequirement",
        "@id": "WCAG21:audio-only-and-video-only-prerecorded"
      },
      "result": {
        "outcome": "earl:passed",
        "source": [ … ]
      }
    }, {
      "test": {
        "@type": "earl:TestRequirement",
        "@id": "WCAG21:captions-prerecorded"
      },
      "result" : {
        "outcome": "earl:passed",
        "source": [ … ]
      }
    }, … ]
  }
}
```

**Example 5:** Assumed 'Context' for this section

```javascript
{
  "@vocab": "http://www.w3.org/ns/earl#",

  "cnt": "http://www.w3.org/2011/content#",
  "dct": "http://purl.org/dc/terms/",
  "earl": "http://www.w3.org/ns/earl#",
  "foaf": "http://xmlns.com/foaf/0.1/",
  "htp": "http://www.w3.org/2011/http#",
  "ptr": "https://www.w3.org/2009/pointers#",
  "schema": "http://schema.org/",
  "xsd": "https://www.w3.org/2001/XMLSchema#",

  "WCAG20": "https://www.w3.org/TR/WCAG20#",
  "WCAG21": "https://www.w3.org/TR/WCAG21#",
  "ACT-RULES-CG": "https://act-rules.github.io/",

  "WebSite": "schema:WebSite",
  "WebPage": "schema:WebPage",

  "title": "dct:title",
  "description": "dct:description",
  "date": "dct:date",
  "hasVersion": "dct:hasVesion", 
  "isPartOf": "dct:isPartOf", 
  "hasPart": "dct:hasPart",
  "source": "dct:source",

  "Agent": "foaf:Agent",
  "Person": "foaf:Person",
  "Organization": "foaf:Organization",
  "Group": "foaf:Group",
  "Document": "foaf:Document",
  "name": "foaf:name",
  "firstName": "foaf:firstName",
  "surname": "foaf:surname",
  "mbox": "foaf:mbox",
  "mbox_sha1sum": "foaf:mbox_sha1sum",
  "member": "foaf:member",
  "homepage": "foaf:homepage",

  "assertedBy": { "@type": "@id" },
  "subject": { "@type": "@id" },
  "test": { "@type": "@id" },
  "mode": { "@type": "@id" },
  "outcome": { "@type": "@id" },
  "pointer": {
    "@id": "earl:pointer",
    "@type": "ptr:CSSSelectorPointer"
  }
}
```

Appendix 2: Acknowledgments {#Acknowledgments}
===========================

This section is *non-normative*.


Participants of the AG WG active in the development of this document {#participants}
--------------------------------------------------------------------

Shadi Abou-Zahra, Trevor Bostic, Romain Deltour, Kathy Eng, Wilco Fiers, Alistair Garrison, Kasper Isager, Maureen Kraft, Mary Jo Mueller, Jey Nandakumar, Charu Pandhi, Stein Erik Skotkjerra, Anne Thyme Nørregaard, Kathleen Wahlbin


Enabling funders {#enabling-funders}
----------------

This publication has been developed with support from the [WAI-Tools Project](https://www.w3.org/WAI/about/projects/wai-tools/), co-funded by the European Commission (EC) under the Horizon 2020 Program (Grant Agreement 780057). The content of this publication does not necessarily reflect the views or policies of the European Commission (EC) or any of the European Union (EU) Member States.


Appendix 3: Change History {#Change_History}
==========================

This section is *non-normative*.

No substantial changes have been made since the previous [Candidate Recommendation draft of 16 April 2019](https://www.w3.org/TR/2019/CR-act-rules-format-1.0-20190416/). The following editorial changes have been made since the previous draft:

<ul>
  <li><strong>1. Introduction:</strong> Added relationship of ACT Rules to WCAG 2 Techniques</li>
  <li><strong>1. Introduction:</strong> Removed unintended word "must" (was never a requirement)</li>
  <li><strong>4. Rule Structure:</strong> Clarified that optional parts are a MAY requirement</li>
  <li><strong>4.1. Rule Identifier:</strong> Moved requirements on versioning here from 4.11. Changelog</li>
  <li><strong>4.1. Rule Identifier:</strong> Clarified scope of uniqueness of an identifier</li>
  <li><strong>4.5.1. Input Aspects:</strong> Moved description of serving methods further down</li>
  <li><strong>4.7.1. Expectations for Atomic Rules:</strong> Expanded note on complex aggregation</li>
  <li><strong>4.14. Background:</strong> Removed unintended word "should" (was never a requirement)</li>
  <li><strong>Appendix 1. Expressing ACT Results:</strong> Major revision (non-normative examples)</li>
  <li><strong>Overall:</strong> Edits to align and clarify examples throughout the document</li>
  <li><strong>Overall:</strong> Fixing typographical, grammatical, and spelling mistakes throughout</li>
  <li><strong>Overall:</strong> Changed coding of RFC 2119 terms to improve accessibility/semantic</li>
</ul>

All changes from the previous published version can be viewed using the [April 2019 to July 2019 diff link](https://services.w3.org/htmldiff?doc1=https%3A%2F%2Fwww.w3.org%2FTR%2F2019%2FCR-act-rules-format-1.0-20190416%2F&doc2=https%3A%2F%2Fw3c.github.io%2Fwcag-act%2Fact-rules-format.html)