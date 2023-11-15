- Site-to-Site VPN ECMP (equal-cost multi-path routing);
- Allow **forward a packet over multiple best path**
- **Use case:** multiple Site-to-Site VPN connections to increase bandwidth of your connection to AWS.

**VPN** **to** **Virtual Private Gateway**

1x VPN = 1x VPC
1x VPN = 1.25Gbps
2 Tunnels

**VPN to Transit Gateway**

1x VPN = 1x Transit Gateway = xN VPCs
1x VPN = 2.5Gbps (ECMP) - 2 tunnels used
2x VPN = 5Gbps (ECMP)
3x VPN = 7.5Gbps (ECMP)

**It is costlier**: More $ per GB of TGW processed data.

