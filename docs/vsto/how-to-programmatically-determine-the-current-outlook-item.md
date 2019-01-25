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
ms.openlocfilehash: e72928c6244ba15a96bdedd7aba6b59c1e50e708
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875098"
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
 [Model obiektu Outlook ― omówienie](../vsto/outlook-object-model-overview.md)   
 [Instrukcje: Programowe pobieranie folderu według nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Instrukcje: Programowe wyszukiwanie określonego kontaktu](../vsto/how-to-programmatically-search-for-a-specific-contact.md)  
