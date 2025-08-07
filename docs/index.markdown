---
layout: default
title: Home
nav_order: 10
has_children: false
---

# The Evaluation Reference Stack

_Part of the AI Alliance [**Trust and Safety Evaluation Initiative**](https://thealliance.ai/core-projects/trust-and-safety-evaluations){:target="tsei"} (TSEI), our goal is to create the world's most comprehensive and useful tool set and resources for anyone seeking to benchmark, evaluate, and monitor AI systems. Welcome to the **Evaluation Reference Stack** project, a foundation of that effort, to provide a de-facto standard, easy-to-use platform to run [evaluations]({{site.glossaryurl}}/#evaluation){:target="glossary"} of all kinds._

> **Tip:** The links for _italicized terms_ go to [this glossary]({{site.glossaryurl}}){:target="glossary"}.

There are many open-source and commercial frameworks for AI [_evaluation_]({{site.glossaryurl}}/#evaluation){:target="glossary"}, for example to detect hate speech and [_hallucination_]({{site.glossaryurl}}/#hallucination){:target="glossary"}, to measure the [_question-answering_]({{site.glossaryurl}}/#question-answering){:target="glossary"} abilities, etc. However, there are no real standards which are widely used by implementers, so that most evaluation suites require separate tools. Some suites and corresponding tools are better engineered for research purposes, while others are suitable for production deployments.

This project is identifying and endorsing evaluation tools that are already widely used, with the potential to become industry standards. These tools address the varied needs of both creators (researchers and system builders), as well as consumers of evaluations. Ideally, an evaluation platform supports _offline_ use, such as for [_benchmarks_]({{site.glossaryurl}}/#benchmark){:target="glossary"} and related testing purposes, as well as _online_ use, during inference and agent flows, where support is required for production-quality concerns, such as [_scalability_]({{site.glossaryurl}}/#scalability){:target="glossary"} and [_robustness_]({{site.glossaryurl}}/#robustness){:target="glossary"}.

Our goal is to enable enterprise developers, who are usually not evaluation experts, to quickly and easily deploy the runtime stack they need for executing evaluations online or offline. The companion AI Alliance projects, [Evaluation Is for Everyone](https://the-ai-alliance.github.io/trust-safety-evals/){:target="tse"} and [Achieving Confidence in Enterprise AI Applications](https://the-ai-alliance.github.io/ai-application-testing/){:target="aceaa"} focus on defining the evaluations themselves (e.g., for hate speech, hallucinations, etc.), which are deployed on the reference stack. 

**Figure 1** shows the relationship between these projects. 

<div class="text-center">
	<img src="{{site.baseurl}}/assets/images/projects-diagram.png" alt="Evaluation Reference Stack in Context"/>
	<br/>
	<b>Figure 1:</b> The reference stack in context.
</div>

Note that the evaluation reference stack _runs_ the evaluations that come from the other two projects.

Specifically, [Evaluation Is for Everyone](https://the-ai-alliance.github.io/trust-safety-evals/){:target="_blank"} is aimed at making it easy for developers to find and deploy the AI trust and safety evaluations they need, analogous to how [_cybersecurity_]({{site.glossaryurl}}/#security){:target="glossary"} capabilities must be included in all modern applications. The appropriate set of evaluations would run on the reference stack. 

Similarly, [Achieving Confidence in Enterprise AI Applications](https://the-ai-alliance.github.io/ai-application-testing/){:target="_blank"} addresses a current gap in AI-enabled application development; how to test that the applications behave as designed, when generative AI models are inherently _probabilistic_, instead of _deterministic_. The same evaluation tools AI experts use to evaluate models for trust and safety concerns can be applied to this problem. In other words, custom evaluations need to be written that test individual use cases and related requirements, and integrated into familiar test suites. In part, the _confidence_ project will help educate developers on how to use these tools effectively in combination with the testing and quality assurance (QA) tools they already use.

**Figure 1** also shows several possible components in the reference stack. We dive into the details in [Reference Stack Details]({{site.baseurl}}/ref-stack/ref-stack).

## Getting Involved

Are you interested in contributing? If so, please see the [Contributing]({{site.baseurl}}/contributing) page for information on how you can get involved. See the [About Us]({{site.baseurl}}/about) page for more details about this project and the AI Alliance.

## Additional Links

* The project's [GitHub repo](https://github.com/The-AI-Alliance/eval-ref-stack){:target="repo"}
* Companion projects:
	* <a href="https://the-ai-alliance.github.io/ai-application-testing/" target="acea">Achieving Confidence in Enterprise AI Applications</a>
	* <a href="https://the-ai-alliance.github.io/trust-safety-evals/" target="eie">Evaluation Is for Everyone</a>
* The AI Alliance: 
	* [Website](https://thealliance.ai){:target="ai-alliance"}
	* [The Trust and Safety Work Group](https://thealliance.ai/focus-areas/trust-and-safety){:target="ai-alliance-tns"} 
	* [Trust and Safety Evaluation Initiative](https://thealliance.ai/core-projects/trust-and-safety-evaluations){:target="tsei"}

| **Authors** | [The AI Alliance Trust and Safety Work Group](https://thealliance.ai/focus-areas/trust-and-safety){:target="ai-alliance-tns"} |
| **Last Update** | {{site.last_version}}, {{site.last_modified_timestamp}} |
