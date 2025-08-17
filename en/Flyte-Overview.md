# Introduction to Flyte


Since the term *big data* first introduced in the early 1990s, the volume of global data has grown at an exponential pace. As machine learning continues to rise, companies are building countless AI pipelines to solve real-world business problems, from predicting ad clicks to personalizing recommendations.

At its core, an AI pipeline can be thought of as:

$$
\text{AI Pipeline = Code + Data [1]}
$$

But in practice, building and managing these pipelines is far from simple. Developers often face two major problems:

1. **Multi-cluster deployment** - Reliably ship code to production at scale, without endless manual fixes
2. **Data flow** - Ensure data moves smoothly across a complex workflow of preprocessing, model training, serving, and evaluation

To address these pain points, Lyft created Flyte [2], an open-source orchestration platform designed to support tens of thousands of AI pipelines at scale.

Flyte tackles five specific challenges that AI teams commonly face:

1. **Scalability** - Handle massive growth in requests and data with efficient concurrency
2. **Reusability** - Reuse components across pipelines and business units, avoiding “reinventing the wheel."
3. **Reproducibility** - Ensure experiments can be replicated by mirroring dev environments in production
4. **Maintainability** - Operate and update thousands of pipelines with ease
5. **Extensibility** - Integrate smoothly with third-party tools and services

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

The Flyte workflow can be defined through simple Python syntax that is similar to other
workflow orchastration tools.

(Put the code/screenshot here)

After defining the workflow, we can either executing it locally by `pyflyte run task.py
wf` for debugging locally or running on remote with `pyflyte run --remote task.py wf`.
When running on remote, Flyte automatically creates Kubernetes pods to execute tasks and
provides real-time status updates.

The command prints a URL to access Flyte Console, a web dashboard for monitoring workflow
progress, viewing logs, and managing operations like retries.

(Put the Flyte console image here)


## References
[1] [A Chat with Andrew on MLOps: From Model-centric to Data-centric AI](https://www.youtube.com/watch?v=06-AZXmwHjo) <br>
[2] [Flyte OSS](https://www.union.ai/docs/v1/flyte/user-guide/) <br>
[3] [OpenConnect: LinkedIn’s next-generation AI pipeline ecosystem](https://www.linkedin.com/blog/engineering/infrastructure/openconnect-linkedins-next-generation-ai-pipeline-ecosystem) <br>
