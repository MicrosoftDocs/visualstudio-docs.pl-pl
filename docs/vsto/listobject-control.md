---
title: ListObject — formant
description: Formant ListObject to lista, która ujawnia zdarzenia i może być powiązana z danymi. Ponadto można dodać kontrolki ListObject do arkusza w czasie projektowania lub w czasie wykonywania.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 1a80b56134f59975a39d24e824b6c83b2513b163
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526593"
---
# <a name="listobject-control"></a>ListObject — formant
  <xref:Microsoft.Office.Tools.Excel.ListObject>Kontrolka jest listą, która ujawnia zdarzenia i może być powiązana z danymi. Po dodaniu listy do arkusza program Visual Studio tworzy <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolkę, którą można bezpośrednio programować bez konieczności przechodzenia przez model obiektów programu Microsoft Office Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="create-the-control"></a>Tworzenie kontrolki
 W projektach na poziomie dokumentu można dodawać <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki do arkusza w czasie projektowania lub w czasie wykonywania. W projektach dodatku VSTO można dodawać <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki do arkuszy tylko w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie formantów ListObject do arkuszy](../vsto/how-to-add-listobject-controls-to-worksheets.md).

> [!NOTE]
> Domyślnie obiekty list utworzone dynamicznie nie są utrwalane w arkuszu jako kontrolki hosta, gdy arkusz jest zamknięty. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="bind-data-to-the-control"></a>Powiąż dane z kontrolką
 <xref:Microsoft.Office.Tools.Excel.ListObject>Kontrolka obsługuje proste i złożone powiązanie danych. <xref:Microsoft.Office.Tools.Excel.ListObject>Formant można powiązać ze źródłem danych przy użyciu <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> <xref:Microsoft.Office.Tools.Excel.ListObject.DataMember%2A> właściwości i w czasie projektowania lub w <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> metodzie w czasie wykonywania.

> [!NOTE]
> Program <xref:Microsoft.Office.Tools.Excel.ListObject> jest aktualizowany automatycznie, gdy jest powiązany ze źródłem danych, takim jak <xref:System.Data.DataTable> , który podnosi zdarzenia po zmianie danych. Jeśli powiążesz ze <xref:Microsoft.Office.Tools.Excel.ListObject> źródłem danych, które nie wywołuje zdarzeń, gdy zmienią się dane, musisz wywołać <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRow%2A> metodę lub, <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRows%2A> Aby zaktualizować <xref:Microsoft.Office.Tools.Excel.ListObject> .

 Po dodaniu <xref:Microsoft.Office.Tools.Excel.ListObject> do komórki arkusza przez mapowanie powtarzanego elementu schematu do tej komórki program Visual Studio automatycznie mapuje <xref:Microsoft.Office.Tools.Excel.ListObject> do wygenerowanego zestawu danych. <xref:Microsoft.Office.Tools.Excel.ListObject>Nie jest to jednak automatycznie powiązane z danymi. Można wykonać kroki, aby powiązać z <xref:Microsoft.Office.Tools.Excel.ListObject> zestawem danych w czasie projektowania lub w czasie wykonywania w projekcie na poziomie dokumentu. Można programowo powiązać z <xref:Microsoft.Office.Tools.Excel.ListObject> zestawem danych w czasie wykonywania w dodatku VSTO.

 Ponieważ dane są oddzielone od <xref:Microsoft.Office.Tools.Excel.ListObject> , należy dodać i usunąć dane za pośrednictwem powiązanego zestawu danych, a nie bezpośrednio za pośrednictwem <xref:Microsoft.Office.Tools.Excel.ListObject> . Jeśli dane w powiązanym zestawie danych są aktualizowane za pomocą dowolnego mechanizmu, <xref:Microsoft.Office.Tools.Excel.ListObject> formant automatycznie odzwierciedla zmiany. Aby uzyskać więcej informacji, zobacz temat [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).

 Możesz szybko wypełnić formant, <xref:Microsoft.Office.Tools.Excel.ListObject> wiążąc <xref:Microsoft.Office.Tools.Excel.ListObject> względem źródła danych. Jeśli edytujesz dane w powiązane dane <xref:Microsoft.Office.Tools.Excel.ListObject> , zmiany są również automatycznie wykonywane w źródle danych. Jeśli chcesz wypełnić, <xref:Microsoft.Office.Tools.Excel.ListObject> a następnie zezwolić użytkownikowi na zmianę danych w programie <xref:Microsoft.Office.Tools.Excel.ListObject> bez modyfikowania źródła danych, możesz użyć <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> metody, aby odłączyć <xref:Microsoft.Office.Tools.Excel.ListObject> od źródła danych. Aby uzyskać więcej informacji, zobacz [How to: fillobject Controls with Data](../vsto/how-to-fill-listobject-controls-with-data.md).

