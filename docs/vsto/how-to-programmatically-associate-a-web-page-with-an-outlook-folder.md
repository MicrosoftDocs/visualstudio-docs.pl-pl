---
title: Kojarzenie strony internetowej z folderem programu Outlook
description: Dowiedz się, jak skojarzyć stronę internetową z Microsoft Office programu Outlook. W tym przykładzie jest sprawdzany folder o nazwie HtmlView w programie Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- folders [Office development in Visual Studio], Web pages and
- Outlook [Office development in Visual Studio], Web pages attached to folders
- Web pages [Office development in Visual Studio], Outlook folders
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3f022deca9b8cd1b8f00bf847ab0bfdc7882a45f
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828270"
---
# <a name="associate-a-web-page-with-an-outlook-folder"></a>Kojarzenie strony internetowej z folderem programu Outlook

  Ten przykład sprawdza folder o nazwie w `HtmlView` programie Microsoft Office Outlook. Jeśli folder nie istnieje, kod tworzy folder i przypisuje do niego stronę internetową. Jeśli folder istnieje, kod wyświetla zawartość folderu.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Przykład
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs" id="Snippet1":::

## <a name="see-also"></a>Zobacz także
- [Praca z folderami](../vsto/working-with-folders.md)
- [How to: Programowe pobieranie folderu według nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [How to: Programowe tworzenie niestandardowych elementów folderów](../vsto/how-to-programmatically-create-custom-folder-items.md)
