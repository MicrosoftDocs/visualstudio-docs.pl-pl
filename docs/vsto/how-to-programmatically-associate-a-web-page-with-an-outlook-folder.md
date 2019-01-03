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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1950a75eeee6f99a03346dde53317b30824a35f4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990662"
---
# <a name="how-to-programmatically-associate-a-web-page-with-an-outlook-folder"></a>Instrukcje: Programowe kojarzenie strony internetowej z folderem programu Outlook
  W tym przykładzie wyszukuje folder o nazwie `HtmlView` w programie Microsoft Office Outlook. Jeśli folder nie istnieje, kod tworzy folder i przypisuje do strony sieci Web. Jeśli folder istnieje, kod wyświetla zawartość folderu.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Zobacz także  
 [Praca z folderami](../vsto/working-with-folders.md)   
 [Instrukcje: Programowe pobieranie folderu według nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Instrukcje: Programowe tworzenie niestandardowych elementów folderu](../vsto/how-to-programmatically-create-custom-folder-items.md)  
