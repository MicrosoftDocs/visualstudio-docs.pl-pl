---
title: Jak programowo przenosić elementy w programie Outlook
description: Dowiedz się, jak programowo przenosić elementy w programie Microsoft Outlook. W tym przykładzie nieprzeczytane wiadomości e-mail są przenosine ze skrzynki odbiorczej do folderu o nazwie Test.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b8e951ab393d09506ad4f2d593962ea1826eff09
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826736"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Jak programowo przenosić elementy w programie Outlook
  W tym przykładzie nieprzeczytane wiadomości e-mail są przenoszyne ze **skrzynki** odbiorczej do folderu o nazwie **Test**. Przykład przenosi tylko komunikaty, które mają **słowo Test** w `Subject` polu .

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Przykład
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Kompilowanie kodu
 Ten przykład wymaga:

- Folder poczty programu Outlook o nazwie **Test**.

- Wiadomość e-mail z wyrazem **Test** w `Subject` polu.

## <a name="see-also"></a>Zobacz też
- [Praca z folderami](../vsto/working-with-folders.md)
- [How to: Programowe pobieranie folderu według nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [How to: Programowe wyszukiwanie w określonym folderze](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Dzieje się tak: Programowe wykonywanie akcji po otrzymaniu wiadomości e-mail](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
