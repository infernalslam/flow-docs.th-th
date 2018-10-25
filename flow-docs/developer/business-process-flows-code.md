---
title: ทำงานกับโฟลว์กระบวนการทางธุรกิจโดยใช้โค้ด | MicrosoftDocs
description: เรียนรู้วิธีเขียนโปรแกรมด้วยโฟลว์กระบวนการทางธุรกิจเพื่อสร้างกระบวนการทางธุรกิจที่มีประสิทธิภาพและคล่องตัวมากขึ้น
ms.custom: ''
ms.date: 07/09/2018
ms.reviewer: ''
ms.service: flow
ms.topic: article
ms.assetid: 67d8cf80-9f77-4804-97a1-cf9f61417e83
author: msftman
ms.author: deonhe
manager: kvivek
search.app:
- Flow
search.audienceType:
- developer
ms.openlocfilehash: ae3633047bda556058c8e2ec94e6411e7f277e76
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: th-TH
ms.lasthandoff: 09/12/2018
ms.locfileid: "44691077"
---
# <a name="work-with-business-process-flows-using-code"></a>ทำงานกับโฟลว์กระบวนการทางธุรกิจโดยใช้โค้ด

*โฟลว์กระบวนการทางธุรกิจ*ช่วยให้คุณสร้างกระบวนการขาย การบริการ และกระบวนการทางธุรกิจอื่น ๆ ที่มีประสิทธิภาพและคล่องตัวมากขึ้น โดยจะสร้างการแสดงภาพของกระบวนการทางธุรกิจของคุณโดยการใส่ตัวควบคุมพิเศษที่ด้านบนของฟอร์มเอนทิตี ผู้ใช้จะได้รับคำแนะนำผ่านขั้นตอนต่าง ๆ ของการขาย การตลาด หรือกระบวนการบริการจนเสร็จสมบูรณ์ แต่ละกระบวนการจะสนับสนุนลำดับขั้นและขั้นตอนต่าง ๆ หลายขั้น คุณสามารถเพิ่มหรือลบขั้นตอนออก รวมถึงเปลี่ยนลำดับขั้น หรือเพิ่มเอนทิตีใหม่ไปยังโฟลว์กระบวนการทางธุรกิจ  
  
อินสแตนซ์โฟลว์กระบวนการทางธุรกิจที่แตกต่างกันสามารถเรียกใช้พร้อมกันกับเรกคอร์ดเอนทิตีเดียวกันได้ ผู้ใช้สามารถสลับไปมาระหว่างอินสแตนซ์กระบวนการทางธุรกิจที่เกิดขึ้นพร้อมกัน และดำเนินงานในลำดับขั้นปัจจุบันในกระบวนการต่อได้ 

หัวข้อนี้จะมีข้อมูลเกี่ยวกับวิธีที่คุณสามารถเขียนโปรแกรมด้วยโฟลว์กระบวนการทางธุรกิจ

> [!NOTE]
> คุณไม่จำเป็นต้องเขียนโค้ดเพื่อทำงานกับโฟลว์กระบวนการทางธุรกิจ สำหรับข้อมูลเกี่ยวกับการใช้ UI เพื่อสร้างและจัดการโฟลว์กระบวนการทางธุรกิจ โปรดดู[ภาพรวมโฟลว์กระบวนการทางธุรกิจ](../business-process-flows-overview.md)  

<a name="PrereqsBPF"></a>   
## <a name="prerequisites-for-business-process-flow"></a>ข้อกำหนดเบื้องต้นสำหรับโฟลว์กระบวนการทางธุรกิจ 

เอนทิตีแบบกำหนดเองและเอนทิตีที่มีฟอร์ม UI ที่อัปเดตสามารถเข้าร่วมในโฟลว์กระบวนการทางธุรกิจได้ เอนทิตี UI ที่อัปเดตมีคุณสมบัติ <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsAIRUpdated> ที่ตั้งค่าเป็น `true` 

เมื่อต้องการเปิดใช้งานเอนทิตีสำหรับโฟลว์กระบวนการทางธุรกิจ ให้ตั้งค่าคุณสมบัติ <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsBusinessProcessEnabled> เป็น `true`

> [!IMPORTANT]
>  การเปิดใช้งานเอนทิตีสำหรับโฟลว์กระบวนการทางธุรกิจเป็นกระบวนการเดียว คุณไม่สามารถย้อนกลับได้

   
<a name="DefineBPF"></a>   
## <a name="define-business-process-flow"></a>กำหนดโฟลว์กระบวนการธุรกิจ
  
ใช้ตัวออกแบบโฟลว์กระบวนการทางธุรกิจตามที่เห็นเพื่อกำหนดโฟลว์กระบวนการทางธุรกิจ ข้อมูลเพิ่มเติม:[สร้างโฟลว์กระบวนการทางธุรกิจ](../create-business-process-flow.md)

ตามค่าเริ่มต้น เรกคอร์ดโฟลว์กระบวนการทางธุรกิจจะสร้างขึ้นในสถานะ `Draft`  

ข้อกำหนดของโฟลว์กระบวนการทางธุรกิจจะถูกเก็บไว้ในเอนทิตี <xref:Microsoft.Dynamics.CRM.workflow> และข้อมูลลำดับขั้นสำหรับโฟลว์กระบวนการทางธุรกิจจะถูกเก็บไว้ในเอนทิตี <xref:Microsoft.Dynamics.CRM.processstage>
  