> [!NOTE]
> Powiązanie danych nie jest obsługiwane dla nakładających się <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolek.

### <a name="improve-performance-in-listobject-controls"></a>Poprawianie wydajności w kontrolkach ListObject
 Odczytywanie pliku XML do kontrolki powiązanej z danymi <xref:Microsoft.Office.Tools.Excel.ListObject> jest wolniejsze, jeśli najpierw powiążesz formant, a następnie Wywołaj, <xref:System.Data.DataSet.ReadXml%2A> Aby wypełnić zestaw danych. Aby zwiększyć wydajność, należy wywołać <xref:System.Data.DataSet.ReadXml%2A> przed powiązaniem formantu.

### <a name="disconnect-listobject-controls-from-the-data-source"></a>Odłączanie formantów ListObject ze źródła danych
 Po wypełnieniu <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki danymi przez powiązanie jej ze źródłem danych, można odłączyć ją tak, aby zmiany wprowadzone do danych w obiekcie list nie miały wpływu na źródło danych. Aby uzyskać więcej informacji, zobacz [How to: fillobject Controls with Data](../vsto/how-to-fill-listobject-controls-with-data.md).

### <a name="restore-column-and-row-order"></a>Przywracanie kolumny i kolejności wierszy
 Po powiązaniu danych z <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolką, która została dodana do dokumentu w czasie projektowania, program Visual Studio śledzi kolejność kolumn i wierszy za każdym razem, gdy skoroszyt zostanie zapisany. Jeśli użytkownik przenosi <xref:Microsoft.Office.Tools.Excel.ListObject> kolumny lub wiersze w czasie wykonywania, nowe zamówienie jest zachowywane przy następnym otwarciu skoroszytu i <xref:Microsoft.Office.Tools.Excel.ListObject> ponownie tworzy powiązanie ze źródłem danych.

 Jeśli chcesz przywrócić <xref:Microsoft.Office.Tools.Excel.ListObject> pierwotną kolejność kolumn i wierszy, możesz wywołać <xref:Microsoft.Office.Tools.Excel.ListObject.ResetPersistedBindingInformation%2A> metodę. Ta metoda usuwa niestandardowe właściwości dokumentu powiązane z kolumną i kolejnością wierszy określonych <xref:Microsoft.Office.Tools.Excel.ListObject> . Wywołaj tę metodę ze <xref:Microsoft.Office.Tools.Excel.Workbook.Shutdown> zdarzenia skoroszytu, jeśli nie chcesz zachować kolejności kolumn i wierszy <xref:Microsoft.Office.Tools.Excel.ListObject> .

## <a name="format"></a>Format
 Formatowanie, które można zastosować do elementu, <xref:Microsoft.Office.Interop.Excel.ListObject> można zastosować do <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki. Dotyczy to również obramowań, czcionek, formatu liczb i stylów. Użytkownicy końcowi mogą zmieniać rozmieszczenie kolumn w powiązane dane <xref:Microsoft.Office.Tools.Excel.ListObject> , a te zmiany zostaną utrwalone w dokumencie, pod warunkiem, że <xref:Microsoft.Office.Tools.Excel.ListObject> został dodany do dokumentu w czasie projektowania. Przy następnym otwarciu dokumentu obiekt listy zostanie powiązany z tym samym źródłem danych, ale kolejność kolumn będzie odzwierciedlać zmiany wprowadzone przez użytkownika.

