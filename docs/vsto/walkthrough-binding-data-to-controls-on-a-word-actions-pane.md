---
title: 'Przewodnik: Wiązanie danych z kontrolkami w okienku akcji programu Word'
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
ms.openlocfilehash: 49d307b687943ec99e04166b66e9ca5b15efb2a3
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866818"
---
# <a name="walkthrough-bind-data-to-controls-on-a-word-actions-pane"></a>Przewodnik: Wiązanie danych z kontrolkami w okienku akcji programu Word
  W tym instruktażu przedstawiono powiązanie danych z kontrolkami w okienku akcji programu Word. Formanty pokazują wzorzec/szczegół relacji między tabelami w bazie danych programu SQL Server.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Tworzenie okienek akcji za pomocą formantów Windows Forms, które są powiązane z danymi.  
  
-   Przy użyciu relacji wzorzec/szczegół do wyświetlania danych w kontrolkach.  
  
-   Pokaż okienko akcji, gdy aplikacja zostanie otwarta.  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
-   Dostęp do serwera z przykładową bazą danych Northwind programu SQL Server.  
  
-   Uprawnienia do odczytu i zapisu w bazie danych programu SQL Server.  
  
## <a name="create-the-project"></a>Utwórz projekt  
 Pierwszym krokiem jest utworzenie projektu dokument programu Word.  
  
### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1.  Tworzenie projektu dokument programu Word z nazwą **Moje okienku akcji programu Word**. W kreatorze Wybierz **Utwórz nowy dokument**.  
  
     Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio otwiera nowy dokument programu Word w Projektancie i dodaje **Moje okienku akcji programu Word** projekt **Eksploratora rozwiązań**.  
  
## <a name="add-controls-to-the-actions-pane"></a>Dodawanie formantów do okienka akcji  
 W ramach tego przewodnika należy kontrolka okienka akcji, który zawiera formanty Windows Forms powiązanych z danymi. Dodawanie źródła danych do projektu, a następnie przeciągnij formanty z **źródeł danych** okna kontrolki okienka akcji.  
  
### <a name="to-add-an-actions-pane-control"></a>Aby dodać kontrolki okienka akcji  
  
1.  Wybierz **Moje okienku akcji programu Word** projektu w **Eksploratora rozwiązań**.  
  
2.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
3.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **kontrolki okienka akcji**, nadaj jej nazwę **ActionsControl**, a następnie kliknij przycisk **Dodaj**.  
  
### <a name="to-add-a-data-source-to-the-project"></a>Aby dodać źródło danych do projektu  
  
1. Jeśli **źródeł danych** okno nie jest widoczne, wyświetlić je, na pasku menu, wybierając **widoku** > **Windows inne**  >   **Źródła danych**.  
  
   > [!NOTE]  
   >  Jeśli **Pokaż źródła danych** nie jest dostępny, kliknij go, a następnie sprawdź ponownie.  
  
2. Kliknij przycisk **Dodaj nowe źródło danych** można uruchomić **Kreatora konfiguracji źródła danych**.  
  
3. Wybierz **bazy danych** a następnie kliknij przycisk **dalej**.  
  
4. Wybierz połączenie danych z bazie danych programu SQL Server Northwind lub Dodaj nowe połączenie przy użyciu **nowe połączenie** przycisku.  
  
5. Kliknij przycisk **Dalej**.  
  
6. Usuń zaznaczenie opcji, aby zapisać połączenie, jeśli jest ono zaznaczone, a następnie kliknij **dalej**.  
  
7. Rozwiń **tabel** w węźle **obiektów bazy danych** okna.  
  
8. Zaznacz pole wyboru obok pozycji **dostawców** i **produktów** tabel.  
  
9. Kliknij przycisk **Zakończ**.  
  
   Kreator dodaje **dostawców** tabeli i **produktów** do tabeli **źródeł danych** okna. Dodaje także typizowany zestaw danych do projektu, który jest widoczny w **Eksploratora rozwiązań**.  
  
### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Aby dodać kontrolki formularzy Windows powiązane z danymi kontrolki okienka akcji  
  
1.  W **źródeł danych** okna, rozwiń węzeł **dostawców** tabeli.  
  
2.  Kliknij strzałkę listy rozwijanej **nazwa firmy** , a następnie wybierz węzeł **ComboBox**.  
  
