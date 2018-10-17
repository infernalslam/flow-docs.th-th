---
title: สร้างลำดับกระบวนการทางธุรกิจใน PowerApps | MicrosoftDocs
description: เรียนรู้วิธีสร้างลำดับกระบวนการทางธุรกิจ
ms.custom: ''
ms.date: 08/17/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: efe86ab3-430f-485a-b924-6ed82cfbb449
caps.latest.revision: 39
author: Mattp123
ms.author: matp
manager: kvivek
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: 1e765d4c7c11354e382c3ff74ac66103345ff39f
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: th-TH
ms.lasthandoff: 09/12/2018
ms.locfileid: "44691054"
---
# <a name="tutorial-create-a-business-process-flow-to-standardize-processes"></a>บทช่วยสอน: สร้างลำดับกระบวนการทางธุรกิจเพื่อกำหนดมาตรฐานกระบวนการ

บทช่วยสอนนี้แสดงวิธีการสร้างลำดับกระบวนการทางธุรกิจด้วย PowerApps เมื่อต้องการเรียนรู้เพิ่มเติมเกี่ยวกับสาเหตุที่คุณใช้ลำดับกระบวนการทางธุรกิจ ดูที่ [ลำดับกระบวนการทางธุรกิจ](business-process-flows-overview.md) สำหรับข้อมูลเกี่ยวกับการสร้างลำดับงานบนโทรศัพท์ ดู[สร้างลำดับงานบนโทรศัพท์](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-mobile-task-flow)  
  
 เมื่อผู้ใช้เริ่มลำดับกระบวนการทางธุรกิจ ขั้นและขั้นตอนของกระบวนการจะปรากฏในแถบกระบวนการด้านบนของแบบฟอร์ม  
  
 ![กระบวนการทางธุรกิจด้วยขั้น](media/business-process-stages.png "กระบวนการทางธุรกิจที่มีลำดับขั้น")  
  
 > [!TIP]
 >  หลังจากที่คุณสร้างคำนิยามของลำดับกระบวนการทางธุรกิจ คุณสามารถควบคุมว่าใครสามารถสร้าง อ่าน ปรับปรุงข้อมูล หรือลบตัวอย่างลำดับกระบวนการทางธุรกิจได้ ตัวอย่างเช่น สำหรับกระบวนการที่เกี่ยวข้องกับบริการ คุณอาจให้ตัวแทนฝ่ายบริการของลูกค้าเข้าถึงเต็มรูปแบบเพื่อเปลี่ยนตัวอย่างลำดับ์กระบวนการทางธุรกิจ แตให้ตัวแทนฝ่ายขาย่เข้าถึงตัวอย่างแบบอ่านอย่างเดียว เพื่อให้พวกเขาสามารถตรวจสอบกิจกรรมหลังการขายสำหรับลูกค้าของพวกเขาได้ ตั้งค่าการรักษาความปลอดภัยสำหรับคำจำกัดความของลำดับกระบวนการทางธุรกิจที่คุณสร้าง โดย**ปิดใช้งานบทความการรักษาความปลอดภัย** บนแถบการดำเนินการ  
  
<a name="BKMK_Createbusinessprocessflows"></a>   
## <a name="create-a-business-process-flow"></a>สร้างลำดับกระบวนการทางธุรกิจ  
  
