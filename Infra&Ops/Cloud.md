## What is cloud and why it exists?
We need to a computer to answer request/question 24hr as a server, needs to handle millions times of asking pre hour. 

Of cause, we can use our computer to handle it, but it needs large bandwidth, memory, powerful computing chip, etc...

But what if someone has this large & powerful machine, and we can rent it for a while?

That's call cloud, renting a 'slice' of this machine instead of owning them. 

## How cloud provider lend you a computer?
They will NOT make a single machine for you to connect and run, that's stupidity

They will run a software in large machine, 'slice' it, make it into one fake computer. Each computer has its own memory, storage, OS.

![image](/images/04.jpg)

## What is ICP?
Internet Content Provider. It's a regulatory permit unique to mainland China. 

It is asking you 

`Does physcial cloud provider has legal permit to provide cloud service to the public?`

## Internet & Location & Regulation
Company go for Domain Registrar, to claim '*I'm the person who own this name (google.com*). Domain registrar is doing the job to manage the registration of domain name, it will claim it globally. Then goes to DNS server (*'if you want to know the IP, go ask Cloudflare*).

When you browser is typing into a domain (like google.com), meanwhile, your computer is a device only sending electrical signal by optical fiber, it needs one thing called IP address(106.54....) to know which server you ask for data. 

Some companies offer service to translate the domain name into IP address, it called DNS service, suck company like Cloudflare. 

The server you ask data for is actually a massive computer running 24hrs, it needs to have a physical space which's called data center. In China, there's ICP filing, to regulate whether the server is allowed to serve website to public. If the ICP filing is checked, meaning the physical location of the server is legal to serve you with a business license. 

As long as your device send the request signal to server, your message will go across all the internet, bypass someone's computer as well. You have to encrypt the connection otherwise anyone on the public internet knows what's inside in your request. The SSL/TLS certificate is doing encryption  and identity to solves those two problems. 

![images](/images/08.png)

The application will ask data from server by dialing the domain name, not by ip address. The ip and port is resolved underneath. 

## Domain name & Safety
Once you bought a name from domain registrar, you own the entire namespace beneath it. You can have a.c.v at front / back if you want. 

Also you control the DNS, which domain name can points to our VM ip. 

The last guard is the nginx, if you are not the domain name in certificate card, then you are in the wrong place. 

## The AWS setup
Let's take the largest cloud provider AWS as an example (2026), they divide the world as each Region geographically.

One region have multiple data center clusters running called the Available Zone (AZs). For example, `us-east-1` is the region, and `us-east-1a`,`us-east-1c`, those are available Zone. 

In most dev team, to choose which region as their cloud computer are:
- legal. Need to follow local data law
- Hardware availability. The physical hardware
- The cost. Whether it's expensive or cheap
- Distance. Latency, take too long to respond. 

## Linux on Cloud
It's stable, open source, free to use, it can run non-stop for 24hrs. It accounts for 90% of global cloud workloads. 

Most of debugging on cloud vm is through command line terminal by SSH connection. It's waste of CPU and memory to use graphic interface (Also more difficult). 

*Each cloud provider has its own doc to teach you how to config on cloud*. 

`bin` holds every command you type in, like `ls`, `cd`. 

`etc` holds all the configuration of how system is being setup. 

There are lots of commands 

For most of developer, they DO NOT write on the config file, those are Operating System Territory. You can read them, but do not write on it. 

The primary workspace is /home/developer

There's a abstraction and categorical name called `hypervisor`, which means the whole section to run virtual machine. It's a VM monitor. 




## What is SSH?
Secure Shell (SSH), cryptographic network protocol. To secure the connection between your local and remote computer. 

## Why use SSH instead of web terminal?
- Directly edit on web terminal is fraglie to whole vm
- Hard to transfer data to VMs

*Nobody use cloud's console's web terminal for daily development*

## IP in VM
`0.0.0.0` means it listens on every network interface, reachable from anywhere

`127.0.0.1` means it only can be reachable from inside this machine. 

`172.16.0.0/12`  is a UFW firewall rule — it only restricts which source addresses are allowed to connect to those ports (the docker bridge network range).

## The enterprise cloud architecture?
The modern enterprise design architecture differently. 

They will use a lightweight agent to run inside the cloud, and establish a outbound connection to secure gateway. 

![image](/images/05.png)

The cloud firewall will block 100% of all inbound traffic. 

## Why SSH connection need port?
Under the law of physics, when you sent signal through internet, it arrives to VM as raw electrical signals.

The physical server has lots of processing running together, the OS uses PORT to sort those signals. (Server is like a residential building, port is like a door number)

Master owner create this hidden doorway outside the server, which is waiting the incoming traffic. 

## The port 80
It's the default setting by tech convention. Because when user type google.com on browser, it doesn't type `HTTP` or `HTTPS`, so browser doesn't know whether it is secured connection or not. 

So by default, it will reach to port 80 at the first place. And nginx will 

## Structure of local & VMs & GitHub?
`Local desktop  ──push──►  GitHub  ◄──pull──  Cloud VM`

Inside the VM cli, only use git pull, not git push. 

It's another computer running Linux OS. Also never edit your code directly on VM. 

## Gated Pattern
It's a patter designed to set the security to handle incoming traffic.

e.g Two-GATED model

`Internet → [Gate 1: Cloud console firewall] → [Gate 2: ufw on the VM] → service`


## Reverse Proxy / Edge Servers
It's a tool to handle the incoming client request, then route them to backend application server

Most used tool is AWS Elastic Load Balancing (ELB/ALB), accounts for 60-70% of market shares.

## Nginx & Certbot in SSL/TLS
Nginx is the host which is like a safeguard secure your front door. 

When the URL asking sent to VM, the nginx will differentiate whether it can pass. Because the internet connection need SSL/TLS security handshake, the certbot is a tool to provide certificate files to nginx.

Certbot only run once and never show up again. The VM will show the certificate to the Visitor (request), the visitor will look at the certificate, *is it the name i dial is on this card?* If yes, the secure channel open. 

Image the request or call is a person who's urge to find the office in the city, it knows the location of the building, but doesn't know which floor it needs to go. So it sees the info card provide by security guard. 

## How to decide whether you need docker?
It depends on the requirements. 

- What are our deployment and reproducibility requirement?

docker is worth it when your software is long and fragile. 

If you application is a ready-used package, you don't need docker to do this. 

## How to decide automation patter by using GitHub (CI/CD)?
You push to git, then the robot/github action build and deploy automatically. The server is one-time setup. 

Most dev team does that way, the git push triggers an automation pipeline. 

For example, when github action being triggered by `push main`, then it build the JAR file, and push to cloud VM.

Now, old JAR will disable, then new JAR will continue sit on given port (PORT 3000), to listen new request.

## How to deploy (CI/CD)?
Most professional teams insert one extra step: the pipeline packages the JAR into a container image, pushes that image to a registry, and deploys it onto a container platform — Kubernetes, ECS, or Cloud Run. 

So for most teams the flow is: push → CI builds → builds a container image → deploys the image to a container platform → live.

## What is containerization?
It's `OS level virtualization`. It's a practice to bundling an application all together. 

![image](/images/07.png)

## What is Docker?
It's a suite of software products, created by a company called Docker. Inc. It's the first tool to make containerization accessible, people somehow say it 'dockerize'.

## Problems Docker can solve?
To maintain the prefect environmental synchronization. For example, if your VM installed package version is 1.5, but your local is version 1.2, then the application will crash

Docker is built for standardize the environment. It is an open-source platform for you to deliver (`build, test, ship, run`) software quickly. Which allows you to run your application on the single, sealed packaged called a `container`. 

## What is ECS?
ECS (Amazon Elastic Container Service) is one of the serval ways to run container on AWS.

## Standards connection between mobile and cloud?
The working relationship will be `Client-Server model`

They need to share the same language of communication, which is API. 

The data is packaged into a lightweight format, the common one is JSON (JavaScript Object Notation). It's like a physical letter is delivered by postman. 

## What's TCP connection?
It's a logical solution to handle physical hardware. 

Electrons travels through copper wires, or another way is photons being shooted through fiber optic cables.

## What's ip address and port?
IP address is like the address on internet. Cloud is just a large-sliced computer, it has its onw ip address. 

The port is like door, a virtual connection point. It's like a multiple gate on a large, massive building. 

It's regulated by building owner, decide who can come in or who's not. 

## How software being deployed on cloud?
In old way, you drop a single software on cloud, which's a large-sliced computer, the problem arises when lack of correct version of all kinds of library. 

In modern solution, engineer bundles all the libraries, extern files all in one single package. Make use execute accurately.

That's why you see not more then JAR file, other different files are being sent to cloud by a single package. 

## How to setup safeguard when someone access to your vm port?
- `The public can not find that 'door'.` For example, like most cloud provider, they use built-in network firewalls. Sit outside the VM and block unauthorized traffic. TO restrict the port access.
- `Since signal arrived, prove has right to enter.` For example, use password or cryptographic keys (like SSH).
-  `Monitoring who knocks the door.` For example to use a software called Fail2Ban, it monitors the server's entry log. 
-  `Move the door.` To avoid using common port on internet.

## Why many server use port 22?
It's a global standard for SSH. There is historical reason back to 1995 for secure reason to set port 22, therefore, the global convention is born.

Most server is Linux based, and SSH is defaults to port 22.

If you set your server out of port 22, then it can avoid internet noise. Many hacker random try to access port 22, cause they know it's convention. 

## What if public direct access to cloud?
- No TLS. It's transport layer security, a cryptographic protocol designed to provide private communication. Between local and cloud, they do the math to agree on secret language to protect the tunnel where data is travels
- No Rate Limiting. You can let stranger to access 1000 times pre mins. 

## What is JWT?
JSON Web Token. It's an unforgettable card. 

The internet is series of physical cables and routers owned by strangers. JWT is like a VIP wristband, to have the authority to access this place 

To use JWT without TLS, it's dangerous. 

## What is Nginx?
A lightweight to protect the connection between local and cloud. 

The application inside cloud is using 'loopback' address (127.0.0.1:3000), it can only be accessed request inside the cloud. 

Nginx put the public traffic into TLS first, a safe communicate tunnel. Also enforces rate limits, once verifies it's safe, then knocks the door 127.0.0.1:3000.

## why we need domain name instead of public ip?
- For convenience. When you access Google, instead of 198.XXX.XXX.XXX
- Stamp of trust. it's identity, not location. Even under laws of physics, it's actually an ip address. 

## How to evaluate container implementation?
The Docker container is to set up an isolated wrapper around one or more program. So it really depends on the consistency of env variable.

For example, if one program needs specific packages, then put it into single container. 