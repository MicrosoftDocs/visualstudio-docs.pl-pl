---
title: 'How to: Map ListObject columns to data (Jak mapować kolumny ListObject na dane)'
description: Dowiedz się, jak mapować kolumny, które mają być wyświetlane w obiektach ListObject podczas wywołania metody SetDataBinding.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], mapping to ListObject column
- ListObject control, mapping data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 68cb12503d0f8ad59de92f965c0ed51fbc0d7f40
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827464"
---
# <a name="how-to-map-listobject-columns-to-data"></a>How to: Map ListObject columns to data (Jak mapować kolumny ListObject na dane)
  Powiązanie kontrolki z kontrolką może nie być konieczne wyświetlanie wszystkich kolumn na liście lub niektórych kolumn, które nie <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:System.Data.DataTable> są powiązane z danymi. Można mapować kolumny, które mają być wyświetlane w metodzie <xref:Microsoft.Office.Tools.Excel.ListObject> podczas wywołania <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> metody .

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="map-columns"></a>Mapowanie kolumn

### <a name="to-map-a-data-table-to-columns-in-a-list"></a>Aby zamapować tabelę danych na kolumny na liście

1. Utwórz <xref:System.Data.DataTable> klasę na poziomie klasy.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet16":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet16":::

2. Dodaj przykładowe kolumny i dane w programie obsługi zdarzeń klasy (w projekcie na poziomie dokumentu) lub klasy `Startup` `Sheet1` `ThisAddIn` (w projekcie dodatku VSTO).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet17":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet17":::

3. Wywołaj <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> metodę i przekaż nazwy kolumn w kolejności, w których powinny się pojawić. Obiekt listy zostanie powiązany z nowo utworzonym obiektem , ale kolejność kolumn w obiekcie listy będzie się różnić od kolejności, w których występują <xref:System.Data.DataTable> w <xref:System.Data.DataTable> obiekcie .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet18":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet18":::

## <a name="specify-unmapped-columns"></a>Określanie niezamapowanych kolumn
 Podczas mapowania kolumn na element można również określić, że niektóre kolumny nie powinny być powiązane z danymi, przekazując <xref:System.Data.DataTable> pusty ciąg. Nowa kolumna, która nie jest powiązana z danymi, jest następnie dodawana do <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki.

### <a name="to-specify-an-unmapped-column-when-mapping-listobject-columns"></a>Aby określić niezamapowane kolumny podczas mapowania kolumn ListObject

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> metodę i przekaż nazwy kolumn w kolejności, w których powinny się pojawić. Użyj pustego ciągu, aby wskazać, gdzie jest dodawana niezamapowana kolumna; w tym przypadku między kolumną tytułu a kolumną nazwiska.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet19":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet19":::

## <a name="compile-the-code"></a>Kompilowanie kodu
 W tym przykładzie kodu założono, że masz istniejącą <xref:Microsoft.Office.Tools.Excel.ListObject> nazwę `list1` w arkuszu, w którym ten kod jest wyświetlany.

## <a name="see-also"></a>Zobacz też
- [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatki VSTO w czasie uruchamiania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Kontrolki w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie rzeczywistym](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [2017: wypełnianie kontrolek ListObject danymi](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Automatyzowanie programu Excel przy użyciu obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [ListObject, kontrolka](../vsto/listobject-control.md)