<a name="ActivateBPF"></a>   
## <a name="activate-business-process-flow"></a>เปิดใช้งานโฟลว์กระบวนการธุรกิจ  
 คุณต้องเปิดใช้งานก่อนจึงจะสามารถใช้โฟลว์กระบวนการได้ เมื่อต้องการเปิดใช้งาน คุณต้องมีสิทธิ์การใช้งาน `prvActivateBusinessProcessFlow` สำหรับเอนทิตี `Workflow` ใช้ข้อความ <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> เพื่อตั้งค่าสถานะของเรกคอร์ดเอนทิตี `Workflow` เป็น `Activated` ข้อมูลเพิ่มเติม:[การดำเนินการแบบพิเศษที่ใช้การอัปเดต](/dynamics365/customer-engagement/developer/org-service/perform-specialized-operations-using-update) 

 > [!NOTE]
 > คุณยังสามารถใช้ตัวออกแบบโฟลว์กระบวนการทางธุรกิจเพื่อเปิดใช้งานโฟลว์กระบวนการทางธุรกิจได้อีกด้วย 

<a name="BPFEntity"></a>   
## <a name="business-process-flow-entity"></a>เอนทีตีโฟลว์กระบวนการธุรกิจ 
 เมื่อคุณเปิดใช้งานข้อกำหนดโฟลว์กระบวนการทางธุรกิจโดยการเปลี่ยนสถานะของเรกคอร์ดเอนทิตี `Workflow` ที่สอดคล้องกันหรือโดยการใช้ตัวออกแบบโฟลว์กระบวนการทางธุรกิจ เอนทิตีแบบกำหนดเองที่มีชื่อต่อไปนี้จะถูกสร้างขึ้นโดยอัตโนมัติเพื่อจัดเก็บอินสแตนซ์โฟลว์กระบวนการทางธุรกิจที่เปิดใช้งาน: "*\<activesolutionprefix>*_*\<uniquename>*" โดยที่ uniquename จะได้มาจากชื่อที่คุณระบุ  
  
 ตัวอย่างเช่น ถ้าคุณระบุ "My Custom BPF" เป็นชื่อของข้อกำหนดโฟลว์กระบวนการทางธุรกิจ และกำลังใช้ผู้เผยแพร่เริ่มต้น (ใหม่) สำหรับโซลูชันที่ใช้งานของคุณ ชื่อของเอนทิตีแบบกำหนดเองที่สร้างขึ้นสำหรับการจัดเก็บอินสแตนซ์กระบวนการจะเป็น "new_mycustombpf"  
  
 ถ้าไม่มีการระบุค่า `uniquename` สำหรับข้อกำหนดโฟลว์กระบวนการธุรกิจ ตัวอย่างเช่น ถ้ามีการนำเข้าโฟลว์กระบวนการทางธุรกิจมาเป็นส่วนหนึ่งของโซลูชันจากเวอร์ชันก่อนหน้า ชื่อเริ่มต้นของเอนทิตีแบบกำหนดเองจะเป็น "*\<activesolutionprefix>*\_bpf\_*<GUID_BPF_Definition>*:  
  
> [!IMPORTANT]
>  เรกคอร์ดตัวอย่างของโฟลว์กระบวนการทางธุรกิจใช้เอนทิตีของระบบเพื่อจัดเก็บเรกคอร์ดของอินสแตนซ์โฟลว์กระบวนการธุรกิจที่สอดคล้องกัน  
>   
>  อย่างไรก็ตาม ข้อกำหนดใด ๆ ของโฟลว์กระบวนการธุรกิจที่คุณสร้างจะใช้เอนทิตีแบบกำหนดเองเพื่อจัดเก็บเรกคอร์ดของอินสแตนซ์ตามที่อธิบายไว้ก่อนหน้านี้ 

คุณสามารถเรียกดูชื่อเอนทิตีโฟลว์กระบวนการทางธุรกิจของคุณโดยใช้วิธีต่อไปนี้:

- **ใช้ UI**: ใช้ UI แบบกำหนดเองเพื่อเรียกดูเอนทิตีโฟลว์กระบวนการทางธุรกิจของคุณ:

    ![](media/bpf-entity-name.png)
- **ใช้ API ของเว็บ**: ใช้คำขอต่อไปนี้:

    **คำขอ**

    ```
    GET [Organization URI]/api/data/v9.0/workflows?$filter=name eq 'My Custom BPF'&$select=uniquename HTTP/1.1
    ```

    **การตอบกลับ**
    ```
    {  
    "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#workflows(uniquename)",
    "value":[  
         {  
             "@odata.etag":"W/\"1084677\"",
             "uniquename":"new_mycustombpf",
             "workflowid":"2669927e-8ad6-4f95-8a9a-f1008af6956f"
         }
      ]
    }

- **Using the Organization service**: Use the following code sample:

    ```c#
    QueryExpression query = new QueryExpression
    {
        EntityName = "workflow",
        ColumnSet = new ColumnSet("uniquename"),
        Criteria = new FilterExpression
        {
            Conditions =
            {
                new ConditionExpression
                {
                    AttributeName = "name",
                    Operator = ConditionOperator.Equal,
                    Values = { "My Custom BPF" }
                }
            }
        }
    };
    Workflow Bpf = (Workflow)_serviceProxy.RetrieveMultiple(query).Entities[0]; 

> [!NOTE]
> The <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsBPFEntity> property is `true` for business process flow entities. You can retrieve all the business process flow entities in your instance by running the following Web API request:
> ```http
> GET [Organization URI]/api/data/v9.0/EntityDefinitions?$select=SchemaName,LogicalName,DisplayName&$filter=IsBPFEntity eq true HTTP/1.1
> ```