1. เปิด [การสำรวจการแก้ปัญหา](/powerapps/maker/model-driven-apps/advanced-navigation#solution-explorer)
  
2. ในบานหน้าต่างนำทางด้านซ้าย เลือก**กระบวนการ** 
  
3.  บนแถบเครื่องมือ**การดำเนินการ** เลือก**ใหม่**  
  
4.  ในกล่องข้อความโต้ตอบ **สร้างกระบวนการ** กรอกข้อมูลในเขตข้อมูลที่กำหนด  
  
    -   ป้อน่ชื่อกระบวนการ ชื่อกระบวนการไม่จำเป็นต้องต่างกัน แต่ควรมีความหมายสำหรับผู้ที่ต้องเลือกกระบวนการ คุณสามารถเปลี่ยนได้ในภายหลัง  
  
    -   ในรายการ**ประเภท** เลือก**ลำดับกระบวนการทางธุรกิจ**  
  
         คุณไม่สามารถเปลี่ยนประเภทได้หลังจากที่สร้างกระบวนการ  
  
    -   ในรายการ**เอนทิตี** เลือกเอนทิตีที่คุณต้องการตามกระบวนการ  
  
         เอนทิตีคุณเลือกมีผลต่อเขตข้อมูลที่พร้อมใช้งานสำหรับขั้นตอนที่สามารถเพิ่มลงในขั้นแรกของลำดับขั้นตอน หากคุณไม่พบเอนทิตี้ที่ต้องการ ให้แน่ใจว่าเอนทิตี้มีการกำหนดตัวเลือกสำหรับลำดับกระบวนการทางธุรกิจ (จะสร้างเขตข้อมูลขึ้น) ในคำจำกัดความของเอนทิตี้ คุณไม่สามารถเปลี่ยนได้หลังจากที่บันทึกกระบวนการ  
  
5. เลือก **ตกลง**  
  
     สร้างกระบวนการใหม่ และตัวออกแบบลำดับกระบวนการทางธุรกิจที่เปิดขึ้นพร้อมกันในขั้นตอนเดียวที่สร้างไว้แล้วสำหรับคุณ  
  
 ![หน้าต่างลำดับกระบวนการทางธุรกิจแสดงองค์ประกอบหลัก](media/business-process-flow-window-showing-main-elements.png "หน้าต่างลำดับกระบวนการทางธุรกิจแสดงองค์ประกอบหลัก")  
  
6. **เพิ่มขั้นตอน** หากผู้ใช้ของคุณจะดำเนินจากขั้นตอนทางธุรกิจหนึ่งไปยังอีกขั้นหนึ่งในกระบวนการ:  
  
    1.  ลากองค์ประกอบ**ขั้นตอน**จากแท็บ**ส่วนประกอบ** แล้ววางบนสัญลักษณ์ + ในตัวออกแบบ  
  
        ![ลากขั้นกระบวนการทางธุรกิจ](media/drag-business-process-stage.png "ลากขั้นกระบวนการทางธุรกิจ")  
  
    2.  กำหนดคุณสมบัติสำหรับขั้นตอน เลือกขั้น จากนั้นกำหนดคุณสมบัติในแท็บ**คุณสมบัติ**ทางด้านขวาของหน้าจอ:  
  
        -   ป้อนชื่อที่แสดง  
  
        -   เลือกประเภทสำหรับขั้นตอนได้ตามต้องการ  ประเภท (เช่น**คุณสมบัติเหมาะสม**หรือ**พัฒนา**) ปรากฏเป็นเครื่องหมายบั้งในแถบกระบวนการ  
  
            ![เครื่องหมายบั้งที่แถบกระบวนการทางธุรกิจ](media/business-process-bar-chevron.png "เครื่องหมายบั้งที่แถบกระบวนการทางธุรกิจ")  
  
        -   เมื่อคุณเปลี่ยนแปลงคุณสมบัติเสร็จ เลือกปุ่ม**นำไปใช้**  
  
7. **เพิ่มขั้นตอนลงในขั้น** ดูขั้นตอนในขั้น โดยเลือก**รายละเอียด**ที่มุมล่างขวาของขั้น เพิ่มขั้นตอนเพิ่มเติม:  
  
    1.  โดยลากส่วนประกอบของ**ขั้นตอน** ไว้ในขั้นจากแท็บ**ส่วนประกอบ**  
  
        ![เพิ่มขั้นตอนในขั้นที่อยู่ในกระบวนการทางธุรกิจ](media/add-step-stage-business-process.png "เพิ่มขั้นตอนในขั้นที่อยู่ในกระบวนการทางธุรกิจ")  
  
    2.  เลือกขั้นตอน จากนั้นกำหนดคุณสมบัติในแท็บ**คุณสมบัติ**:  
  
        1.  ป้อนชื่อที่แสดงสำหรับขั้นตอน  
  
        2.  หากต้องการให้ผู้ใช้ป้อนข้อมูลเพื่อดำเนินการขั้นตอนให้เสร็จสิ้น เลือกเขตข้อมูลที่เหมาะสมจากรายการเลื่อนลง  
  
        3.  เลือก**จำเป็น**หากต้องกรอกข้อมูลในเขตข้อมูลเพื่อดำเนินการตามขั้นตอนให้เสร็จสิ้นก่อนย้ายไปยังขั้นถัดไปของกระบวนการ  
  
        4.  เลือก**นำไปใช้**เมื่อดำเนินการเสร็จ  
  
8. **เพิ่มสาขา (เงื่อนไข) ในกระบวนการ** เพิ่มเงื่อนไขการโยงหัวข้อ:  
  
    1.  โดยลากส่วนประกอบ**เงื่อนไข**จากแท็บ**ส่วนประกอบ์** ไปยังสัญลักษณ์ + ระหว่างสองขั้นตอน  
  
        ![เพิ่มเงื่อนไขในลำดับกระบวนการทางธุรกิจ](media/add-condition-business-process-flow.png "เพิ่มเงื่อนไขในลำดับกระบวนการทางธุรกิจ")  
  
    2.  เลือกเงื่อนไข จากนั้นกำหนดคุณสมบัติในแท็บ**คุณสมบัติ** สำหรับข้อมูลเพิ่มเติมเกี่ยวกับคุณสมบัติโยงหัวข้อ ดู[ปรับปรุงลำดับกระบวนการทางธุรกิจด้วยการโยงหัวข้อ](enhance-business-process-flows-branching.md) เมื่อคุณกำหนดคุณสมบัติสำหรับเงื่อนไขเสร็จ เลือก**นำไปใช้**  
  
9. **เพิ่มขั้นตอนการทำงาน** เมื่อต้องการเรียกใช้ขั้นตอนการทำงาน:  
  
    1.  ลากส่วนประกอบของ**ขั้นตอนการทำงาน**จากแท็บ**ส่วนประกอบ**ไปยังขั้นตอน หรือไปยังรายการ**ขั้นตอนการทำงานทั้งหมด**ในตัวออกแบบ   สิ่งที่คุณเพิ่มขึ้นอยู่กับต่อไปนี้:  
  
       - **ลากไปที่ขั้น**เมื่อต้องการนำไปยังขั้นตอนการทำงานบนรายการหรือออกจากขั้น ส่วนประกอบของขั้นตอนการทำงานต้องเป็นไปตามเอนทิตี้หลักเดียวกันเช่นเดียวกับขั้น  
  
       - **ลากไปยังรายการขั้นตอนการทำงานทั้งหมด**เมื่อต้องการนำไปยังขั้นตอนการทำงานเมื่อเปิดใช้งานกระบวนการหรือเมื่อเก็บข้อมูลกระบวนการ (เมื่อสถานะเปลี่ยนเป็น**เสร็จสิ้น**หรือ **ละทิ้ง**) ส่วนประกอบของขั้นตอนการทำงานต้องเป็นไปตามเอนทิตี้หลักเดียวกันเช่นเดียวกับกระบวนการ  
  
    2.  เลือกขั้นตอนการทำงาน จากนั้นกำหนดคุณสมบัติในแท็บ**คุณสมบัติ**:  
  
       1.  ป้อนชื่อที่แสดง  
  
       2.  เลือกเมื่อควรนำไปยังขั้นตอนการทำงาน  
  
       3.  ค้นหาขั้นตอนการทำงานที่ใช้งานอยู่ตามความต้องการซึ่งตรงกับเอนทิตี้ของขั้นตอนหรือสร้างขั้นตอนการทำงานใหม่โดยเลือก **ใหม่**  
  
       4.  เลือก**นำไปใช้**เมื่อดำเนินการเสร็จ  
  
       สำหรับข้อมูลเพิ่มเติมเกี่ยวกับขั้นตอนการทำงาน ดูที่[กระบวนการของขั้นตอนการทำงาน](../common-data-service/workflow-processes.md)  
  
10. เมื่อต้องการตรวจสอบลำดับกระบวนการทางธุรกิจ เลือก**ตรวจสอบ**บนแถบการดำเนินการ  
  
11. บันทึกกระบวนการเป็นแบบร่างขณะที่ยังคงทำงานอยู่ โดยเลือก**บันทึก**ในแถบการดำเนินการ  
  
    > [!IMPORTANT]
    >  ตราบใดที่กระบวนเป็นแบบร่าง จะไม่สามารถใช้งานได้  
  
12. เปิดใช้งานกระบวนการและทำให้พร้อมใช้งานสำหรับทีมของคุณโดยเลือก**เปิดใช้งาน**บนแถบการดำเนินการ  

13. ควบคุมว่าผู้ใด่สามารถสร้าง อ่าน ปรับปรุงข้อมูล หรือลบตัวอย่างลำดับกระบวนการทางธุรกิจ โดยเลือก**แก้ไขบทบาทการรักษาความปลอดภัย**บนแถบคำสั่งของตัวออกแบบ ตัวอย่างเช่น สำหรับกระบวนการที่เกี่ยวข้องกับบริการ คุณอาจให้ตัวแทนฝ่ายบริการของลูกค้าเข้าถึงเต็มรูปแบบเพื่อเปลี่ยนตัวอย่างลำดับกระบวนการทางธุรกิจ แตให้ตัวแทนฝ่ายขาย่เข้าถึงตัวอย่างแบบอ่านอย่างเดียว เพื่อให้พวกเขาสามารถตรวจสอบกิจกรรมหลังการขายสำหรับลูกค้าของพวกเขาได้

  ในหน้าจอ**บทบาทการรักษาความปลอดภัย** เลือกชื่อของบทบาทเพื่อเปิดหน้าข้อมูลของบทบาทการรักษาความปลอดภัย เลือกแท็บลำดับกระบวนการทางธุรกิจ จากนั้นกำหนดสิทธิ์ที่เหมาะสมในลำดับกระบวนการทางธุรกิจสำหรับบทบาทการรักษาความปลอดภัย

  > [!NOTE]
  > บทบาทการรักษาความปลอดภัยของผู้ดูแลระบบและผู้กำหนดค่าของระบบสามารถเข้าถึงลำดับกระบวนการทางธุรกิจใหมได้่ตามค่าเริ่มต้น

   ![กำหนดสิทธิ์สำหรับกระบวนการทางธุรกิจ](media/bpf-assign-privileges.png)

  ระบุสิทธิ์โดยเลือกปุ่มรูปวิทยุที่เหมาะสม แล้วคลิกบันทึก สำหรับข้อมูลเพิ่มเติมเกี่ยวกับสิทธิ์การใช้งาน ดู[สิทธิ์การใช้งานลำดับกระบวนการทางธุรกิจ](business-process-flows-overview.md#BKMK_MultipleBPF)

  ถัดไป อย่าลืมกำหนดบทบาทการรักษาความปลอดภัยให้แก่ผู้ใช้ที่เหมาะสมในองค์กรของคุณ

> [!TIP] 
>  ต่อไปนี้เป็นเคล็ดลับบางประการที่ควรทราบเมื่อคุณทำงานตามลำดับงานของคุณในหน้าต่างตัวออกแบบ:  
>   
> - ถ่ายภาพทุกสิ่งในหน้าต่างลำดับกระบวนการทางธุรกิจ โดยเลือก**สแนปช็อต**บนแถบการดำเนินการ ซึ่งจะเป็นประโยชน์ เช่น หากคุณต้องการแชร์และรับข้อคิดเห็นบนกระบวนการจากสมาชิกในทีม  
> - ใช้แผนที่ขนาดเล็กเพื่อนำทางไปยังส่วนต่าง ๆ ของกระบวนการได้อย่างรวดเร็ว ซึ่งจะเป็นประโยชน์เมื่อคุณมีกระบวนการที่ซับซ้อนที่เลื่อนออกจากหน้าจอ  
> - เพิ่มคำอธิบายสำหรับกระบวนการทางธุรกิจ โดยเลือก**รายละเอียด**ภายใต้ชื่อกระบวนการที่มุมบนซ้ายของหน้าต่างลำดับกระบวนการทางธุรกิจ คุณสามารถกำหนดได้ถึง 2000 ตัวอักขระ  
  
<a name="BKMK_Editbusinessprocessflows"></a>   
## <a name="edit-a-business-process-flow"></a>แก้ไขลำดับกระบวนการทางธุรกิจ  
 แก้ไขลำดับกระบวนการทางธุรกิจ โดยเปิดตัวสำรวจการแก้ปัญหา เลือก**กระบวนการ** จากนั้นเลือก **ลำดับกระบวนการทางธุรกิจ**จากรายการกระบวนการที่คุณต้องการแก้ไข  
  
 เมื่อคุณเลือกชื่อลำดับกระบวนการทางธุรกิจที่คุณต้องการแก้ไขจากรายการกระบวนการ จะเปิดขึ้นในตัวออกแบบซึ่งคุณสามารถทำการปรับปรุงใดๆ ได้ตามที่่คุณต้องการ ขยาย**รายละเอียด**ภายใต้ชื่อกระบวนการเพื่อเปลี่ยนชื่อหรือเพิ่มคำอธิบาย และดูข้อมูลเพิ่มเติม  
  
 ![ขยายส่วนรายละเอียดของลำดับกระบวนการทางธุรกิจ](media/business-process-flow-details.png "ขยายส่วนรายละเอียดของลำดับกระบวนการทางธุรกิจ")  
  
  
## <a name="other-things-to-know-about-business-process-flows"></a>สิ่งอื่นที่ต้องทราบเกี่ยวกับลำดับกระบวนการทางธุรกิจ
 **แก้ไขขั้นตอน**  
ลำดับกระบวนการทางธุรกิจอาจมีถึง 30 ขั้น    
  
คุณสามารถเพิ่มหรือเปลี่ยนคุณสมบัติต่อไปนี้ของขั้นตอนได้:  
  
- **ชื่อขั้นตอน**  
  
- **เอนทิตี้** คุณสามารถเปลี่ยนเอนทิตี้สำหรับขั้นตอนใดๆ ก็ได้ยกเว้นขั้นแรก  
  
- **ประเภทของขั้นตอน** ประเภทช่วยให้คุณสามารถจัดกลุ่มขั้นตามประเภทการดำเนินการ ซึ่งจะมีประโยชน์สำหรับรายงานที่จะจัดกลุ่มระเบียนตามขั้นตอนนั้น ตัวเลือกสำหรับประเภทของขั้นตอนมาจากชุดตัวเลือกทั้งหมดในประเภทของขั้นตอน คุณสามารถเพิ่มตัวเลือกเพิ่มเติมลงในชุดตัวเลือกทั้งหมดและเปลี่ยนป้ายเชื่อของตัวเลือกที่มีได้ตามต้องการ คุณยังสามารถลบตัวเลือกเหล่านีได้หากคุณต้องการ แต่ขอแนะนำให้ คุณเก็บตัวเลือกเดิมไว้ คุณจะไม่สามารถเพิ่มตัวเลือกที่เหมือนกันไดอีกหากลบไปแล้ว หากคุณไม่ต้องการให้ใช้ เปลี่ยนป้ายชื่อเป็น "ไม่ใช้"  
  
- **ความสัมพันธ์**. ป้อนความสัมพันธ์เมื่อขั้นก่อนหน้าในกระบวนการเป็นไปตามเอนทิตี้อื่น สำหรับขั้นที่กำหนดในปัจจุบัน เลือก**เลือกความสัมพันธ์**เพื่อระบุความสัมพันธที่์จะใช้เมื่อย้ายไปมาระหว่างสองขั้น ขอแนะนำให้คุณเลือกความสัมพันธ์เพื่อสิทธิประโยชน์ต่อไปนี้:  
  
    -   ความสัมพันธ์มักจะมีแผนที่คุณลักษณะที่กำหนดซึ่งดำเนินการโดยอัตโนมัติผ่านข้อมูลระหว่างระเบียน เพื่อลดการป้อนข้อมูล  
  
    -   เมื่อคุณเลือก**ขั้นถัดไป**บนแถบกระบวนการสำหรับระเบียน ระเบียนใดๆ ที่ใช้ความสัมพันธ์จะปรากฏอยู่ในลำดับกระบวนการ ดังนั้นจึงส่งเสริมการใช้ระเบียนในกระบวนการซ้ำ นอกจากนี้ คุณยังสามารถใช้ขั้นตอนการทำงานเพื่อสร้างระเบียนโดยอัตโมัติเพื่อให้ผู้ใช้เพียงแค่เลือกแทนที่จะสร้างการปรับปรุงประสิทธิภาพของกระบวนการต่อไป  
  
**แก้ไขขั้นตอน**  
 แต่ละขั้นตอนอาจมีถึง 30 ขั้นตอน    
  
**เพิ่มสาขา**  
เรียนรู้เกี่ยวกับการเพิ่มสาขาลงในขั้น โดยดูที่ [ปรับปรุงกระบวนการทางธุรกิจด้วยการโยงหัวข้อ](enhance-business-process-flows-branching.md)  
  
เพื่อทำใหลำดับกระบวนการทางธุรกิจพร้อมใช้งาน คุณต้องจัดลำดับกระบวนการ เปิดใช้งานบทบาทการรักษาความปลอดภัย และเปิดใช้งาน  
  
**การกำหนดลำดับกระบวนการ**  
 เมื่อคุณมีลำดับกระบวนการทางธุรกิจมากกว่าหนึ่งลำดับสำหรับเอนทิตี้ (ชนิดระเบียน) คุณจะต้องกำหนดกระบวนการที่ทำงานโดยอัตโนมัติสำหรับสำหรับระเบียนใหม่... ในแถบคำสั่ง เลือก**จัดลำดับกระบวนการ** สำหรับระเบียนใหม่หรือระเบียนที่ยังไม่มีลำดับขั้นตอนที่เกี่ยวข้องนั้น จะใช้ลำดับกระบวนการทางธุรกิจแรกที่ผู้ใช้มีสิทธิ์เข้าถึง  
  
**เปิดใช้งานบทบาทการรักษาความปลอดภัย**  
ผู้ใช้สามารถเข้าถึงลำดับกระบวนการทางธุรกิจได้โดยขึ้นอยู่กับสิทธิ์การใช้งานที่กำหนดบนลำดับกระบวนการทางธุรกิจในบทบาทการรักษาความปลอดภัยที่กำหนดให้กับผู้ใช้ 

จากค่าเริ่มต้น เฉพาะบทบาทการรักษาความปลอดภัยของ**ผู้ดูแลระบบ**และ**ผู้กำหนดค่าของระบบ**ที่สามารถดูลำดับกระบวนการทางธุรกิจได้ 

ระบุสิทธิ์การใช้งานบนลำดับกระบวนการทางธุรกิจ โดยเปิดลำดับกระบวนการทางธุรกิจที่จะแก้ไข จากนั้นเลือก**แก้ไขบทบาทการรักษาความปลอดภัย**บนแถบคำสั่งของตัวออกแบบลำดับกระบวนการทางธุรกิจ ดูขั้นตอนที่ 13 ภายใต้[สร้างลำดับกระบวนการทางธุรกิจ](#create-a-business-process-flow)ดังแสดงไว้ก่อนหน้าในหัวข้อนี้
  
**เปิดใช้งาน**  
ก่อนที่ทุกคนจะสามารถใช้ลำดับกระบวนการทางธุรกิจ คุณจะต้องเปิดใช้งานก่อน ในแถบคำสั่ง เลือก**เปิดใช้งาน** หลังจากที่คุณยืนยันการเปิดใช้งาน ลำดับกระบวนการทางธุรกิจจะพร้อมใช้งาน หากลำดับกระบวนการทางธุรกิจมีข้อผิดพลาด คุณจะไม่สามารถเปิดใช้งานได้จนกว่าจะแก้ไขข้อผิดพลาด  

## <a name="add-an-on-demand-action-to-a-business-process-flow"></a>เพิ่มการดำเนินการตามต้องการในลำดับกระบวนการทางธุรกิจ
Dynamics 365 (ออนไลน์), เวอร์ชันปรับปรุง 9.0 มีคุณลักษณะลำดับกระบวนการทางธุรกิจ: ลำดับกระบวนการทางธุรกิจอัตโนมัติที่มีขั้นตอนการดำเนินการ คุณสามารถเพิ่มปุ่มในลำดับกระบวนการทางธุรกิจที่นำไปสู่การดำเนินการหรือขั้นตอนการทำงาน

### <a name="add-on-demand-workflows-or-actions-using-an-action-step"></a>เพิ่มขั้นตอนการทำงานตามต้องการหรือการดำเนินการโดยใช้ขั้นตอนการดำเนินการ
สมมติว่าในฐานะที่เป็นส่วนหนึ่งของกระบวนการตรวจสอบคุณสมบัติผู้มีสิทธิ์ องค์กร Contoso กำหนดให้มีการพิจารณาโอกาสทั้งหมดโดยผู้พิจารณาที่กำหนดไว้ ต่อมา องค์กร Contoso สร้างการดำเนินการที่: 

- สร้างระเบียนงานที่กำหนดให้กับผู้พิจารณาโอกาส 
- ผนวก "พร้อมสำหรับการพิจารณา" ไปยังหัวข้อโอกาส 

นอกจากนี้ Contoso ยังต้องสามารถเรียกใช้การดำเนินการเหล่านี้ได้ตามความต้องการ รวมงานเหล่านี้ในกระบวนการตรวจสอบคุณสมบัติผู้มีสิทธิ์ โดยการดำเนินการต้องปรากฏบนลำดับกระบวนการทางธุรกิจสำหรับโอกาส เปิดใช้งานฟังก์ชันนี้ โดยเลือก**เป็นขั้นตอนการดำเนินการที่เป็นลำดับกระบวนการทางธุรกิจ**
![สามารถเรียกใช้เป็นลำดับกระบวนการทางธุรกิจได้](media/action-available-to-run.png)

ถัดไป มีการเพิ่มขั้นตอนการดำเนินการลงในลำดับกระบวนการทางธุรกิจในโอกาสของ Contoso จากนั้นตรวจสอบและปรับปรุงข้อมูลลำดับกระบวนการ

![เพิ่มการดำเนินการให้กับลำดับกระบวนการทางธุรกิจเพื่อโอกาส](media/add-action-to-bpf.png)

ตอนนี้ สมาชิกฝ่ายขายของ Contoso สามารถเริ่มการดำเนินการได้จากขั้นกระบวนการทางธุรกิจ**เมื่อได้รับโอกาส** ตามต้องการ โดยเลือก**ดำเนินการ**

![ดำเนินการ](media/action-execute.png)

> [!IMPORTANT]
> - เพื่อให้สามารถดำเนินการหรือปฏิบัติตามขั้นตอนการทำงานได้ตามต้องการ ลำดับ์กระบวนการทางธุรกิจต้องประกอบด้วยขั้นตอนการดำเนินการ หากขั้นตอนการดำเนินการใช้ขั้นตอนการทำงาน ต้องกำหนดค่าของขั้นตอนการทำงานเพื่อเรียกใช้ตามต้องการ
> - เอนทิตี้ที่เกี่ยวข้องกับการดำเนินการหรือขั้นตอนการทำงานต้องเหมือนกับเอนทิตี้ที่เกี่ยวข้องกับลำดับกระบวนการทางธุรกิจ

### <a name="limitation-of-using-action-steps-in-a-business-process-flow"></a>ข้อจำกัดของการใช้ขั้นตอนการดำเนินการในลำดับกระบวนการทางธุรกิจ

- การดำเนินการไม่พร้อมใช้งานเนื่องจากเป็นขั้นตอนการดำเนินการหากค่าพารามิเตอร์ของข้อมูลเข้าหรือข้อมูลออกเป็นเอนทิตี้ กลุ่มเอนทิตี้ หรือชุดตัวเลือก (รายการให้เลือก) ไม่สามารถดำเนินการที่มีพารามิเตอร์ข้อมูลออกของการอ้างอิงเอนทิตี้ที่มีมากกว่าหนึ่งรายการหรือค่าพารามิเตอร์ข้อมูลขาเข้าของการอ้างอิงเอนทิตี้ไม่ว่ากี่รายการเนื่องจากเป็นขั้นตอนการดำเนินการ ไม่มีการดำเนินการที่ไม่เกี่ยวข้องกับเอนทิตี้หลัก (การดำเนินการทั้งหมด) เนื่องจากเป็นขั้นตอนการดำเนินการ

  
## <a name="next-steps"></a>ขั้นตอนถัดไป  
 [ภาพรวมของลำดับกระบวนการทางธุรกิจ](business-process-flows-overview.md) </br>   
 [ปรับปรุงลำดับกระบวนการทางธุรกิจด้วยการโยงหัวข้อ](enhance-business-process-flows-branching.md)
