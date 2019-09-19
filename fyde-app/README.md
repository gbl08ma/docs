---
layout: default
title: Fyde App
has_children: false
nav_order: 3
permalink: /fyde-app
---
# Fyde App
{: .no_toc }

The Fyde app bundles the end user UI and the Fyde agent. It is available on the following platforms:

* iOS - available on the [App Store](https://www.fyde.com/downloads)
* MacOS - available on the [App Store](https://www.fyde.com/downloads)
* Windows - available on the [Microsoft Store](https://www.fyde.com/downloads)
* Linux - repos soon available for Debian and Arch.

## Fyde Agent

The Fyde agent intersects requests at the network layer. When a DNS request matches a protected resource, it injects a reply, pointing the domain to an internally accessible marker IP address that represents the resouce. It then, in parallel, initiates a request to the Access Policy Engine to grant permission to the resouce, and establishes an mTLS connection to the Access Proxy that is associated with the resource. It also includes a DNS security engine that blocks requests that match blacklists configured at the Enterprise Console level.

## Fyde App UI

Besides configuration and enrollment, the Fyde app UI has two main responsibilities: (1) to guide the user through remediations to be able to access a resource and (2) to provide a friendly UX for blocked DNS resources. Both flows start with a notification that is triggered when the user either tries to access a resource without fully complying with the corresponding policy, or when the user tries to access a blocked domain.
