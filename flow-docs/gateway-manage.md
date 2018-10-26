---
title: เรียนรู้การจัดการเกตเวย์ข้อมูลภายในองค์กร | Microsoft Docs
description: ดูและติดตั้งเกตเวย์ข้อมูลภายในองค์กรใน Microsoft Flow
services: ''
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 02/05/2018
ms.author: deonhe
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: b25f63a3980d21e60b26a0783ac4bf5eb6030cd3
ms.sourcegitcommit: 282059c82bfcf5896d06043476c34641906e20e3
ms.translationtype: HT
ms.contentlocale: th-TH
ms.lasthandoff: 10/11/2018
ms.locfileid: "49087919"
---
# <a name="manage-an-on-premises-data-gateway-in-microsoft-flow"></a>จัดการเกตเวย์ข้อมูลภายในองค์กรใน Microsoft Flow

ติดตั้งและจัดการเกตเวย์ข้อมูลภายในองค์กรเพื่อรวมแอปบนระบบคลาวด์กับข้อมูลและแอปภายในองค์กรอย่างปลอดภัยผ่าน Microsoft Flow

เมื่อมีเกตเวย์ คุณจะสามารถเชื่อมต่อข้อมูลภายในองค์กนผ่านการเชื่อมต่อเหล่านี้:

* Apache Impala
* ตัวเชื่อมต่อแบบกำหนดเองที่คุณสร้าง
* DB2
* ระบบไฟล์
* Http ด้วย Azure AD
* Informix
* MySQL
* ฐานข้อมูล Oracle
* PostgreSQL
* SharePoint
* SQL Server
* Teradata (แสดงตัวอย่าง)

> [!IMPORTANT]
> ในตอนนี้ เกตเวย์ข้อมูลของ Microsoft SharePoint สนับสนุนทั้งหมดปริมาณการใช้งานแบบ HTTP และ HTTPS

## <a name="prerequisites"></a>ข้อกำหนดเบื้องต้น

* ชื่อผู้ใช้และรหัสผ่านที่คุณใช้ในการ[ลงทะเบียน](sign-up-sign-in.md)สำหรับ Microsoft Flow
* สิทธิ์ระดับผู้ดูแลระบบบนเกตเวย์

  คุณจะมีสิทธิ์เหล่านี้ตามค่าเริ่มต้นสำหรัลทุกเกตเวย์ที่คุณติดตั้ง นอกจากนี้ ผู้ดูแลระบบของเกตเวย์อื่นยังสามารถมอบสิทธิ์เหล่านี้สำหรับเกตเวย์ดังกล่าวให้กับคุณได้
* สิทธิ์การใช้งานที่สนับสนุนเกตเวย์ สำหรับข้อมูลเพิ่มเติม ให้ดูส่วน "การเชื่อมต่อ" ของ[หน้าการกำหนดราคา](https://flow.microsoft.com/pricing/)

> [!NOTE]
> คุณสามารถสร้างเกตเวย์และการเชื่อมต่อภายในองค์กรได้เฉพาะใน[สถาพแวดล้อมเริ่มต้น](environments-overview-maker.md)เท่านั้น



## <a name="view-your-gateways"></a>ดูเกตเวย์ของคุณ

ที่มุมขวาบนของ[เว็บไซต์ Microsoft Flow](https://flow.microsoft.com) ให้เลือกไอคอนรูปเฟือง แล้วเลือก **เกตเวย์**

![เกตเวย์ภายใต้การจัดการ][1]

> [!NOTE]
> ถ้าคุณสร้างหรือได้รับสิทธิ์การเข้าถึงเกตเวย์ใน PowerApps เกตเวย์จะปรากฏในรายการ **เกตเวย์ของฉัน** ใน Microsoft Flow



## <a name="install-a-gateway"></a>ติดตั้งเกตเวย์

1. ดาวน์โหลด[ตัวช่วยสร้างการติดตั้งเกตเวย์](https://go.microsoft.com/fwlink/?LinkID=820580&clcid=0x409)

1. เรียกใช้ตัวช่วยสร้างและป้อนข้อมูลประจำตัวเดียวกับที่คุณใช้ลงชื่อเข้าใช้ Microsoft Flow

    หลังจากที่คุณลงทะเบียนและกำหนดค่าเกตเวย์ของคุณเรียบร้อยแล้ว จะแสดงในรายการ **เกตเวย์** ใน Microsoft Flow

สำหรับข้อมูลเพิ่มเติม ให้ดู [ทำความเข้าใจเกตเวย์](gateway-reference.md)

<!-- Image references -->
[1]: ./media/manage-gateway/view-gateways.png
