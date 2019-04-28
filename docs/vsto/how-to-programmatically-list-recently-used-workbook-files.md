---
title: 'Instrukcje: Programowe listy ostatnio używanych plików skoroszytu'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 954a106b87d0ee941aa9c3a6c9c35579d1cb3d54
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62812537"
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Instrukcje: Programowe listy ostatnio używanych plików skoroszytu
  <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> Właściwość zwraca kolekcję zawierającą nazwy wszystkich plików, które pojawiają się na liście ostatnio używanych plików programu Microsoft Office Excel. Długość listy różni się zależnie od liczby plików wybranych do zachowania. Możesz wyświetlić wyniki w zakresie.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Do listy ostatnio używanych skoroszytów w obiekt zakresu

1. W pętli poprzez listy ostatnio używanych plików i wyświetlić nazwy w komórkach względem <xref:Microsoft.Office.Interop.Excel.Range> obiektu.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]

## <a name="see-also"></a>Zobacz także
- [Praca ze skoroszytami](../vsto/working-with-workbooks.md)
- [Namedrange — formant](../vsto/namedrange-control.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
