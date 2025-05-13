---
date: '2025-05-13'
draft: false
title: 'Transforming Power Grids from OpenStreetMaps to CIM with the help of linkml'
---

# Work in Progress

This text documents the work to transform power grid infrastructure data from OpenStreetMaps to the Common Information Model (CIM) using linkml.

* Source Data: The source data is available on [zenodo](https://zenodo.org/records/14144752). It is documented in this [paper](https://doi.org/10.1038/s41597-025-04550-7) and comes in the data format from Pypsa, a power system modeling tool.
* The [Common Information Model - CIM](https://www.entsoe.eu/digital/common-information-model/) is a data model for all kind of data relevant to the electricity grid. 
* [`linkml`](https://linkml.io/linkml/) is a python package to create and work with data models. An [existing project from Netbeheer Nederland](https://github.com/Netbeheer-Nederland/im-tc57cim/) has already created a linkml schema for CIM.
* Only a small subpart of the CIM is needed for the given task, hence [`gen-linkml-profile`](https://github.com/Netbeheer-Nederland/gen-linkml-profile) will be used to create a CIM profile with the relevant classes.

## Steps to reproduce

* Create a python environment and install the [`gen-linkml-profile`](https://github.com/Netbeheer-Nederland/gen-linkml-profile) library.
* Copy the linkml CIM schema file from [this repository](https://github.com/Netbeheer-Nederland/im-tc57cim/) 
* Create a profile for the OSM grid data by running
    ```bash
    gen-linkml-profile profile im_tc57cim.schema.linkml.yml -c ConductingEquipment -c GeneratingUnit \
    -c Substation -c PowerTransformer -c TransformerWinding -c GeneratingUnit -c SynchronousMachine \
    -c EnergyConsumer -c ACLineSegment -c Terminal -c ConnectivityNode -c Length \
    -c Resistance -c Reactance -c Susceptance -c BaseVoltage -c Voltage > osm-profile.yml
    ```
    This creates a profile with the relevant classes in a new .yml file.
* Create a python dataclasses using the command `gen-python osm-profile.yml > orm.py`.
* Parse the csv files from [zenodo](https://zenodo.org/records/14144752) and use the [python linkml generators](https://linkml.io/linkml/data/python.html) to create the relevant data objects. Dump the objects to a yml file. This looks like this:
    ```yml
    Equipments:
    - aliasName: merged_way/680204409-220+3
    mRID: '#_fdd83d-6cc5-4f7c-90b5-b616044857ea'
    BaseVoltage:
        mRID: '#_8ce6ab-b3e9-42a8-9b85-51ba726a1227'
        nominalVoltage:
        multiplier: k
        unit: V
        value: 220.0
    length:
        unit: m
        value: 8098.240000000001
    bch:
        unit: none
        value: 3.18e-05
    r:
        unit: ohm
        value: 0.485894
    x:
        unit: ohm
        value: 2.43757
    - aliasName: way/655764544-220
    mRID: '#_ffae21-d206-4850-8db4-d6f3ee0ad094'
    BaseVoltage:
        mRID: '#_8ce6ab-b3e9-42a8-9b85-51ba726a1227'
        nominalVoltage:
        multiplier: k
        unit: V
        value: 220.0
    length:
        unit: m
        value: 16065.22
    bch:
        unit: none
        value: 6.309e-05
    r:
        unit: ohm
        value: 0.963913
    x:
        unit: ohm
        value: 4.835631
    ```  

* Use the linkml converter to convert the data instance to rdf format: `linkml-convert --no-validate -s osm-profile.yml -C ACLineSegment -t rdf lines.yml`