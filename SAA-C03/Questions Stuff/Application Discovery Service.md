• Plan migration projects by gathering information about on-premises data centers
- Server utilization data and dependency mapping are important for migrations
- **Agentless Discovery**: 
	- Suited for VMWare hosts.
	- Needs to be deployed on a VM host associated with VMware vCenter;
	- No additional software is required to discover parameters;
	- Agent can collect the required information irrespective of the OS installed on VMs.
- **Agent-based Discovery**:
	- Suitable for collecting data for hosts other than VMware hosts;
	- Agents are deployed on machines having Windows, Linux, Ubuntu, CentOS, SUSE;