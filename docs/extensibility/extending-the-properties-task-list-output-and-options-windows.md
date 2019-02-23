---
title: Rozszerzanie właściwości, listy zadań, danych wyjściowych i opcji Windows | Dokumentacja firmy Microsoft
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
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1a32772abb6dd0a4fb1a2d1dc7026cf5d4bac214
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56717822"
---
# <a name="extend-the-properties-task-list-output-and-options-windows"></a>Rozszerzanie właściwości, listy zadań, danych wyjściowych i opcji systemu windows
Możesz uzyskać dostęp do każdego okna narzędzi w programie Visual Studio. W tym przewodniku pokazano, jak zintegrować informacji na temat okna narzędzia nową **opcje** strony i nowe ustawienie na **właściwości** strony, a także zapisywać **listy zadań** i **dane wyjściowe** systemu windows.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalacji programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-tool-window"></a>Tworzenie rozszerzenia za pomocą okna narzędzi

1.  Utwórz projekt o nazwie **TodoList** przy użyciu szablonu VSIX, a następnie dodaj niestandardowe narzędzie szablon elementu okno o nazwie **TodoWindow**.

    > [!NOTE]
    >  Aby uzyskać więcej informacji na temat tworzenia rozszerzenia za pomocą okna narzędzi, zobacz [Tworzenie rozszerzenia za pomocą okna narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="set-up-the-tool-window"></a>Konfigurowanie okna narzędzi
 Dodaj pole tekstowe, w którym można wpisać nowy element ToDo, przycisk, aby dodać nowy element do listy i pola listy w celu wyświetlenia elementów na liście.

1.  W *TodoWindow.xaml*, usuwanie kontrolek przycisku, pola tekstowego i StackPanel UserControl.

    > [!NOTE]
    >  Nie spowoduje to usunięcia **button1_Click** obsługi zdarzeń, który zostanie ponownie użyty w kolejnym kroku.

2.  Z **wszystkie formanty WPF** części **przybornika**, przeciągnij **kanwy** formant do siatki.

3.  Przeciągnij **TextBox**, **przycisk**, a **ListBox** do kanwy. Rozmieść elementy, tak aby pole tekstowe i przycisk znajdują się na tym samym poziomie, a pole listy wypełnia pozostałe okna pod pozycją je, tak jak na ilustracji poniżej.

     ![Zakończono okna narzędzia](../extensibility/media/t5-toolwindow.png "T5 ToolWindow")

4.  W okienku XAML znaleźć przycisk i ustaw jej właściwości zawartości **Dodaj**. Ponownie połączyć program obsługi zdarzeń przycisku do kontrolki przycisku, dodając `Click="button1_Click"` atrybutu. W bloku obszaru roboczego powinien wyglądać następująco:

    ```xml
    <Canvas HorizontalAlignment="Left" Width="306">
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>
    </Canvas>
    ```

### <a name="customize-the-constructor"></a>Dostosowywanie konstruktora

1.  W *TodoWindowControl.xaml.cs* plików, dodaj następującą instrukcję using:

    ```csharp
    using System;
    ```

2.  Dodaj publiczny odwołanie do TodoWindow i ma konstruktora TodoWindowControl przyjmować parametr TodoWindow. Kod powinien wyglądać następująco:

    ```csharp
    public TodoWindow parent;

    public TodoWindowControl(TodoWindow window)
    {
        InitializeComponent();
        parent = window;
    }
    ```

3.  W *TodoWindow.cs*, zmień TodoWindowControl konstruktora, aby dodać parametr TodoWindow. Kod powinien wyglądać następująco:

    ```csharp
    public TodoWindow() : base(null)
    {
        this.Caption = "TodoWindow";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;

         this.Content = new TodoWindowControl(this);
    }
    ```

## <a name="create-an-options-page"></a>Tworzenie strony opcji
 Możesz podać strony w **opcje** okno dialogowe, dzięki czemu użytkownicy mogą zmieniać ustawienia dla okna narzędzia. Tworzenie strony opcji wymaga obu klasę, która w tym artykule opisano opcje i wpis w *TodoListPackage.cs* lub *TodoListPackage.vb* pliku.

1. Dodaj klasę o nazwie `ToolsOptions.cs`. Wprowadź `ToolsOptions` klasa dziedziczy <xref:Microsoft.VisualStudio.Shell.DialogPage>.

   ```csharp
   class ToolsOptions : DialogPage
   {
   }
   ```

2. Dodaj następującą instrukcję using:

   ```csharp
   using Microsoft.VisualStudio.Shell;
   ```

3. Strona opcji, w tym przewodniku zawiera tylko jedną opcję o nazwie DaysAhead. Dodaj pole private o nazwie **daysAhead** i właściwość o nazwie **DaysAhead** do `ToolsOptions` klasy:

   ```csharp
   private double daysAhead;

   public double DaysAhead
   {
       get { return daysAhead; }
       set { daysAhead = value; }
   }
   ```

   Teraz należy projekt o tej stronie opcje.

### <a name="make-the-options-page-available-to-users"></a>Udostępnić użytkownikom stronę opcji

1.  W *TodoWindowPackage.cs*, Dodaj <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> do `TodoWindowPackage` klasy:

    ```csharp
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]
    ```

2.  Pierwszy parametr do konstruktora ProvideOptionPage jest typ klasy `ToolsOptions`, która została utworzona wcześniej. Drugi parametr "ToDo" to nazwa kategorii w **opcje** okno dialogowe. Trzeci parametr "Ogólne", nazywa się Podkategoria **opcje** okno dialogowe, w której będą dostępne na stronie opcji. Następne dwa parametry są identyfikatory zasobów dla ciągów; Pierwszy to nazwa kategorii, a drugi to nazwa podkategorii. Ostatni parametr określa, czy ta strona jest możliwy za pomocą automatyzacji.

     Gdy użytkownik otwiera stronę opcje, powinien on przypominać poniższej ilustracji.

     ![Strona opcji](../extensibility/media/t5optionspage.gif "T5OptionsPage")

     Zwróć uwagę, Kategoria **ToDo** i podkategorii **ogólne**.

## <a name="make-data-available-to-the-properties-window"></a>Udostępnianie danych w oknie dialogowym właściwości
 Możesz udostępnić informacje listy zadań do wykonania, tworząc klasę o nazwie `TodoItem` która przechowuje informacje o poszczególnych elementów listy zadań do wykonania.

1.  Dodaj klasę o nazwie `TodoItem.cs`.

     Po udostępnieniu użytkownikom okna narzędzi elementów w kontrolce ListBox będą reprezentowane przez TodoItems. Gdy użytkownik wybierze jeden z tych elementów w kontrolce ListBox, **właściwości** oknie będą wyświetlane informacje na temat elementu.

     Aby udostępnić dane w **właściwości** okna, możesz przekształcić w danych właściwości publiczne, które mają dwa atrybuty specjalne, `Description` i `Category`. `Description` to tekst, który pojawia się w dolnej części **właściwości** okna. `Category` Określa, gdzie właściwość powinna zostać wyświetlona po **właściwości** okno jest wyświetlane w **kategorii** widoku. Na poniższej ilustracji **właściwości** okno **kategorii** widoku **nazwa** właściwości w **pól zadań do wykonania** kategorii zaznaczone oraz opis **nazwa** właściwości są wyświetlane u dołu okna.

     ![Okno właściwości](../extensibility/media/t5properties.png "T5Properties")

2.  Dodaj następujące instrukcje using *TodoItem.cs* pliku.

    ```csharp
    using System.ComponentModel;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3.  Dodaj `public` modyfikator dostępu do deklaracji klasy.

    ```csharp
    public class TodoItem
    {
    }
    ```

     Dodaj dwie właściwości `Name` i `DueDate`. Wykonamy `UpdateList()` i `CheckForErrors()` później.

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

4.  Dodaj odwołanie prywatnych do kontrolki użytkownika. Dodaj Konstruktor, który przyjmuje nazwę dla tego elementu ToDo i kontrolki użytkownika. Aby znaleźć wartość `daysAhead`, pobiera właściwość strony opcje.

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

5.  Ponieważ wystąpienia `TodoItem` klasy, które będą przechowywane w polu listy i pole listy będzie wywoływać `ToString` funkcji, muszą przeciążać `ToString` funkcji. Dodaj następujący kod do *TodoItem.cs*po konstruktora i przed końcem klasy.

    ```csharp
    public override string ToString()
    {
        return name + " Due: " + dueDate.ToShortDateString();
    }
    ```

6.  W *TodoWindowControl.xaml.cs*, Dodaj metody klasy zastępczej `TodoWindowControl` klasy dla `CheckForError` i `UpdateList` metody. Umieść je po ProcessDialogChar i przed końcem pliku.

    ```csharp
    public void CheckForErrors()
    {
    }
    public void UpdateList(TodoItem item)
    {
    }
    ```

     `CheckForError` Metoda wywoła metodę, która ma taką samą nazwę w obiekcie nadrzędnym, a metoda sprawdzi, czy wystąpiły wszelkie błędy, a je poprawnie obsłużyć. `UpdateList` Metoda zaktualizuje ListBox formantu nadrzędnego; metoda jest wywoływana, gdy `Name` i `DueDate` właściwości w tej zmianie klasy. Będą one prowadzone później.

## <a name="integrate-into-the-properties-window"></a>Integrowanie w oknie właściwości
 Teraz napisać kod, który zarządza ListBox, który zostanie powiązany **właściwości** okna.

 Należy zmienić przycisk kliknij program obsługi do odczytu w polu tekstowym, Utwórz czynność do wykonania i dodaje go do pola listy.

1.  Zastąp istniejące `button1_Click` funkcji z kodem, który tworzy nowy TodoItem i dodaje go do pola listy. Wywołuje `TrackSelection()`, które będą definiowane później.

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

2.  W widoku projektu wybierz kontrolkę ListBox. W **właściwości** kliknij okno **procedury obsługi zdarzeń** przycisk i Znajdź **SelectionChanged** zdarzeń. Wypełnij pole tekstowe z **listBox_SelectionChanged**. W ten sposób dodaje wycinka obsługi SelectionChanged i przypisuje go do zdarzenia.

3.  Implementowanie `TrackSelection()` metody. Ponieważ będą potrzebne uzyskać <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> usług, należy wprowadzić <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> dostępny za pomocą TodoWindowControl. Dodaj następującą metodę do `TodoWindow` klasy:

    ```
    internal object GetVsService(Type service)
    {
        return GetService(service);
    }
    ```

4.  Dodaj następujące instrukcje using *TodoWindowControl.xaml.cs*:

    ```csharp
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Shell.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    ```

5.  Należy wypełnić w obsłudze SelectionChanged w następujący sposób:

    ```
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)
    {
        TrackSelection();
    }
    ```

6.  Teraz, wypełnij funkcji TrackSelection, która zapewnia integrację z usługą **właściwości** okna. Ta funkcja jest wywoływana, gdy użytkownik dodaje element do pola listy lub kliknie element w kontrolce ListBox. Dodaje zawartość pola listy do SelectionContainer i przekazuje SelectionContainer do **właściwości** okna <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> programu obsługi zdarzeń. Usługa TrackSelection śledzi wybranych obiektów w interfejsie użytkownika (UI) i wyświetla ich właściwości

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

     Teraz, gdy masz klasę, **właściwości** okna można użyć, możesz zintegrować **właściwości** okno z okna narzędzia. Gdy użytkownik kliknie element na liście w oknie narzędzia **właściwości** okna powinien być odpowiednio aktualizowany. Podobnie, gdy użytkownik zmieni wykonania w **właściwości** oknie skojarzony element powinien zostać zaktualizowany.

7.  Teraz, Dodaj pozostałe UpdateList kod funkcji w *TodoWindowControl.xaml.cs*. Powinien usunąć i ponownie dodać TodoItem zmodyfikowane w polu listy.

    ```csharp
    public void UpdateList(TodoItem item)
    {
        var index = listBox.SelectedIndex;
        listBox.Items.RemoveAt(index);
        listBox.Items.Insert(index, item);
        listBox.SelectedItem = index;
    }
    ```

8.  Przetestuj swój kod. Skompiluj projekt, a następnie rozpocząć debugowanie. Wystąpienie eksperymentalne powinna zostać wyświetlona.

9. Otwórz **narzędzia** > **opcje** strony. Powinien zostać wyświetlony kategorii zadań do wykonania, w okienku po lewej stronie. Kategorie są wyświetlane w alfabetycznej, aby można było w ramach usług terminalowych.

10. Na **Todo** Strona opcji, powinien zostać wyświetlony `DaysAhead` właściwością **0**. Zmień ją na **2**.

11. Na **widok / inne Windows** menu Otwórz **TodoWindow**. Typ **EndDate** w polu tekstowym i kliknij **Dodaj**.

12. W polu listy powinny być widoczne dwa dni późniejsza niż dzisiejsza data.

## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Dodaj tekst w oknie danych wyjściowych i elementy do listy zadań
 Dla **listy zadań**, Utwórz nowy obiekt typu zadania, a następnie dodaj ten obiekt zadania, aby **listy zadań** przez wywołanie jego `Add` metody. Można zapisać do **dane wyjściowe** okna, należy wywołać jej `GetPane` wywołać metodę, aby uzyskać obiekt okienka, a następnie `OutputString` metody obiektu w okienku.

1.  W *TodoWindowControl.xaml.cs*w `button1_Click` metody, Dodaj kod, aby uzyskać **ogólne** okienku **dane wyjściowe** oknie (jest to ustawienie domyślne) i zapisanie w nim. Metoda powinna wyglądać następująco:

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

2.  Aby dodać elementy do listy zadań, należy dodać klasę zagnieżdżoną klasę TodoWindowControl. Klasa zagnieżdżona musi pochodzić od <xref:Microsoft.VisualStudio.Shell.TaskProvider>. Dodaj następujący kod na końcu `TodoWindowControl` klasy.

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

3.  Następnie dodaj odwołanie prywatnych do `TodoTaskProvider` i `CreateProvider()` metody `TodoWindowControl` klasy. Kod powinien wyglądać następująco:

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

4.  Dodaj `ClearError()`, która czyści listę zadań, oraz `ReportError()`, która dodaje wpis do listy zadań do `TodoWindowControl` klasy.

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

5.  Teraz wdrożyć `CheckForErrors` metody w następujący sposób.

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

## <a name="try-it-out"></a>Wypróbuj

1.  Skompiluj projekt, a następnie rozpocząć debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne.

2.  Otwórz **TodoWindow** (**widoku** > **innych Windows** > **TodoWindow**).

3.  W polu tekstowym wpisz coś, a następnie kliknij przycisk **Dodaj**.

     Termin 2 dni od dzisiaj jest dodawany do pola listy. Są generowane nie błędy, a **listy zadań** (**widoku** > **listy zadań**) powinien mieć żadnych wpisów.

4.  Teraz Zmień ustawienie na **narzędzia** > **opcje** > **ToDo** strony **2** do **0**.

5.  Wpisz coś innego w **TodoWindow** a następnie kliknij przycisk **Dodaj** ponownie. Spowoduje to wyzwolenie błąd, a także do wpisu w **listy zadań**.

     Podczas dodawania elementów początkowa data ustawiono teraz plus 2 dni.

6.  Na **widoku** menu, kliknij przycisk **dane wyjściowe** otworzyć **dane wyjściowe** okna.

     Należy zauważyć, że zawsze że dodawanie elementu, zostanie wyświetlony komunikat w **listy zadań** okienka.

7.  Kliknij jeden z elementów w kontrolce ListBox.

     **Właściwości** oknie zostaną wyświetlone dwie właściwości dla elementu.

8.  Zmień jedną z właściwości, a następnie naciśnij klawisz **Enter**.

     Element jest aktualizowany w kontrolce ListBox.