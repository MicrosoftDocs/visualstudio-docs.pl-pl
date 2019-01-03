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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 850dc26b9a5f270b3806d9623795535d34cf8f4b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989636"
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Instrukcje: Programowe listy ostatnio używanych plików skoroszytu
  <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> Właściwość zwraca kolekcję zawierającą nazwy wszystkich plików, które pojawiają się na liście ostatnio używanych plików programu Microsoft Office Excel. Długość listy różni się zależnie od liczby plików wybranych do zachowania. Możesz wyświetlić wyniki w zakresie.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Do listy ostatnio używanych skoroszytów w obiekt zakresu  
  
1.  W pętli poprzez listy ostatnio używanych plików i wyświetlić nazwy w komórkach względem <xref:Microsoft.Office.Interop.Excel.Range> obiektu.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>Zobacz także  
 [Praca ze skoroszytami](../vsto/working-with-workbooks.md)   
 [Namedrange — formant](../vsto/namedrange-control.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)  
