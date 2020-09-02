---
title: 'Przewodnik: powiązywanie danych z kontrolkami w okienku akcji programu Word'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], data binding
- actions panes [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], smart documents
- data binding [Office development in Visual Studio], actions panes
- actions panes [Office development in Visual Studio], binding controls
- smart documents [Office development in Visual Studio], data binding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ddeba1539cf68d53f4b9f931d2bcd18a159028fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64802663"
---
# <a name="walkthrough-bind-data-to-controls-on-a-word-actions-pane"></a>Przewodnik: powiązywanie danych z kontrolkami w okienku akcji programu Word
  Ten Instruktaż przedstawia powiązanie danych z kontrolkami w okienku Akcje w programie Word. Kontrolki ilustrują relację wzorzec/szczegóły między tabelami w bazie danych SQL Server.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie okienka akcji z kontrolkami Windows Forms, które są powiązane z danymi.

- Używanie relacji wzorzec/szczegóły do wyświetlania danych w kontrolkach.

- Pokaż okienko akcje, gdy aplikacja zostanie otwarta.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

- Dostęp do serwera za pomocą przykładowej bazy danych Northwind SQL Server.

- Uprawnienia do odczytu i zapisu w bazie danych SQL Server.

## <a name="create-the-project"></a>Tworzenie projektu
 Pierwszym krokiem jest utworzenie projektu dokumentu programu Word.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt dokumentu programu Word za pomocą **okienka nazwa moje akcje programu Word**. W kreatorze wybierz pozycję **Utwórz nowy dokument**.

     Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Program Visual Studio otwiera nowy dokument programu Word w Projektancie i dodaje projekt **okienka Akcje my Word** do **Eksplorator rozwiązań**.

## <a name="add-controls-to-the-actions-pane"></a>Dodawanie kontrolek do okienka Akcje
 W tym instruktażu potrzebna jest kontrolka okienka akcji, która zawiera powiązane z danymi kontrolki Windows Forms. Dodaj źródło danych do projektu, a następnie przeciągnij kontrolki z okna **źródła danych** do kontrolki okienko akcji.

### <a name="to-add-an-actions-pane-control"></a>Aby dodać kontrolkę okienka akcji

1. Wybierz projekt **okienka Akcje w programie Word** w **Eksplorator rozwiązań**.

2. W menu **projekt** kliknij polecenie **Dodaj nowy element**.

3. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **kontrolka okienka akcji**, nadaj jej nazwę **ActionsControl**, a następnie kliknij przycisk **Dodaj**.

### <a name="to-add-a-data-source-to-the-project"></a>Aby dodać źródło danych do projektu

1. Jeśli okno **źródła danych** nie jest widoczne, Wyświetl je na pasku menu, wybierając opcję **Wyświetl**  >  **inne**  >  **źródła danych**systemu Windows.

   > [!NOTE]
   > Jeśli **Pokaż źródła danych** nie są dostępne, kliknij dokument programu Word, a następnie sprawdź ponownie.

2. Kliknij przycisk **Dodaj nowe źródło danych** , aby uruchomić **Kreatora konfiguracji źródła danych**.

3. Wybierz pozycję **baza danych** , a następnie kliknij przycisk **dalej**.

4. Wybierz połączenie danych z przykładową bazą danych Northwind SQL Server lub Dodaj nowe połączenie za pomocą przycisku **nowe połączenie** .

5. Kliknij przycisk **Dalej**.

6. Usuń zaznaczenie opcji Zapisz połączenie, jeśli jest zaznaczone, a następnie kliknij przycisk **dalej**.

7. Rozwiń węzeł **tabele** w oknie **obiekty bazy danych** .

8. Zaznacz pole wyboru obok tabel **dostawcy** i **produkty** .

9. Kliknij przycisk **Zakończ**.

   Kreator dodaje tabelę tabele i **produkty** **dostawcy** do okna **źródła danych** . Dodaje również typ DataSet do projektu, który jest widoczny w **Eksplorator rozwiązań**.

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Aby dodać kontrolki Windows Forms powiązane z danymi do kontrolki okienka akcji

1. W oknie **źródła danych** Rozwiń tabelę **dostawcy** .

