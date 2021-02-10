---
title: 'Instrukcje: programowe Określanie bieżącego elementu programu Outlook'
description: Dowiedz się, jak można programowo określić bieżący element programu Microsoft Outlook. W tym przykładzie jest stosowane zdarzenie Explorer. SelectionChange.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 720028528c036bf4485ca529f735fd26b1ff6e9e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963838"
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
