---
title: 'Instrukcje: programowe Określanie bieżącego elementu programu Outlook'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], current
- e-mail [Office development in Visual Studio], current item
- SelectionChange event
- Outlook [Office development in Visual Studio], current item
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 94d7e16b011b153a43e3d1666451a90b0e44c8b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547163"
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Instrukcje: programowe Określanie bieżącego elementu programu Outlook
  Ten przykład używa `Explorer.SelectionChange` zdarzenia, aby wyświetlić nazwę bieżącego folderu oraz pewne informacje o wybranym elemencie. Następnie kod wyświetla wybrany element.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Przykład
 [!code-vb[Trin_OL_CurrentItem#1](../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb#1)]
 [!code-csharp[Trin_OL_CurrentItem#1](../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Kompiluj kod
 Ten przykład wymaga:

- Elementy terminu, kontaktu i wiadomości e-mail w programie Microsoft Office Outlook.

## <a name="see-also"></a>Zobacz też
- [Model obiektów programu Outlook — Omówienie](../vsto/outlook-object-model-overview.md)
- [Instrukcje: programowe pobieranie folderu według nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Instrukcje: programowe wyszukiwanie określonego kontaktu](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
