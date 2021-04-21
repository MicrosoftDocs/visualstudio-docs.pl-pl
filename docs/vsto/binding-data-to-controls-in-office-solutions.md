---
title: Wiązanie danych z kontrolkami w rozwiązaniach pakietu Office
description: Dowiedz się, jak powiązać kontrolki Windows Forms i kontrolki hosta w dokumencie Microsoft Office word lub arkuszu programu Excel ze źródłem danych.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio], connecting to data
- data, data binding
- data binding
- data binding, Office solutions
- data binding, controls
- Office applications [Office development in Visual Studio], data binding
- controls, data binding
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ccc45e9ec389e265e69c81baaf569aa3eb3c978b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825631"
---
# <a name="bind-data-to-controls-in-office-solutions"></a>Wiązanie danych z kontrolkami w rozwiązaniach pakietu Office
  Kontrolki Windows Forms i kontrolki  hosta w dokumencie programu Microsoft Office Word lub Microsoft Office excel można powiązać ze źródłem danych, aby kontrolki automatycznie wyświetlały dane. Dane można powiązać z kontrolkami w projektach zarówno na poziomie aplikacji, jak i na poziomie dokumentu.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Kontrolki hosta rozszerzają obiekty w modelach obiektów programów Word i Excel, takie jak kontrolki zawartości w programie Word i nazwane zakresy w programie Excel. Aby uzyskać więcej informacji, zobacz [Host items and host controls overview (Omówienie elementów hosta i kontrolek hosta).](../vsto/host-items-and-host-controls-overview.md)

 Zarówno Windows Forms, jak i kontrolki hosta używają modelu powiązania danych  Windows Forms,  który obsługuje zarówno proste powiązanie danych, jak i złożone powiązanie danych ze źródłami danych, takimi jak zestawy danych i tabele danych. Aby uzyskać pełne informacje na temat modelu powiązania danych w Windows Forms, zobacz Powiązanie danych [i Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

## <a name="simple-data-binding"></a>Proste powiązanie danych
 Proste powiązanie danych istnieje, gdy właściwość kontrolki jest powiązana z pojedynczym elementem danych, takim jak wartość w tabeli danych. Na przykład <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolka ma <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> właściwość, która może być powiązana z polem w zestawie danych. Po zmianie pola w zestawie danych zmienia się również wartość w nazwanych zakresach. Wszystkie kontrolki hosta, z wyjątkiem <xref:Microsoft.Office.Tools.Word.XMLNodes> kontrolki, obsługują proste powiązanie danych. Kontrolka <xref:Microsoft.Office.Tools.Word.XMLNodes> jest kolekcją i dlatego nie obsługuje powiązania danych.

 Aby wykonać proste powiązanie danych z kontrolką hosta, dodaj do <xref:System.Windows.Forms.Binding> `DataBindings` właściwości kontrolki . Obiekt <xref:System.Windows.Forms.Binding> reprezentuje proste powiązanie między wartością właściwości kontrolki a wartością elementu danych.

 W poniższym przykładzie pokazano, jak powiązać <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> właściwość z elementem danych w projekcie na poziomie dokumentu.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_BindableComponent/Sheet1.vb" id="Snippet4":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_BindableComponent/Sheet1.cs" id="Snippet4":::

 Aby uzyskać wskazówki demonstrują proste powiązanie danych, zobacz [Przewodnik:](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md) proste powiązanie danych w projekcie na poziomie dokumentu dla projektu na poziomie dokumentu i [Przewodnik: proste](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md) powiązanie danych w projekcie dodatku VSTO dla projektu dodatku VSTO.

## <a name="complex-data-binding"></a>Złożone powiązanie danych
 Złożone powiązanie danych istnieje, gdy właściwość kontrolki jest powiązana z więcej niż jednym elementem danych, takim jak wiele kolumn w tabeli danych. Kontrolka <xref:Microsoft.Office.Tools.Excel.ListObject> programu Excel jest jedyną kontrolką hosta, która obsługuje złożone powiązanie danych. Istnieje również wiele kontrolek Windows Forms, które obsługują złożone powiązania danych, takich jak <xref:System.Windows.Forms.DataGridView> kontrolka.

 Aby wykonać złożone powiązanie danych, ustaw właściwość kontrolki na obiekt źródła danych obsługiwany `DataSource` przez złożone powiązanie danych. Na przykład właściwość <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> kontrolki może <xref:Microsoft.Office.Tools.Excel.ListObject> być powiązana z wieloma kolumnami w tabeli danych. Wszystkie dane w tabeli danych są wyświetlane w kontrolce, a w przypadku zmiany danych w tabeli danych również <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:Microsoft.Office.Tools.Excel.ListObject> te zmiany. Aby uzyskać listę źródeł danych, których można użyć do złożonego powiązania danych, zobacz Źródła danych [obsługiwane](/dotnet/framework/winforms/data-sources-supported-by-windows-forms)przez Windows Forms .

 Poniższy przykład kodu tworzy obiekt <xref:System.Data.DataSet> z dwoma <xref:System.Data.DataTable> obiektami i wypełnia jedną z tabel danymi. Następnie kod wiąże tabelę <xref:Microsoft.Office.Tools.Excel.ListObject> z tabelą zawierającą dane. Ten przykład dotyczy projektu na poziomie dokumentu programu Excel.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelListObject/Trin_ExcelListObject.cs" id="Snippet18":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ExcelListObject/Sheet1.vb" id="Snippet18":::

 Aby uzyskać wskazówki demonstrują złożone powiązanie danych, zobacz [Przewodnik:](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md) złożone powiązanie danych w projekcie na poziomie dokumentu dla projektu na poziomie dokumentu i [Przewodnik: złożone](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md) powiązanie danych w projekcie dodatku VSTO dla projektu dodatku VSTO.

## <a name="display-data-in-documents-and-workbooks"></a>Wyświetlanie danych w dokumentach i skoroszytach
 W projektach na poziomie dokumentu  można użyć okna Źródła danych, aby łatwo dodawać kontrolki powiązane z danymi do dokumentów lub skoroszytów, tak samo jak w przypadku Windows Forms. Aby uzyskać więcej informacji na temat korzystania z **okna Źródła** danych, zobacz [Wiązanie kontrolek Windows Forms z](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) danymi w programie Visual Studio i Dodawanie nowych źródeł [danych.](../data-tools/add-new-data-sources.md)

### <a name="drag-controls-from-the-data-sources-window"></a>Przeciąganie kontrolek z okna Źródła danych
 Kontrolka jest tworzona w dokumencie podczas przeciągania na niego obiektu z **okna Źródła** danych. Typ tworzonej kontrolki zależy od tego, czy tworzysz powiązanie pojedynczej kolumny danych, czy wielu kolumn danych.

 W przypadku programu Excel kontrolka jest tworzona w arkuszu dla każdego pola, a kontrolka jest tworzona dla każdego zakresu danych, który <xref:Microsoft.Office.Tools.Excel.NamedRange> zawiera wiele wierszy i <xref:Microsoft.Office.Tools.Excel.ListObject> kolumn. Możesz zmienić to ustawienie domyślne, wybierając tabelę lub pole w oknie **Źródła** danych, a następnie wybierając inną kontrolkę z listy rozwijanej.

 Kontrolka <xref:Microsoft.Office.Tools.Word.ContentControl> jest dodawana do dokumentów. Typ kontrolki zawartości zależy od typu danych wybranego pola.

### <a name="bind-data-in-document-level-projects-at-design-time"></a>Wiązanie danych w projektach na poziomie dokumentu w czasie projektowania
 W poniższych tematach przedstawiono przykłady powiązań danych w czasie projektowania:

- [Jak wypełnić arkusze danymi z bazy danych](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)

- [How to: Populate documents with data from a database (Jak wypełnić dokumenty danymi z bazy danych)](../vsto/how-to-populate-documents-with-data-from-a-database.md)

- [Jak wypełnić dokumenty danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md)

- [Jak wypełnić dokumenty danymi z usług](../vsto/how-to-populate-documents-with-data-from-services.md)

- [How to: Scroll through database records in a worksheet (Jak przewijać rekordy bazy danych w arkuszu)](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)

### <a name="bind-data-in-vsto-add-in-projects"></a>Wiązanie danych w projektach dodatków VSTO
 W projektach dodatków VSTO kontrolki można dodawać tylko w czasie uruchamiania. W poniższych tematach przedstawiono przykłady powiązania danych w czasie działania:

- [Przewodnik: proste powiązanie danych w projekcie dodatku VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)

- [Przewodnik: złożone powiązanie danych w projekcie dodatku VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md)

## <a name="update-data-that-is-bound-to-host-controls"></a>Aktualizowanie danych powiązanych z kontrolkami hosta
 Powiązanie danych między źródłem danych i kontrolką hosta obejmuje dwukierunkową aktualizację danych. W przypadku prostego powiązania danych zmiany w źródle danych są odzwierciedlane automatycznie w kontrolce hosta, ale zmiany w kontrolce hosta wymagają jawnego wywołania w celu zaktualizowania źródła danych. Przyczyną jest to, że w niektórych przypadkach zmiany w jednym polu powiązanym z danymi nie są akceptowane, chyba że towarzyszy im zmiana w innym polu powiązanym z danymi. Na przykład możesz mieć dwa pola: jedno dla wieku i jedno dla lat doświadczenia. Doświadczenie nie może przekraczać wieku. Użytkownik nie może zaktualizować wieku od 50 do 25 lat, a następnie doświadczenia z 30 do 10, chyba że wprowadza zmiany w tym samym czasie. Aby rozwiązać ten problem, pola z prostym powiązaniem danych nie są aktualizowane, dopóki aktualizacje nie zostaną jawnie wysłane przez kod.

 Aby zaktualizować źródło danych z kontrolek hosta, które umożliwiają proste powiązanie danych, należy wysłać aktualizacje do źródła danych w pamięci (takiego jak lub ) i do bazy danych wewnętrznej bazy danych, jeśli rozwiązanie z nich <xref:System.Data.DataSet> <xref:System.Data.DataTable> korzysta.

 Nie trzeba jawnie aktualizować źródła danych w pamięci podczas wykonywania złożonego powiązania danych przy użyciu <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki . W takim przypadku zmiany są automatycznie wysyłane do źródła danych w pamięci bez dodatkowego kodu.

 Aby uzyskać więcej informacji, zobacz How to: Update a data source with data from a host control ( Jak [zaktualizować źródło danych przy użyciu danych z kontrolki hosta).](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)

## <a name="see-also"></a>Zobacz też
- [Powiązanie danych i Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms)
- [Jak utworzyć prostą powiązaną kontrolkę w formularzu systemu Windows](/dotnet/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form)
- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
- [Aktualizowanie danych za pomocą adaptera TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)
- [Dane pamięci podręcznej](../vsto/caching-data.md)
- [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)
