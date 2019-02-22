---
title: 'Instrukcje: Programowe wyznaczanie bieżącego elementu programu Outlook'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 3608f516eb9206bc5b4c232c227d3e49c2414be7
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56599756"
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Instrukcje: Programowe wyznaczanie bieżącego elementu programu Outlook
  W tym przykładzie użyto `Explorer.SelectionChange` zdarzenie, aby wyświetlić nazwę bieżącego folderu i niektóre informacje na temat wybranego elementu. Ten kod wyświetla wybrany element.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Przykład
 [!code-vb[Trin_OL_CurrentItem#1](../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb#1)]
 [!code-csharp[Trin_OL_CurrentItem#1](../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Skompilować kod
 Ten przykład wymaga:

-   Termin, skontaktuj się z pomocą i elementów poczty e-mail w programie Microsoft Office Outlook.

## <a name="see-also"></a>Zobacz także
- [Model obiektu Outlook ― omówienie](../vsto/outlook-object-model-overview.md)
- [Instrukcje: Programowe pobieranie folderu według nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Instrukcje: Programowe wyszukiwanie określonego kontaktu](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
