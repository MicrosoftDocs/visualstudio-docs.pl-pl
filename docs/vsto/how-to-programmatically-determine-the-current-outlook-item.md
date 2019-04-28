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
ms.openlocfilehash: 5566538b428502c8e63e752463b0271daeac2918
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62814822"
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Instrukcje: Programowe wyznaczanie bieżącego elementu programu Outlook
  W tym przykładzie użyto `Explorer.SelectionChange` zdarzenie, aby wyświetlić nazwę bieżącego folderu i niektóre informacje na temat wybranego elementu. Ten kod wyświetla wybrany element.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Przykład
 [!code-vb[Trin_OL_CurrentItem#1](../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb#1)]
 [!code-csharp[Trin_OL_CurrentItem#1](../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Skompilować kod
 Ten przykład wymaga:

- Termin, skontaktuj się z pomocą i elementów poczty e-mail w programie Microsoft Office Outlook.

## <a name="see-also"></a>Zobacz także
- [Model obiektu Outlook ― omówienie](../vsto/outlook-object-model-overview.md)
- [Instrukcje: Programowe pobieranie folderu według nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Instrukcje: Programowe wyszukiwanie określonego kontaktu](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
