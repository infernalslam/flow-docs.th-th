---
title: 'ตัวอย่าง: ทำงานกับลำดับงานของกระบวนการทางธุรกิจ (คู่มือนักพัฒนาสำหรับ Dynamics 365 Customer Engagement) | MicrosoftDocs'
description: ตัวอย่างแสดงให้เห็นถึงวิธีการทำงานร่วมกับลำดับงานของกระบวนการทางธุรกิจ เช่น การเรียกคืนอินสแตนซ์โฟลว์ลำดับงานของกระบวนการทางธุรกิจสำหรับระเบียนเอนทิตี้ การเรียกคืนเส้นทางที่ใช้งานสำหรับอินสแตนซ์โฟลว์ลำดับงานของกระบวนการทางธุรกิจและลำดับขั้นของกระบวนการ และการเปลี่ยนลำดับขั้นที่ใช้งานอยู่
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.service: flow
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 7d378504-b4b2-4a09-838c-69ee094072ef
caps.latest.revision: 15
author: msftman
ms.author: deonhe
search.app:
- Flow
search.audienceType:
- developer
ms.openlocfilehash: 6fe2b6d600d86dfd807dbb1ef794a1f428f26fbf
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: th-TH
ms.lasthandoff: 09/12/2018
ms.locfileid: "44690065"
---
# <a name="sample-work-with-business-process-flows"></a>ตัวอย่าง: ทำงานกับลำดับขั้นของกระบวนการทางธุรกิจ

