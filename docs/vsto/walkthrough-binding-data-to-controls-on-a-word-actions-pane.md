---
title: 'Przewodnik: wiązanie danych z kontrolkami w okienku akcji programu Word'
description: Wiązanie danych z kontrolkami w okienku akcji w programie Microsoft Word. Kontrolki pokazują relację wzorzec/szczegół między tabelami w SQL Server danych.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d94891520695117c7a395f81feda81e52f909fe6
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824500"
---
# <a name="walkthrough-bind-data-to-controls-on-a-word-actions-pane"></a>Przewodnik: wiązanie danych z kontrolkami w okienku akcji programu Word
  W tym przewodniku pokazano powiązanie danych z kontrolkami w okienku akcji w programie Word. Kontrolki pokazują relację wzorzec/szczegół między tabelami w SQL Server danych.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie okienka akcji z Windows Forms, które są powiązane z danymi.

- Używanie relacji wzorzec/szczegół do wyświetlania danych w kontrolkach.

- Pokaż okienko akcji po otworze aplikacji.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [Personalizowanie środowiska IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

- Dostęp do serwera przy użyciu bazy danych Northwind SQL Server przykładowej bazy danych.

- Uprawnienia do odczytu i zapisu w SQL Server danych.

## <a name="create-the-project"></a>Tworzenie projektu
 Pierwszym krokiem jest utworzenie projektu dokumentu programu Word.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt dokument programu Word o nazwie **My Word Actions Pane (Okienko akcji programu Word).** W kreatorze wybierz **pozycję Utwórz nowy dokument.**

     Aby uzyskać więcej informacji, [zobacz How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio nowy dokument programu Word w projektancie i dodaje projekt **Okienko** Moje akcje programu Word do **Eksplorator rozwiązań**.

## <a name="add-controls-to-the-actions-pane"></a>Dodawanie kontrolek do okienka akcji
 W tym przewodniku potrzebna jest kontrolka okienka akcji zawierająca kontrolki Windows Forms danych. Dodaj źródło danych do projektu, a następnie przeciągnij kontrolki z okna **Źródła** danych do kontrolki okienka akcji.

### <a name="to-add-an-actions-pane-control"></a>Aby dodać kontrolkę okienka akcji

1. Wybierz projekt **Okienko akcji programu My Word** w **Eksplorator rozwiązań**.

2. W menu **Project (Projekt)** kliknij **pozycję Add New Item (Dodaj nowy element).**

3. W **oknie dialogowym Dodawanie nowego elementu** wybierz pozycję **Kontrolka okienka Akcje,** nadaj jej nazwę **ActionsControl,** a następnie kliknij przycisk **Dodaj**.

### <a name="to-add-a-data-source-to-the-project"></a>Aby dodać źródło danych do projektu

1. Jeśli **okno Źródła danych** nie jest widoczne, wyświetl je na pasku menu, wybierając pozycję **Wyświetl** inne źródła  >  danych systemu **Windows.**  >  

   > [!NOTE]
   > Jeśli **polecenie Pokaż źródła danych** nie jest dostępne, kliknij dokument programu Word, a następnie sprawdź ponownie.

2. Kliknij **pozycję Dodaj nowe źródło danych,** aby uruchomić Kreatora konfiguracji źródła **danych.**

3. Wybierz **pozycję Baza danych,** a następnie kliknij przycisk **Dalej.**

4. Wybierz połączenie danych z przykładową bazą danych Northwind SQL Server lub dodaj nowe połączenie przy użyciu **przycisku Nowe** połączenie.

5. Kliknij przycisk **Dalej**.

6. Wyczyść opcję zapisywania połączenia, jeśli jest zaznaczone, a następnie kliknij przycisk **Dalej.**

7. Rozwiń **węzeł Tabele** w **oknie Obiekty bazy** danych.

8. Zaznacz pole wyboru obok tabel **Suppliers** and **Products.**

9. Kliknij przycisk **Finish** (Zakończ).

   Kreator dodaje **tabelę Suppliers (Dostawcy)** **i Tabelę Products (Produkty)** do **okna Źródła** danych. Dodaje również typowany zestaw danych do projektu, który jest widoczny w **Eksplorator rozwiązań**.

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Aby dodać kontrolki powiązane z Windows Forms do kontrolki okienka akcji

1. W **oknie Źródła** danych rozwiń **tabelę Suppliers** (Dostawcy).

2. Kliknij strzałkę listy rozwijanej w **węźle Nazwa firmy,** a następnie wybierz pozycję **ComboBox.**

3. Przeciągnij **element CompanyName** z **okna Źródła danych** do kontrolki okienka akcji.

     Kontrolka <xref:System.Windows.Forms.ComboBox> jest tworzona w kontrolce okienka akcji. W tym samym czasie do projektu w zasobniku składników dodawane są <xref:System.Windows.Forms.BindingSource> nazwane , adaptery tabel `SuppliersBindingSource` <xref:System.Data.DataSet> i .

4. Wybierz `SuppliersBindingNavigator` pozycję na pasku **składników** i naciśnij pozycję **Usuń.** W tym przewodniku nie `SuppliersBindingNavigator` będziesz używać instrukcji .

    > [!NOTE]
    > Usunięcie nie `SuppliersBindingNavigator` powoduje usunięcia całego kodu, który został dla niego wygenerowany. Możesz usunąć ten kod.

5. Przenieś pole kombi tak, aby znajduje się pod etykietą, i zmień właściwość **Size** na **171, 21**.

6. W **oknie Źródła** danych rozwiń **tabelę Products (Produkty),** która jest podrzędną **tabelą Suppliers** (Dostawcy).

7. Kliknij strzałkę listy rozwijanej w **węźle ProductName,** a następnie wybierz pozycję **ListBox**.

8. Przeciągnij **kontrolkę ProductName (Nazwa** produktu) do kontrolki okienka akcji.

     Kontrolka <xref:System.Windows.Forms.ListBox> jest tworzona w kontrolce okienka akcji. W tym samym czasie do projektu w zasobniku składników jest dodawana nazwana karta i <xref:System.Windows.Forms.BindingSource> `ProductBindingSource` karta tabeli.

9. Przenieś pole listy tak, aby było pod etykietą i zmień właściwość **Size** na **171,95**.

10. Przeciągnij element <xref:System.Windows.Forms.Button> z **przybornika do** kontrolki okienka akcji i umieść go poniżej pola listy.

11. Kliknij prawym przyciskiem myszy <xref:System.Windows.Forms.Button> pozycję , kliknij polecenie **Właściwości** w menu skrótów i zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**Insert**|
    |**Tekst**|**Insert**|

12. Zmień rozmiar kontrolki użytkownika, aby pasowała do kontrolek.

## <a name="set-up-the-data-source"></a>Konfigurowanie źródła danych
 Aby skonfigurować źródło danych, dodaj kod do zdarzenia kontrolki okienka akcji, aby wypełnić kontrolkę danymi z kontrolki i ustawić właściwości i dla <xref:System.Windows.Forms.UserControl.Load> <xref:System.Data.DataTable> każdej <xref:System.Windows.Forms.Binding.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> kontrolki.

### <a name="to-load-the-control-with-data"></a>Aby załadować kontrolkę z danymi

1. W <xref:System.Windows.Forms.UserControl.Load> programie obsługi zdarzeń `ActionsControl` klasy dodaj następujący kod.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet1":::

2. W języku C# należy dołączyć do zdarzenia program obsługi <xref:System.Windows.Forms.UserControl.Load> zdarzeń. Ten kod można umieścić w `ActionsControl` konstruktorze po wywołaniu . `InitializeComponent` Aby uzyskać więcej informacji na temat sposobu tworzenia programów obsługi zdarzeń, zobacz [How to: Create event handlers in Office projects](../vsto/how-to-create-event-handlers-in-office-projects.md)( Jak utworzyć procedury obsługi zdarzeń w projektach pakietu Office).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet33":::

### <a name="to-set-data-binding-properties-of-the-controls"></a>Aby ustawić właściwości powiązania danych kontrolek

1. Wybierz `CompanyNameComboBox` kontrolkę.

2. W **oknie** Właściwości kliknij przycisk z prawej strony właściwości **DataSource,** a następnie wybierz **pozycję suppliersBindingSource.**

3. Kliknij przycisk z prawej strony właściwości **DisplayMember,** a następnie wybierz **pozycję Nazwa firmy.**

4. Rozwiń **właściwość DataBindings,** kliknij przycisk z prawej strony właściwości **Text** i wybierz pozycję **Brak.**

5. Wybierz `ProductNameListBox` kontrolkę.

6. W **oknie** Właściwości kliknij przycisk z prawej strony właściwości **DataSource,** a następnie wybierz **pozycję productsBindingSource.**

7. Kliknij przycisk z prawej strony właściwości **DisplayMember,** a następnie wybierz **pozycję ProductName**.

8. Rozwiń **właściwość DataBindings,** kliknij przycisk z prawej strony właściwości **SelectedValue** i wybierz pozycję **Brak.**

## <a name="add-a-method-to-insert-data-into-a-table"></a>Dodawanie metody wstawiania danych do tabeli
 Następnym zadaniem jest odczytanie danych z powiązanych kontrolek i wypełnienie tabeli w dokumencie programu Word. Najpierw utwórz procedurę formatowania nagłówków w tabeli, a następnie dodaj metodę w celu utworzenia i `AddData` sformatowania tabeli programu Word.

### <a name="to-format-the-table-headings"></a>Aby sformatować nagłówki tabeli

1. W `ActionsControl` klasie utwórz metodę do formatowania nagłówków tabeli.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet2":::

### <a name="to-create-the-table"></a>Aby utworzyć tabelę

1. W klasie napisz metodę , która utworzy tabelę, jeśli jeszcze nie istnieje, i doda dane z okienka akcji `ActionsControl` do tabeli.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet3":::

### <a name="to-insert-text-into-a-word-table"></a>Aby wstawić tekst do tabeli programu Word

1. Dodaj następujący kod do procedury <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń **przycisku Wstaw.**

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet4":::

2. W języku C# należy utworzyć program obsługi zdarzeń <xref:System.Windows.Forms.Control.Click> dla zdarzenia przycisku.  Ten kod można umieścić w <xref:System.Windows.Forms.UserControl.Load> programie obsługi zdarzeń `ActionsControl` klasy .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet5":::

## <a name="show-the-actions-pane"></a>Wyświetlanie okienka akcji
 Okienko akcji staje się widoczne po dodaniu do niego kontrolek.

### <a name="to-show-the-actions-pane"></a>Aby wyświetlić okienko akcji

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy plik **ThisDocument.vb** lub **ThisDocument.cs,** a następnie kliknij polecenie **Wyświetl** kod w menu skrótów.

2. Utwórz nowe wystąpienie kontrolki w górnej części klasy, tak `ThisDocument` aby wyglądało to jak w poniższym przykładzie.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet6":::

3. Dodaj kod do <xref:Microsoft.Office.Tools.Word.Document.Startup> procedury obsługi zdarzeń programu , aby wyglądał jak w poniższym `ThisDocument` przykładzie.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet7":::

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz możesz przetestować dokument, aby sprawdzić, czy okienko akcji jest wyświetlane po otwarciu dokumentu. Przetestuj relację wzorzec/szczegół w kontrolkach w okienku akcji i upewnij się, że dane są wypełnione w tabeli programu Word po kliknięciu **przycisku** Wstaw.

### <a name="to-test-your-document"></a>Aby przetestować dokument

1. Naciśnij **klawisz F5,** aby uruchomić projekt.

2. Upewnij się, że okienko akcji jest widoczne.

3. Wybierz firmę w polu kombi i sprawdź, czy elementy w polu **listy** Produkty się zmieniają.

4. Wybierz produkt, kliknij przycisk **Wstaw** w okienku akcji i sprawdź, czy szczegóły produktu zostały dodane do tabeli w programie Word.

5. Wstaw dodatkowe produkty od różnych firm.

## <a name="next-steps"></a>Następne kroki
 W tym przewodniku przedstawiono podstawy powiązania danych z kontrolkami w okienku akcji w programie Word. Oto kilka zadań, które mogą pojawić się w następnej części:

- Wiązanie danych z kontrolkami w programie Excel. Aby uzyskać więcej informacji, zobacz [Przewodnik: wiązanie danych z kontrolkami w okienku akcji programu Excel.](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)

- Wdrażanie projektu. Aby uzyskać więcej informacji, zobacz Deploy an Office solution by using ClickOnce (Wdrażanie [rozwiązania pakietu Office przy użyciu technologii ClickOnce).](../vsto/deploying-an-office-solution-by-using-clickonce.md)

## <a name="see-also"></a>Zobacz też
- [Omówienie okienka Akcje](../vsto/actions-pane-overview.md)
- [How to: Add an actions pane to Word documents or Excel workbooks (Jak dodać okienko akcji do dokumentów programu Word lub skoroszytów programu Excel)](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Wiązanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
