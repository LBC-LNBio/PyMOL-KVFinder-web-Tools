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

KVFinder-web (https://parkvfinder.cnpem.br) is an open source web-based application for cavity detection and spatial characterization with parKVFinder software [@Guerra2020] of any type of biomolecular structure. The web application is composed of two modules: a server and a PyMOL plugin client.

The server module (https://github.com/LBC-LNBio/KVFinder-webserver) has a Web-Queue-Worker architecture style. The Web component receives jobs requests in JSON format with detection parameters. If the request is valid, it returns a response with an unique id, based on the provided parameters, corresponding to the accepted job to the client. Otherwise, it returns an HTTP error code with an error message. The client must send a request with an id and the Web component returns "queued", "running" or "completed" together with the respective results. 

The client module (https://github.com/LBC-LNBio/PyMOL-KVFinder-web-Tools) is a plugin that integrates the KVFinder-web server with PyMOL.

# Statment of need

# Acknowledgements

# References
