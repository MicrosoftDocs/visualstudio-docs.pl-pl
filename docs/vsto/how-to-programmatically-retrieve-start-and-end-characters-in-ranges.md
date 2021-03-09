---
title: Programowe pobieranie &ch znaków końcowych w zakresach
description: W tym przykładzie pokazano, jak można pobrać pozycje znaku początku i końca zakresu.
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 98c550adf60dd92b8b6d99cb82cedcbe0136c551
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2021
ms.locfileid: "102470095"
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>Instrukcje: programowe pobieranie znaków początkowych i końcowych w zakresach
  W tym przykładzie pokazano, jak można pobrać pozycje znaku początku i końca zakresu.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>Aby pobrać znaki początkowe i końcowe zakresu w dostosowaniu na poziomie dokumentu

1. Pobierz wartości <xref:Microsoft.Office.Interop.Word.Range.Start%2A> <xref:Microsoft.Office.Interop.Word.Range.End%2A> właściwości i <xref:Microsoft.Office.Interop.Word.Range> obiektu. Poniższy przykład kodu pobiera początkową i końcową pozycję drugiego zdania w dokumencie. Aby użyć tego przykładu kodu, należy uruchomić go z `ThisDocument` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#25)]

## <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-a-vsto-add-in"></a>Aby pobrać znaki początkowe i końcowe zakresu przy użyciu dodatku VSTO

1. Pobierz wartości <xref:Microsoft.Office.Interop.Word.Range.Start%2A> <xref:Microsoft.Office.Interop.Word.Range.End%2A> właściwości i <xref:Microsoft.Office.Interop.Word.Range> obiektu. Poniższy przykład kodu pobiera początkową i końcową pozycję drugiego zdania w aktywnym dokumencie. Aby użyć tego przykładu kodu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#25)]

## <a name="see-also"></a>Zobacz też
- [Instrukcje: programowe Definiowanie i wybieranie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Instrukcje: Programowane poszerzanie zakresów w dokumentach](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Instrukcje: Programowane Resetowanie zakresów w dokumentach programu Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Instrukcje: programowe zwijanie zakresów lub zaznaczenia w dokumentach](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Instrukcje: Programowane wykluczanie znaczników akapitu podczas tworzenia zakresów](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
- [Instrukcje: Programowane zliczanie znaków w dokumentach](../vsto/how-to-programmatically-count-characters-in-documents.md)
