---
title: Programowo Zapisuj załączniki z elementów poczty e-mail programu Outlook
description: Dowiedz się, jak za pomocą programu Visual Studio programistycznie zapisywać załączniki z elementów poczty e-mail programu Microsoft Outlook.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: d33c2c820f03d7fb40c953165f62943e44648082
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528246"
---
# <a name="how-to-programmatically-save-attachments-from-outlook-email-items"></a>Instrukcje: programowe zapisywanie załączników z elementów poczty e-mail programu Outlook

Ten przykład zapisuje załączniki wiadomości e-mail do określonego folderu po odebraniu wiadomości w skrzynce odbiorczej.

> [!IMPORTANT]
> Ten przykład działa tylko w przypadku dodania folderu o nazwie **TestFileSave** w katalogu głównym katalogu C.

[!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Przykład

[!code-csharp[Trin_OL_SaveAttachments#1](../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs#1)]

## <a name="see-also"></a>Zobacz także

- [Pracuj z elementami poczty](../vsto/working-with-mail-items.md)
- [Instrukcje: programowe pobieranie folderu według nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Instrukcje: Programowane wykonywanie akcji po otrzymaniu wiadomości e-mail](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
- [Instrukcje: programowe wyszukiwanie w określonym folderze](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
