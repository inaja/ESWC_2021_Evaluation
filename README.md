# ESWC_2021_Evaluation

## SHACL proof of concept test 

See the folder shaclValidationExample

## Using OOPS! Ontology Pitfall Scanner  

See the folder oopsValidation for details.

## Creation of Example Knowledge Graph 

We have used the accountability fabric tool in https://github.com/RAINS-UOA/rains-workflow-builder/tree/ESWC-2020. The branch remains frozen with the snapshoot of the tool used for generating and querying the example knowledge graph. 

For details about the knowledge graph see the exampleKnowledgeGraph folder 

## Limitations of the tool

The version of the tool used for evaluation is a proof of concept and not a serious piece of software. It serves a specific purpose and it was mostly used by researchers who were aware of its insufficencies. Use at your own risk..

If you attempt to run the tool please be aware of some unpredictable behaviour that may prevent your data to be saved in the graph store. This is likely related to a bug in the connection pool whcih will be looked at in future. In the meantime, to make sure that your plans and execution traces are saved always restart the server app before pressing save from the HTML page, which reduces the chances of connection freezing. Also the code currently has various validations missing including not escaping special characters that may break JSON-LD payload so be cautios when creating free text (e.g., for labels and comments) and do not use ", etc.   


## Guide to using the tool

### I. Initial Setup and running:
#### A. Install GraphDB 
#### B. Install SPRING workplace and import the project. 
#### C. Launch GraphDB, by default, you can access GraphDB from a browser on http://localhost:7200/. Create a repository with the name ‘AccountabilityFabric’ and make sure that you choose that no inferences are made:
![](figures/IC.png)

#### D. Start SPRING Workplace and run the project as ‘Spring Boot App’. By default, you can access the Accountability Framework from a browser on http://localhost:8080/. Please note that if you downloaded and imported the project (as opposed to pulling it from github) you will need to do the following:
1. Comment out line 49 so that the project complies properly (import org.omg.CORBA.portable.InputStream;).
2.	Create a folder named ‘sqlite’ under the folder src/main/resources.
#### E. Click on ‘Workflow Components Library’
![](figures/IE.png) 
#### F. On this page: 
1.	Browse to the file containing the ontologies.
![](figures/IF1.png) 
2.	Upload SAO. Then also upload RAInS. 
3.	The components are now imported and can used – you do not need to do anything else:
![](figures/IF3.png) 


### II. Creating your AI System:
#### A. Click on ‘Systems Library’
![](figures/IIA.png) 
#### B. Click on ‘Add New System URI’
![](figures/IIB.png) 
#### C. On this page:
1.	Fill in the name of your system in the Label text field (this is a text label, it is not your system’s IRI; the IRI will be automatically created)
2.	Fill in the Description (optional)
3.	Click ‘Submit’
![](figures/IIC.png) 
#### D. The system is now created in the graph store – you do not need to do anything. The ID of the system is clickable and will take you to a new page so you can start populating the fields.
![](figures/IID.png) 

