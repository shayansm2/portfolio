+++
date = '2024-12-16T09:14:38+03:30'
draft = true
title = 'My Personal Journey into Learning Kubernetes'
+++

For the last three months, I’ve been diving deep into Kubernetes as part of my new job, and I decided to write this blog to share my journey in learning Kubernetes. If you work in a DevOps role or your company operates on Kubernetes, understanding it inside and out is essential. However, as a software engineer, I also encourage every other software engineer to learn Kubernetes. Here’s why:

1. **The Rise of No-Ops**  
   With the growing popularity of cloud solutions, there’s a noticeable shift from DevOps to No-Ops. Catching this trend early can put you ahead of the curve.
2. **The Transformation to Generalists**  
   The job market is evolving, thanks to advancements in GenAI and LLMs. Specialized roles like "Django Back-End Developer," "React Front-End Developer," or "DevOps Specialist" are increasingly giving way to more generalist roles. Today, I see more "full-function software engineers" whose responsibilities include designing solutions, coding both client and server sides, configuring builds, deploying to production, and delivering the final product. Based on this, I believe it’s becoming crucial for software engineers to develop cloud and Kubernetes skills.
3. **A Masterclass in Design and Architecture**  
   Kubernetes' design is elegant and showcases some of the best practices in software architecture and design patterns. When you explore its components, it’s like watching Lego pieces come together to form a self-reliable infrastructure. The way Kubernetes uses separation of concerns and well-defined abstractions is inspiring—it’s no surprise that it has become the new standard for cloud and DevOps.

All that aside, these are the resources I found most useful for learning and working with Kubernetes.

### Resources to Learn Kubernetes

