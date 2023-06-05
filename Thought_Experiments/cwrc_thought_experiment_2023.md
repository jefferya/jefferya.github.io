# A Thought Experiment: CWRC in a Minimal Socio-technical System

Status:

* first draft

## Introduction

Starting with a digital asset management system (aka repository), add in the socio-technical systems and processes that support the repository and blend with minimal computing concepts, how does this world look like? The following thought experiment deconstructs the typical repository software stack along with surrounding processes and then through the lens of minimal computing, tries to reconstitute the pieces. What does the outcome look like?

User experience and sustainability are two of the main lens given special consideration during the thought experiment. The user experience lens includes not only the end-user but also the entire range of personnel involved in the socio-technical system from the content creators to those managing the processes and developing the software and system. The sustainability lens tries to help direct the thought experiment by motivating thoughts on how to enable the long-term viability of the mission, vision and values that motivated the socio-technical system. Together, user experience and sustainability help set guardrails on the limitations of the thought experiment and why the thought experiment might not be the best approach in certain contexts, partially due to the tensions between sustainability and user experience in a minimal environment.  

## What is a Digitial Asset Management System

The context of this thought experiment: a digital asset management system (aka repository) as a software stack and a set of processes helping to manage the repository plus the people that create, manage and use the content. Let us not forget the people that manage, develop and fix the system, not just the software. The aforementioned pieces of technology, process and people constitute the socio-technical system.

