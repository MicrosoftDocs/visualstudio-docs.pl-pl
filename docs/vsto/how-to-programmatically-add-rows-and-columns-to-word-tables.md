---
title: 'How to: Programowe dodawanie wierszy i kolumn do tabel programu Word'
description: Dowiedz się, jak za pomocą metody Add obiektu Rows dodać wiersze do tabeli. Możesz również użyć metody Add obiektu Columns, aby dodać kolumny.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- rows [Office development in Visual Studio], adding to Word tables
- tables [Office development in Visual Studio], adding rows and columns
- columns [Office development in Visual Studio], adding to Word tables
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7cac3e11f73e53441f1bcf20c67dd5659a49a1b0
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828426"
---
# <a name="how-to-programmatically-add-rows-and-columns-to-word-tables"></a>How to: Programowe dodawanie wierszy i kolumn do tabel programu Word
  W tabeli Microsoft Office Word komórki są zorganizowane w wiersze i kolumny. Możesz użyć metody obiektu , aby dodać wiersze do tabeli i metody obiektu <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> <xref:Microsoft.Office.Interop.Word.Rows> , aby dodać <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> <xref:Microsoft.Office.Interop.Word.Columns> kolumny.

 [!INCLUDE[appliesto_wdalldocapp](includes/appliesto-wdalldocapp-md.md)]

## <a name="document-level-customization-examples"></a>Przykłady dostosowywania na poziomie dokumentu
 Następujące przykłady kodu mogą być używane w dostosowywaniu na poziomie dokumentu. Aby użyć tych przykładów, uruchom je z `ThisDocument` klasy w projekcie. W tych przykładach przyjęto założenie, że dokument skojarzony z dostosowaniem zawiera już co najmniej jedną tabelę.

> [!IMPORTANT]
> Ten kod jest uruchamiany tylko w projektach, które tworzysz przy użyciu dowolnego z następujących szablonów projektów:
>
> - Dokument programu Word 2013
> - Szablon programu Word 2013
> - Dokument programu Word 2010
> - Szablon programu Word 2010
>
>   Jeśli chcesz wykonać to zadanie w dowolnym innym typie projektu, musisz dodać odwołanie do zestawu **Microsoft.Office.Interop.Word,** a następnie użyć klas z tego zestawu, aby dodać wiersze i kolumny do tabel. Aby uzyskać więcej informacji, zobacz temat How [to: Target Office applications through primary interop assemblies](how-to-target-office-applications-through-primary-interop-assemblies.md) (Jak kierować aplikacje pakietu Office za pomocą podstawowych zestawów międzyoptykowych) i Word 2010 primary interop assembly reference (Informacje o podstawowym zestawie [międzyoptykowym programu Word 2010).](office-primary-interop-assemblies.md)

### <a name="to-add-a-row-to-a-table"></a>Aby dodać wiersz do tabeli

1. Użyj <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> metody , aby dodać wiersz do tabeli.

     :::code language="vb" source="codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet95":::
     :::code language="csharp" source="codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet95":::

### <a name="to-add-a-column-to-a-table"></a>Aby dodać kolumnę do tabeli

1. Użyj <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> metody , a następnie użyj <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> metody , aby wszystkie kolumny mają taką samą szerokość.

     :::code language="vb" source="codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet96":::
     :::code language="csharp" source="codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet96":::

## <a name="vsto-add-in-examples"></a>Przykłady dodatków VSTO
 W dodatku VSTO można użyć następujących przykładów kodu. Aby użyć przykładów, uruchom je z `ThisAddIn` klasy w projekcie. W tych przykładach przyjęto założenie, że aktywny dokument ma już co najmniej jedną tabelę.

> [!IMPORTANT]
> Ten kod jest uruchamiany tylko w projektach, które tworzysz przy użyciu szablonów dodatków Word VSTO.
>
> Jeśli chcesz wykonać to zadanie w dowolnym innym typie projektu, musisz dodać odwołanie do zestawu **Microsoft.Office.Interop.Word,** a następnie użyć klas z tego zestawu, aby dodać wiersze i kolumny do tabel. Aby uzyskać więcej informacji, zobacz temat How [to: Target Office applications through primary interop assemblies](how-to-target-office-applications-through-primary-interop-assemblies.md) (Jak kierować aplikacje pakietu Office za pomocą podstawowych zestawów międzyoptykowych) i Word 2010 primary interop assembly reference (Informacje o podstawowym zestawie [międzyoptykowym programu Word 2010).](office-primary-interop-assemblies.md)

### <a name="to-add-a-row-to-a-table"></a>Aby dodać wiersz do tabeli

1. Użyj <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> metody , aby dodać wiersz do tabeli.

     :::code language="vb" source="codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet95":::
     :::code language="csharp" source="codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet95":::

### <a name="to-add-a-column-to-a-table"></a>Aby dodać kolumnę do tabeli

1. Użyj <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> metody , a następnie użyj <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> metody , aby wszystkie kolumny mają taką samą szerokość.

     :::code language="vb" source="codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet96":::
     :::code language="csharp" source="codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet96":::

## <a name="see-also"></a>Zobacz też
- [How to: Programmatically create Word tables (Tworzyć programowo tabele programu Word)](how-to-programmatically-create-word-tables.md)
- [Jak programowo dodać tekst i formatowanie do komórek w tabelach programu Word](how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)
- [How to: Programowe wypełnianie tabel programu Word właściwościami dokumentu](how-to-programmatically-populate-word-tables-with-document-properties.md)