## <a name="add-and-remove-columns-at-run-time"></a>Dodawanie i usuwanie kolumn w czasie wykonywania
 Nie można ręcznie dodawać ani usuwać kolumn w kontrolce powiązanej z danymi <xref:Microsoft.Office.Tools.Excel.ListObject> w czasie wykonywania. Jeśli użytkownik końcowy podejmie próbę usunięcia kolumny, zostanie ona natychmiast przywrócona, a wszystkie dodane kolumny zostaną usunięte. W związku z tym ważne jest, aby napisać kod, aby wyjaśnić użytkownikom, dlaczego nie mogą wykonywać tych czynności w odniesieniu <xref:Microsoft.Office.Tools.Excel.ListObject> do danych. Program Visual Studio zawiera kilka zdarzeń <xref:Microsoft.Office.Tools.Excel.ListObject> związanych z powiązaniem danych. Można na przykład użyć <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored> zdarzenia, aby ostrzec użytkowników, że dane, które próbowano usunąć, nie mogą zostać usunięte i przywrócone.

## <a name="add-and-remove-rows-at-run-time"></a>Dodawanie i usuwanie wierszy w czasie wykonywania
 Można ręcznie dodawać i usuwać wiersze w kontrolce powiązanej z danymi <xref:Microsoft.Office.Tools.Excel.ListObject> , pod warunkiem, że źródło danych umożliwia dodanie nowych wierszy i nie jest tylko do odczytu. Można napisać kod przed zdarzeniami, takimi jak <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> Sprawdzanie poprawności danych. Aby uzyskać więcej informacji, zobacz [jak: sprawdzanie poprawności danych po dodaniu nowego wiersza do kontrolki ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md).

 Czasami relacja obiektu listy ze źródłem danych powoduje błędy rutynowe. Na przykład można mapować kolumny, które mają być wyświetlane w <xref:Microsoft.Office.Tools.Excel.ListObject> , dlatego w przypadku pominięcia kolumn z ograniczeniami, takich jak pole, które nie może akceptować wartości null, błędy są wywoływane za każdym razem, gdy wiersz zostanie utworzony. Można napisać kod, aby dodać brakujące wartości w procedurze obsługi zdarzeń dla <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow> zdarzenia.

## <a name="rename-listobject-controls-in-excel"></a>Zmień nazwę formantów ListObject w programie Excel
 Program Excel umożliwia użytkownikom zmianę nazwy tabel programu Excel w czasie wykonywania przy użyciu karty **projektowanie** . Jednak formant nie <xref:Microsoft.Office.Tools.Excel.ListObject> obsługuje tej funkcji. Jeśli użytkownik spróbuje zmienić nazwę tabeli programu Excel, która odnosi się do <xref:Microsoft.Office.Tools.Excel.ListObject> , nazwa tabeli programu Excel zostanie automatycznie przywrócona do oryginalnej nazwy, gdy skoroszyt zostanie zapisany.

## <a name="events"></a>Zdarzenia
 Dla kontrolki dostępne są następujące zdarzenia <xref:Microsoft.Office.Tools.Excel.ListObject> :

- <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow>

- <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.ListObject.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.Change>

- <xref:Microsoft.Office.Tools.Excel.ListObject.DataBindingFailure>

- <xref:Microsoft.Office.Tools.Excel.ListObject.DataMemberChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.DataSourceChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.Deselected>

- <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow>

- <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored>

- <xref:Microsoft.Office.Tools.Excel.ListObject.Selected>

- <xref:Microsoft.Office.Tools.Excel.ListObject.SelectedIndexChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.SelectionChange>

## <a name="see-also"></a>Zobacz też
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Instrukcje: Dodawanie formantów ListObject do arkuszy](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Instrukcje: Zmienianie rozmiaru formantów ListObject](../vsto/how-to-resize-listobject-controls.md)
- [Instrukcje: sprawdzanie poprawności danych po dodaniu nowego wiersza do kontrolki ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)
- [Instrukcje: Mapowanie kolumn ListObject na dane](../vsto/how-to-map-listobject-columns-to-data.md)
- [Instrukcje: wypełnianie kontrolek ListObject danymi](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Przykłady i przewodniki dotyczące programowania pakietu Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Rozwiń dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Instrukcje: zapełnianie arkuszy danymi z bazy danych](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
