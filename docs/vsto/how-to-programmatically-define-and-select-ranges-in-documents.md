---
title: 'Instrukcje: programowe Definiowanie i wybieranie zakresów w dokumentach'
description: Dowiedz się, jak można programowo definiować i wybierać zakresy w dokumentach programu Microsoft Word przy użyciu obiektu Range.
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
ms.openlocfilehash: e9c703f4d4e747934d1bab458b75a9d499f0d439
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963955"
---
# <a name="how-to-programmatically-define-and-select-ranges-in-documents"></a>Instrukcje: programowe Definiowanie i wybieranie zakresów w dokumentach
  Można zdefiniować zakres w Microsoft Office dokumencie programu Word przy użyciu <xref:Microsoft.Office.Interop.Word.Range> obiektu. Można wybrać cały dokument na wiele sposobów, na przykład przy użyciu <xref:Microsoft.Office.Interop.Word.Range.Select%2A> metody <xref:Microsoft.Office.Interop.Word.Range> obiektu lub przy użyciu właściwości content <xref:Microsoft.Office.Tools.Word.Document> klasy (w dostosowaniu na poziomie dokumentu) lub <xref:Microsoft.Office.Interop.Word.Document> klasy (w dodatku narzędzi VSTO).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="define-a-range"></a>Zdefiniuj zakres
 Poniższy przykład pokazuje, jak utworzyć nowy <xref:Microsoft.Office.Interop.Word.Range> obiekt, który zawiera pierwsze siedem znaków w aktywnym dokumencie, w tym znaki niedrukowalne. Następnie zaznacza tekst w zakresie.

### <a name="to-define-a-range-in-a-document-level-customization"></a>Aby zdefiniować zakres w dostosowaniu na poziomie dokumentu

1. Dodaj zakres do dokumentu przez przekazanie znaku początkowego i końcowego do <xref:Microsoft.Office.Tools.Word.Document.Range%2A> metody <xref:Microsoft.Office.Tools.Word.Document> klasy. Aby użyć tego przykładu kodu, należy uruchomić go z `ThisDocument` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#18)]

### <a name="to-define-a-range-by-using-a-vsto-add-in"></a>Aby zdefiniować zakres przy użyciu dodatku VSTO

1. Dodaj zakres do dokumentu przez przekazanie znaku początkowego i końcowego do <xref:Microsoft.Office.Interop.Word._Document.Range%2A> metody <xref:Microsoft.Office.Interop.Word.Document> klasy. Poniższy przykład kodu dodaje zakres do aktywnego dokumentu. Aby użyć tego przykładu kodu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#18)]

## <a name="select-a-range-in-a-document-level-customization"></a>Wybierz zakres w dostosowaniu na poziomie dokumentu
 W poniższych przykładach pokazano, jak wybrać cały dokument przy użyciu <xref:Microsoft.Office.Interop.Word.Range.Select%2A> metody <xref:Microsoft.Office.Interop.Word.Range> obiektu lub przy użyciu <xref:Microsoft.Office.Tools.Word.Document.Content%2A> właściwości <xref:Microsoft.Office.Tools.Word.Document> klasy.

### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Aby zaznaczyć cały dokument jako zakres przy użyciu metody Select

1. Użyj <xref:Microsoft.Office.Interop.Word.Range.Select%2A> metody <xref:Microsoft.Office.Interop.Word.Range> , która zawiera cały dokument. Aby użyć następującego przykładu kodu, uruchom go z `ThisDocument` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#19)]

### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>Aby wybrać cały dokument jako zakres przy użyciu właściwości content

1. Użyj <xref:Microsoft.Office.Tools.Word.Document.Content%2A> właściwości, aby zdefiniować zakres, który obejmuje cały dokument.

    [!code-vb[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#20)]
    [!code-csharp[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#20)]

   Można również użyć metod i właściwości innych obiektów do zdefiniowania zakresu.

### <a name="to-select-a-sentence-in-the-active-document"></a>Aby wybrać zdanie w aktywnym dokumencie

1. Ustaw zakres przy użyciu <xref:Microsoft.Office.Interop.Word.Sentences> kolekcji. Użyj indeksu zdania, które chcesz wybrać.

    [!code-vb[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#21)]
    [!code-csharp[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#21)]

   Innym sposobem wybrania zdania jest ręczne ustawienie wartości początkowych i końcowych dla zakresu.

### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>Aby wybrać zdanie przez ręczne ustawienie wartości początkowych i końcowych

1. Utwórz zmienną zakresu.

     [!code-vb[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#23)]

2. Sprawdź, czy w dokumencie znajdują się co najmniej dwa zdania, ustaw argumenty *początku* i *końca* zakresu, a następnie wybierz zakres.

     [!code-vb[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#24)]

## <a name="select-a-range-by-using-a-vsto-add-in"></a>Wybierz zakres przy użyciu dodatku VSTO
 W poniższych przykładach pokazano, jak wybrać cały dokument przy użyciu <xref:Microsoft.Office.Interop.Word.Range.Select%2A> metody <xref:Microsoft.Office.Interop.Word.Range> obiektu lub przy użyciu <xref:Microsoft.Office.Interop.Word._Document.Content%2A> właściwości <xref:Microsoft.Office.Interop.Word.Document> klasy.

### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Aby zaznaczyć cały dokument jako zakres przy użyciu metody Select

1. Użyj <xref:Microsoft.Office.Interop.Word.Range.Select%2A> metody <xref:Microsoft.Office.Interop.Word.Range> , która zawiera cały dokument. Poniższy przykład kodu wybiera zawartość aktywnego dokumentu. Aby użyć tego przykładu kodu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#19)]

### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>Aby wybrać cały dokument jako zakres przy użyciu właściwości content

1. Użyj <xref:Microsoft.Office.Interop.Word._Document.Content%2A> właściwości, aby zdefiniować zakres, który obejmuje cały dokument.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#20)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#20)]

   Można również użyć metod i właściwości innych obiektów do zdefiniowania zakresu.

### <a name="to-select-a-sentence-in-the-active-document"></a>Aby wybrać zdanie w aktywnym dokumencie

1. Ustaw zakres przy użyciu <xref:Microsoft.Office.Interop.Word.Sentences> kolekcji. Użyj indeksu zdania, które chcesz wybrać.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#21)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#21)]

   Innym sposobem wybrania zdania jest ręczne ustawienie wartości początkowych i końcowych dla zakresu.

### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>Aby wybrać zdanie przez ręczne ustawienie wartości początkowych i końcowych

1. Utwórz zmienną zakresu.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#23)]

2. Sprawdź, czy w dokumencie znajdują się co najmniej dwa zdania, ustaw argumenty *początku* i *końca* zakresu, a następnie wybierz zakres.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#24)]

## <a name="see-also"></a>Zobacz też
- [Model obiektów programu Word — omówienie](../vsto/word-object-model-overview.md)
- [Instrukcje: Programowane poszerzanie zakresów w dokumentach](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Instrukcje: programowe pobieranie znaków początkowych i końcowych w zakresach](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Instrukcje: Programowane poszerzanie zakresów w dokumentach](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Instrukcje: Programowane Resetowanie zakresów w dokumentach programu Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Instrukcje: programowe zwijanie zakresów lub zaznaczenia w dokumentach](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Instrukcje: Programowane wykluczanie znaczników akapitu podczas tworzenia zakresów](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