3.  Przeciągnij **CompanyName** z **źródeł danych** okna kontrolki okienka akcji.  
  
     A <xref:System.Windows.Forms.ComboBox> formant zostanie utworzony na kontrolki okienka akcji. W tym samym czasie <xref:System.Windows.Forms.BindingSource> o nazwie `SuppliersBindingSource`, karty tabeli, a <xref:System.Data.DataSet> są dodawane do projektu w zasobniku składnika.  
  
4.  Wybierz `SuppliersBindingNavigator` w **składnika** na pasku zadań, a następnie naciśnij klawisz **Usuń**. Nie będzie używać `SuppliersBindingNavigator` w tym przewodniku.  
  
    > [!NOTE]  
    >  Usuwanie `SuppliersBindingNavigator` nie powoduje usunięcia cały kod, który został wygenerowany dla niego. Możesz usunąć ten kod.  
  
5.  Przenieś pole kombi tak, aby w ramach etykiety i zmień **rozmiar** właściwości **171, 21**.  
  
6.  W **źródeł danych** okna, rozwiń węzeł **produktów** tabeli, czyli elementem podrzędnym **dostawców** tabeli.  
  
7.  Kliknij strzałkę listy rozwijanej **ProductName** , a następnie wybierz węzeł **ListBox**.  
  
8.  Przeciągnij **ProductName** do kontrolki okienka akcji.  
  
     A <xref:System.Windows.Forms.ListBox> formant zostanie utworzony na kontrolki okienka akcji. W tym samym czasie <xref:System.Windows.Forms.BindingSource> o nazwie `ProductBindingSource` i karty tabeli są dodawane do projektu w zasobniku składnika.  
  
9. Przenieś pole listy tak, aby w ramach etykiety i zmień **rozmiar** właściwości **171,95**.  
  
10. Przeciągnij <xref:System.Windows.Forms.Button> z **przybornika** do okienka Akcje kontroli i umieść ją poniżej pola listy.  
  
11. Kliknij prawym przyciskiem myszy <xref:System.Windows.Forms.Button>, kliknij przycisk **właściwości** w menu skrótów i Zmień następujące właściwości.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**Wstaw**|  
    |**Text**|**Wstaw**|  
  
12. Zmień rozmiar kontrolki użytkownika, aby dopasować kontrolki.  
  
## <a name="set-up-the-data-source"></a>Konfigurowanie źródła danych  
 Aby skonfigurować źródło danych, Dodaj kod, aby <xref:System.Windows.Forms.UserControl.Load> zdarzeń kontrolki okienka akcji w celu wypełnienia kontrolki z danymi z <xref:System.Data.DataTable>i ustaw <xref:System.Windows.Forms.Binding.DataSource%2A> i <xref:System.Windows.Forms.BindingSource.DataMember%2A> właściwości dla każdego formantu.  
  
### <a name="to-load-the-control-with-data"></a>Aby załadować kontrolki z danymi  
  
1.  W <xref:System.Windows.Forms.UserControl.Load> program obsługi zdarzeń `ActionsControl` klasy, Dodaj następujący kod.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#1)]  
  
2.  W języku C#, należy dołączyć program obsługi zdarzeń do <xref:System.Windows.Forms.UserControl.Load> zdarzeń. Możesz umieścić ten kod w `ActionsControl` konstruktora, po wywołaniu `InitializeComponent`. Aby uzyskać więcej informacji na temat tworzenia procedury obsługi zdarzeń, zobacz [jak: Tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#33)]  
  
### <a name="to-set-data-binding-properties-of-the-controls"></a>Aby ustawić właściwości powiązania danych formantów  
  
1.  Wybierz `CompanyNameComboBox` kontroli.  
  
2.  W **właściwości** okna, kliknij przycisk po prawej stronie **DataSource** właściwości, a następnie wybierz **suppliersBindingSource**.  
  
3.  Kliknij przycisk po prawej stronie **elementu DisplayMember** właściwości, a następnie wybierz **CompanyName**.  
  
4.  Rozwiń **powiązania danych** właściwości, kliknij przycisk po prawej stronie **tekstu** właściwości, a następnie wybierz **Brak**.  
  
5.  Wybierz `ProductNameListBox` kontroli.  
  
6.  W **właściwości** okna, kliknij przycisk po prawej stronie **DataSource** właściwości, a następnie wybierz **productsBindingSource**.  
  
