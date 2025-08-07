---
layout: default
title: Reference Stack Details
nav_order: 20
has_children: true
---

# Evaluation Reference Stack Details

Recall we said on the [home page]({{site.baseurl}}) that the reference stack provides the &ldquo;runtime&rdquo; for evaluations, but the set of evaluations themselves has to be provided. The companion AI Alliance projects, [Evaluation Is for Everyone](https://the-ai-alliance.github.io/trust-safety-evals/){:target="_blank"} and [Achieving Confidence in Enterprise AI Applications](https://the-ai-alliance.github.io/ai-application-testing/){:target="_blank"} focus on defining the evaluations themselves (e.g., for hate speech, hallucinations, testing, etc.), which are deployed on the reference stack. 

So, the rest of this website focuses on the components in the reference stack and doesn't cover the details of writing evaluations themselves, except where useful for expository purposes. See the companion Alliance projects and the documentation for the tools discussed below for all the details.

## The Requirements for the Reference Stack

First, let's summarize the requirements for the stack, which the components described below were selected to satisfy.

### Deployment Options

An evaluation deployment must support public leaderboards, as well private deployments for research and development (R&D) tasks, such as evaluating models under development that may be released to the public or kept proprietary. These are examples of _offline_ evaluation in the sense that the evaluations can be run when needed and the results cached for later viewing and analysis. Hence, relatively easy deployment and management in diverse environments are important, including &ldquo;hyperscalar&rdquo; cloud platforms, Kubernetes, &ldquo;bare metal&rdquo; servers, personal workstations, etc.

The stack must also support _online_ evaluation, where evaluation happens on demand as part of the control flow that includes model inference and tool invocations. Here, fast and efficient execution, horizontal scaling, and failure resilience are essential.

### The Kinds of Evaluations

Most evaluation tools tools emerged to support R&D of models where experts needed to measure how well the models performed certain functions, like text and image generation, language translation, instruction following, mathematical problem solving, and logical reasoning. Also, they wanted to measure how well models avoided hallucination, generation of undesirable content, etc. These objectives remain important.

Evaluation needs are broadening, however. The [Achieving Confidence in Enterprise AI Applications](https://the-ai-alliance.github.io/ai-application-testing/){:target="_blank"} project focuses on how existing evaluation tools and techniques can be used by application developers to evaluate how well their models and applications support specific requirements and use cases. As that project [explains](https://the-ai-alliance.github.io/ai-application-testing/#the-challenge-we-face){:target="_blank"}, traditional testing tools, which lean heavily on deterministic behavior, breakdown when probabilistic outputs are inherent system properties, as they are for generative models. Effectively handling probabilistic behaviors requires the same statistical evaluation and analysis tools AI experts have been using, adapted appropriately for these new testing needs.

Hence, the reference stack must be as flexible as possible to support existing evaluation techniques, including data management and execution, while adapting to new requirements as they emerge, such as integration with traditional developer testing tools.

### Ease of Use and Backwards Compatibility

In general, the reference stack needs to be sufficiently usable by software developers and system administrators who are not AI evaluation experts, but need to deploy and use these tools in their R&D and production environments.

Many evaluation suites have been implemented already by R&D teams around the world, often with ad hoc tools. The reference stack needs to support execution of as many of them as possible, or at least the most widely used suites.

## What Is in the Reference Stack?

Schematically, **Figure 1** shows an evaluation deployment of the reference stack with some example evaluators:

<div class="text-center">
	<img src="{{site.baseurl}}/assets/images/reference-stack-diagram.png" alt="Reference stack deployment"/>
	<br/>
	<b>Figure 1:</b> Reference stack deployment.
</div>

There is currently no industry-standard evaluation stack, but several tools have achieved wide adoption, which we focus on.

| Name | URLs | Description |
| :--- | :--- | :---------- |
| EleutherAI’s LM Evaluation Harness | [website](https://www.eleuther.ai/projects/large-language-model-evaluation){:target="lm-site"}<br/>[`lm-evaluation-harness` repo](https://github.com/EleutherAI/lm-evaluation-harness){:target="lm-repo"} | A widely used, efficient evaluation platform for inference time (i.e., runtime) evaluation and for leaderboards. |
| IBM’s Unitxt | [website](https://www.unitxt.ai){:target="unitxt"}<br/>[`unitxt` repo](https://github.com/IBM/unitxt/){:target="unitxt-repo"} | A library for writing and running individual evaluations, which has an interesting benefit that evaluations can be _declaratively_ defined and executed without the need to write and execute third-party, possibly-untrusted code. |
| IBM's EvalAssist | [website](https://ibm.github.io/eval-assist/){:target="eval-assist"}<br/>[`eval-assist` repo](https://github.com/IBM/eval-assist){:target="eval-assist-repo"} | A relatively new tool that makes writing `unitxt`-based evaluations easier. Specifically, EvalAssist is an application that simplifies using LLMs as evaluations (LLM-as-a-Judge) of the output of other LLMs by supporting users in iteratively refining evaluation criteria in a web-based user experience, with other features designed for the incremental process of building evaluations.

The diagram in **Figure 1** suggests other authoring tools. None are supported by the reference stack at this time, but this may change as the stack matures.

`unitxt` evaluations can be executed by the `unitxt` runtime or using a plugin for `lm-evaluation-harness`, which has its own runtime. For &ldquo;personal&rdquo; use, e.g., a researcher testing some models on her workstation or a research cluster, these tools may be all that are needed. 

Larger evaluation activities, like team activities that run large suites over big models, routine regression testing, leaderboard management, and finally _online_ evaluation, will integrate these authoring and runtime tools into larger application stacks or platforms. Additional services will be required, some of which are mentioned in the following table.

| Name | URLs | Description |
| :--- | :--- | :---------- |
| Infosys' Responsible AI Toolkit | [repo](https://github.com/Infosys/Infosys-Responsible-AI-Toolkit){:target="irait"} | A suite of tools providing an integrated environment for a variety of evaluation purposes. |
| Meta's Llama Stack | [website](https://llama-stack.readthedocs.io/en/latest/){:target="mls"}<br/>[`llama-stack` repo](https://github.com/meta-llama/llama-stack){:target="mls-repo"} | A full-featured AI application stack that provides built-in integrations for evaluation tools, like [Llama Guard](https://www.llama.com/docs/model-cards-and-prompt-formats/llama-guard-4/){:target="mlg"}, for agents, [MCP](https://modelcontextprotocol.io/introduction){:target="mcp"} support, etc. The AI Alliance has [several initiatives](https://the-ai-alliance.github.io/#llama-stack-and-llama-stack-agents){:target="_blank"} involving Llama Stack. |

The diagram in **Figure 1** suggests other possible runtime tools and even _none_, for small deployments, like personal research experiments.

It's worth mentioning a few other production deployment options and support tools that were omitted from the diagram for simplicity. Large-scale and _online_ deployments will need to consider these and other options, like tools for observability, security, horizontal scaling, etc. Tools like [Arize Phoenix](https://phoenix.arize.com/){:target="phoenix"} provide AI-centric observability and metrics collection (discussed below). 


| Name | URLs | Description |
| :--- | :--- | :---------- |
| Arize's Phoenix | [website](https://phoenix.arize.com/){:target="phoenix"}<br/>[`phoenix` repo](https://github.com/Arize-ai/phoenix){:target="phoenix-repo"}) | An AI application-centric tool for observability and metrics collection. Real deployments of the reference stack need to provide these capabilities, but the stack needs to be agnostic about the specific tools used, as different deployments will use different tools. |
| Kubernetes | [website](https://kubernetes.io){:target="k8s"} | The de facto cluster management system, especially for on-premise deployments. Other deployments will use cloud environments like AWS, Azure, and Google Cloud, possibly with Kubernetes. |
| Experiment tracking | _N/A_ | It's easy to lose track of how different versions of models and applications perform against different evaluations, so tracking tools are essential. |
| Model and dataset and [_governance_]({{site.glossaryurl}}/#governance){:target="glossary"}  | _N/A_ | You will need to know exactly what datasets went into training and tuning specific model versions, which dataset versions were deployed to RAG systems, etc., and which model versions you are running in production. |

Also not shown are leaderboards and tools that use some of the components discussed here. Examples include IBM's [Risk Atlas Nexus](https://huggingface.co/spaces/ibm/risk-atlas-nexus){:target="ran"} and [SafetyBAT Leaderboard](https://huggingface.co/spaces/aialliance/safetybat){:target="sb"}, as well as many other leaderboards and benchmarks hosted on [Hugging Face](https://huggingface.co/){:target="hf"}. Risk Atlas Nexus and SafetyBAT provide accessible tools for viewing how different models perform against user-specified criteria. See [Leaderboards](https://the-ai-alliance.github.io/trust-safety-evals/leaderboards/leaderboards/){:target="tse-lb"} in the [Evaluation Is for Everyone](https://the-ai-alliance.github.io/trust-safety-evals/){:target="tse"} project for more details.
