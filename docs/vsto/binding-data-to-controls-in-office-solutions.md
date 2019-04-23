---
title: Wiązanie danych do kontrolek w rozwiązaniach pakietu Office
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1bbcbc2411d261b4ddec9423896dc21acc3e0033
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60073738"
---
# <a name="bind-data-to-controls-in-office-solutions"></a>Wiązanie danych do kontrolek w rozwiązaniach pakietu Office
  Możesz powiązać kontrolek formularzy Windows Forms i *hostowania kontrolek* na dokument programu Microsoft Office Word lub skoroszyt programu Microsoft Office Excel ze źródłem danych, więc formanty automatycznie wyświetlać dane. Dane można powiązać formanty w projektach na poziomie dokumentu i poziomie aplikacji.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Formanty hosta rozszerzyć obiektów, które znajdują się w programach Word i Excel modeli obiektów, takich jak formanty zawartości w programie Word lub nazwane zakresy w programie Excel. Aby uzyskać więcej informacji, zobacz [elementów, a omówienie kontrolek](../vsto/host-items-and-host-controls-overview.md).

 Zarówno Windows Forms i kontrolek hosta przy użyciu modelu powiązanie danych formularzy Windows, który obsługuje zarówno *proste powiązanie danych* i *złożone powiązanie danych* ze źródłami danych, takich jak zestawy danych i tabel danych. Aby uzyskać pełne informacje o modelu powiązanie danych w formularzach Windows Forms, zobacz [powiązanie danych i formularze Windows](/dotnet/framework/winforms/data-binding-and-windows-forms).

 ![Link do wideo](../vsto/media/playvideo.gif "link do wideo") powiązane demonstracyjne wideo – zobacz [jak: Używanie bazy danych w programie Excel? ](http://go.microsoft.com/fwlink/?LinkID=130287).

## <a name="simple-data-binding"></a>Proste powiązanie danych
 Proste powiązanie danych występuje, gdy właściwość formantu jest powiązana z elementu danych jednego, takiego jak wartość w tabeli danych. Na przykład <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> właściwość, która może być powiązany z polem w zestawie danych. Po zmianie pola w zestawie danych zmienia się również wartość nazwanego zakresu Wszystkie hosta formantów, z wyjątkiem <xref:Microsoft.Office.Tools.Word.XMLNodes> sterowania, pomocy technicznej proste powiązanie danych. <xref:Microsoft.Office.Tools.Word.XMLNodes> Formantu kolekcji, i dlatego nie obsługuje powiązanie danych.

 Aby wykonać proste powiązanie danych z kontrolką hosta, Dodaj <xref:System.Windows.Forms.Binding> do `DataBindings` właściwości formantu. A <xref:System.Windows.Forms.Binding> obiekt reprezentuje proste powiązanie między wartością właściwości formantu, a wartość elementu danych.

 Poniższy przykład pokazuje jak powiązać <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> właściwość elementu danych w projekcie na poziomie dokumentu.

 [!code-vb[Trin_BindableComponent#4](../vsto/codesnippet/VisualBasic/Trin_BindableComponent/Sheet1.vb#4)]
 [!code-csharp[Trin_BindableComponent#4](../vsto/codesnippet/CSharp/Trin_BindableComponent/Sheet1.cs#4)]

 Aby uzyskać wskazówki, który demonstruje proste powiązanie danych, zobacz [instruktażu: Proste powiązanie danych w projekcie na poziomie dokumentu](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md) dla projektu na poziomie dokumentu i [instruktażu: Proste powiązanie danych w projekcie dodatku narzędzi VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md) w projekcie dodatku narzędzi VSTO.

## <a name="complex-data-binding"></a>Złożone powiązanie danych
 Złożone powiązanie danych występuje, gdy właściwość formantu jest powiązana z więcej niż jednego elementu danych, takich jak wiele kolumn w tabeli danych. <xref:Microsoft.Office.Tools.Excel.ListObject> Sterowania dla programu Excel jest jedynym formantem hosta, która obsługuje złożone powiązanie danych. Dostępne są także wiele kontrolek formularzy Windows, które obsługują złożone powiązanie danych, takie jak <xref:System.Windows.Forms.DataGridView> kontroli.

 Aby wykonać złożone powiązanie danych, należy ustawić `DataSource` właściwości formantu do obiektu źródła danych, która jest obsługiwana przez złożone powiązanie danych. Na przykład <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> właściwość <xref:Microsoft.Office.Tools.Excel.ListObject> kontroli można powiązać z wielu kolumn w tabeli danych. Wszystkie dane w tabeli danych pojawia się w <xref:Microsoft.Office.Tools.Excel.ListObject> kontroli i z danymi w tabeli zmian danych, <xref:Microsoft.Office.Tools.Excel.ListObject> zmienia także. Aby uzyskać listę źródeł danych, które umożliwiają złożone powiązanie danych, zobacz [źródła danych obsługiwane przez formularze Windows](/dotnet/framework/winforms/data-sources-supported-by-windows-forms).

 Poniższy przykład kodu tworzy <xref:System.Data.DataSet> przy użyciu dwóch <xref:System.Data.DataTable> obiektów i wypełnia jednej z tabel z danymi. Kod następnie powiąże <xref:Microsoft.Office.Tools.Excel.ListObject> do tabeli, która zawiera dane. Ten przykład dotyczy programu Excel projektów dokumentów.

 [!code-csharp[Trin_ExcelListObject#18](../vsto/codesnippet/CSharp/Trin_ExcelListObject/Trin_ExcelListObject.cs#18)]
 [!code-vb[Trin_ExcelListObject#18](../vsto/codesnippet/VisualBasic/Trin_ExcelListObject/Sheet1.vb#18)]

 Aby uzyskać wskazówki dotyczące pokazują złożone powiązanie danych, zobacz [instruktażu: Złożone powiązanie danych w projekcie na poziomie dokumentu](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md) dla projektu na poziomie dokumentu i [instruktażu: Złożone powiązanie danych w projekcie dodatku narzędzi VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md) w projekcie dodatku narzędzi VSTO.

## <a name="display-data-in-documents-and-workbooks"></a>Wyświetlanie danych w dokumentach i skoroszyty
 W projektach na poziomie dokumentu można używać **źródeł danych** okna można łatwo dodać formanty powiązane z danymi do dokumentów lub skoroszytów, ten sam sposób, możesz użyć dla formularzy Windows Forms. Aby uzyskać więcej informacji o korzystaniu z **źródeł danych** okna, zobacz [formanty powiązania formularzy Windows do danych w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) i [dodasz nowe źródła danych](../data-tools/add-new-data-sources.md).

### <a name="drag-controls-from-the-data-sources-window"></a>Przeciągnij formanty z okna źródeł danych
 Formant jest tworzony w dokumencie po przeciągnięciu obiektu na jego z **źródeł danych** okna. Typ kontrolki, który jest tworzony zależy od tego, czy powiązanie pojedynczej kolumny danych lub wiele kolumn z danymi.

 Dla programu Excel <xref:Microsoft.Office.Tools.Excel.NamedRange> formant zostanie utworzony w arkuszu dla każdego indywidualnego pola i <xref:Microsoft.Office.Tools.Excel.ListObject> kontroli jest tworzony dla każdego zakresu danych, który zawiera wiele wierszy i kolumn. Możesz zmienić to ustawienie domyślne, wybierając tabelę lub pole **źródeł danych** okna, a następnie wybierając innej kontrolki z listy rozwijanej.

 A <xref:Microsoft.Office.Tools.Word.ContentControl> formant jest dodawany do dokumentów. Typ zawartości kontrolki zależy od typu danych pola, które wybrano.

### <a name="bind-data-in-document-level-projects-at-design-time"></a>Powiązanie danych w projektach na poziomie dokumentu w czasie projektowania
 Poniższe tematy przedstawiają przykłady powiązanie danych w czasie projektowania:

- [Instrukcje: Zapełnianie arkuszy danymi z bazy danych](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)

- [Instrukcje: Zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md)

- [Instrukcje: Zapełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md)

- [Instrukcje: Zapełnianie dokumentów danymi z usług](../vsto/how-to-populate-documents-with-data-from-services.md)

- [Instrukcje: Przewijanie rekordów bazy danych w arkuszu](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)

### <a name="bind-data-in-vsto-add-in-projects"></a>Powiązanie danych w projektach dodatku narzędzi VSTO
 W projektach dodatku narzędzi VSTO formanty można dodać tylko w czasie wykonywania. Poniższe tematy przedstawiają przykłady powiązanie danych w czasie wykonywania:

- [Przewodnik: Proste powiązanie danych w projekcie dodatku narzędzi VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)

- [Przewodnik: Złożone powiązanie danych w projekcie dodatku narzędzi VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md)

## <a name="update-data-that-is-bound-to-host-controls"></a>Aktualizowanie danych, który jest powiązany z kontrolki hosta
 Powiązanie danych między źródłem danych i kontrolki hosta obejmuje aktualizację dwukierunkowe danych. W proste powiązanie danych, zmiany w źródle danych są automatycznie odzwierciedlane w kontrolce hosta, ale zmiany w kontrolce hosta wymagają jawnym wywołaniem można zaktualizować źródła danych. Przyczyną jest to, że w niektórych przypadkach, zmiany w jednym polu powiązanych z danymi nie są akceptowane, chyba że towarzyszy im zmiany w innym polu powiązanych z danymi. Na przykład możesz mieć dwa pola, jeden dla wieku i jeden dla lat doświadczenia. Środowisko nie może przekraczać wieku. Użytkownik nie może zaktualizować wiek od 50 do 25, a następnie doświadczenie od 30 do 10, chyba że użytkownik wprowadza zmiany w tym samym czasie. Aby rozwiązać ten problem, pola z proste powiązanie danych nie są aktualizowane, dopóki aktualizacje jawnie są wysyłane przez kod.

 Aby zaktualizować źródła danych z kontrolki hosta, które umożliwiają proste powiązanie danych, konieczne jest wysłanie aktualizacji do źródła danych w pamięci (takie jak <xref:System.Data.DataSet> lub <xref:System.Data.DataTable>) i bazy danych zaplecza, jeśli rozwiązanie używa jednego.

 Nie trzeba jawnie zaktualizować źródło danych w pamięci, gdy wykonujesz złożone powiązanie danych przy użyciu <xref:Microsoft.Office.Tools.Excel.ListObject> kontroli. W takim przypadku zmiany są automatycznie wysyłane do źródła danych w pamięci bez dodatkowego kodu.

 Aby uzyskać więcej informacji, zobacz [jak: Aktualizowanie źródła danych danymi z kontrolki hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

## <a name="see-also"></a>Zobacz także
- [Powiązanie danych oraz Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms)
- [Instrukcje: Tworzenie prostego formantu powiązanego na formularzu Windows](/dotnet/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form)
- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
- [Aktualizowanie danych za pomocą adaptera TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)
- [Dane w pamięci podręcznej](../vsto/caching-data.md)
- [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)
