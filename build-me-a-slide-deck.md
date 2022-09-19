# Building a Slide Deck with AI

I love giving talks, but when I need to start a new talk - I will go check on all the plants around the house and then make lunch before starting a new presentation. I am, however, enjoying editing and improving existing slides. This set of prompts automates kickstarting the slide deck for me.

Here I am using 3 steps:
1. Genereate an outline of 10 points to talk about.
2. Put those in a template format, which I'll use as input in the next step.
3. Use the template to generate 3 bullet points for each topic.

All this is done in markdown, and you can use a library like [Go's Present](https://pkg.go.dev/golang.org/x/tools/present) to make your slides.
I am moving these to Google Slides for this specific talk.

The slide are ready to be shown as is, but I personally like adding my own take into the content.
Either way, I would only recommend doing it if you are familiar with the content and are comfortable with this style of Power Point Kareoke. If you don't have the domain expertise - I would recommend stopping after step 1, then proceeding to learning about each topic (and I will make a separate entry on doign this too), and then composing the slides.

## Step 1 - Generate and outline
Prompt: 
```
List a 10 points outline for a talk about security in the cloud.
Exclude introduction to the cloud.
```

Output:
```
1. Defining security in the cloud
2. The shared responsibility model
3. Cloud service providers' security measures
4. Your organization's security measures
5. Securing data in transit
6. Securing data at rest
7. Identity and access management
8. Incident response
9. Compliance
10. Conclusion
```


## Step 2 - Generate templates based on the outline
Prompt: 
``` 
For each line in the Topics List, replace the @@at-quoted expressions@@ in the Template.
Repeat for the entire Topics List.

Topics List:
1. Defining security in the cloud
2. The shared responsibility model
3. Cloud service providers' security measures
4. Your organization's security measures
5. Securing data in transit
6. Securing data at rest
7. Identity and access management
8. Incident response
9. Compliance
10. Conclusion

Template:
# @@dollar-quoted expressions@@
$$give 3 speaker notes bullet points about @@dollar-quoted expressions@@$$

Replaced List:
# Defining security in the cloud
$$give 3 speaker notes bullet points about Defining security in the cloud$$
```

Output:
```
# The shared responsibility model
$$give 3 speaker notes bullet points about The shared responsibility model$$
# Cloud service providers' security measures
$$give 3 speaker notes bullet points about Cloud service providers' security measures$$
# Your organization's security measures
$$give 3 speaker notes bullet points about Your organization's security measures$$
# Securing data in transit
$$give 3 speaker notes bullet points about Securing data in transit$$
# Securing data at rest
$$give 3 speaker notes bullet points about Securing data at rest$$
# Identity and access management
$$give 3 speaker notes bullet points about Identity and access management$$
# Incident response
$$give 3 speaker notes bullet points about Incident response$$
# Compliance
$$give 3 speaker notes bullet points about Compliance$$
# Conclusion
$$give 3 speaker notes bullet points about Conclusion$$
```


## Step 3 - Generate bulletpoints
Prompt: 
```
Replace the @@at-quoted expressions@@ in the following files with the content described.

slides.md
/``` [NP: the slash is me escaping markdown in GitHub]
# Defining security in the cloud
$$give 3 speaker notes bullet points about Defining security in the cloud$$
# The shared responsibility model
$$give 3 speaker notes bullet points about The shared responsibility model$$
# Cloud service providers' security measures
$$give 3 speaker notes bullet points about Cloud service providers' security measures$$
# Your organization's security measures
$$give 3 speaker notes bullet points about Your organization's security measures$$
# Securing data in transit
$$give 3 speaker notes bullet points about Securing data in transit$$
# Securing data at rest
$$give 3 speaker notes bullet points about Securing data at rest$$
# Identity and access management
$$give 3 speaker notes bullet points about Identity and access management$$
# Incident response
$$give 3 speaker notes bullet points about Incident response$$
# Compliance
$$give 3 speaker notes bullet points about Compliance$$
# Conclusion
$$give 3 speaker notes bullet points about Conclusion$$
/``` [NP: the slash is me escaping markdown in GitHub]
```

Output:
```
slides.md
/``` [NP: the slash is me escaping markdown in GitHub]
# Defining security in the cloud
- Defining security in the cloud is the process of protecting data and resources in the cloud from unauthorized access and data breaches. 
- Security in the cloud is a shared responsibility between the cloud service provider and the customer. 
- Cloud service providers are responsible for securing the infrastructure and providing security features and tools, while customers are responsible for securing their data and applications.

# The shared responsibility model
- The shared responsibility model is a security model that defines the roles and responsibilities of the cloud service provider and the customer in securing data and resources in the cloud. 
- Under the shared responsibility model, the cloud service provider is responsible for securing the infrastructure and providing security features and tools, while the customer is responsible for securing their data and applications. 
- This model provides a clear division of responsibility between the two parties and helps ensure that data and resources are properly secured.

# Cloud service providers' security measures
- Cloud service providers use a variety of security measures to protect data and resources in the cloud from unauthorized access and data breaches. 
- These security measures include physical security, logical security, and data security. 
- Physical security measures protect the physical infrastructure from unauthorized access, while logical security measures protect the data and resources from unauthorized access. 
- Data security measures protect the data from unauthorized access and data breaches.

# Your organization's security measures
- Organizations must take measures to protect their data and resources in the cloud from unauthorized access and data breaches. 
- These security measures include encrypting data at rest, encrypting data in transit, and implementing identity and access management. 
- Encrypting data at rest helps protect data from unauthorized access, while encrypting data in transit helps protect data from data breaches. 
- Implementing identity and access management helps ensure that only authorized users have access to data and resources.

# Securing data in transit
- Data in transit is data that is being transmitted from one location to another. 
- Data in transit is vulnerable to interception and data breaches. 
- To protect data in transit, organizations should encrypt data using SSL/TLS. 
- SSL/TLS is a protocol that encrypts data before it is transmitted, making it difficult for attackers to intercept and read the data.

# Securing data at rest
- Data at rest is data that is stored on a physical device, such as a hard drive or a server. 
- Data at rest is vulnerable to unauthorized access and data breaches. 
- To protect data at rest, organizations should encrypt data using AES. 
- AES is a standard that encrypts data using a key, making it difficult for attackers to access and read the data.

# Identity and access management
- Identity and access management is a security process that helps ensure that only authorized users have access to data and resources. 
- Identity and access management includes authenticating users, authorizing access, and auditing user activity. 
- Authenticating users ensures that only authorized users can access data and resources. 
- Authorizing access ensures that users can only access the data and resources that they are authorized to access. 
- Auditing user activity helps organizations track and monitor user activity to ensure that only authorized actions are being performed.

# Incident response
- Incident response is the process of handling and managing security incidents. 
- Incident response includes identifying, containment, eradication, and recovery. 
- Identifying helps organizations identify security incidents. 
- Containment helps organizations contain and control security incidents. 
- Eradication helps organizations remove and eliminate security incidents. 
- Recovery helps organizations restore and recover from security incidents.

# Compliance
- Compliance is the process of ensuring that an organization meets all the regulatory requirements for data security. 
- Compliance includes identifying, assessing, and remediation. 
- Identifying helps organizations identify all the regulatory requirements for data security. 
- Assessing helps organizations assess their compliance with all the regulatory requirements for data security. 
- Remediation helps organizations remediate any compliance issues that are identified.

# Conclusion
- Security in the cloud is a shared responsibility between the cloud service provider and the customer. 
- Cloud service providers are responsible for securing the infrastructure and providing security features and tools, while customers are responsible for securing their data and applications. 
- Organizations must take measures to protect their data and resources in the cloud from unauthorized access and data breaches. 
- These security measures include encrypting data at rest, encrypting data in transit, and implementing identity and access management.
```
