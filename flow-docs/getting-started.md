---
title: เริ่มต้นใช้งาน | Microsoft Docs
description: วิธีที่รวดเร็วในการเริ่มทำให้งานและชีวิตของคุณเป็นกระบวนการอัตโนมัติด้วย Microsoft Flow
services: ''
suite: flow
documentationcenter: na
author: stepsic-microsoft-com
manager: kvivek
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: hero-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/31/2017
ms.author: stepsic
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: cfd337180d1517df67864e239b611f6283e3af14
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: th-TH
ms.lasthandoff: 09/12/2018
ms.locfileid: "44689789"
---
# <a name="get-started-with-microsoft-flow"></a>เริ่มต้นใช้งาน Microsoft Flow #

<iframe width="560" height="315" src="https://www.youtube.com/embed/iMteXfAvDSE?list=PL8nfc9haGeb55I9wL9QnWyHp3ctU2_ThF" frameborder="0" allowfullscreen></iframe>

ยินดีต้อนรับ! Microsoft Flow เป็นบริการที่ช่วยให้คุณสร้างเวิร์กโฟลว์อัตโนมัติระหว่างแอปและบริการที่คุณชื่นชอบเพื่อซิงโครไนซ์ไฟล์ รับการแจ้งเตือน รวบรวมข้อมูลและอื่น ๆ อีกมากมาย

ชนิดของลำดับงานหลักคือ ลำดับงาน [อัตโนมัติ](get-started-logic-flow.md), [ปุ่ม](introduction-to-button-flows.md), [กำหนดเวลา](run-scheduled-tasks.md) และ [กระบวนการทางธุรกิจ](business-process-flows-overview.md)

ถ้าคุณเป็นผู้กำหนดค่า Dynamics 365 customer engagement คุณอาจคุ้นเคยกับ Classic Common Data Service สำหรับกระบวนการของแอปซึ่งรวมถึง [เวิร์กโฟลว์](configure-workflow-steps.md),[การดำเนินการ](create-actions.md), [ลำดับงานของอุปกรณ์เคลื่อนที่](create-mobile-task-flow.md) และ [กล่องโต้ตอบ](use-cds-for-apps-dialogs.md)

