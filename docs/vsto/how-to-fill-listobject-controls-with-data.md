---
title: '2017: wypełnianie kontrolek ListObject danymi'
description: Powiązanie danych umożliwia szybkie dodawanie danych do dokumentu. Możesz również odłączyć obiekt listy, aby wyświetlał dane, ale nie jest już powiązany ze źródłem danych.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disconnecting from data sources
- ListObject control, disconnecting from a data source
- ListObject control, filling with data
- data [Office development in Visual Studio], adding to worksheets
- data binding, ListObject controls
- worksheets, populating with data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 91fb4da23f388234e3800805e2beb3b7a8fbb20e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828920"
---
# <a name="how-to-fill-listobject-controls-with-data"></a>2017: wypełnianie kontrolek ListObject danymi
  Powiązania danych można użyć jako sposobu szybkiego dodawania danych do dokumentu. Po powiązaniu danych z obiektem listy można rozłączyć obiekt listy, aby wyświetlał dane, ale nie jest już powiązany ze źródłem danych.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

### <a name="to-bind-data-to-a-listobject-control"></a>Aby powiązać dane z kontrolką ListObject

1. Utwórz <xref:System.Data.DataTable> klasę na poziomie klasy.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs" id="Snippet20":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb" id="Snippet20":::

2. Dodaj przykładowe kolumny i dane w obsłudze zdarzeń klasy (w projekcie na poziomie dokumentu) lub klasy `Startup` `Sheet1` `ThisAddIn` (w projekcie na poziomie aplikacji).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs" id="Snippet21":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb" id="Snippet21":::

3. Wywołaj <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> metodę i przekaż nazwy kolumn w kolejności, w których powinny się pojawić. Kolejność kolumn w obiekcie listy może różnić się od kolejności, w jakiej występują w obiekcie <xref:System.Data.DataTable> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs" id="Snippet22":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb" id="Snippet22":::

### <a name="to-disconnect-the-listobject-control-from-the-data-source"></a>Aby odłączyć kontrolkę ListObject od źródła danych

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> metodę `List1` metody .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs" id="Snippet23":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb" id="Snippet23":::

## <a name="compile-the-code"></a>Kompilowanie kodu
 W tym przykładzie kodu przyjęto założenie, że w arkuszu, w którym pojawia się ten kod, znajduje się <xref:Microsoft.Office.Tools.Excel.ListObject> `list1` istniejąca nazwa.

## <a name="see-also"></a>Zobacz też
- [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatki VSTO w czasie uruchamiania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Kontrolki w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie rzeczywistym](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Jak mapować kolumny ListObject na dane](../vsto/how-to-map-listobject-columns-to-data.md)
- [Automatyzowanie programu Excel przy użyciu obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [ListObject, kontrolka](../vsto/listobject-control.md)
- [Wiązanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Jak wypełnić arkusze danymi z bazy danych](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Jak wypełnić dokumenty danymi z usług](../vsto/how-to-populate-documents-with-data-from-services.md)
