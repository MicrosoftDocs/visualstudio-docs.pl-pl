---
title: Programowe zapisywanie załączników z elementów wiadomości e-mail programu Outlook
description: Dowiedz się, jak za pomocą Visual Studio programowo zapisywać załączniki z elementów poczty e-mail programu Microsoft Outlook.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ad64593f91e14bcfd993929420764869a8359e3e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826697"
---
# <a name="how-to-programmatically-save-attachments-from-outlook-email-items"></a>Jak programowo zapisywać załączniki z elementów poczty e-mail programu Outlook

W tym przykładzie załączniki wiadomości e-mail są zapisywane w określonym folderze po otrzymaniu wiadomości e-mail w skrzynce odbiorczej.

> [!IMPORTANT]
> Ten przykład działa tylko wtedy, gdy dodasz folder o nazwie **TestFileZave** w katalogu głównym katalogu C.

[!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Przykład

:::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs" id="Snippet1":::

## <a name="see-also"></a>Zobacz także

- [Praca z elementami poczty](../vsto/working-with-mail-items.md)
- [How to: Programowe pobieranie folderu według nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Dzieje się tak: Programowe wykonywanie akcji po otrzymaniu wiadomości e-mail](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
- [How to: Programowe wyszukiwanie w określonym folderze](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
