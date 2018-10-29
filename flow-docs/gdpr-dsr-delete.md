---
title: คำขอการลบเจ้าของข้อมูล GDPR ของ Microsoft Flow | Microsoft Docs
description: เรียนรู้วิธีใช้ Microsoft Flow เพื่อตอบสนองคำขอการลบเจ้าของข้อมูล GDPR
services: ''
suite: flow
documentationcenter: na
author: KentWeareMSFT
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 4/17/2018
ms.author: keweare
search.app:
- Flow
- Powerplatform
search.audienceType:
- admin
ms.openlocfilehash: 77ce6e368c8cb54d360ebeaa32f1f649e30aa297
ms.sourcegitcommit: 44bc9de9f06b64615731ceb60a4f46cfcd45b167
ms.translationtype: HT
ms.contentlocale: th-TH
ms.lasthandoff: 09/17/2018
ms.locfileid: "45727193"
---
# <a name="responding-to-gdpr-data-subject-delete-requests-for-microsoft-flow"></a>การตอบสนองคำขอการลบเจ้าของข้อมูล GDPR สำหรับ Microsoft Flow

"สิทธิ์ในการลบ" โดยการเอาข้อมูลส่วนบุคคลออกจากข้อมูลลูกค้าขององค์กรเป็นการป้องกันหลักใน GDPR การเอาข้อมูลส่วนบุคคลออกประกอบด้วยการเอาข้อมูลส่วนบุคคลและบันทึกที่ระบบสร้างขึ้นทั้งหมดออก ยกเว้นข้อมูลบันทึกการตรวจสอบ

Microsoft Flow ช่วยให้ผู้ใช้สามารถสร้างเวิร์กโฟลว์อัตโนมัติที่เป็นส่วนสำคัญของการดำเนินการประจำวันขององค์กรของคุณ เมื่อผู้ใช้ออกจากองค์กรของคุณ ผู้ดูแลระบบจำเป็นต้องตรวจทานและพิจารณาว่าจะลบข้อมูลและทรัพยากรที่ผู้ใช้สร้างขึ้นหรือไม่ด้วยตนเอง มีข้อมูลส่วนบุคคลอื่นที่ถูกลบโดยอัตโนมัติเมื่อบัญชีของผู้ใช้ถูกลบจาก Azure Active Directory

ตารางต่อไปนี้แสดงข้อมูลส่วนบุคคลที่ถูกลบโดยอัตโนมัติ และข้อมูลที่ผู้ดูแลระบบต้องตรวจทานและลบด้วยตนเอง:

|จำเป็นต้องตรวจทานและลบด้วยตนเอง|ลบโดยอัตโนมัติเมื่อผู้ใช้ถูกลบจาก Azure Active Directory|
|------|------|
|สภาพแวดล้อม*|บันทึกที่ระบบสร้างขึ้น|
|สิทธิ์ของสภาพแวดล้อม**|ประวัติการใช้|
|โฟลว์|ฟีดกิจกรรม|
|สิทธิ์โฟลว์|เกตเวย์ |
|รายละเอียดผู้ใช้|สิทธิ์ของเกตเวย์|
|การเชื่อมต่อ*||
|สิทธิ์การเชื่อมต่อ||
|ตัวเชื่อมต่อแบบกำหนดเอง*||
|สิทธิของตัวเชื่อมต่อแบบกำหนดเอง||

*แต่ละทรัพยากรประกอบด้วยระเบียน "สร้างโดย" และ "แก้ไขโดย" ที่มีข้อมูลส่วนบุคคล สำหรับเหตุผลด้านความปลอดภัย ระเบียนเหล่านี้จะถูกเก็บไว้จนกว่าจะมีการลบทรัพยากร

