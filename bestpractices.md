# Best Practices for Azure Templates
## 1. Naming Conventions for the Templates
   While adding the template name we need to ensure that we are following the best practice like which Cource/lab and other parmeters which is easy to identify the template.
 

   ![](./images/bst1.png)


## 2. CloudLabs Parameter
   CloudLabs parameters can be used while creation of the cloudlabs template, which will helps us to fetch the values from the cloud.
   
below are some of the cloudlabs parameter that can be used.


| **Parameter** | **Remarks** |
| ------------- | ----------- |
| GEN-PASSWORD  | Generates a random password of 12 characters.|
| GEN-UNIQUE    | Generates a GUID of 18 characters starting with 'cs'. |
| GEN-UNIQUE-[Length] | Generates a GUID of [Length] characters starting with 'cs'. |
| GEN-UNIQUE-NUM-[Limit] | Generates a random number with upper limit [Limit]. |
| GEN-SSH-PUB-KEY | Generates SSH Public Key. |
| GEN-GUID | Generates a GUID. |
| GET-ENV-[Length] | Gets Environment variable. |
| CONFIG_STORAGE_ACCOUNT_NAME | Gets Azure Functions storage account name. |
| GET-SERVICEPRINCIPAL-NAME | Gets SP display name. |
| GET-SERVICEPRINCIPAL-SECRET | Gets SP secret key. |
| GET-SERVICEPRINCIPAL-APPLICATION-ID | Gets SP Application Id. |
| GET-SERVICEPRINCIPAL-OBJECT-ID | Gets SP Application Object Id.|
| GET-SERVICEPRINCIPAL-SPOBJECT-ID | Gets SP Object Id.|
| GET-AZUSER-UPN | Gets Azure AD user email. |
| GET-AZUSER-PASSWORD | Gets Azure AD user password. |
| GET-PARAMETER-FILE-BASEURI | Gets Parameter file base URI.
| GET-TEMPLATE-FILE-BASEURI | Gets Template file base URI. |
| GET-AZUSER-OBJECTID | Gets Azure AD user object Id. |
| GET-DEPLOYMENT-ID | Gets CloudLabs deployment Id.
 | GET-TENANT-FQDN | Gets Azure AD domain. |
| GET-LAUNCH-TYPE | Cloud labs deployment type used to tags|
| GET-TEMPLATE-ID | Cloud labs deployment related template Id |
| GET-TENANT-ID | Cloud labs deployment related Tenant Id |
| GET-SERVICEPRINCIPAL-APPLICATION-ID | Gets the AWS Access Key for accessing the AWS Console through CLI (Command Line Interface) |
| GET-SERVICEPRINCIPAL-SECRET | Gets the AWS Secret Key for accessing the AWS Console through CLI (Command Line Interface) |

![](./images/bst2.png)

## 3. How to define the Parmeter and Variables

 **Parmeters**: In the parameters section of the template, you specify which values you can input while deploying the resources.

 ![](./images/bst3.png)

 **Parameter file**: Rather than passing parameters as inline values in your ARM Template, you can use a JSON file that contains the parameter values. The parameter names in the parameter section of your ARM template and Parameter file must match.

 Find the below is an ARM Template sample: https://cloudlabsai.blob.core.windows.net/sample-templates/deploy-arm-01.json



 **Variables** - In the variables section, you construct values that can be used throughout your template. You don't need to define variables, but they often simplify your template by reducing complex expressions.

 ![](./images/bst4.png)

## 4. TEMPLATE PERMISSIONS

1. **Permission/Role Type:** Here we have three types of Permissions –

   * **Azure**:
     * **Azure Built-in Role**: Roles that are available in Azure itself.
     * **Azure Custom Role**: If the Azure built-in roles don't meet the specific needs of your lab, you can create your own custom roles.
     * **Custom ARM Policy**: Here, you can restrict the resources/services by specifying the custom permission URL based on your needs.
   * **AWS**:
     * **IAM Built-in Policy**: It provides an option to attach AWS Managed permissions to the users.
     * **IAM Custom Policy**: If we want to provide restricted access to AWS services to users, then we can select this option.
     * **IAM Instructor Access**: This option can be used to provide access to instructors.
   * **GCP**:
     * **Basic Role**: Basic roles are highly permissive roles that existed prior to the introduction of IAM. You can use basic roles to grant principals broad access to Google Cloud resources.
     * **Custom Role**: If we want to provide restricted access to GCP services to users, then we can select this option.
    
   ***NOTE***: While developing a new lab (dev - phase), you can grant Owner (Azure/GCP) or Administrator access (AWS) for the user, so that there are no conflicts/errors while deploying any kind of resources and once the lab development is completed, you can build custom policies based on the lab requirements so that the users cannot deploy anything besides the lab guide.

2. **Profile Type:**

   * **Attendee**: Select this option if you want to assign permission to a User.
   * **Instructor (Not Applicable for GCP)**: Select this option if you want to assign permission to an Instructor/Mentor/Proctor.
   * **Group Member**: Select this option if you want to assign permission to a user who is an Azure Active Directory Group Member.

## 5. VM CONFIGURATION – ONLY APPLICABLE FOR AZURE:

Under **Add VM Configuration**, add following values:

1. **Name**: In this column, you must enter the exact name of your VM that you supplied in your ARM Template.

2. **Type**: Here you have to choose the Type of your virtual machine. There are two options available - RDP and SSH, so choose one based on the type of your VM.

3. **Server DNS Name**: From your ARM Template, pick up the output parameter that has the VM DNS name stored in it and paste it into this field.
   
4. **Server User Name**: From your ARM Template, pick up the output parameter that has the VM Username stored in it and paste it into this field.

5. **Server Password**: From your ARM Template, pick up the output parameter that has the VM Password stored in it and paste it into this field.
   
6. At last, click on **SUBMIT** to save the configurations.





 


       
