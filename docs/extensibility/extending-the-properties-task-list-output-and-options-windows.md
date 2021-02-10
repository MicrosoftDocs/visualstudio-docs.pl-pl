---
title: Rozszerzone właściwości, Lista zadań, dane wyjściowe, Opcje systemu Windows
description: Dowiedz się, jak zintegrować informacje o oknie narzędzia w programie Visual Studio z nową stroną opcji i nowym ustawieniem na stronie właściwości.
ms.date: 11/04/2016
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2586618b16afa8f8bfd6b7aa529486adf1d9ce41
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938138"
---
# <a name="extend-the-properties-task-list-output-and-options-windows"></a>Rozwiń okna właściwości, Lista zadań, dane wyjściowe i opcje
Możesz uzyskać dostęp do dowolnego okna narzędzi w programie Visual Studio. W tym instruktażu pokazano, jak zintegrować informacje o oknie narzędzia z nową stroną **opcji** oraz nowe ustawienie na stronie **Właściwości** , a także jak zapisywać w oknach **Lista zadań** i **wyjściowych** .

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-tool-window"></a>Tworzenie rozszerzenia za pomocą okna narzędziowego

1. Utwórz projekt o nazwie **todolist** przy użyciu szablonu VSIX i Dodaj szablon elementu niestandardowego okna narzędzi o nazwie **TodoWindow**.

    > [!NOTE]
    > Aby uzyskać więcej informacji na temat tworzenia rozszerzenia za pomocą okna narzędzi, zobacz [Tworzenie rozszerzenia przy użyciu okna narzędzi](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="set-up-the-tool-window"></a>Skonfiguruj okno narzędzi
 Dodaj pole tekstowe, w którym ma zostać wpisane nowe zadanie do wykonania, przycisk umożliwiający dodanie nowego elementu do listy, a pole listy, aby wyświetlić elementy na liście.

1. W *TodoWindow. XAML* Usuń kontrolki Button, TextBox i StackPanel z obiektu UserControl.

    > [!NOTE]
    > Nie spowoduje to usunięcia programu obsługi zdarzeń **Button1_Click** , którego użyjesz ponownie w późniejszym kroku.

2. Z sekcji **wszystkie kontrolki WPF** w **przyborniku** przeciągnij kontrolkę **kanwy** do siatki.

3. Przeciągnij **pole tekstowe**, **przycisk** i element **ListBox** do kanwy. Rozmieść elementy w taki sposób, aby pole tekstowe i przycisk były na tym samym poziomie, a pole listy wypełnia resztę poniższego okna, jak na poniższej ilustracji.

     ![Zakończono okno narzędzia](../extensibility/media/t5-toolwindow.png "T5-ToolWindow")

4. W okienku XAML Znajdź przycisk i ustaw jego właściwość content na **Dodaj**. Połącz ponownie program obsługi zdarzeń przycisku z kontrolką przycisku przez dodanie `Click="button1_Click"` atrybutu. Blok kanwy powinien wyglądać następująco:

    ```xml
    <Canvas HorizontalAlignment="Left" Width="306">
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>
    </Canvas>
    ```

### <a name="customize-the-constructor"></a>Dostosowywanie konstruktora

1. W pliku *TodoWindowControl.XAML.cs* Dodaj następującą dyrektywę using:

    ```csharp
    using System;
    ```

2. Dodaj odwołanie publiczne do TodoWindow i Utwórz w konstruktorze TodoWindowControl parametr TodoWindow. Kod powinien wyglądać następująco:

    ```csharp
    public TodoWindow parent;

    public TodoWindowControl(TodoWindow window)
    {
        InitializeComponent();
        parent = window;
    }
    ```

3. W *TodoWindow.cs* Zmień konstruktora TodoWindowControl, tak aby zawierał parametr TodoWindow. Kod powinien wyglądać następująco:

    ```csharp
    public TodoWindow() : base(null)
    {
        this.Caption = "TodoWindow";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;

         this.Content = new TodoWindowControl(this);
    }
    ```

## <a name="create-an-options-page"></a>Utwórz stronę opcji
 Możesz podać stronę w oknie dialogowym **Opcje** , aby użytkownicy mogli zmieniać ustawienia okna narzędzi. Tworzenie strony opcji wymaga zarówno klasy opisującej opcje, jak i wpisu w pliku *TodoListPackage.cs* lub *TodoListPackage. vb* .

1. Dodaj klasę o nazwie `ToolsOptions.cs` . `ToolsOptions`Dziedzicz z klasy <xref:Microsoft.VisualStudio.Shell.DialogPage> .

   ```csharp
   class ToolsOptions : DialogPage
   {
   }
   ```

2. Dodaj następującą dyrektywę using:

   ```csharp
   using Microsoft.VisualStudio.Shell;
   ```

3. Strona Opcje w tym instruktażu zawiera tylko jedną opcję o nazwie DaysAhead. Dodaj prywatne pole o nazwie **daysAhead** i właściwości o nazwie **daysAhead** do `ToolsOptions` klasy:

   ```csharp
   private double daysAhead;

   public double DaysAhead
   {
       get { return daysAhead; }
       set { daysAhead = value; }
   }
   ```

   Teraz musisz pamiętać, aby projekt był świadomy tej strony opcji.

### <a name="make-the-options-page-available-to-users"></a>Udostępnienie strony opcji użytkownikom

1. W *TodoWindowPackage.cs* Dodaj <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> do `TodoWindowPackage` klasy:

    ```csharp
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]
    ```

2. Pierwszym parametrem konstruktora ProvideOptionPage jest typ klasy `ToolsOptions` , która została utworzona wcześniej. Drugi parametr "do zrobienia" jest nazwą kategorii w oknie dialogowym **Opcje** . Trzeci parametr "ogólny" jest nazwą podkategorii okna dialogowego **Opcje** , w którym strona Opcje będzie dostępna. Następne dwa parametry to identyfikatory zasobów dla ciągów; Pierwsza to nazwa kategorii, a druga to nazwa podkategorii. Końcowy parametr określa, czy można uzyskać dostęp do tej strony przy użyciu automatyzacji.

     Po otwarciu strony opcji użytkownik powinien wyglądać podobnie do poniższej ilustracji.

     ![Strona opcji](../extensibility/media/t5optionspage.gif "T5OptionsPage")

     Zwróć uwagę o kategorię do **zrobienia** i podkategorii **Ogólne**.

## <a name="make-data-available-to-the-properties-window"></a>Udostępnianie danych okno Właściwości
 Aby uzyskać dostęp do informacji o liście zadań do wykonania, można utworzyć klasę o nazwie `TodoItem` , która przechowuje informacje o poszczególnych elementach listy zadań do zrobienia.

1. Dodaj klasę o nazwie `TodoItem.cs` .

     Gdy okno narzędzi jest dostępne dla użytkowników, elementy na liście rozwijanej będą reprezentowane przez TodoItems. Gdy użytkownik wybierze jeden z tych elementów w polu listy, w oknie **Właściwości** zostaną wyświetlone informacje o elemencie.

     Aby zapewnić dostęp do danych w oknie **Właściwości** , należy przekształcić dane w właściwości publiczne, które mają dwa atrybuty specjalne `Description` i `Category` . `Description` to tekst wyświetlany w dolnej części okna **Właściwości** . `Category` Określa, gdzie ma być wyświetlana właściwość, gdy okno **Właściwości** jest wyświetlane w widoku z **kategoryzacją** . Na poniższej ilustracji okno **Właściwości** jest w widoku z **kategoryzacją** , właściwość **Nazwa** w kategorii **pola do zrobienia** jest zaznaczone, a opis właściwości **Nazwa** jest wyświetlany u dołu okna.

     ![Okno właściwości](../extensibility/media/t5properties.png "T5Properties")

2. Dodaj następujące dyrektywy using w pliku *TodoItem.cs* .

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

     Dodaj dwie właściwości `Name` i `DueDate` . Wykonamy te czynności `UpdateList()` i `CheckForErrors()` później.

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

4. Dodaj odwołanie prywatne do kontrolki użytkownika. Dodaj konstruktora, który przyjmuje kontrolkę użytkownika i nazwę tego elementu do wykonania. Aby znaleźć wartość dla `daysAhead` , pobiera właściwość strony opcji.

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

5. Ponieważ wystąpienia `TodoItem` klasy będą przechowywane w polu listy, a element ListBox wywoła `ToString` funkcję, należy przeciążyć `ToString` funkcję. Dodaj następujący kod do *TodoItem.cs*, po konstruktorze i przed końcem klasy.

    ```csharp
    public override string ToString()
    {
        return name + " Due: " + dueDate.ToShortDateString();
    }
    ```

6. W *TodoWindowControl.XAML.cs* Dodaj metody zastępcze do `TodoWindowControl` klasy dla `CheckForError` `UpdateList` metod i. Umieść je po ProcessDialogChar i przed końcem pliku.

    ```csharp
    public void CheckForErrors()
    {
    }
    public void UpdateList(TodoItem item)
    {
    }
    ```

     `CheckForError`Metoda wywoła metodę, która ma taką samą nazwę w obiekcie nadrzędnym, i ta metoda sprawdzi, czy wystąpiły jakieś błędy i prawidłowo obsłużą je. `UpdateList`Metoda zaktualizuje element ListBox w kontrolce nadrzędnej; Metoda jest wywoływana, gdy `Name` `DueDate` właściwości i w tej klasie zmienią się. Zostaną one zaimplementowane później.

## <a name="integrate-into-the-properties-window"></a>Integruj z okno Właściwości
 Teraz napisz kod zarządzający polem listy, który zostanie powiązany z oknem **Właściwości** .

 Należy zmienić przycisk procedury obsługi, aby odczytać pole tekstowe, utworzyć TodoItem i dodać go do listy.

1. Zamień istniejącą `button1_Click` funkcję na kod, który tworzy nowy TodoItem i dodaje go do elementu ListBox. Wywołuje `TrackSelection()` , który zostanie zdefiniowany w dalszej części.

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

2. W widok Projekt wybierz formant ListBox. W oknie **Właściwości** kliknij przycisk **programy obsługi zdarzeń** i Znajdź zdarzenie **SelectionChanged** . Wypełnij pole tekstowe **listBox_SelectionChanged**. Spowoduje to dodanie elementu zastępczego dla programu obsługi SelectionChanged i przypisanie go do zdarzenia.

3. Zaimplementuj `TrackSelection()` metodę. Ponieważ trzeba będzie uzyskać <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> dostęp do usług, należy udostępnić <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> TodoWindowControl. Dodaj następującą metodę do klasy `TodoWindow`:

    ```
    internal object GetVsService(Type service)
    {
        return GetService(service);
    }
    ```

4. Dodaj następujące dyrektywy using do *TodoWindowControl.XAML.cs*:

    ```csharp
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Shell.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    ```

5. Wypełnij procedurę obsługi SelectionChanged w następujący sposób:

    ```
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)
    {
        TrackSelection();
    }
    ```

6. Teraz Wypełnij funkcję TrackSelection, która zapewni integrację z oknem **Właściwości** . Ta funkcja jest wywoływana, gdy użytkownik dodaje element do elementu ListBox lub klika element w polu listy. Dodaje zawartość ListBox do SelectionContainer i przekazuje SelectionContainer do  <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> procedury obsługi zdarzeń okna właściwości. Usługa TrackSelection śledzi wybrane obiekty w interfejsie użytkownika (UI) i wyświetla ich właściwości

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

     Teraz, gdy masz klasę, której może użyć okno **Właściwości** , możesz zintegrować okno **Właściwości** z oknem narzędzia. Gdy użytkownik kliknie element na liście w oknie narzędzia, należy odpowiednio zaktualizować okno **Właściwości** . Podobnie, gdy użytkownik zmienia element do wykonania w oknie **Właściwości** , skojarzony element powinien zostać zaktualizowany.

7. Teraz Dodaj resztę kodu funkcji UpdateList w *TodoWindowControl.XAML.cs*. Powinien on porzucić i dodać ponowną modyfikację TodoItem z listy kontrolnej.

    ```csharp
    public void UpdateList(TodoItem item)
    {
        var index = listBox.SelectedIndex;
        listBox.Items.RemoveAt(index);
        listBox.Items.Insert(index, item);
        listBox.SelectedItem = index;
    }
    ```

8. Przetestuj swój kod. Skompiluj projekt i Rozpocznij debugowanie. Powinno zostać wyświetlone wystąpienie eksperymentalne.

9. Otwórz stronę   >  **Opcje** narzędzi. Kategoria zadań do wykonania powinna zostać wyświetlona w okienku po lewej stronie. Kategorie są wyświetlane w kolejności alfabetycznej, dlatego w obszarze TS.

10. Na stronie **Opcje do** wykonania powinna zostać wyświetlona `DaysAhead` Właściwość o wartości **0**. Zmień ją na **2**.

11. W **widoku/innym menu systemu Windows** Otwórz **TodoWindow**. W polu tekstowym wpisz **EndDate** , a następnie kliknij przycisk **Dodaj**.

12. W polu listy powinna zostać wyświetlona data dwie dni późniejsze od dzisiaj.

## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Dodaj tekst do okna danych wyjściowych i elementów do Lista zadań
 Dla **Lista zadań** można utworzyć nowy obiekt typu zadanie, a następnie dodać ten obiekt zadania do **Lista zadań** , wywołując jego `Add` metodę. Aby zapisać w oknie **danych wyjściowych** , należy wywołać `GetPane` metodę w celu uzyskania obiektu okienka, a następnie wywołać `OutputString` metodę obiektu okienka.

1. W *TodoWindowControl.XAML.cs*, w `button1_Click` metodzie, Dodaj kod w celu uzyskania okienka **Ogólne** okna **danych wyjściowych** (czyli domyślnego) i Zapisz w nim. Metoda powinna teraz wyglądać następująco:

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

2. Aby można było dodać elementy do Lista zadań, należy dodać klasę zagnieżdżoną do klasy TodoWindowControl. Klasa zagnieżdżona musi pochodzić od <xref:Microsoft.VisualStudio.Shell.TaskProvider> . Dodaj następujący kod na końcu `TodoWindowControl` klasy.

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

3. Następnie Dodaj odwołanie prywatne do `TodoTaskProvider` i `CreateProvider()` metodę do `TodoWindowControl` klasy. Kod powinien wyglądać następująco:

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

4. Dodaj `ClearError()` , który czyści Lista zadań i `ReportError()` , który dodaje wpis do lista zadań, do `TodoWindowControl` klasy.

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

5. Teraz Zaimplementuj `CheckForErrors` metodę w następujący sposób.

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

1. Skompiluj projekt i Rozpocznij debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne.

2. Otwórz **TodoWindow** (**Wyświetl**  >  **inne systemy Windows**  >  **TodoWindow**).

3. Wpisz coś w polu tekstowym, a następnie kliknij przycisk **Dodaj**.

     Data ukończenia przypada 2 dni po dniu dzisiejszym zostanie dodana do pola listy. Nie Wygenerowano żadnych błędów, a **Lista zadań** (**Widok**  >  **Lista zadań**) nie powinien zawierać żadnych wpisów.

4. Teraz zmień ustawienie na stronie opcje **narzędzi** do  >    >  **zrobienia** z **2** z powrotem na **0**.

5. Wpisz coś innego w **TodoWindow** , a następnie ponownie kliknij przycisk **Dodaj** . Powoduje to wyzwolenie błędu, a także wpis w **Lista zadań**.

     Podczas dodawania elementów początkowa data jest ustawiana na teraz plus 2 dni.

6. W menu **Widok** kliknij pozycję **dane wyjściowe** , aby otworzyć okno **dane wyjściowe** .

     Zwróć uwagę, że za każdym razem, gdy dodasz element, w okienku **Lista zadań** zostanie wyświetlony komunikat.

7. Kliknij jeden z elementów na liście.

     Okno **Właściwości** wyświetla dwie właściwości dla elementu.

8. Zmień jedną z właściwości, a następnie naciśnij klawisz **Enter**.

     Element zostanie zaktualizowany na liście rozwijanej.
