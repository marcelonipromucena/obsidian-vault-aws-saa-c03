##### Scenario 01
- Company wants to delegate access to set of users from development environment so they can access some resources in production env;
- **Production environment is managed under another account**;
- Answers:
	- <mark class="hltr-green">1. Create a new IAM role with the required permissions to access the resources in the production env;</mark>
	- <mark class="hltr-green">2. Users can then assume this IAM role while accessing the resources from the production env;</mark>

