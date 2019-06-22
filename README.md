# Jupyter REES Builder

REES stands for [Reproducible Execution Environment Specification](https://repo2docker.readthedocs.io/en/latest/specification.html),
It was conceived by the developers of [Binder](https://mybinder.org) but its
utility extends beyond Binder specifically.

This project is still in the design stage. It grew out of discussions at the
[Jupyter Community Workshop for Scientific User Facilities and High-Performance Computing](https://blog.jupyter.org/jupyter-community-workshop-jupyter-for-scientific-user-facilities-and-high-performance-computing-3afa4a990086).

## Goals

* Reduce the learning curve for creating Binder-compatible repositories by
  adding a UI for specifying dependencies and configuration.
* Provide Binder-like functionality without Kubernetes. This is useful in
  environments where cloud services aren't a good fit and where there are not
  local resources to maintain a Kubernetes cluster.

## Related Work

* This has some similarities to
  [nb_conda](https://github.com/Anaconda-Platform/nb_conda) but it will produce
  containers instead of kernels.
* This has some similarities to Code Ocean's UI for building containers, but it
  will operate _outside_ of a running notebook server, and it will be
  open-source.

## Components

1. A JupyterLab extension that lets you right-click a folder and choose, "Make
   this into a repo2docker container."

2. A JupyterHub Service that processes requests from (1). It has permission to
   run docker and has access to storage where it can cache images.

3. A UI for building a [REES](https://repo2docker.readthedocs.io/en/latest/config_files.html#config-files)
   It would have a section for "Add Python requirements," and a section for "Add
   system requirements," etc. This UI would be stand-alone---not a
   JupyterLab/notebook extension---and could be deployed in the same web app as
   (2).

4. A gallery of images, with the ability to browse static notebooks within them
   and to launch them as named servers on the Hub, with the optional to mount
   local storage for persistence.