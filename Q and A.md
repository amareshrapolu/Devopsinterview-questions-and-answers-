Perfect 👍 Got it — you want each answer **4–5 lines long**, professional but still simple enough to speak naturally in an interview. I’ll expand all answers accordingly. Let’s go tool by tool.

---

# ✅ **Tool-Wise Questions with 4–5 Line Answers**

---

## 🔹 **Linux**

**11. What is the difference between a hard link & a soft link?**
👉 A hard link is like another name for the same file and points directly to the data on disk. If you delete the original file, the hard link still works. A soft link (symlink) is like a shortcut and points to the file path, not the actual data. If the original file is deleted, the soft link becomes broken.

**12. How would you check the available disk space and usage?**
👉 In Linux, I use `df -h` to check overall disk space in a human-readable format. If I need to check which folder is consuming more space, I use `du -sh <directory>`. Sometimes I also combine `find` with `du` to locate large files. This helps in troubleshooting disk issues effectively.

---

## 🔹 **Git / GitHub**

**4. How do you define branching strategies in your organization?**
👉 We follow the Git Flow branching strategy. The `main` branch is always stable and represents production. Developers create `feature` branches from `develop`, and once tested, these are merged back. Hotfixes are created directly from main to quickly patch production issues.

**17. What is a GitHub webhook?**
👉 A webhook in GitHub is used to automatically notify external services when an event happens in the repository. For example, when code is pushed, the webhook can trigger a Jenkins pipeline. This helps in automating CI/CD and reduces manual steps.

**27. How will you resolve conflict in Git?**
👉 First, I pull the latest code from the branch and identify the conflicted files. Then I open those files and manually decide which changes to keep. After fixing, I add the files, commit, and push again. I also discuss with teammates if it’s a big conflict.

**28. What is Git cherry-pick?**
👉 Cherry-pick allows me to take one specific commit from one branch and apply it to another. This is useful when I don’t want to merge a whole branch but need only one feature or bug fix. For example, I can cherry-pick a hotfix from `develop` into `main` without merging everything else.

---

## 🔹 **Jenkins**

**5. Explain the pipeline of your project and its purpose.**
👉 Our pipeline starts with code checkout from GitHub, followed by build and unit tests. Then SonarQube checks code quality, and if it passes, a Docker image is built and pushed to the registry. Finally, the image is deployed into dev, staging, or production. The purpose is full automation of CI/CD with minimum manual effort.

**9. What plugins have you used in your project?**
👉 We use Git and GitHub plugins for source code integration. Maven/Gradle for builds, Docker plugin for container builds, and SonarQube plugin for code quality analysis. Slack plugin is used for sending notifications to teams. Pipeline and Credentials plugins are also widely used.

**10. How many builds do you perform daily?**
👉 On average, we perform 10 to 15 builds daily depending on developer commits. Some are regular feature builds, while others are bug fixes or hotfix builds. During release times, the number of builds increases. Jenkins makes it easy to manage multiple builds in parallel.

**18. What is the master–slave architecture in Jenkins?**
👉 In this setup, the master node controls scheduling jobs and managing configurations. The slave nodes are used to run build tasks, tests, or deployments. This helps distribute workloads across multiple machines. It improves performance and avoids overloading the master.

**19. Explain the two types of pipelines in Jenkins.**
👉 Jenkins provides two pipeline types — Declarative and Scripted. Declarative pipelines use a simple, structured syntax and are easier to read and maintain. Scripted pipelines are written in Groovy and provide more flexibility and logic control. Most teams prefer declarative for standard CI/CD workflows.

**20. Explain Jenkins shared libraries and their benefits.**
👉 Shared libraries are reusable pipeline code stored in a Git repository. Instead of repeating the same pipeline steps across jobs, we just call the shared library. This makes pipelines consistent, easier to maintain, and faster to develop. It’s like having common functions for all Jenkins jobs.

**21. If you run both Spring Boot and Jenkins on the same EC2, same port 8080, will it work?**
👉 No, it will not work because only one process can use port 8080 at a time. Either Jenkins or Spring Boot will fail to start. To fix this, we need to change the port of one application, for example, run Spring Boot on port 8081. This ensures both can run together.

---

## 🔹 **SonarQube**

**13. Why do we use SonarQube and what are its use cases?**
👉 SonarQube is used to analyze code quality and detect issues like bugs, vulnerabilities, and code smells. It enforces coding standards and helps developers maintain clean and secure code. In CI/CD, SonarQube ensures code is reviewed automatically before deployment. This reduces risk and improves maintainability.

---

## 🔹 **AWS**

**14. What is a VPC in AWS?**
👉 A VPC is a virtual private network inside AWS where we launch our resources. We can create subnets, route tables, internet gateways, and security groups inside it. For example, web servers are placed in public subnets and databases in private subnets. It gives us full control of networking in the cloud.

