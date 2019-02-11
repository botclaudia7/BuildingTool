# HowToHave2Deploys

Support Fiori LP deployment in common LP (Test space) and separate LP (incubator spaces).

## Overview

This project is a simple FLP app.
The best solution until now is to have 2 folders, each one with mta.yaml file:
- FLPproject: fiori module + app router module + mta.yaml + xs-security.json
- UIproject: UI app + deployer + mta.yaml

## Setup

1. If a module requirs a module declared in another mta.yaml, then the type is org.cloudfoundry.existing-service.
Example: dt_UIproject_ui_deployer

2. The service xsuaa is required for both modules (appRouter and flp).
Example: uaa_FLPproject

3. AppRouter type
- For a build from WebIde:
    - name: FLPproject_appRouter
    - type: approuter.nodejs
- For a build from command line:
    - name: FLPproject_appRouter
    - type: nodejs

Info: for cmd, the flp module will not be created in cockpit, but the app will work in the same mode.

## Deploy

Deploy first the UIproject build and then the FLPproject build.

The FLP app has some problems: can't open portal page (linkapp/cp.portal), but the app could be accessed via id. 
Need to be investigated why.
