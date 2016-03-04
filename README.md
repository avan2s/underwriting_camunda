"Underwriting" with BPMN, DMN and CMMN
=========================

This project is a sample application using BPMN + CMMN + DMN to implement a typical underwriting process of an insurance company
(but is actually pretty generic to serve other industries as well). It was initially build for the 
[Camunda Hands-On Webinar on CMMN](https://network.camunda.org/webinars/7).

It includes a user interface for the knowledge worker implemented in JSF.

Built and tested against *Camunda BPM 7.4.0 - alpha3* on JBoss WildFly 8.2.1.

Important note: *Requires JSF - does not run on Tomcat!*

*Required 7.4.x - as DMN is used!*


Show me the important parts!
----------------------------

![CMMN Case](docs/case.png)

The BPMN process starts the underwriting. It implements all structured activities and calls the more CMMN case when the
unstructured phase of the real underwriting from a clerk starts: 

![BPMN Process and CMMN Case](docs/process-and-case.png)


The UI now visualizes all Tasks from Task Management for the case (basically "ACTIVE" activities from CMMN), 
"ENABLED" Activities from CMMN and Historic Tasks from the engine history. Maybe this would be a good time to check out
the [CMMN Lifecycle in our docs](http://docs.camunda.org/latest/api-references/cmmn10/#concepts-plan-item-lifecycles-taskstage-lifecycle):

![BPMN Process](docs/case-ui.png)

And as a last remark I want to point out that it is already built-in the CMMN to call processes from a case:

![BPMN Process](docs/case-and-process.png)

This allows you to use the right tool for the right job - BPMN for structured process parts and CMMN for unstructured ones:

![BPMN Process](docs/structured-vs-unstructured.png)


How to use it?
--------------

You can also use `ant` to build and deploy the example to an application server.
For that to work you need to copy the file `build.properties.example` to `build.properties`
and configure the path to your application server inside it.
Alternatively, you can also copy it to `${user.home}/.camunda/build.properties`
to have a central configuration that works with all projects generated by the
[Camunda BPM Maven Archetypes](http://docs.camunda.org/latest/guides/user-guide/#process-applications-maven-project-templates-archetypes).

Once you deployed the application you can access the user interface:
[http://localhost:8080/underwriting/](http://localhost:8080/underwriting/)

You might also want to inspect it using 
[Camunda Cockpit](http://docs.camunda.org/latest/guides/user-guide/#cockpit) 
and the [ACM Plugin](https://github.com/camunda/camunda-acm-plugin/tree/master/) 
available via the [Plugin Store](http://camunda.org/plugins/).


Webinar Recording
------------------

This example was presented in a Webinar, the recording is available:
- English: http://vimeo.com/116525703
- German: https://vimeo.com/116330092

Environment Restrictions
------------------------

Built and tested against Camunda BPM version 7.4.0 and WildFly 8.2.1. 

License
-------

[Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0).
