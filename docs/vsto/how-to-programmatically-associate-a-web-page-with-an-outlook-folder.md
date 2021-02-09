---
title: Kojarzenie strony sieci Web z folderem programu Outlook
description: Dowiedz się, jak skojarzyć stronę sieci Web z folderem Microsoft Office Outlook. Ten przykład umożliwia sprawdzenie folderu o nazwie HtmlView w programie Outlook.
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
ms.openlocfilehash: 35fad43f78d654cfaf9e06c1f432c620da830dd4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885576"
---
# <a name="associate-a-web-page-with-an-outlook-folder"></a>Kojarzenie strony sieci Web z folderem programu Outlook

  Ten przykład umożliwia sprawdzenie folderu o nazwie `HtmlView` w Microsoft Office Outlook. Jeśli folder nie istnieje, kod tworzy folder i przypisuje do niego stronę sieci Web. Jeśli folder istnieje, w kodzie zostanie wyświetlona zawartość folderu.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Przykład
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]

## <a name="see-also"></a>Zobacz także
- [Pracuj z folderami](../vsto/working-with-folders.md)
- [Instrukcje: programowe pobieranie folderu według nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Instrukcje: Programowane tworzenie niestandardowych elementów folderów](../vsto/how-to-programmatically-create-custom-folder-items.md)
