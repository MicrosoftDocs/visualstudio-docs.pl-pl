---
title: 'How to: Programmatically list recently used workbook files (2017: Programowe udostępnianie listy ostatnio używanych plików skoroszytu)'
description: Dowiedz się, jak programowo wyświetlić ostatnio używane pliki skoroszytów programu Microsoft Excel przy użyciu Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing recently used
- RecentFiles property
- Excel [Office development in Visual Studio], recently used files listing
- recent file list, Excel
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ba7ca717af4330e8fb3c102b3a5fe5bf7d9162b6
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825332"
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>How to: Programmatically list recently used workbook files (2017: Programowe udostępnianie listy ostatnio używanych plików skoroszytu)
  Właściwość zwraca kolekcję zawierającą nazwy wszystkich plików, które są wyświetlane na liście <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> Microsoft Office Excel ostatnio używanych plików. Długość listy różni się w zależności od liczby plików wybranych przez użytkownika do zachowania. Wyniki można wyświetlić w zakresie.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Aby wyświetlić listę ostatnio używanych skoroszytów w obiekcie zakresu

1. Zapętla listę ostatnich plików i wyświetla nazwy w komórkach względem <xref:Microsoft.Office.Interop.Excel.Range> obiektu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet9":::

## <a name="see-also"></a>Zobacz też
- [Praca ze skoroszytami](../vsto/working-with-workbooks.md)
- [NamedRange, kontrolka](../vsto/namedrange-control.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
