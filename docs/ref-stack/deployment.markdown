---
layout: default
title: Deployment of Reference Stack Components
nav_order: 210
parent: Reference Stack Details
has_children: false
---

# Deployment of the Reference Stack Components

We are working on easy to use examples for all the components in various deployment configurations. For now, here is some guidance for getting started.

## LM Evaluation Harness Installation

To install [LM Evaluation Harness](https://www.eleuther.ai/projects/large-language-model-evaluation){:target="lm-site"}, use the following commands, taken from the  `lm-evaluation-harness` repo [README](https://github.com/EleutherAI/lm-evaluation-harness){:target="lm-repo"}:

```shell
git clone --depth 1 https://github.com/EleutherAI/lm-evaluation-harness
cd lm-evaluation-harness
pip install -e .
```

The [README](https://github.com/EleutherAI/lm-evaluation-harness){:target="lm-repo"} has examples and other ways to run the tools and specific evaluations in different deployment scenarios.

## Unitxt Examples

Several examples using [`unitxt`](https://www.unitxt.ai){:target="unitxt"} are available in the [IBM Granite Community](https://github.com/ibm-granite-community){:target="igc"}, e.g., in the [Granite &ldquo;Snack&rdquo; Cookbook](https://github.com/ibm-granite-community/granite-snack-cookbook){:target="igc-snack"} repo. See the [`recipes/Evaluation`](https://github.com/ibm-granite-community/granite-snack-cookbook/tree/main/recipes/Evaluation){:target="igc-snack-eval"} folder. These examples only require running [Jupyter](https://jupyter.org/){:target="jupyter"} locally, because all inference is done remotely by the community's back-end services. Here are the specific Jupyter notebooks:

* [`Unitxt_Quick_Start.ipynb`](https://github.com/ibm-granite-community/granite-snack-cookbook/tree/main/recipes/Evaluation/Unitxt_Quick_Start.ipynb){:target="igc-snack-eval1"} - A quick introduction to `unitxt`.
* [`Unitxt_Demo_Strategies.ipynb`](https://github.com/ibm-granite-community/granite-snack-cookbook/tree/main/recipes/Evaluation/Unitxt_Demo_Strategies.ipynb){:target="igc-snack-eval2"} - Various ways to use `unitxt`.
* [`Unitxt_Granite_as_Judge.ipynb`](https://github.com/ibm-granite-community/granite-snack-cookbook/tree/main/recipes/Evaluation/Unitxt_Granite_as_Judge.ipynb){:target="igc-snack-eval3"} - Using `unitxt` to drive the _LLM as a judge_ pattern.

## Using LM Evaluation Harness and Unitxt Together

Start on this [Unitxt page](https://www.unitxt.ai/en/latest/docs/lm_eval.html){:target="unitxt-lm-eval"}. Then look at the [`unitxt` tasks](https://github.com/EleutherAI/lm-evaluation-harness/tree/main/lm_eval/tasks/unitxt){:target="unitxt-lm-eval2"} described in the [`lm-evaluation-harness`](https://github.com/EleutherAI/lm-evaluation-harness){:target="lm-eval"} repo.

## EvalAssist

One popular evaluation technique is _LLM as a judge_, which uses a smart &ldquo;teacher model&rdquo; to evaluate the quality of benchmark datasets and model responses, because having humans do this is expensive and not sufficiently scalable. (This is different from data synthesis with a teacher model.) [`EvalAssist`](https://ibm.github.io/eval-assist/){:target="eval-assist"} is designed to make writing these kinds of evaluations easier, including incremental development. It uses `unitxt` to implement evaluations.

## Observability with Arize Phoenix

[Arize Phoenix](https://phoenix.arize.com/){:target="phoenix"} ([GitHub](https://github.com/Arize-ai/phoenix){:target="phoenix-gh"}) is an open-source LLM tracing and evaluation platform designed to provide seamless support for evaluating, experimenting, and optimizing AI applications.

See the [home page](https://phoenix.arize.com/){:target="phoenix"} for details on installing and using Phoenix. We are working on an example deployment that demonstrates the integration with the rest of the reference stack discussed above.
