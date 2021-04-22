---
title: 'KVFinder-web: a web-based application for detecting and characterizing cavities in biomolecules'
tags:
  - Rust
  - Python
  - PyMOL
  - cavity detection
  - cavity characterization
  - web service
  - web server
authors:
  - name: João Victor da Silva Guerra
    orcid: 0000-0002-6800-4425
    affiliation: "1, 2"
  - name: Helder Veras Ribeiro Filho
    orcid: 0000-0001-8471-207X
    affiliation: 1  
  - name: José Geraldo de Carvalho Pereira^[corresponding author]
    orcid: 0000-0003-1041-0209
    affiliation: 1
  - name: Paulo Sergio Lopes de Oliveira^[corresponding author]
    orcid: 0000-0002-1287-8019
    affiliation: "1, 2"
affiliations:
 - name: Brazilian Biosciences National Laboratory (LNBio), Brazilian Center for Research in Energy and Materials (CNPEM), Campinas 13083-100, SP, Brazil
   index: 1
 - name: Graduate Program in Pharmaceutical Sciences, Faculty of Pharmaceutical Sciences, University of Campinas, Campinas, SP, Brazil
   index: 2
date: 19 April 2021
bibliography: paper.bib
---

# Summary 

KVFinder-web is an open-source web-based application of parKVFinder software [@Guerra2020] for cavity detection and spatial characterization of any type of biomolecular structure. The KVFinder-web application has two components: a RESTful web service and a PyMOL plugin client. The web service handles requests from the clients, manages accepted jobs and performs cavity detection and characterization on accepted jobs. The client sends job requests to the web service, customize parKVFinder detection parameters and visualize job results on PyMOL [@PyMOL]. We provide a publicly available KVFinder-web service at http://parkvfinder.cnpem.br, running in a Cloud environment; additionally, a KVFinder-web service can also be configured locally. Hence, users may opt to run jobs on a locally configured service or on our public KVFinder-web service.

# Statment of need 

Biomolecules, such as proteins, perform biological processes by interacting with other molecules at binding sites [@Oliveira2014;@Simoes2017]. These sites are mostly cavities that exhibit specific properties and, ultimately, dictate the preference for molecules to bind [@Henrich2010]. Thus, detection and characterization of biomolecular cavities play an important role in the rational drug discovery and design pipelines. Based on this, several computational methods have been developed for prospecting and describing binding sites [@Simoes2017], such as parKVFinder that applies a thread-level parallelization to efficiently achieve this goal. Besides its advancements in usability, the installation and configuration of parKVFinder and even other standalone detection cavity software may limit access to less experienced users on local workstations. In addition, some users may lack of computational resources, which can ultimately affect a proper use of parKVFinder. In this sense, we introduced KVFinder-web to democratize and expand even further the user base of parKVFinder in the scientific community. These users will be able to perform cavity detection on third-party computing platforms, e. g. institutional servers or Cloud infrastructure, using parKVFinder as a service (SaaS), which can globally benefit researchers, students and educators with limited computational resources.

# Web service 

The web service (https://github.com/LBC-LNBio/KVFinder-web-service), written mainly in Rust, has a Web-Queue-Worker architecture. The web server module receives jobs requests in JSON. If the request is valid, it returns a response with a unique id. Otherwise, it returns an HTTP error code with an error message. This id is created by the server, applying a hash function into the received data, which includes parameters and the molecular structures. Accepted jobs are sent to the queue module, where they wait until requested by the worker module. The queue module uses Ocypod service (https://github.com/davechallis/ocypod) to manage accepted jobs sent by the web server module. The worker module communicates with queue module, requesting "queued" jobs, that will be processed with parKVFinder software. However, to prevent highly demanding jobs from exhausting the web service, some parKVFinder parameters are constrained or even pre-defined. After completion, the job results are sent back to the queue module and made available to the client via the web server module. In order to get the job results back, the client must send a HTTP request with a valid id and the web server module returns the current job status - "queued", "running" or "completed" - together with its respective results if available. According to the processing requirements, more worker modules can be allocated to allow the processing of more than one job concurrently. Each web service module is packaged inside of a Docker container, making available to execute on different platforms and Cloud services.

# Client (PyMOL plugin) 

To interact with the web service, we developed a graphical client (https://github.com/LBC-LNBio/PyMOL-KVFinder-web-Tools), written in Python and Qt, that integrates the KVFinder-web service with PyMOL. The PyMOL KVFinder-web Tools is a user-friendly graphical user interface (GUI) that enables customization of parKVFinder parameters for a target structure and submits jobs via HTTP POST request to a configured KVFinder-web service. After submission, jobs are routinely and asynchronously requested via HTTP GET request to the KVFinder-web service. When a job is finished, the client automatically processes the incoming data to files and makes it available to the GUI. The PyMOL KVFinder-web Tools is the recommended client to our publicly available web service.  Besides, we developed a client script, also written in Python, to guide other developers to create standalone clients according to their specific needs. 

Both web service and client modules will undergo continuous improvements and updates, according to the needs of the scientific community, including new characterizations and performance enhancements.

# Acknowledgements 

We thank the Brazilian Biosciences National Laboratory (LNBio), part of the Brazilian Center for Research in Energy and Materials (CNPEM) for accessibility to the Computational Biology Laboratory (LBC). This work was supported by the Fundação de Amparo à Pesquisa do Estado de São Paulo (FAPESP) [grant number 2018/00629-0]. 

# References 
