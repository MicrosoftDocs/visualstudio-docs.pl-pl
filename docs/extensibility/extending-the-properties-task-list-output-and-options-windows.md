---
title: Rozszerzanie okien Właściwości, Lista zadań, Dane wyjściowe, Opcje
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db14068c97ff6868f5fb73c9ddd790020e99e7c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711638"
---
# <a name="extend-the-properties-task-list-output-and-options-windows"></a>Rozszerzanie okien Właściwości, Lista zadań, Dane wyjściowe i Opcje
Dostęp do dowolnego okna narzędzia można uzyskać w programie Visual Studio. W tym przewodniku pokazano, jak zintegrować informacje o oknie narzędzia z nową stroną **Opcje** i nowym ustawieniem na stronie **Właściwości,** a także jak zapisywać w oknach **Lista zadań** i Dane **wyjściowe.**

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-tool-window"></a>Tworzenie rozszerzenia za pomocą okna narzędzia

1. Utwórz projekt o nazwie **TodoList** przy użyciu szablonu VSIX i dodaj niestandardowy szablon elementu okna narzędzia o nazwie **TodoWindow**.

    > [!NOTE]
    > Aby uzyskać więcej informacji na temat tworzenia rozszerzenia z oknem narzędzia, zobacz [Tworzenie rozszerzenia z oknem narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="set-up-the-tool-window"></a>Konfigurowanie okna narzędzia
 Dodaj pole tekstowe, w którym można wpisać nowy element DoDo, przycisk, aby dodać nowy element do listy, i Pole listy, aby wyświetlić elementy na liście.

1. W *pliku TodoWindow.xaml*usuń formanty Button, TextBox i StackPanel z usercontrol.

    > [!NOTE]
    > Nie powoduje to usunięcia **button1_Click** programu obsługi zdarzeń, który zostanie ponownie użycia w późniejszym kroku.

2. W sekcji **Wszystkie formanty WPF** **przybornika**przeciągnij kontrolkę **Kanwa** do siatki.

3. Przeciągnij **pole tekstowe**, **przycisk**i **pole listy** na kanwę. Rozmieść elementy tak, aby TextBox i Button były na tym samym poziomie, a ListBox wypełnia resztę okna pod nimi, jak na poniższym rysunku.

     ![Okno Gotowego narzędzia](../extensibility/media/t5-toolwindow.png "T5-ToolWindow")

4. W okienku XAML znajdź przycisk i ustaw jego właściwość Zawartość na **Dodaj**. Ponownie podłącz program obsługi zdarzeń przycisku `Click="button1_Click"` do button kontroli przez dodanie atrybutu. Blok kanwy powinien wyglądać następująco:

    ```xml
    <Canvas HorizontalAlignment="Left" Width="306">
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>
    </Canvas>
    ```

### <a name="customize-the-constructor"></a>Dostosowywanie konstruktora

1. W pliku *TodoWindowControl.xaml.cs* dodaj następujące elementy za pomocą dyrektywy:

    ```csharp
    using System;
    ```

2. Dodaj odwołanie publiczne do TodoWindow i niech TodoWindowControl konstruktora wziąć TodoWindow parametru. Kod powinien wyglądać następująco:

    ```csharp
    public TodoWindow parent;

    public TodoWindowControl(TodoWindow window)
    {
        InitializeComponent();
        parent = window;
    }
    ```

3. W *TodoWindow.cs*, zmień konstruktora TodoWindowControl, aby uwzględnić parametr TodoWindow. Kod powinien wyglądać następująco:

    ```csharp
    public TodoWindow() : base(null)
    {
        this.Caption = "TodoWindow";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;

         this.Content = new TodoWindowControl(this);
    }
    ```

## <a name="create-an-options-page"></a>Tworzenie strony Opcje
 W oknie dialogowym **Opcje** można podać stronę, aby użytkownicy mogli zmieniać ustawienia okna narzędzia. Tworzenie strony Opcje wymaga zarówno klasy opisującej opcje, jak i wpisu w *pliku TodoListPackage.cs* lub *TodoListPackage.vb.*

1. Dodaj klasę `ToolsOptions.cs`o nazwie . Spraw, `ToolsOptions` aby <xref:Microsoft.VisualStudio.Shell.DialogPage>klasa dziedziczyła po .

   ```csharp
   class ToolsOptions : DialogPage
   {
   }
   ```

2. Dodaj następujące za pomocą dyrektywy:

   ```csharp
   using Microsoft.VisualStudio.Shell;
   ```

3. Opcja strona w tym instruktażu zawiera tylko jedną opcję o nazwie DaysAhead. Dodaj do `ToolsOptions` klasy pole prywatne o nazwie **daysAhead** i właściwość o nazwie **DaysAhead:**

   ```csharp
   private double daysAhead;

   public double DaysAhead
   {
       get { return daysAhead; }
       set { daysAhead = value; }
   }
   ```

   Teraz musisz uświadomić projektowi tę stronę Opcje.

### <a name="make-the-options-page-available-to-users"></a>Udostępnianie użytkownikom strony Opcje

1. W *TodoWindowPackage.cs*, dodaj <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> a `TodoWindowPackage` do klasy:

    ```csharp
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]
    ```

2. Pierwszym parametrem konstruktora ProvideOptionPage jest `ToolsOptions`typ klasy, który został utworzony wcześniej. Drugi parametr, "ToDo", to nazwa kategorii w oknie dialogowym **Opcje.** Trzeci parametr, "Ogólne", to nazwa podkategorii okna dialogowego **Opcje,** w którym będzie dostępna strona Opcje. Następne dwa parametry to identyfikatory zasobów dla ciągów; pierwsza to nazwa kategorii, a druga to nazwa podkategorii. Parametr końcowy określa, czy ta strona jest dostępna za pomocą automatyzacji.

     Gdy użytkownik otworzy stronę Opcje, powinna ona przypominać poniższy obrazek.

     ![Strona opcji](../extensibility/media/t5optionspage.gif "Strona T5Options")

     Zwróć uwagę na kategorię **ToDo** i podkategorię **Ogólne**.

## <a name="make-data-available-to-the-properties-window"></a>Udostępnianie danych w oknie Właściwości
 Można udostępnić informacje listy Zadań do wykonania, tworząc klasę o nazwie, `TodoItem` która przechowuje informacje o poszczególnych elementach na liście Zadań.

1. Dodaj klasę `TodoItem.cs`o nazwie .

     Gdy okno narzędzia jest dostępne dla użytkowników, elementy w Liście Będą reprezentowane przez TodoItems. Gdy użytkownik wybierze jeden z tych elementów w Pole listy, **właściwości** okna wyświetli informacje o elemencie.

     Aby udostępnić dane w oknie **Właściwości,** należy przekształcić dane w właściwości `Description` publiczne, które mają dwa atrybuty specjalne, i `Category`. `Description`to tekst wyświetlany u dołu okna **Właściwości.** `Category`określa, gdzie właściwość powinna być wyświetlana, gdy okno **Właściwości** jest wyświetlane w widoku **Kategoryzowane.** Na poniższej **ilustracji** okno Właściwości znajduje się w widoku **Kategoryzowanym,** wybrano **właściwość Nazwa** w kategorii **Pola do wykonania,** a w dolnej części okna zostanie wyświetlony opis **właściwości Nazwa.**

     ![Okno Właściwości](../extensibility/media/t5properties.png "T5Właściwości")

2. Dodaj następujące za pomocą dyrektyw *TodoItem.cs* pliku.

    ```csharp
    using System.ComponentModel;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Dodaj `public` modyfikator dostępu do deklaracji klasy.

    ```csharp
    public class TodoItem
    {
    }
    ```

     Dodaj dwie właściwości `Name` i `DueDate`. Zrobimy `UpdateList()` i `CheckForErrors()` później.

    ```csharp
    public class TodoItem
    {
        private TodoWindowControl parent;
        private string name;
        [Description("Name of the ToDo item")]
        [Category("ToDo Fields")]
        public string Name
        {
            get { return name; }
            set
            {
                name = value;
                parent.UpdateList(this);
            }
        }

        private DateTime dueDate;
        [Description("Due date of the ToDo item")]
        [Category("ToDo Fields")]
        public DateTime DueDate
        {
            get { return dueDate; }
            set
            {
                dueDate = value;
                parent.UpdateList(this);
                parent.CheckForErrors();
            }
        }
    }
    ```

4. Dodaj odwołanie prywatne do formantu użytkownika. Dodaj konstruktora, który przyjmuje kontrolkę użytkownika i nazwę tego elementu Do. Aby znaleźć wartość `daysAhead`dla , pobiera opcje page właściwości.

    ```csharp
    private TodoWindowControl parent;

    public TodoItem(TodoWindowControl control, string itemName)
    {
        parent = control;
        name = itemName;
        dueDate = DateTime.Now;

        double daysAhead = 0;
        IVsPackage package = parent.parent.Package as IVsPackage;
        if (package != null)
        {
            object obj;
            package.GetAutomationObject("ToDo.General", out obj);

            ToolsOptions options = obj as ToolsOptions;
            if (options != null)
            {
                daysAhead = options.DaysAhead;
            }
        }

        dueDate = dueDate.AddDays(daysAhead);
    }
    ```

5. Ponieważ wystąpienia `TodoItem` klasy będą przechowywane w ListBox i ListBox `ToString` wywoła funkcję, należy `ToString` przeciążyć funkcję. Dodaj następujący kod, aby *TodoItem.cs*, po konstruktorze i przed końcem klasy.

    ```csharp
    public override string ToString()
    {
        return name + " Due: " + dueDate.ToShortDateString();
    }
    ```

6. W *TodoWindowControl.xaml.cs*, dodaj metody skrótowe `TodoWindowControl` do `CheckForError` `UpdateList` klasy i metod. Umieść je po ProcessDialogChar i przed końcem pliku.

    ```csharp
    public void CheckForErrors()
    {
    }
    public void UpdateList(TodoItem item)
    {
    }
    ```

     Metoda `CheckForError` wywoła metodę, która ma taką samą nazwę w obiekcie nadrzędnym, a ta metoda sprawdzi, czy wystąpiły błędy i obsłuży je poprawnie. Metoda `UpdateList` zaktualizuje ListBox w formancie nadrzędnym; metoda jest wywoływana, gdy `Name` i `DueDate` właściwości w tej klasie zmiany. Zostaną one wdrożone później.

## <a name="integrate-into-the-properties-window"></a>Integracja z oknem Właściwości
 Teraz napisz kod, który zarządza ListBox, który będzie związany z **właściwości** okna.

 Należy zmienić przycisk obsługi kliknij, aby odczytać TextBox, utworzyć TodoItem i dodaje go do ListBox.

1. Zastąp istniejącą `button1_Click` funkcję kodem, który tworzy nowy TodoItem i dodaje go do ListBox. Wywołuje `TrackSelection()`, które zostaną zdefiniowane później.

    ```csharp
    private void button1_Click(object sender, RoutedEventArgs e)
    {
        if (textBox.Text.Length > 0)
        {
            var item = new TodoItem(this, textBox.Text);
            listBox.Items.Add(item);
            TrackSelection();
            CheckForErrors();
        }
    }
    ```

2. W widoku Projekt wybierz kontrolkę ListBox. W oknie **Właściwości** kliknij przycisk **Programy obsługi zdarzeń** i znajdź zdarzenie **SelectionChanged.** Wypełnij pole tekstowe **listBox_SelectionChanged**. W ten sposób dodaje skrót dla SelectionChanged programu obsługi i przypisuje go do zdarzenia.

3. Zaimplementuj `TrackSelection()` metodę. Ponieważ trzeba będzie uzyskać <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> usługi, należy <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> udostępnić przez TodoWindowControl. Dodaj następującą metodę do klasy `TodoWindow`:

    ```
    internal object GetVsService(Type service)
    {
        return GetService(service);
    }
    ```

4. Dodaj następujące za pomocą dyrektyw, aby *TodoWindowControl.xaml.cs:*

    ```csharp
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Shell.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    ```

5. Wypełnij program obsługi SelectionChanged w następujący sposób:

    ```
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)
    {
        TrackSelection();
    }
    ```

6. Teraz wypełnij funkcję TrackSelection, która zapewni integrację z okna **Właściwości.** Ta funkcja jest wywoływana, gdy użytkownik dodaje element do Pola listy lub klika element w Pole listy. Dodaje zawartość ListBox do SelectionContainer i przekazuje SelectionContainer do obsługi <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> zdarzeń okna **Właściwości.** Usługa TrackSelection śledzi wybrane obiekty w interfejsie użytkownika (UI) i wyświetla ich właściwości

    ```csharp
    private SelectionContainer mySelContainer;
    private System.Collections.ArrayList mySelItems;
    private IVsWindowFrame frame = null;

    private void TrackSelection()
    {
        if (frame == null)
        {
            var shell = parent.GetVsService(typeof(SVsUIShell)) as IVsUIShell;
            if (shell != null)
            {
                var guidPropertyBrowser = new
                Guid(ToolWindowGuids.PropertyBrowser);
                shell.FindToolWindow((uint)__VSFINDTOOLWIN.FTW_fForceCreate,
                ref guidPropertyBrowser, out frame);
            }
        }
        if (frame != null)
            {
                frame.Show();
            }
        if (mySelContainer == null)
        {
            mySelContainer = new SelectionContainer();
        }

        mySelItems = new System.Collections.ArrayList();

        var selected = listBox.SelectedItem as TodoItem;
        if (selected != null)
        {
            mySelItems.Add(selected);
        }

        mySelContainer.SelectedObjects = mySelItems;

        ITrackSelection track = parent.GetVsService(typeof(STrackSelection))
                                as ITrackSelection;
        if (track != null)
        {
            track.OnSelectChange(mySelContainer);
        }
    }
    ```

     Teraz, gdy masz klasę, której można użyć w oknie **Właściwości,** można zintegrować okno **Właściwości** z oknem narzędzia. Gdy użytkownik kliknie element w Liście w oknie narzędzia, **właściwości** okna powinny być odpowiednio aktualizowane. Podobnie, gdy użytkownik zmieni element DoDo w oknie **Właściwości, skojarzony** element powinien zostać zaktualizowany.

7. Teraz dodaj resztę kodu funkcji UpdateList w *TodoWindowControl.xaml.cs*. Należy upuścić i ponownie dodać zmodyfikowany TodoItem z ListBox.

    ```csharp
    public void UpdateList(TodoItem item)
    {
        var index = listBox.SelectedIndex;
        listBox.Items.RemoveAt(index);
        listBox.Items.Insert(index, item);
        listBox.SelectedItem = index;
    }
    ```

8. Przetestuj swój kod. Skompiluj projekt i rozpocznij debugowanie. Powinno pojawić się wystąpienie eksperymentalne.

9. Otwórz stronę**Opcje** **narzędzi.** >  W lewym okienku powinna zostać wyświetlone kategoria Do wykonania. Kategorie są wymienione w alfabetycznym, więc spójrz pod Ts.

10. Na stronie Opcje **Todo** powinna `DaysAhead` zostać wyświetlona właściwość ustawiona na **0**. Zmień go na **2**.

11. W menu **Widok / Inne okna** otwórz **todoWindow**. Wpisz **polecenie EndDate** w polu tekstowym i kliknij przycisk **Dodaj**.

12. W polu listy powinieneś zobaczyć datę dwa dni później niż dzisiaj.

## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Dodawanie tekstu do okna Dane wyjściowe i elementów do listy zadań
 Dla **listy zadań**należy utworzyć nowy obiekt typu Zadanie, a następnie dodać obiekt `Add` Zadanie do listy **zadań,** wywołując jego metodę. Aby zapisać w oknie **Dane wyjściowe,** należy wywołać jego `GetPane` metodę, `OutputString` aby uzyskać obiekt okienka, a następnie wywołać metodę obiektu okienka.

1. W *TodoWindowControl.xaml.cs*, w `button1_Click` metodzie, dodaj kod, aby uzyskać **ogólne** okienka okna **dane wyjściowe** (co jest ustawieniem domyślnym) i zapisuj do niego. Metoda powinna teraz wyglądać następująco:

    ```csharp
    private void button1_Click(object sender, EventArgs e)
    {
        if (textBox.Text.Length > 0)
        {
            var item = new TodoItem(this, textBox.Text);
            listBox.Items.Add(item);

            var outputWindow = parent.GetVsService(
                typeof(SVsOutputWindow)) as IVsOutputWindow;
            IVsOutputWindowPane pane;
            Guid guidGeneralPane = VSConstants.GUID_OutWindowGeneralPane;
            outputWindow.GetPane(ref guidGeneralPane, out pane);
            if (pane != null)
            {
                 pane.OutputString(string.Format(
                    "To Do item created: {0}\r\n",
                 item.ToString()));
        }
            TrackSelection();
            CheckForErrors();
        }
    }
    ```

2. Aby dodać elementy do listy zadań, należy dodać klasę zagnieżdżoną do klasy TodoWindowControl. Klasa zagnieżdżona <xref:Microsoft.VisualStudio.Shell.TaskProvider>musi pochodzić od . Dodaj następujący kod na końcu `TodoWindowControl` klasy.

    ```csharp
    [Guid("72de1eAD-a00c-4f57-bff7-57edb162d0be")]
    public class TodoWindowTaskProvider : TaskProvider
    {
        public TodoWindowTaskProvider(IServiceProvider sp)
            : base(sp)
        {
        }
    }
    ```

3. Następnie dodaj odwołanie `TodoTaskProvider` prywatne `CreateProvider()` i metodę `TodoWindowControl` do klasy. Kod powinien wyglądać następująco:

    ```csharp
    private TodoWindowTaskProvider taskProvider;
    private void CreateProvider()
    {
        if (taskProvider == null)
        {
            taskProvider = new TodoWindowTaskProvider(parent);
            taskProvider.ProviderName = "To Do";
        }
    }
    ```

4. Dodaj `ClearError()`, który czyści listę `ReportError()`zadań i , który dodaje wpis `TodoWindowControl` do listy zadań, do klasy.

    ```csharp
    private void ClearError()
    {
        CreateProvider();
        taskProvider.Tasks.Clear();
    }
    private void ReportError(string p)
    {
        CreateProvider();
        var errorTask = new Task();
        errorTask.CanDelete = false;
        errorTask.Category = TaskCategory.Comments;
        errorTask.Text = p;

        taskProvider.Tasks.Add(errorTask);

        taskProvider.Show();

        var taskList = parent.GetVsService(typeof(SVsTaskList))
            as IVsTaskList2;
        if (taskList == null)
        {
            return;
        }

        var guidProvider = typeof(TodoWindowTaskProvider).GUID;
         taskList.SetActiveProvider(ref guidProvider);
    }
    ```

5. Teraz zaimplementuj `CheckForErrors` metodę w następujący sposób.

    ```csharp
    public void CheckForErrors()
    {
        foreach (TodoItem item in listBox.Items)
        {
            if (item.DueDate < DateTime.Now)
            {
                ReportError("To Do Item is out of date: "
                    + item.ToString());
            }
        }
    }
    ```

## <a name="try-it-out"></a>Testowanie

1. Skompiluj projekt i rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie.

2. Otwórz **Okno TodoWindow** (**Wyświetl** > **inne okna** > **TodoWindow**).

3. Wpisz coś w polu tekstowym, a następnie kliknij przycisk **Dodaj**.

     Data ukończenia 2 dni po dniu dzisiejszym jest dodawany do pola listy. Nie są generowane żadne błędy, a **lista zadań** **(Wyświetl** > **listę zadań)** nie powinna mieć żadnych wpisów.

4. Teraz zmień ustawienie na stronie**Opcje** >  **narzędzi** > **do wykonania** z **2** z powrotem na **0**.

5. Wpisz coś innego w **TodoWindow,** a następnie kliknij przycisk **Dodaj** ponownie. Spowoduje to wyświetlenie błędu, a także wpisu na **liście zadań**.

     Podczas dodawania elementów początkowa data jest ustawiona na teraz plus 2 dni.

6. W menu **Widok** kliknij polecenie **Dane wyjściowe,** aby otworzyć okno **Dane wyjściowe.**

     Należy zauważyć, że za każdym razem, gdy dodajesz element, w okienku **Lista zadań** jest wyświetlany komunikat.

7. Kliknij jeden z elementów w skrzynce listy.

     Okno **Właściwości** wyświetla dwie właściwości towaru.

8. Zmień jedną z właściwości, a następnie naciśnij klawisz **Enter**.

     Element zostanie zaktualizowany w pole listy.