7.  Kliknij przycisk po prawej stronie **elementu DisplayMember** właściwości, a następnie wybierz **ProductName**.  
  
8.  Rozwiń **powiązania danych** właściwości, kliknij przycisk po prawej stronie **SelectedValue** właściwości, a następnie wybierz **Brak**.  
  
## <a name="add-a-method-to-insert-data-into-a-table"></a>Dodaj metodę, aby wstawić dane do tabeli  
 Kolejnym krokiem jest odczytać danych z powiązanej kontrolki i wypełnić tabelę w dokumencie programu Word. Najpierw należy utworzyć procedurę formatowania nagłówków w tabeli, a następnie dodaj `AddData` metodę, aby utworzyć i sformatować tabelę programu Word.  
  
### <a name="to-format-the-table-headings"></a>Aby sformatować nagłówki tabeli  
  
1.  W `ActionsControl` klasy, Utwórz metodę, aby sformatować nagłówki tabeli.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#2)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#2)]  
  
### <a name="to-create-the-table"></a>Aby utworzyć tabelę  
  
1.  W `ActionsControl` klasy, napisanie metody, która utworzy tabelę, w przypadku, gdy jeden jeszcze nie istnieje i dodać dane w okienku Akcje do tabeli.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#3)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#3)]  
  
### <a name="to-insert-text-into-a-word-table"></a>Aby wstawić tekst do tabeli w programie Word  
  
1.  Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń **Wstaw** przycisku.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#4)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#4)]  
  
2.  W języku C#, należy utworzyć program obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia przycisku.  Możesz umieścić ten kod w <xref:System.Windows.Forms.UserControl.Load> program obsługi zdarzeń `ActionsControl` klasy.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#5)]  
  
## <a name="show-the-actions-pane"></a>Pokaż okienko akcji  
 W okienku Akcje staje się widoczna po dodaniu kontrolki do niego.  
  
### <a name="to-show-the-actions-pane"></a>Aby pokazać okienko akcji  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ThisDocument.vb** lub **ThisDocument.cs**, a następnie kliknij przycisk **Wyświetl kod** w menu skrótów.  
  
2.  Utwórz nowe wystąpienie kontrolki w górnej części `ThisDocument` klasy tak, aby wyglądał jak w poniższym przykładzie.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#6)]  
  
3.  Dodaj kod, aby <xref:Microsoft.Office.Tools.Word.Document.Startup> program obsługi zdarzeń `ThisDocument` tak, aby wyglądał jak w poniższym przykładzie.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]  
  
## <a name="test-the-application"></a>Testowanie aplikacji  
 Teraz można przetestować dokument, aby sprawdzić, czy po otwarciu dokumentu jest wyświetlana w okienku Akcje. Testowanie dla relacji wzorzec/szczegół w kontrolkach w okienku akcji i upewnij się, wypełnieniu danych w programie Word tabeli, gdy **Wstaw** przycisku.  
  
### <a name="to-test-your-document"></a>Aby przetestować dokumentu  
  
1.  Naciśnij klawisz **F5** Aby uruchomić projekt.  
  
2.  Upewnij się, że widoczne jest okienko akcji.  
  
3.  Wybierz firmę, w polu kombi i sprawdź, czy elementy w **produktów** zmiany pola listy.  
  
4.  Wybierz produkt, kliknij przycisk **Wstaw** w okienku akcji i sprawdź, czy szczegóły produktu są dodawane do tabeli w programie Word.  
  
5.  Wstaw dodatkowe produkty z różnych firm.  
  
## <a name="next-steps"></a>Następne kroki  
 W tym przewodniku przedstawiono podstawowe informacje dotyczące powiązania danych z kontrolkami w okienku akcji programu Word. Poniżej przedstawiono niektóre zadania, które mogą pochodzić dalej:  
  
-   Powiązanie danych z kontrolkami w programie Excel. Aby uzyskać więcej informacji, zobacz [instruktażu: Wiązanie danych z kontrolkami w okienku akcji programu Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).  
  
-   Wdrażanie projektu. Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązania pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Okienko akcji ― omówienie](../vsto/actions-pane-overview.md)   
 [Instrukcje: Dodawanie okienek akcji do dokumentów programu Word lub arkuszy programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