**15. Have you worked with Auto Scaling Groups (ASG)?**
👉 Yes, ASGs automatically adjust the number of EC2 instances based on demand. If traffic increases, more instances are launched; if it decreases, instances are terminated. This saves cost and improves availability. In my project, we used ASGs for web servers to handle sudden traffic spikes.

**16. What is a Security Group in AWS?**
👉 A Security Group acts like a virtual firewall for EC2 instances. It controls inbound and outbound traffic based on rules. For example, I can allow only port 22 for SSH or 80/443 for web access. Unlike NACLs, Security Groups are stateful, so return traffic is automatically allowed.

**30. Can you describe a disaster recovery plan in AWS?**
👉 In one project, we set up a multi-AZ RDS and regular snapshots for disaster recovery. We also enabled S3 cross-region replication for critical data. During an AZ failure, traffic automatically shifted to another healthy AZ. This ensured business continuity with minimum downtime.

**31. What is AWS Secrets Manager?**
👉 Secrets Manager is used to store and manage sensitive data like database passwords, API keys, and tokens. It automatically rotates secrets and integrates with AWS services like RDS. This removes the need to hardcode credentials in code. It improves security and simplifies secret handling.

---

## 🔹 **Ansible**

**22. What are Ansible roles and how do you use them?**
👉 Ansible roles help organize playbooks into smaller, reusable components. Each role has tasks, variables, templates, and handlers. For example, I create a role for installing Docker and another for configuring Nginx. This keeps playbooks clean and modular, and multiple projects can reuse the same role.

---

## 🔹 **Docker**

**24. How do you set up a Docker Hub Private Registry?**
👉 First, I create a private repository in Docker Hub. Then, from Jenkins or local, I log in using `docker login`. I build an image, tag it with my repo name, and push it using `docker push`. In the pipeline, I use stored credentials to pull the image securely for deployment.

**25. Can you write a sample Dockerfile?**
👉 Sure, here is a simple Dockerfile:

```dockerfile
FROM openjdk:11
COPY app.jar /app.jar
CMD ["java", "-jar", "/app.jar"]
```

This uses an OpenJDK base image, copies the JAR file, and runs it with `java -jar`.

**26. What is the difference between CMD and ENTRYPOINT in Docker?**
👉 CMD provides default arguments but can be overridden when running the container. ENTRYPOINT defines the main command that always runs. For example, ENTRYPOINT could be `java -jar`, while CMD could specify which JAR to run. Together they provide flexibility and control.

**29. If you exit a Docker container, do you lose files?**
👉 If you just exit, the container stops but files inside remain. You lose data only if you remove the container without committing it or without using volumes. That’s why in production we always use volumes to persist data.

---

## 🔹 **Scenario / General Questions**

**1. Tell me about yourself.**
👉 I am a DevOps Engineer with experience in CI/CD, AWS cloud, Docker, Jenkins, and automation tools like Ansible. I have worked on building pipelines, managing deployments, and infrastructure automation. My strength is problem-solving and ensuring smooth delivery. I enjoy learning new technologies and applying them in real projects.

**2. What are your daily responsibilities?**
👉 My daily tasks include monitoring Jenkins pipelines, handling deployment activities, and troubleshooting build failures. I also write automation scripts and manage AWS environments. Additionally, I coordinate with developers and QA teams to ensure smooth releases.

**3. Explain the technologies you used in your current project.**
👉 We use AWS for infrastructure, Jenkins for CI/CD pipelines, and Docker for containerization. Ansible is used for configuration management, and SonarQube for code quality checks. GitHub is our version control system. Together, these tools help us achieve full automation in software delivery.

**6. What type of automation do you work on daily?**
👉 I work on automating infrastructure setup with Ansible and Terraform. I also automate Jenkins pipelines for build and deployment processes. Apart from this, I create shell and Python scripts for log monitoring, cleanup, and backups. This reduces manual effort and improves efficiency.

**7. How many environments are you maintaining?**
👉 In my project, we maintain four environments — Development, QA, Staging, and Production. Developers test features in Dev, QA validates functionality, staging is used for final checks, and production is for live users. Each environment is maintained with proper access controls.

**8. What types of deployments do you follow?**
👉 We use Blue-Green and Rolling deployments. Blue-Green helps us switch traffic between old and new versions without downtime. Rolling deployments update servers gradually, so users don’t face service interruptions. Both approaches ensure smooth and safe releases.

**23. How do you handle failure in deployment?**
👉 First, I check Jenkins logs and identify the error. If it’s a code issue, I coordinate with developers to fix it. If it’s infra-related, I roll back to the previous stable version. We also have health checks to detect failures early and reduce downtime.

**32. Have you ever managed an application single-handedly?**
👉 Yes, in one project I was the only DevOps engineer initially. I set up the full Jenkins pipeline, configured Docker, managed AWS infrastructure, and deployed applications. It was challenging but helped me gain end-to-end ownership and problem-solving skills.

---

✅ Now every answer is **4–5 lines, simple, and interview-ready**.

Would you like me to make a **condensed PDF cheat sheet** of these answers so you can revise them quickly before interviews?
