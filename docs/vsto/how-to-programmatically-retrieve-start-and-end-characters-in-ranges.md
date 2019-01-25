---
title: 'Instrukcje: Programowe pobieranie znaków początkowych i końcowych w zakresach'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, retrieving start and end characters
- end characters
- start characters
- documents [Office development in Visual Studio], retrieving ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 88876641d0c6e72385d6f9e514ff8135de9518fa
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863204"
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>Instrukcje: Programowe pobieranie znaków początkowych i końcowych w zakresach
  W tym przykładzie pokazano, jak można pobrać pozycji znaku pozycji początkowej i końcowej zakresu.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>Aby pobrać znaków początkowych i końcowych zakresu w dostosowaniu na poziomie dokumentu  
  
1.  Pobierz wartości <xref:Microsoft.Office.Interop.Word.Range.Start%2A> i <xref:Microsoft.Office.Interop.Word.Range.End%2A> właściwości <xref:Microsoft.Office.Interop.Word.Range> obiektu. Poniższy przykładowy kod pobiera położenie początkowe i końcowe drugiego zdania w dokumencie. Aby wykorzystać ten przykład kodu, należy uruchomić go z `ThisDocument` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#25)]  
  
## <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-a-vsto-add-in"></a>Aby pobrać znaków początkowych i końcowych zakresu przy użyciu dodatku narzędzi VSTO  
  
1.  Pobierz wartości <xref:Microsoft.Office.Interop.Word.Range.Start%2A> i <xref:Microsoft.Office.Interop.Word.Range.End%2A> właściwości <xref:Microsoft.Office.Interop.Word.Range> obiektu. Poniższy przykładowy kod pobiera położenie początkowe i końcowe drugiego zdania w aktywnym dokumencie. Aby wykorzystać ten przykład kodu, należy uruchomić go z `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#25)]  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje: Programowe definiowanie i zaznaczanie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Instrukcje: Programowe rozszerzanie zakresów w dokumentach](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Instrukcje: Programowe Resetowanie zakresów w dokumentach programu Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Instrukcje: Programowe zwijanie zakresów lub zaznaczenia w dokumentach](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Instrukcje: Programowe wykluczanie znaczników akapitu podczas tworzenia zakresów](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [Instrukcje: Programowe zliczanie znaków w dokumentach](../vsto/how-to-programmatically-count-characters-in-documents.md)  