ขั้นตอนแรกคือการ[ลงทะเบียน](sign-up-sign-in.md) หรือถ้าคุณมีบัญชีผู้ใช้ Microsoft Flow ให้[ลงชื่อเข้าใช้](https://flow.microsoft.com/signin)บนแท็บเล็ต คอมพิวเตอร์เดสก์ท็อป หรือแม้แต่โทรศัพท์ของคุณ

## <a name="check-out-the-start-page"></a>ดูหน้าเริ่มต้น ##

[บนหน้าเริ่มต้น](https://flow.microsoft.com)สำหรับ Microsoft Flow คุณสามารถ[สำรวจชุดเทมเพลตที่หลากหลาย](https://flow.microsoft.com/templates)และเรียนรู้เกี่ยวกับคุณลักษณะสำคัญสำหรับ Microsoft Flow ได้ คุณสามารถดูอย่างคร่าว ๆ ได้สำหรับความสามารถต่าง ๆ และวิธีที่ Microsoft Flow สามารถช่วยธุรกิจและชีวิตของคุณได้

ด้วย Microsoft Flow คุณสามารถ:

- ค้นหาเทมเพลตและบริการได้อย่างง่ายดาย

    ![หน้าเริ่มต้นโฟลว์ 1](./media/getting-started/flowhome1.png)

- เลือกจากบริการที่ได้รับความนิยมมากที่สุด

    ![หน้าเริ่มต้นโฟลว์ 2](./media/getting-started/flowhome2.png)

- ดูภาพรวมของแต่ละโฟลว์

    ![หน้าเริ่มต้นโฟลว์ 3](./media/getting-started/flowhome3.png)

แต่ละเทมเพลตถูกออกแบบมาสำหรับวัตถุประสงค์เฉพาะ ตัวอย่างเช่น มีเทมเพลตสำหรับส่งการข้อความถึงคุณเมื่อเจ้านายของคุณส่งอีเมลถึงคุณ การเพิ่มลูกค้าเป้าหมาย Twitter ไปยัง Dynamics 365 หรือสำรองไฟล์ของคุณ เทมเพลตเหล่านี้เป็นเพียงคำแนะนำของภูเขาน้ำแข็ง โดยมีวัตถุประสงค์เพื่อทำให้คุณสามารถสร้างเวิร์กโฟลว์แบบกำหนดเองสำหรับกระบวนการตามความต้องการของคุณ

## <a name="create-your-first-flow"></a>สร้างโฟลว์แรกของคุณ ##

1. เลือกเทมเพลตที่เป็นประโยชน์สำหรับคุณ เทมเพลตอย่างง่ายคือ [ **รับการเตือนความจำรายวันในอีเมล**](https://flow.microsoft.com/galleries/public/templates/45a3399aa29345308f08b6db0a9c85b9/):

    ![เทมเพลตการเตือนความจำประจำวัน](./media/getting-started/template-details.png)

1. เลือก**ดำเนินต่อ**

    ![สร้างการเชื่อมต่อ](./media/getting-started/create-connection.png)

1. ใส่ที่อยู่อีเมลที่จะถูกส่งการเตือนความจำประจำวันไป ถัดไป ใส่ข้อความการเตือนความจำ สุดท้าย เลือก**สร้างโฟลว์** จากนั้นตรวจสอบว่าโฟลว์ของคุณทำงานตามที่คาดไว้หรือไม่

    ![ระบุข้อมูลประจำตัวสำหรับการเชื่อมต่อ](./media/getting-started/configure-email-details.png)

    > [!NOTE]
    > คุณสามารถสำรวจเงื่อนไขที่ทริกเกอร์โฟลว์และการดำเนินการที่เป็นผลลัพธ์จากเหตุการณ์นั้น ลองใช้งานการตั้งค่าเพื่อสร้างโฟลว์ของคุณเอง นอกจากนี้ คุณยังสามารถเพิ่มหรือลบการดำเนินการได้

1. เลือก **เสร็จสิ้น**

[ทำตามบทช่วยสอนนี้](get-started-logic-template.md)เพื่อเรียนรู้เพิ่มเติมเกี่ยวกับการสร้างโฟลว์จากเทมเพลต

## <a name="get-creative"></a>มีความคิดสร้างสรรค์ ##

หลังจากที่คุณได้สร้างโฟลว์แรกของคุณจากเทมเพลตแล้ว ใช้แหล่งข้อมูลที่มีมากกว่า[150 แหล่ง](https://flow.microsoft.com/connectors/)ที่ Microsoft Flow สนับสนุน เพื่อ[สร้างโฟลว์ของคุณเองตั้งแต่เริ่มต้น](get-started-logic-flow.md)

![การสร้างโฟลว์](./media/getting-started/build-a-flow.png)

เมื่อคุณสร้างโฟลว์ตั้งแต่เริ่มต้น คุณควบคุมทั้งเวิร์กโฟลว์ ต่อไปนี้คือบางแนวคิดเพื่อให้คุณเริ่มต้น:

- [โฟลว์ที่มีหลายขั้นตอน](multi-step-logic-flow.md)
- [เรียกใช้งานหน้าที่ตามกำหนดการ](run-scheduled-tasks.md)
- [สร้างโฟลว์การอนุมัติ](wait-for-approvals.md)
- [ดูโฟลว์ทำงาน](see-a-flow-run.md)
- [เผยแพร่เทมเพลต](publish-a-template.md)

## <a name="use-the-mobile-app"></a>ใช้แอปสำหรับอุปกรณ์เคลื่อนที ##

ดาวน์โหลดแอปอุปกรณ์เคลื่อนที่ Microsoft Flow [Android](https://aka.ms/flowmobiledocsandroid), [iOS](https://aka.ms/flowmobiledocsios) หรือ [Windows Phone](https://aka.ms/flowmobilewindows) ด้วยแอปนี้ คุณสามารถ[ตรวจติดตามกิจกรรมโฟลว์](mobile-monitor-activity.md) [จัดการโฟลว์ของคุณ](mobile-manage-flows.md) และ[สร้างโฟลว์จากเทมเพล](mobile-create-flow.md)ได้

## <a name="were-here-to-help"></a>เราคอยช่วยเหลือคุณ ##

เรารู้สึกตื่นเต้นที่จะได้เห็นสิ่งที่คุณสร้างด้วย Microsoft Flow และเราต้องการให้แน่ใจว่า คุณจะได้รับประสบการณ์ดีที่สุด โปรดอย่าลืมดูบทช่วยสอน[การเรียนรู้ที่แนะแนวทาง](https://flow.microsoft.com/guided-learning/)ของเรา และ[เข้าร่วมชุมชนของเรา](http://go.microsoft.com/fwlink/?LinkID=787467)เพื่อถามคำถามและแชร์แนวคิดของคุณ [ติดต่อฝ่ายสนับสนุน](http://go.microsoft.com/fwlink/?LinkID=787479)ถ้าคุณพบปัญหาใด ๆ
