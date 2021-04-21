---
title: 'How to: Read from and write to document properties ( Jak odczytywać właściwości dokumentu i zapisywać je w dokumencie)'
description: Dowiedz się, jak za pomocą Visual Studio uzyskać lub ustawić właściwości dokumentu w programach Microsoft Excel i Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
- Excel [Office development in Visual Studio], document properties
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3474d86a7408e841d383c82e5ab38da90253dbbf
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826684"
---
# <a name="how-to-read-from-and-write-to-document-properties"></a>How to: Read from and write to document properties ( Jak odczytywać właściwości dokumentu i zapisywać je w dokumencie)
  Właściwości dokumentu można przechowywać razem z dokumentem. Aplikacje pakietu Office oferują szereg wbudowanych właściwości, takich jak autor, tytuł i temat. W tym temacie przedstawiono sposób ustawienia właściwości dokumentu w programach Microsoft Office Excel i Microsoft Office Word.

 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]

## <a name="set-document-properties-in-excel"></a>Ustawianie właściwości dokumentu w programie Excel
 Aby pracować z właściwościami wbudowanymi w programie Excel, użyj następujących właściwości:

- W projekcie na poziomie dokumentu <xref:Microsoft.Office.Tools.Excel.Workbook.BuiltinDocumentProperties%2A> użyj właściwości `ThisWorkbook` klasy .

- W projekcie dodatku VSTO użyj <xref:Microsoft.Office.Interop.Excel._Workbook.BuiltinDocumentProperties%2A> właściwości <xref:Microsoft.Office.Interop.Excel.Workbook> obiektu .

  Te właściwości zwracają <xref:Microsoft.Office.Core.DocumentProperties> obiekt , który jest kolekcją <xref:Microsoft.Office.Core.DocumentProperty> obiektów. Właściwość kolekcji umożliwia pobranie określonej właściwości według nazwy lub `Item` indeksu w kolekcji.

  Poniższy przykład kodu pokazuje, jak zmienić wbudowaną właściwość **Numer** poprawki w projekcie na poziomie dokumentu.

### <a name="to-change-the-revision-number-property-in-excel"></a>Aby zmienić właściwość Numer poprawki w programie Excel

1. Przypisz wbudowane właściwości dokumentu do zmiennej.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs" id="Snippet7":::

2. Zwiększa właściwość `Revision Number` o jeden.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb" id="Snippet8":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs" id="Snippet8":::

## <a name="set-document-properties-in-word"></a>Ustawianie właściwości dokumentu w programie Word
 Aby pracować z właściwościami wbudowanymi w programie Word, użyj następujących właściwości:

- W projekcie na poziomie dokumentu <xref:Microsoft.Office.Tools.Word.Document.BuiltInDocumentProperties%2A> użyj właściwości `ThisDocument` klasy .

- W projekcie dodatku VSTO użyj <xref:Microsoft.Office.Interop.Word._Document.BuiltInDocumentProperties%2A> właściwości <xref:Microsoft.Office.Interop.Word.Document> obiektu .

  Te właściwości zwracają <xref:Microsoft.Office.Core.DocumentProperties> obiekt , który jest kolekcją <xref:Microsoft.Office.Core.DocumentProperty> obiektów. Właściwość kolekcji umożliwia pobranie określonej właściwości według nazwy lub `Item` indeksu w kolekcji.

  Poniższy przykład kodu pokazuje, jak zmienić wbudowaną właściwość **Podmiot** w projekcie na poziomie dokumentu.

### <a name="to-change-the-subject-property"></a>Aby zmienić właściwość Podmiot

1. Przypisz wbudowane właściwości dokumentu do zmiennej.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb" id="Snippet1":::

2. Zmień właściwość `Subject` na "Oficjalny plan".

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb" id="Snippet2":::

## <a name="robust-programming"></a>Niezawodne programowanie
 W przykładach założono, że kod w klasie został napisany w projekcie na poziomie dokumentu dla programu Excel, a klasa w projekcie na poziomie dokumentu dla `ThisWorkbook` `ThisDocument` programu Word.

 Mimo że pracujesz z programami Word i Excel oraz ich obiektami, Microsoft Office dostarcza listę dostępnych wbudowanych właściwości dokumentu. Próba uzyskania dostępu do niezdefiniowanych właściwości zgłasza wyjątek.

## <a name="see-also"></a>Zobacz też
- [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md)
- [Zaprogramowanie dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)
- [How to: Create and modify custom document properties (Tworzyć i modyfikować niestandardowe właściwości dokumentu)](../vsto/how-to-create-and-modify-custom-document-properties.md)
