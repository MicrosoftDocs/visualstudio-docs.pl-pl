---
title: 'Instrukcje: programowe Dodawanie wierszy i kolumn do tabel programu Word'
description: Dowiedz się, jak za pomocą metody Add obiektu Rows dodać wiersze do tabeli. Można również użyć metody Add obiektu Columns, aby dodać kolumny.
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
ms.openlocfilehash: a4077e78da512ef7b49546ae9b5271b5dfd8ff15
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910166"
---
# <a name="how-to-programmatically-add-rows-and-columns-to-word-tables"></a>Instrukcje: programowe Dodawanie wierszy i kolumn do tabel programu Word
  W tabeli programu Microsoft Office Word komórki są zorganizowane w wiersze i kolumny. Możesz użyć <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> metody <xref:Microsoft.Office.Interop.Word.Rows> obiektu, aby dodać wiersze do tabeli i <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> metodę <xref:Microsoft.Office.Interop.Word.Columns> obiektu, aby dodać kolumny.

 [!INCLUDE[appliesto_wdalldocapp](includes/appliesto-wdalldocapp-md.md)]

## <a name="document-level-customization-examples"></a>Przykłady dostosowania na poziomie dokumentu
 Poniższe przykłady kodu mogą służyć do dostosowywania na poziomie dokumentu. Aby użyć tych przykładów, uruchom je z `ThisDocument` klasy w projekcie. W poniższych przykładach założono, że dokument skojarzony z Twoim dostosowaniem ma już co najmniej jedną tabelę.

> [!IMPORTANT]
> Ten kod jest uruchamiany tylko w projektach utworzonych przy użyciu dowolnego z następujących szablonów projektu:
>
> - Dokument programu Word 2013
> - Szablon programu Word 2013
> - Dokument programu Word 2010
> - Szablon programu Word 2010
>
>   Jeśli chcesz wykonać to zadanie w dowolnym innym typie projektu, musisz dodać odwołanie do zestawu **Microsoft. Office. Interop. Word** , a następnie należy użyć klas z tego zestawu, aby dodać wiersze i kolumny do tabel. Aby uzyskać więcej informacji, zobacz [jak: docelowa aplikacja pakietu Office za poorednictwem zestawów podstawowych międzyoperacyjnych](how-to-target-office-applications-through-primary-interop-assemblies.md) i [odwołania do podstawowego zestawu międzyoperacyjnego programu Word 2010](office-primary-interop-assemblies.md).

### <a name="to-add-a-row-to-a-table"></a>Aby dodać wiersz do tabeli

1. Użyj <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> metody, aby dodać wiersz do tabeli.

     [!code-vb[Trin_VstcoreWordAutomation#95](codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomation#95](codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#95)]

### <a name="to-add-a-column-to-a-table"></a>Aby dodać kolumnę do tabeli

1. Użyj <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> metody, a następnie użyj metody, <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> aby wszystkie kolumny miały tę samą szerokość.

     [!code-vb[Trin_VstcoreWordAutomation#96](codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomation#96](codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#96)]

## <a name="vsto-add-in-examples"></a>Przykłady dodatków narzędzi VSTO
 Poniższe przykłady kodu mogą być używane w dodatku narzędzi VSTO. Aby użyć przykładów, uruchom je z `ThisAddIn` klasy w projekcie. W tych przykładach przyjęto założenie, że aktywny dokument ma już co najmniej jedną tabelę.

> [!IMPORTANT]
> Ten kod jest uruchamiany tylko w projektach utworzonych przy użyciu szablonów dodatków programu Word VSTO.
>
> Jeśli chcesz wykonać to zadanie w dowolnym innym typie projektu, musisz dodać odwołanie do zestawu **Microsoft. Office. Interop. Word** , a następnie należy użyć klas z tego zestawu, aby dodać wiersze i kolumny do tabel. Aby uzyskać więcej informacji, zobacz [jak: docelowa aplikacja pakietu Office za poorednictwem zestawów podstawowych międzyoperacyjnych](how-to-target-office-applications-through-primary-interop-assemblies.md) i [odwołania do podstawowego zestawu międzyoperacyjnego programu Word 2010](office-primary-interop-assemblies.md).

### <a name="to-add-a-row-to-a-table"></a>Aby dodać wiersz do tabeli

1. Użyj <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> metody, aby dodać wiersz do tabeli.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#95](codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#95](codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#95)]

### <a name="to-add-a-column-to-a-table"></a>Aby dodać kolumnę do tabeli

1. Użyj <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> metody, a następnie użyj metody, <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> aby wszystkie kolumny miały tę samą szerokość.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#96](codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#96](codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#96)]

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Programowane tworzenie tabel programu Word](how-to-programmatically-create-word-tables.md)
- [Instrukcje: Programowane dodawanie tekstu i formatowania do komórek w tabelach programu Word](how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)
- [Instrukcje: Programowane Wypełnianie tabel programu Word przy użyciu właściwości dokumentu](how-to-programmatically-populate-word-tables-with-document-properties.md)
