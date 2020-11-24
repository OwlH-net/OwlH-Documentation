Suricata Ruleset management
===========================

Use OpenRules for Suricata to:

  * create local rulesets based on 3rd party rulesets and custom rules
  * synchronize each local ruleset with one or more nodes 
  * schedule ruleset update
  * edit rules from User Interface
  * enable or disable rules 
  * search rules and find where are rules installed and stored

Ruleset Management 
------------------

**concepts** 

:ruleset source: Is a ruleset that can be use to create your local rulesets. This ruleset source can be from a local file with custom rules or from a 3rd party vendor like Emerging Threat. 

:local ruleset: Is the ruleset you want to use in one or more OwlH Nodes that are running Suricata. You will create it by using one or more ruleset sources. you can include all ruleset files or just select a few files. 

**Creation process**

 #. configure ruleset sources.
 #. configure local ruleset using sources.
 #. assign ruleset to Suricata services
 #. sync.

**Ruleset Maintenance process**

 #. set scheduler to update your source ruleset with latest updates.
 #. decide if you want to overwrite your local ruleset with any new update or if you prefer to just include the new rules included.
 #. send the updated ruleset to your Suricata systems and reload it.

 All this maintenance process is defined in local ruleset with the schedule configuration.

**Manage rules**

 from UI -> Open Rules you have multiple options. 

  :Search bar: you can find rules using a SID, or a ruleset name, or any other param. This search result will show you rules matching search criteria, rules status and ruleset and file where rule is stored.

  :Create Local Ruleset: Action to create a new local ruleset, you will be prompted for a name, description and you will select ruleset sources to be included in your ruleset, and you will choose the files you want to include. you can decide to fully include a ruleset source, or just include a few files. Also you can include your custom rules as they will be consider a ruleset source. 

  :Manage Ruleset Sources: Action to manage, create, delete, edit your sources. We do provide a default ruleset list to help you create a few of them in a few clicks. You can add your own 3rd party providers as well as your custom rules files. 

  :Sync all: Action to send all rulesets to each OwlH Node running suricata. Suricata will only receive the ruleset that is selected on Suricata service under node configuration.

  :Local Rulesets table: Is the list of available rulesets to be synchronized with any suricata service. You can edit the ruleset to change ruleset content. You can see ruleset details, which includes all rules files in the ruleset, allows you to see all rules on each file and do actions like Edit rule, disable/enable rule, or clone rule. Also you can write a note about the rule to specify why the rule is there.
