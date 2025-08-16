# Introduction to Flyte

- What is Flyte? -> quick summary
- What problem does Flyte solve?
- Some highlight

Flyte is a workflow orchestration platform built for running tasks at massive scale. It is
designed for large-scale clusters, delivering high concurrency, scalability, and
maintainability for production-grade workflows.

Originally developed by Lyft, Flyte is trusted by leading companies like Tesla, Spotify,
LinkedIn, and Toyota, running over 30 million tasks per day on the platform.
In a recent LinkedIn Engineering blog, the team unveiled their next-generation AI
pipelines powered by Flyte, enabling 20–30× faster training and launch times, and the
ability to train models 200× larger^1.



[1] https://www.linkedin.com/blog/engineering/infrastructure/openconnect-linkedins-next-generation-ai-pipeline-ecosystem

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

## Challenges in Previous ML Orchestration Platforms

> Reference here: https://eng.lyft.com/introducing-flyte-cloud-native-machine-learning-and-data-processing-platform-fb2bb3046a59

- Skip for now and try to finish following first :P

- List things out in bullet point with simple description


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
