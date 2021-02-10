---
title: 'Instrukcje: Programowane Resetowanie zakresów w dokumentach programu Word'
description: Dowiedz się, jak za pomocą programu Visual Studio programowo zmienić rozmiar istniejącego zakresu w dokumencie programu Microsoft Word.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], resetting ranges
- ranges, resetting in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 562b4dab6c26af12760190b01ff460c7080a3bb2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958781"
---
# <a name="how-to-programmatically-reset-ranges-in-word-documents"></a>Instrukcje: Programowane Resetowanie zakresów w dokumentach programu Word
  Użyj <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> metody, aby zmienić rozmiar istniejącego zakresu w dokumencie programu Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-reset-an-existing-range"></a>Aby zresetować istniejący zakres

1. Ustaw początkowy zakres zaczynający się od pierwszych siedmiu znaków w dokumencie.

     Poniższy przykład kodu może być używany w dostosowaniu na poziomie dokumentu.

     [!code-vb[Trin_VstcoreWordAutomation#43](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#43)]
     [!code-csharp[Trin_VstcoreWordAutomation#43](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#43)]

     Poniższy przykład kodu może być używany w dodatku VSTO. Ten kod używa aktywnego dokumentu.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#43](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#43)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#43](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#43)]

2. Użyj, <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> Aby rozpocząć zakres od drugiego zdania i zakończyć je na końcu piątego zdania.

     [!code-vb[Trin_VstcoreWordAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#44)]
     [!code-csharp[Trin_VstcoreWordAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#44)]

## <a name="document-level-customization-example"></a>Przykład dostosowywania Document-Level

### <a name="to-reset-an-existing-range-in-a-document-level-customization"></a>Aby zresetować istniejący zakres w dostosowaniu na poziomie dokumentu

1. Poniższy przykład pokazuje kompletny przykład dostosowywania na poziomie dokumentu. Aby użyć tego kodu, należy uruchomić go z `ThisDocument` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#42](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#42)]
     [!code-csharp[Trin_VstcoreWordAutomation#42](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#42)]

## <a name="vsto-add-in-example"></a>Przykład dodatku narzędzi VSTO

### <a name="to-reset-an-existing-range-in-a-vsto-add-in"></a>Aby zresetować istniejący zakres w dodatku narzędzi VSTO

1. Poniższy przykład pokazuje kompletny przykład dla dodatku VSTO. Aby użyć tego kodu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#42](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#42)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#42](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#42)]

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Programowane poszerzanie zakresów w dokumentach](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Instrukcje: programowe Definiowanie i wybieranie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Instrukcje: programowe pobieranie znaków początkowych i końcowych w zakresach](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Instrukcje: programowe zwijanie zakresów lub zaznaczenia w dokumentach](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
