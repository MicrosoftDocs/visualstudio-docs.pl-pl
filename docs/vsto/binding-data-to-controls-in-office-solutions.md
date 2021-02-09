---
title: Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office
description: Dowiedz się, w jaki sposób można powiązać kontrolki Windows Forms i kontrolki hosta w dokumencie Microsoft Office Word lub arkuszu programu Excel ze źródłem danych.
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
ms.openlocfilehash: 459c50b5f8135756f85de852a62de44b3878148d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882482"
---
# <a name="bind-data-to-controls-in-office-solutions"></a>Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office
  Można powiązać kontrolki Windows Forms i *kontrolki hosta* w dokumencie Microsoft Office Word lub Microsoft Office arkuszu programu Excel ze źródłem danych, aby kontrolki automatycznie wyświetlały dane. Dane można powiązać z kontrolkami zarówno w projektach na poziomie aplikacji, jak i na poziomie dokumentu.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Formanty hosta poszerzają obiekty, które znajdują się w modelach programów Word i Excel, takich jak kontrolki zawartości w programie Word i nazwane zakresy w programie Excel. Aby uzyskać więcej informacji, zobacz [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md).

 Zarówno Windows Forms, jak i formanty hosta używają modelu powiązań danych Windows Forms, który obsługuje zarówno *proste powiązanie danych* , jak i *złożone powiązanie danych* ze źródłami danych, takimi jak zestawy danych i tabele dane. Aby uzyskać pełne informacje na temat modelu powiązań danych w Windows Forms, zobacz [powiązane z danymi i Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

## <a name="simple-data-binding"></a>Proste powiązanie danych
 Proste powiązanie danych istnieje, gdy właściwość kontrolki jest powiązana z pojedynczym elementem danych, takim jak wartość w tabeli danych. Na przykład <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolka zawiera <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> Właściwość, która może być powiązana z polem w zestawie danych. Gdy pole w zestawie danych ulegnie zmianie, wartość w nazwanym zakresie zmienia się również. Wszystkie kontrolki hosta, z wyjątkiem <xref:Microsoft.Office.Tools.Word.XMLNodes> kontrolki, obsługują proste powiązanie danych. <xref:Microsoft.Office.Tools.Word.XMLNodes>Formant jest kolekcją i w związku z tym nie obsługuje powiązania danych.

 Aby wykonać proste powiązanie danych z kontrolką hosta, należy dodać <xref:System.Windows.Forms.Binding> do `DataBindings` właściwości kontrolki. <xref:System.Windows.Forms.Binding>Obiekt reprezentuje proste powiązanie między wartością właściwości kontrolki a wartością elementu danych.

 Poniższy przykład ilustruje sposób powiązania <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> właściwości z elementem danych w projekcie na poziomie dokumentu.

 [!code-vb[Trin_BindableComponent#4](../vsto/codesnippet/VisualBasic/Trin_BindableComponent/Sheet1.vb#4)]
 [!code-csharp[Trin_BindableComponent#4](../vsto/codesnippet/CSharp/Trin_BindableComponent/Sheet1.cs#4)]

 Aby zapoznać się z przewodnikami, które pokazują proste powiązanie danych, zobacz [Przewodnik: proste powiązanie danych w projekcie na poziomie](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md) dokumentu dla projektu na poziomie dokumentu i [Przewodnik: proste powiązanie danych w projekcie dodatku VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md) dla projektu dodatku VSTO.

## <a name="complex-data-binding"></a>Złożone powiązanie danych
 Złożone powiązanie danych istnieje, gdy właściwość kontrolki jest powiązana z więcej niż jednym elementem danych, takim jak wiele kolumn w tabeli danych. <xref:Microsoft.Office.Tools.Excel.ListObject>Formant dla programu Excel jest jedyną kontrolką hosta, która obsługuje złożone powiązanie danych. Istnieje również wiele Windows Forms formantów, które obsługują złożone powiązanie danych, takie jak <xref:System.Windows.Forms.DataGridView> kontrolka.

 Aby wykonać złożone powiązanie danych, ustaw `DataSource` Właściwość kontrolki na obiekt źródła danych, który jest obsługiwany przez złożone powiązanie danych. Na przykład <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> Właściwość <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki może być powiązana z wieloma kolumnami w tabeli danych. Wszystkie dane w tabeli danych są wyświetlane w <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolce, a w miarę zmiany danych w tabeli danych <xref:Microsoft.Office.Tools.Excel.ListObject> . Aby zapoznać się z listą źródeł danych, których można użyć do tworzenia złożonych powiązań danych, zobacz [źródła danych obsługiwane przez Windows Forms](/dotnet/framework/winforms/data-sources-supported-by-windows-forms).

 Poniższy przykład kodu tworzy <xref:System.Data.DataSet> z dwoma <xref:System.Data.DataTable> obiektami i wypełnia jedną z tabel danymi. Następnie kod tworzy powiązanie z <xref:Microsoft.Office.Tools.Excel.ListObject> tabelą zawierającą dane. Ten przykład dotyczy projektu na poziomie dokumentu programu Excel.

 [!code-csharp[Trin_ExcelListObject#18](../vsto/codesnippet/CSharp/Trin_ExcelListObject/Trin_ExcelListObject.cs#18)]
 [!code-vb[Trin_ExcelListObject#18](../vsto/codesnippet/VisualBasic/Trin_ExcelListObject/Sheet1.vb#18)]

 Aby zapoznać się ze wskazówkami, które demonstrują złożone powiązanie danych, zobacz [Przewodnik: złożone powiązanie danych w projekcie na poziomie](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md) dokumentu dla projektu na poziomie dokumentów i [Przewodnik: złożone powiązanie danych w projekcie dodatku VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md) dla projektu dodatku VSTO.

## <a name="display-data-in-documents-and-workbooks"></a>Wyświetlanie danych w dokumentach i skoroszytach
 W projektach na poziomie dokumentu, można użyć okna **źródła danych** , aby łatwo dodać kontrolki powiązane z danymi do dokumentów lub skoroszytów, tak samo jak w przypadku Windows Forms. Aby uzyskać więcej informacji o korzystaniu z okna **źródła danych** , zobacz [bind Windows Forms Controls to Data in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) i [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md).

### <a name="drag-controls-from-the-data-sources-window"></a>Przeciągnij kontrolki z okna źródła danych
 W dokumencie jest tworzony formant, gdy przeciągasz na niego obiekt z okna **źródła danych** . Typ formantu, który jest tworzony, zależy od tego, czy jest on powiązany z jedną kolumną danych, czy z wieloma kolumnami danych.

 Dla programu Excel w <xref:Microsoft.Office.Tools.Excel.NamedRange> arkuszu tworzony jest formant dla każdego pojedynczego pola, a <xref:Microsoft.Office.Tools.Excel.ListObject> dla każdego zakresu danych, który zawiera wiele wierszy i kolumn, tworzony jest formant. Można zmienić to ustawienie domyślne, wybierając tabelę lub pole w oknie **źródła danych** , a następnie wybierając inną kontrolkę z listy rozwijanej.

 <xref:Microsoft.Office.Tools.Word.ContentControl>Kontrolka jest dodawana do dokumentów. Typ formantu zawartości zależy od typu danych wybranego pola.

### <a name="bind-data-in-document-level-projects-at-design-time"></a>Powiąż dane w projektach na poziomie dokumentu w czasie projektowania
 W poniższych tematach przedstawiono przykłady powiązań danych w czasie projektowania:

- [Instrukcje: zapełnianie arkuszy danymi z bazy danych](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)

- [Instrukcje: zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md)

- [Instrukcje: zapełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md)

- [Instrukcje: zapełnianie dokumentów danymi z usług](../vsto/how-to-populate-documents-with-data-from-services.md)

- [Instrukcje: przewijanie rekordów bazy danych w arkuszu](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)

### <a name="bind-data-in-vsto-add-in-projects"></a>Powiązywanie danych w projektach dodatku narzędzi VSTO
 W projektach dodatku VSTO można dodawać kontrolki tylko w czasie wykonywania. W poniższych tematach przedstawiono przykłady powiązań danych w czasie wykonywania:

- [Przewodnik: proste powiązanie danych w projekcie dodatku VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)

- [Przewodnik: złożone powiązanie danych w projekcie dodatku VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md)

## <a name="update-data-that-is-bound-to-host-controls"></a>Aktualizowanie danych powiązanych z kontrolkami hosta
 Powiązanie danych między źródłem danych a kontrolką hosta obejmuje dwukierunkową aktualizację danych. W prostym powiązaniu danych zmiany w źródle danych są automatycznie odzwierciedlane w formancie hosta, ale zmiany w formancie hosta wymagają jawnego wywołania, aby zaktualizować źródło danych. Przyczyną jest to, że w niektórych przypadkach zmiany w jednym polu związanym z danymi nie są akceptowane, chyba że zostaną dołączone przez zmiany w innym polu związanym z danymi. Na przykład mogą istnieć dwa pola — jeden dla wieku i jeden dla lat doświadczenia. Środowisko pracy nie może przekroczyć wieku. Użytkownik nie może zaktualizować wieku z 50 do 25, a następnie doświadczenia z od 30 do 10, chyba że wprowadza zmiany w tym samym czasie. Aby rozwiązać ten problem, pola z prostym powiązaniem danych nie są aktualizowane, dopóki aktualizacje nie zostaną jawnie przesłane przez kod.

 Aby zaktualizować źródło danych z formantów hosta, które włączają proste powiązanie danych, należy wysłać aktualizacje do źródła danych znajdującego się w pamięci (na przykład <xref:System.Data.DataSet> lub <xref:System.Data.DataTable> ) oraz do bazy danych zaplecza, jeśli rozwiązanie używa jednego z nich.

 Nie musisz jawnie aktualizować źródła danych znajdującego się w pamięci podczas wykonywania złożonych powiązań danych przy użyciu <xref:Microsoft.Office.Tools.Excel.ListObject> formantu. W takim przypadku zmiany są automatycznie wysyłane do źródła danych znajdującego się w pamięci bez dodatkowego kodu.

 Aby uzyskać więcej informacji, zobacz [jak: aktualizowanie źródła danych przy użyciu danych z kontrolki hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

## <a name="see-also"></a>Zobacz też
- [Powiązanie danych i Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms)
- [Instrukcje: Tworzenie prostego formantu powiązanego w formularzu systemu Windows](/dotnet/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form)
- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
- [Aktualizowanie danych za pomocą adaptera TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)
- [Dane pamięci podręcznej](../vsto/caching-data.md)
- [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)
