## What is cloud and why it exists?
We need to a computer to answer request/question 24hr as a server, needs to handle millions times of asking pre hour. 

Of cause, we can use our computer to handle it, but it needs large bandwidth, memory, powerful computing chip, etc...

But what if someone has this large & powerful machine, and we can rent it for a while?

That's call cloud, renting a 'slice' of this machine instead of owning them. 

## How cloud provider lend you a computer?
They will NOT make a single machine for you to connect and run, that's stupidity

They will run a software in large machine, 'slice' it, make it into one fake computer. Each computer has its own memory, storage, OS.

![image](/images/04.jpg)

## How to choose your machine?
Let's take the largest cloud provider AWS as an example (2026), they divide the world as each Region geographically.

One region have multiple data center clusters running called the Available Zone (AZs). For example, `us-east-1` is the region, and `us-east-1a`,`us-east-1c`, those are available Zone. 

## Why using VM?
Since the cloud provider can not actually give you the whole piece of hardware, then it gives you a software-based computers called Virtual Machines (VMs)

A cloud console is a dashboard, which can let you remote control both physical and virtual resources. 

## Why cloud VM only run CLI?
Cloud usually pop you out the `web terminal`, which is the vm terminal, the linux CLI. 

In most case, it only shows command line interface (CLI), it is more efficient, it does not has to download GUI.

## What is SSH?
Secure Shell(SSH), cryptographic network protocol. To secure the connection between your local and remote computer. 

## Why use SSH instead of web terminal?
- Directly edit on web terminal is fraglie to whole vm
- Hard to transfer data to VMs

Nobody use cloud's console's web terminal for daily development. 

## Why SSH connection need port?
Under the law of physics, when you sent signal through internet, it arrives to VM as raw electrical signals.

The physical server has lots of processing running together, the OS uses PORT to sort those signals. (Server is like a residential building, port is like a door number)

Master owner create this hidden doorway outside the server, which is waiting the incoming traffic. 

## Structure of local & VMs & GitHub?
`Local desktop  ──push──►  GitHub  ◄──pull──  Cloud VM`

Inside the VM cli, only use git pull, not git push. 

It's another computer running Linux OS. Also never edit your code directly on VM. 

## What is ECS?
ECS is one of the serval ways to run container on AWS.





