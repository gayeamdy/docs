---
title: Accessing data from your Object Storage
slug: access-object-storage-data
excerpt: Learn how to access data from your Object Storage in your Notebook
section: How to (with CLI)
order: 2
---

**Last updated 27th of May, 2021.**

## Objective

This guide shows how to access Object Storage data from your [**notebooks**](https://docs.ovh.com/ca/en/publiccloud/ai/notebooks/definition/).

## Requirements

-   a working `ovhai` CLI ([how to install ovhai CLI](https://docs.ovh.com/ca/en/ai-training/install-client/))

## Upload data to your Object Storage

First, we need to push some data to the Object Storage before accessing it from the notebook.

Assuming a file named `my-dataset.zip` exists in your current working directory, you can use the following command
to create a data container named `my-dataset` in the GRA region that will contain your `my-dataset.zip` file.

``` {.console}
$ ovhai data upload GRA my-dataset my-dataset.zip
```

This file can now be accessed from your notebooks, either with read-only or read-write permissions.

## Access with Read-Only permissions

In order to access your dataset, you can use the `--volume` option.

``` {.console}
$ ovhai notebook run --volume my-dataset@GRA:/workspace/datasets:ro tensorflow jupyterlab
```

This command can be read as "Load the container `my-dataset` from the GRA region, in the /workspace/datasets directory,
with `ro` (read-only) permissions".

Wait a few seconds for the notebook to start, then you should see its URL in the output that you can access from your browser.
You can read the [Getting started](https://docs.ovh.com/ca/en/publiccloud/ai/notebooks/getting-started-cli/) page to know how to find this URL.

You should get a page like this, showing your dataset in the file explorer:

![image](images/jupyterlab_with_dataset.png){.thumbnail}

You will not be able to modify the dataset from this notebook because you loaded it with read-only permissions.

Read-only permissions are to ensure you don't modify your data by mistake. If you want to modify data from your
notebooks, to store a trained neural network for example, you can use the read-write permission instead.

## Access with Read-Write permissions

Similarly to the read-only mode, you can use the `--volume` option to load data with read-write permission.
The only difference is that you specify `rw` instead of `ro` in the command:

``` {.console}
$ ovhai notebook run --volume my-neural-networks@GRA:/workspace/neural-networks:rw tensorflow jupyterlab
```

Once you have some data that you want to save (a trained neural network in this example), you can simply write it
to the `/workspace/neural-networks` folder.

This folder will be uploaded to your Object Storage when you will stop your notebook.
As long as your notebook is in the `STOPPING` state, this means that the upload is still in progress. Once the state
changes to `STOPPED`, it means all the data were uploaded to your Object Storage.

## Access multiple volumes

In many cases you need at least one volume for your dataset, and another to store your results. You can load as many
volumes as you want by chaining the `--volume` options:

``` {.console}
$ ovhai notebook run --volume my-dataset@GRA:/workspace/datasets:ro \
    --volume my-neural-networks@GRA:/workspace/neural-networks:rw tensorflow jupyterlab
```

In this case, we loaded `my-dataset` in read-only, and `my-neural-networks` in read-write mode.

## Using cached volumes

When loading large files from the Object Storage, it can take some time to download to your notebooks. In these cases, you can cache the volumes so that it does not need to be downloaded again when you start new notebooks that use the same data.

To do so, you can append `:cache` after the permissions when specifying volumes:

``` {.console}
$ ovhai notebook run --volume my-dataset@GRA:/workspace/datasets:ro:cache tensorflow jupyterlab
```

Cached volumes will be deleted at least 72 hours after the last notebook using it has stopped.
Note that the cache is shared with all users in your project. The main consequence that you need to be careful about
is the fact that if someone else modifies the data in your cached volume, you will also see the modifications on your side.

## Feedback

Please send us your questions, feedback and suggestions to improve the service:

- On the OVHcloud [Discord server](https://discord.com/invite/vXVurFfwe9) 
