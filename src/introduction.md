# Introduction

Overengineered is here to help you develop fast, efficient, and safe
decentralized apps. We accomplish this by providing an easy to install _cloud
at home_, where decentralized services can be installed like an app on your
phone.

A GraphQL _data abstraction service_ and decentralized _registries_ are
provided to help distribute data schemas. Progressive Web Apps provide
requirements to the abstraction service that can then be fetched and installed
from the registry.

This should enable developers to move quickly to implement new products and
features. We also want to provide all the glue needed to develop within this
environment in a cohesive manor.

## Rust

In the spirit of trying to create a safe and secure platform that treats data
ownership as a first class feature; Rust feels like a natural fit.

Note that the current state of many of the dependencies are not considered
stable. Therefore our platform will not be considered stable or support
backwards compatibility between versions. These guarantees will likely evolve
over time, but for now expect rapid breaking changes.

## Who is this book for?

This book is ideal for any developer who wants to quickly deliver decentralized
apps or who are just interested to see how this landscape is changing with the
next generation of the internet.

## How to use this book

We try to structure the book so you get introduced to a new topic with a little
background and further reading before moving into a project that will be
continuously developed throughout this book.

The app that we will be developing and breaking down is a simple TODO app. We
will be slowly introducing you to more and more features as we shape it to
something that is actually useful.

We will be covering a broad range of topics, which will all require their own
set of dependencies. To make sure, as a reader, you can follow along, we have
developed tools to manage the dependencies in a secure environment. These will
be covered in later chapters.

## Source Code

The source files from this book can be found in the github repo
[GitHub](https://github.com/overengineered/docs) and will be found under the
folder following the folder naming pattern of
`chapter-section-title`.

## Stack

Briefly let's cover the stack that we will be working with. Later we'll have a
gentle introduction to many of them and others may not require direct
interaction with, but it may be important to know for debugging purposes.

You can follow up on any of these topics to learn more.

### Frontend

The frontend is what the user sees when they load a web page or views one of
apps using Overengineered. Web being the dominate platform today, we choose a
lot of our decisions around that. WebAssembly is how we are able to create apps
that support a wide range of architecture and devices.

- **Yew** - Yew is a Rust Crate similar to [React](https://reactjs.org/). They
  both use a virtual dom, components return a JSX like syntax and have both a
  class and functional implementation with hooks into state and lifecycle
  management.
- **GraphQL** - [GraphQL](https://graphql.org/) was chosen as the primary
  server / client communication to minimize network traffic. With the ever
  growing number of devices we want to keep payloads as small as possible.
  GraphQL provides a very nice abstraction for developers and has existing
  client libraries for many languages including Rust.

### Backend

All of the services that need to run to keep the lights running and the apps
working.

#### Webserver

- **Rocket** - [Rocket](https://rocket.rs/) is the primary recommended way to
  create a user facing web server. Rocket is a Rust Crate that focuses on a great
  developer experience with an easy to use API. We think this fits perfectly
  with what we are trying to accomplish. And many Overengineered Rust Crates
  take inspiration from this.
- **GraphQL** - Like previously mentioned for various reasons we use GraphQL.
  GraphQL is very easy to integrate with Rocket.

### DevOps

These cover the infrastructure that the cloud at home services use to manage
and deploy the apps used for the cloud apps as well as the development
environments. Don't worry most of this will soon be abstracted away and will
not require expertise in to use Overengineered. We will cover enough
information to be able to unblock yourself in the case of an issue or
unforeseen problem.

- **Docker** - We primarily use [Docker](https://docker.com/) for the build
  tools, but use [Containard](https://containerd.io/) for the container
  service.
- **Kubernetes** - [Kubernetes](https://kubernetes.io/) is a container
  orchestration service to manage containers across all devices within your
  network. We specifically use [k3s](https://k3s.io/) since it supports the arm
  architecture and can easily be ran on Raspberry Pi to enable low cost
  hardware and low power consumption.
- **Template Cluster K3s** - An
  [opinionated](https://github.com/k8s-at-home/template-cluster-k3s)
  template for deploying a single k3s cluster.
  - **Ansible** - [Ansible](https://ansible.com/) is an automation platform for
    managing automation across devices.
  - **Terraform** - [Terraform](https://terraform.io/) provides infrastructure
    as code. We
    use it for managing the Cloudflare domain.
  - **Flux** - [Flux](https://fluxcd.io/docs/) is a tool for keeping the
    Kubernetes cluster
    in sync with the code repository.
  - **SOPS** - [SOPS](https://github.com/mozilla/sops) is a tool for managing
    private data such as passwords and private information within the
    configuration files that will be checked int source control. \*
  - **Cloudflare** - [Cloudflare](https://cloudflare.com/) manages domain and
    updates the DNS.
