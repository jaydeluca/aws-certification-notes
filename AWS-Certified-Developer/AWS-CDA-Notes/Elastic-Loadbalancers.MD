# Elastic Load Balancers

### Types of Load Balancers
- **Application Load Balancer**
	- Operates at OSI Layer 7 
	- Best suited for load balancing of HTTP and HTTPS traffic. They operate at Layer 7 and are application-aware. They are intelligent, and you can create advanced request routing, sending specific requests to specific web servers

- **Network Load Balancer**
	- Operates at OSI Layer 4
	- best suited for load balancing of TCP traffic where  extreme performance is required. Operating at the connection level (Layer 4) Network Load Balancer are capable of handling millions of requests per second, while maintaining ultra-low latencies.
	
- **Classic Load Balance**
	- are the legacy Elastic Load Balancers. You can balance HTTP/HTTPS applications and use Layer-7-specific features, such as X-Forwarded and sticky sessions. You can also use strict Layer  4 load balancing applications that rely purely on TCP connections.


### Tips:
- 504 error means the gateway has times out. This means that the application not responding within the idle timeout period.
	- Trouble shoot the application. Is it the Web Server or Database Server? 
- If you need the IPv4 address of your end user, look for the X-Forwarded-For header when request comes from your ELB into EC2 instance