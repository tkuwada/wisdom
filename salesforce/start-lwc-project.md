# Start Lightning Web Component Project


##  Setup Salesforce Org

-  Setup my domain

-  Anable Devhub

##  Local development enviropment

####  Install Tools
- [Salesforce CLI](https://developer.salesforce.com/ja/tools/sfdxcli)

####  VSCode

####  Install VSCode Extention

-  [Salesforce Extension Pack](https://marketplace.visualstudio.com/items?itemName=salesforce.salesforcedx-vscode)

[dependencies]
 - the Java 8 Platform.
 
###  1.Create Project

create project.
####  VSCode
  [Ctrl] + [Shift] + [P] > "SFDX:Create Project with Manifest "

#### sfdx command
```
sfdx force:project:create --projectname {your projectname}
```

### 2.Authorize DevHub
####  VSCode
  [Ctrl] + [Shift] + [P] > "SFDX: Authorize a Dev Hub"

#### sfdx command
```
sfdx force:auth:web:login --setdefaultdevhubusername
```


### 3.Authorize DevHub
####  VSCode
  [Ctrl] + [Shift] + [P] > "SFDX: Authorize a Dev Hub"

#### sfdx command
```
sfdx force:auth:web:login --setdefaultdevhubusername
```

### 4.Create Scratch Org

####  VSCode
  [Ctrl] + [Shift] + [P] > "SFDX: Create a Default Scratch Org"

#### sfdx command
```
sfdx force:org:create -f config\project-scratch-def.json --setalias {your some alias} --durationdays 30 --setdefaultusername
```

### 5. Create Lightning Web Component

####  VSCode
Right click mouse on "force-app/main/default/lwc" > select "Create Lightning Web Component"

#### sfdx command
```
sfdx force:lightning:component:create --type lwc --componentname {your lwc name} --outputdir force-app\main\default\lwc
```

### 6. Deploy Lightning Web Component

####  VSCode
Push the source local to default scratch org.
```
sfdx force:source:push -u {targetusername or alias}
```
[Note] if unset "-u" option, use default target org form config.  

  
Right click mouse the source code. and select "SFDX: Deploy Source to Org"
```
sfdx force:source:deploy --sourcepath {the soure path}
```
