---
title: 'How to: Programmatically create Word tables (Tworzyć programowo tabele programu Word)'
description: Dowiedz się, jak za pomocą metody Add kolekcji Tables dodać tabelę w określonym zakresie w dokumencie programu Microsoft Word.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5651487e280d7fb9912734b919b00fab28a702db
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827386"
---
# <a name="how-to-programmatically-create-word-tables"></a>How to: Programmatically create Word tables (Tworzyć programowo tabele programu Word)
  Kolekcja jest członkiem klas , , i , co oznacza, że można utworzyć tabelę <xref:Microsoft.Office.Interop.Word.Tables> w dowolnym z tych <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Interop.Word.Selection> <xref:Microsoft.Office.Interop.Word.Range> kontekstów. Metoda <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> kolekcji służy <xref:Microsoft.Office.Interop.Word.Tables> do dodawania tabeli w określonym zakresie.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="create-tables-in-document-level-customizations"></a>Tworzenie tabel w dostosowaniach na poziomie dokumentu

### <a name="to-add-a-table-to-a-document"></a>Aby dodać tabelę do dokumentu

- Użyj <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> metody , aby dodać tabelę składającą się z trzech wierszy i czterech kolumn na początku dokumentu.

   Aby użyć poniższego przykładu kodu, uruchom go z `ThisDocument` klasy w projekcie.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet86":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet86":::

  Po utworzeniu tabeli jest ona automatycznie dodawana do <xref:Microsoft.Office.Interop.Word.Tables> kolekcji <xref:Microsoft.Office.Tools.Word.Document> elementu hosta. Następnie możesz odwołać się do tabeli według numeru elementu przy użyciu <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> właściwości , jak pokazano w poniższym kodzie.

### <a name="to-refer-to-a-table-by-item-number"></a>Aby odwołać się do tabeli według numeru elementu

1. Użyj <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> właściwości i podać numer elementu tabeli, do której chcesz się odwołać.

    Aby użyć poniższego przykładu kodu, uruchom go z `ThisDocument` klasy w projekcie.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet87":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet87":::

   Każdy <xref:Microsoft.Office.Interop.Word.Table> obiekt ma również <xref:Microsoft.Office.Interop.Word.Table.Range%2A> właściwość, która umożliwia ustawianie atrybutów formatowania.

### <a name="to-apply-a-style-to-a-table"></a>Aby zastosować styl do tabeli

1. Użyj właściwości , aby zastosować jeden z wbudowanych stylów <xref:Microsoft.Office.Interop.Word.Table.Style%2A> programu Word do tabeli.

     Aby użyć poniższego przykładu kodu, uruchom go z `ThisDocument` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet88":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet88":::

## <a name="create-tables-in-vsto-add-ins"></a>Tworzenie tabel w dodatki VSTO

### <a name="to-add-a-table-to-a-document"></a>Aby dodać tabelę do dokumentu

- Użyj metody , aby dodać tabelę składającą się z trzech wierszy i czterech kolumn <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> na początku dokumentu.

   Poniższy przykład kodu dodaje tabelę do aktywnego dokumentu. Aby użyć tego przykładu, uruchom go z `ThisAddIn` klasy w projekcie.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet86":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet86":::

  Podczas tworzenia tabeli jest ona automatycznie dodawana do <xref:Microsoft.Office.Interop.Word.Tables> kolekcji tabeli <xref:Microsoft.Office.Interop.Word.Document> . Następnie możesz odwołać się do tabeli według jej numeru elementu przy użyciu <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> właściwości , jak pokazano w poniższym kodzie.

### <a name="to-refer-to-a-table-by-item-number"></a>Aby odwołać się do tabeli według numeru elementu

1. Użyj <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> właściwości i podać numer elementu tabeli, do której chcesz się odwołać.

    W poniższym przykładzie kodu używany jest aktywny dokument. Aby użyć tego przykładu, uruchom go z `ThisAddIn` klasy w projekcie.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet87":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet87":::

   Każdy <xref:Microsoft.Office.Interop.Word.Table> obiekt ma również <xref:Microsoft.Office.Interop.Word.Table.Range%2A> właściwość, która umożliwia ustawianie atrybutów formatowania.

### <a name="to-apply-a-style-to-a-table"></a>Aby zastosować styl do tabeli

1. Użyj właściwości , aby zastosować jeden z wbudowanych stylów <xref:Microsoft.Office.Interop.Word.Table.Style%2A> programu Word do tabeli.

     W poniższym przykładzie kodu używany jest aktywny dokument. Aby użyć tego przykładu, uruchom go z `ThisAddIn` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet88":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet88":::

## <a name="see-also"></a>Zobacz też
- [Jak programowo dodać tekst i formatowanie do komórek w tabelach programu Word](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)
- [How to: Programowe dodawanie wierszy i kolumn do tabel programu Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)
- [How to: Programowe wypełnianie tabel programu Word właściwościami dokumentu](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
