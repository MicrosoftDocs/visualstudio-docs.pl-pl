---
title: 'Instrukcje: Programowe Dodawanie wierszy i kolumn do tabel programu Word'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- rows [Office development in Visual Studio], adding to Word tables
- tables [Office development in Visual Studio], adding rows and columns
- columns [Office development in Visual Studio], adding to Word tables
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 780d794874ae87f3310810f2b46127fdf2eb46c5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63419580"
---
# <a name="how-to-programmatically-add-rows-and-columns-to-word-tables"></a>Instrukcje: Programowe Dodawanie wierszy i kolumn do tabel programu Word
  W tabeli programu Microsoft Office Word komórki są zorganizowane w wiersze i kolumny. Możesz użyć <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> metody <xref:Microsoft.Office.Interop.Word.Rows> obiektu, aby dodać wiersze do tabeli i <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> metody <xref:Microsoft.Office.Interop.Word.Columns> obiektu, aby dodać kolumny.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="document-level-customization-examples"></a>Przykłady dostosowywania poziomie dokumentu
 Poniższe przykłady kodu może służyć w dostosowaniu na poziomie dokumentu. Aby użyć tych przykładów, uruchomić je z `ThisDocument` klasy w projekcie. W przykładach założono, że dokument skojarzony z dostosowywaniem w już ma co najmniej jedna tabela.

> [!IMPORTANT]
> Ten kod zadziała tylko w projektach, które tworzysz przy użyciu dowolnej z poniższych szablonów projektu:
>
> - Dokument programu Word 2013
> - Word 2013 Template
> - Dokument programu Word 2010
> - Szablon programu Word 2010
>
>   Jeśli chcesz wykonać to zadanie w typie projektu, należy dodać odwołanie do **Microsoft.Office.Interop.Word** zestawu, a następnie należy użyć klas z tego zestawu na dodawanie wierszy i kolumn do tabel. Aby uzyskać więcej informacji, zobacz [jak: Konfigurowanie pod kątem aplikacji pakietu Office przy użyciu podstawowych zestawów międzyoperacyjnych](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) i [odwołanie do zestawu podstawowej usługi międzyoperacyjnej Word 2010](http://go.microsoft.com/fwlink/?LinkId=189588).

### <a name="to-add-a-row-to-a-table"></a>Aby dodać wiersz do tabeli

1. Użyj <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> metodę, aby dodać wiersz do tabeli.

     [!code-vb[Trin_VstcoreWordAutomation#95](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomation#95](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#95)]

### <a name="to-add-a-column-to-a-table"></a>Aby dodać kolumnę do tabeli

1. Użyj <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> metody, a następnie użyj <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> metodę, aby wyświetlić wszystkie kolumny taką samą szerokość.

     [!code-vb[Trin_VstcoreWordAutomation#96](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomation#96](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#96)]

## <a name="vsto-add-in-examples"></a>Przykłady dodatku narzędzi VSTO
 Poniższe przykłady kodu może służyć w dodatku VSTO. Aby użyć w przykładach, uruchomić je z `ThisAddIn` klasy w projekcie. W przykładach założono, że aktywny dokument ma już co najmniej jedna tabela.

> [!IMPORTANT]
> Ten kod zadziała tylko w projektach, które tworzysz przy użyciu szablonów w dodatku narzędzi VSTO programu Word.
>
> Jeśli chcesz wykonać to zadanie w typie projektu, należy dodać odwołanie do **Microsoft.Office.Interop.Word** zestawu, a następnie należy użyć klas z tego zestawu na dodawanie wierszy i kolumn do tabel. Aby uzyskać więcej informacji, zobacz [jak: Konfigurowanie pod kątem aplikacji pakietu Office przy użyciu podstawowych zestawów międzyoperacyjnych](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) i [odwołanie do zestawu podstawowej usługi międzyoperacyjnej Word 2010](http://go.microsoft.com/fwlink/?LinkId=189588).

### <a name="to-add-a-row-to-a-table"></a>Aby dodać wiersz do tabeli

1. Użyj <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> metodę, aby dodać wiersz do tabeli.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#95](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#95](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#95)]

### <a name="to-add-a-column-to-a-table"></a>Aby dodać kolumnę do tabeli

1. Użyj <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> metody, a następnie użyj <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> metodę, aby wyświetlić wszystkie kolumny taką samą szerokość.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#96](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#96](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#96)]

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Programowe tworzenie tabel programu Word](../vsto/how-to-programmatically-create-word-tables.md)
- [Instrukcje: Programowe Dodawanie tekstu i formatowania do komórek w tabelach programu Word](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)
- [Instrukcje: Programowe Wypełnianie tabel programu Word właściwościami dokumentu](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)
