use Route 53.
1. Create an Alias Record and set **Evaluate Target Health** to **Yes**.
2. Create a Secondary Record and create a **health check**  in Route 53 for web servers in data center.
3. Create **two failover alias records** for each primary and secondary resource.