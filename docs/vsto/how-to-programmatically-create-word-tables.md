---
title: 'Instrukcje: Programowe tworzenie tabel programu Word'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], adding tables
- tables [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 24a365ba239e4d87e179bfecd664aa31aef0f359
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62574914"
---
# <a name="how-to-programmatically-create-word-tables"></a>Instrukcje: Programowe tworzenie tabel programu Word
  <xref:Microsoft.Office.Interop.Word.Tables> Kolekcji jest elementem członkowskim <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Interop.Word.Selection>, i <xref:Microsoft.Office.Interop.Word.Range> klasy, które oznacza, że można utworzyć tabelę w dowolnym z tych kontekstach. Możesz użyć <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> metody <xref:Microsoft.Office.Interop.Word.Tables> kolekcji, aby dodać tabelę w określonym zakresie.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="create-tables-in-document-level-customizations"></a>Tworzenie tabel w dostosowaniach na poziomie dokumentu

### <a name="to-add-a-table-to-a-document"></a>Aby dodać tabelę do dokumentu

- Użyj <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> metodę, aby dodać tabelę składającą się z trzech wierszy i czterech kolumn na początku dokumentu.

   Aby użyć w poniższym przykładzie kodu, należy uruchomić go z `ThisDocument` klasy w projekcie.

   [!code-vb[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#86)]
   [!code-csharp[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#86)]

  Podczas tworzenia tabeli jest automatycznie dodawany do <xref:Microsoft.Office.Interop.Word.Tables> zbiór <xref:Microsoft.Office.Tools.Word.Document> element hosta. Możesz następnie można się odwoływać do tabeli za pomocą numeru elementu za pomocą <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> właściwości, jak pokazano w poniższym kodzie.

### <a name="to-refer-to-a-table-by-item-number"></a>Aby odwołać się do tabeli przez liczbę elementów

1. Użyj <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> właściwość i podaj numer tabelę, która ma dotyczyć.

    Aby użyć w poniższym przykładzie kodu, należy uruchomić go z `ThisDocument` klasy w projekcie.

    [!code-vb[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#87)]
    [!code-csharp[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#87)]

   Każdy <xref:Microsoft.Office.Interop.Word.Table> obiekt również ma <xref:Microsoft.Office.Interop.Word.Table.Range%2A> właściwość, która pozwala ustawić formatowanie atrybutów.

### <a name="to-apply-a-style-to-a-table"></a>Aby zastosować styl do tabeli

1. Użyj <xref:Microsoft.Office.Interop.Word.Table.Style%2A> właściwość, aby zastosować jedną z wbudowanych stylów programu Word do tabeli.

     Aby użyć w poniższym przykładzie kodu, należy uruchomić go z `ThisDocument` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#88)]

## <a name="create-tables-in-vsto-add-ins"></a>Tworzenie tabel w dodatków narzędzi VSTO

### <a name="to-add-a-table-to-a-document"></a>Aby dodać tabelę do dokumentu

- Użyj <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> metodę, aby dodać tabelę składającą się z trzech wierszy i czterech kolumn na początku dokumentu.

   Poniższy przykład kodu dodaje tabelę do aktywnego dokumentu. Aby użyć tego przykładu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

   [!code-vb[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#86)]
   [!code-csharp[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#86)]

  Podczas tworzenia tabeli jest automatycznie dodawany do <xref:Microsoft.Office.Interop.Word.Tables> zbiór <xref:Microsoft.Office.Interop.Word.Document>. Możesz następnie można się odwoływać do tabeli za pomocą numeru elementu za pomocą <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> właściwości, jak pokazano w poniższym kodzie.

### <a name="to-refer-to-a-table-by-item-number"></a>Aby odwołać się do tabeli przez liczbę elementów

1. Użyj <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> właściwość i podaj numer tabelę, która ma dotyczyć.

    Poniższy przykład kodu wykorzystuje aktywnego dokumentu. Aby użyć tego przykładu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#87)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#87)]

   Każdy <xref:Microsoft.Office.Interop.Word.Table> obiekt również ma <xref:Microsoft.Office.Interop.Word.Table.Range%2A> właściwość, która pozwala ustawić formatowanie atrybutów.

### <a name="to-apply-a-style-to-a-table"></a>Aby zastosować styl do tabeli

1. Użyj <xref:Microsoft.Office.Interop.Word.Table.Style%2A> właściwość, aby zastosować jedną z wbudowanych stylów programu Word do tabeli.

     Poniższy przykład kodu wykorzystuje aktywnego dokumentu. Aby użyć tego przykładu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#88)]

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Programowe Dodawanie tekstu i formatowania do komórek w tabelach programu Word](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)
- [Instrukcje: Programowe Dodawanie wierszy i kolumn do tabel programu Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)
- [Instrukcje: Programowe Wypełnianie tabel programu Word właściwościami dokumentu](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
