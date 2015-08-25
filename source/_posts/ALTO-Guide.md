title: ALTO Guide
date: 2015-08-25 23:48:42
tags:
---

# **Part 1: Work Environment Setup**

## Create your account in Opendaylight Gerrit

* [ODL Gerrit Setup Guide](https://wiki.opendaylight.org/view/OpenDaylight_Controller:Gerrit_Setup)

* [ODL Gerrit Link](https://git.opendaylight.org/gerrit/#/q/status:open)

## Subscribe your email to [alto-dev](mailto:alto-dev@lists.opendaylight.org) email list

* [Link of All ODL Public Mailing Lists](https://lists.opendaylight.org/mailman/listinfo)
* [Link for subscribing alto-dev mailing list](https://lists.opendaylight.org/mailman/listinfo/alto-dev)

* If you are interested in other ODL projects and hope to get latest information from that project, go ahead and subscribe to accordingly mailing list.

## Clone ALTO Project from ODL Gerrit

* You'd better add your ssh-key to the gerrit of ODL. Although it's not necessary to clone a repo from gerrit, if you want to contribute and push your code via git, a ssh-key is needed. Check [ODL Wiki](https://wiki.opendaylight.org/view/OpenDaylight_Controller:Gerrit_Setup#Generating_SSH_keys_for_your_system) for details.

* People in China may not be able to get access to  ODL Gerrit repo because of GFW. You can use Github instead. However, you shall notice that they are just mirrors of projects in ODL gerrit, which means you shall not push code to Github directly.

    * [Opendaylight Github Link](https://github.com/opendaylight)

    * [ODL ALTO Github Link](https://github.com/opendaylight/alto)

## Compile and Install ALTO

### Prerequisites

* [Development Environment Setup for ODL](https://wiki.opendaylight.org/view/GettingStarted:Development_Environment_Setup)

    * **Important:** Don’t forget to edit your ~/.m2/settings.xml file otherwise you will not be able to download any ODL Java dependencies

### Steps

* Enter your ALTO project root directory

* Checkout to stable/lithium branch and run **_mvn compile_** and **_mvn install_** to compile and install ALTO

### Notes:

* If you met any problems while compiling or installing, check **Common Problems List** section at the end of the doc first. If it does not help, please email **_godrickk@gmail.com_**, **_dongs2011@gmail.com_** or **_2010_fno@tongji.edu.cn_** for help.

# **Part 2: ALTO Introduction**

## ALTO Protocol

The full name of ALTO is **Application-Layer Traffic Optimization**. Read [RFC 7285](https://tools.ietf.org/html/rfc7285) to get more details.

## Basic Components

[ALTO in ODL Implementation Introduction Slides](https://docs.google.com/presentation/d/1gsShHkvKO-5f8FsEKg9fgIND00R585B5iF2XEBq-Tv8/edit#slide=id.p)

<table>
  <tr>
    <td>Components</td>
    <td>Description</td>
  </tr>
  <tr>
    <td>ALTO Yang Model</td>
    <td>A YANG Model of data instances and RPCs to support ALTO.</td>
  </tr>
  <tr>
    <td>ALTO Provider</td>
    <td>A simple implementation of endpoint cost map service.</td>
  </tr>
  <tr>
    <td>ALTO Hosttracker</td>
    <td>An implementation of automatically generating network maps and cost maps using collected network host information (by l2switch).</td>
  </tr>
  <tr>
    <td>ALTO Services</td>
    <td>Implementations of RFC 7285 format map services.</td>
  </tr>
  <tr>
    <td>ALTO Northbound</td>
    <td>RESTful API based on ALTO protocol.</td>
  </tr>
  <tr>
    <td>ALTO Manger</td>
    <td>Supports of map managements.</td>
  </tr>
  <tr>
    <td>ALTO Features</td>
    <td></td>
  </tr>
  <tr>
    <td>ALTO Commons</td>
    <td>Common library.</td>
  </tr>
  <tr>
    <td>ALTO Config</td>
    <td>Configs to initiate ALTO services in Karaf.</td>
  </tr>
  <tr>
    <td>ALTO Karaf</td>
    <td>Create e karaf instance with all ALTO features installed </td>
  </tr>
</table>


## Build and run ALTO in Karaf

* Checkout to stable/lithium branch

* Run mvn install to build the project

* Enter into alto-karaf/target/assembly/ directory

* Run command ./bin/karaf to start the karaf

    * It will take some time to install features, initialize services and download dependencies. Be patient and check ./data/log/karaf.log file to track the latest status.

* Play around. You can:

    * use ALTO Manager load/unload maps from/to ODL data store

    * use RESTCONF to read/insert data into ODL data store

    * query map service through ALTO Northbound API

    * Check [ALTO User Guide](https://wiki.opendaylight.org/view/ALTO:Lithium_User_Guide) for more details

## Import ALTO to Eclipse

* Run mvn eclipse:eclipse to generate Eclipse IDE files (*.classpath, *.project …)

* Import ALTO project to Eclipse as general Java projects

* Check [ALTO Developer Guide](https://github.com/opendaylight/docs/blob/master/manuals/developer-guide/src/main/asciidoc/alto/alto-developer-guide.adoc) for more details.

# **Part 3: Useful Docs and Links**

## Open Source Tools Used by Opendaylight Project

[IRC](https://wiki.opendaylight.org/view/IRC): Communicate with other ODL members

[Bugzilla](https://bugs.opendaylight.org/index.cgi): Submit and track bugs related to the OpenDaylight project.

[SonarQube](https://sonar.opendaylight.org/dashboard/index/50636): Help review and manage the code quality of the OpenDaylight project.

[Gerrit](https://git.opendaylight.org/gerrit/#/admin/projects/): Access Git repositories, review, and comment on the OpenDaylight code base.

[Jenkins](https://jenkins.opendaylight.org/releng/): Integrate changes or obtain a fresh build of components.

[Nexus](https://nexus.opendaylight.org/content/repositories/): Proxy remote repositories and share software artifacts.

[Ask](https://ask.opendaylight.org/): Q&A Forum for Developers and Users.

[Wiki](https://wiki.opendaylight.org/view/Main_Page): Opendaylight wiki for developers

## Opendaylight and ALTO Release

[ODL Release Plan](https://wiki.opendaylight.org/view/Simultaneous_Release:Lithium_Release_Plan)

[ODL Release Status Tracker(Google Doc)](https://docs.google.com/spreadsheets/d/1KPpO9LH539Vlcoa4RvLa6PPCdLifi5JD-ihRhlybqeo/edit#gid=676729675)

[ALTO Project Proposal](https://wiki.opendaylight.org/view/Project_Proposals:Alto)

[ALTO Release Plan](https://wiki.opendaylight.org/view/ALTO:LithiumReleasePlan)

[ALTO Release Review](https://wiki.opendaylight.org/view/ALTO:Lithium:Release_Review)

[ALTO Release Note](https://wiki.opendaylight.org/view/ALTO:Lithium:Release_Notes)