<a name="BPFSecurity"></a>   
## Manage security for business process flows

The custom entity that is automatically created on activating a business process flow to store business process flow instances adheres to the standard security model as for any other custom entity in Customer Engagement. This implies that privileges granted on these entities define the runtime permissions for users for business process flows.

The custom business process flow entity has organization scope. The regular create, retrieve, update and delete privileges on this entity define the permission the user would have based on his/her assigned roles. By default, when the business process flow custom entity is created, only **System Administrator** and **System Customizer** security roles are granted access to it, and you must explicitly grant permissions to the new business process flow entity (for example, **My Custom BPF**) for other security roles as required.

![](media/bpf-privileges.png)

<a name="ManageBPF"></a>   
## Create, retrieve, update, and delete business process flow entity records (process instances)  
 The custom entity that is automatically created on activating a business process flow definition stores all the process instances for the business process flow definition. The custom entity supports the standard programmatic creation and management of records (process instances) using Web API and CRM 2011 endpoint.

> [!IMPORTANT]
> Switching to another process instance for an entity record is only supported through UI (client) or programmatically using information available in this section. You can no longer use the `SetProcess` message (<xref href="Microsoft.Dynamics.CRM.SetProcess?text=SetProcess Action" /> or <xref:Microsoft.Crm.Sdk.Messages.SetProcessRequest>) to programmatically switch processes (set another business process flow as the active process instance) for the target entity record. 

 Lets consider the following example where we have a cross-entity business process flow, "My Custom BPF," with 3 stages: S1:Account, S2:Account, and S3:Contact. 

 ![](media/sample-bpf.png)
 
### Retrieve all the records (instances) for a business process flow entity
 If the name of your business process flow entity is "new_mycustombpf", use the following query to retrieve all the records (process instances) for your business process flow entity:  
  
```http
GET [Organization URI]/api/data/v9.0/new_mycustombpfs HTTP/1.1 
```

ในตอนนี้ คุณอาจไม่ได้รับอินสแตนซ์ในการตอบกลับเนื่องจากยังไม่มี เรียกใช้คำขอนี้หลังจากสร้างอินสแตนซ์ของข้อกำหนดโฟลว์กระบวนการทางธุรกิจของคุณภายหลังในหัวข้อนี้

