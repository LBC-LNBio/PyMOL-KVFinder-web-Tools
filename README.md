# PyMOL KVFinder-web Tools

![GitHub release (latest by date)](https://img.shields.io/github/v/release/LBC-LNBio/PyMOL-KVFinder-web-Tools?color=informational)
![GitHub](https://img.shields.io/github/license/LBC-LNBio/PyMOL-KVFinder-web-Tools)

Welcome to the PyMOL KVFinder-web Tools, this page was built to help you get started with our graphical PyMOL plugin for [KVFinder-web service](https://github.com/LBC-LNBio/KVFinder-web-service).

## KVFinder-web

KVFinder-web is an open-source web-based application of [parKVFinder](https://github.com/LBC-LNBio) software for cavity detection and spatial characterization of any type of biomolecular structure.

The KVFinder-web application has two independent components:

- interactive graphical clients, that are:
  - [PyMOL KVFinder-web Tools](https://github.com/LBC-LNBio/PyMOL-KVFinder-web-Tools): a graphical PyMOL plugin.
  - [KVFinder-web portal](https://github.com/LBC-LNBio/KVFinder-web-portal): a graphical web portal;
- a RESTful web service: [KVFinder-web service](https://github.com/LBC-LNBio/KVFinder-web-service);

The full KVFinder-web documentation can be found here: <http://lbc-lnbio.github.io/KVFinder-web>.

### PyMOL KVFinder-web Tools

The PyMOL KVFinder-web Tools, written in Python and Qt, is a PyMOL v2.x plugin for detecting and characterizing biomolecular cavities at a KVFinder-web service with functionalities similar to [PyMOL parKVFinder Tools](https://github.com/LBC-LNBio/parKVFinder/wiki/parKVFinder-Tutorial#pymol2-parkvfinder-tools), which is natively configured to our publicly available web service (<http://kvfinder-web.cnpem.br>).

#### Installation

[PyMOL v2](https://pymol.org/2/) is required if you wish to use PyMOL KVFinder-web Tools.

To install the Python dependencies from [requirements.txt](https://github.com/LBC-LNBio/PyMOL-KVFinder-web-Tools/blob/master/requirements.txt), run:

```bash
pip3 install -r requirements.txt
```

To install PyMOL KVFinder-web Tools, download the latest version of PyMOL KVFinder-web Tools from [here](https://github.com/LBC-LNBio/PyMOL-KVFinder-web-Tools/releases/latest/download/PyMOL-KVFinder-web-Tools.zip). Now, follow these steps:

1. Open PyMOL;
2. Go to **Plugin** menu and select **Plugin Manager** option;
3. The **Plugin Manager** window will open, go to the **Install New Plugin** tab;
4. Under **Install from local file** group, click on **Choose file...**;
5. The **Install Plugin** window will open, select the `PyMOL-KVFinder-web-Tools.zip`;
6. The **Select plugin directory** window will open, select `/home/user/.pymol/startup` and click **OK**;
7. The **Confirm** window will open, click on **OK**;
8. The **Sucess** window will open, confirming that the plugin has been installed;
9. Restart PyMOL;
10. **PyMOL KVFinder-web Tools** is ready to use under **Plugin** menu.

Or, if you clone this [repository](https://github.com/LBC-LNBio/PyMOL-KVFinder-web-Tools), instead of selecting `PyMOL-KVFinder-web-Tools.zip` (Step 5), user must select `__init__.py` of PyMOL-KVFinder-web-Tools directory.

To use the PyMOL KVFinder-web Tools in a locally configured KVFinder-web service, users must change the server url and port hardcoded on the [**init**.py](https://github.com/LBC-LNBio/PyMOL-KVFinder-web-Tools/blob/main/PyMOL-KVFinder-web-tools/__init__.py) file and reinstall the client plugin on PyMOL.

From:

```bash
    # Server                                 #
    server = "http://kvfinder-web.cnpem.br"  #
    # Path                                   #
    port = "/api"                            #
```

to:

```bash
    # Server                                 #
    server = "http://localhost:8081"         #
    # Path                                   #
    path = ""                                #
```

If the KVFinder-web service is on another computer on your network, you must provide the IP Address instead of localhost.

### KVFinder-web portal

The KVFinder-web portal, written in R and Shiny, is a graphical web application for detecting and characterizing biomolecular cavities at a KVFinder-web service, natively configured in our publicly available web service ([http://kvfinder-web.cnpem.br](http://kvfinder-web.cnpem.br)).

### KVFinder-web service

KVFinder-web service, written in Rust language, has a robust web-queue-worker architecture that processes HTTP requests and responses from the interface, manages jobs, and executes parKVFinder for accepted jobs.

## Funding

KVFinder-web interface was supported by Fundação de Amparo à Pesquisa do Estado de São Paulo (FAPESP) [Grant Number 2018/00629-0], Brazilian Biosciences National Laboratory (LNBio) and Brazilian Center for Research in Energy and Materials (CNPEM).

## License

The software is licensed under the terms of the Apache-2.0 License and is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the Apache-2.0 License for more details.

---
