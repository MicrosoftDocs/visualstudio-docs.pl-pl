---
title: 'Instrukcje: odczytywanie i zapisywanie właściwości dokumentu'
description: Dowiedz się, jak za pomocą programu Visual Studio pobrać lub ustawić właściwości dokumentu w programach Microsoft Excel i Microsoft Word.
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
ms.openlocfilehash: 864906e678cb3976e99dd8d9aeb9147e303f2517
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942187"
---
# <a name="how-to-read-from-and-write-to-document-properties"></a>Instrukcje: odczytywanie i zapisywanie właściwości dokumentu
  Można przechowywać właściwości dokumentu wraz z dokumentem. Aplikacje pakietu Office udostępniają wiele wbudowanych właściwości, takich jak autor, tytuł i temat. W tym temacie przedstawiono sposób ustawiania właściwości dokumentu w programie Microsoft Office Excel i Microsoft Office Word.

 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]

## <a name="set-document-properties-in-excel"></a>Ustawianie właściwości dokumentu w programie Excel
 Aby współpracować z wbudowanymi właściwościami w programie Excel, użyj następujących właściwości:

- W projekcie na poziomie dokumentu, użyj <xref:Microsoft.Office.Tools.Excel.Workbook.BuiltinDocumentProperties%2A> właściwości `ThisWorkbook` klasy.

- W projekcie dodatku VSTO Użyj <xref:Microsoft.Office.Interop.Excel._Workbook.BuiltinDocumentProperties%2A> właściwości <xref:Microsoft.Office.Interop.Excel.Workbook> obiektu.

  Te właściwości zwracają <xref:Microsoft.Office.Core.DocumentProperties> obiekt, który jest kolekcją <xref:Microsoft.Office.Core.DocumentProperty> obiektów. Możesz użyć `Item` właściwości kolekcji, aby pobrać określoną właściwość według nazwy lub indeksu w kolekcji.

  Poniższy przykład kodu pokazuje, jak zmienić wbudowaną Właściwość **numeru poprawki** w projekcie na poziomie dokumentu.

### <a name="to-change-the-revision-number-property-in-excel"></a>Aby zmienić właściwość numeru poprawki w programie Excel

1. Przypisz wbudowane właściwości dokumentu do zmiennej.

     [!code-vb[Trin_VstcoreProgramming#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#7)]
     [!code-csharp[Trin_VstcoreProgramming#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#7)]

2. Zwiększ `Revision Number` Właściwość o jeden.

     [!code-vb[Trin_VstcoreProgramming#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#8)]
     [!code-csharp[Trin_VstcoreProgramming#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#8)]

## <a name="set-document-properties-in-word"></a>Ustawianie właściwości dokumentu w programie Word
 Aby współpracować z wbudowanymi właściwościami w programie Word, użyj następujących właściwości:

- W projekcie na poziomie dokumentu, użyj <xref:Microsoft.Office.Tools.Word.Document.BuiltInDocumentProperties%2A> właściwości `ThisDocument` klasy.

- W projekcie dodatku VSTO Użyj <xref:Microsoft.Office.Interop.Word._Document.BuiltInDocumentProperties%2A> właściwości <xref:Microsoft.Office.Interop.Word.Document> obiektu.

  Te właściwości zwracają <xref:Microsoft.Office.Core.DocumentProperties> obiekt, który jest kolekcją <xref:Microsoft.Office.Core.DocumentProperty> obiektów. Możesz użyć `Item` właściwości kolekcji, aby pobrać określoną właściwość według nazwy lub indeksu w kolekcji.

  Poniższy przykład kodu pokazuje, jak zmienić wbudowaną Właściwość **subject** w projekcie na poziomie dokumentu.

### <a name="to-change-the-subject-property"></a>Aby zmienić właściwość podmiotu

1. Przypisz wbudowane właściwości dokumentu do zmiennej.

     [!code-csharp[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#1)]

2. Zmień `Subject` Właściwość na "oficjalny dokument".

     [!code-csharp[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#2)]

## <a name="robust-programming"></a>Niezawodne programowanie
 W przykładach założono, że Zapisano kod w `ThisWorkbook` klasie w projekcie na poziomie dokumentu dla programu Excel, a `ThisDocument` Klasa w projekcie na poziomie dokumentu dla programu Word.

 Chociaż pracujesz z programami Word i Excel i ich obiektami, Microsoft Office dostarcza listę dostępnych wbudowanych właściwości dokumentu. Próba uzyskania dostępu do niezdefiniowanej właściwości wywołuje wyjątek.

## <a name="see-also"></a>Zobacz też
- [Dodatki narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md)
- [Dostosowywanie na poziomie dokumentu programu](../vsto/programming-document-level-customizations.md)
- [Instrukcje: Tworzenie i modyfikowanie właściwości dokumentu niestandardowego](../vsto/how-to-create-and-modify-custom-document-properties.md)
