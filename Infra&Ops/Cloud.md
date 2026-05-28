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

## What is ECS?
ECS is one of the serval ways to run container on AWS.

