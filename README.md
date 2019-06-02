com.ingeint.template
====================

Description
-----------
This project (com.ingeint.template) is a example template for iDempiere plugins. It's a standard structure.
It contains examples about the most frequently used elements (5) Callout, Forms, Models, Processes, Events.


Features
--------
- Copyright: 2015 INGEINT (http://www.ingeint.com)
- Repository: https://bitbucket.org/ingeint/template_idempiere
- License: GPL 2
- Branch: dev


Instructions
------------
- Clone project
- Rename folder com.ingeint.template to com.ingeint.{plugin name}. the name must be lowercase.
- Import to eclipse 
- Rename project into eclipse to com.ingeint.{plugin name}
- Update Name, Version and ID plugin in MANIFEST.MF
- Rename OSGI callout factory component to com.ingeint.{plugin name}.component.CalloutFactory (com.ingeint.component.CalloutFactory.xml, no rename xml file)
- Rename OSGI event manager component to com.ingeint.{plugin name}.component.EventManager (com.ingeint.component.EventManager.xml, no rename xml file)
- Rename OSGI form factory component to com.ingeint.{plugin name}.component.FormFactory (com.ingeint.component.FormFactory.xml, no rename xml file)
- Rename OSGI model factory component to com.ingeint.{plugin name}.component.ModelFactory (com.ingeint.component.ModelFactory.xml, no rename xml file)
- Rename OSGI process factory component to com.ingeint.{plugin name}.component.ProcessFactory (com.ingeint.component.ProcessFactory.xml, no rename xml file)
- Create/Delete/Modify elements
- Add license header to each new file
- Register/Unregister elements in components
- Update README file
- Add TODO file (optional)


Standard New Plugin
-------------------
- New callout
    * Name: C{callout name}
    * Package: com.ingeint.callout
    * Example: com.ingeint.callout.CStringFormat
    
- New process
    * Name: P{process name}
    * Package: com.ingeint.process
    * Example: com.ingeint.process.PGenerateWithholding
    
- New form
    * Name: F{form name}
    * Package: com.ingeint.form
    * Example: com.ingeint.form.FMultiPayment
    
- New event
    * Name: E{event name}
    * Package: com.ingeint.event
    * Example: com.ingeint.event.EAfterCompleteInvoice
    
- New model (extends class X)
    * Name: M{table name without prefix}. 
    * Package: com.ingeint.model
    * Example: com.ingeint.model.X_IGI_TableExample -> com.ingeint.model.MTableExample
    
- Folder estructure
    * com.ingeint.{plugin name}
        |_.settings
        |_.classpath
        |_.project
        |_.hgignore
        |_build.properties
        |_COPYING
        |_README
        |_META-INF
        |   |_MANIFEST.MF
        |_OSGI-INF
        |   |_com.ingeint.component.CalloutFactory.xml
        |   |_com.ingeint.component.EventManager.xml
        |   |_com.ingeint.component.FormFactory.xml
        |   |_com.ingeint.component.ModelFactory.xml
        |   |_com.ingeint.component.ProcessFactory.xml
        |_src
            |_com
                |_ingeint
                    |_base (plugin core)
                    |   |_BundleInfo.java (gets plugin information dynamically)
                    |   |_CustomCalloutFactory.java (IColumnCalloutFactory implementation)
                    |   |_CustomEventManager.java (AbstractEventHandler implementation)
                    |   |_CustomFormFactory.java (IFormFactory implementation)
                    |   |_CustomModelFactory.java (IModelFactory implementation)
                    |   |_CustomProcessFactory.java (IProcessFactory implementation)
                    |   |_CustomCallout.java (IColumnCallout implementation)
                    |   |_CustomEventHandler.java (for event implementation)
                    |   |_CustomFormController.java (IFormController implementation)
                    |   |_CustomProcess.java (SvrProcess implementation)
                    |_component (pugin components)
                    |   |_CalloutFactory.java (register class callout)
                    |   |_EventManager.java (register class event handler)
                    |   |_FormFactory.java (register class form)
                    |   |_ProcessFactory.java (register class process)
                    |   |_ModelFactory.java (register class model)
                    |_callout (new callouts, extends CustomCallout)
                    |_event (new events, extends CustomEventHandler)
                    |_form (new forms, extends CustomFormController)
                    |_process (new processes, extends CustomProcess)
                    |_model (autogenerated models)
        
        
Standard TODO file
------------------
TODO is a file for general task list.

Standard for pending task:
- [ ] {pending task}

Standard for complete task:
- [x] {year-month-day} {complete task}

Example: 
- [ ] Database standard name
- [x] 2015-11-03 Standard for TODO file


Standard Backup Database file name
----------------------------------
Test Database:
    * Name: {database name}_T{yearmonthdayhourmin}.{database}
    * Example: idempiere_T201511031125.postgres
    
Development Database:
    * Name: {database name}_D{yearmonthdayhourmin}.{database}
    * Example: idempiere_D201511031125.postgres
    
Production Database:
    * Name: {database name}_P{yearmonthdayhourmin}.{database}
    * Example: idempiere_P201511031125.postgres

    
Documentation
-------------
- New callout
    * Create callout in package com.ingeint.callout, extends CustomCallout
    * Add license header, copy from file other_templates/license template header.txt
    * Update license header variables: {year}, {name of contributor}, {email}
    * Register callout in com.ingeint.component.CalloutFactory. Example:
        protected void initialize() {
            registerCallout(MTableExample.Table_Name, MTableExample.COLUMNNAME_Text, CPrintPluginInfo.class);
        }
    
- New process
    * Create process in package com.ingeint.process, extends CustomProcess
    * Add license header, copy from file other_templates/license template header.txt
    * Update license header variables: {year}, {name of contributor}, {email}
    * Register process in com.ingeint.component.ProcessFactory. Example:
        protected void initialize() {
            registerProcess(PPrintPluginInfo.class);
        }
    
- New form
    * Create form in package com.ingeint.form, extends CustomFormController
    * Add license header, copy from file other_templates/license template header.txt
    * Update license header variables: {year}, {name of contributor}, {email}
    * Register form in com.ingeint.component.FormFactory. Example:
        protected void initialize() {
            registerForm(FPrintPluginInfo.class);
        }
    
- New event
    * Create event in package com.ingeint.event, extends CustomEventHandler
    * Add license header, copy from file other_templates/license template header.txt
    * Update license header variables: {year}, {name of contributor}, {email}
    * Register event in com.ingeint.component.EventManager. Example:
        protected void initialize() {
            registerTableEvent(IEventTopics.DOC_BEFORE_COMPLETE, MTableExample.Table_Name, EPrintPluginInfo.class);
        }
    
- New model (extends form class X)
    * Create model in package com.ingeint.model, extends class X. Example: com.ingeint.model.X_IGI_TableExample -> com.ingeint.model.MTableExample
    * Add license header, copy from file other_templates/license template header.txt
    * Update license header variables: {year}, {name of contributor}, {email}
    * Register model in com.ingeint.component.ModelFactory. Example:
        protected void initialize() {
            registerTableModel(MTableExample.Table_Name, MTableExample.class);
        }

- Other templates, files into folder other_templates/:
    * README: Template for README files
    * COPYING: GPL 2 License
    * hgignore: Template .hgignore file. Rename to .hgignore
    * license template header.txt: License GPL 2 header. Copy to each new file. Update variables: {year}, {name of contributor}, {email}
    * databaseBackup.sh and databaseRestore.sh: List commands for database backup and restore
    * INGEINT Entity Type.zip: Standard INGEINT Entity Type, Packout
    * INGEINT Table Template.zip: Table Template, Packout
    * INGEINT Table Doc Template.zip: Table Template for new document, Packout
    * INGEINT 2Pack com.ingeint.template.zip: 2Pack for test com.ingeint.template plugin
    * ExampleClass.java: Template for class documentation


Standard Repo Name
------------------
- Lowercase name
- Word separator: underscore "_"

- Product:
    * {name}_{platform}
    * Example: id-asset_idempiere, id-asset_wince, id-asset_android

- Customization:
    * {client}_custom
    * Example: bce_custom
    

Standard Table/Column Name
--------------------------
- For new table/column use prefix IGI_. Example: IGI_TableExample
- Use iDempiere convention: Capitalization name. Example Column Name: IGI_IsExample


Standard Branchs
----------------
- dev: This Branch it's for development
- release: This branch it's for stable source
- Versions: The software version  are controlled by tag. Tag name standard on release branch is v{current}.{revision}.{maintenance}. Example: v1.2.0
- Versions unstable: Tag name standard for dev branch is {type(alpha/beta)}{sequence}. Example: alpha1, beta1


Standard Class Documentation
----------------------------
- Example: other_templates/ExampleClass.java
- Language: English
- Include an example if necessary. Use tag <pre></pre>