---
title: 'Instrukcje: Programowe zapisywanie załączników z elementów poczty e-mail programu Outlook'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], attachments
- e-mail [Office development in Visual Studio], attachments
- saving e-mail attachments
- mail items [Office development in Visual Studio], attachments
- attachments [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ec543a23a68965c0fa629d7318f40e840fb81152
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53911237"
---
# <a name="how-to-programmatically-save-attachments-from-outlook-email-items"></a>Instrukcje: Programowe zapisywanie załączników z elementów poczty e-mail programu Outlook
  Ten przykład zapisuje załączniki wiadomości e-mail do określonego folderu, po odebraniu wiadomości e-mail w skrzynce odbiorczej.  
  
> [!IMPORTANT]  
>  Ten przykład działa tylko wtedy, gdy dodać folder o nazwie **TestFileSave** w katalogu głównym katalogu c.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Trin_OL_SaveAttachments#1](../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Zobacz także  
 [Praca z elementami poczty](../vsto/working-with-mail-items.md)   
 [Instrukcje: Programowe pobieranie folderu według nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Instrukcje: Programowe wykonywanie akcji po otrzymaniu wiadomości e-mail](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)   
 [Instrukcje: Programowe wyszukiwanie w określonym folderze](../vsto/how-to-programmatically-search-within-a-specific-folder.md)  
