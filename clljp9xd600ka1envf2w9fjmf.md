---
title: "Demystifying EKS Authentication and Authorization: A Guide to Strengthening Network Security"
datePublished: Sun Aug 20 2023 16:17:12 GMT+0000 (Coordinated Universal Time)
cuid: clljp9xd600ka1envf2w9fjmf
slug: demystifying-eks-authentication-and-authorization-a-guide-to-strengthening-network-security-1
canonical: https://dev.to/aws-builders/demystifying-eks-authentication-and-authorization-a-guide-to-strengthening-network-security-32eb
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692551181354/9d9d4558-6045-487a-bf4e-fdf48105d919.png
tags: aws, kubernetes, eks

---

Amazon EKS, the managed Kubernetes service by AWS, holds paramount importance in understanding how API server authentication and authorization function. Before delving into the details, let's distinguish between Authentication and Authorization.

Authentication: Ensuring Legitimate Requests
--------------------------------------------

Authentication denotes valid user requests. Kubernetes offers diverse authentication methods, often referred to as "authentication modules" or "authenticators". Every API server request, whether from external sources like `kubectl` or internal entities like the `kubelet` on worker nodes, is authenticated.

Authorization: Granting Action Permissions
------------------------------------------

Once the request's legitimacy is confirmed, it's vital to ensure authorized actions. This is where "authorization" comes into play. Each request carries a specific `Kubernetes action` (e.g., "get pods," "delete deployment"). Given that different cluster users have varying privileges, verifying their permission to execute the action is imperative.

in general Authenticators and authorisers are independent from each other, and they are configured separately. you can read more from [here](https://kubernetes.io/docs/concepts/security/controlling-access/).

EKS Authentication and Authorization: Unveiled
----------------------------------------------

For the creators of the EKS cluster, accessing it using kubectl is straightforward. However, other users, even administrators or root users, face restrictions. The authentication method is EKS-specific, employing AWS Identity and Access Management (IAM) identities. The authentication outcome hinges on IAM permissions.

Authentication alone isn't enough; authorization is essential. EKS employs an RBAC (Role-Based Access Control) authorizer for this. Unlike authentication, authorization is independent of EKS, following standard Kubernetes practices. It's based on Kubernetes users returned by the EKS authenticator. Configuring the RBAC authorizer in an EKS cluster mirrors the process in any Kubernetes environment.

Bridging the Authentication Gap
-------------------------------

Although administrators are authenticated, authorization isn't automatic. Authorization in EKS centers around the aws-auth configmap, housing a mapping of IAM identities to Kubernetes users. As an EKS user, it's your responsibility to craft and maintain this critical object.

IAM User Authorization: A Step-by-Step Guide
--------------------------------------------

1.  AWS utilizes the aws-auth configmap, responsible for mapping IAM identities to Kubernetes users.
    
2.  Though EKS streamlines many tasks, creating the `aws-auth` configmap isn't one. You're accountable for its creation and upkeep.
    
3.  By default, running `kubectl get configmap aws-auth -n kube-system` provides an overview of the existing configuration.
    

The existing configuration might resemble the following:  

    apiVersion: v1
    data:
      mapRoles: |
        - groups:
          - system:bootstrappers
          - system:nodes
          rolearn: arn:aws:iam::xxxxxx:role/eksCreateCluster
          username: system:node:{{EC2PrivateDNSName}}
    kind: ConfigMap
    metadata:
      name: aws-auth
      namespace: kube-system
    

Enter fullscreen mode Exit fullscreen mode

1.  You can add users to this file using `kubectl edit`, linking users with the necessary permissions for the cluster.
    
2.  The `mapUsers` section designates the user's ARN (Amazon Resource Name), username, and group. The group's permissions dictate the allowed actions.
    
3.  In this example, I'm providing the username "clusteradmin" with permissions in the cluster's `system:masters` group:  
    

    apiVersion: v1
    data:
      mapRoles: |
        - groups:
          - system:bootstrappers
          - system:nodes
          rolearn: arn:aws:iam::xxxxx:role/eksCreateCluster20230111
          username: system:node:{{EC2PrivateDNSName}}
      mapUsers: |
        - userarn: arn:aws:iam::xxxx:user/ahmedzidan
          username: ahmedzidan
          groups:
          - system:masters
    kind: ConfigMap
    metadata:
      name: aws-auth
      namespace: kube-system
    

Enter fullscreen mode Exit fullscreen mode

Fine-Tuned Access Control
-------------------------

EKS's power lies in the flexibility it offers. You can tailor access, granting permissions for specific namespaces and actions.

Creating Role-Based Access Control
----------------------------------

1.  Kubernetes RBAC relies on `Role` and `RoleBinding` to set access policies.
2.  A `Role` comprises rules specifying permissible Kubernetes actions.
3.  `RoleBinding` links a role to subjects, such as usernames or groups.

Limiting User Access to Specific Namespace
------------------------------------------

As an illustration, let's limit a user's access to the default namespace:

1.  Begin by downloading the YAML file:

    curl -O https://s3.us-west-2.amazonaws.com/amazon-eks/docs/eks-console-restricted-access.yaml
    

Enter fullscreen mode Exit fullscreen mode

1.  Apply the file. This creates restricted permissions for the default namespace and associates them with the `eks-console-dashboard-restricted-access-group`.
2.  Update the `aws-auth` configmap with the new user and group:

    mapUsers: |
      - userarn: arn:aws:iam::xxxx:user/ahmedzidan
        username: ahmedzidan
        groups:
        - eks-console-dashboard-restricted-access-group
    

Enter fullscreen mode Exit fullscreen mode

In Conclusion
-------------

Understanding EKS authentication and authorization is pivotal for safeguarding applications within a network. Navigating these intricacies fortifies your infrastructure, fostering robustness and resilience.

For more insights, connect with me on:

*   [Linkedin](https://www.linkedin.com/in/ahmedmahmoudzidan/)
*   [Twitter](https://twitter.com/zidanahmed2020)
*   [original-blog](https://www.dailytask.co/task/demystifying-eks-authentication-and-authorization-a-guide-to-strengthening-network-security-1692547549)

Stay tuned for further enlightenment on AWS EKS, networking, and security.