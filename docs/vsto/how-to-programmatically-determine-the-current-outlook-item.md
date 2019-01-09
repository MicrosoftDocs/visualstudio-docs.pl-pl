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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7ed0a235a24b65b89a1b82ec47236f3f013f81dc
ms.sourcegitcommit: 73861cd0ea92e50a3be1ad2a0ff0a7b07b057a1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54153973"
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
