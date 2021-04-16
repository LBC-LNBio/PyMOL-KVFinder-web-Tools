---
title: 'KVFinder-web: a web-based tool for detecting and characterizing cavities in biomolecules'
tags:
  - Rust
  - C
  - Python
  - PyMOL
  - cavity detection
  - cavity characterization
  - webservice
authors:
  - name: João Victor da Silva Guerra
    orcid: 0000-0002-6800-4425
    affiliation: "1, 2"
  - name: José Geraldo de Carvalho Pereira
    affiliation: 1
  - name: Paulo Sergio Lopes de Oliveira
    orcid: 0000-0002-1287-8019
    affiliation: "1, 2"
affiliations:
 - name: Brazilian Biosciences National Laboratory (LNBio), Brazilian Center for Research in Energy and Materials (CNPEM), Campinas 13083-100, SP, Brazil
   index: 1
 - name: Graduate Program in Pharmaceutical Sciences, Faculty of Pharmaceutic Sciences, University of Campinas, Campinas, SP, Brazil
   index: 2
date: 12 April 2021
bibliography: paper.bib
---

# Summary 

KVFinder-web is an open-source web-based application for cavity detection and spatial characterization with parKVFinder software [@Guerra2020] of any type of biomolecular structure. The KVFinder-web application has two components: a RESTful web service and a PyMOL plugin client. The web service handles requests from the clients, manages accepted jobs and performs cavity detection and characterization on accepted jobs. The client sends job requests to the web service, customize parKVFinder detection parameters and visualize job results on PyMOL [@PyMOL]. Our publicly available KVFinder-web service (https://parkvfinder.cnpem.br), running in a Cloud environment, has some limitations compared to parKVFinder local installation, that are stated on the documentation (https://lbc-lnbio.github.io/KVFinder-web). Hence, users may opt to run jobs on a locally configured server or on our public KVFinder-web service. 

# Statment of need 

Biomolecules, mainly proteins, perform biological processes by interacting with other molecules, which occur at binding sites, located in cavities [@Oliveira2014;@Simoes2017]. These cavities exhibit some specific properties that ultimately dictate the molecules that can bind to them, aiding the understanding of molecular recognition patterns [@Henrich2010]. Thus, detection and characterization of biomolecular cavities play an important role in the rational drug discovery and design pipelines. Based on this, several computational methods have been developed for prospecting and describing binding sites [@Simoes2017], such as parKVFinder that applies a thread-level parallelization to efficiently achieve this goal. Besides its advancements in usability, the installation and configuration of parKVFinder and even other standalone detection cavity software may limit access to less experienced users on local workstations. In addition, some users may lack of computational resources, which can ultimately affect a proper use of parKVFinder. In this sense, we introduced KVFinder-web to democratize and expand even further the user base of parKVFinder in the scientific community. These users will be able to perform cavity detection on outsourced computing platforms, e. g. institutional servers or Cloud infrastructure, which can globally benefit researchers, students and educators with limited computational resources. 

# Server module 

The server module (https://github.com/LBC-LNBio/parKVFinder-webserver), written in Rust, has a Web-Queue-Worker architecture style. The Web component receives jobs requests in JSON format with detection parameters. If the request is valid, it returns a response with a unique id, based on the provided parameters, corresponding to the accepted job to the client. Otherwise, it returns an HTTP error code with an error message. The client must send a request with an id and the Web component returns "queued", "running" or "completed" together with the respective results. The Queue component uses Ocypod software that receives jobs accepted by the Web component. The Worker component communicate with Queue component, requesting "queued" jobs, that will be processed with parKVFinder software. After completion, the job results are sent back to the Web component and made available to the client. According to the processing requirements, new Worker components can be allocated to increase capacity. The server module is packaged inside of a Docker container, making available to execute on different platforms and Cloud services. 

# Client module 

The client  (https://github.com/LBC-LNBio/PyMOL-KVFinder-web-Tools), written in Python, is a Qt interface that integrates the KVFinder-web service with PyMOL. The PyMOL KVFinder-web Tools is a user-friendly graphical user interface (GUI) that enables customization of parKVFinder parameters for a target structure and submits jobs via HTTP POST request to a configured KVFinder-web service. After submission, jobs are routinely requested via HTTP GET request to the KVFinder-web service by a worker thread. When a job is finished, the worker thread automatically processes the incoming data to files and making them available to the GUI. 

Both modules will undergo continuous improvements and updates, according to the needs of the scientific community, including new characterizations and performance enhancements.

# Acknowledgements 

We thank the Brazilian Biosciences National Laboratory (LNBio), part of the Brazilian Center for Research in Energy and Materials (CNPEM) for accessibility to the Computational Biology Laboratory (LBC). This work was supported by the Fundação de Amparo à Pesquisa do Estado de São Paulo (FAPESP) [grant number 2018/00629-0]. 

# References 