The software stack of a repository, (for example, DSpace, Islandora, Semvera, Aviary and [Jupiter](https://github.com/ualbertalib/jupiter)) have common components. A data persistence layer that holds the content (e.g., RDBMS, filesystem, S3 object store or the like). On top of the persistence layer is a storage abstraction layer -- software libraries to read the content (e.g., ActiveStorage, Object Relational Mapping (ORM), object store API). On top of this layer is an application framework (e.g., Ruby on Rails, Symphony, Drupal) that tries to help the developer create models of the underlying content made accessible by the previous layer. From these models, the developer creates controllers and views that build the web pages. This passes through a web server that interacts with the users' web browser (or a web API for machine-to-machine access). Also, a separate Javascript framework may enter the stack to help enhance the user experience. The above technology stack is generalized across multiple repository examples and is complicated, requiring substantial skill and experience to maintain, let alone enhance the software.

One intention of the 3rd party modules in the software stack is to help the developer become more productive/efficient by offering the opportunity to build upon others' work. However, each additional module includes the potential to increase the learning curve for any developer new to the software stack thus reducing initial productivity and increasing the time before productive work starts flowing. The more code libraries, the bigger the framework, the larger the learning curve for the inexperienced developer and the longer the lag before productive work can flow.

``` text
--------------------------------|
| Client (e.g., browser)        |
|-------------------------------|
| Server (e.g., web server)     |
|-------------------------------|
| Discovery (application code)  |
|-------------------------------|
| Application Framework         |
|-------------------------------|
| Storage abstraction layer     |
|-------------------------------|
| Persistant storage            |
|-------------------------------|

Figure #1 Generalized Repository Application Stack
```

Each layer is comprised of multiple software libraries and modules that are extremely powerful in the feature set provided. However, a repository may only use a small percentage of the features. A bug, defect or security problem may require updating parts of the software stack and possibly requiring refactoring customizations to work with the new version of the module. Altogether, this adds to the burden of this type of system. Can more energy be directed to the research problem as opposed to supporting a technical stack? If the stack is flattened then what is the impact? These are the questions the thought experiment explores.

The discussion so far does not mention the processes and people that create the content, ingest the content, manage the system, work with the content, train the content creators/users, fix the content via bulk processes or more generally how people keep the system alive.  The shortness of this description should not be interpreted as an indication of the importance and size of the pieces of the system outside the software stack.

## Why the thought experiment?

What is the motivation behind the thought experiment? One driver is the complexity of the software stack requires not just general IT skills but specialized skills and experience to develop, maintain and operationalize. For a research project to undertake using a repository this may mean hiring experienced resources at a considerable cost or training the inexperienced person. Often labor with a research project is precarious and the turnover adds risk to the goals of a research project.

One option is a Software as a Service (SaaS) solution where one can pay a fee, often monthly, to receive the use of a repository. On the surface, this seems cheaper. One does not have to wait for the repository to be set up, you have instant access. One might be able to pay the vendor for new features, assuming they have time and resources otherwise be confined to the user experience controlled by the vendor. The user experience may or may not align with the mission, vision and values of the project. Also, one is paying for the time savings so one does not have to wait while the repository is set up and technical staff members learn the tools. The SaaS organization exists to generate a profit (even if it is a non-profit) to keep the lights on and expand services. What happens when the research project lacks funding to pay -- how does the project end is a question that needs upfront thought and needs to be added to the total cost of the SaaS solution (some cloud providers charge for data transfer and leaving the SaaS may not be free if you want the data). Other factors, the SaaS offering may not follow OCAP or FAIR principles. In closing, the SaaS solution may use the same complicated software stack and the SaaS fees are going toward maintenance costs, hopefully, spread over enough subscribers to help pay for the technical expertise hired into non-precarious positions and offloading technical expertise from the research project (i.e., grouping multiple research projects to help build a better economy of scale).

However, what if we thought about deconstructing the software stack? Can the level of specialized technical expertise be reduced substantially? The cost of technical expertise due to system complexity impacts the sustainability of the socio-technical system, especially those precariously funded through research. How is the socio-technical system impacted deconstruction?

## The interplay between sustainability and user-experience

Sustainability, at a basic level, is a vision of the future plus the enablers and environment required to maintain or exceed that vision. There are multiple definitions and each project should define what sustainability looks like at the beginning. Plans can change over time. Should sustainability be built into the initial software architecture choices? Depends on the context.

User experience needs to be defined early as well and for the entire life-cycle of the project. Parts of the existing repository software mentioned earlier (in Figure #1), have places where the developer experience is privileged over the end-user experience. This is not a slight on the repository software teams -- the small teams do a good job with the resources available given the advantages and disadvantages of the chosen software stacks. An example, Islandora Workbench is a good tool that matches well to the expertise of the users ingesting content but on the other hand, for the user interested in a preservation tool to extract content, Islandora's is less well developed. This is not a slight against Islandora, all the repositories have areas that are less end-user friendly than others.

Can we enhance the developer experience by simplifying the software stack plus enhance the sustainability all the while trying to allocate more time to the end-user and content management tasks (e.g., ingesting content, integrating tools/viz, enhancing content)?

Possibility of experience: how is a new experience/feature added to a socio-technical system? One way is to add more code. A naive view: the bigger the software stack, the more significant the task and the more expertise thus the possibility to create the user experience is decreased. One example. To help provide flexibility, repositories generally provide web (REST) APIs to allow machine connections however these come with assumptions and restrictions on how one can interact with the repository and the complicated software stack. With trends such as an increased focus on security, including multifactor authentication, the level of expertise required to interact with the APIs needs to increase to allow the possibility of experience (e.g., a new feature) for a user. If adding more code to the software stack increases the complexity of the system then can the new feature or user experience be added without code? Or can code be written in a carefully chosen manner and not impact sustainability and experience?

In the age of generative AI, can a socio-technical system around a repository service be designed to leverage the strengths of the generative AI as a possibility to enhance sustainability by reducing the dependency on IT talent? Are the "hallucinations" from generative AI less severe on smaller/simpler software stacks?

Can we break the idea that a better user experience means more code and sustainability improves with less code?

## The guiding principles of the thought experiment

To start this thought experiment, we need to define the world we live in through a set of guiding principles.

We consider the socio-technical system. Let us go deeper than user-centered design. Let us take into consideration the entire socio-technical system thus going beyond the developer's view of the world or even a user-experience view.

We think that if we have a hammer then there are no such things as nails. As a developer, there is a tendency to write code to fix a problem whereas the problem might be better solved by a socio-technical change to the system. We privilege shifting the socio-technical system instead trying to hit every nail with our hammer. Let us avoid the Law of the Instrument by Abraham Kaplan.

We get inspired by minimal computing concepts. The experiment "advocates for using only the technologies that are necessary and sufficient for developing digital humanities scholarship in such constrained environments" (Risam 2022). We look a what we need. Is the complicated software stack born out of a need or born out of Kaplan's Law of the Instrument (e.g., a software developer's skillset and the easiest approach to a working thing)?

We start experimenting by throwing out the entire software stack (and technical people) in the system. Developers are expensive and mobile (especially ones with experience building within the frameworks mentioned above). We then add back parts to the system, as needed, with the understanding of the trade-offs.

## Deconstruction / reconstruction

If we split apart a repository into its constituent socio-technical system parts and break apart the software stack then what does the remainder look like? This is a thought experiment and not meant to design a new repository.  

What is a repository? At a high level, the repository manages digital assets by providing ways to discover, access, manage and ingest content for both humans and computers.

First, let us start with the experiment, can a repository be replaced with a static site generator? Some examples include Jykell / Wax but these are limited in features compared to a digital asset repository. The idea: generate the entire set of static pages instead of leveraging a complicated software stack to dynamically generate the content in real-time.

In broad terms, a static site generator (like Wax or Jykell) can leverage a template plus contents to generate a set of static web pages. The approach reduces or replaces the need for the dynamic components of a site such as the RDBMS, dynamically generated web pages via the software stack. The resulting static pages are stored on a web server. Plugins are available to help support use cases such as search and IIIF image support <https://minicomp.github.io/wiki/wax/>

Next, we think through what the different components of a repository mean (from Figure #1).

### Persistent Storage

What does a repository store?

* descriptive metadata about the resource (e.g., title, author, type, etc.)
* structural metadata describing the relationship with other resources (or more generally objects -- e.g., member of a collection, page in a paged resource, etc.)
* media file(s) of the resource (e.g., the original file that might be in the form of a PDF, XML, audio, video, etc.) in other words the original digital asset
* derivative files of the media file (e.g., OCR document, thumbnails, service files of a smaller size than the original (e.g., low quality for low bandwidth users, etc.), transcriptions of audio/video, etc.)
* technical metadata describing the media file(s)
* workflow metadata (e.g., embargo, published, draft)
* access metadata (e.g., publically visible or restricted to a subset of users for viewing and/or editing)
* copyright

In the aforementioned example repository software stacks, the above list is persisted in a combination of an RDBMS, filesystem, and/or FedoraCommons. Each requires a backup service as part of a disaster recovery plan. Also, the resources may be copied as part of a long-term preservation plan. The backup and preservation use cases require additional software to facilitate removing content from the RDBMS (and maybe Fedora depending on the repository). The result is an increased burden and strain on sustainability. What if we do not use an RDBMS (and Fedora)?

### Storage abstraction layer (Software layer interacting with the persistent storage)

Aside from the original digital assets, the above information is persisted in one format and then transformed by a software stack upon each access to a web page display, search index or into a different format or manifestation via an API call in the software stack. Some examples of storage abstraction layers are ORMs (object relation mappings) including ActiveRecord for RDBMS access or ActiveStorage for accessing filesystem or object storage.

### Application Frameworks

Heavyweight application frameworks such as Rails, Drupal/Symfony build upon the storage abstraction layers such as those supporting an RDMS. The frameworks offer convenient methods to model persistent content (read, write, update), control and route web requests, and create views (e.g., web pages to view and edit content). The frameworks are generalized to work in a wide range of use cases and are extensible via add-on modules. The frameworks help technical experts quickly build a dynamic application. Does this help or hinder long-term sustainability? Does the answer depend on the context of each project individually and their definition of sustainability and user experience?

Tools integrated into a framework (e.g., Drupal module) may gain a critical mass of usage where support is retained from one version of the framework to the next. However, this might not be the case. The application built upon the framework may need to swap out unsupported modules or the custom application code may need to be significantly refactored or rewritten (e.g., Drupal 7 to Drupal 8+ that started using the PHP Symfony framework). Is it better to include a module into the framework (e.g., to improve user experience) or rely on loosely or uncoupled/external tools?

What if the application framework layer was removed? Or at least the heavy-weight framework? If one prescribes to the notion that the longer something is, the harder it is to understand there might be benefits. By reducing the amount of code, are there sustainability wins? Without the framework, development techniques such as monkey patching or patching to override existing code in either the framework or third-party module are no longer needed.

The application framework layer offers substantial benefit to the expert developer to quickly move forward but does it benefit the socio-technical system as a whole when sustainability enters the equation?

## What a deconstructed model may look like

### User experience

One needs to define what UX (user experience) means to the team. What are the areas where certain user experience approaches are acceptable and where more attention is required due to the skillsets of the users? For example, a metadata expert may be more comfortable working with CSV files whereas a humanities researcher may not, at least initially.

### How dynamic should the site be?

Let us think about content creation. What if it becomes less dynamic? Users no longer have the instant gratification of seeing their changes reflected in the content. How important is it to the user that the system dynamically reflect the content change within seconds? In a micro context, everyone would want instant gratification. In the greater socio-technical system context, a question should be asked, what are the negative trade-offs? What if the context could benefit from a more formal review process of content changes? Think of the editorial review of a book in the publishing world or code review in the software development world. What if adding content to a repository followed a similar set of steps, would this be beneficial to the system as a whole? Removing the dynamic updating would help to reduce complexity and thus may help with sustainability. Plus, without the web application to allow dynamic content changes, the integration with updating the search index and other derivatives of the content/metadata may become less complex and more predictable.

### RDBMS & application frameworks

If the RBBMS is removed, what happens? The application frameworks tend to assume that web forms store content within an RDBMS (e.g., metadata capture, comments, etc.). A big piece of the web application framework is no longer necessary. The RDBMS excels at storing tabular data with type constraints and with possible explicit relationships to other tabular data rows while providing a query language to filter and join tabular data. An RDBMS is a common and well-understood tool by technical experts (taught in computing science education) however, not it is the most user-friendly tool for non-technical people due to the learning curve associated with querying and type constraints. In a project leveraging linked open data, how necessary/effective is the "relational" part of an RDBMS? What happens if the RDBMS's role is removed or greatly reduced? Are there "easier" ways to create, store and manipulate the content that is stored in an RDBMS for those working with the content that helps to reduce the cost of the RDMS and heavyweight application framework without decreasing overall user experience in the socio-technical system and sustainability?  

### Access control

An area in the deconstruction that requires special attention is if/when access control is needed to limit the viewing of select resources. An application framework often contains access control mechanisms and by removing the framework, the reconstructed architecture needs special attention to control access.

For viewing, one possible approach is to leverage an authenticating reverse proxy that provides a means to authenticate the user and track what URL routes the user has access to thus protecting content from anonymous users (e.g., content is inaccessible by default except via the authenticating reverse proxy which decides on whether or not to allow the web request through).

For editing, if the content was split into separate sites (e.g., Git repositories and combined to form a viewable discovery site) then one could limit editing permissions to the content (e.g., S3 object store, Git repository, etc.)

### Batch changes

Are batch changes of content easier and/or more predictable in the deconstructed model? Could the content could be modified offline and then quickly swapped into production with accompanying pieces (e..g, search index, caching). The idea for the content changes: follow or be inspired by the code review practices in software development teams. Also, could the content updates follow similar practices to software development's continuous integration and continuous deployment practices?

### Processes: edit to view

In the deconstructed model, does the same software need to be used to both create and view the content? If a more editorial or software development-influenced view toward the content creation/editorial process was used, one could make content changes and have the change peer reviewed and perhaps updated on a staging site and then committed to the production system. This could provide a version history of changes and the ability to roll back changes without the help of the technical expert (e.g., restore database and content from backups).

### Search index

The search index helps with the discovery of items but in a deconstructed model, how is the search index created and updated without the application framework that also helps to limit access to protected items? Is there a separate site for each group of protected items? Or is there a layer discovery tool that filters depending on the user's access level? Yes, viewing access requires careful thought in this deconstructed model.

### FAIR and OCAP

Are there advantages in the deconstructed model that help to better align with FAIR and OCAP principles? Without the RDBMS and application framework, there are opportunities for a researcher to have more control over their data through more transparency. In mainstream repositories, the contributor is "giving" content to the repository software and relinquishing transparency as often the content is stored in an RDBMS or other opaque data stores.

### Metadata harvesting - OAI-PMH

Repositories allow the ability for outside systems to harvest metadata to create a large, searchable index spanning a large number of repositories. For example, The Alliance FRDR & Lunaris.ca, harvest metadata and provide a cross-repository search layer. An API endpoint is required to interpret the OAI-PMH standard plus a templating system to provide a way to combine the expected OAI-PMH responses with the descriptive metadata (e.g., from a static site generator).

### The tension between sustainability and user experience?

If one decreases the complexity of the software stack, does the user experience also decrease? If the UX is being enhanced only by adding more and more code then possibly yes -- if only viewing the socio-technical system at a micro level and not the larger socio-technical system as a whole. Adding more code to a complex stack adds to the complexity. If one looks at the micro UX question in the greater socio-technical system then then the question to ask is how the change impacts the system as a whole. Considering the whole system, does this micro approach limit UX in another area of the system or make the system increasingly complex and less sustainable? Can a process change or documentation limit the amount of code required?

Can the tension between adding more to increase UX while simplifying to increase sustainability be broken? If one knows the expertise level of the type of person completing a task along with documentation and tools intentionally created with the user's expertise in mind then a project might be able to optimize the result and limit the tension between sustainability and user experience. This is an area that needs consideration when resources are limited, especially when future resource levels are unknown.

## Principles for reconstruction

* remove or limit the RDBMS usage (e.g., only as part of third-party applications or visualizations)
* static sites improve the ability to cache (e.g., dynamic sites require clever caching whereas static pages offer simpler processes to indicate when content has changed, such as purging a CDN)
* user accounts: application frameworks have features and extensions to enable access control to content. Static sites need a cleaver process.
* searching and querying: application frameworks have features and extensions to enable access control to content. Static sites need a cleaver process to enable the searching and querying activity to maintain access controls.

## Thought experiment #1: static site generation

The gist of the socio-technical system: use a static site generation-inspired approach for the discovery layer to replace the heavy-weight framework along with:

* search endpoint
* small, largely independent applications supporting visualization
* LEAF-writer standalone to create/edit content within a Git repository
* a URL-accessible storage service (e.g., S3 or the like) for the media/binary files that do not fit nicely in a Git Repository

### Persistent storage

The experiment views content creation as part of a peer review process akin to editorial work in publishing or code review in software development as opposed to instant production updates (or drafts) in other repositories. The textual content is added/updated/deleted from a Git repository with access controlled by the Git tool. Similarly, the media/binary content not suited for a Git repository is stored in an URL-accessible storage service (e.g., S3) with access controlled by the site. A downside, the two separate storage areas may cause additional effort to manage access (e.g., who has permission to create/update/delete). Also, link checking is required to verify the resource metadata remains linked to the content via active URIs.

Git repositories (e.g., GitHub and GitLab) have become extremely popular in the software development world and are unlikely to undergo significant changes without a well-documented migration plan by the vendors. However, there is a risk of what is free today may have a cost tomorrow. This risk may be mitigated by forming partnerships or agreements with the corporate entity.

### Storage abstraction layer

Each part of the system uses its own storage abstraction layer depending on its specific needs. For example, LEAF-Writer is using a library to interact with a Git Repository. The static site generation may as well too. These would be special purpose and tightly coupled to the tool and data source (i.e., not a general purpose module with more expertise required to use and sustain such as those used in the mainstream repositories). Each visualization may have its own, possibly different, storage abstraction layer and storage (e.g., search index or derivative of the original content to power a visualization application)

### Application frameworks

The idea, rethink a digital asset management system without a heavy-weight software framework.

For the discovery use case, a static site generator-influenced tool would use the content to create a multitude of static pages and structures that would need to be placed on a web server and contain links to the media stored elsewhere (via metadata) and representations of any XML content documents (e.g., TEI, Orlando, etc.). the generator could combine multiple Git repositories into one static site allowing different parts of the site to have different user permissions/roles. A workflow might look like a person commits updates to the Git repository then changes are reviewed and merged into the release branch. A CI/CD process runs automated tests. Perhaps also automated, a staging site is updated with the changes. When the changes are approved, the production site is updated. This process may offer a means to roll back changes to a previous version without the need for a technical expert. The downside, the UX assumes a greater comfort level with the Git workflow compared to a more simplistic web form for creating/updating/deleting. However, this workflow offers the potential for different ways of working with the content via FAIR principles and OCAP principles by allowing a researcher to own/control the Git repository (or media/S3 container) in a transparent way (as opposed to other repositories that have opaque persistent storage layers and require technical experts to access content or create software tools to help with access content in bulk). Without having to dynamically generate the view during each access, the computation resources used to run the site can be decreased. The static nature might offer opportunities to cache pages further helping performance by not having to invoke the software stack during each site/page access. For example, in cwrc.ca, multiple web crawlers seem to randomly walk the content thus limiting the effectiveness of cached pages because they are likely not reused.

For the content creation use case, any tool that the user is comfortable with could be used to interact with the Git repository or the media store.  The create/update/deletion could be supported by any tool. However, LEAF-Writer standalone offers advantages if the textual content is XML. For example, adding linked open data identifiers. LEAF-Writer standalone uses a specialized storage abstraction layer to interact with Git repositories (e.g., GitHub and GitLab).

Search aids in the discovery of content. As part of the static site generation, a search index would need to be built. The static site web pages would need to know how to interact with the search service (e.g., how to submit queries and incorporate search result lists into a view for the user).

What if some content needs to be hidden from the public? One possible approach. The statically generated sites can be similarly split along access lines to the underlying content splits. The static sites can be by default inaccessible to the public with all requests traveling through an authenticating reverse proxy that will only allow requests through to the static web pages that the currently authenticated users have access to view. Authentication and access control add a burden to the site manager that is easier in a mainstream digital asset management system. Limiting search results based on access needs consideration.

Other digital asset management systems create derivatives or service files. These would need to be created as part of the static site generation or part of another parallel process to content creation. Specialized derivatives may be used to power visualization tools depending on the input format for the tool.

Visualization tools and other independent, self-contained tools using the content or derivatives may have their own application stack in this thought experiment instead of being incorporated into the digital asset management system's stack or API. The independence gives the tool flexibility however this may lead to multiple frameworks and languages being used in supporting the site features. On the plus side, the number of interdependencies is decreased thus possibly reducing the complexity of the software though some socio-technical processes may need more human support. Thinking through the impact of the Git content workflow, a visualization leveraging the text-based content would have the ability to be versioned and thus reproducible (e.g., reproduce research paper results). Each tool may have a smaller amount of code (e.g., no need for code to integrate into the software stack). However, the tool may have a different look and feel to the user thus possibly adding a GUI discontinuity and fragmentation of coding style, language usage and framework usage. The self-container tools are easy to remove or replace due to their self-contained nature.

## Words of caution

This thought experiment is not meant to imply that heavy-weight application frameworks are bad. From a sustainability lens, there are positives if the expertise to expertly maintain software using the framework can be retained or easily obtained. If not, choices need to be made around the cost versus benefit in a long-term context. Smaller, lighter, and more readily understandable frameworks and architectures might better align with certain contexts and UX requirements. Using LEAF-Writer standalone and LEAF-Writer integrated into Drupal as an example. The former is simpler to maintain as a content creation platform while the latter's integration with Drupal offers more UX opportunities to be built at a faster rate by an expert if one can sustain the code needed to add the integration.

Moving from one digital asset management system to another or sometimes to a new major version incurs a cost to move the content. One can liken this to moving to a new residence. The new place may look awesome and offer many advantages however moving your current contents and processes is not something one enjoys. Things get lost during the move. Things that fit in the current place do not fit in the new spaces quite right (e.g., the couch might be a bit too long for the wall or the metadata does not have a one-to-one equivalency in the new software). Processes are different and time is needed to adjust. Change requires time and different people adapt to change in different ways and at different rates. Changing to a new system should only be considered after careful thought. In this thought experiment, the aim is to limit the cost by separating the storage from the application and giving those creating and maintaining the content greater flexibility within a set of standards needed to interact with the static site generation and other tools.

Access control makes pieces harder of this experiment hard thus requiring creative approaches to the problem and organization of content to control access.

## Summary

Can minimal computing concepts help create a digital asset management system that better fits the needs of certain organizations? This thought experiment works through the question from a socio-technical system perspective paying special attention to sustainability and user-experience conciderations. The experiment wades into areas including recovery/resilience, editorial process component inspired by code review practices and content transparency/control.

## References

Risam 2022 - <http://digitalhumanities.org/dhq/vol/16/2/000646/000646.html>

DHCC - <https://sas-dhrh.github.io/dhcc-toolkit/toolkit/minimal-computing.h>tml

DHQ 2022 - <http://digitalhumanities.org/dhq/vol/16/2/index.html>

Sayers 2016 - <https://go-dh.github.io/mincomp/thoughts/2016/10/02/minimal-definitions/>
