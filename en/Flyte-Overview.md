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

> 我們可能需要一個快速的 overview 說 Flyte 怎麼用? 還不確定要放哪

The most basic use case of Flyte is to create the workflow (a DAG) containing multiple
tasks with simple Python syntax (see below). Then we can run the workflow in cluster Pod
with `pyflyte run --remote task.py wf`. You can then see the pod is created for executing
tasks, and status is updated to the Flyte console, which is the dashboard. How simple it
is!

(Put the code/screenshot here)

## Challenges in Previous ML Orchestration Platforms

> Reference here: https://eng.lyft.com/introducing-flyte-cloud-native-machine-learning-and-data-processing-platform-fb2bb3046a59

- Skip for now and try to finish following first :P

- List things out in bullet point with simple description


## Flyte Features 

This section describe some highlight Flyte features. We will have more articles diving
into more details in each topic and we will do the brief overview in this article.

- Output caching
    - Flyte will cache the output for a task. If we later running the same task with same
    input, it will trigger cache hit and directly use the output from the cache rather
    than re-running the whole things.
- workflow versioning
    - Workflow in Flyte is versioned with all tasks as immutable. We can run differnet
    workflow versions with totally different structure simultaneously. Also, even if we
    change some tasks in the workflow, we can still leverage the cache for the unchanged
    task as long as its input is the same.
- Decoupled control plane (FlyteAdmin) and data plane (FlytePropeller)
    - Flyte control plane and data plane are natively decoupled, this allows users to
    register their workflow through a single control plane and execute them on multiple
    different clusters.
    - (Put image from LinkedIn Engineering blog [Figure 8: Flyte multi-region routing
    setup])
- Node Migration
    - In production multi-node environments, nodes may fail or require maintenance. Flyte
    automatically retries tasks on healthy nodes when disruptions occur. With
    checkpointing enabled, tasks resume from their last checkpoint rather than restarting
    completely.
- External Service Integration via Agents
    - Flyte Agents enable integration with external compute services like Databricks,
    Snowflake, and AWS Batch. Users can execute tasks on these external platforms while
    maintaining Flyte's workflow orchestration, monitoring, and retry capabilities.
