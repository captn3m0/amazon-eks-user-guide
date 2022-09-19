# Amazon EKS platform versions<a name="platform-versions"></a>

Amazon EKS platform versions represent the capabilities of the Amazon EKS cluster control plane, such as which Kubernetes API server flags are enabled, as well as the current Kubernetes patch version\. Each Kubernetes minor version has one or more associated Amazon EKS platform versions\. The platform versions for different Kubernetes minor versions are independent\.

When a new Kubernetes minor version is available in Amazon EKS, such as 1\.23, the initial Amazon EKS platform version for that Kubernetes minor version starts at `eks.1`\. However, Amazon EKS releases new platform versions periodically to enable new Kubernetes control plane settings and to provide security fixes\.

When new Amazon EKS platform versions become available for a minor version:
+ The Amazon EKS platform version number is incremented \(`eks.n+1`\)\.
+ Amazon EKS automatically upgrades all existing clusters to the latest Amazon EKS platform version for their corresponding Kubernetes minor version\. Automatic upgrades of existing Amazon EKS platform versions are rolled out incrementally\. The roll\-out process might take some time\. If you need the latest Amazon EKS platform version features immediately, you should create a new Amazon EKS cluster\.

  If your cluster is more than two platform versions behind the current platform version, then it's possible that Amazon EKS wasn't able to automatically update your cluster\. For details of what may cause this, see [Amazon EKS platform version is more than two versions behind the current platform version](troubleshooting.md#troubleshooting-platform-version)\.
+ Amazon EKS might publish a new node AMI with a corresponding patch version\. However, all patch versions are compatible between the EKS control plane and node AMIs for a given Kubernetes minor version\.

 New Amazon EKS platform versions don't introduce breaking changes or cause service interruptions\.

Clusters are always created with the latest available Amazon EKS platform version \(`eks.n`\) for the specified Kubernetes version\. If you update your cluster to a new Kubernetes minor version, your cluster receives the current Amazon EKS platform version for the Kubernetes minor version that you updated to\.

The current and recent Amazon EKS platform versions are described in the following tables\.

## Kubernetes version `1.23`<a name="platform-versions-1.23"></a>

The following admission controllers are enabled for all `1.23` platform versions: `CertificateApproval`, `CertificateSigning`, `CertificateSubjectRestriction`, `DefaultIngressClass`, `DefaultStorageClass`, `DefaultTolerationSeconds`, `ExtendedResourceToleration`, `LimitRanger`, `MutatingAdmissionWebhook`, `NamespaceLifecycle`, `NodeRestriction`, `PersistentVolumeClaimResize`, `Priority`, `PodSecurityPolicy`, `ResourceQuota`, `RuntimeClass`, `ServiceAccount`, `StorageObjectInUseProtection`, `TaintNodesByCondition`, and `ValidatingAdmissionWebhook`\.


|  Kubernetes version  |  Amazon EKS platform version  |  Release notes  |  Release date  | 
| --- | --- | --- | --- | 
|  `1.23.7`  |  `eks.1`  |  Initial release of Kubernetes version `1.23` for Amazon EKS\. For more information, see [Kubernetes 1\.23](kubernetes-versions.md#kubernetes-1.23)\.  | August 11, 2022 | 

## Kubernetes version `1.22`<a name="platform-versions-1.22"></a>

The following admission controllers are enabled for all `1.22` platform versions: `DefaultStorageClass`, `DefaultTolerationSeconds`, `LimitRanger`, `MutatingAdmissionWebhook`, `NamespaceLifecycle`, `NodeRestriction`, `ResourceQuota`, `ServiceAccount`, `ValidatingAdmissionWebhook`, `PodSecurityPolicy`, `TaintNodesByCondition`, `StorageObjectInUseProtection`, `PersistentVolumeClaimResize`, `ExtendedResourceToleration`, `CertificateApproval`, `PodPriority`, `CertificateSigning`, `CertificateSubjectRestriction`, `RuntimeClass`, and `DefaultIngressClass`\.


|  Kubernetes version  |  Amazon EKS platform version  |  Release notes  |  Release date  | 
| --- | --- | --- | --- | 
|  `1.22.10`  |  `eks.5`  |  New platform version with improved `etcd` resiliency\.  | August 15, 2022 | 
|  `1.22.10`  |  `eks.4`  |  New platform version with security fixes and enhancements\. This platform version also introduces a new tagging controller which tags all worker nodes with `aws:eks:cluster-name` to make it easy to allocate cost for these worker nodes\. For more information, see [Tagging your resources for billing](eks-using-tags.md#tag-resources-for-billing)\.  | July 21, 2022 | 
|  `1.22.10`  |  `eks.3`  |  New platform version with security fixes and enhancements\.  | July 7, 2022 | 
|  `1.22.9`  |  `eks.2`  |  New platform version with security fixes and enhancements\.  | May 31, 2022 | 
|  `1.22.6`  |  `eks.1`  | Initial release of Kubernetes version 1\.22 for Amazon EKS\. For more information, see [Kubernetes 1\.22](kubernetes-versions.md#kubernetes-1.22)\. | April 4, 2022 | 

## Kubernetes version `1.21`<a name="platform-versions-1.21"></a>

The following admission controllers are enabled for all `1.21` platform versions: `DefaultStorageClass`, `DefaultTolerationSeconds`, `LimitRanger`, `MutatingAdmissionWebhook`, `NamespaceLifecycle`, `NodeRestriction`, `ResourceQuota`, `ServiceAccount`, `ValidatingAdmissionWebhook`, `PodSecurityPolicy`, `TaintNodesByCondition`, `StorageObjectInUseProtection`, `PersistentVolumeClaimResize`, `ExtendedResourceToleration`, `CertificateApproval`, `PodPriority`, `CertificateSigning`, `CertificateSubjectRestriction`, `RuntimeClass`, and `DefaultIngressClass`\.


|  Kubernetes version  |  Amazon EKS platform version  |  Release notes  |  Release date  | 
| --- | --- | --- | --- | 
|  `1.21.13`  |  `eks.10`  | New platform version with improved etcd resiliency\. | August 15, 2022 | 
|  `1.21.13`  |  `eks.9`  |  New platform version with security fixes and enhancements\. This platform version also introduces a new tagging controller which tags all worker nodes with `aws:eks:cluster-name` to make it easy to allocate cost for these worker nodes\. For more information, see [Tagging your resources for billing](eks-using-tags.md#tag-resources-for-billing)\.  | July 21, 2022 | 
|  `1.21.13`  |  `eks.8`  |  New platform version with security fixes and enhancements\.  | July 7, 2022 | 
|  `1.21.12`  |  `eks.7`  |  New platform version with security fixes and enhancements\.  | May 31, 2022 | 
|  `1.21.9`  |  `eks.6`  |  The AWS Security Token Service endpoint is reverted back to the global endpoint from the previous platform version\. If you want to use the Regional endpoint when using IAM roles for service accounts, then you have to enable it\. For instructions on how to enable the regional endpoint, see [Configuring the AWS Security Token Service endpoint for a service account](configure-sts-endpoint.md)\.  | April 8, 2022 | 
|  `1.21.5`  |  `eks.5`  |  When using [IAM roles for service accounts](iam-roles-for-service-accounts.md), the AWS Security Token Service Regional endpoint is now used by default instead of the global endpoint\. This change is reverted back to the global endpoint in `eks.6` however\. An updated Fargate scheduler provisions nodes at a significantly higher rate during large deployments\.  | March 10, 2022 | 
|  `1.21.5`  |  `eks.4`  | Version 1\.10\.1\-eksbuild\.1 of the Amazon VPC CNI self\-managed and Amazon EKS add\-on is now the default version deployed\. | August 19, 2021 | 
|  `1.21.2`  |  `eks.3`  | New platform version with support for Windows IPv4 address management on the VPC Resource Controller running on the Kubernetes control plane\. Added the Kubernetes filter directive for Fargate Fluent Bit logging\. | August 7, 2021 | 
|  `1.21.2`  |  `eks.2`  |  New platform version with security fixes and enhancements\.  | July 28, 2021 | 
|  `1.21.2`  |  `eks.1`  |  Initial release of Kubernetes version `1.21` for Amazon EKS\. For more information, see [Kubernetes 1\.21](kubernetes-versions.md#kubernetes-1.21)\.  | July 19, 2021 | 

## Kubernetes version `1.20`<a name="platform-versions-1.20"></a>

The following admission controllers are enabled for all `1.20` platform versions: `DefaultStorageClass`, `DefaultTolerationSeconds`, `LimitRanger`, `MutatingAdmissionWebhook`, `NamespaceLifecycle`, `NodeRestriction`, `ResourceQuota`, `ServiceAccount`, `ValidatingAdmissionWebhook`, `PodSecurityPolicy`, `TaintNodesByCondition`, `StorageObjectInUseProtection`, `PersistentVolumeClaimResize`, `ExtendedResourceToleration`, `CertificateApproval`, `PodPriority`, `CertificateSigning`, `CertificateSubjectRestriction`, `RuntimeClass`, and `DefaultIngressClass`\.


|  Kubernetes version  |  Amazon EKS platform version  |  Release notes  |  Release date  | 
| --- | --- | --- | --- | 
|  `1.20.15`  |  `eks.8`  | New platform version with improved etcd resiliency\. | August 15, 2022 | 
|  `1.20.15`  |  `eks.7`  |  New platform version with security fixes and enhancements\. This platform version also introduces a new tagging controller which tags all worker nodes with `aws:eks:cluster-name` to make it easy to allocate cost for these worker nodes\. For more information, see [Tagging your resources for billing](eks-using-tags.md#tag-resources-for-billing)\.  | July 21, 2022 | 
|  `1.20.15`  |  `eks.6`  |  New platform version with security fixes and enhancements\.  | May 31, 2022 | 
|  `1.20.15`  |  `eks.5`  | The AWS Security Token Service endpoint is reverted back to the global endpoint from the previous platform version\. If you want to use the Regional endpoint when using IAM roles for service accounts, then you have to enable it\. For instructions on how to enable the regional endpoint, see [Configuring the AWS Security Token Service endpoint for a service account](configure-sts-endpoint.md)\. | August 7, 20 | 
|  `1.20.11`  |  `eks.4`  |  When using [IAM roles for service accounts](iam-roles-for-service-accounts.md), the AWS Security Token Service Regional endpoint is now used by default instead of the global endpoint\. This change is reverted back to the global endpoint in `eks.5` however\. An updated Fargate scheduler provisions nodes at a significantly higher rate during large deployments\.  | July 7, 2021 | 
|  `1.20.11`  |  `eks.3`  |  New platform version with support for Windows `IPv4` address management on the VPC Resource Controller running on the Kubernetes control plane\. Added the Kubernetes filter directive for Fargate Fluent Bit logging\.  | July 14, 2021  | 
|  `1.20.7`  |  `eks.2`  |  New platform version with security fixes and enhancements\.  | June 6, 2021 | 
|  `1.20.4`  |  `eks.1`  |  Initial release of Kubernetes version `1.20` for Amazon EKS\. For more information, see [Kubernetes 1\.20](kubernetes-versions.md#kubernetes-1.20)\.  | May 18, 2021 | 

## Kubernetes version `1.19`<a name="platform-versions-1.19"></a>

The following admission controllers are enabled for all `1.19` platform versions: `DefaultStorageClass`, `DefaultTolerationSeconds`, `LimitRanger`, `MutatingAdmissionWebhook`, `NamespaceLifecycle`, `NodeRestriction`, `ResourceQuota`, `ServiceAccount`, `ValidatingAdmissionWebhook`, `PodSecurityPolicy`, `TaintNodesByCondition`, `StorageObjectInUseProtection`, `PersistentVolumeClaimResize`, `ExtendedResourceToleration`, `CertificateApproval`, `PodPriority`, `CertificateSigning`, `CertificateSubjectRestriction`, `RuntimeClass`, and `DefaultIngressClass`\.


|  Kubernetes version  |  Amazon EKS platform version  |  Release notes  |  Release date  | 
| --- | --- | --- | --- | 
|  `1.19.16`  |  `eks.11`  |  New platform version with improved `etcd` resiliency\.  | October 27, 2021 | 
|  `1.19.16`  |  `eks.10`  |  New platform version with security fixes and enhancements\.  | September 22, 2021 | 
|  `1.19.16`  |  `eks.9`  | The AWS Security Token Service endpoint is reverted back to the global endpoint from the previous platform version\. If you want to use the Regional endpoint when using IAM roles for service accounts, then you have to enable it\. For instructions on how to enable the regional endpoint, see [Configuring the AWS Security Token Service endpoint for a service account](configure-sts-endpoint.md)\. | August 19, 2021 | 
|  `1.19.15`  |  `eks.8`  |  When using [IAM roles for service accounts](iam-roles-for-service-accounts.md), the AWS Security Token Service Regional endpoint is now used by default instead of the global endpoint\. This change is reverted back to the global endpoint in `eks.9` however\. An updated Fargate scheduler provisions nodes at a significantly higher rate during large deployments\.  | August 8, 2021  | 
|  `1.19.15`  |  `eks.7`  | New platform version with support for Windows IPv4 address management on the VPC Resource Controller running on the Kubernetes control plane\. Added the Kubernetes filter directive for Fargate Fluent Bit logging\. | July 28, 2021 | 
|  `1.19.8`  |  `eks.6`  |  New platform version with security fixes and enhancements\.  | July 14, 2021 | 
|  `1.19.8`  |  `eks.5`  |  New platform version that supports custom security groups with Fargate\.  | June 30, 2021 | 
|  `1.19.8`  |  `eks.4`  |  New platform version with security fixes and enhancements\.  | May 5, 2021 | 
|  `1.19.8`  |  `eks.3`  |  New platform version with security fixes and enhancements\.  | April 15, 2021 | 
|  `1.19.6`  |  `eks.2`  |  New platform version with security fixes and enhancements\.  | March 27, 2021 | 
|  `1.19.6`  |  `eks.1`  |  Initial release of Kubernetes version `1.19` for Amazon EKS\. For more information, see [Kubernetes 1\.19](kubernetes-versions.md#kubernetes-1.19)\.  | February 20, 2021 | 

## Kubernetes version `1.18`<a name="platform-versions-1.18"></a>

The following admission controllers are enabled for all `1.18` platform versions: `DefaultStorageClass`, `DefaultTolerationSeconds`, `LimitRanger`, `MutatingAdmissionWebhook`, `NamespaceLifecycle`, `NodeRestriction`, `ResourceQuota`, `ServiceAccount`, `ValidatingAdmissionWebhook`, `PodSecurityPolicy`, `TaintNodesByCondition`, `StorageObjectInUseProtection`, `PersistentVolumeClaimResize`, `ExtendedResourceToleration`, `CertificateApproval`, `PodPriority`, `CertificateSigning`, `CertificateSubjectRestriction`, `RuntimeClass`, and `DefaultIngressClass`\.


|  Kubernetes version  |  Amazon EKS platform version  |  Release notes  |  Release date  | 
| --- | --- | --- | --- | 
|  `1.18.20`  |  `eks.13`  |  New platform version with improved `etcd` resiliency\.  | December 17, 2021 | 
|  `1.18.20`  |  `eks.12`  |  New platform version with security fixes and enhancements\.  | October 27, 2021 | 
|  `1.18.20`  |  `eks.11`  | The AWS Security Token Service endpoint is reverted back to the global endpoint from the previous platform version\. If you want to use the Regional endpoint when using IAM roles for service accounts, then you have to enable it\. For instructions on how to enable the regional endpoint, see [Configuring the AWS Security Token Service endpoint for a service account](configure-sts-endpoint.md)\. | September 22, 2021 | 
|  `1.18.20`  |  `eks.10`  |  When using [IAM roles for service accounts](iam-roles-for-service-accounts.md), the AWS Security Token Service Regional endpoint is now used by default instead of the global endpoint\. This change is reverted back to the global endpoint in `eks.11` however\. An updated Fargate scheduler provisions nodes at a significantly higher rate during large deployments\.  |  August 19, 2021  | 
|  `1.18.20`  |  `eks.9`  | New platform version with support for Windows IPv4 address management on the VPC Resource Controller running on the Kubernetes control plane\. Added the Kubernetes filter directive for Fargate Fluent Bit logging\. | August 6, 2021 | 
|  `1.18.20`  |  `eks.8`  | New platform version with security fixes and enhancements\. | July 28, 2021 | 
|  `1.18.16`  |  `eks.7`  | New platform version that supports custom security groups with Fargate\. | July 14, 2021 | 
|  `1.18.16`  |  `eks.6`  | New platform version with security fixes and enhancements\. | June 30, 2021 | 
|  `1.18.16`  |  `eks.5`  | New platform version with security fixes and enhancements\. | May 22, 2021 | 
|  `1.18.9`  |  `eks.4`  | New platform version with security fixes and enhancements\. | May 5, 2021 | 
|  `1.18.9`  |  `eks.3`  |  Includes support for [Amazon EKS add\-ons](eks-add-ons.md) and [Fargate logging](fargate-logging.md)\.  | April 15, 2021 | 
|  `1.18.9`  |  `eks.2`  |  New platform version with security fixes and enhancements\.  | March 26, 2021 | 
|  `1.18.8`  |  `eks.1`  |  Initial release of Kubernetes version `1.18` for Amazon EKS\. For more information, see [Kubernetes 1\.18](kubernetes-versions.md#kubernetes-1.18)\.  | December 1, 2020 | 
