---
title: 'Instrukcje: Programowe Resetowanie zakresów w dokumentach programu Word'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], resetting ranges
- ranges, resetting in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 622d807da832c4c07baf8b62c902c2b1d25cc14d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955705"
---
# <a name="how-to-programmatically-reset-ranges-in-word-documents"></a>Instrukcje: Programowe Resetowanie zakresów w dokumentach programu Word
  Użyj <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> metodę, aby zmienić rozmiar istniejącej zakresu w dokumencie programu Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-reset-an-existing-range"></a>Aby zresetować istniejący zakres

1. Ustaw początkowy zakresu, począwszy od pierwszych siedem znaków w dokumencie.

     Poniższy przykład kodu może służyć w dostosowaniu na poziomie dokumentu.

     [!code-vb[Trin_VstcoreWordAutomation#43](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#43)]
     [!code-csharp[Trin_VstcoreWordAutomation#43](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#43)]

     Poniższy przykład kodu może służyć w dodatku VSTO. Ten kod używa aktywnego dokumentu.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#43](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#43)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#43](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#43)]

2. Użyj <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> Rozpocznij zakres przy drugie zdanie i kończyć się na końcu piąty zdania.

     [!code-vb[Trin_VstcoreWordAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#44)]
     [!code-csharp[Trin_VstcoreWordAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#44)]

## <a name="document-level-customization-example"></a>Przykład dostosowania na poziomie dokumentu

### <a name="to-reset-an-existing-range-in-a-document-level-customization"></a>Aby zresetować istniejący zakres w dostosowaniu na poziomie dokumentu

1. Poniższy przykład pokazuje kompletny przykład dla dostosowywania poziomie dokumentu. Aby użyć tego kodu, należy uruchomić go z `ThisDocument` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#42](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#42)]
     [!code-csharp[Trin_VstcoreWordAutomation#42](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#42)]

## <a name="vsto-add-in-example"></a>Przykładu dodatku narzędzi VSTO

### <a name="to-reset-an-existing-range-in-a-vsto-add-in"></a>Aby zresetować istniejący zakres w dodatku narzędzi VSTO

1. Poniższy przykład pokazuje kompletny przykład dodatku narzędzi VSTO dla programów. Aby użyć tego kodu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#42](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#42)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#42](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#42)]

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Programowe rozszerzanie zakresów w dokumentach](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Instrukcje: Programowe definiowanie i zaznaczanie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Instrukcje: Programowe pobieranie znaków początkowych i końcowych w zakresach](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Instrukcje: Programowe zwijanie zakresów lub zaznaczenia w dokumentach](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
