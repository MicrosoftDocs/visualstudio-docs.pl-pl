---
title: 'Instrukcje: programowe Wyświetlanie listy niedawno używanych plików skoroszytu'
description: Dowiedz się, jak programowo wystawić listę ostatnio używanych plików skoroszytów programu Microsoft Excel przy użyciu programu Visual Studio.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bbcad553ade6234d3a688c8f718a0dd6e6cda509
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525635"
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Instrukcje: programowe Wyświetlanie listy niedawno używanych plików skoroszytu
  <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A>Właściwość zwraca kolekcję zawierającą nazwy wszystkich plików, które pojawiają się na liście Microsoft Office Excel ostatnio używanych plików. Długość listy różni się w zależności od liczby plików, które użytkownik wybrał do zachowania. Wyniki można wyświetlić w zakresie.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Aby wyświetlić listę ostatnio używanych skoroszytów w obiekcie zakresu

1. Przepętlenie przez listę ostatnio używanych plików i wyświetlenie nazw w komórkach odnoszących się do <xref:Microsoft.Office.Interop.Excel.Range> obiektu.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]

## <a name="see-also"></a>Zobacz też
- [Pracuj ze skoroszytami](../vsto/working-with-workbooks.md)
- [NamedRange — formant](../vsto/namedrange-control.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