2. Kliknij strzałkę listy rozwijanej w węźle **Nazwa firmy** , a następnie wybierz pole **kombi**.

3. Przeciągnij wartość **NazwaFirmy** z okna **źródła danych** do kontrolki okienko akcji.

     <xref:System.Windows.Forms.ComboBox>Kontrolka jest tworzona w kontrolce okienka Akcje. W tym samym czasie <xref:System.Windows.Forms.BindingSource> nazwaną `SuppliersBindingSource` , kartę tabeli i a <xref:System.Data.DataSet> są dodawane do projektu na pasku składnika.

4. Wybierz pozycję `SuppliersBindingNavigator` na pasku **składnika** i naciśnij klawisz **delete**. `SuppliersBindingNavigator`W tym instruktażu nie będą używane.

    > [!NOTE]
    > Usunięcie programu `SuppliersBindingNavigator` nie powoduje usunięcia całego kodu, który został wygenerowany dla niego. Możesz usunąć ten kod.

5. Przenieś pole kombi tak, aby było ono pod etykietą, i zmień właściwość **size** na **171, 21**.

6. W oknie **źródła danych** Rozwiń tabelę **produkty** , która jest elementem podrzędnym tabeli **dostawcy** .

7. Kliknij strzałkę listy rozwijanej w węźle **ProductName** , a następnie wybierz pozycję **ListBox**.

8. Przeciągnij **ProductName** do kontrolki okienka Akcje.

     <xref:System.Windows.Forms.ListBox>Kontrolka jest tworzona w kontrolce okienka Akcje. W tym samym czasie <xref:System.Windows.Forms.BindingSource> nazwa `ProductBindingSource` i adapter tabeli są dodawane do projektu na pasku składnika.

9. Przenieś pole listy tak, aby było ono pod etykietą, i zmień właściwość **size** na **171, a, 95**.

10. Przeciągnij <xref:System.Windows.Forms.Button> z **przybornika** do formantu okienka Akcje i umieść go poniżej pola listy.

11. Kliknij prawym przyciskiem myszy <xref:System.Windows.Forms.Button> , kliknij polecenie **Właściwości** w menu skrótów, a następnie Zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**Insert**|
    |**Tekst**|**Insert**|

12. Zmień rozmiar kontrolki użytkownika, aby dopasować ją do kontrolek.

## <a name="set-up-the-data-source"></a>Konfigurowanie źródła danych
 Aby skonfigurować źródło danych, Dodaj kod do <xref:System.Windows.Forms.UserControl.Load> zdarzenia kontrolki okienko akcji, aby wypełnić formant danymi z <xref:System.Data.DataTable> i ustawić <xref:System.Windows.Forms.Binding.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> właściwości i dla każdej kontrolki.

### <a name="to-load-the-control-with-data"></a>Aby załadować formant z danymi