> [!NOTE]
> เมื่อต้องทราบวิธีการเรียกใช้ชื่อของเอนทิตีโฟลว์กระบวนการทางธุรกิจของคุณ โปรดดูส่วน [เอนทิตีโฟลว์กระบวนการธุรกิจ](#business-process-flow-entity) ที่อยู่ก่อนหน้า
  
### <a name="create-a-business-process-flow-entity-record-process-instance"></a>สร้างเรกคอร์ดเอนทิตีโฟลว์กระบวนการธุรกิจ (อินสแตนซ์ของกระบวนการ) 

สร้างเรกคอร์ดเอนทิตีโฟลว์กระบวนการธุรกิจ (อินสแตนซ์ของกระบวนการ) โดยทางโปรแกรมหากคุณต้องการสลับไปยังโฟลว์กระบวนการทางธุรกิจอื่นสำหรับเรกคอร์ดเอนทิตีโดยไม่ใช้ UI 

เพื่อสร้างเรกคอร์ดเอนทิตีโฟลว์กระบวนการธุรกิจ คุณจำเป็นต้องระบุค่าต่อไปนี้: 
- เชื่อมโยงเรกคอร์ดเอนทิตีโฟลว์กระบวนการธุรกิจกับเรกคอร์ดเอนทิตีหลัก โดยการตั้งค่าคุณสมบัติการนำทางแบบเดี่ยวโดยใช้คำอธิบายประกอบ `@odata.bind` เมื่อต้องการดูชื่อคุณสมบัติการนำทางที่ชี้ไปยังเรกคอร์ดเอนทิตีหลักสำหรับข้อกำหนดโฟลว์กระบวนการทางธุรกิจของคุณ ให้ใช้[เอกสาร CSDL $metadata](/dynamics365/customer-engagement/developer/webapi/web-api-types-operations.md#csdl-metadata-document) 
- เชื่อมโยงเรกคอร์ดเอนทิตีโฟลว์กระบวนการธุรกิจกับลำดับขั้นที่ถูกต้องที่ระบุไว้ในข้อกำหนดโฟลว์กระบวนการธุรกิจ โดยการตั้งค่าคุณสมบัติการนำทางแบบเดี่ยวโดยใช้`@odata.bind`คำอธิบายประกอบ เมื่อต้องการดูชื่อคุณสมบัติการนำทาง (โดยปกติ `activestageid`) ที่ชี้ไปยังเรกคอร์ดของลำดับขั้นสำหรับข้อกำหนดโฟลว์กระบวนการทางธุรกิจของคุณ ให้ใช้[เอกสาร CSDL $metadata](/dynamics365/customer-engagement/developer/webapi/web-api-types-operations.md#csdl-metadata-document)

    นอกจากนี้ คุณสามารถเรียกดูข้อมูลเกี่ยวกับลำดับขั้นทั้งหมดสำหรับข้อกำหนดโฟลว์กระบวนการทางธุรกิจได้โดยใช้คำขอ API ของเว็บต่อไปนี้ โดยสมมติว่า ID ของข้อกำหนดโฟลว์กระบวนการทางธุรกิจของคุณคือ 2669927e-8ad6-4f95-8a9a-f1008af6956f:

    **คำขอ**

    ```http
    GET [Organization URI]/api/data/v9.0/processstages?$select=stagename&$filter=processid/workflowid eq 2669927e-8ad6-4f95-8a9a-f1008af6956f HTTP/1.1
    ```

    **การตอบกลับ**

    ```http
    {
        "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#processstages(stagename)",
        "value": [
            {
                "@odata.etag": "W/\"858240\"",
                "stagename": "S1",
                "processstageid": "9a9185f5-b75b-4bbb-9c2b-a6626683b99b"
            },
            {
                "@odata.etag": "W/\"858239\"",
                "stagename": "S3",
                "processstageid": "a107e2fd-7543-4c1a-b6b4-b8060ecb1a1a"
            },
            {
                "@odata.etag": "W/\"858238\"",
                "stagename": "S2",
                "processstageid": "19a11fc0-3398-4214-8522-cb2a97f66e4b"
            }
        ]
    }
    ```

ต่อไป ให้ใช้คำขอต่อไปนี้เพื่อสร้างอินสแตนซ์ของข้อกำหนดโฟลว์กระบวนการทางธุรกิจสำหรับเรกคอร์ดบัญชีผู้ใช้ (ID=a176be9e-9a68-e711-80e7-00155d41e206) และกำหนดลำดับขั้นที่ใช้งานอยู่เป็นลำดับขั้นแรก S1 ของอินสแตนซ์ของกระบวนการ (ID=9a9185f5-b75b-4bbb-9c2b-a6626683b99b):

**คำขอ**

```http
POST [Organization URI]/api/data/v9.0/new_mycustombpfs HTTP/1.1 
Content-Type: application/json; charset=utf-8 
OData-MaxVersion: 4.0 
OData-Version: 4.0 
Accept: application/json 

{
    "bpf_accountid@odata.bind": "/accounts(a176be9e-9a68-e711-80e7-00155d41e206)",
    "activestageid@odata.bind": "/processstages(9a9185f5-b75b-4bbb-9c2b-a6626683b99b)"    
}
```

**การตอบกลับ**

```http
HTTP/1.1 204 No Content
OData-Version: 4.0
OData-EntityId: [Organization URI]/api/data/v9.0/new_mycustombpfs(cc3f721b-026e-e811-80ff-00155d513100)
```

โปรดทราบว่าถ้าคุณต้องการสร้างอินสแตนซ์ของข้อกำหนดโฟลว์กระบวนการธุรกิจโดยกำหนดลำดับขั้นที่ใช้งานอยู่เป็นลำดับขั้น***อื่น ๆ*** คุณต้องระบุ `traversedpath` ในคำขอของคุณด้วย เส้นทางที่ตรวจสอบเป็นสตริงที่คั่นด้วยจุลภาคของรหัสลำดับขั้นของกระบวนการที่แสดงถึงลำดับขั้นที่เข้าเยี่ยมชมของอินสแตนซ์ของโฟลว์กระบวนการทางธุรกิจ คำขอต่อไปนี้จะสร้างอินสแตนซ์สำหรับเรกคอร์ดบัญชีผู้ใช้ (ID=679b2464-71b5-e711-80f5-00155d513100) และกำหนดลำดับขั้นที่ใช้งานอยู่เป็นลำดับขั้น S2 (ID=19a11fc0-3398-4214-8522-cb2a97f66e4b)

```http
POST [Organization URI]/api/data/v9.0/new_mycustombpfs HTTP/1.1 
Content-Type: application/json; charset=utf-8 
OData-MaxVersion: 4.0 
OData-Version: 4.0 
Accept: application/json 

{
    "bpf_accountid@odata.bind": "/accounts(679b2464-71b5-e711-80f5-00155d513100)",
    "activestageid@odata.bind": "/processstages(19a11fc0-3398-4214-8522-cb2a97f66e4b)",
    "traversedpath":"9a9185f5-b75b-4bbb-9c2b-a6626683b99b,19a11fc0-3398-4214-8522-cb2a97f66e4b"   
}
```

### <a name="update-a-business-process-flow-entity-record-process-instance"></a>อัปเดตเรกคอร์ดเอนทิตีโฟลว์กระบวนการธุรกิจ (อินสแตนซ์ของกระบวนการ)

คุณสามารถอัปเดตอินสแตนซ์ของกระบวนเพื่อย้ายไปยังลำดับขั้นถัดไป หรือก่อนหน้า ยกเลิกอินสแตนซ์ของกระบวนการ เปิดใช้งานอินสแตนซ์ของกระบวนการใหม่ หรือดำเนินการอินสแตนซ์ของกระบวนการจนเสร็จเรียบร้อย 

#### <a name="stage-navigation"></a>การนำทางของลำดับขั้น

เมื่อต้องการนำทางไปยังลำดับขั้นอื่น คุณต้องอัปเดตเรกคอร์ดของอินสแตนซ์ของกระบวนการเพื่อเปลี่ยน ID ของลำดับขั้นที่ใช้งานอยู่ และอัปเดตตามเส้นทางที่ตรวจสอบ โปรดทราบว่าคุณต้องย้ายไปยังลำดับขั้นถัดไป หรือก่อนหน้าเท่านั้นในขณะอัปเดตอินสแตนซ์ของโฟลว์กระบวนการทางธุรกิจ

ในการดำเนินการนำทางของลำดับขั้น คุณจะต้องใช้ ID ของอินสแตนซ์ของโฟลว์กระบวนการทางธุรกิจที่คุณต้องการอัปเดต เมื่อต้องการเรียกดูอินสแตนซ์ทั้งหมดของโฟลว์กระบวนการทางธุรกิจของคุณ โปรดดู[เรียกดูเรกคอร์ดทั้งหมด (อินสแตนซ์) สำหรับเอนทิตีโฟลว์กระบวนการทางธุรกิจ](#retrieve-all-the-records-instances-for-a-business-process-flow-entity)ก่อนหน้านี้

สมมติว่า ID ของอินสแตนซ์ของกระบวนการที่คุณต้องการอัปเดตคือ dc2ab599-306d-e811-80ff-00155d513100 ให้ใช้คำขอต่อไปนี้เพื่ออัปเดตลำดับขั้นที่ใช้งานจาก S1 เป็น S2:

```http
PATCH [Organization URI]/api/data/v9.0/new_mycustombpfs(dc2ab599-306d-e811-80ff-00155d513100) HTTP/1.1
Content-Type: application/json
OData-MaxVersion: 4.0
OData-Version: 4.0

{
    "activestageid@odata.bind": "/processstages(19a11fc0-3398-4214-8522-cb2a97f66e4b)",
    "traversedpath": "9a9185f5-b75b-4bbb-9c2b-a6626683b99b,19a11fc0-3398-4214-8522-cb2a97f66e4b"
}
```

#### <a name="change-the-state-of-a-process-instance-abort-reactivate-or-finish"></a>เปลี่ยนสถานะของอินสแตนซ์ของกระบวนการ: ยกเลิก เปิดใช้งานใหม่ หรือเสร็จสิ้น 

อินสแตนซ์ของกระบวนการสามารถมีสถานะใดสถานะหนึ่งต่อไปนี้ได้: **ใช้งานอยู่**, **เสร็จเรียบร้อย** หรือ**ยกเลิกแล้ว**ได้ สถานะจะถูกกำหนดโดยแอตทริบิวต์ต่อไปนี้ในเรกคอร์ดของอินสแตนซ์ของกระบวนการ:

- **statecode**: จะแสดงสถานะของอินสแตนซ์ของกระบวนการ

    |ค่า|ป้ายกำกับ|
    |-----|-----|
    |0    |ใช้งานอยู่|
    |1    |ไม่ใช้งาน|

- **statuscode**: แสดงข้อมูลเกี่ยวกับสถานะของอินสแตนซ์ของกระบวนการ

    |ค่า|ป้ายกำกับ|
    |-----|-----|
    |1    |ใช้งานอยู่|
    |2    |เสร็จเรียบร้อย!|
    |3    |ยกเลิกการทำงาน|

ดังนั้น หากต้องการ**ยกเลิก**อินสแตนซ์ของกระบวนการ ให้ใช้คำขอต่อไปนี้เพื่อตั้งค่า `statecode` และ `statuscode` อย่างเหมาะสม:

```http
PATCH [Organization URI]/api/data/v9.0/new_mycustombpfs(dc2ab599-306d-e811-80ff-00155d513100) HTTP/1.1   
Content-Type: application/json   
OData-MaxVersion: 4.0   
OData-Version: 4.0 
  
{ 
    "statecode" : "1", 
    "statuscode": "3" 
}
```
 
> [!NOTE]
> คุณสามารถยกเลิกอินสแตนซ์ของกระบวนการในลำดับขั้นใดก็ได้

ในทำนองเดียวกัน หากต้องการเปิดใช้อินสแตนซ์ของกระบวนการใหม่ ให้แทนที่ค่า `statecode` และ `statuscode` ในรหัสด้านบนด้วย **0** และ **1** ตามลำดับ

สุดท้าย หากต้องการตั้งค่าสถานะอินสแตนซ์ของกระบวนการเป็น**เสร็จเรียบร้อย** ซึ่งจะสามารถทำได้เฉพาะในลำดับขั้นสุดท้ายของอินสแตนซ์ของกระบวนการเท่านั้น ให้แทนที่ค่า `statecode` และ `statuscode` ในรหัสด้านบนด้วย **0** และ **2** ตามลำดับ

#### <a name="cross-entity-navigation"></a>การนำทางระหว่างเอนทิตี

สำหรับการนำทางระหว่างเอนทิตีในตัวอย่างนี้ คุณต้องตั้งค่าลำดับขั้นที่ใช้งานอยู่ของอินสแตนซ์ของกระบวนเป็นลำดับขั้นสุดท้าย S3 (ID=a107e2fd-7543-4c1a-b6b4-b8060ecb1a1a) และอัปเดตเส้นทางที่ตรวจสอบตามลำดับ รวมถึงตั้งค่าเรกคอร์ดผู้ติดต่อเป็นเรกคอร์ดเอนทิตีหลักตามข้อกำหนดโฟลว์กระบวนการทางธุรกิจ

```http
PATCH [Organization URI]/api/data/v9.0/new_mycustombpfs(dc2ab599-306d-e811-80ff-00155d513100) HTTP/1.1   
Content-Type: application/json   
OData-MaxVersion: 4.0   
OData-Version: 4.0 
  
{
    "activestageid@odata.bind": "/processstages(a107e2fd-7543-4c1a-b6b4-b8060ecb1a1a)",
    "traversedpath":"9a9185f5-b75b-4bbb-9c2b-a6626683b99b,19a11fc0-3398-4214-8522-cb2a97f66e4b,a107e2fd-7543-4c1a-b6b4-b8060ecb1a1a",
    "bpf_contactid@odata.bind": "/contacts(0e3f10b0-da33-e811-80fc-00155d513100)"
}
``` 

### <a name="delete-a-business-process-flow-entity-record-process-instance"></a>ลบเรกคอร์ดเอนทิตีโฟลว์กระบวนการธุรกิจ (อินสแตนซ์ของกระบวนการ)

ใช้คำขอ API ของเว็บต่อไปนี้:

**คำขอ**

```http
DELETE [Organization URI]/api/data/v9.0/new_mycustombpfs(dc2ab599-306d-e811-80ff-00155d513100) HTTP/1.1
```  

**การตอบกลับ**

ถ้ามีเรกคอร์ดอยู่ คุณจะได้รับการตอบกลับตามปกติพร้อมสถานะ 204 เพื่อระบุว่าการลบสำเร็จแล้ว ถ้าไม่พบเอนทิตี คุณจะได้รับการตอบกลับพร้อมสถานะ 404

## <a name="use-retrieveprocessinstances-and-retrieveactivepath-messages"></a>ใช้ข้อความ RetrieveProcessInstances และ RetrieveActivePath

ใช้ข้อความ `RetrieveProcessInstances` (<xref href="Microsoft.Dynamics.CRM.RetrieveProcessInstances?text=RetrieveActivePath Function" /> หรือ <xref:Microsoft.Crm.Sdk.Messages.RetrieveProcessInstancesRequest>) เพื่อเรียกดูอินสแตนซ์ของโฟลว์กระบวนการธุรกิจทั้งหมดสำหรับเรกคอร์ดเอนทิตีที่ใช้ในข้อกำหนดโฟลว์กระบวนการทางธุรกิจทั้งหมด อินสแตนซ์ของโฟลว์กระบวนการทางธุรกิจที่ส่งกลับสำหรับเอนทิตีจะถูกจัดเรียงตามแอตทริบิวต์ `modifiedon` สำหรับอินสแตนซ์ ตัวอย่างเช่น อินสแตนซ์ของโฟลว์กระบวนการทางธุรกิจที่ปรับเปลี่ยนครั้งล่าสุดจะอยู่ในเรกคอร์ด*แรก*ในคอลเลกชันที่ส่งกลับ อินสแตนซ์ของโฟลว์กระบวนการทางธุรกิจที่ปรับเปลี่ยนครั้งล่าสุดเป็นอินสแตนซ์ที่ใช้งานอยู่ใน UI สำหรับเรกคอร์ดเอนทิตี  
  
แต่ละเรกคอร์ดอินสแตนซ์ของโฟลว์กระบวนการทางธุรกิจที่ส่งกลับสำหรับเรกคอร์ดเอนทิตีเป็นผลมาจากการใช้ข้อความ `RetrieveProcessInstances` ในการจัดเก็บ ID ของลำดับขั้นที่ใช้งานอยู่ในแอตทริบิวต์ `processstageid` ที่สามารถใช้เพื่อค้นหาลำดับขั้นที่ใช้งานอยู่ แล้ว ย้ายไปยังลำดับขั้นก่อนหน้า หรือถัดไป ในการดำเนินการดังกล่าว ขั้นแรกคุณต้องพบเส้นทางใช้งานอยู่ของอินสแตนซ์ของโฟลว์กระบวนการทางธุรกิจและลำดับขั้นต่าง ๆ ที่มีอยู่ในอินสแตนซ์กระบวนการธุรกิจโดยใช้ข้อความ `RetrieveActivePath` (<xref href="Microsoft.Dynamics.CRM.RetrieveActivePath?text=RetrieveActivePath Function" /> หรือ <xref:Microsoft.Crm.Sdk.Messages.RetrieveActivePathRequest>)   
  
 เมื่อคุณมีลำดับขั้นที่ใช้งานอยู่และข้อมูลเส้นทางที่ใช้งานสำหรับอินสแตนซ์ของโฟลว์กระบวนการทางธุรกิจ คุณสามารถใช้ข้อมูลเพื่อย้ายไปลำดับขั้นถัดไป หรือก่อนหน้าในเส้นทางที่ใช้งานอยู่ได้ การนำทางไปข้างหน้าของลำดับขั้นต้องทำตามลำดับ นั่นคือ คุณควรย้ายไปยังลำดับขั้นต่อไปในเส้นทางที่ใช้งานอยู่เท่านั้น   
  
 สำหรับตัวอย่างทั้งหมดที่โค้ดแสดงการใช้งานของทั้งสองวิธีและการนำทางของลำดับขั้นโดยใช้[บริการองค์กร](/dynamics365/customer-engagement/developer/org-service/use-organization-service-read-write-data-metadata) โปรดดู[ตัวอย่าง: ทำงานกับโฟลว์กระบวนการทางธุรกิจ](sample-work-business-process-flows.md) 

<a name="ApplyBPF"></a>   
## <a name="apply-business-process-flow-while-creating-an-entity-record"></a>ใช้โฟลว์กระบวนการทางธุรกิจในขณะสร้างเรกคอร์ดเอนทิตี

ส่วนนี้จะมีข้อมูลเกี่ยวกับลักษณะเริ่มต้นสำหรับการนำโฟลว์กระบวนการทางธุรกิจโดยอัตโนมัติไปใช้ในเรกคอร์ดเอนทิตีใหม่ที่สร้างขึ้นใน Customer Engagement และวิธีที่คุณสามารถแทนที่ได้เพื่อใช้โฟลว์กระบวนการทางธุรกิจที่คุณต้องการสำหรับเรกคอร์ดเอนทิตีใหม่

ตามค่าเริ่มต้น สำหรับเอนทิตีที่มีโฟลว์กระบวนการทางธุรกิจหลายระบบที่กำหนด ระบบจะนำโฟลว์กระบวนการทางธุรกิจไปใช้ในเรกคอร์ดเอนทิตีใหม่โดยใช้ตรรกะหลายขั้นตอนต่อไปนี้:
1. ระบุโฟลว์กระบวนทางธุรกิจทั้งหมดที่สามารถใช้ได้กับเรกคอร์ดเอนทิตีใหม่ตามแอตทริบิวต์ **Workflow.PrimaryEntity** ของเรกคอร์ดข้อกำหนดโฟลว์กระบวนการทางธุรกิจ
2. ระบุข้อกำหนดโฟลว์กระบวนการทางธุรกิจที่ผู้ใช้ปัจจุบันมีสิทธิ์เข้าถึง สำหรับข้อมูลเกี่ยวกับวิธีการเข้าถึงโฟลว์กระบวนการธุรกิจที่จะกำหนดและจัดการ โปรดดู[จัดการความปลอดภัยสำหรับโฟลว์กระบวนการทางธุรกิจ](#BPFSecurity)ในหัวข้อก่อนหน้านี้<br/>  
3. ข้อกำหนดโฟลว์กระบวนการทางธุรกิจทั้งหมดในระบบอยู่ภายใต้ระเบียบสากลสำหรับแต่ละเอนทิตี ลำดับของโฟลว์กระบวนการทางธุรกิจจะถูกเก็บไว้ในแอตทริบิวต์ **Workflow.ProcessOrder** ข้อกำหนดโฟลว์กระบวนการทางธุรกิจสำหรับเอนทิตีจะเรียงลำดับตามนี้ และจะเลือกลำดับที่มีค่าลำดับต่ำสุด
4. สุดท้าย ถ้ามีการสร้างเรกคอร์ดเอนทิตีขึ้นจากแอปสำหรับธุรกิจ (โมดูลแอป) จะมีการใช้การกรองระดับที่มากขึ้นเพื่อเลือกโฟลว์กระบวนการทางธุรกิจที่จะนำมาใช้กับเรกคอร์ดเอนทิตีใหม่โดยอัตโนมัติ เมื่อทำงานในแอป ผู้ใช้สามารถเข้าถึงเฉพาะเอนทิตี โฟลว์กระบวนการทางธุรกิจ มุมมอง และฟอร์มที่เกี่ยวข้อง ที่ผู้ใช้เข้าถึงได้โดยอาศัยบทบาทด้านความปลอดภัยที่กำหนดให้กับแอปธุรกิจเท่านั้น 
    - ถ้าแอปพลิเคชันทางธุรกิจไม่มีโฟลว์กระบวนการทางธุรกิจใด ๆ อยู่เลย ระบบจะนำโฟลว์กระบวนการทางธุรกิจมาใช้ตามที่อธิบายไว้จนถึงขั้นตอนที่ 3
    - ถ้าแอปพลิเคชันทางธุรกิจมีอย่างน้อยหนึ่งโฟลว์กระบวนการทางธุรกิจ ระบบจะนำเฉพาะโฟลว์กระบวนการธุรกิจที่มีอยู่ในแอปมาใช้เท่านั้น ในกรณีนี้ เมื่อผู้ใช้กำลังทำงานในบริบทแอปพลิเคชันทางธุรกิจ รายการของโฟลว์กระบวนการธุรกิจจากขั้นตอนที่ 3 จะถูกกรองไปยังส่วนที่เป็นส่วนหนึ่งของแอปพลิเคชันทางธุรกิจที่อยู่ภายในโมดูลแอป และจะเรียงลำดับตามลำดับกระบวนการ 
    - ถ้าไม่มีโฟลว์กระบวนการทางธุรกิจในแอปพลิเคชันทางธุรกิจสำหรับเอนทิตีหรือที่ผู้ใช้มีสิทธิ์เข้าถึง ระบบจะไม่นำโฟลว์กระบวนการทางธุรกิจไปใช้สำหรับเรกคอร์ดเอนทิตีใหม่

คุณสามารถแทนที่ตรรกะเริ่มต้นของโฟลว์กระบวนการทางธุรกิจที่จะใช้กับเรกคอร์ดเอนทิตีใหม่โดยอัตโนมัติ เมื่อต้องการทำเช่นนั้น ขณะสร้างเรกคอร์ดเอนทิตีใหม่ ให้ตั้งค่าแอตทริบิวต์ **ProcessId** ของเอนทิตีไปยังค่าใดค่าหนึ่งต่อไปนี้:
- ตั้งค่าเป็น **Guid.Empty** เพื่อข้ามการตั้งค่าโฟลว์กระบวนการธุรกิจสำหรับเรกคอร์ดเอนทิตีใหม่ คุณอาจต้องการทำเช่นนั้นถ้าคุณมีการสร้างเรกคอร์ดเอนทิตีจำนวนมาก แต่ไม่ต้องการนำโฟลว์กระบวนการทางธุรกิจมาใช้
- ตั้งค่าให้เป็นเอนทิตีโฟลว์กระบวนการทางธุรกิจโดยเฉพาะ (เป็นการอ้างอิงเอนทิตี) ในกรณีนี้ ระบบจะใช้โฟลว์กระบวนการทางธุรกิจที่ระบุแทนตรรกะเริ่มต้น

ถ้าคุณไม่ได้ตั้งค่าแอตทริบิวต์ **ProcessId** ในขณะสร้างเรกคอร์ดเอนทิตีใหม่ ระบบจะใช้ตรรกะเริ่มต้นตามที่อธิบายไว้ก่อนหน้านี้

> [!NOTE]
> การแทนที่ตรรกะเริ่มต้นของโฟลว์กระบวนการทางธุรกิจที่จะใช้กับเรกคอร์ดเอนทิตีใหม่โดยอัตโนมัติจะสนับสนุนเฉพาะการเขียนโปรแกรมเท่านั้น คุณไม่สามารถทำขั้นตอนนี้ได้โดยใช้ UI

## <a name="legacy-process-related-attributes-in-entities"></a>แอตทริบิวต์ที่เกี่ยวข้องกับกระบวนการเดิมในเอนทิตี

แอตทริบิวต์ที่เกี่ยวข้องกับกระบวนการเดิม (เช่น **ProcessId**, **StageId** และ **TraversedPath**) บนเอนทิตีที่เปิดใช้งานสำหรับโฟลว์กระบวนการทางธุรกิจได้เลิกใช้แล้ว การจัดการกับแอตทริบิวต์ที่เกี่ยวข้องกับกระบวนการเดิมสำหรับเรกคอร์ดเอนทิตีเป้าหมายไม่รับประกันความสอดคล้องของสถานะโฟลว์กระบวนการทางธุรกิจ และ***ไม่ใช่***สถานการณ์ที่สนับสนุน วิธีที่แนะนำก็คือการใช้แอตทริบิวต์ของเอนทิตีโฟลว์กระบวนการทางธุรกิจตามที่อธิบายไว้ก่อนหน้าในส่วน[สร้าง เรียกใช้ อัปเดต และลบเรกคอร์ดเอนทีตีโฟลว์กระบวนการธุรกิจ (อินสแตนซ์ของกระบวนการ)](#create-retrieve-update-and-delete-business-process-flow-entity-records-process-instances)

ยกเว้นในกรณีนี้ก็คือ การปรับเปลี่ยนแอตทริบิวต์ **ProcessId** โดยการเขียนโปรแกรมในขณะสร้างเรกคอร์ดเอนทิตี เพื่อแทนที่แอปพลิเคชันเริ่มต้นของโฟลว์กระบวนการทางธุรกิจกับระเบียนใหม่ตามที่อธิบายไว้ในส่วนก่อนหน้า: [ใช้โฟลว์กระบวนการทางธุรกิจในขณะสร้างเรกคอร์ดเอนทิตี](#ApplyBPF)

<a name="BKMK_clientSideScript"></a>   
## <a name="client-side-programmability-support-for-business-process-flows"></a>การสนับสนุนการเขียนโปรแกรมฝั่งไคลเอ็นต์สำหรับโฟลว์กระบวนการทางธุรกิจ  
 คุณสามารถใช้วัตถุฝั่งไคลเอ็นต์ในสคริปต์ฟอร์มของคุณเพื่อโต้ตอบกับโฟลว์กระบวนการทางธุรกิจ โฟลว์กระบวนการทางธุรกิจจะทริกเกอร์เหตุการณ์ฝั่งไคลเอ็นต์ทุกครั้งที่มีการใช้กระบวนการใด ๆ กับเรกคอร์ด ลำดับขั้นมีการเปลี่ยนแปลง หรือสถานะมีการเปลี่ยนแปลงเป็น `Active`, `Finished` หรือ `Aborted` ข้อมูลเพิ่มเติม: [formContext.data.process (การอ้างอิง API ไคลเอ็นต์)](/dynamics365/customer-engagement/developer/clientapi/reference/formcontext-data-process.md)  
  
<a name="BKMK_MaxSettings"></a>   
## <a name="maximum-number-of-processes-stages-and-steps"></a>จำนวนสูงสุดของกระบวนการ ลำดับขั้น และขั้นตอน  
 สำหรับแต่ละเอนทิตี ค่าเริ่มต้นสำหรับจำนวนของโฟลว์กระบวนการทางธุรกิจที่เปิดใช้งานสูงสุดคือ 10 คุณสามารถระบุค่าอื่นได้โดยใช้แอตทริบิวต์ `Organization.MaximumActiveBusinessProcessFlowsAllowedPerEntity` อย่างไรก็ตาม หากค่ามากกว่า 10 คุณอาจเห็นประสิทธิภาพของระบบลดลงเมื่อคุณเปลี่ยนกระบวนการหรือเปิดเรกคอร์ดที่มีโฟลว์กระบวนการทางธุรกิจที่กำหนดไว้ ซึ่งอาจเห็นได้ชัดเจนโดยเฉพาะอย่างยิ่งถ้ากระบวนการดังกล่าวครอบคลุมหลายเอนทิตี  
  
 การตั้งค่าต่อไปนี้ไม่สามารถกำหนดเองได้:  
  
-   จำนวนสูงสุดของลำดับขั้นสำหรับแต่ละเอนทิตีในกระบวนการคือ 30  
  
-   จำนวนสูงสุดของขั้นตอนในแต่ละลำดับขั้นคือ 30  
  
-   จำนวนสูงสุดของเอนทิตีที่สามารถเข้าร่วมในโฟลว์กระบวนการคือ 5  

