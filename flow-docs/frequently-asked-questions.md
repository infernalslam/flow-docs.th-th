---
title: คำถามที่ถามบ่อย | Microsoft Docs
description: คำตอบของคำถามทั่วไปหลายคำถามที่เกี่ยวกับ Microsoft Flow
services: ''
suite: flow
documentationcenter: na
author: stepsic-microsoft-com
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/15/2017
ms.author: stepsic
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: 15f7a58f6cee58d588cf10976cabf55b800f28ce
ms.sourcegitcommit: ffed9f02092fbd19fc4108aee05dd40d1a2a3755
ms.translationtype: HT
ms.contentlocale: th-TH
ms.lasthandoff: 09/24/2018
ms.locfileid: "46711668"
---
# <a name="frequently-asked-questions"></a>คำถามที่ถามบ่อย
## <a name="audience-and-strategy"></a>ผู้ใช้งานและกลยุทธ์
### <a name="what-is-microsoft-flow"></a>Microsoft Flow คืออะไร?
Microsoft Flow เป็นบริการบนระบบคลาวด์ที่ทำให้ง่ายและใช้งานได้ดีในทางปฏิบัติสำหรับผู้ใช้งานทางธุรกิจในการสร้างเวิร์กโฟลว์ที่ทำให้งานและกระบวนการที่ต้องใช้เวลามาก เป็นงานที่ทำโดยอัตโนมัติสำหรับการใช้งานและบริการต่าง ๆ

### <a name="who-is-the-intended-audience-for-microsoft-flow"></a>ใครคือใช้งานเป้าหมายสำหรับ Microsoft Flow?
Microsoft Flow มีใช้งานสองประเภท:

* ผู้ใช้ในธุรกิจ "Citizen Integrator" ในองค์กรซึ่งเป็นคู่ค้ากับ IT เพื่อย้ายความรับผิดชอบสำหรับโซลูชันทางธุรกิจให้เข้าใกล้กับธุรกิจมากขึ้น
* ผู้มีอำนาจตัดสินใจด้าน IT ที่ต้องการเพิ่มประสิทธิภาพให้กับคู่ค้าทางธุรกิจเพื่อสร้างโซลูชันของตนเอง เพื่อให้ผู้เชี่ยวชาญด้าน IT และผู้เชี่ยวชาญด้านการผสานรวมสามารถมุ่งความชำนาญของตนไปที่เครื่องมือการผสานรวมขั้นสูงมากขึ้น เช่น Azure Logic Apps

