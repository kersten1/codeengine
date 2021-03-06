---

copyright:
  years: 2020
lastupdated: "2020-11-02"

keywords: code engine, project

subcollection: codeengine

---

{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:android: data-hd-operatingsystem="android"}
{:apikey: data-credential-placeholder='apikey'}
{:app_key: data-hd-keyref="app_key"}
{:app_name: data-hd-keyref="app_name"}
{:app_secret: data-hd-keyref="app_secret"}
{:app_url: data-hd-keyref="app_url"}
{:authenticated-content: .authenticated-content}
{:beta: .beta}
{:c#: data-hd-programlang="c#"}
{:codeblock: .codeblock}
{:curl: .ph data-hd-programlang='curl'}
{:deprecated: .deprecated}
{:dotnet-standard: .ph data-hd-programlang='dotnet-standard'}
{:download: .download}
{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}
{:fuzzybunny: .ph data-hd-programlang='fuzzybunny'}
{:generic: data-hd-operatingsystem="generic"}
{:generic: data-hd-programlang="generic"}
{:gif: data-image-type='gif'}
{:go: .ph data-hd-programlang='go'}
{:help: data-hd-content-type='help'}
{:hide-dashboard: .hide-dashboard}
{:hide-in-docs: .hide-in-docs}
{:important: .important}
{:ios: data-hd-operatingsystem="ios"}
{:java: #java .ph data-hd-programlang='java'}
{:java: .ph data-hd-programlang='java'}
{:java: data-hd-programlang="java"}
{:javascript: .ph data-hd-programlang='javascript'}
{:javascript: data-hd-programlang="javascript"}
{:new_window: target="_blank"}
{:note .note}
{:note: .note}
{:objectc data-hd-programlang="objectc"}
{:org_name: data-hd-keyref="org_name"}
{:php: data-hd-programlang="php"}
{:pre: .pre}
{:preview: .preview}
{:python: .ph data-hd-programlang='python'}
{:python: data-hd-programlang="python"}
{:route: data-hd-keyref="route"}
{:row-headers: .row-headers}
{:ruby: .ph data-hd-programlang='ruby'}
{:ruby: data-hd-programlang="ruby"}
{:runtime: architecture="runtime"}
{:runtimeIcon: .runtimeIcon}
{:runtimeIconList: .runtimeIconList}
{:runtimeLink: .runtimeLink}
{:runtimeTitle: .runtimeTitle}
{:screen: .screen}
{:script: data-hd-video='script'}
{:service: architecture="service"}
{:service_instance_name: data-hd-keyref="service_instance_name"}
{:service_name: data-hd-keyref="service_name"}
{:shortdesc: .shortdesc}
{:space_name: data-hd-keyref="space_name"}
{:step: data-tutorial-type='step'}
{:subsection: outputclass="subsection"}
{:support: data-reuse='support'}
{:swift: #swift .ph data-hd-programlang='swift'}
{:swift: .ph data-hd-programlang='swift'}
{:swift: data-hd-programlang="swift"}
{:table: .aria-labeledby="caption"}
{:term: .term}
{:tip: .tip}
{:tooling-url: data-tooling-url-placeholder='tooling-url'}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tsSymptoms: .tsSymptoms}
{:tutorial: data-hd-content-type='tutorial'}
{:unity: .ph data-hd-programlang='unity'}
{:url: data-credential-placeholder='url'}
{:user_ID: data-hd-keyref="user_ID"}
{:vb.net: .ph data-hd-programlang='vb.net'}
{:video: .video}


# Managing projects 
{: #manage-project}

Learn how to create and work with projects.
{: shortdesc} 

## What is a project?

A project is a grouping of {{site.data.keyword.codeengineshort}} entities such as applications, jobs, and builds. Projects are used to manage resources and provide access to its entities. A project provides the following items<ul><li>Provides a unique namespace for entity names.</li><li> Manages access to project resources (inbound access).</li><li> Manages access to backing services, registries, and repositories (outbound access).</li><li> Has an automatically generated certificate for Transport Layer Service (TLS).</li><li> Is based on a Kubernetes namespace.</li></ul>

For more information about managing access control to projects with IAM, see [Managing user access](/docs/codeengine?topic=codeengine-iam).

Projects incur no costs, but instead serve as folders for your apps and jobs.

### How can I see what projects I can access?

You can see a list of your projects in the [{{site.data.keyword.codeengineshort}} console](https://cloud.ibm.com/codeengine/overview){: external}.

You can also run the [`project list`](/docs/codeengine?topic=codeengine-cli#cli-project-list) command. 

```
ibmcloud ce project list
```
{: pre}

**Example output**

```
Name            ID                                    Status         Tags   Location   Resource Group
myproject       42642513-8805-4da8-8dbf-bc4f409g9089   active               us-south   default
new_proj        d294c0a3-30d8-49bc-b070-1921692f41d4   active               us-south   default

Command 'project list' performed successfully
```
{: screen}


### How can I see details about a project? 

From the {{site.data.keyword.codeengineshort}} console, you can see details of a project by clicking the name of a project from the [{{site.data.keyword.codeengineshort}} Projects page](https://cloud.ibm.com/codeengine/projects){: external}.

You can also run the [`project get`](/docs/codeengine?topic=codeengine-cli#cli-project-get) command. Replace `PROJECT_NAME` with the name of your project.

```
ibmcloud ce project get --name PROJECT_NAME
```
{: pre}

**Example output**

```
Getting project 'myproject'...
OK

Name: myproject
ID: 12345678-abcd-abcd-abcd-bc4f409g9089
Status: active
Location: us-south
Resource Group: default
Created: Tue, 28 Apr 2020 09:27:22 -0400
Updated: Tue, 28 Apr 2020 09:27:57 -0400

```
{: screen}


### How can I set policies so others can work with my project? 

See information about [managing user access](/docs/codeengine?topic=codeengine-iam) to learn about setting IAM policies so others can work with your {{site.data.keyword.codeengineshort}} project. 

## Create a project
{: #create-a-project}
You can create a project through the console or with the CLI.
{: shortdesc} 

Wait for several minutes after you create your project before you proceed to the next step as it will take some time for your project to provision.
{: important}

### Creating a project from the console
{: #create-project-console}

1. From the [{{site.data.keyword.codeengineshort}} console](https://cloud.ibm.com/codeengine/overview){: external} project menu, select **Create Project**.
2. Enter a name for the project. The name must be unique for all your projects within the specified location.
3. Choose the resource group where you want to create the project and a location to deploy the project.
4. Click **Create**.

To view the service instance for the project resource, go to your [{{site.data.keyword.cloud_notm}} dashboard](https://cloud.ibm.com/resources){: external} and find your project name in **{{site.data.keyword.codeengineshort}}**.

### Creating a project with the CLI
{: #create-project-cli}

When you create a project, it is automatically selected for context. To create a project that is not automatically selected, use the `--no-select` option.

1. Install the [{{site.data.keyword.codeengineshort}} CLI](/docs/codeengine?topic=codeengine-install-cli). Target the resource group that you want to use for the project. 

2. Create a project with the [`project create`](/docs/codeengine?topic=codeengine-cli#cli-project-create) command. Use a project name that is unique to your region. 

  ```
  ibmcloud ce project create --name PROJECT_NAME 
  ```
  {: pre}

  **Example output**

  ```
  Creating project 'myProject'...
  Successfully created project myProject
  ```
  {: screen}

3. Verify that your new project is created with the [`project get`](/docs/codeengine?topic=codeengine-cli#cli-project-get) command.

  ```
  ibmcloud ce project get --name PROJECT_NAME
  ```
  {: pre}

  **Example output**

  ```
  Getting project 'myProject'...
  OK

  Name: myProject
  ID: 12345678-abcd-abcd-abcd-bc4f409g7456
  Status: active
  Location: us-south
  Resource Group: default
  Created: Tue, 28 Apr 2020 09:27:22 -0400
  Updated: Tue, 28 Apr 2020 09:27:57 -0400
  ```
  {: screen}

  You can also list all projects:

  ```
  ibmcloud ce project list
  ```
  {: pre}

## Work with a project
{: #target-a-project}

After you create a project, you can work with the project by using the {{site.data.keyword.codeengineshort}} console or CLI.
{: shortdesc} 

### Working with a project from the console
{: #target-project-console}

To work with a project, go to the [{{site.data.keyword.codeengineshort}} Projects page](https://cloud.ibm.com/codeengine/projects){: external} and click the name of the project from the list.

From the context of your project, you can create and work with {{site.data.keyword.codeengineshort}} components, such as [applications](/docs/codeengine?topic=codeengine-application-workloads) or [jobs](/docs/codeengine?topic=codeengine-job-deploy).

### Working with a project with the CLI
{: #target-project-cli}

To work with a project with the CLI, the project must be selected for context. A project is automatically selected for context when it is created, unless you specify the `--no-select` option. To select a project that is not currently targeted, use the [`project select`](/docs/codeengine?topic=codeengine-cli#cli-project-select) command.  

```
ibmcloud ce project select --name PROJECT_NAME
```
{: pre}

**Example output**

```
Selecting project 'myproject'...
```
{: screen}

From within the context of the selected project, you can work with {{site.data.keyword.codeengineshort}} components, such as [applications](/docs/codeengine?topic=codeengine-application-workloads) or [jobs](/docs/codeengine?topic=codeengine-job-deploy).

### Determining which project is selected for context
{: #current-project-cli}

You can find details about the project that is currently selected for context by using the `ibmcloud ce project current` command. 

## Delete a project
{: #delete-project}

When you no longer need a project, you can delete it. Deleting a project deletes all of the components that it contains. You can use the console or the CLI.
{: #shortdesc} 

### Deleting a project through the console
{: #delete-project-console}

To delete a project from the console, go to the [{{site.data.keyword.codeengineshort}} Projects page](https://cloud.ibm.com/codeengine/projects){: external}, select the project that you want to delete, and click **Delete**.  

### Deleting a project through the CLI
{: #delete-project-cli}

To delete a project with the CLI, use the [`project delete`](/docs/codeengine?topic=codeengine-cli#cli-project-delete) command. 

```
ibmcloud ce project delete --name PROJECT_NAME 
```
{: pre}

**Example output**

```
Deleting project 'myproject'...

Deleted project  myproject
```
{: screen}

## <img src="images/kube.png" alt="Kubernetes icon"/> Inside {{site.data.keyword.codeengineshort}}: Interacting with Kubernetes API
{: #kubectl-kubeconfig}
  
In order to interact with your project from the Kubernetes command-line interface, `kubectl`, or with Knative, `kn` you must set up your environment to interact with the Kubernetes API of {{site.data.keyword.codeengineshort}}.

**Before you begin**

- You must [create your project](#create-a-project) and the project must be in `Ready` status.
- Install the [Kubernetes CLI (`kubectl`)](/docs/codeengine?topic=codeengine-install-cli#kube-install) and the [Knative CLI (`kn`)](/docs/codeengine?topic=codeengine-install-cli#knative-install).

You can set up your environment in the following ways. 

- You can add the `--kubecfg` option to your `project select` command. For example, 

  ```
  ibmcloud ce project select --name PROJECT_NAME --kubecfg
  ```
  {: pre}

- You can export the `kubeconfig` file directly. Run `ibmcloud ce project current` to find the project that you are currently targeting. This command also returns the export command for your `kubeconfig` file.  For example,

  ```
  ibmcloud ce project current
  ```
  {: pre}

  **Example output**

  ```
  Getting the current project context...
  OK

  Project Name:  myproj  
  Region:        us-south  

  To use kubectl with your project, run the following command:
  export KUBECONFIG=/Users/email@us.ibm.com/.bluemix/plugins/code-engine/myproj-c9e230d4-9341-4845b-ae8f-ab514c647665.yaml
  ```
  {: screen}

  Then, copy the export command, paste it into your command-line interface, and run it.

Verify that your environment is set correctly by running the `kubectl config` command.

```
kubectl config current-context
```
{: pre}

If the context is correctly set, the output matches the ID of your project. For example, if your project ID is `c9e230b4-9342-484b-ae8f-ab514b647663`, the command returns `c9e230b4-9342`.

You can find your project ID by running the `ibmcloud ce project get --name PROJECT_NAME` command.
{: tip}
  
