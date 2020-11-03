<!-- -----------------------------------------------------------------------------------------------
https://github.com/JoshuaRady/FOSS_EcoForce5_DMP/README.md
EcoForce5 Team
Started: 11/3/2020
------------------------------------------------------------------------------------------------ -->

<!-- Header: -->
<img src="/images/EcoForce5_Header.png">

# EcoForce5 Reproducibility Lab

Welcome to the lab!  This guide explains how we work with data in our lab team, but it is not just a set of rules.  For us data is a central part of the science that we do.  We strive for a culture that treats data in a way that will allow it to be as usefully as possible to ourselves and others.

## Team Members
*[Kyla Dahlin](http://geo.msu.edu/people/dahlin-kyla/) (Michigan State)  
[Debjani Sihi](http://envs.emory.edu/home/people/bios/Sihi-Debjani.html) (Emory)  
[R. Quinn Thomas](https://rquinnthomas.com) (Virginia Tech)   
[Jessica L. O'Connell](https://www.landscapemodeling.net) (University of Texas at Austin)  
Joshua Rady (Virginia Tech)*

## Principles

This lab uses a reproducible research philosophy and an open science approach. We also ascribe to [FAIR](https://en.wikipedia.org/wiki/FAIR_data) data practices. Our goal is that *any lab member should be able to reproduce the work of any other* and that project workflows and data will be properly documented, shared and archived. Raw data and subsequent data products generated by individual participants in this research team are a common asset, and we place high priority on promoting transparency, accessibility, and sharing of these data assets within the research team, the broader scientific community, and with the public. To encourage transparency and reproducibility, we will use open-source analytical platforms, such as R, that allow us to document our data processing and analysis steps through open-source code, where feasible. We commit to timely publication of our research results and to rapid and open access to these data products. 

## **EcoForce5 Lab Data Management Plan**

This plan sets clear general guidelines for handling data within our lab group and when working with collaborators.  This plan is designed to be compatible with NSF DMP guidelines but in some cases the individual grant DMPs may supersede this document for specific projects.  If you have questions, ask one of the lab leaders.  If you have ideas for how to improve this plan, bring them up at lab meeting

### Roles & Responsibilities

The lab Principal Investigator (PI; Dr. EcoForce) is solely responsible for the quality and direction of research in the lab. While different projects have different leadership structures, if the PI is the lead on a grant that is funding the research, then the PI is responsible for reporting progress, products, data storage, etc, to the funders. As such, any new project should begin with a discussion with the PI about data storage, data security (if relevant), project objectives, and reporting requirements. As a data driven lab group, data management paramount to our research success, so adhering to the following guidelines is essential. Questions about data and methods should be directed to the PI as soon as possible.

### Reproducible Research Analysis Guidelines

Our research is meant to be reproducible and readily shared. As part of this, analytical projects are meant to be easily portable to new computational environments and will often be archived for the public following publication. To make our manuscript analyses portable, we should organize the data and files associated with a manuscript into hierarchical folders that can be referenced with relative paths. To facilitate this, please use a consistent hierarchical folder structure as follows:

#### Manuscript Folder Structure:
##### Big Data folder:
- A folder on a shared file server, outside the manuscript project folder, that can be accessed by all team members. Large, relatively unportable datasets, such as satellite data, are stored here, and accompanied by metadata.

##### Manuscript:
- data: raw data specific to the manuscript, with metadata, and soft links to data in the big data folder
- functions: function scripts shareable among multiple analysis scripts
- analysis: data processing and analysis scripts
- output: derived data created by the data processing/analysis scripts
- results: figures/tables saved by analysis scripts
- doc: manuscript text and project documentation

Manuscript analyses are also meant to be reproducible by others. To accomplish this, we will preserve our raw data files without directly manipulating them and document our data and analysis steps through the use of an open-source scripting language such as R. Raw data that are only used in the manuscript go into the data folder. The manuscript data folder can also include soft links to folders outside of the project where large data files are stored and shared among multiple manuscripts.

When creating data processing and analysis scripts, the purpose of each analysis needs to be clear. Include comments at the top of each script describing the general purpose of the analysis/data steps. In the body of the script, code should be sufficiently commented so that the purpose of code lines are clear. While you might work on your manuscript project folders on your personal computer, these should be backed up to the lab server periodically (see [Backups](https://github.com/JoshuaRady/FOSS_EcoForce5_DMP/#data-backups-and-versioning)), and especially at the conclusion of the project before leaving the lab. 

Analyses are meant to be portable among computational environments (HPCCs, cloud computing, personal laptops, etc). Thus, don’t use absolute paths to data in scripts, rather analyses should reference data via relative paths, with the absolute path to the data folder stored in a variable at the top of the analysis.

### Data

#### Data Types and Formats:

In the lab we work with *new data* we generate, *shared data* we get from collaborators, and *open data* we access off the web. In general we assume open data is archived and backed up elsewhere and does not need to be re-archived by us, but new data and shared data should be treated as though they have no other backup (see [Data Backups & Versioning](https://github.com/JoshuaRady/FOSS_EcoForce5_DMP/blob/main/README.md#data-backups-and-versioning)).

Paper data on data sheets or in notebooks should be backed up electronically by photographing/photocopying the data sheets and storing the copies on the lab server. This should be done as soon as possible after data collection to avoid data loss. The prefered format for scanned materials is PDF or for images lossless compressed TIFFs with a resolution of no less than 300 dpi.

Paper data should also be transcribed into tabular data as soon as possible. Transcribed data should be checked for data error entries directly after transcription.

Tabular data should be stored in Tidy data format: columns as data attributes and rows as data records, data are sortable, no blank cells (use 0 for values and -9999 or NA as appropriate for true missing values), attributes about data are stored as variables in text columns (not through color coding, etc). ALWAYS store a version of your data as a .csv file (never just .xlsx, even if you use Excel or similar to enter data).

Data types we use in the Lab include:
- Tablar (csv, txt)
- GeoTIFFs
- HDF5
- netCDF
- LAS/LAZ
- Shapefiles
- jpegs
- TIFFS
- Portable Document Format (PDF)

Members of the Lab have various expertise in these data types. Always ask around if you need help with a new data type!

#### File Names:

Use file names that are cross platform:
Do not use special characters other than dash/hyphen (-), underscore (_), and period/dot (.).  Keep file names short, definitely not longer than 143 characters.  (Long file names may mean you are trying to store data in them.  See below.)

Always include the 1-3 character file extension (e.g. ‘.txt’).

Avoid extra dots in file names when possible.  (Some outside files will come with more than on dot in their names and that's OK.)

##### Do not store data in file names:  
Filenames are prone to being changed so no critical information should be stored only in a file’s name.  For example, store the date of collection for a set of data in the file, not just in the file name.

If a file was obtained from elsewhere and lacks information internally to unambiguously identify it associate the appropriate metadata with the file (see metadata)

##### Chose wisely:  
Assume others will look at your work.  Will they be able to interpret your files names?

Use named directories to organize files and give them context (rather than just using longer names.)

Using case in file names to increase readability is fine but do not rely on case alone to distinguish between files.

Use whitespace carefully.  Spaces in file names may be fine for human readable files but can cause issues on the command line.

#### Metadata:

If you are downloading data from somewhere, make sure to include any metadata or data protocol information with the data. If you are generating new data, at minimum you should create a ‘readme.txt’ file in the same directory as your data with the basic info about what it is, who collected it, and how to contact you with questions.

#### Data Storage:

ALL *NEW OR SHARED DATA* MUST BE BACKED UP WEEKLY if it is actively being manipulated/added to on the Lab server/HPCC. If you are working on a project it should be backed up monthly at minimum. Remember, the less frequently you back up, the more work you lose in the event of a catastrophic failure.

#### Data Backups and Versioning:

Data represents time, energy, money and progress.  Don’t lose it!

All computers, including any personal computer used for lab research, should employ a multiple tiered backup system.
- Local backups:  All computers must have at least one backup drive that automatically archives the computer’s data directory.  For desktop machines backups should run at least hourly.  For laptops you should connect to your drive to backup at least daily.
- Cloud backups:  All computers must also perform automatic backups to (a/our) cloud backup service.

#### Data Archive:

All new data generated by the lab should be archived indefinitely on the lab server as well as in paper format at the end of the project, with one copy stored in the lab and one in the PI’s office.

#### Data Retention:

As analyses are completed data copies should be moved to the lab’s institutional data repository.  This data should be retained for at least 5 years beyond the completion of the funding grant, longer if required by the grant’s DMP, and indefinitely if possible.  To ensure the integrity of stored data checksums should be performed and stored with a list of all files in the analysis directory.

#### Data Sharing:

To the greatest extent possible we seek to contribute our data to appropriate data stores at the time of publication. This increases the likelihood of our data getting shared and used! As a second option, data should be published with manuscripts via an online service like Zenodo, EDI, Mendeley, etc.
