---
title: 'How to: Programowe wyszukiwanie w określonym folderze'
description: Dowiedz się, jak używać Visual Studio do programowego wyszukiwania w określonym folderze programu Microsoft Outlook.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b25880420e23b82f6f63ab28ef5f1f93429bdd8c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824760"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>How to: Programowe wyszukiwanie w określonym folderze
  W tym przykładzie kodu użyto metod i do wyszukiwania tekstu w polu tematu wiadomości `Find` `FindNext` e-mail, które znajdują się w **skrzynce odbiorczej**. Ta metoda używa filtru ciągu, aby sprawdzić literę T jako literę początkową `Subject` tekstu.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Przykład
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs" id="Snippet1":::

## <a name="see-also"></a>Zobacz także
- [Praca z folderami](../vsto/working-with-folders.md)
- [Omówienie modelu obiektów programu Outlook](../vsto/outlook-object-model-overview.md)
- [How to: Programowe pobieranie folderu według nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
