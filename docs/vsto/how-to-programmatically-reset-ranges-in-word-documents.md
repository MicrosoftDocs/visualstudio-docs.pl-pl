---
title: 'How to: Programowe resetowanie zakresów w dokumentach programu Word'
description: Dowiedz się, jak za pomocą Visual Studio programowo zmienić rozmiar istniejącego zakresu w dokumencie programu Microsoft Word.
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
ms.openlocfilehash: ae3b8f92231b77d81c1ef68e0929ccd000653b14
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824149"
---
# <a name="how-to-programmatically-reset-ranges-in-word-documents"></a>How to: Programowe resetowanie zakresów w dokumentach programu Word
  Użyj metody <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> , aby zmienić rozmiar istniejącego zakresu w Microsoft Office word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-reset-an-existing-range"></a>Aby zresetować istniejący zakres

1. Ustaw początkowy zakres, zaczynając od pierwszych siedmiu znaków w dokumencie.

     Poniższy przykład kodu może służyć do dostosowywania na poziomie dokumentu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet43":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet43":::

     Poniższy przykład kodu może być używany w dodatku VSTO. Ten kod używa aktywnego dokumentu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet43":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet43":::

2. Użyj , aby rozpocząć zakres od drugiego zdania i zakończyć <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> go na końcu piątego zdania.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet44":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet44":::

## <a name="document-level-customization-example"></a>Document-Level przykład dostosowywania

### <a name="to-reset-an-existing-range-in-a-document-level-customization"></a>Aby zresetować istniejący zakres w dostosowywaniu na poziomie dokumentu

1. W poniższym przykładzie przedstawiono kompletny przykład dostosowywania na poziomie dokumentu. Aby użyć tego kodu, uruchom go z `ThisDocument` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet42":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet42":::

## <a name="vsto-add-in-example"></a>Przykład dodatku VSTO

### <a name="to-reset-an-existing-range-in-a-vsto-add-in"></a>Aby zresetować istniejący zakres w dodatku VSTO

1. W poniższym przykładzie przedstawiono kompletny przykład dodatku VSTO. Aby użyć tego kodu, uruchom go z `ThisAddIn` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet42":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet42":::

## <a name="see-also"></a>Zobacz też
- [Jak programowo rozszerzyć zakresy w dokumentach](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Jak programowo definiować i wybierać zakresy w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [How to: Programowe pobieranie znaków początku i końca w zakresach](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Jak programowo zwinąć zakresy lub wybory w dokumentach](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
