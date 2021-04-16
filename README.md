# PyMOL KVFinder-web Tools

![GitHub Release](https://img.shields.io/github/v/release/LBC-LNBio/PyMOL-KVFinder-web-Tools.svg?color=informational)
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
<!-- [![DOI](http://joss.theoj.org/papers)](http://joss.theoj.org/papers) -->

Welcome to the PyMOL KVFinder-web Tools, this page was built to help you get started with our web service client.

PyMOL KVFinder-web Tools is a PyMOL v2 plugin for detecting and characterizing biomolecular cavities at a KVFinder-web service, which is natively configured to our publicly available web service (http://parkvfinder.cnpem.br/8081).

## Installation

[PyMOL v2](https://pymol.org/2/) is required if you wish to use PyMOL KVFinder-web Tools.

Follow these steps to install PyMOL KVFinder-web Tools:

### Install python packages

Install the required Python packages from [requirements.txt](https://github.com/LBC-LNBio/PyMOL-KVFinder-web-Tools/blob/master/requirements.txt) file.

```bash
pip3 install -r requirements.txt
```

or directly,

```bash
pip3 install pyqt5 toml typing
```

### Install PyMOL KVFinder-web Tools in PyMOL

Download the latest version of PyMOL KVFinder-web Tools from [here](https://github.com/LBC-LNBio/PyMOL-KVFinder-web-Tools/releases/latest/download/PyMOL-KVFinder-web-Tools.zip).

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

## Documentation

Documentation and tutorials are available at https://lbc-lnbio.github.io/KVFinder-web.

## License

The software is licensed under the terms of the GNU General Public License version 3 (GPL3) and is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

---