I prefer to start by getting a big-picture understanding and then dive deeper into the details. For this reason, I recommend beginning your Kubernetes journey by watching YouTube videos. Here are two excellent videos from [Techworld with Nana](https://www.youtube.com/@TechWorldwithNana) that I found incredibly helpful:

- [**Kubernetes Crash Course for Absolute Beginners**](https://youtu.be/s_o8dwzRlu4?si=qto_Q): A 1-hour introductory course.
- [**Kubernetes Tutorial for Beginners**](https://youtu.be/X48VuDVv0do?si=7afRBw6iVUVAFhRi): A more detailed 4-hour course.

Once you have a general understanding of Kubernetes, you can move on to more detailed resources. I’ve explored these two books, but I’m sure there are many other excellent options out there:

- **[Kubernetes in Action](https://www.manning.com/books/kubernetes-in-action)**  
   This is a fantastic book that walks you through Kubernetes concepts at a steady pace. It was recommended to me by my tech lead and does a brilliant job of explaining not only _how_ Kubernetes works but also the _why_ behind its design decisions. While reading it, you’ll not only learn how to work with Kubernetes but also gain insights into software design and architecture principles, such as separation of concerns (from SOLID principles) and abstraction. These are what make Kubernetes such a great tool for a wide range of use cases. That said, this book can feel overwhelming if you’re just looking to quickly understand how to use Kubernetes. If that’s the case, the next book might be a better starting point.
- **[Learn Kubernetes in a Month of Lunches](https://www.manning.com/books/learn-kubernetes-in-a-month-of-lunches)**  
   This book takes a more practical approach while still covering all the essential Kubernetes concepts. It’s lighter than the previous book and includes hands-on experiments and labs to help you grasp the concepts through practice. While it doesn’t dive as deep as _Kubernetes in Action_, it explores interesting applications and use cases that grabbed my attention when I decided to read it. For example, it covers topics like connecting Elasticsearch to Kubernetes for better log management, integrating Kubernetes with Prometheus for metrics monitoring, and using Helm as a Kubernetes package manager.

However, just by reading these materials, you won’t become a Kubernetes expert. It’s crucial to get hands-on experience and “get your hands dirty.”

### Resources to Play With Kubernetes

If you prefer experimenting with Kubernetes locally, you can use one of the following tools:

- [**k3s**](https://k3s.io/) (a lighter version of Kubernetes)
- [**Minikube**](https://minikube.sigs.k8s.io/docs/)
- [**Kind**](https://kind.sigs.k8s.io/)
- [**Docker Desktop Kubernetes Server**](https://docs.docker.com/desktop/features/kubernetes/)

If you’re unsure how to set up a local Kubernetes cluster, you can search online, ask ChatGPT, or refer to the first chapter of _Learn Kubernetes in a Month of Lunches_, which provides clear instructions.

If you prefer working in the cloud and avoiding any potential mess on your desktop computer (_I prefer this too_), here are some suggestions:

- **[Play with Kubernetes](https://labs.play-with-k8s.com/)**  
   This site allows you to create nodes, launch Kubernetes worker and control plane nodes, and interact with them using `kubectl`—all **for free**. Each session lasts for 4 hours, and as far as I’ve checked, there’s no daily usage limit. The only downside is that you cannot access applications you create (using services or port-forwarding) via the given URL. This appears to be a bug that has been reported on their GitHub.
- **[iximiuz Labs](https://labs.iximiuz.com/)**  
   This platform offers various tutorials and challenges (which I haven’t explored yet), as well as a Kubernetes playground where you can use Kubernetes for **free** in 2-hour sessions per day. If you need more time, their Premium plan provides extended access to labs and additional content.
- **[GitHub Codespaces](https://github.com/features/codespaces)**  
   This is my favorite solution. You can fork a repository (e.g., I forked [this one](https://github.com/sixeyed/kiamol), which contains the files and labs from _Learn Kubernetes in a Month of Lunches_) and use Codespaces to create and experiment with your Kubernetes cluster. The great thing about Codespaces is that it comes pre-installed with tools like `docker` and `kubectl`. Plus, the first 120 hours per month are **free**. I use [Kind](https://kind.sigs.k8s.io/) to create my cluster by following these steps:

1. Create a `kind-config.yaml` file with the following configuration:

```yaml
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
  - role: control-plane
  - role: worker
```

2. Run the following commands in the terminal to download Kind, set it up, and create a Kubernetes cluster with two nodes (one control-plane and one worker):

```bash
[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.25.0/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind
kind create cluster --config kind-config.yaml
```

Lastly, there are tools that can simplify the Kubernetes experience. You can explore these and decide which ones best suit your needs.

### Tools

- **[kubectl](https://kubernetes.io/docs/reference/kubectl/)**  
   This is the official command-line tool for interacting with Kubernetes. Most books and resources use `kubectl` as it is the standard way of managing Kubernetes. However, for beginners, `kubectl` can feel overwhelming—it might seem slow, confusing, and packed with options without any visual aids.
  If you find it frustrating, I recommend exploring other tools until you become more familiar with Kubernetes concepts, after which you can gradually move back to `kubectl`.
  To make working with `kubectl` more efficient, take advantage of aliases. Aliases can speed up your workflow and allow you to create fun, complex commands that are easily accessible. While there are many popular alias collections available (like this [GitHub repo](https://github.com/ahmetb/kubectl-aliases)), I personally recommend creating your own. This can be both educational and rewarding. For example, you can create a simple alias like the following and add it to your `.bashrc` or `.zshrc` file:

```bash
ky() {
    kubectl get "$1" -o yaml | less
}
```

- **[k9s](https://k9scli.io/)**  
   According to the [Thoughtworks 2024 Technology Radar](https://www.thoughtworks.com/en-de/radar/tools/summary/k9s), k9s is a tool worth adopting. It provides a terminal-based visualization layer on top of `kubectl`. With `k9s`, it’s much faster to navigate through resources, search for details, view logs, and inspect events.
  That said, don’t get too dependent on it. While k9s is excellent for quick navigation, it doesn’t offer all the features of `kubectl`. Always make sure you know how to perform the same tasks using `kubectl`.
- **[Lens](https://k8slens.dev/)**  
   While I haven’t personally used Lens, I’ve heard a lot of good things about it. Lens is a visualization tool for Kubernetes, offering an IDE-like experience on top of `kubectl`. Like k9s, it can be a helpful starting point for exploring and discovering Kubernetes. Once you’re comfortable, you can decide whether to stick with tools like Lens or transition fully to `kubectl`.
- **Other Tools** - **[Cyphernet](https://cyphernet.es/)**: Allows you to query Kubernetes resources using Cypher language. - **[Steampipe](https://hub.steampipe.io/plugins/turbot/kubernetes)**: Enables querying Kubernetes resources with SQL.  
   These tools are fun to have in your toolkit but are not alternatives to replace `kubectl`. There was an interesting discussion on [Hacker News](https://news.ycombinator.com/item?id=42427916) about these tools, which I think is worth reading.
  From my experience, the more senior and professional a developer is, the more they rely on `kubectl` and the less they depend on other tools.

And finally, if you’re curious why it’s called **k8s**, here’s the reason:
![alt text](https://substackcdn.com/image/fetch/w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F499e6a38-b05b-4c03-9cf3-149cc218dd13_551x140.png)
Thank you for reading my blog! I’d love to hear about your experiences with learning Kubernetes and any suggestions you might have for resources or tools. Feel free to share your thoughts.
