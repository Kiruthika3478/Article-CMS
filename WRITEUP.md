# Write-up Template

### Analyze, choose, and justify the appropriate resource option for deploying the app.

*For **both** a VM or App Service solution for the CMS app:*
- *Analyze costs, scalability, availability, and workflow*
    A. Virtual Machine (VM) Analysis
    1. Cost
    Virtual Machines are more expensive because they charge for compute continuously, even when not in use, and they also require payment for additional components such as the OS disk, network interface, and public IP. Costs increase when scaling to larger VM sizes, and even when the VM is stopped, storage charges still apply.
    2. Scalability
    Scalability on a VM is not automatic and requires manual setup, such as creating additional VMs, configuring VM Scale Sets, and setting up load balancers, making the overall scaling process more complex.
    3. Availability
    With a VM, you are responsible for managing uptime, OS patching, monitoring, and failover configuration, and achieving high availability requires additional setup through Availability Sets or Availability Zones.
    4. Workflow
    Using a VM requires full server management, including connecting through SSH, installing necessary software like Python, Nginx, and ODBC drivers, configuring certificates and firewall rules, and handling deployments manually unless CI/CD pipelines are created, which increases operational effort.

    B. App Service Analysis
    1. Cost
    App Service is more cost‑efficient because you only pay for the App Service Plan, and there is no additional cost for OS disks or network infrastructure; it even supports a free tier suitable for development and testing.
    2. Scalability
    Scaling an App Service is very simple, as you can scale up by changing the plan or scale out through built‑in options, with support for automatic scaling without requiring any manual server configuration.
    3. Availability
    App Service provides built‑in availability because Azure automatically manages load balancing, redundancy, OS patching, and runtime updates, with higher‑tier plans offering SLAs above 99.95%.
    4. Workflow
    The workflow with App Service is much easier since deployments can happen directly from GitHub or zip packages, environment variables are managed through the portal, and logs and console access are readily available, making it ideal for Flask and Python applications.

- *Choose the appropriate solution (VM or App Service) for deploying the app*
    I chose to deploy the CMS application using Azure App Service rather than a VM.

- *Justify your choice*
    Justification:
    Lower maintenance: App Service removes the need to manage OS, runtime, and patches.
    Simpler workflow: Deployment through GitHub is fast and reliable.
    Easy scaling: Scaling requires only a button click, unlike VM-based manual scaling.
    Cost effective: Free or Basic tiers are more than enough for this project and cheaper than running a VM 24/7.
    Built-in availability: Azure handles redundancy and ensures continuous operation.

### Assess app changes that would change your decision.

*Detail how the app and any other needs would have to change for you to change your decision in the last section.* 
    1.I would switch to a VM if the application needed full control over the operating system, such as installing custom drivers or setting up advanced networking.
    2.A VM would be necessary if the app required heavy CPU or GPU power for tasks like image processing, machine learning, or video transcoding.
    3.I would use a VM if the application needed software or services that App Service cannot run, such as special web servers or background daemons.
    4.Switching to a VM would also require changes to deployment and infrastructure, including SSH-based deployment scripts, load balancers for scaling, monitoring tools, and OS patch management.