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

**Management process**

 #. configure ruleset sources.
 #. configure local ruleset.
 #. assign ruleset to Suricata services
 #. sync.