สำหรับสภาพแวดล้อมที่มีฐานข้อมูล Common Data Service สำหรับแอป สิทธิ์ของสภาพแวดล้อม (เช่น ผู้ใช่ที่ถูกกำหนดบทบาทผู้สร้างสภาพแวดล้อม และผู้ดูแลระบบ) จะถูกจัดเก็บไว้เป็นระเบียนในฐานข้อมูล Common Data Service โปรดดู [การดำเนินการ DSR กับข้อมูลลูกค้า Common Data Service](https://go.microsoft.com/fwlink/?linkid=872251) สำหรับคำแนะนำเกี่ยวกับวิธีการตอบสนอง DSR สำหรับผู้ใช้ที่ใช้ Common Data Service

สำหรับข้อมูลและทรัพยากรที่จำเป็นต้องตรวจทานด้วยตนเอง Microsoft Flow มอบประสบการณ์การใช้งานต่อไปนี้เพื่อค้นหาหรือเปลี่ยนข้อมูลส่วนบุคคลสำหรับผู้ใช้ที่ระบุ:

* **การเข้าถึงเว็บไซต์:** ลงชื่อเข้าใช้ [ศูนย์การจัดการ PowerApps](https://admin.powerapps.com/) หรือ [ศูนย์การจัดการ Microsoft Flow](https://admin.flow.microsoft.com/)

* **การเข้าถึง PowerShell:**  [cdmlet ของ PowerShell ของผู้ดูแลระบบ PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) 

นี่คือการแบ่งย่อยประสบการณ์การใช้งานที่พร้อมใช้งานสำหรับผู้ดูแลระบบเพื่อใช้ในการลบข้อมูลส่วนบุคคลแต่ละชนิดภายในทรัพยากรแต่ละชนิด:

|ทรัพยากรที่มีข้อมูลส่วนบุคคล|การเข้าถึงเว็บไซต์|การเข้าถึง PowerShell:|การลบโดยอัตโนมัติ|
|-----|----|----|----|
|บันทึกที่ระบบสร้างขึ้น|[Service Trust Portal ของ Office 365](https://servicetrust.microsoft.com/)|||
|สภาพแวดล้อม|ศูนย์การจัดการ Microsoft Flow|cmdlet ของ PowerApps||
|สิทธิ์ของสภาพแวดล้อม*|ศูนย์การจัดการ Microsoft Flow|cmdlet ของ PowerApps||
|ประวัติการใช้||| ลบผ่านนโยบายการเก็บข้อมูล 28 วัน|
|ตัวดึงข้อมูลกิจกรรม |||ลบผ่านนโยบายการเก็บข้อมูล 28 วัน|
|งานของผู้ใช้|| ||
|โฟลว์|พอร์ทัล Microsoft Flow Maker**|||
|สิทธิ์ของโฟลว์|พอร์ทัล Microsoft Flow Maker|||
|รายละเอียดผู้ใช้งาน||cmdlet ของ PowerApps||
|การเชื่อมต่อ|พอร์ทัลผู้สร้างของ Microsoft Flow| ||
|สิทธิ์การเชื่อมต่อ|พอร์ทัล Microsoft Flow Maker| ||
|ตัวเชื่อมต่อแบบกำหนดเอง|พอร์ทัล Microsoft Flow Maker| ||
|สิทธิของตัวเชื่อมต่อแบบกำหนดเอง|พอร์ทัล Microsoft Flow Maker| ||
|ประวัติการอนุมัติ|พอร์ทัล Microsoft PowerApps Maker|||

*ด้วยการแนะนำของ Common Data Service สำหรับแอป ถ้าฐานข้อมูลถูกสร้างขึ้นภายในสภาพแวดล้อม สิทธิ์ของสภาพแวดล้อมและสิทธิ์ของแอปที่อิงตามรูปแบบจะถูกจัดเก็บไว้เป็นระเบียนภายในอินสแตนซ์ฐานข้อมูล Common Data Service สำหรับแอป โปรดดู [การดำเนินการ DSR กับข้อมูลลูกค้า Common Data Service](https://go.microsoft.com/fwlink/?linkid=872251) สำหรับคำแนะนำเกี่ยวกับวิธีการตอบสนอง DSR สำหรับผู้ใช้ที่ใช้ Common Data Service

\*\* ผู้ดูแลระบบจะสามารถเข้าถึงทรัพยากรเหล่านี้จากพอร์ทัล Microsoft Flow Maker หากผู้ดูแลระบบได้รับการกำหนดการเข้าถึงจากศูนย์การจัดการ Microsoft Flow

## <a name="manage-delete-requests"></a>จัดการคำขอการลบ

ขั้นตอนด้านล่างอธิบายวิธีที่ฟังก์ชันการจัดการมีไว้เพื่อให้บริการคำขอการลบสำหรับ GDPR ควรทำขั้นตอนเหล่านี้ตามลำดับที่แสดงด้านล่าง

> [!IMPORTANT]
> เมื่อต้องการหลีกเลี่ยงไม่ให้ข้อมูลเสียหาย ให้ทำตามขั้นตอนเหล่านี้ตามลำดับ
>
>

## <a name="list-and-re-assign-flows"></a>สร้างรายการและกำหนดโฟลว์อีกครั้ง

ขั้นตอนเหล่านี้คัดลอกโฟลว์ที่มีอยู่สำหรับผู้ใช้ที่แยกไป ถ้าคุณกำหนดความเป็นเจ้าของใหม่ให้กับสำเนา โฟลว์เหล่านี้สามารถดำเนินการต่อเพื่อสนับสนุนกระบวนการทางธุรกิจที่มีอยู่ การคัดลอกโฟลว์เหล่านี้เป็นสิ่งสำคัญที่จะลบการเชื่อมต่อตัวระบุส่วนบุคคลกับผู้ใช้ที่จากไป และต้องสร้างการเชื่อมต่อใหม่สำหรับโฟลว์เพื่อเชื่อมต่อกับแอปพลิเคชัน API และ SaaS อื่น

1. ลงชื่อเข้าใช้ [ศูนย์การจัดการ Microsoft Flow](https://admin.flow.microsoft.com/) แล้วเลือกสภาพแวดล้อมที่มีโฟลว์ที่ผู้ใช้ที่ถูกลบเป็นเจ้าของ

    ![ดูสภาพแวดล้อม](./media/gdpr-dsr-delete/view-environments.png)

1. เลือก **ทรัพยากร** > **โฟลว์** แล้วเลือกชื่อเรื่องสำหรับโฟลว์ที่คุณต้องการกำหนดใหม่

    ![ดูโฟลว์](./media/gdpr-dsr-delete/admin-view-flows.png)

1. เลือก **จัดการการแชร์**

    ![จัดการการแชร์](./media/gdpr-dsr-delete/admin-manage-sharing.png)

1. ในแผง **แชร์** ที่ปรากฏอยู่ใกล้กับขอบด้านขวา ให้เพิ่มตัวคุณเองเป็นเจ้าของ แล้วเลือก **บันทึก**

    ![แชร์โฟลว์](./media/gdpr-dsr-delete/flow-sharing-save.png)

1. ลงชื่อเข้าใช้ [Microsoft Flow](https://flow.microsoft.com/) เลือก **โฟลว์ของฉัน** แล้วเลือก **โฟลว์ของทีม**

1. เลือกจุดไข่ปลา **(… )** สำหรับโฟลว์ที่คุณต้องการคัดลอก แล้วเลือก **บันทึกเป็น**

    ![โฟลว์บันทึกเป็น](./media/gdpr-dsr-delete/flow-save-as.png)

1. กำหนดค่าการเชื่อมต่อตามความจำเป็น แล้วเลือก **ดำเนินการต่อ**

1. ใส่ชื่อใหม่ แล้วเลือก **บันทึก**

    ![สร้างสำเนาของโฟลว์](./media/gdpr-dsr-delete/create-copy-flow.png)

1. โฟลว์เวอร์ชันใหม่นี้จะปรากฏขึ้นใน **โฟลว์ของฉัน** ตำแหน่งที่คุณสามารถแชร์กับผู้ใช้เพิ่มเติมได้ถ้าคุณต้องการ

    ![โฟลว์ของทีม](./media/gdpr-dsr-delete/team-flows.png)

1. ลบโฟลว์ต้นฉบับโดยการเลือกจุดไข่ปลา **(…)** เลือก **ลบ** แล้วเลือก **ลบ** อีกครั้งเมื่อได้รับพร้อมท์ ขั้นตอนนี้จะเอาตัวระบุส่วนบุคคลเบื้องต้นที่รวมอยู่ในการขึ้นต่อกันของระบบระหว่างผู้ใช้และ Microsoft Flow

    ![ลบการยืนยันโฟลว์](./media/gdpr-dsr-delete/delete-flow-confirmation.png)

1. เปิดใช้งานสำเนาของโฟลว์ โดยการเปิด **โฟลว์ของฉัน** แล้ว **เปิด** ตัวควบคุมการสลับ

    ![เปิดใช้งานโฟลว์](./media/gdpr-dsr-delete/toggle-on.png)

1. ขณะนี้การคัดลอกจะดำเนินตรรกะเวิร์กโฟลว์แบบเดียวกับเวอร์ชันเดิม

## <a name="delete-approval-history-from-microsoft-flow"></a>ลบประวัติการอนุมัติจาก Microsoft Flow

 ข้อมูลการอนุมัติสำหรับ Microsoft Flow จะถูกจัดเก็บไว้ภายใน Common Data Service สำหรับแอปเวอร์ชันปัจจุบันหรือก่อนหน้า ภายในการอนุมัติ ข้อมูลส่วนบุคคลจะอยู่ในรูปแบบการกำหนดการอนุมัติและข้อคิดเห็นที่รวมอยู่ในการตอบกลับการอนุมัติ ผู้ดูแลระบบสามารถเข้าถึงข้อมูลดังกล่าวได้โดยทำตามขั้นตอนเหล่านี้:

1. ลงชื่อเข้าใช้ [PowerApps](https://web.powerapps.com/)

1. เลือก **ข้อมูล** แล้วเลือก **เอนทิตี**

1. เลือกจุดไข่ปลา **(...)** สำหรับเอนทิตี **การอนุมัติโฟลว์** แล้วเปิดข้อมูลใน Microsoft Excel

1. ใน Microsoft Excel ค้นหา กรอง แล้วลบข้อมูลการอนุมัติตามความจำเป็น

โปรดดู [การดำเนินการ DSR กับข้อมูลลูกค้า Common Data Service](https://go.microsoft.com/fwlink/?linkid=872251) สำหรับการแนะนำเพิ่มเติมเกี่ยวกับวิธีการตอบสนอง DSR สำหรับผู้ใช้ที่ใช้ Common Data Service


## <a name="delete-connections-created-by-a-user"></a>ลบการเชื่อมต่อที่สร้างโดยผู้ใช้

การเชื่อมต่อจะใช้ร่วมกับตัวเชื่อมต่อเพื่อสร้างการเชื่อมต่อกับระบบ API และ SaaS อื่น  การเชื่อมต่อมีการอ้างอิงผู้ใช้ที่สร้างรายการเหล่านั้น ละเป็นผลให้สามารถลบออกเพื่อเอาการอ้างอิงผู้ใช้ออก

cmdlet ของ PowerShell ของ PowerApps Maker

ผู้ใช้สามารถลบการเชื่อมต่อของตนทั้งหมด โดยใช้ฟังก์ชันเอาการเชื่อมต่อออกจาก [cmdlet ของ PowerShell ของ PowerApps Maker](https://go.microsoft.com/fwlink/?linkid=871448):

```PowerShell
Add-PowerAppsAccount

#Retrieves all connections for the calling user and deletes them
Get-Connection | Remove-Connection
```

cmdlet ของ PowerShell ของผู้ดูแลระบบ PowerApps

```PowerShell
Add-PowerAppsAccount

$deleteDsrUserId = "7822bb68-7c24-49ce-90ce-1ec8deab99a7"
#Retrieves all connections for the DSR user and deletes them 
Get-AdminConnection -CreatedBy $deleteDsrUserId | Remove-AdminConnection 

```
## <a name="delete-the-users-permissions-to-shared-connections"></a>ลบสิทธิ์ของผู้ใช้ในการเชื่อมต่อที่แชร์

cmdlet ของ PowerShell ของ PowerApps Maker

ผู้ใช้สามารถลบลบการกำหนดบทาบาทการเชื่อมต่อของตนทั้งหมดสำหรับฟังก์ชันเอาการกำหนดบทบาทการเชื่อมต่อออกใน [cmdlet ของ PowerShell ของ PowerApps Maker](https://go.microsoft.com/fwlink/?linkid=871448):

```PowerShell
Add-PowerAppsAccount

#Retrieves all connection role assignments for the calling users and deletes them
Get-ConnectionRoleAssignment | Remove-ConnectionRoleAssignment
```

cmdlet ของ PowerShell ของผู้ดูแลระบบ PowerApps

```PowerShell
Add-PowerAppsAccount

$deleteDsrUserId = "7822bb68-7c24-49ce-90ce-1ec8deab99a7"
#Retrieves all shared connections for the DSR user and deletes their permissions 
Get-AdminConnectionRoleAssignment -PrincipalObjectId $deleteDsrUserId | Remove-AdminConnectionRoleAssignment  

```
> [!NOTE]
> ไม่สามารถลบการกำหนดบทบาทเจ้าของได้โดยไม่ต้องลบทรัพยากรการเชื่อมต่อ
>
>

## <a name="delete-custom-connectors-created-by-the-user"></a>ลบตัวเชื่อมต่อแบบกำหนดเองที่สร้างโดยผู้ใช้

ตัวเชื่อมต่อแบบกำหนดเองเพิ่มตัวเชื่อมต่อที่มีอยู่ และช่วยให้สามารถเชื่อมต่อกับ API, SaaS และระบบที่พัฒนาตามที่กำหนดเอง ตัวเชื่อมต่อแบบกำหนดเองมีการอ้างอิงผู้ใช้ที่สร้าง และเป็นผลให้สามารถลบออกเพื่อเอาการอ้างอิงผู้ใช้ออก

cmdlet ของ PowerShell ของ PowerApps Maker

ผู้ใช้สามารถลบลบตัวเชื่อมต่อแบบกำหนดเองของตนทั้งหมดสำหรับฟังก์ชันเอาตัวเชื่อมต่อออกใน [cmdlet ของ PowerShell ของ PowerApps Maker](https://go.microsoft.com/fwlink/?linkid=871448):

```PowerShell
Add-PowerAppsAccount

#Retrieves all custom connectors for the calling user and deletes them
Get-Connector -FilterNonCustomConnectors | Remove-Connector
```

cmdlet ของ PowerShell ของผู้ดูแลระบบ PowerApps
```PowerShell
Add-PowerAppsAccount

$deleteDsrUserId = "7822bb68-7c24-49ce-90ce-1ec8deab99a7"
#Retrieves all custom connectors created by the DSR user and deletes them 
Get-AdminConnector -CreatedBy $deleteDsrUserId | Remove-AdminConnector  

```

## <a name="delete-the-users-permissions-to-shared-custom-connectors"></a>ลบสิทธิ์ของผู้ใช้ในตัวเชื่อมต่อแบบกำหนดเองที่แชร์

cmdlet ของ PowerShell ของ PowerApps Maker

ผู้ใช้สามารถลบลบการกำหนดบทาบาทตัวเชื่อมต่อของตนทั้งหมดสำหรับตัวเชื่อมต่อแบบกำหนดเองที่แชร์ด้วยฟังก์ชันเอาการกำหนดบทบาทตัวเชื่อมต่อออกใน [cmdlet ของ PowerShell ของ PowerApps Maker](https://go.microsoft.com/fwlink/?linkid=871448):

```PowerShell
Add-PowerAppsAccount

#Retrieves all connector role assignments for the calling users and deletes them
Get-ConnectorRoleAssignment | Remove-ConnectorRoleAssignment
```

cmdlet ของ PowerShell ของผู้ดูแลระบบ PowerApps
```PowerShell
Add-PowerAppsAccount

$deleteDsrUserId = "7822bb68-7c24-49ce-90ce-1ec8deab99a7"
#Retrieves all custom connector role assignments for the DSR user and deletes them 
Get-AdminConnectorRoleAssignment -PrincipalObjectId $deleteDsrUserId | Remove-AdminConnectorRoleAssignment  

```

> [!NOTE]
> ไม่สามารถลบการกำหนดบทบาทเจ้าของได้โดยไม่ต้องลบทรัพยากรการเชื่อมต่อ
>
>


## <a name="delete-or-reassign-all-environments-created-by-the-user"></a>ลบ หรือกำหนดสภาพแวดล้อมทั้งหมดที่สร้างโดยผู้ใช้ใหม่

ในฐานะผู้ดูแลระบบ คุณจะต้องตัดสินใจสองอย่างขณะประมวลผลคำขอการลบ DSR สำหรับผู้ใช้สำหรับแต่ละสภาพแวดล้อมที่สร้างโดยผู้ใช้:

1. ถ้าคุณตัดสินใจว่า ไม่มีการใช้สภาพแวดล้อมโดยบุคคลอื่นในองค์กรของคุณ คุณสามารถเลือกที่จะลบสภาพแวดล้อมได้
1. ถ้าคุณตัดสินใจว่า ยังจำเป็นต้องใช้สภาพแวดล้อม คุณสามารถเลือกที่จะไม่ลบสภาพแวดล้อม และเพิ่มตัวคุณเอง (หรือผู้ใช้อื่นในองค์กรของคุณ) เป็นผู้ดูแลระบบสภาพแวดล้อม
> [!IMPORTANT]
> การลบสภาพแวดล้อมจะลบทรัพยากรภายในสภาพแวดล้อมอย่างถาวร รวมถึงแอป โฟลว์ การเชื่อมต่อ ฯลฯ ดังนั้นโปรดตรวจทานเนื้อหาของสภาพแวดล้อมก่อนที่จะลบ
>
>

## <a name="give-access-to-a-users-environments-from-the-microsoft-flow-admin-center"></a>ให้สิทธิ์การเข้าถึงสภาพแวดล้อมของผู้ใช้จากศูนย์การจัดการ Microsoft Flow

ผู้ดูแลระบบสามารถให้ผู้ดูแลระบบเข้าถึงสภาพแวดล้อมที่สร้างโดยผู้ใช้ที่ระบุจาก [ศูนย์การจัดการ Microsoft Flow](https://admin.flow.microsoft.com/) สำหรับข้อมูลเพิ่มเติมเกี่ยวกับการดูแลจัดการสภาพแวดล้อม โปรดนำทางไปยัง [การใช้สภาพแวดล้อมภายใน Microsoft Flow](https://docs.microsoft.com/flow/environments-overview-admin)

## <a name="delete-the-users-permissions-to-all-other-environments"></a>ลบสิทธิ์ไปยังสภาพแวดล้อมอื่นๆ ทั้งหมดของผู้ใช้

ผู้ใช้สามารถกำหนดสิทธิ์ (เช่น ผู้ดูแลระบบสภาพแวดล้อม ผู้สร้างสภาพแวดล้อม ฯลฯ) ในสภาพแวดล้อม ซึ่งถูกจัดเก็บไว้ในบริการ Microsoft Flow เป็น "การกำหนดบทบาท"

ด้วยการมาถึงของ Common Data Service สำหรับแอป ถ้าชุดข้อมูลถูกสร้างขึ้นภายในสภาพแวดล้อม "การกำหนดบทบาท" เหล่านี้จะถูกจัดเก็บไว้ภายในอินสแตนซ์ชุดข้อมูล Common Data Service สำหรับแอป

สำหรับข้อมูลเพิ่มเติมเกี่ยวกับการเอาสิทธิ์ของผู้ใช้ในสภาพแวดล้อมออก ให้นำทางไปยัง [การใช้สภาพแวดล้อมภายใน Microsoft Flow](https://docs.microsoft.com/flow/environments-overview-admin)

## <a name="delete-gateway-settings"></a>ลบการตั้งค่าเกตเวย์
การตอบสนองต่อการร้องขอการลบเจ้าของข้อมูลสำหรับเกตเวย์ข้อมูลภายในองค์กรสามารถดูได้[ที่นี่](https://docs.microsoft.com/power-bi/service-gateway-onprem#tenant-level-administration)

## <a name="delete-user-details"></a>ลบรายละเอียดผู้ใช้
รายละเอียดผู้ใช้ให้ความเชื่อมโยงระหว่างผู้ใช้และผู้เช่าที่เฉพาะเจาะจง ก่อนที่ใช้คำสั่งนี้ ตรวจสอบให้แน่ใจว่าเวิร์กโฟลว์ทั้งหมดสำหรับผู้ใช้รายนี้ได้ถูกมอบหมายอีกครั้ง และ/หรือถูกลบไปแล้วหรือไม่ หลังจากที่ขั้นตอนดังกล่าวเสร็จสมบูรณ์ ผู้ดูแลสามารถลบรายละเอียดผู้ใช้ได้โดยการเรียกใช้ cmdlet **Remove-AdminFlowUserDetails** และส่งผ่านใน ID ออบเจ็กต์สำหรับผู้ใช้นั้น


cmdlet ของ PowerShell ของผู้ดูแลระบบ PowerApps
```PowerShell
Add-PowerAppsAccount
Remove-AdminFlowUserDetails -UserId 1b6759b9-bbea-43b6-9f3e-1af6206e0e80
```

> [!IMPORTANT]
> ถ้าผู้ใช้ยังคงเป็นเจ้าของแต่ละโฟลว์หรือโฟลว์ทีม คำสั่งนี้จะส่งกลับข้อผิดพลาด เพื่อแก้ไขปัญหา ลบโฟล์หรือโฟลว์ทีมที่เหลือทั้งหมดสำหรับผู้ใช้รายนี้ และเรียกใช้คำสั่งอีกครั้ง
>
>
## <a name="delete-the-user-from-azure-active-directory"></a>ลบผู้ใช้จาก Azure Active Directory
เมื่อขั้นตอนข้างต้นเสร็จสมบูรณ์ ขั้นตอนสุดท้ายคือการลบบัญชีผู้ใช้ของผู้ใช้สำหรับ Azure Active Directory โดยทำตามขั้นตอนที่แสดงในเอกสารประกอบ GDPR การร้องขอของเจ้าของข้อมูล Azure ที่สามารถดูได้ใน [Office 365 Service Trust Portal](https://servicetrust.microsoft.com/ViewPage/GDPRDSR)

## <a name="delete-the-user-from-unmanaged-tenant"></a>ลบผู้ใช้จากผู้เช่าที่ไม่มีการจัดการ
ในกรณีที่คุณเป็นสมาชิกของผู้เช่าที่ไม่มีการจัดการ คุณจำเป็นต้องดำเนินการ**ปิดบัญชีผู้ใช้**จากการ[พอร์ทัลความเป็นส่วนตัวของที่ทำงานและโรงเรียน](https://go.microsoft.com/fwlink/?linkid=873123)

เพื่อทำให้ทราบว่าคุณเป็นผู้ใช้ของผู้เช่าที่มีการจัดการหรือไม่มีการจัดการ ให้ดำเนินการกระทำต่อไปนี้:
1. เปิด URL ต่อไปนี้ในเบราว์เซอร์ ตรวจสอบให้แน่ใจว่าได้แทนที่อยู่อีเมลของคุณใน URL:[ https://login.windows.net/common/userrealm/foobar@contoso.com?api-version=2.1 ](https://login.windows.net/common/userrealm/foobar@contoso.com?api-version=2.1)
1. ถ้าคุณเป็นสมาชิกของ**ผู้เช่าที่ไม่มีการจัดการ** คุณจะเห็น `"IsViral": true` จากการตอบสนอง


```JSON
{
  "เข้าสู่ระบบ": "foobar@unmanagedcontoso.com",
  "DomainName": "unmanagedcontoso.com",
  "IsViral": true
}
 ```

1. มิฉะนั้น คุณอยู่ในผู้เช่าที่มีการจัดการ

