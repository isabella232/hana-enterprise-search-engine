# SAP HANA Search Example
<!--- Register repository https://api.reuse.software/register, then add REUSE badge:
[![REUSE status](https://api.reuse.software/badge/github.com/SAP-samples/REPO-NAME)](https://api.reuse.software/info/github.com/SAP-samples/REPO-NAME)
-->

## Description
This example shows how to use [SAP HANA Search](https://help.sap.com/docs/SAP_HANA_PLATFORM/691cb949c1034198800afde3e5be6570 "HANA search developer guide") to build a high-performance search-centric application on [SAP HANA DB](https://www.sap.com/products/hana.html) (cloud or on-premise). It is written in Python and demonstrates how to:
- define separated data stores using a schema-based tenant concept
- define an object-oriented data model using a subset of [SAP CAP CSN](https://cap.cloud.sap/docs/cds/csn  "documentation")
- load data in JSON-Format
- search via the OData-based search-API

## Requirements
- Up-to date SAP HANA (on-prem or cloud)
- Latest version of [Python 3.10](https://www.python.org/downloads/ "download")
- [SAP CAP](https://cap.cloud.sap/docs/get-started/ "getting started")

### Additional requirements for development
- [Visual Studio Code](https://code.visualstudio.com/download "download")
- [SAP CDS language support for Visual Studio Code](https://cap.cloud.sap/docs/tools/#add-cds-editor)
- Python linting as described [here](https://code.visualstudio.com/docs/python/linting)


## Download and Installation
Clone or download this repository for example to c:\devpath\hana-search. 

Then open a console and change to the download path:
```bat
c:\ cd c:\devpath\hana-search
```

Create a python virtual environment named .venv:
```bat
c:\devpath\hana-search> python -m venv .venv
```

Activate the python virtual environment:
```bat
c:\devpath\hana-search> .venv\scripts\activate
```

If the environment is activated correctly, a previx (.venv) is shown in the command line:
```bat
(.venv) c:\devpath\hana-search>
```


Install the required Python packages:
```bat
(.venv) c:\devpath\hana-search> python -m pip install -r requirements/core.txt
```
Install additional Python packages if this installation is used for development:
```bat
(.venv) c:\devpath\hana-search> python -m pip install -r requirements/development.txt
```


### Configuration
Configuration is done with the config.py script using the following parameters
- --action install
- --db-host: The HANA host name
- --db-port: The HANA port number
- --db-setup-user: The HANA user name used for setup
- --db-setup-password: The HANA user password for the seup-user. Note: This user-name and passwords are not stored
- --db-schema-prefix: The prefix which is used for the schemas for this installation. E.g. HANA_SEARCH_\<myinitials>

```bat
c:\devpath\hana-search> python src/config.py --action install --db-host <<your_hana_host>> --db-port <<your_hana_port>> --db-setup-user <<your HANA admin user>> --db-setup-password <<your HANA admin password>> --db-schema-prefix <<your HANA >>

```
The configuration will create some HANA DB users and the src/.config.json file which contains configuration information and users and passwords created for the installation (needed e.g. for debugging purposes). Please do not change the src/.config.json file.

The default settings for the web-server (host 127.0.0.1 and port 8000) can be changed using parameters srv-host and srv-port.


To uninstall run the following command:

```bat
c:\devpath\hana-search> python src/config.py --action delete --db-setup-user <<your HANA admin user>> --db-setup-password <<your HANA admin password>>
```
Attention: This will delete ALL data of this installation!

### Start server
Start the server in the console with the activated virtual environment:
```bat
c:\ cd c:\devpath\hana-search
c:\devpath\hana-search> .venv\scripts\activate
(.venv) c:\devpath\hana-search> python src\server.py
```

The message "Application startup complete" indicates a successful server startup.

### Run end-to-end test

```bat
(.venv) c:\devpath\hana-search> python tests\test_suite\e2e_service_test.py
```


## Known Issues
This is an example application in an early stage of development. Hence,
- productive usage is not recommended
- storing personal information is prohibited


## How to obtain support
This is an example application and not supported by SAP. However, you can 
[create an issue](https://github.com/SAP-samples/<repository-name>/issues) in this repository if you find a bug or have questions about the content.
 
For additional support, [ask a question in SAP Community](https://answers.sap.com/questions/ask.html).

## Contributing
If you wish to contribute code, offer fixes or improvements, please send a pull request. Due to legal reasons, contributors will be asked to accept a DCO when they create the first pull request to this project. This happens in an automated fashion during the submission process. SAP uses [the standard DCO text of the Linux Foundation](https://developercertificate.org/).

## [Code of Conduct](CODE_OF_CONDUCT)
## License
Copyright (c) 2022 SAP SE or an SAP affiliate company. All rights reserved. This project is licensed under the Apache Software License, version 2.0 except as noted otherwise in the [LICENSE](LICENSE) file.
