---
title: Okna rozszerzania właściwości, Lista zadań, danych wyjściowych i opcji
description: Dowiedz się, jak zintegrować informacje o oknie narzędzi w Visual Studio na nowej stronie Opcje i nowym ustawieniu na stronie Właściwości.
ms.date: 11/04/2016
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3334ba3694ee3c1354c152b013c38472e4b90b72
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903284"
---
# <a name="extend-the-properties-task-list-output-and-options-windows"></a>Rozszerzanie okien właściwości, Lista zadań, danych wyjściowych i opcji
Możesz uzyskać dostęp do dowolnego okna narzędzi w Visual Studio. W tym przewodniku pokazano, jak zintegrować  informacje o oknie  narzędzia z nową stroną **Opcje** i nowym ustawieniem na stronie Właściwości, a także jak zapisywać w oknach Lista zadań **i wyjściowych.**

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od Visual Studio 2015 r., zestaw SDK usługi Visual Studio nie jest instalowany z Centrum pobierania. Jest ona dołączona jako opcjonalna funkcja w Visual Studio konfiguracji. Zestaw VS SDK można również zainstalować później. Aby uzyskać więcej informacji, zobacz Install the Visual Studio SDK (Instalowanie [Visual Studio SDK).](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-an-extension-with-a-tool-window"></a>Tworzenie rozszerzenia za pomocą okna narzędzi

1. Utwórz projekt o nazwie **TodoList** przy użyciu szablonu VSIX i dodaj szablon niestandardowego elementu okna narzędzi o **nazwie TodoWindow.**

    > [!NOTE]
    > Aby uzyskać więcej informacji na temat tworzenia rozszerzenia za pomocą okna narzędzi, zobacz Create an extension with a tool window (Tworzenie [rozszerzenia za pomocą okna narzędzi).](../extensibility/creating-an-extension-with-a-tool-window.md)

## <a name="set-up-the-tool-window"></a>Konfigurowanie okna narzędzi
 Dodaj pole tekstowe, w którym ma być wpisanie nowego elementu ToDo, przycisk, aby dodać nowy element do listy, oraz pole ListBox do wyświetlania elementów na liście.

1. W *pliku TodoWindow.xaml* usuń kontrolki Button, TextBox i StackPanel z kontrolki UserControl.

    > [!NOTE]
    > Nie powoduje to usunięcia **button1_Click** zdarzeń, które zostaną ponownie użyte w późniejszym kroku.

2. Z sekcji **Wszystkie kontrolki WPF** przybornika przeciągnij  **kontrolkę Kanwa** do siatki.

3. Przeciągnij pola **TextBox,** **Button** i **ListBox do** kanwy. Rozmieść elementy tak, aby elementy TextBox i Button znajdują się na tym samym poziomie, a pole ListBox wypełni pozostałą część okna poniżej, jak na poniższej ilustracji.

     ![Gotowe okno narzędzia](../extensibility/media/t5-toolwindow.png "T5-ToolWindow")

4. W okienku XAML znajdź przycisk i ustaw jego właściwość Content na **dodaj**. Połącz ponownie program obsługi zdarzeń przycisku z kontrolką Przycisk, dodając `Click="button1_Click"` atrybut. Blok Kanwa powinien wyglądać tak:

    ```xml
    <Canvas HorizontalAlignment="Left" Width="306">
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>
    </Canvas>
    ```

### <a name="customize-the-constructor"></a>Dostosowywanie konstruktora

1. W pliku *TodoWindowControl.xaml.cs* dodaj następującą dyrektywę using:

    ```csharp
    using System;
    ```

2. Dodaj publiczne odwołanie do todoWindow i konstruktor TodoWindowControl weź parametr TodoWindow. Kod powinien wyglądać tak:

    ```csharp
    public TodoWindow parent;

    public TodoWindowControl(TodoWindow window)
    {
        InitializeComponent();
        parent = window;
    }
    ```

3. W *todoWindow.cs*, zmień TodoWindowControl konstruktora, aby uwzględnić TodoWindow parametru. Kod powinien wyglądać tak:

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
 W oknie dialogowym  Opcje możesz podać stronę, aby użytkownicy mogą zmieniać ustawienia okna narzędzi. Tworzenie strony Opcje wymaga zarówno klasy, która opisuje opcje, jak i wpisu w pliku *TodoListPackage.cs* lub *TodoListPackage.vb.*

1. Dodaj klasę o nazwie `ToolsOptions.cs` . Sprawić, `ToolsOptions` aby klasa dziedziczyła z <xref:Microsoft.VisualStudio.Shell.DialogPage> klasy .

   ```csharp
   class ToolsOptions : DialogPage
   {
   }
   ```

2. Dodaj następującą dyrektywę using:

   ```csharp
   using Microsoft.VisualStudio.Shell;
   ```

3. Strona Opcje w tym przewodniku zawiera tylko jedną opcję o nazwie DaysAhead. Dodaj do klasy pole prywatne o nazwie **daysAhead** i właściwość o nazwie **DaysAhead:** `ToolsOptions`

   ```csharp
   private double daysAhead;

   public double DaysAhead
   {
       get { return daysAhead; }
       set { daysAhead = value; }
   }
   ```

   Teraz musisz pamiętać projekt o tej stronie Opcje.

### <a name="make-the-options-page-available-to-users"></a>Udostępnij użytkownikom stronę Opcje

1. W *todoWindowPackage.cs* dodaj do <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> klasy `TodoWindowPackage` :

    ```csharp
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]
    ```

2. Pierwszym parametrem konstruktora ProvideOptionPage jest typ utworzonej `ToolsOptions` wcześniej klasy . Drugi parametr, "ToDo", to nazwa kategorii w **oknie dialogowym** Opcje. Trzeci parametr, "Ogólne", to nazwa podkategorii  okna dialogowego Opcje, w którym będzie dostępna strona Opcje. Dwa następne parametry to identyfikatory zasobów dla ciągów. Pierwszy to nazwa kategorii, a drugi to nazwa podkategorii. Ostatni parametr określa, czy dostęp do tej strony można uzyskać za pomocą automatyzacji.

     Gdy użytkownik otworzy stronę Opcje, powinna ona wyglądać jak na poniższej ilustracji.

     ![Strona opcji](../extensibility/media/t5optionspage.gif "T5OptionsPage")

     Zwróć uwagę na **kategorię ToDo** i podkategorię **Ogólne.**

## <a name="make-data-available-to-the-properties-window"></a>Udostępnij dane okno Właściwości
 Aby udostępnić informacje o liście zadań do zatwierdzeń, można utworzyć klasę o nazwie , która przechowuje informacje o poszczególnych elementach `TodoItem` na liście zadań do zatwierdzeń.

1. Dodaj klasę o nazwie `TodoItem.cs` .

     Gdy okno narzędzia jest dostępne dla użytkowników, elementy w listBox będą reprezentowane przez TodoItems. Gdy użytkownik wybierze jeden z tych elementów  w poleceniu ListBox, w oknie Właściwości zostaną wyświetlane informacje o tym elementie.

     Aby udostępnić dane w **oknie** Właściwości, należy przekształcić dane w właściwości publiczne, które mają dwa specjalne atrybuty: `Description` i `Category` . `Description` to tekst wyświetlany w dolnej części **okna** Właściwości. `Category`Określa, gdzie właściwość powinna być wyświetlana, gdy **okno** Właściwości jest wyświetlane w widoku **Kategoryzowane.** Na poniższej ilustracji okno  Właściwości znajduje się w widoku Kategoryzowanie, wybrana jest właściwość **Name** w kategorii **Pola todo,** a opis właściwości  **Name** jest wyświetlany w dolnej części okna.

     ![Okno właściwości](../extensibility/media/t5properties.png "T5Properties (Właściwości T5)")

2. Dodaj następujące dyrektywy using do *pliku TodoItem.cs.*

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

     Dodaj dwie właściwości: `Name` i `DueDate` . Zrobimy to `UpdateList()` `CheckForErrors()` później.

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

4. Dodaj prywatne odwołanie do kontrolki użytkownika. Dodaj konstruktor, który przejmuje kontrolę użytkownika i nazwę tego elementu ToDo. Aby znaleźć wartość `daysAhead` dla właściwości , pobiera ona właściwość strona Opcje.

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

5. Ponieważ wystąpienia klasy będą przechowywane w listbox, a ListBox wywoła `TodoItem` `ToString` funkcję, należy przeciążyć `ToString` funkcję. Dodaj następujący kod do *todoItem.cs* po konstruktorze i przed końcem klasy .

    ```csharp
    public override string ToString()
    {
        return name + " Due: " + dueDate.ToShortDateString();
    }
    ```

6. W *pliku TodoWindowControl.xaml.cs* dodaj metody wycinki do `TodoWindowControl` klasy dla metod i `CheckForError` `UpdateList` . Umieść je po pliku ProcessDialogChar i przed końcem pliku.

    ```csharp
    public void CheckForErrors()
    {
    }
    public void UpdateList(TodoItem item)
    {
    }
    ```

     Metoda wywoła metodę, która ma taką samą nazwę w obiekcie nadrzędnym, i sprawdzi, czy wystąpiły błędy, i obsłuży `CheckForError` je poprawnie. Metoda zaktualizuje element ListBox w kontrolce nadrzędnej. Metoda jest wywoływana, gdy właściwości `UpdateList` i w tej klasie `Name` `DueDate` zmienią się. Zostaną one zaimplementowane później.

## <a name="integrate-into-the-properties-window"></a>Integracja z okno Właściwości
 Teraz napisz kod, który zarządza listBox, który zostanie powiązany z **oknem** Właściwości.

 Musisz zmienić program obsługi kliknięcia przycisku, aby odczytać pole tekstowe, utworzyć todoItem i dodaje go do listy ListBox.

1. Zastąp istniejącą `button1_Click` funkcję kodem, który tworzy nowy todoItem i dodaje go do listBox. Wywołuje on `TrackSelection()` , który zostanie zdefiniowany później.

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

2. W widok Projekt kontrolkę ListBox. W **oknie Właściwości** kliknij przycisk **Procedury obsługi** zdarzeń i znajdź zdarzenie **SelectionChanged.** Wypełnij pole tekstowe przy użyciu **listBox_SelectionChanged**. W ten sposób dodano wycinki programu obsługi SelectionChanged i przypisano go do zdarzenia.

3. Zaim `TrackSelection()` implementuj metodę . Ponieważ musisz uzyskać te usługi, musisz udostępnić je za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> todoWindowControl. Dodaj następującą metodę do klasy `TodoWindow`:

    ```
    internal object GetVsService(Type service)
    {
        return GetService(service);
    }
    ```

4. Dodaj następujące dyrektywy using do *pliku TodoWindowControl.xaml.cs:*

    ```csharp
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Shell.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    ```

5. Wypełnij procedury obsługi SelectionChanged w następujący sposób:

    ```
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)
    {
        TrackSelection();
    }
    ```

6. Teraz wypełnij funkcję TrackSelection, która zapewni integrację z **oknem** Właściwości. Ta funkcja jest wywoływana, gdy użytkownik dodaje element do elementu ListBox lub klika element w listBox. Dodaje on zawartość obiektu ListBox do obiektu SelectionContainer i przekazuje  go do procedury obsługi zdarzeń <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> okna Właściwości. Usługa TrackSelection śledzi wybrane obiekty w interfejsie użytkownika i wyświetla ich właściwości

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

     Teraz, gdy masz klasę, **z** których może korzystać okno Właściwości, możesz zintegrować okno **Właściwości** z oknem narzędzi. Gdy użytkownik kliknie element w aplikacji ListBox w oknie narzędzia, **okno** Właściwości powinno zostać odpowiednio zaktualizowane. Podobnie, gdy użytkownik zmieni element ToDo w oknie **Właściwości,** skojarzony element powinien zostać zaktualizowany.

7. Teraz dodaj pozostałą część kodu funkcji UpdateList w pliku *TodoWindowControl.xaml.cs*. Powinna ona usunąć i ponownie dodać zmodyfikowane todoItem z listy ListBox.

    ```csharp
    public void UpdateList(TodoItem item)
    {
        var index = listBox.SelectedIndex;
        listBox.Items.RemoveAt(index);
        listBox.Items.Insert(index, item);
        listBox.SelectedItem = index;
    }
    ```

8. Przetestuj kod. Skompilowanie projektu i rozpoczęcie debugowania. Powinno zostać wyświetlone wystąpienie eksperymentalne.

9. Otwórz stronę  >  **Opcje** narzędzi. W okienku po lewej stronie powinna zostać wyświetlony kategoria ToDo. Kategorie są wymienione w porządku alfabetycznym, więc sprawdź w obszarze Ts (Ts).

10. Na **stronie opcji todo** powinna zostać wyświetlony właściwość `DaysAhead` ustawiona na **0**. Zmień ją na **2**.

11. W menu **View /Other Windows (Widok/inne okna)** otwórz **pozycję TodoWindow.** W **polu tekstowym wpisz EndDate** i kliknij przycisk **Dodaj**.

12. W polu listy powinna zostać wyświetlona data dwa dni późniejsza niż dzisiaj.

## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Dodaj tekst do okna Dane wyjściowe i elementy do Lista zadań
 Dla **Lista zadań** należy utworzyć nowy obiekt typu Task, a następnie dodać ten obiekt Task do **Lista zadań,** wywołując jego `Add` metodę . Aby zapisać dane w **oknie Dane** wyjściowe, należy wywołać jego metodę w celu uzyskania obiektu okienka, a następnie wywołać `GetPane` metodę obiektu `OutputString` okienka.

1. W *pliku TodoWindowControl.xaml.cs* w metodzie dodaj kod w celu uzyskania okienka Ogólne okna Dane wyjściowe (co jest ustawieniem domyślnym) i `button1_Click` zapisz go.   Metoda powinna teraz wyglądać następująco:

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

2. Aby dodać elementy do Lista zadań, należy dodać zagnieżdżone klasy do klasy TodoWindowControl. Klasa zagnieżdżona musi pochodzić od <xref:Microsoft.VisualStudio.Shell.TaskProvider> klasy . Dodaj następujący kod na końcu `TodoWindowControl` klasy .

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

3. Następnie dodaj prywatne odwołanie do klasy `TodoTaskProvider` i metodę do klasy `CreateProvider()` `TodoWindowControl` . Kod powinien wyglądać tak:

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

4. Dodaj `ClearError()` , co powoduje wyczyszczenie Lista zadań i , co powoduje dodanie wpisu do Lista zadań do klasy `ReportError()` `TodoWindowControl` .

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

5. Teraz zaim `CheckForErrors` implementuj metodę w następujący sposób.

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

## <a name="try-it-out"></a>Czas to wypróbować

1. Skompilowanie projektu i rozpoczęcie debugowania. Zostanie wyświetlone wystąpienie eksperymentalne.

2. Otwórz okno **TodoWindow** **(Wyświetl**  >  **inne okna**  >  **TodoWindow).**

3. Wpisz coś w polu tekstowym, a następnie kliknij przycisk **Dodaj**.

     Data płatności 2 dni po dacie dzisiejszej jest dodawana do pola listy. Nie są generowane żadne  błędy, a Lista zadań **(Wyświetl** Lista zadań  >  ) nie powinny mieć żadnych wpisów.

4. Teraz zmień ustawienie na stronie **Narzędzia**  >  **Opcje**  >  **toDo** z **2 z powrotem** na **0**.

5. Wpisz coś innego w **todoWindow,** a następnie kliknij **przycisk Dodaj** ponownie. Wyzwoli to błąd, a także wpis w **Lista zadań**.

     W przypadku dodawania elementów początkowa data jest ustawiona na wartość plus 2 dni.

6. W menu **Widok** kliknij pozycję **Dane wyjściowe,** aby otworzyć **okno Dane** wyjściowe.

     Zwróć uwagę, że za każdym razem, gdy dodajesz element, w okienku Lista zadań **wyświetlany** komunikat.

7. Kliknij jeden z elementów w listBox.

     W **oknie** Właściwości zostaną wyświetlone dwie właściwości elementu.

8. Zmień jedną z właściwości, a następnie naciśnij **klawisz Enter**.

     Element zostanie zaktualizowany w poleceniu ListBox.