1. W <xref:System.Windows.Forms.UserControl.Load> procedurze obsługi zdarzeń `ActionsControl` klasy Dodaj następujący kod.

     [!code-vb[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#1)]

2. W języku C# należy dołączyć procedurę obsługi zdarzeń do <xref:System.Windows.Forms.UserControl.Load> zdarzenia. Ten kod można umieścić w `ActionsControl` konstruktorze po wywołaniu `InitializeComponent` . Aby uzyskać więcej informacji na temat sposobu tworzenia programów obsługi zdarzeń, zobacz [How to: Create Event Handles in Office projects](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#33)]

### <a name="to-set-data-binding-properties-of-the-controls"></a>Aby ustawić właściwości powiązań danych kontrolek

1. Zaznacz `CompanyNameComboBox` kontrolkę.

2. W oknie **Właściwości** kliknij przycisk z prawej strony właściwości **DataSource** , a następnie wybierz pozycję **suppliersBindingSource**.

3. Kliknij przycisk z prawej strony właściwości **DisplayMember** , a następnie wybierz pozycję **NazwaFirmy**.

4. Rozwiń Właściwość **DataBindings** , kliknij przycisk z prawej strony właściwości **Text** , a następnie wybierz **Brak**.

5. Zaznacz `ProductNameListBox` kontrolkę.

6. W oknie **Właściwości** kliknij przycisk z prawej strony właściwości **DataSource** , a następnie wybierz pozycję **productsBindingSource**.

7. Kliknij przycisk z prawej strony właściwości **DisplayMember** , a następnie wybierz pozycję **ProductName**.

8. Rozwiń Właściwość **DataBindings** , kliknij przycisk z prawej strony właściwości **SelectedValue** , a następnie wybierz **Brak**.

## <a name="add-a-method-to-insert-data-into-a-table"></a>Dodawanie metody wstawiania danych do tabeli
 Następnym zadaniem jest odczytanie danych z formantów powiązanych i wypełnienie tabeli w dokumencie programu Word. Najpierw Utwórz procedurę formatowania nagłówków w tabeli, a następnie Dodaj `AddData` metodę, aby utworzyć i sformatować tabelę programu Word.

### <a name="to-format-the-table-headings"></a>Aby sformatować nagłówki tabeli

1. W `ActionsControl` klasie Utwórz metodę formatowania nagłówków tabeli.

     [!code-vb[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#2)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#2)]

### <a name="to-create-the-table"></a>Aby utworzyć tabelę

1. W `ActionsControl` klasie Napisz metodę, która utworzy tabelę, jeśli jeszcze nie istnieje, i Dodaj dane z okienka Akcje do tabeli.

     [!code-vb[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#3)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#3)]

### <a name="to-insert-text-into-a-word-table"></a>Aby wstawić tekst do tabeli programu Word

1. Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> procedury obsługi zdarzeń przycisku **Wstaw** .

     [!code-vb[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#4)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#4)]

2. W języku C# należy utworzyć procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia przycisku.  Ten kod można umieścić w <xref:System.Windows.Forms.UserControl.Load> obsłudze zdarzeń `ActionsControl` klasy.

     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#5)]

## <a name="show-the-actions-pane"></a>Pokaż okienko akcje
 Okienko akcje jest widoczne po dodaniu do niego kontrolek.

### <a name="to-show-the-actions-pane"></a>Aby wyświetlić okienko akcje

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy **ThisDocument. vb** lub **ThisDocument.cs**, a następnie kliknij polecenie **Wyświetl kod** w menu skrótów.

2. Utwórz nowe wystąpienie formantu w górnej części `ThisDocument` klasy, tak aby wyglądało jak w poniższym przykładzie.

     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#6)]

3. Dodaj kod do <xref:Microsoft.Office.Tools.Word.Document.Startup> programu obsługi zdarzeń, `ThisDocument` tak aby wyglądał jak w poniższym przykładzie.

     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz można przetestować dokument, aby sprawdzić, czy okienko akcje pojawia się po otwarciu dokumentu. Test dla relacji wzorzec/szczegóły w kontrolkach w okienku Akcje i upewnij się, że dane są wypełniane w tabeli programu Word po kliknięciu przycisku **Wstaw** .

### <a name="to-test-your-document"></a>Aby przetestować dokument

1. Naciśnij klawisz **F5** , aby uruchomić projekt.

2. Upewnij się, że okienko akcje jest widoczne.

3. Wybierz firmę w polu kombi i sprawdź, czy elementy w polu listy **produkty** zmieniają się.

4. Wybierz produkt, kliknij przycisk **Wstaw** w okienku Akcje i sprawdź, czy szczegóły produktu są dodawane do tabeli w programie Word.

5. Wstaw dodatkowe produkty z różnych firm.

## <a name="next-steps"></a>Następne kroki
 W tym instruktażu przedstawiono podstawowe informacje dotyczące wiązania danych z kontrolkami w okienku Akcje w programie Word. Poniżej przedstawiono kilka zadań, które mogą wystąpić poniżej:

- Powiązywanie danych z kontrolkami w programie Excel. Aby uzyskać więcej informacji, zobacz [Przewodnik: powiązywanie danych z kontrolkami w okienku akcji programu Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).

- Wdrażanie projektu. Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązania pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="see-also"></a>Zobacz też
- [Przegląd okienka Akcje](../vsto/actions-pane-overview.md)
- [Instrukcje: Dodawanie okienka akcji do dokumentów programu Word lub skoroszytów programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
