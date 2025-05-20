+++
date = '2025-02-05T09:31:37+03:30'
title = 'Temporal VS DBOS '
+++

I recently read [this article](https://www.dbos.dev/blog/what-is-lightweight-durable-execution) about a lightweight durable execution solution called DBOS. Meanwhile, I was working heavily with Temporal, a well-known open-source tool for durable executions. Technically, both serve the same purpose, but with major differences:

Temporal is heavyweight. To run it, you need a Temporal cluster, a database connected to the cluster, one or more Temporal workers, the Temporal UI, and finally, the Temporal SDK to trigger workflows from your application. On the other hand, DBOS is lightweight and requires only a database to store its data. The workflow runs within the same application that includes the DBOS library, whereas in Temporal, workflows run on separate resources called workers. Essentially, DBOS is a library, while Temporal is a full-fledged software solution that you interact with via its SDKs.

Temporal is an external orchestration solution written in Golang, with support for multiple languages through its SDKs. However, DBOS libraries are only available in TypeScript and Python, and I'm not sure whether they offer the same features in both languages.

Temporal encourages a microservices architecture. While it's possible to use it differently, Temporal is best suited for a microservices-based system, making it a great choice for structured, scalable organizations. You can even have workflows distributed across multiple services (workers), each with its own stack and language, and Temporal makes it work seamlessly. On the flip side, DBOS does not support multi-language or distributed architectures, as it runs entirely within your code. This makes it perfect for small-sized applications with no dependencies on external services or components.

These were my thoughts after reading the article. I'd love to hear yours!
