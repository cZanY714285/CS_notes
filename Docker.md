# the Difference between Docker & Scoop & Anaconda
1. Docker
   Docker is like an insulated lunchbox that contains fruit, vagetables and meat in different compartments. Everyone, even those whose dinner table (computer) is empty and has nothing installed, or those whose kitchen is dirty, empty, or broken (your system lacks dependencies) can enjoy the same food directly everywhere. Also, we can say that it is a package isolating from my dinner table (computer), so i won't get my kitchen dirty. It’s fully **self-contained**.
2. Scoop
   Scoop is like a fast, efficient food shop where you can order different types of food (software) with a single command `scoop install xxx` instead of running around different markets (different websites) to buy them separately.
   Sccop is the only one between this three that only works on Windows
3. Anaconda
   Anaconda is like a huge tool storehouse filled with **pre-organized** toolboxes for different tasks. Each toolbox (environment) contains specific tools (packages) needed for a particular job. Instead of installing and uninstalling tools every time you **switch** jobs, you just grab the toolbox (environment) you need and start working.

|      Feature       |                        **Docker**                         |                     **Scoop**                     |                  **Anaconda**                   |
| :----------------: | :-------------------------------------------------------: | :-----------------------------------------------: | :---------------------------------------------: |
|    **Analogy**     | Insulated lunchbox with everything needed to eat anywhere |  Fast food shop that delivers software instantly  | Specialized tool storehouse for Python projects |
|  **Main Purpose**  |    Runs applications in isolated, portable containers     |       Installs & manages Windows CLI tools        |   Manages Python environments & dependencies    |
| **Where It Works** |                    Windows, Mac, Linux                    |                   Windows only                    |               Windows, Mac, Linux               |
| **What It Solves** |     "Works on my machine" problem & deployment issues     |      Tedious manual installation of software      |       Python version & package conflicts        |
| **Best Use Case**  |    Running web apps, services, and cloud applications     | Installing Git, Python, Node.js on Windows easily |         Machine learning & data science         |
# What is Docker?
Docker allows you to separate your applications from your infrastructure so you can deliver software quickly. With Docker, you can manage your infrastructure in the same ways you manage your applications.
# Install Docker for Windows
there're two ways:
1. install docker on this offical website [dockerdocs](https://docs.docker.com/desktop/setup/install/).
2. use scoop to install docker. [[Scoop]]