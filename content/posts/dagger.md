+++
date = '2024-10-22T09:18:06+03:30'
title = 'Dagger CI'
+++

I was recently introduced to [dagger.io](https://dagger.io/) by my tech lead. Dagger is a CI tool created by Solomon Hykes, who is also the founder of Docker. I listened to his interview on the [kubernetes podcast](https://kubernetespodcast.com/episode/236-dagger/) and several aspects about the motivation behind Dagger caught my attention.

The most interesting aspect of Dagger is its objective to provide a separation of concerns. These days, the CI code and configuration you write are often tightly coupled with the specific technology or infrastructure you are using. For example, gitlab-ci.yaml files are tailored for GitLab runners, and GitHub Actions has its own unique file format. Dagger aims to unify CI pipeline configurations and code, making them executable anywhere—similar to Docker.

Another compelling feature of Dagger is its ability to execute CI pipelines anywhere, even locally. This can significantly reduce the feedback loop time for development teams when fixing and maintaining their code. The Dagger engine ensures the CI pipeline runs consistently on any machine.

Lastly, what I found particularly interesting is that Dagger's team believes CI pipelines should be written in code, not in JSON or YAML files. As Solomon pointed out, the complexity of CI pipelines is often better expressed through code rather than YAML. They have developed SDKs in Python, Golang, and TypeScript, with plans to expand to other languages like Java and PHP. These SDKs are declarative and communicate with the Dagger engine through GraphQL APIs to define the desired pipeline.

In addition to the podcast, you can watch this [youtube](https://www.youtube.com/watch?v=S_Z4AHZlSUI) from KubeCon for more insights into Dagger.
