---
title: Jak dodać kontrolki wykresu do arkuszy
description: Dowiedz się, jak dodawać kontrolki wykresu do Microsoft Office programu Excel w czasie projektowania i w czasie uruchamiania w dostosowaniach na poziomie dokumentu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 88ebe38a881e148f10149189a2d27ac81bd0ddc2
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827035"
---
# <a name="how-to-add-chart-controls-to-worksheets"></a>Jak dodać kontrolki wykresu do arkuszy
  Kontrolki można dodawać do arkusza programu Microsoft Office Excel w czasie projektowania i w czasie uruchamiania w <xref:Microsoft.Office.Tools.Excel.Chart> dostosowaniach na poziomie dokumentu. Kontrolki można również <xref:Microsoft.Office.Tools.Excel.Chart> dodawać w czasie uruchamiania w dodatki VSTO.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 W tym temacie opisano następujące zadania:

- [Dodawanie kontrolek wykresu w czasie projektowania](#designtime)

- [Dodawanie kontrolek wykresu w czasie uruchamiania w projekcie na poziomie dokumentu](#runtimedoclevel)

- [Dodawanie kontrolek wykresu w czasie uruchamiania w projekcie dodatku VSTO](#runtimeaddin)

  Aby uzyskać więcej informacji na temat <xref:Microsoft.Office.Tools.Excel.Chart> kontrolek, zobacz [Kontrolka wykresu](../vsto/chart-control.md).

## <a name="add-chart-controls-at-design-time"></a><a name="designtime"></a> Dodawanie kontrolek wykresu w czasie projektowania
 Kontrolkę można dodać do arkusza w taki sam sposób, jak w przypadku dodawania <xref:Microsoft.Office.Tools.Excel.Chart> wykresu z poziomu aplikacji.

> [!NOTE]
> Kontrolka <xref:Microsoft.Office.Tools.Excel.Chart> nie jest dostępna w **przyborniku** ani w **oknie Źródła** danych.

### <a name="to-add-a-chart-host-control-to-a-worksheet-in-excel"></a>Aby dodać kontrolkę hosta wykresu do arkusza w programie Excel

1. Na karcie **Wstawianie** w grupie **Wykresy** kliknij pozycję **Kolumna,** kliknij kategorię wykresów, a następnie kliknij typ wykresu.

2. W **oknie dialogowym Wstawianie** wykresu kliknij przycisk **OK.**

3. Na karcie **Projekt** w grupie **Dane** kliknij pozycję **Wybierz dane.**

4. W **oknie dialogowym Wybieranie źródła** danych kliknij pole **Zakres** danych **wykresu** i wyczyść zaznaczenie domyślne.

5. W arkuszu **Dane wykresu** wybierz zakres komórek, które zawierają dane wykresu (komórki **od A5** do **D8).**

6. W **oknie dialogowym Wybieranie źródła** danych kliknij przycisk **OK.**

## <a name="add-chart-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Dodawanie kontrolek wykresu w czasie uruchamiania w projekcie na poziomie dokumentu
 Kontrolkę można <xref:Microsoft.Office.Tools.Excel.Chart> dodać dynamicznie w czasie uruchamiania. Dynamicznie tworzone wykresy nie są utrwalane w dokumencie jako kontrolki hosta po zamknięciu dokumentu. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie rzeczywistym.](../vsto/adding-controls-to-office-documents-at-run-time.md)

#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Aby programowo dodać kontrolkę Wykres do arkusza

1. W <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> programie obsługi zdarzeń `Sheet1` wstaw następujący kod, aby dodać <xref:Microsoft.Office.Tools.Excel.Chart> kontrolkę .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet1":::

## <a name="add-chart-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Dodawanie kontrolek wykresu w czasie uruchamiania w projekcie dodatku VSTO
 Kontrolkę można <xref:Microsoft.Office.Tools.Excel.Chart> dodać programowo do dowolnego otwartego arkusza w projekcie dodatku VSTO. Aby uzyskać więcej informacji, zobacz [Extend Word documents and Excel workbooks in VSTO Add-ins at run time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)(Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatki VSTO w czasie uruchamiania).

 Dynamicznie tworzone kontrolki wykresu nie są utrwalane w arkuszu jako kontrolki hosta po zamknięciu arkusza. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie rzeczywistym.](../vsto/adding-controls-to-office-documents-at-run-time.md)

#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Aby programowo dodać kontrolkę Wykres do arkusza

1. Poniższy kod generuje element hosta arkusza, który jest oparty na otwartym arkuszu, a następnie dodaje <xref:Microsoft.Office.Tools.Excel.Chart> kontrolkę.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet9":::

## <a name="compile-the-code"></a>Kompilowanie kodu
 Ten przykład ma następujące wymagania:

- Dane, które mają być na wykresie, przechowywane w zakresie od A5 do D8 w arkuszu.

## <a name="see-also"></a>Zobacz też
- [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatki VSTO w czasie uruchamiania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Kontrolki w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Kontrolka wykresu](../vsto/chart-control.md)
- [Automatyzowanie programu Excel przy użyciu obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
- [Wiązanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Programowe ograniczenia elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
