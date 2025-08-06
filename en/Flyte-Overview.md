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

## Challenges in Previous ML Orchestration Platforms

> Reference here: https://eng.lyft.com/introducing-flyte-cloud-native-machine-learning-and-data-processing-platform-fb2bb3046a59

- Skip for now and try to finish following first :P

- List things out in bullet point with simple description


## Flyte Features 

- Input/output caching
- workflow versioning
- Decoupled control plane (FlyteAdmin) and data plane (FlytePropeller)
    - This allows users to register their workflows once against a single control plane
    and execute them across any clusters
    - keep data in on-prem cluster
- Migrate nodes (Disruption readiness)
    - Disrupted jobs exit with a special error code, prompting Flyte to retry the job on a new set of nodes
    - Also start from checkpoint?? -> check
- Connect other services through "Agent"
    - E.g. Enable dispatch workflows to platforms like Databricks
    - User can build their own agent easily with Python
