# ⚙️ Helm Cheat-Sheet

Helm is a package manager for Kubernetes that helps you define, install, and upgrade even the most complex Kubernetes applications. It uses **charts** to define the structure of Kubernetes applications.

---

## 🔍 Overview

- **Product Type**: Kubernetes Package Manager
    
- **Focus**: Simplifies the management of Kubernetes applications using "charts," which define resources and configurations. Helm allows you to install, upgrade, configure, and manage applications within a Kubernetes cluster.
    
    - **Chart Management**: Organize and manage Kubernetes applications as charts
        
    - **Repository Management**: Use repositories to store Helm charts for distribution
        
    - **Deployment**: Install, upgrade, or delete applications with ease in Kubernetes environments
        

---

## 📦 Repository Management

|COMMAND|DESCRIPTION|
|---|---|
|`helm repo list`|List Helm repositories|
|`helm repo update`|Update list of Helm charts from repositories|

---

## 📊 Chart Management

|COMMAND|DESCRIPTION|
|---|---|
|`helm search`|List all installed charts|
|`helm search <CHARTNAME>`|Search for a specific chart|
|`helm ls`|List all installed Helm charts|
|`helm ls --deleted`|List all deleted Helm charts|
|`helm ls --all`|List installed and deleted Helm charts|
|`helm inspect values <REPO>/<CHART>`|Inspect the variables in a chart|

---

## 🛠️ Install/Delete Helm Charts

|COMMAND|DESCRIPTION|
|---|---|
|`helm install --name <NAME> <REPO>/<CHART>`|Install a Helm chart|
|`helm install --name <NAME> --values <VALUES.YML> <REPO>/<CHART>`|Install a Helm chart with overrides|
|`helm status <NAME>`|Show the status of a Helm chart installation|
|`helm delete --purge <NAME>`|Delete a Helm chart|

> [!warning]  
> When you delete a chart with `--purge`, the release is permanently removed. You cannot restore it without reinstalling.

---

## 🔄 Upgrading Helm Charts

|COMMAND|DESCRIPTION|
|---|---|
|`helm get values <NAME>`|Return the variables for a release|
|`helm upgrade --values <VALUES.YML> <NAME> <REPO>/<CHART>`|Upgrade the chart or variables in a release|
|`helm history <NAME>`|List release numbers|
|`helm rollback <NAME> 1`|Rollback to a previous release number|

---

## 📝 Creating Helm Charts

|COMMAND|DESCRIPTION|
|---|---|
|`helm create <NAME>`|Create a blank chart|
|`helm lint <NAME>`|Lint the chart to check for errors|
|`helm package <NAME>`|Package the chart into `.tgz` format|
|`helm dependency update`|Install chart dependencies|

---

## 📂 Chart Folder Structure

When you create a Helm chart, it follows a specific folder structure. Below is an example for the `wordpress` chart:

```
wordpress/
  Chart.yaml          # A YAML file containing information about the chart
  LICENSE             # OPTIONAL: A plain text file containing the license for the chart
  README.md           # OPTIONAL: A human-readable README file
  requirements.yaml   # OPTIONAL: A YAML file listing dependencies for the chart
  values.yaml         # The default configuration values for this chart
  charts/             # A directory containing any charts upon which this chart depends.
  templates/          # A directory of templates that, when combined with values,
                      # will generate valid Kubernetes manifest files.
  templates/NOTES.txt # OPTIONAL: A plain text file containing short usage notes
```

> [!info]  
> **Chart.yaml** is the heart of your chart, containing metadata like the chart's name, version, and description. You can also define dependencies in the `requirements.yaml`.

---

## 📚 Resources

- **Official Website**: [Helm Official Website](https://helm.sh/)
    

---

## 🔁 Related

- [**Getting Started with Kubernetes**](https://kubernetes.io/docs/tutorials/kubernetes-basics/) — A guide to setting up and managing Kubernetes clusters.
    
- [**Using Kubernetes with Helm**](https://helm.sh/docs/intro/using_helm/) — Dive deeper into Helm's features for managing Kubernetes applications.
    

---

## 🌍 **Explore More**

- Explore [**Kubernetes Networking**](https://kubernetes.io/docs/concepts/services-networking/) to learn about networking in a containerized environment.
    
- Dive into [**Helm Chart Development**](https://helm.sh/docs/topics/chart_developing/) for advanced techniques in creating and customizing your own Helm charts.
    

---

## Tags 📚

#helm #kubernetes #charts #deployment #package-manager