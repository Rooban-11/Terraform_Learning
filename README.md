# Tekton/Terraform_Learning

**Terraform **

What is terraform -  Infrastructure as code  : Common practice of managing infrastructure with same principals that apply to managing software including the use of version control,pipelines, etc. WRT GCP, this means writing  HCL (HashiCorp Configuration Language), checking that code into github and using tekton pipeline to run terrafrom.

Declarative Language - HCL
Open Source Command line tool.

Easy to learn and manage infrastructure since we can avoid developing other language codes to manage these configurations.
Can easily create complex infrastructure configurations.
Changes can be made incrementally

**About Terraform **

Current State ---------------(Terraform Plan(Core))-----------------> Desired state(TF-Config)

**sample terraform.tfvars (key/value tet type) :**

name = "mybucket"
location = "us-central1"
project = "myproject1"
**
Terraform-Ford :**

**Manage GCP Infrastructure like below**
  -Networking
  -Permissions
  -Projects

These codes are stored in Github. GCP Team manages these codes. Tekton pipelines used to run terraform.

**Use Case for Terraform - Create a GCS storage bucket**

 -Name your bucket in google console and create them. On Provision method
 -Using Terraform (" Captured in phone")


**How to use Terraform :**

Terraform init (Create state,download addl dependencies)
Terrafrom Apply (Run terraform code, changes must be confirmed before they happen manually)
Terraform destroy ( Destroys the infrastructure).

Give them a demo on how to create an gcp-app-terraform template repo. 
Clone them to your local. Place projects.json in that folder.(ITO Team will provide the file)

Lot of modules can be used. ref(github.ford.com/gcp/tfm*)



****What is Tekton ?****

The Tekton Pipelines project provides k8s-style resources for declaring CI/CD-style pipelines.
Tekton makes it easier to deploy across multiple cloud providers or hybrid environments.
Tekton uses the Kubernetes control plane to run pipeline tasks.
Resources such as git repos can easily be swapped between runs

****How Tekton Works?****

**These are the base components of  tekton **


**Reg [Task]** - Base level component of a tekton CI/CD  integration  pipeline is a task. The task is a one which you create to perform an operation such as deploy,manage,compare. Tekton allows you to seperate your task s that are then consumed by devs and can be isolated easily.

**Sequence[Pipelines]** - Pipeline is made up of n number of tasks. The tasks can be customized to a specific order of the dev needs.

**Execution[pipeline run] **- You can trigger a pipeline from pipeline run. 

**Git repository[Pipeline Resource]** - To make it run smoothly you need to provide some data for that execution.

Once the tasks are created, they will be registered to a kubernetics environment aka the tekton execution engine. These can be shared across diff teams whihc can make use of those tasks fro their applications. There will be a template created for this where every team can use them(YAML Definitions)

There can be a pipeline definition created with these templates for specific applications with their corresponding git repo. This namespace can have a number of tasks wrt to the YAML file. The YAML file basically a registered pipeline in Tekton.
Once you have defined the pipeline definition inside the application. Then the developer can push their change to their git repository. This will trigger a webhook, which in turn connects to tekton execution. Whenever a github change is done. The pipeline will trigger. This is a repititive operation. From here the namespace will be created also called as k8 image registry softwares which can be used repetively.

****What is openshift?****

OpenShift Pipelines is a Kubernetes-native CI/CD solution based on Tekton. It builds on Tekton to provide a CI/CD experience through tight integration with OpenShift and Red Hat developer tools. OpenShift Pipelines is designed to run each step of the CI/CD pipeline in its own container, allowing each step to scale independently to meet the demands of the pipeline.
Openshift basically allow the devs to view logs,monitor pipeline and many other ui operations. 


Explain the workflow, the pipeline and the github repo of the pipeline and trigger events in tekton catalog git hub repo 

How github connects to pipeline (Explain the webhook(ingress link), pipeline account as a collaborator)
