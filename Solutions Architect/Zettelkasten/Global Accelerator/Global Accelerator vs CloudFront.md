
- Both use **AWS Global Network** and its **Edge Locations**
- Both integrate with **AWS Shield**;

## CloudFront
- Improves performance for cacheable content, like images and videos;
- Improves performance for Dynamic Content, such as API acceleration and dynamic site delivery.
- **Content is served at the edge**

## Global Accelerator
- Improves performance for apps over **TPC or UDP**
- Proxy packets at the edge to apps in one or more regions;
- **Good for non-HTTP** use cases such as **Gaming (UDP)**, **IoT(MQTT)** or **Voice over IP (VoIP)** 
- **Good for HTTP** that require **static ip addresses**;
- **Good for HTTP** that require **deterministic, fast regional failover.**;
- 