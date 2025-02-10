# ODPS Maintainer Guide

## About the versions

Dev is the live view of what is cooking and most likely coming in the next release 

- Source: https://github.com/Open-Data-Product-Initiative/dev 
- Rendered:  https://opendataproducts.org/dev/ 

Release versions have numbering, Major.Minor 

- Source: https://github.com/Open-Data-Product-Initiative/v3.1 
- Rendered: https://opendataproducts.org/v3.1/ 

- https://github.com/Open-Data-Product-Initiative/v3.0 
- https://github.com/Open-Data-Product-Initiative/v2.1 
- https://github.com/Open-Data-Product-Initiative/v2.0 
- https://github.com/Open-Data-Product-Initiative/v1.0 

Breaking change increases a minor number. Major number change is decided by maintainers based on judgement when the ODPS takes a leap forward and incorporates new concepts or fully new document level objects or changes. 

## Domain, DNS, and paths in the web

GitHub is the core. We have set the domain opendataproducts.org at the organization level. 
As a result, any of the repositories become paths under the domain as long as those are set to serve pages from Git Hub. 

- An example “dev” repo of ODPS becomes opendataproducts.org/dev 

The ODPS website is also served from GitHub and is an exception in paths. It resolves to the main domain root.  Repository https://github.com/Open-Data-Product-Initiative/open-data-product-initiative.github.io 

### Domain management 

DNS, etc hosted by the Linux Foundation. LF also renews the domain. 

We can request changes via https://jira.linuxfoundation.org/plugins/servlet/desk/user/requests?status=any&reporter=me 

The following DNS settings have been added to the DNS

- opendataproducts.org - resolves to Github IPs
- blog.opendataproducts.org - resolves to Medium
- governance.opendataproducts.org - resolves to Gitbook (Not maintained at the moment)

## Different versions of ODPS and rendering the specification

- Each of the version of ODPS is a separate repository. They have just the version as name, reason is explained above so that automatic domain paths work without DNS or other changes. 
- All of the versions have been configured in Github to serve pages as a result. https://pages.github.com/ 
- All of the versions use Slate open source solution to generate “documentation”. Slate is originally intended to be used to generate 3 column API documentation as static HTML pages. But it has been applied to the ODPS. 
- In normal specification development, Slate does not need to be touched. 
- Only if the layout of the result needs tweaking and can not be done with CSS, then Slate needs refactoring. 
- Slate is part of every ODPS version repository
- The process of generating HTML pages to serve is fully automated with GitHub Actions in each repository. 
- If something is changed in the main branch, the rebuild and published process kicks in automatically. 


## Modifying the ODPS spec

- We use feature branches. Pushing directly to the main is to be avoided. All PRs are expected to be branches. Maintainers review the PRs and either requires changes or accepts. 
- If branch is accepted, it will  be merged to main branch and that ignites automated rebuild and publish. Only maintainers merge anything to main branch. 
- Branches by default after merge should be removed. 

## Release process 

Technical Steering Committee (TSC) decides when a new release is needed since they lead the specification development and have the best knowledge of changes and maturity of the development version. 

### Alignment phase
- Maintainers create a proposal for a new release and schedule
- The release proposal is discussed at the TSC group and possible comments will be provided to maintainers to consider. 
- TSC can stop the release process but the reasons must be very solid and most commonly additional discussion is needed between TSC and maintainers. We seek always alignment, not power struggles.

### Release phase

After TSC's review, the maintainer starts executing the accepted and aligned release plan. The default minimal process contains the following steps:

- A Release Candidate from the development version is created and the development version is closed. Stopping development is needed, so that focus can be given for the release. Release the RC to Github as a repository. Will be available via https://opendataproducts.org/rc/ 
- A blog post about the RC is published on Medium, https://blog.opendataproducts.org/ 
- RC is open for comments for 14 days
- After commenting maintainers process the feedback.
- If changes are needed before release, then after implementing the changes, a new Release Candidate is published (RC1). Again commenting is open for 14 days.
- The above is repeated until no changes are requested and we have strong alignment about the new release.

Finally, RC is published as a new version of ODPS. 

- Rename the repo to match the new version number
- Initiate rebuild and it will become visible under opendataproducts.org 
- After this new development version is derived from the release and new development version is opened for pull requests. Move old issues from previous dev version to new. 
- Opendataproducts.org website is updated regarding the versions part to match the current situation and versions. Repo: https://github.com/Open-Data-Product-Initiative/open-data-product-initiative.github.io 
- Blog post about the release is published on Medium, https://blog.opendataproducts.org/ 