### III. Creating the Plan:
#### A. Click on ‘Systems Library’
![](figures/IIIA.png)  
#### B. Click on the name of the system you want to start with:
![](figures/IIIB.png)   
#### C. On this page:
1.	Section (1) displays the unchangeable details of your system: the IRI which was automatically created, the label, and the description.
2.	Section (2) displays the hierarchy of the system’s accountable objects. You can create Accountable Objects here (For more details ono this, see VIII.A).
3.	Section (3) displays the system’s life cycle (only the Design stage in this version). This is where you can create plans. Note that once you’ve created a plan, the ‘Create Plan’ button will be replaced with a ‘Generate Provenance Collection Interface’ button.
4.	Section (4) displays a button which opens the audit manager in a new tab. At this stage there are no saved provenance records, so the audit manager tab will only display empty results.
![](figures/IIIC4.png)  
#### D. First, create your accountable objects by expanding the list and creating on ‘Add Object’
![](figures/IIID.png)  
#### E. Enter the details of the accountable objects:
![](figures/IIIE.png)   
#### F. The accountable object you created now shows under your system’s name:
![](figures/IIIF.png)   
#### G. Once you’ve created all the accountable object you want, you can proceed to click on ‘Create Plan’:
![](figures/IIIG.png)   
#### H. On this page:
1.	Section (1) is where you input the plan’s label and descriptions as plain text.
2.	Section (2) is where the plan’s steps are created. Steps are dragged from Section (2a) onto Section (2b). Additional elements such as variables are created in Section (3b).
3.	Section (3) is where the plan can be saved and where additional templates can be imported.
![](figures/IIIH3.png)  
#### I. Start with dragging a step from the Steps Library (2a) onto one row of the Workflow Steps (2b):
![](figures/IIII.png)   
#### J. Click on the step to change its label:
![](figures/IIIJ.png)   
#### K. Fill in the description of the step in Inspect Element (2c):
![](figures/IIIK.png)   
#### L. Click on the plus sign next to Inputs or next to Outputs in Inspect Element (2c):
![](figures/IIIL.png)   
#### M. In the popup, click on ‘Create New Variable’:
![](figures/IIIM.png)   
#### N. Fill in the values and click on ‘Add’:
![](figures/IIIN.png)  
#### O. The variable is now created. Click ‘Add Selected Variables’ to add it:
![](figures/IIIO.png)   
#### P. The variable now appears. Click on ‘Apply Changes’ to save the changes for this step:
![](figures/IIIP.png)   
#### Q. Once you’ve finished creating all the steps, your workflow steps will look something like this:
![](figures/IIIQ.png)   
#### R. Click on ‘Save’ in Section (3) to save your plan.
![](figures/IIIR.png)   

### IV. Creating the Provenance Records:
#### A. Back on the System’s page, the ‘Create Plan’ button has now been replaced with a ‘Generate Provenance Collection Interface’ button. Click on it:
![](figures/IVA.png)  
#### B. A new tab opens which displays the Provenance Collector. Fill in the Information in the top section then click on ‘Generate Provenance Collection Tasks’
![](figures/IVB.png) 
#### C. A task to collect provenance is now created, click on ‘click to complete task’ 
![](figures/IVC.png) 
#### D. A new tab opens where you can start populating the fields:
![](figures/IVD.png) 
#### E. Example: Produce System Purpose Specification (this step does not have any inputs from previous steps)
1.	Fill in the Start and End dates of the task
2.	Fill in who performed the task – this has to be an IRI of a person
3.	Fill in the description of the outputs
4.	Click on ‘Add Information Element’ to add information elements, you will get a popup. Choose the type of the information element from the drop-down list. In this example, we will choose ‘Intended Use Case’.
5.	Click on ‘Add Information Element’ to add information elements, you will get a popup. Choose the type of the information element from the drop-down list. In this example, we will choose ‘Intended Use Case’
![](figures/IVE5.png) 
6.	Fill in the other information of this information element and Click ‘Add Element’.
7.	This step will look like the below.:
![](figures/IVE7.png) 
#### F. If a step has inputs from previous steps, it will look like this (the red rectangle highlights the inputs):
![](figures/IVF.png)
#### G. Once you’ve finished, click submit. You will get a confirmation message:
 ![](figures/IVG.png)

### V. Using the Audit Manager:
#### A. Back on the System’s page, click on ‘Open Audit Manager’.
#### B. A new tab opens. Section 1 shows the accountable agents. The IRIs of the accountable agents are clickable. When one is clicked, Section 2 shows the accountable actions that were associated with that agent, along with the results produced by said action (clicking on any of these show their details in the box in Section 3), and what other actions depend on this action (clicking on any of these show their details in the box in Section 3), and how the accountable result relates to an accountable object.
![](figures/VB.png) 
#### C. Click on an agent, for example jane.smith. The Results tab of Section (2) now lists this agent’s accountable actions
![](figures/VC.png)  
#### D. Clicking on accountable result makes Section 3 display its information elements:
1.	
![](figures/VD1.png)  
2.	
![](figures/VD2.png)  
#### E. Clicking on an accountable action which depends on the current one its information elements:
![](figures/VE.png)  

