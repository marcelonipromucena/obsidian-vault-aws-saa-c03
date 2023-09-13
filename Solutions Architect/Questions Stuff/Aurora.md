#database #aurora 
##### Scenario 01
- Company uses Aurora;
- Entire tech stack is deployed in USA;
- Company has plans to expand to Europe and Asia;
- Needs the **games** table to be accessible globally;
- **But** needs the **users** and **games_played** to be accessible regionally;
- **_Minimal Application Refactoring_**
- Answer:
	- Cannot be Dynamo cuz of "Minimal Application Refactoring";
	- <mark style="background: #BBFABBA6;">Aurora Global Database for GAMES table and Aurora for USERS and GAMES_PLAYED table;</mark>
