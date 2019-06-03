---
title: 'Instrukcje: Programowe zapisywanie załączników z elementów poczty e-mail programu Outlook'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], attachments
- e-mail [Office development in Visual Studio], attachments
- saving e-mail attachments
- mail items [Office development in Visual Studio], attachments
- attachments [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d222924e753db1b476a5d7729e2c794a8ab305e2
ms.sourcegitcommit: c6249a8f3054db881ba62f4e80bf006d440f5a2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2019
ms.locfileid: "66462122"
---
# <a name="how-to-programmatically-save-attachments-from-outlook-email-items"></a>Instrukcje: Programowe zapisywanie załączników z elementów poczty e-mail programu Outlook

Ten przykład zapisuje załączniki wiadomości e-mail do określonego folderu, po odebraniu wiadomości e-mail w skrzynce odbiorczej.

> [!IMPORTANT]
> Ten przykład działa tylko wtedy, gdy dodać folder o nazwie **TestFileSave** w katalogu głównym katalogu c.

[!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Przykład

[!code-csharp[Trin_OL_SaveAttachments#1](../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs#1)]

## <a name="see-also"></a>Zobacz także

- [Praca z elementami poczty](../vsto/working-with-mail-items.md)
- [Instrukcje: Programowe pobieranie folderu według nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Instrukcje: Programowe wykonywanie akcji po otrzymaniu wiadomości e-mail](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
- [Instrukcje: Programowe wyszukiwanie w określonym folderze](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
