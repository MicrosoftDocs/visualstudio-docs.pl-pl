---
title: Kojarzenie strony sieci Web z folderem programu Outlook
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 35eb2dc3b1b595a4bf960af67ac5006cd9839c6e
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585343"
---
# <a name="associate-a-web-page-with-an-outlook-folder"></a>Kojarzenie strony sieci Web z folderem programu Outlook

  Ten przykład umożliwia sprawdzenie folderu o nazwie `HtmlView` w Microsoft Office Outlook. Jeśli folder nie istnieje, kod tworzy folder i przypisuje do niego stronę sieci Web. Jeśli folder istnieje, w kodzie zostanie wyświetlona zawartość folderu.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Przykład
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]

## <a name="see-also"></a>Zobacz też
- [Pracuj z folderami](../vsto/working-with-folders.md)
- [Instrukcje: programowe pobieranie folderu według nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Instrukcje: Programowane tworzenie niestandardowych elementów folderów](../vsto/how-to-programmatically-create-custom-folder-items.md)
