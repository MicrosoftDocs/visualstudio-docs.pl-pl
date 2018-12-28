---
title: 'Instrukcje: Programowe Dodawanie i usuwanie komentarzy do arkusza'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, comments
- worksheets, comments
- comments, worksheets
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 06097d72693e0b7a00c7af48609523d5e7dfc5a0
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/27/2018
ms.locfileid: "53804198"
---
# <a name="how-to-programmatically-add-and-delete-worksheet-comments"></a>Instrukcje: Programowe Dodawanie i usuwanie komentarzy do arkusza
  Można programowo Dodawanie i usuwanie komentarzy w arkuszach programu Microsoft Office Excel. Komentarze można dodawać tylko do jednej komórki, nie do zakresów wielu komórek.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="add-and-delete-a-comment-in-a-document-level-project"></a>Dodawanie i usuwanie komentarzy w projekcie na poziomie dokumentu  
 W poniższych przykładach założono, że jest pojedynczą komórkę <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu o nazwie `dateComment` w arkuszu o nazwie `Sheet1`.  
  
### <a name="to-add-a-new-comment-to-a-named-range"></a>Aby dodać nowy komentarz do nazwany zakres  
  
1.  Wywołaj <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A> metody <xref:Microsoft.Office.Tools.Excel.NamedRange> kontroli i podać tekst komentarza. Ten kod musi być umieszczony w `Sheet1` klasy.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#30)]  
  
#### <a name="to-delete-a-comment-from-a-named-range"></a>Usuń komentarz z nazwany zakres  
  
1.  Sprawdź, czy komentarz istnieje na zakres i usuń go. Ten kod musi być umieszczony w `Sheet1` klasy.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#29)]  
  
## <a name="add-and-delete-a-comment-in-a-vsto-add-in-project"></a>Dodawanie i usuwanie komentarzy w projekcie dodatku narzędzi VSTO  
 W poniższych przykładach założono, że jest pojedynczą komórkę <xref:Microsoft.Office.Interop.Excel.Range> o nazwie `dateComment` w aktywnym arkuszu.  
  
### <a name="to-add-a-new-comment-to-an-excel-range"></a>Aby dodać nowy komentarz do zakresu programu Excel  
  
1.  Wywołaj <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A> metody <xref:Microsoft.Office.Interop.Excel.Range> i Podaj tekst komentarza.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#20)]  
  
### <a name="to-delete-a-comment-from-an-excel-range"></a>Usuń komentarz z zakresu programu Excel  
  
1.  Sprawdź, czy komentarz istnieje na zakres i usuń go.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#19)]  
  
## <a name="see-also"></a>Zobacz także  
 [Praca z arkuszami](../vsto/working-with-worksheets.md)   
 [Instrukcje: Programowe wyświetlanie komentarzy do arkusza](../vsto/how-to-programmatically-display-worksheet-comments.md)   
 [Namedrange — formant](../vsto/namedrange-control.md)  
  
  