---
title: Jak programowo definiować i wybierać zakresy w dokumentach
description: Dowiedz się, jak programowo definiować i wybierać zakresy w dokumentach programu Microsoft Word przy użyciu obiektu Range.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], selecting sentences
- documents [Office development in Visual Studio], ranges
- sentences, selecting in documents
- ranges, selecting in documents
- ranges, defining in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3a5dc0c7fb9f3e9a2b4a15447f81239db973c215
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825956"
---
# <a name="how-to-programmatically-define-and-select-ranges-in-documents"></a>Jak programowo definiować i wybierać zakresy w dokumentach
  Zakres w dokumencie programu Word można Microsoft Office za pomocą <xref:Microsoft.Office.Interop.Word.Range> obiektu . Cały dokument można wybrać na wiele sposobów, na przykład przy użyciu metody obiektu lub właściwości Content klasy (w dostosowywaniu na poziomie dokumentu) lub klasy (w dodatku <xref:Microsoft.Office.Interop.Word.Range.Select%2A> <xref:Microsoft.Office.Interop.Word.Range> <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Interop.Word.Document> VSTO).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="define-a-range"></a>Definiowanie zakresu
 W poniższym przykładzie pokazano, jak utworzyć nowy obiekt, który zawiera pierwsze siedem znaków w aktywnym dokumencie, w tym znaki <xref:Microsoft.Office.Interop.Word.Range> niedrukowe. Następnie wybiera tekst w zakresie.

### <a name="to-define-a-range-in-a-document-level-customization"></a>Aby zdefiniować zakres w dostosowywaniu na poziomie dokumentu

1. Dodaj zakres do dokumentu, przekazując znak początku i końca <xref:Microsoft.Office.Tools.Word.Document.Range%2A> do metody <xref:Microsoft.Office.Tools.Word.Document> klasy . Aby użyć tego przykładu kodu, uruchom go z `ThisDocument` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet18":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet18":::

### <a name="to-define-a-range-by-using-a-vsto-add-in"></a>Aby zdefiniować zakres przy użyciu dodatku VSTO

1. Dodaj zakres do dokumentu, przekazując znak początku i końca <xref:Microsoft.Office.Interop.Word._Document.Range%2A> do metody <xref:Microsoft.Office.Interop.Word.Document> klasy . Poniższy przykład kodu dodaje zakres do aktywnego dokumentu. Aby użyć tego przykładu kodu, uruchom go z `ThisAddIn` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet18":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet18":::

## <a name="select-a-range-in-a-document-level-customization"></a>Wybieranie zakresu w dostosowywaniu na poziomie dokumentu
 Poniższe przykłady pokazują, jak wybrać cały dokument przy użyciu metody obiektu lub właściwości <xref:Microsoft.Office.Interop.Word.Range.Select%2A> <xref:Microsoft.Office.Interop.Word.Range> klasy <xref:Microsoft.Office.Tools.Word.Document.Content%2A> <xref:Microsoft.Office.Tools.Word.Document> .

### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Aby wybrać cały dokument jako zakres przy użyciu metody Select

1. Użyj <xref:Microsoft.Office.Interop.Word.Range.Select%2A> metody , <xref:Microsoft.Office.Interop.Word.Range> która zawiera cały dokument. Aby użyć poniższego przykładu kodu, uruchom go z `ThisDocument` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet19":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet19":::

### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>Aby wybrać cały dokument jako zakres przy użyciu właściwości Content

1. Użyj właściwości <xref:Microsoft.Office.Tools.Word.Document.Content%2A> , aby zdefiniować zakres obejmujący cały dokument.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet20":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet20":::

   Do zdefiniowania zakresu można również użyć metod i właściwości innych obiektów.

### <a name="to-select-a-sentence-in-the-active-document"></a>Aby wybrać zdanie w aktywnym dokumencie

1. Ustaw zakres przy użyciu <xref:Microsoft.Office.Interop.Word.Sentences> kolekcji . Użyj indeksu zdania, które chcesz wybrać.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet21":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet21":::

   Innym sposobem wybrania zdania jest ręczne ustawienie wartości początku i końca zakresu.

### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>Aby wybrać zdanie, ręcznie ustawiając wartości początku i końca

1. Utwórz zmienną zakresu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet23":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet23":::

2. Sprawdź, czy w dokumencie znajdują się co najmniej dwa  zdania, ustaw *argumenty Początek* i Koniec zakresu, a następnie wybierz zakres.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet24":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet24":::

## <a name="select-a-range-by-using-a-vsto-add-in"></a>Wybieranie zakresu przy użyciu dodatku VSTO
 Poniższe przykłady pokazują, jak wybrać cały dokument przy użyciu metody obiektu lub właściwości <xref:Microsoft.Office.Interop.Word.Range.Select%2A> <xref:Microsoft.Office.Interop.Word.Range> klasy <xref:Microsoft.Office.Interop.Word._Document.Content%2A> <xref:Microsoft.Office.Interop.Word.Document> .

### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Aby wybrać cały dokument jako zakres przy użyciu metody Select

1. Użyj <xref:Microsoft.Office.Interop.Word.Range.Select%2A> metody , <xref:Microsoft.Office.Interop.Word.Range> która zawiera cały dokument. Poniższy przykład kodu wybiera zawartość aktywnego dokumentu. Aby użyć tego przykładu kodu, uruchom go z `ThisAddIn` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet19":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet19":::

### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>Aby wybrać cały dokument jako zakres przy użyciu właściwości Content

1. Użyj właściwości <xref:Microsoft.Office.Interop.Word._Document.Content%2A> , aby zdefiniować zakres obejmujący cały dokument.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet20":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet20":::

   Do zdefiniowania zakresu można również użyć metod i właściwości innych obiektów.

### <a name="to-select-a-sentence-in-the-active-document"></a>Aby wybrać zdanie w aktywnym dokumencie

1. Ustaw zakres przy użyciu <xref:Microsoft.Office.Interop.Word.Sentences> kolekcji . Użyj indeksu zdania, które chcesz wybrać.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet21":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet21":::

   Innym sposobem wybrania zdania jest ręczne ustawienie wartości początku i końca zakresu.

### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>Aby wybrać zdanie, ręcznie ustawiając wartości początku i końca

1. Utwórz zmienną zakresu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet23":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet23":::

2. Sprawdź, czy w dokumencie znajdują się co najmniej dwa zdania, ustaw *argumenty Start* i *End* zakresu, a następnie wybierz zakres.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet24":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet24":::

## <a name="see-also"></a>Zobacz też
- [Omówienie modelu obiektów programu Word](../vsto/word-object-model-overview.md)
- [Pisano: Programowe rozszerzanie zakresów w dokumentach](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [How to: Programowe pobieranie znaków początku i końca w zakresach](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Pisano: Programowe rozszerzanie zakresów w dokumentach](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [How to: Programowe resetowanie zakresów w dokumentach programu Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Jak programowo zwinąć zakresy lub wybory w dokumentach](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Dzieje się tak: Programowe wykluczanie znaczników akapitu podczas tworzenia zakresów](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
