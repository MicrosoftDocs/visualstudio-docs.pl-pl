---
title: 'Instrukcje: Programowe kojarzenie strony internetowej z folderem programu Outlook'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: e83f8b7f6bcdb790b5e545aa76426bc05f0735f5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62817312"
---
# <a name="how-to-programmatically-associate-a-web-page-with-an-outlook-folder"></a>Instrukcje: Programowe kojarzenie strony internetowej z folderem programu Outlook
  W tym przykładzie wyszukuje folder o nazwie `HtmlView` w programie Microsoft Office Outlook. Jeśli folder nie istnieje, kod tworzy folder i przypisuje do strony sieci Web. Jeśli folder istnieje, kod wyświetla zawartość folderu.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Przykład
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]

## <a name="see-also"></a>Zobacz także
- [Praca z folderami](../vsto/working-with-folders.md)
- [Instrukcje: Programowe pobieranie folderu według nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Instrukcje: Programowe tworzenie niestandardowych elementów folderu](../vsto/how-to-programmatically-create-custom-folder-items.md)
