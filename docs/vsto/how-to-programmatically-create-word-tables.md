---
title: 'Instrukcje: Programowane tworzenie tabel programu Word'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: a1bc20b277df90ae963d257137373457a0196e72
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544758"
---
# <a name="how-to-programmatically-create-word-tables"></a>Instrukcje: Programowane tworzenie tabel programu Word
  <xref:Microsoft.Office.Interop.Word.Tables>Kolekcja jest składową <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Tools.Word.Document> klas,, <xref:Microsoft.Office.Interop.Word.Selection> , i <xref:Microsoft.Office.Interop.Word.Range> , co oznacza, że można utworzyć tabelę w dowolnym z tych kontekstów. <xref:Microsoft.Office.Interop.Word.Tables.Add%2A>Metoda <xref:Microsoft.Office.Interop.Word.Tables> kolekcji służy do dodawania tabeli w określonym zakresie.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="create-tables-in-document-level-customizations"></a>Tworzenie tabel w dostosowaniach na poziomie dokumentu

### <a name="to-add-a-table-to-a-document"></a>Aby dodać tabelę do dokumentu

- Użyj <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> metody, aby dodać tabelę składającą się z trzech wierszy i czterech kolumn na początku dokumentu.

   Aby użyć następującego przykładu kodu, uruchom go z `ThisDocument` klasy w projekcie.

   [!code-vb[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#86)]
   [!code-csharp[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#86)]

  Podczas tworzenia tabeli jest ona automatycznie dodawana do <xref:Microsoft.Office.Interop.Word.Tables> kolekcji <xref:Microsoft.Office.Tools.Word.Document> elementów hosta. Następnie można odwołać się do tabeli według numeru elementu przy użyciu <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> właściwości, jak pokazano w poniższym kodzie.

### <a name="to-refer-to-a-table-by-item-number"></a>Aby odwołać się do tabeli według numeru elementu

1. Użyj <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> właściwości i podaj numer elementu tabeli, do której chcesz się odwołać.

    Aby użyć następującego przykładu kodu, uruchom go z `ThisDocument` klasy w projekcie.

    [!code-vb[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#87)]
    [!code-csharp[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#87)]

   Każdy <xref:Microsoft.Office.Interop.Word.Table> obiekt ma również <xref:Microsoft.Office.Interop.Word.Table.Range%2A> Właściwość, która umożliwia ustawianie atrybutów formatowania.

### <a name="to-apply-a-style-to-a-table"></a>Aby zastosować styl do tabeli

1. Użyj <xref:Microsoft.Office.Interop.Word.Table.Style%2A> właściwości, aby zastosować jeden z wbudowanych stylów słowa do tabeli.

     Aby użyć następującego przykładu kodu, uruchom go z `ThisDocument` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#88)]

## <a name="create-tables-in-vsto-add-ins"></a>Tworzenie tabel w dodatkach narzędzi VSTO

### <a name="to-add-a-table-to-a-document"></a>Aby dodać tabelę do dokumentu

- Użyj <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> metody, aby dodać tabelę składającą się z trzech wierszy i czterech kolumn na początku dokumentu.

   Poniższy przykład kodu dodaje tabelę do aktywnego dokumentu. Aby użyć tego przykładu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

   [!code-vb[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#86)]
   [!code-csharp[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#86)]

  Podczas tworzenia tabeli jest ona automatycznie dodawana do <xref:Microsoft.Office.Interop.Word.Tables> kolekcji <xref:Microsoft.Office.Interop.Word.Document> . Następnie można odwołać się do tabeli według numeru elementu przy użyciu <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> właściwości, jak pokazano w poniższym kodzie.

### <a name="to-refer-to-a-table-by-item-number"></a>Aby odwołać się do tabeli według numeru elementu

1. Użyj <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> właściwości i podaj numer elementu tabeli, do której chcesz się odwołać.

    Poniższy przykład kodu używa aktywnego dokumentu. Aby użyć tego przykładu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#87)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#87)]

   Każdy <xref:Microsoft.Office.Interop.Word.Table> obiekt ma również <xref:Microsoft.Office.Interop.Word.Table.Range%2A> Właściwość, która umożliwia ustawianie atrybutów formatowania.

### <a name="to-apply-a-style-to-a-table"></a>Aby zastosować styl do tabeli

1. Użyj <xref:Microsoft.Office.Interop.Word.Table.Style%2A> właściwości, aby zastosować jeden z wbudowanych stylów słowa do tabeli.

     Poniższy przykład kodu używa aktywnego dokumentu. Aby użyć tego przykładu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#88)]

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Programowane dodawanie tekstu i formatowania do komórek w tabelach programu Word](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)
- [Instrukcje: programowe Dodawanie wierszy i kolumn do tabel programu Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)
- [Instrukcje: Programowane Wypełnianie tabel programu Word przy użyciu właściwości dokumentu](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
