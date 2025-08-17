# Introduction to Flyte


Since the term *big data* first introduced in the early 1990s, the volume of global data has grown at an exponential pace. As machine learning continues to rise, companies are building countless AI pipelines to solve real-world business problems, from predicting ad clicks to personalizing recommendations.

At its core, an AI pipeline can be thought of as:

$$
\text{AI Pipeline = Code + Data [1]}
$$

But in practice, building and managing these pipelines is far from simple. Developers often face two major challenges:

1. **Data flow.** Ensure data moves smoothly across a complex workflow of preprocessing, model training, serving, and evaluation.
2. **Deployment.** Ship code reliably into production without endless manual fixes.

To address these pain points, Lyft created Flyte [2], an open-source orchestration platform designed to support tens of thousands of AI pipelines at scale.

Flyte tackles five specific challenges that AI teams commonly face:

1. Reusability: Reuse components across pipelines and business units, avoiding “reinventing the wheel."
2. Reproducibility: Ensure experiments can be replicated by mirroring dev environments in production.
3. Scalability: Handle massive growth in requests and data with efficient concurrency.
4. Maintainability: Operate and update thousands of pipelines with ease.
5. Extensibility: Integrate smoothly with third-party tools and services.

Today, Flyte is trusted by leading companies such as Tesla, Spotify, LinkedIn, and Toyota, and runs over 30 million tasks per day. For example, in a recent LinkedIn Engineering blog [3], the team unveiled their next-generation AI pipelines powered by Flyte, achieving 20–30× faster training and launch times, while enabling them to train models 200× larger than before.


## Flyte Features 

This section highlights key Flyte features with brief overviews. Detailed articles
covering each topic will be published in future articles.

- Output Caching
    - Flyte automatically saves task results. When the same task runs again with identical
    inputs, Flyte reuses the cached output instead of re-executing the task, saving time
    and compute resources.
- Workflow Versioning
    - Flyte creates immutable versions of workflows, allowing different versions to run
    simultaneously without conflicts. When updating workflows, unchanged tasks can still
    reuse their cached results, avoiding unnecessary re-execution.
- Multi-Cluster Management
    - Flyte separates workflow management from execution, allowing you to define workflows once in a central location and run them across
  multiple compute clusters as needed.
    - (Put image from LinkedIn Engineering blog [Figure 8: Flyte multi-region routing
    setup])
- Automatic Recovery
    - When servers fail or need maintenance, Flyte automatically moves tasks to working
    machines. Tasks can resume from where they left off instead of starting over,
    minimizing lost work.
- Connect External Services
    - Flyte can run tasks on popular data platforms like Databricks, Snowflake, and AWS
    Batch while still providing centralized workflow management, monitoring, and error
    handling.


## How to Run Workflow in Flyte?

> 我們可能需要一個快速的 overview 說 Flyte 怎麼用? 還不確定要放哪

The most basic use case of Flyte is to create the workflow (a DAG) containing multiple
tasks with simple Python syntax (see below). Then we can run the workflow in cluster Pod
with `pyflyte run --remote task.py wf`. You can then see the pod is created for executing
tasks, and status is updated to the Flyte console, which is the dashboard. How simple it
is!

(Put the code/screenshot here)

By running the workflow, we can access the Flyte console with the URL printed in the
terminal. Flyte console is an UI interface for monitoring the workflow status, loggings,
and do other operations like retrying.

(Put the Flyte console image here)


## References
[1] [A Chat with Andrew on MLOps: From Model-centric to Data-centric AI](https://www.youtube.com/watch?v=06-AZXmwHjo) <br>
[2] [Flyte OSS](https://www.union.ai/docs/v1/flyte/user-guide/) <br>
[3] [OpenConnect: LinkedIn’s next-generation AI pipeline ecosystem](https://www.linkedin.com/blog/engineering/infrastructure/openconnect-linkedins-next-generation-ai-pipeline-ecosystem) <br>