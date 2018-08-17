# Contributing to Our Projects, Version 1.5 from code.mil

Thanks for thinking about using or contributing to this software ("Project") and its documentation!

* [Policy & Legal Info](#policy)
* [Getting Started](#getting-started)
* [Submitting an Issue](#submitting-an-issue)
* [Submitting Code](#submitting-code)

## Policy

### 1. Introduction

The project maintainer for this Project will only accept contributions using the Developer's Certificate of Origin 1.1 located at https://developercertificate.org. The DCO is a legally binding statement asserting that you are the creator of your contribution, or that you otherwise have the authority to distribute the contribution, and that you are intentionally making the contribution available under the license associated with the Project ("License").

### 2. Developer Certificate of Origin Process

Before submitting contributing code to this repository for the first time, you'll need to sign a Developer Certificate of Origin (DCO) (see below). To agree to the DCO, you'll add your name and email address to [CONTRIBUTORS.md](CONTRIBUTORS.md) file. At a high level, this tells us that you have the right to submit the work you're contributing and says that you consent to us treating the contribution in a way consistent with the license associated with this software (as described in [LICENSE.md](LICENSE.md)) and its documentation ("Project").

### 3. Important Points

Pseudonymous or anonymous contributions are permissible, but you must be reachable at the email provided in the Signed-off-by line.

If your contribution is significant, you are also welcome to add your name and copyright date to the source file header.

U.S. Federal law prevents the government from accepting gratuitous services unless certain conditions are met. By submitting a pull request, you acknowledge that your services are offered without expectation of payment and that you expressly waive any future pay claims against the U.S. Federal government related to your contribution.

If you are a U.S. Federal government employee and use a *.mil or *.gov email address, we interpret your Signed-off-by to mean that the contribution was created in whole or in part by you and that your contribution is not subject to copyright protections.

### 4. DCO Text

The text of the DCO is (from https://developercertificate.org):
```
Developer Certificate of Origin
Version 1.1

Copyright (C) 2004, 2006 The Linux Foundation and its contributors.
1 Letterman Drive
Suite D4700
San Francisco, CA, 94129

Everyone is permitted to copy and distribute verbatim copies of this
license document, but changing it is not allowed.

Developer's Certificate of Origin 1.1

By making a contribution to this project, I certify that:

(a) The contribution was created in whole or in part by me and I
    have the right to submit it under the open source license
    indicated in the file; or

(b) The contribution is based upon previous work that, to the best
    of my knowledge, is covered under an appropriate open source
    license and I have the right under that license to submit that
    work with modifications, whether created in whole or in part
    by me, under the same open source license (unless I am
    permitted to submit under a different license), as indicated
    in the file; or

(c) The contribution was provided directly to me by some other
    person who certified (a), (b) or (c) and I have not modified
    it.

(d) I understand and agree that this project and the contribution
    are public and that a record of the contribution (including all
    personal information I submit with it, including my sign-off) is
    maintained indefinitely and may be redistributed consistent with
    this project or the open source license(s) involved.
```

## Getting Started

`add information here`

### Making Changes

`add information here`

### Code Style

Your bug fix or feature addition won't be rejected if it runs afoul of any (or all) of these guidelines, but following the guidelines will definitely make everyone's lives a little easier.

## Submitting an Issue

You should feel free to [submit an issue](https://github.com/brettpalmberg/metvue-docs/issues) on our GitHub repository for anything you feel needs attention on the site. That includes content, functionality, design, or anything else!

### Submitting a Bug

When submitting a bug on the site please be sure to add extensive information about the problem you're having. Be sure to include (at least):

* What page you were on
* What you did (which could just be trying to load the page)
* What you expected to happen
* What actually happened (or didn't)
* Your browser (including the version number if possible)

## Submitting Code

When making your changes, it is highly encouraged that you use a [branch in Git](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging), then submit a [Pull Request (PR)](https://github.com/brettpalmberg/metvue-docs/pulls) on GitHub. **FUTURE:** Your request will go through some automated checks using [Travis CI](https://travis-ci.org/brettpalmberg/metvue-docs), a continuous integration and deployment tool.

After review by the HEC team your PR will either be commented on with a request for more information or changes, or it will be merged into the codebase which will automatically deploy the changes.

Assuming everything checks out, the HEC team will deploy the changes to **FUTURE** by creating a [new release](https://github.com/brettpalmberg/metvue-docs/releases/new) on master with a tag like vX.X.X (where X is between 0 and 9), human readable title, and any other relevent context in the description.

### Check Your Changes

While there are automated checks on every PR, you can run the build process locally first to ensure things are working as expected before submitting your PR.

`Add information here on how to do that...`