ตัวอย่างนี้แสดงให้เห็นถึงวิธีการทำงานร่วมกับลำดับงานของกระบวนการทางธุรกิจ เช่น การเรียกคืนอินสแตนซ์โฟลว์ลำดับงานของกระบวนการทางธุรกิจสำหรับระเบียนเอนทิตี้ การเรียกคืนเส้นทางที่ใช้งานสำหรับอินสแตนซ์โฟลว์ลำดับงานของกระบวนการทางธุรกิจและลำดับขั้นของกระบวนการ และการเปลี่ยนลำดับขั้นที่ใช้งานอยู่ สำหรับข้อมูลเกี่ยวกับแนวคิดเหล่านี้ ดูที่ [ทำงานกับลำดับขั้นของกระบวนการทางธุรกิจโดยใช้โค้ด](business-process-flows-code.md)  

 คุณสามารถดาวน์โหลดตัวอย่างนี้จาก [ตัวอย่าง: ทำงานกับลำดับขั้นของกระบวนการทางธุรกิจ](https://go.microsoft.com/fwlink/p/?LinkId=846108)  

<a name="BKMK_Prerequisites"></a>   
## <a name="prerequisites"></a>ข้อกำหนดเบื้องต้น  
 ก่อนที่คุณจะสามารถเรียกใช้ตัวอย่าง:  

1. มีการเข้าถึงสภาพแวดล้อม Common Data Service สำหรับแอปก่อน  

2. มีสิทธิ์ที่เหมาะสมบนเอนทิตี้ลูกค้าเป้าหมาย โอกาสทางการขาย และเวิร์กโฟลว์และระเบียนเอนทิตี้คำจำกัดความลำดับงานของกระบวนการทางธุรกิจที่ใช้ในตัวอย่างนี้  

3. มี Visual Studio 2015 หรือใหม่กว่าเพื่อเรียกใช้ตัวอย่าง  

4. มีการเชื่อมต่ออินเทอร์เน็ตเพื่อดาวน์โหลดโครงการตัวอย่างและเพื่อคืนค่าแพคเกจ NuGet ที่ใช้ในโครงการตัวอย่าง  

<a name="BKMK_WhatThisSampleDoes"></a>   
## <a name="what-this-sample-does"></a>ตัวอย่างนี้ทำอะไร  

1.  สร้างระเบียนลูกค้าเป้าหมายตัวอย่าง ซึ่งจะสร้างอินสแตนซ์ของกระบวนการทางธุรกิจ "กระบวนการเปลี่ยนลูกค้าเป้าหมายไปเป็นการขาย" สำหรับระเบียนลูกค้าเป้าหมายโดยอัตโนมัติ  

2.  แปลงระเบียนลูกค้าเป้าหมายไปยังระเบียนโอกาสทางการขาย  


4.  เรียกใช้อินสแตนซ์ของลำดับงานของกระบวนการทางธุรกิจที่เกี่ยวข้องกับระเบียน "โอกาสทางการขาย" ที่ใช้ข้อความ `RetrieveProcessInstances` ระเบียนแรกในคอลเล็กชันที่ได้รับคืนคืออินสแตนซ์ของลำดับงานของกระบวนการทางธุรกิจที่ใช้งานได้สำหรับระเบียนโอกาสทางการขาย ซึ่งเป็น "กระบวนการเปลี่ยนลูกค้าเป้าหมายไปเป็นการขาย" ในกรณีนี้  

5.  เรียกคืนข้อมูลเส้นทางที่ใช้งานอยู่และลำดับขั้นของกระบวนการสำหรับอินสแตนซ์ "กระบวนการเปลี่ยนลูกค้าเป้าหมายไปเป็นการขาย" ที่ใช้ข้อความ `RetrieveActivePath`  

6.  เรียกคืนลำดับขั้นที่ใช้งานอยู่ในปัจจุบันสำหรับอินสแตนซ์ "กระบวนการเปลี่ยนลูกค้าเป้าหมายไปเป็นการขาย" และแจ้งให้ผู้ใช้ทราบว่าจะย้ายไปยังลำดับขั้นถัดไปหรือไม่ เมื่อยืนยันการย้าย ตั้งค่าลำดับขั้นถัดไปในเส้นทางที่ใช้งานเป็นลำดับขั้นที่ใช้งานสำหรับอินสแตนซ์ "กระบวนการเปลี่ยนลูกค้าเป้าหมายไปเป็นการขาย"  

7.  สุดท้าย พร้อมท์ให้ผู้ใช้ทราบว่าจะลบระเบียนที่สร้างขึ้นในระหว่างการเรียกใช้ตัวอย่างหรือไม่  

     นี่คือผลลัพธ์ของตัวอย่าง:  

    ![ผลลัพธ์ของตัวอย่าง](media/work-with-bpf-sample-output.png "ผลลัพธ์ของตัวอย่าง")  

<a name="BKMK_runSample"></a>   
## <a name="run-the-sample"></a>เรียกใช้ตัวอย่าง  

1. [ดาวน์โหลด](https://go.microsoft.com/fwlink/p/?LinkId=846108) โครงการตัวอย่าง WorkWithBPF Visual Studio และแตกไฟล์ไปยังโฟลเดอร์ในคอมพิวเตอร์ของคุณ  

2. ค้นหาตำแหน่ง `WorkWithBPF.sln`ไฟล์ในโฟลเดอร์ที่แตกออกมา และเปิดใน Visual Studio  

3. โครงการตัวอย่างใช้แพคเกจ NuGet ที่ต้องคืนค่าก่อนเรียกใช้ตัวอย่าง ตรวจสอบให้แน่ใจว่ามีการเปิดใช้งานการคืนค่าแพคเกจ NuGet โดยอัตโนมัติใน Visual Studio หรือไม่ ข้อมูลเพิ่มเติม: [เปิดใช้งานและปิดใช้งานการคืนค่าแพคเกจ NuGet](https://go.microsoft.com/fwlink/?linkid=846106)  

    หรือเลือก **โครงการ** > **จัดการแพคเกจ NuGet** และเลือก **คืนค่า** เพื่อกู้คืนแพคเกจที่ใช้ในตัวอย่าง  

4. กด F5 หรือเลือก **ดีบัก** > **เริ่มแก้จุดบกพร่อง**  

5. หากคุณยังไม่เคยเรียกใช้ตัวอย่างมาก่อน คุณต้องป้อนข้อมูลเพื่อเรียกใช้โค้ด มิเช่นนั้นให้ป้อนหมายเลขสำหรับอินสแตนซ์ที่คุณได้ตั้งไว้ก่อนหน้านี้  


   |                                 พร้อมท์                                  |                                                                                             คำอธิบาย                                                                                             |
   |-------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |      ป้อนชื่อเซิร์ฟเวอร์และพอร์ต Dynamics 365 [crm.dynamics.com]       | พิมพ์ชื่อของเซิร์ฟเวอร์ Dynamics 365 ของคุณ ค่าเริ่มต้นคือ Dynamics 365 (ออนไลน์) (crm.dynamics.com) ในอเมริกาเหนือ<br /><br /> ตัวอย่าง: <br />crm5.dynamics.com |
   | องค์กรนี้ถูกจัดเตรียมไว้ในบริการออนไลน์ของ Microsoft แล้ว (y/n) [n] |                                                 พิมพ์ **y** หากเป็นองค์กรที่ถูกจัดเตรียมไว้ในบริการออนไลน์ของ Microsoft แล้ว มิฉะนั้น พิมพ์ **n**                                                  |
   |                          ป้อน โดเมน\ชื่อผู้ใช้                          |                                                                                    พิมพ์บัญชี Microsoft ของคุณ                                                                                     |
   |                             ป้อนรหัสผ่าน                              |                      พิมพ์รหัสผ่านของคุณ อักขระจะแสดงเป็น "\*" ในหน้าต่าง รหัสผ่านของคุณจะถูกบันทึกไว้อย่างปลอดภัยใน Microsoft Credential Manager เพื่อนำมาใช้ในภายหลัง                       |
   |                ระบุหมายเลของค์กร (1-n) [1]                 |                      จากรายการองค์กรที่แสดงว่าคุณเป็นสมาชิก ให้พิมพ์หมายเลขที่สอดคล้องกัน ค่าเริ่มต้นคือ 1 ที่ระบุว่าเป็นองค์กรแรกในรายการ                       |


6. ตัวอย่างจะดำเนินการตามที่อธิบายไว้ใน [ตัวอย่างนี้ทำอะไร](#what-this-sample-does) และอาจพร้อมท์ให้คุณทราบพร้อมกับตัวเลือกเพิ่มเติม  

7. เมื่อตัวอย่างเสร็จสมบูรณ์ กด ENTER เพื่อปิดหน้าต่างคอนโซล  

