---
title: Programowe uzyskiwanie & znaków końcowych w zakresach
description: W tym przykładzie pokazano, jak można pobrać pozycje znaków pozycji początku i końca zakresu.
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
ms.openlocfilehash: 4739043362a0f183574959f32a6e324d03522f65
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824032"
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>How to: Programowe pobieranie znaków początku i końca w zakresach
  W tym przykładzie pokazano, jak można pobrać pozycje znaków pozycji początku i końca zakresu.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>Aby pobrać znaki początku i końca zakresu w dostosowywaniu na poziomie dokumentu

1. Pobierz wartości właściwości <xref:Microsoft.Office.Interop.Word.Range.Start%2A> <xref:Microsoft.Office.Interop.Word.Range.End%2A> i obiektu <xref:Microsoft.Office.Interop.Word.Range> . Poniższy przykład kodu pobiera pozycję początku i końca drugiego zdania w dokumencie. Aby użyć tego przykładu kodu, uruchom go z `ThisDocument` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet25":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet25":::

## <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-a-vsto-add-in"></a>Aby pobrać znaki początku i końca zakresu przy użyciu dodatku VSTO

1. Pobierz wartości właściwości <xref:Microsoft.Office.Interop.Word.Range.Start%2A> <xref:Microsoft.Office.Interop.Word.Range.End%2A> i obiektu <xref:Microsoft.Office.Interop.Word.Range> . Poniższy przykład kodu pobiera pozycję początku i końca drugiego zdania w aktywnym dokumencie. Aby użyć tego przykładu kodu, uruchom go z `ThisAddIn` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet25":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet25":::

## <a name="see-also"></a>Zobacz też
- [Jak programowo definiować i wybierać zakresy w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Pisano: Programowe rozszerzanie zakresów w dokumentach](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [How to: Programowe resetowanie zakresów w dokumentach programu Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Jak programowo zwinąć zakresy lub wybory w dokumentach](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Dzieje się tak: Programowe wykluczanie znaczników akapitu podczas tworzenia zakresów](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
- [Jak programowo zliczać znaki w dokumentach](../vsto/how-to-programmatically-count-characters-in-documents.md)
