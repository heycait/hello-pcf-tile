# Hello PCF Tile
This is an example tile contained in one metadata file to get more familiar with [PCF Tile structure](https://docs.pivotal.io/tiledev/2-1/tile-basics.html). This is in opposition to how [kiln](https://github.com/pivotal-cf/kiln) works by separating out the different requirements of a Tile and "baking" it back into one (useful for very large tiles).

### Who is this for?

 * Anyone curious about how tiles in Ops Manager are made
 * Cloud Foundry contributors who want to understand how Ops Manager functions to deploy Pivotal Cloud Foundry
 * BOSH release authors who want to see how releases get incorporated into Pivotal Cloud Foundry

### Quickstart

Clone this repo. Then, from within the repo, create the tile
(`hello-pcf-tile.pivotal`):

```
zip -r products/hello-pcf-tile-v99.pivotal . -i "*metadata/*" "migrations/*" "releases/*"
```

Log into Ops Manager. On the _Installation Dashboard_, click _Import a Product_.
Upload `products/hello-pcf-tile-v99.pivotal`.

## What are Tiles?

> Product tiles make it easy for cloud operators to offer new and upgraded software services to developers in a Pivotal Cloud Foundry (PCF) deployment. Pivotal Network distributes these tiles as zipped code directories, with filename extension .pivotal, that contain or point to all of the software elements that perform the tile’s functions.
>
> In the Ops Manager Installation Dashboard, service tiles present a form-based interface that cloud operators use to configure the service. These configured properties become part of the BOSH manifest that PCF uses to deploy instances of the service.
>
> *—How Tiles Work*

Tiles are composed of BOSH releases, a tile manifest, and migrations.

The tiles shown in the Ops Manager dashboard below include:

1. BOSH Director for GCP
2. Pivotal Application Service
3. MySQL for Pivotal Cloud Foundry v2

![](https://docs.pivotal.io/pivotalcf/2-3/customizing/images/interface.png)

### How do tiles relate to Cloud Foundry?
Tiles are a way to package and configure instance groups and jobs for Pivotal Cloud Foundry through the Ops Manager web UI. In particular, it provides the way to configure and deploy your Pivotal Cloud Foundry through the Pivotal Application Service (PAS) tile. They do not exist in the open source world.

In the open source Cloud Foundry, ops files that are applied to your CF deployment are the functional equivalent of Ops Manager tiles.

## What is Ops Manager?

> Ops Manager is a web application that you use to deploy and manage a Pivotal Cloud Foundry (PCF) PaaS.
>
> *[Using Ops Manager](https://docs.pivotal.io/pivotalcf/2-3/customizing/ops-man.html)*

When an operator configures a tile, Ops Manager takes the information, and under the hood, translates it into a BOSH manifest (that defines properties for each job that the manifest deploys) which gets applied to the Pivotal Cloud Floundry deployment.

Essentially, Ops Manager is a way to abstract away the complications that arise with generating and maintaining a massive [BOSH deployment manifest](https://bosh.io/docs/deployment-manifest/) and creating the appropriate ops files to configure your Cloud Foundry.

## Goals
The goal of `hello-pcf-tile` is an exploration into tile structure, BOSH manifests, and perhaps creating BOSH releases to be packaged up into a tile and used with Ops Manager.

The main purpose is to get a better handle on the different moving parts of a tile and document each part within the tile metadata itself. In particular, how each section relates to each other and how it translates in the Ops Manager UI as well as the underlying BOSH manifest.

The idea of this exploration is translate the base understanding of a singular tile metadata file to how that corresponds to using `kiln` to maintain an enormous tile, such as Pivotal Application Service.

## Learnings / Key Takeaways / Odd Findings
Refer to the sections in the Wiki

### References
* [How Tiles Work](https://docs.pivotal.io/tiledev/2-1/tile-structure.html)
* [Product Template Reference (Ops Manager Manifest)](https://docs.pivotal.io/tiledev/2-1/product-template-reference.html)
* [Property Reference](https://docs.pivotal.io/tiledev/2-1/property-reference.html#expressions)
* [Ops Manager Example Tile Repo](https://github.com/pivotal-cf-experimental/ops-manager-example/blob/master/example-product/metadata/example-product.yml.erb)
* [Ultimate Guide to BOSH](https://ultimateguidetobosh.com/)
* [BOSH docs](https://bosh.io/docs)
* [BOSH release PCF Docs](https://docs.pivotal.io/tiledev/2-2/bosh-release.html)
* [learn-bosh-release](https://github.com/mariash/learn-bosh-release)
* [Ops Files](https://bosh.io/docs/cli-ops-files/)
* [Deploying Cloud Foundry](https://docs.cloudfoundry.org/deploying/cf-deployment/deploy-cf.html)
* [Tile Generator Tool](https://docs.pivotal.io/tiledev/2-1/tile-generator.html)
* [PCF Command Line Utility](https://docs.pivotal.io/tiledev/2-3/pcf-command.html)
* [Vagrant Box for Ops Manager](https://github.com/pivotal-cf/vagrant-ops-manager)
* [smith](https://github.com/pivotal-cf-experimental/smith)