### <a name="how-do-microsoft-flow-and-logic-apps-relate-to-each-other"></a>Microsoft Flow และ Logic Apps เกี่ยวข้องกันอย่างไร?
Microsoft Flow มีคุณลักษณะที่ช่วยให้ผู้ใช้งานทางธุรกิจสร้างเวิร์กโฟลว์อัตโนมัติได้ Logic Apps คือบริการ Azure ที่มีคุณลักษณะเด่นเดียวกันกับของ Microsoft Flow รวมถึงคุณลักษณะการทำงาน เช่น การรวมกับ Azure Resource Manager และพอร์ทัล Azure, PowerShell และ xPlat CLI, Visual Studio และตัวเชื่อมต่อเพิ่มเติม [เรียนรู้เพิ่มเติมเกี่ยวกับ Logic Apps](https://azure.microsoft.com/services/app-service/logic/)

### <a name="how-does-microsoft-flow-fit-in-microsofts-overall-business-application-platform-strategy"></a>Microsoft Flow สามารถใช้งานได้ในกลยุทธ์แพลตฟอร์มการใช้งานทางธุรกิจโดยรวมของ Microsoft อย่างไร?
Microsoft Flow เป็นส่วนหนึ่งของแพลตฟอร์มการใช้งานทางธุรกิจที่ทรงประสิทธิภาพที่มีทั้ง PowerApps, Common Data Service, Dynamics 365 และ Office 365 แพลตฟอร์มนี้ช่วยให้ลูกค้า คู่ค้า และคู่ค้า ISV ของเราสามารถสร้างโซลูชันตามวัตถุประสงค์สำหรับบริษัทของตน อุตสาหกรรมของตน สำหรับบทบาทการทำงาน หรือแม้กระทั่งสำหรับภูมิศาสตร์เฉพาะได้ ผู้ใช้งานทางธุรกิจที่เข้าใจความต้องการทางธุรกิจของตนที่ดีที่สุด ตอนนี้สามารถวิเคราะห์ เขียน และปรับปรุงประสิทธิภาพข้อมูลและกระบวนการต่าง ๆ ของตนได้อย่างง่ายดาย นักพัฒนามืออาชีพสามารถขยายกระบวนการอัตโนมัติ การวิเคราะห์ และแอปสำหรับธุรกิจเพื่อใช้ประโยชน์จากบริการต่าง ๆ ของ Azure ได้อย่างง่ายดาย เช่น Functions, App Service และ Logic Apps ตัวเชื่อมต่อ API เกตเวย์ และ Microsoft Common Data Service ช่วยให้คุณได้คุณค่ามากขึ้นจากบริการหรือข้อมูลที่มีใช้อยู่แล้ว ทั้งในระบบคลาวด์หรือภายในองค์กร

## <a name="functionality"></a>การทำงาน
### <a name="what-do-i-need-to-use-microsoft-flow"></a>ฉันต้องมีอะไรบ้างในการใช้งาน Microsoft Flow?
ในการใช้งาน Microsoft Flow สิ่งที่คุณต้องมีคือเว็บเบราว์เซอร์และอีเมล

### <a name="what-browsers-and-devices-can-i-use-with-microsoft-flow"></a>ฉันสามารถใช้เบราว์เซอร์และอุปกรณ์ใดกับ Microsoft Flow ได้บ้าง

คุณสามารถเรียกใช้ Microsoft Flow บนอุปกรณ์และเบราว์เซอร์ที่ทันสมัยได้

#### <a name="supported-devices"></a>อุปกรณ์ต่าง ๆ ที่สนับสนุน

Microsoft Flow ทำงานยอดเยี่ยมบนอุปกรณ์ที่ทันสมัย ถ้าคุณต้องการจัดการ Microsoft Flow จากอุปกรณ์เคลื่อนที่ ให้ลองแอป Microsoft Flow สำหรับอุปกรณ์เคลื่อนที่ ที่พร้อมใช้งานบน [iPhone](https://itunes.apple.com/app/microsoft-flow/id1094928825?ls=1&mt=8), [Android](https://play.google.com/store/apps/details?id=com.microsoft.flow) และ [Windows Phone](https://www.microsoft.com/p/microsoft-flow/9nkn0p5l9n84?rtc=1#activetab=pivot:overviewtab)

#### <a name="supported-browsers"></a>เบราว์เซอร์ที่สนับสนุน

เราขอแนะนำให้คุณใช้เบราว์เซอร์ล่าสุดที่สามารถใช้ได้กับระบบปฏิบัติการของคุณ เราสนับสนุนเบราว์เซอร์ต่อไปนี้:

* Microsoft Edge
* Internet Explorer 11
* Safari
* Chrome
* Firefox

### <a name="which-email-addresses-are-supported"></a>ที่อยู่อีเมลใดที่สนับสนุน?
Microsoft Flow สนับสนุนที่อยู่อีเมลที่ลงท้ายด้วยอะไรก็ได้ ยกเว้น .gov และ .mil  

### <a name="is-microsoft-flow-available-on-premises"></a>Microsoft Flow ใช้งานได้ภายในองค์กรได้อหรือไม่?
Microsoft Flow เป็นบริการระบบคลาวด์สาธารณะเท่านั้น อย่างไรก็ตาม คุณสามารเชื่อมต่อกับบริการภายในองค์กรของคุณเองผ่านทางเกตเวย์ข้อมูลภายในองค์กรได้อย่างปลอดภัย

### <a name="what-services-can-microsoft-flow-connect-to"></a>บริการใดที่ Microsoft Flow สามารถเชื่อมต่อได้?
Microsoft Flow เชื่อมต่อกับแหล่งข้อมูลมากกว่า 100 แหล่งที่ใช้งานได้ในทันที และเราเพิ่มแหล่งข้อมูลอยู่ตลอดเวลา ตัวอย่างบางส่วนของแหล่งข้อมูลและบริการมีดังนี้:

* SharePoint
* Dynamics 365
* OneDrive
* OneDrive for Business
* Google Drive
* Google Sheets
* Trello
* Twitter
* Box
* Facebook
* SalesForce.com
* Mailchimp
* API ลูกค้า

คุณสามารถค้นหารายการทั้งหมดของตัวเชื่อมต่อที่พร้อมใช้งานได้[ที่นี่](https://go.microsoft.com/fwlink/?LinkId=832211)

คุณสามารถเข้าถึงแหล่งข้อมูลในโครงสร้างพื้นฐานด้าน IT ของคุณเองได้ผ่านทาง[เกตเวย์ข้อมูลภายในองค์กร](gateway-manage.md)

### <a name="what-are-templates"></a>เทมเพลตคืออะไร?
เทมเพลตเป็นโฟลว์ที่สร้างไว้ล่วงหน้าสำหรับสถานการณ์สมมติทั่วไปและได้รับความนิยม ในการใช้เทมเพลตนั้น คุณเพียงจำเป็นต้องเข้าถึงบริการในเทมเพลตและกรอกข้อมูลการตั้งค่าที่จำเป็น

### <a name="what-data-sources-will-i-be-able-to-connect-to"></a>ฉันจะสามารถเชื่อมต่อกับแหล่งข้อมูลใดบ้าง?
คุณสามารถเชื่อมต่อกับบริการมาตรฐานมากกว่า 100 บริการจาก Microsoft และบริษัทบุคคลที่สาม เช่น Office 365, Twitter, SharePoint, OneDrive, Dropbox, SQL Server และอื่น ๆ นอกจากนี้ คุณยังสามารถเชื่อมต่อกับบริการแบบพรีเมียม เช่น Salesforce และ Common Data Service สำหรับ PowerApps ได้

### <a name="how-do-i-connect-to-a-rest-api-in-my-flow"></a>ฉันสามารถเชื่อมต่อกับ REST API ในโฟลว์ของฉันได้อย่างไร?
คุณสามารถเชื่อมต่อกับ REST API ใด ๆ ที่ใช้ JSON และสนับสนุนอย่างน้อยหนึ่งวิธีการรับรองความถูกต้องจากจำนวนมากกว่า 10 วิธี ได้โดยการสร้าง[ตัวเชื่อมต่อแบบกำหนดเอง](developer/register-custom-api.md)

### <a name="how-do-i-connect-to-sql-server-and-other-on-premises-data-sources"></a>ฉันสามารถเชื่อมต่อกับ SQL Server และแหล่งข้อมูลอื่น ๆ ภายในองค์กรได้อย่างไร?
คุณสามารถเชื่อมต่อกับบริการบนเครือข่ายในเครื่องของคุณได้โดยใช้[เกตเวย์ข้อมูลภายในองค์กร](gateway-manage.md)

### <a name="can-i-share-the-flows-i-create"></a>ฉันสามารถแชร์โฟลว์ที่ฉันสร้างได้หรือไม่?
คุณสามารถแชร์โฟลว์ได้โดยใช้หนึ่งในวิธีต่อไปนี้:

* คุณสามารถเพิ่มเพื่อนร่วมงานหรือกลุ่มในองค์กรของคุณเป็นเจ้าของบนโฟลว์ของคุณได้ เพื่อให้บุคคลดังกล่าวสามารถแก้ไข และจัดการโฟลว์ได้ด้วยเช่นกัน
* สำหรับโฟลว์ที่สามารถเปิดใช้งานได้ด้วยตนเอง คุณสามารถอนุญาตให้บุคคลอื่นหรือกลุ่มในสิทธิ์การใช้งานในองค์กรของคุณแค่เรียกใช้โฟลว์ได้เท่านั้นได้

### <a name="how-many-flows-can-i-have"></a>ฉันสามารถมีโฟลว์ได้มากแค่ไหน?
Microsoft Flow มาพร้อมกับโฟลว์สูงสุด 50 โฟลว์ ถ้าคุณต้องการเพิ่ม คุณสามารถร้องขอโฟลว์เพิ่มได้

### <a name="where-do-i-get-started-with-microsoft-flow"></a>ฉันสามารถเริ่มต้นใช้งาน Microsoft Flow ได้จากจุดไหน?
เริ่มต้นใช้งานด้วยทรัพยากรต่อไปนี้:

* [Blog](https://flow.microsoft.com)
* [แชนเนล YouTube](https://youtube.com/playlist?list=PL8nfc9haGeb55I9wL9QnWyHp3ctU2_ThF)
* [หัวข้อ](getting-started.md)
* [ชุมชน](https://powerusers.microsoft.com)

### <a name="what-operating-systems-does-the-mobile-app-for-microsoft-flow-support"></a>ระบบปฏิบัติการใดที่แอปอุปกรณ์เคลื่อนที่สำหรับ Microsoft Flow สนับสนุน?
แอปอุปกรณ์เคลื่อนที่ Microsoft Flow สามารถใช้งานได้บน [Android](https://aka.ms/flowmobiledocsandroid), [iOS](https://aka.ms/flowmobiledocsios) หรือ [Windows Phone](https://aka.ms/flowmobilewindows)

### <a name="can-flows-be-turned-off-or-disabled"></a>สามารถปิดหรือปิดใช้งานโฟลว์ได้หรือไม่?

ได้ แต่ละโฟลว์จะมีปุ่มเปิด/ปิดที่ช่วยให้คุณสามารถหยุดโฟลว์จากการประมวลผลคำขอได้

ดูตารางต่อไปนี้เพื่อทำความเข้าใจวิธีการที่โฟลว์ของคุณตอบสนองเมื่อเปิดกลับมาใช้อีกครั้ง

ชนิดทริกเกอร์|คำอธิบาย
-------|--------
การสำรวจ เช่น ทริกเกอร์**ที่เกิดซ้ำ**|เมื่อโฟลว์ถูกเปิดใช้งานอีกครั้ง ระบบจะประมวลผลเหตุการณ์ที่ยังไม่ได้ประมวลผล/รอการประมวลผลทั้งหมด
Webhook|เมื่อโฟลว์ถูกเปิดใช้งานอีกครั้ง ระบบจะประมวลผลเฉพาะเหตุการณ์ใหม่ที่สร้างขึ้นหลังจากโฟลว์ถูกเปิดใช้งาน

### <a name="what-regions-and-languages-does-microsoft-flow-support"></a>ภูมิภาคใดและภาษาอะไรที่ Microsoft Flow รองรับ?
Microsoft Flow ใช้งานได้ใน 42 ภาษาและใน [6 ภูมิภาค](regions-overview.md)

### <a name="how-does-microsoft-flow-compare-to-sharepoint-designer-2013"></a>เราสามารถเปรียบเทียบ Microsoft Flow กับ SharePoint Designer 2013 ได้อย่างไร?
Microsoft Flow เป็นรุ่นหลังจาก SharePoint Designer สำหรับสถานการณ์สมมติทางธุรกิจทั่วไปหลายสถานการณ์ เช่น การอนุมัติ การตรวจทานเอกสาร และการเข้าร่วมทำงาน/การไม่เข้าร่วมทำงาน ซึ่งจะเป็นเครื่องมือมาตรฐานสำหรับการสร้างกระบวนการอัตโนมัติทางธุรกิจใน SharePoint ต่อไป

### <a name="how-does-microsoft-flow-ensure-that-corporate-data-isnt-accidentally-released-to-social-media-services"></a>Microsoft Flow จะทำอย่างไรเพื่อให้แน่ใจว่าข้อมูลขององค์กรจะไม่ถูกเผยแพร่ไปยังสื่อทางสังคมออนไลน์โดยไม่ตั้งใจ?่
ผู้ดูแลระบบสามารถสร้าง[นโยบายป้องกันการสูญหายของข้อมูล](prevent-data-loss.md)เพื่อให้แน่ใจว่าเฉพาะบริการที่ได้รับอนุมัติเท่านั้นที่ใช้ใน Microsoft Flow ได้

### <a name="does-microsoft-flow-support-service-accounts"></a>Microsoft Flow สนับสนุนบัญชีบริการหรือไม่

แม้ว่าคุณจะสามารถสร้างโฟลว์ข้อมูลด้วยบัญชีบริการ แต่เราไม่แนะนำให้ทำเช่นนี้หากมีการแชร์ข้อมูลประจำตัวของบัญชีบริการ

## <a name="licensing"></a>การให้สิทธิ์การใช้งาน
### <a name="will-microsoft-flow-still-have-a-free-or-trial-option"></a>Microsoft Flow จะยังคงมีตัวเลือกฟรีหรือตัวเลือกทดลองใช้หรือไม่?
มี คุณสามารถใช้ข้อเสนอฟรีของเราได้ ซึ่งมีการจำกัดสิทธิ์ของผู้ใช้ หรือคุณสามารถลงทะเบียนเพื่อทดลองใช้แผน 90 วันฟรีของ Microsoft Flow ได้ คุณสามารถเปิดใช้งานการลงทะเบียนได้ตลอดเวลาในระหว่างการทดลองใช้ของคุณ

### <a name="what-pricing-plans-do-you-offer"></a>คุณนำเสนอแผนราคาใด?
Microsoft Flow มีบริการทั้งสองระดับนั่นคือ บริการฟรีและแบบชำระเงิน [เรียนรู้เพิ่มเติมเกี่ยวกับการกำหนดราคา](billing-questions.md)

## <a name="learn-more"></a>เรียนรู้เพิ่มเติม

* ดู[การเรียนรู้แบบให้คำแนะนำ](https://docs.microsoft.com/learn/paths/automate-process-using-flow)ของ Microsoft Flow
* เรียนรู้พื้นฐานของ Microsoft Flow ใน[แนวทางการเริ่มต้นใช้งาน](getting-started.md)
