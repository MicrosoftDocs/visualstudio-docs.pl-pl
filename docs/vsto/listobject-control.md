---
title: ListObject — formant
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.List
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- lists, events
- ListObject control
- ListObject control, events
- ListObject control, data binding
- ListObject control, improving performance when bound to data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 39156994caa9e6ec073a05b0d8d04edab40e11e7
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56609387"
---
# <a name="listobject-control"></a>ListObject — formant
  <xref:Microsoft.Office.Tools.Excel.ListObject> Formant jest listę, która udostępnia zdarzenia i może być powiązana z danymi. Po dodaniu listy do arkusza programu Visual Studio tworzy <xref:Microsoft.Office.Tools.Excel.ListObject> formant, który można programować względem bezpośrednio, bez konieczności przechodzenia z modelu obiektów programu Microsoft Office Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="create-the-control"></a>Tworzenie formantu
 W projektach na poziomie dokumentu, można dodać <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolek do arkusza w czasie projektowania lub w czasie wykonywania. W projektach dodatku narzędzi VSTO dla programów, można dodać <xref:Microsoft.Office.Tools.Excel.ListObject> formantów do arkuszy tylko w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie formantów ListObject do arkuszy](../vsto/how-to-add-listobject-controls-to-worksheets.md).

> [!NOTE]
>  Domyślnie, dynamicznie utworzoną listę obiektów, nie są zachowywane w arkuszu zgodnie z kontrolki hosta po zamknięciu arkusza. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w środowisku uruchomieniowym](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="bind-data-to-the-control"></a>Wiązanie danych do kontrolki
 A <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolka obsługuje powiązanie danych proste i złożone. <xref:Microsoft.Office.Tools.Excel.ListObject> Kontroli można powiązać źródła danych przy użyciu <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> i <xref:Microsoft.Office.Tools.Excel.ListObject.DataMember%2A> właściwości w czasie projektowania lub <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> metody w czasie wykonywania.

> [!NOTE]
>  <xref:Microsoft.Office.Tools.Excel.ListObject> Jest aktualizowana automatycznie, gdy jest powiązany ze źródłem danych, takich jak <xref:System.Data.DataTable>, która wywołuje zdarzenia, po zmianie danych. Jeżeli powiążesz <xref:Microsoft.Office.Tools.Excel.ListObject> ze źródłem danych, który nie powoduje zdarzenia po zmianie danych, należy wywołać <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRow%2A> lub <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRows%2A> metodę, aby zaktualizować <xref:Microsoft.Office.Tools.Excel.ListObject>.

 Po dodaniu <xref:Microsoft.Office.Tools.Excel.ListObject> do komórki arkusza przez mapowanie elementu schematu powtarzające się do tej komórki, Visual Studio automatycznie mapuje <xref:Microsoft.Office.Tools.Excel.ListObject> do wygenerowanego zestawu danych. Jednak <xref:Microsoft.Office.Tools.Excel.ListObject> automatycznie nie jest powiązany z danymi. Możesz wykonać kroki, aby powiązać <xref:Microsoft.Office.Tools.Excel.ListObject> do zestawu danych w czasie projektowania lub w czasie wykonywania w projekcie na poziomie dokumentu. Możesz programowo powiązać <xref:Microsoft.Office.Tools.Excel.ListObject> do zestawu danych w czasie wykonywania w dodatku VSTO.

 Ponieważ dane są niezależne od <xref:Microsoft.Office.Tools.Excel.ListObject>, należy dodać i usunąć dane za pomocą zestawu powiązanych danych, a nie bezpośrednio za pomocą <xref:Microsoft.Office.Tools.Excel.ListObject>. Jeśli dane w zestawie danych powiązane są aktualizowane przy użyciu dowolnego mechanizmu <xref:Microsoft.Office.Tools.Excel.ListObject> kontroli automatycznie uwzględnia zmiany. Aby uzyskać więcej informacji, zobacz [wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).

 Można szybko wypełniać <xref:Microsoft.Office.Tools.Excel.ListObject> kontroli przez powiązanie <xref:Microsoft.Office.Tools.Excel.ListObject> ze źródłem danych. Jeśli edytujesz danych powiązanych z danymi <xref:Microsoft.Office.Tools.Excel.ListObject>, zmiany zostaną zastosowane automatycznie ze źródła danych. Jeśli chcesz wypełnić <xref:Microsoft.Office.Tools.Excel.ListObject> , a następnie Włącz użytkownikowi na zmianę danych w <xref:Microsoft.Office.Tools.Excel.ListObject> bez modyfikowania źródła danych, możesz użyć <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> metodę, aby odłączyć <xref:Microsoft.Office.Tools.Excel.ListObject> ze źródła danych. Aby uzyskać więcej informacji, zobacz [jak: Wypełnianie formantów ListObject danymi](../vsto/how-to-fill-listobject-controls-with-data.md).

> [!NOTE]
>  Powiązanie danych nie jest obsługiwana w nakładających się <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki.

### <a name="improve-performance-in-listobject-controls"></a>Poprawić wydajność w formantów ListObject
 Odczytywanie pliku XML do powiązanych z danymi <xref:Microsoft.Office.Tools.Excel.ListObject> formant jest zwykle wolniej, jeśli najpierw powiązać formant, a następnie wywołaj <xref:System.Data.DataSet.ReadXml%2A> do wypełniania zestawu danych. Aby zwiększyć wydajność, należy wywołać <xref:System.Data.DataSet.ReadXml%2A> przed powiązać formant.

### <a name="disconnect-listobject-controls-from-the-data-source"></a>Odłącz formantów ListObject ze źródła danych
 Po wypełnieniu <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki z danymi, tworząc powiązanie ze źródłem danych, można go odłączyć tak, aby modyfikacje wprowadzone do danych w obiekcie listy nie wpływają na źródle danych. Aby uzyskać więcej informacji, zobacz [jak: Wypełnianie formantów ListObject danymi](../vsto/how-to-fill-listobject-controls-with-data.md).

### <a name="restore-column-and-row-order"></a>Przywróć kolejność kolumn i wierszy
 Po powiązaniu danych w celu <xref:Microsoft.Office.Tools.Excel.ListObject> formant, który został dodany do dokumentu w czasie projektowania programu Visual Studio przechowuje informacje o kolejności wierszy i kolumn w każdym przypadku, gdy skoroszyt jest zapisywany. Jeśli użytkownik przenosi <xref:Microsoft.Office.Tools.Excel.ListObject> kolumny lub wiersze, w czasie wykonywania, nową kolejność jest zachowywana przy następnym otwarciu skoroszytu i <xref:Microsoft.Office.Tools.Excel.ListObject> kontroli wiąże się ze źródłem danych ponownie.

 Jeśli chcesz przywrócić <xref:Microsoft.Office.Tools.Excel.ListObject> do oryginalnych kolumn i kolejności wierszy można wywołać <xref:Microsoft.Office.Tools.Excel.ListObject.ResetPersistedBindingInformation%2A> metody. Ta metoda usuwa właściwości niestandardowego dokumentu dotyczące kolumny i kolejność wierszy określone <xref:Microsoft.Office.Tools.Excel.ListObject>. Wywołanie tej metody z <xref:Microsoft.Office.Tools.Excel.Workbook.Shutdown> zdarzeń skoroszytu, jeśli nie chcesz zachować kolejność kolumn i wierszy <xref:Microsoft.Office.Tools.Excel.ListObject>.

## <a name="format"></a>Format
 Formatowanie, które mogą być stosowane do <xref:Microsoft.Office.Interop.Excel.ListObject> mogą być stosowane do <xref:Microsoft.Office.Tools.Excel.ListObject> kontroli. W tym obramowania, czcionki, format liczb i stylów. Użytkownicy końcowi mogą zmieniać kolejności kolumn w powiązanych z danymi <xref:Microsoft.Office.Tools.Excel.ListObject>, a te zmiany zostaną utrwalone w dokumencie, pod warunkiem <xref:Microsoft.Office.Tools.Excel.ListObject> został dodany do dokumentu w czasie projektowania. Przy następnym otwarciu dokumentu na obiekt listy, które będą powiązane z tym samym źródłem danych, ale kolejność kolumn będzie odzwierciedlać zmiany wprowadzone przez użytkowników.

## <a name="add-and-remove-columns-at-runtime"></a>Dodawanie i usuwanie kolumn w czasie wykonywania
 Nie można ręcznie dodać lub usunąć kolumny w powiązanym z danymi <xref:Microsoft.Office.Tools.Excel.ListObject> formantu w czasie wykonywania. Jeśli użytkownik końcowy próbuje usunąć kolumnę, zostanie natychmiast przywrócona i wszystkie kolumny dodane zostaną usunięte. Dlatego jest ważne, aby napisać kod, Wyjaśnij użytkownikom, dlaczego nie mogą wykonywać te akcje na <xref:Microsoft.Office.Tools.Excel.ListObject> , jest powiązany z danymi. Program Visual Studio zapewnia kilka zdarzeń na <xref:Microsoft.Office.Tools.Excel.ListObject> związane z powiązanie danych. Na przykład, można użyć <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored> zdarzenie, aby ostrzec użytkowników, które dane będą oni próbowali do usunięcia nie można usunąć została przywrócona.

## <a name="add-and-remove-rows-at-runtime"></a>Dodawanie i usuwanie wierszy w czasie wykonywania
 Możesz ręcznie dodawać i usuwać wiersze w powiązanych z danymi <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolować, pod warunkiem że źródło danych umożliwia dodawanie nowych wierszy i nie jest tylko do odczytu. Można napisać kod w odniesieniu do zdarzeń, takich jak <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> sprawdzania poprawności danych. Aby uzyskać więcej informacji, zobacz [jak: Walidacja danych po dodaniu nowego rzędu do kontrolki ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md).

 Czasami relacji na obiekt listy do źródła danych powoduje, że błędy procedur. Na przykład można mapować kolumny, które mają być wyświetlane w <xref:Microsoft.Office.Tools.Excel.ListObject>, więc Jeśli pominiesz kolumny, które mają ograniczenia, takie jak pola, które nie akceptuje wartości null, błędy są wywoływane za każdym razem, gdy jest tworzona w wierszu. Można napisać kod, aby dodać brakujące wartości w obsłudze zdarzeń dla <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow> zdarzeń.

## <a name="rename-listobject-controls-in-excel"></a>Zmień nazwę kontrolki ListObject programu Excel
 Program Excel umożliwia użytkownikom zmianę nazwy tabel programu Excel w czasie wykonywania za pomocą **projektowania** kartę. Jednak <xref:Microsoft.Office.Tools.Excel.ListObject> formant nie obsługuje tej funkcji. Jeśli użytkownik próbuje zmienić nazwę tabeli programu Excel, który odpowiada <xref:Microsoft.Office.Tools.Excel.ListObject>, nazwę tabeli programu Excel automatycznie przywróci oryginalną nazwę po zapisaniu skoroszytu.

## <a name="events"></a>Zdarzenia
 Następujące zdarzenia są dostępne dla <xref:Microsoft.Office.Tools.Excel.ListObject> sterowania:

-   <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow>

-   <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeDoubleClick>

-   <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeRightClick>

-   <xref:Microsoft.Office.Tools.Excel.ListObject.BindingContextChanged>

-   <xref:Microsoft.Office.Tools.Excel.ListObject.Change>

-   <xref:Microsoft.Office.Tools.Excel.ListObject.DataBindingFailure>

-   <xref:Microsoft.Office.Tools.Excel.ListObject.DataMemberChanged>

-   <xref:Microsoft.Office.Tools.Excel.ListObject.DataSourceChanged>

-   <xref:Microsoft.Office.Tools.Excel.ListObject.Deselected>

-   <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow>

-   <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored>

-   <xref:Microsoft.Office.Tools.Excel.ListObject.Selected>

-   <xref:Microsoft.Office.Tools.Excel.ListObject.SelectedIndexChanged>

-   <xref:Microsoft.Office.Tools.Excel.ListObject.SelectionChange>

## <a name="see-also"></a>Zobacz także
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Instrukcje: Dodawanie formantów ListObject do arkuszy](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Instrukcje: Zmiana rozmiaru formantów ListObject](../vsto/how-to-resize-listobject-controls.md)
- [Instrukcje: Walidacja danych po dodaniu nowego rzędu do kontrolki ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)
- [Instrukcje: Mapowanie kolumn ListObject do danych](../vsto/how-to-map-listobject-columns-to-data.md)
- [Instrukcje: Wypełnianie formantów ListObject danymi](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Office development ― przykłady i przewodniki](../vsto/office-development-samples-and-walkthroughs.md)
- [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Instrukcje: Zapełnianie arkuszy danymi z bazy danych](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
