---
title: 'Przewodnik: Tworzenie aplikacji klasycznej WPF połączonej z usługą Azure Mobile | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 8d42620f-553b-4b04-a38b-f6b306d73a50
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 624fffb9c86a7ad874f27797dfd5251c8585870f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664027"
---
# <a name="walkthrough-create-a-wpf-desktop-application-connected-to-an-azure-mobile-service"></a>Przewodnik: Tworzenie aplikacji klasycznej WPF połączonej z usługą mobilną platformy Azure
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą Windows Presentation Foundation (WPF) można szybko utworzyć nowoczesne aplikacje klasyczne, które używają usługi mobilnej platformy Azure do przechowywania i dostarczania danych.

## <a name="Requirements"></a> Wymagania wstępne
 Aby ukończyć ten przewodnik, musisz wykonać następujące czynności:

- Visual Studio 2015 — dowolna wersja, która obsługuje programowanie WPF.

- Aktywne konto Microsoft Azure.

  - W [tym miejscu](https://azure.microsoft.com/pricing/free-trial/)możesz utworzyć konto bezpłatnej wersji próbnej.

  - Możesz aktywować [korzyści dla subskrybentów MSDN](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/?WT.mc_id=A261C142F). Subskrypcja MSDN daje środki na korzystanie z płatnych usług platformy Azure.

## <a name="create-a-project-and-add-references"></a>Utwórz projekt i Dodaj odwołania
 Pierwszym krokiem jest utworzenie projektu WPF i dodanie pakietu NuGet, który umożliwia nawiązywanie połączenia z usługą Azure Mobile Services.

#### <a name="to-create-the-project"></a>Aby utworzyć projekt

1. Na pasku menu wybierz **plik**, **Nowy**, **projekt**.

2. W oknie dialogowym **Nowy projekt** rozwiń węzeł  **C# Wizualizacja** lub **Visual Basic** i wybierz węzeł **systemu Windows** , a następnie rozwiń węzeł **Windows** i wybierz węzeł **klasyczny pulpit** .

3. Z listy szablon wybierz szablon **Aplikacja WPF** .

4. W polu tekstowym **Nazwa** wprowadź `WPFQuickStart`, a następnie wybierz przycisk **OK** .

     Projekt zostanie utworzony, a pliki projektu zostaną dodane do **Eksplorator rozwiązań**i zostanie wyświetlony Projektant domyślnego okna aplikacji o nazwie **MainWindow. XAML** .

#### <a name="to-add-a-reference-to-the-windows-azure-mobile-services-sdk"></a>Aby dodać odwołanie do zestawu Windows Azure Mobile Services SDK

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła **odwołania** i wybierz polecenie **Zarządzaj pakietami NuGet**.

2. W **Menedżerze pakietów NuGet**wybierz pole **wyszukiwania** i wprowadź `mobileservices`.

3. W lewym okienku wybierz **windowsazure. MobileServices**, a następnie w okienku po prawej stronie wybierz przycisk **Instaluj** .

    > [!NOTE]
    > Jeśli zostanie wyświetlone okno dialogowe **Podgląd** , Przejrzyj proponowane zmiany, a następnie wybierz przycisk **OK** .

4. W oknie dialogowym **Akceptacja licencji** Przejrzyj postanowienia licencyjne, a następnie zaakceptuj je, wybierając przycisk **Akceptuję** .

     Niezbędne odwołania zostaną dodane do **Eksplorator rozwiązań**.

    > [!NOTE]
    > Jeśli nie akceptujesz postanowień licencyjnych, wybierz przycisk **Odrzuć** . Nie będzie można ukończyć pozostałej części przewodnika.

## <a name="create-the-user-interface"></a>Tworzenie interfejsu użytkownika
 Następnym krokiem jest utworzenie interfejsu użytkownika dla aplikacji. Najpierw utworzysz kontrolkę użytkownika wielokrotnego użytku, która wyświetla standardowy układ obu okien. Dodasz kontrolkę użytkownika do głównego okna aplikacji i dodasz kontrolki do wprowadzania i wyświetlania danych, a następnie napiszesz kod w celu zdefiniowania interakcji z zapleczem usługi mobilnej.

#### <a name="to-add-a-user-control"></a>Aby dodać kontrolkę użytkownika

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła **WPFQuickStart** , a następnie wybierz **Dodaj**, **Nowy folder**.

2. Nazwij folder `Common`.

3. Otwórz menu skrótów dla **wspólnego** folderu i wybierz polecenie **Dodaj**, **kontrolkę użytkownika**.

4. W oknie dialogowym **Dodaj nowy element** wybierz pole Nazwa i wprowadź `QuickStartTask`, a następnie wybierz przycisk **Dodaj** .

     Kontrolka użytkownika zostanie dodana do projektu, a plik **QuickStartTask. XAML** zostanie otwarty w projektancie.

5. W dolnym okienku projektanta wybierz Tagi `<Grid>` i `</Grid>` i zastąp je następującym kodem XAML:

    ```xaml
    <Grid VerticalAlignment="Top">
            <StackPanel Orientation="Horizontal">
                <Border BorderThickness="0,0,1,0" BorderBrush="DarkGray" Margin="0,10" MinWidth="70">
                    <TextBlock Text="{Binding Number}" FontSize="45" Foreground="DarkGray" Margin="20,0"/>
                </Border>
                <StackPanel>
                    <TextBlock Text="{Binding Title}" Margin="10,10,0,0" FontSize="16" FontWeight="Bold" />
                    <TextBlock Text="{Binding Description}" Margin="10,0,0,0" TextWrapping="Wrap" MaxWidth="500" />
                </StackPanel>
            </StackPanel>
        </Grid>
    ```

     Ten kod XAML tworzy układ wielokrotnego użytku z symbolami zastępczymi dla pól Number, title i Description. W czasie wykonywania symbole zastępcze mogą zostać zastąpione tekstem, jak pokazano na poniższej ilustracji.

     ![Kontrolka użytkownika QuickStartTask](../designers/media/wpfquickstart1.PNG "WPFQuickStart1")

6. W **Eksplorator rozwiązań**rozwiń węzeł **QuickStartTask. XAML** i Otwórz plik **QuickStartTask.XAML.cs** lub **QuickStartTask. XAML. vb** .

7. W edytorze kodu Zastąp przestrzeń nazw `namespace WPFQuickStart.Common` (C#) lub `Public Class QuickStartTask` (VB) przy użyciu następującego kodu:

    ```csharp
    namespace WPFQuickStart.Common
    {
        /// <summary>
        /// Interaction logic for QuickStartTask.xaml
        /// </summary>
        public partial class QuickStartTask : UserControl
        {
            public QuickStartTask()
            {
                this.InitializeComponent();
                this.DataContext = this;
            }

            public int Number
            {
                get { return (int)GetValue(NumberProperty); }
                set { SetValue(NumberProperty, value); }
            }

            // Using a DependencyProperty as the backing store for Number.  This enables animation, styling, binding, etc...
            public static readonly DependencyProperty NumberProperty =
                DependencyProperty.Register("Number", typeof(int), typeof(QuickStartTask), new PropertyMetadata(0));

            public string Title
            {
                get { return (string)GetValue(TitleProperty); }
                set { SetValue(TitleProperty, value); }
            }

            // Using a DependencyProperty as the backing store for Title.  This enables animation, styling, binding, etc...
            public static readonly DependencyProperty TitleProperty =
                DependencyProperty.Register("Title", typeof(string), typeof(QuickStartTask), new PropertyMetadata(default(string)));

            public string Description
            {
                get { return (string)GetValue(DescriptionProperty); }
                set { SetValue(DescriptionProperty, value); }
            }

            // Using a DependencyProperty as the backing store for Description.  This enables animation, styling, binding, etc...
            public static readonly DependencyProperty DescriptionProperty =
                DependencyProperty.Register("Description", typeof(string), typeof(QuickStartTask), new PropertyMetadata(default(string)));
        }
    }
    ```

    ```vb
    Partial Public Class QuickStartTask
            Inherits UserControl

            Public Sub New()
                Me.InitializeComponent()
                Me.DataContext = Me
            End Sub

            Public Property Number() As Integer
                Get
                    Return CInt(Fix(GetValue(NumberProperty)))
                End Get
                Set(ByVal value As Integer)
                    SetValue(NumberProperty, value)
                End Set
            End Property

            ' Using a DependencyProperty as the backing store for Number.  This enables animation, styling, binding, etc...
            Public Shared ReadOnly NumberProperty As DependencyProperty = DependencyProperty.Register("Number", GetType(Integer), GetType(QuickStartTask), New PropertyMetadata(0))

            Public Property Title() As String
                Get
                    Return CStr(GetValue(TitleProperty))
                End Get
                Set(ByVal value As String)
                    SetValue(TitleProperty, value)
                End Set
            End Property

            ' Using a DependencyProperty as the backing store for Title.  This enables animation, styling, binding, etc...
            Public Shared ReadOnly TitleProperty As DependencyProperty = DependencyProperty.Register("Title", GetType(String), GetType(QuickStartTask), New PropertyMetadata(Nothing))

            Public Property Description() As String
                Get
                    Return CStr(GetValue(DescriptionProperty))
                End Get
                Set(ByVal value As String)
                    SetValue(DescriptionProperty, value)
                End Set
            End Property

            ' Using a DependencyProperty as the backing store for Description.  This enables animation, styling, binding, etc...
            Public Shared ReadOnly DescriptionProperty As DependencyProperty = DependencyProperty.Register("Description", GetType(String), GetType(QuickStartTask), New PropertyMetadata(Nothing))
        End Class
    ```

     Ten kod używa właściwości zależności do ustawiania wartości dla pól Liczba, tytuł i opis w czasie wykonywania.

8. Na pasku menu wybierz **kompilacja**, **Kompiluj WPFQuickStart** , aby skompilować kontrolkę użytkownika.

#### <a name="to-create-and-modify-the-main-window"></a>Aby utworzyć i zmodyfikować okno główne

1. W **Eksplorator rozwiązań**Otwórz plik **MainWindow. XAML** .

2. **Ważne**. Ten krok dotyczy tylko C# programu. Jeśli używasz Visual Basic, przejdź do następnego kroku. W dolnym okienku projektanta Znajdź wiersz `xmlns:local=”clr-namespace:WPFQuickStart”` i zastąp go następującym kodem XAML:

    ```xaml
    xmlns:local=”clr-namespace:WPFQuickStart.Common”
    ```

3. W oknie **Właściwości** rozwiń węzeł **wspólnych** kategorii i wybierz właściwość **Title** , a następnie wprowadź `WPF Todo List` i naciśnij klawisz **Enter** .

     Zwróć uwagę, że element **title** w oknie XAML zmienia się w taki sposób, aby odpowiadał nowej wartości. Właściwości XAML można modyfikować w oknie XAML lub w oknie **Właściwości** , a zmiany są synchronizowane.

4. W oknie XAML ustaw wartość elementu **Height** na `768` i ustaw wartość właściwości **Width** na `1280`.

     Te elementy odpowiadają właściwościom **wysokości** i **szerokości** , które znajdują się w kategorii **Układ** w oknie **Właściwości** .

5. Wybierz Tagi `<Grid>` i `</Grid>` i zastąp je następującym kodem XAML:

    ```xaml
    <Grid>

            <Grid Margin="50,50,10,10">
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="*" />
                    <ColumnDefinition Width="*" />
                </Grid.ColumnDefinitions>
                <Grid.RowDefinitions>
                    <RowDefinition Height="Auto" />
                    <RowDefinition Height="*" />
                </Grid.RowDefinitions>

                <Grid Grid.Row="0" Grid.ColumnSpan="2" Margin="0,0,0,20">
                    <StackPanel>
                        <TextBlock Foreground="#0094ff" FontFamily="Segoe UI Light" Margin="0,0,0,6">MICROSOFT AZURE MOBILE SERVICES</TextBlock>
                        <TextBlock Foreground="Gray" FontFamily="Segoe UI Light" FontSize="45" ><Run Text="My Todo List"/></TextBlock>
                    </StackPanel>
                </Grid>

                <Grid Grid.Row="1">
                    <StackPanel>

                        <local:QuickStartTask Number="1" Title="Insert a TodoItem" Description="Enter some text below and click Save to insert a new todo item into the list." />

                        <StackPanel Orientation="Horizontal" Margin="72,0,0,0">
                            <TextBox x:Name="TodoInput" Margin="5" MinWidth="300"/>
                            <Button x:Name="ButtonSave" Click="ButtonSave_Click" Content="Save"/>
                        </StackPanel>

                    </StackPanel>
                </Grid>

                <Grid Grid.Row="1" Grid.Column="1">
                    <Grid.RowDefinitions>
                        <RowDefinition Height="Auto" />
                        <RowDefinition />
                    </Grid.RowDefinitions>
                    <StackPanel>
                        <local:QuickStartTask Number="2" Title="Query and Update Data" Description="Click the Refresh button to load the unfinished TodoItems from the Azure Mobile Service. Select the checkbox to mark a ToDo item as complete and update the list." />
                        <Button Margin="72,0,0,0" Name="ButtonRefresh" Click="ButtonRefresh_Click">Refresh</Button>
                    </StackPanel>

                    <ListView Name="ListItems" Margin="62,10,0,0" Grid.Row="1">
                        <ListView.ItemTemplate>
                            <DataTemplate>
                                <StackPanel Orientation="Horizontal">
                                    <CheckBox Name="CheckBoxComplete" IsChecked="{Binding Complete, Mode=TwoWay}" Checked="CheckBoxComplete_Checked" Content="{Binding Text}" Margin="10,5" VerticalAlignment="Center"/>
                                </StackPanel>
                            </DataTemplate>
                        </ListView.ItemTemplate>
                    </ListView>

                </Grid>

            </Grid>
        </Grid>
    ```

     Zauważ, że zmiany zostaną odzwierciedlone w oknie projektowania. Po ponownym uruchomieniu można także zdefiniować interfejs użytkownika, dodając formanty z okna **przybornika** i ustawiając właściwości w oknie **Właściwości** . Wszystkie elementy, które mogą być wykonywane w projektancie, można wykonać w kodzie XAML i na odwrót.

     W tym momencie projekt powinien wyglądać jak na poniższej ilustracji.

     ![MainWindow w projektancie](../designers/media/wpfquickstart2.PNG "WPFQuickStart2")

    > [!NOTE]
    > Podczas wykonywania kolejnych kilku procedur mogą pojawić się błędy w **Lista błędów** , jeśli jest otwarte. Nie martw się; te błędy zostaną odrzucone po zakończeniu pozostałych procedur.

6. W **Eksplorator rozwiązań**rozwiń węzeł **MainWindow. XAML** i Otwórz plik **MainWindow.XAML.cs** lub **MainWindow. XAML. vb** .

7. W edytorze kodu Dodaj następujące dyrektywy `using` lub `Imports` na początku pliku:

    ```csharp
    using Microsoft.WindowsAzure.MobileServices;
    using Newtonsoft.Json;
    ```

    ```vb
    Imports Microsoft.WindowsAzure.MobileServices
    Imports Newtonsoft.Json
    ```

8. Zastąp cały kod w przestrzeni nazw **WPFQuickStart** (C#) lub klasy **MainWindow** Class (VB) następującym kodem:

    ```csharp
    namespace WPFQuickStart
    {
        /// <summary>
        /// Interaction logic for MainWindow.xaml
        /// </summary>
        public class TodoItem
        {
            public string Id { get; set; }

            [JsonProperty(PropertyName = "text")]
            public string Text { get; set; }

            [JsonProperty(PropertyName = "complete")]
            public bool Complete { get; set; }
        }

        public partial class MainWindow : Window
        {
            private MobileServiceCollection<TodoItem, TodoItem> items;
            private IMobileServiceTable<TodoItem> todoTable = App.MobileService.GetTable<TodoItem>();

            public MainWindow()
            {
                InitializeComponent();
            }

            private async void InsertTodoItem(TodoItem todoItem)
            {
                // This code inserts a new TodoItem into the database. When the operation completes
                // and Mobile Services has assigned an Id, the item is added to the CollectionView
                await todoTable.InsertAsync(todoItem);
                items.Add(todoItem);
            }

            private async void RefreshTodoItems()
            {
                try
                {
                    // This code refreshes the entries in the list view by querying the TodoItem table.
                    // The query excludes completed TodoItems
                    items = await todoTable
                        .Where(todoItem => todoItem.Complete == false)
                        .ToCollectionAsync();
                    ListItems.ItemsSource = items;
                }
                catch (MobileServiceInvalidOperationException e)
                {
                    MessageBox.Show(e.Message, "Error loading items");
                }
            }

            private async void UpdateCheckedTodoItem(TodoItem item)
            {
                // This code takes a freshly completed TodoItem and updates the database. When the MobileService
                // responds, the item is removed from the list
                await todoTable.UpdateAsync(item);
                items.Remove(item);
            }

            private void ButtonRefresh_Click(object sender, RoutedEventArgs e)
            {
                RefreshTodoItems();
            }

            private void ButtonSave_Click(object sender, RoutedEventArgs e)
            {
                var todoItem = new TodoItem { Text = TodoInput.Text };
                InsertTodoItem(todoItem);
                TodoInput.Text = "";
            }

            private void CheckBoxComplete_Checked(object sender, RoutedEventArgs e)
            {
                CheckBox cb = (CheckBox)sender;
                TodoItem item = cb.DataContext as TodoItem;
                UpdateCheckedTodoItem(item);
            }

            protected override void OnActivated(EventArgs e)
            {
                RefreshTodoItems();
            }
        }

    }
    ```

    ```vb
    Public Class TodoItem
        Public Property Id() As String

        <JsonProperty(PropertyName:="text")>
        Public Property Text() As String

        <JsonProperty(PropertyName:="complete")>
        Public Property Complete() As Boolean
    End Class

    Partial Public Class MainWindow
        Inherits Window

        Private items As MobileServiceCollection(Of TodoItem, TodoItem)
        Private todoTable As IMobileServiceTable(Of TodoItem) = Application.MobileService.GetTable(Of TodoItem)()

        Public Sub New()
            InitializeComponent()
        End Sub

        Private Async Sub InsertTodoItem(ByVal todoItem As TodoItem)
            ' This code inserts a new TodoItem into the database. When the operation completes
            ' and Mobile Services has assigned an Id, the item is added to the CollectionView
            Await todoTable.InsertAsync(todoItem)
            items.Add(todoItem)
        End Sub

        Private Async Sub RefreshTodoItems()
            Dim exception As MobileServiceInvalidOperationException = Nothing
            Try
                ' This code refreshes the entries in the list view by querying the TodoItem table.
                ' The query excludes completed TodoItems
                items = Await todoTable.Where(Function(todoItem) todoItem.Complete = False).ToCollectionAsync()
            Catch e As MobileServiceInvalidOperationException
                exception = e
            End Try

            If exception IsNot Nothing Then
                MessageBox.Show(exception.Message, "Error loading items")
            Else
                ListItems.ItemsSource = items
            End If
        End Sub

        Private Async Sub UpdateCheckedTodoItem(ByVal item As TodoItem)
            ' This code takes a freshly completed TodoItem and updates the database. When the MobileService
            ' responds, the item is removed from the list
            Await todoTable.UpdateAsync(item)
            items.Remove(item)
        End Sub

        Private Sub ButtonRefresh_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)
            RefreshTodoItems()
        End Sub

        Private Sub ButtonSave_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)
            Dim todoItem = New TodoItem With {.Text = TodoInput.Text}
            InsertTodoItem(todoItem)
            TodoInput.Text = ""
        End Sub

        Private Sub CheckBoxComplete_Checked(ByVal sender As Object, ByVal e As RoutedEventArgs)
            Dim cb As CheckBox = DirectCast(sender, CheckBox)
            Dim item As TodoItem = TryCast(cb.DataContext, TodoItem)
            UpdateCheckedTodoItem(item)
        End Sub

        Protected Overrides Sub OnActivated(ByVal e As EventArgs)
            RefreshTodoItems()
        End Sub
    End Class
    ```

     Ten kod definiuje interakcję między interfejsem użytkownika i bazą danych w usłudze mobilnej przy użyciu metod asynchronicznych.

## <a name="create-the-azure-mobile-service"></a>Tworzenie usługi mobilnej Azure
 Ostatnim krokiem jest utworzenie usługi mobilnej w Microsoft Azure, dodanie tabeli w celu przechowania danych, a następnie odwołanie się do wystąpienia usługi z aplikacji.

#### <a name="to-create-a-mobile-service"></a>Aby utworzyć usługę mobilną

1. Otwórz przeglądarkę internetową i zaloguj się do Microsoft Azure Portal, a następnie wybierz kartę **Mobile Services** .

2. Wybierz przycisk **Nowy** , a następnie w oknie dialogowym wybierz pozycję **obliczenia**, **Usługa mobilna, Utwórz**.

3. W oknie dialogowym **Nowa usługa mobilna** wybierz pole tekstowe **adres URL** i wprowadź `wpfquickstart01`.

    > [!NOTE]
    > Może zajść potrzeba zmiany numerycznej części adresu URL. Microsoft Azure wymaga unikatowego adresu URL dla każdej usługi mobilnej.

     Spowoduje to ustawienie adresu URL usługi do `https://wpfquickstart01.azure-mobile.net/`.

4. Na liście **baza danych** wybierz opcję bazy danych. Ponieważ jest to aplikacja, która prawdopodobnie nie będzie mogła uzyskać dużo użycia, możesz chcieć wybrać opcję **Utwórz bezpłatną baza bazę danych SQL** lub wybrać bezpłatną bazę danych, która jest już skojarzona z subskrypcją.

5. Na liście **region** wybierz centrum danych, w którym chcesz wdrożyć usługę mobilną, a następnie wybierz przycisk **dalej** (Strzałka w prawo).

    > [!NOTE]
    > Dla tej usługi będziesz używać domyślnego ustawienia **zaplecza** , **JavaScript**.

6. W przypadku tworzenia nowej bazy danych na stronie **Określanie ustawień bazy danych** na liście **serwer** wybierz pozycję **nowy serwer bazy danych SQL**, wprowadź **nazwę logowania SQL** i **hasło**, a następnie wybierz przycisk **Zakończ** (znacznik wyboru przycisk.

7. W przypadku wybrania istniejącej bazy danych na stronie **Ustawienia bazy danych** wprowadź **hasło logowania** , a następnie wybierz przycisk **Ukończ** (znacznik wyboru).

     Zostanie rozpoczęty proces tworzenia usługi mobilnej. Po zakończeniu procesu stan zmieni się na **gotowe** i możesz przejść do następnego kroku.

8. W portalu wybierz nowo utworzoną usługę mobilną, a następnie wybierz przycisk **Zarządzaj kluczami** .

9. W oknie dialogowym **Zarządzanie kluczami dostępu** Skopiuj **klucz aplikacji**.

     Zostanie ona użyta w następnej procedurze.

#### <a name="to-create-a-table"></a>Aby utworzyć tabelę

1. W Microsoft Azure Portal wybierz strzałkę w prawo obok nazwy usługi mobilnej, a następnie na pasku menu wybierz pozycję **dane**, a następnie wybierz łącze **Dodaj tabelę** .

2. W oknie dialogowym **Utwórz nową tabelę** w polu tekstowym **nazwa tabeli** wprowadź `TodoItem`, a następnie wybierz przycisk **Ukończ** (znacznik wyboru).

     Zaczekaj na utworzenie tabeli, a następnie przejdź do ostatniej procedury.

#### <a name="to-add-a-declaration-for-the-mobile-service"></a>Aby dodać deklarację dla usługi mobilnej

1. Wróć do programu Visual Studio. W **Eksplorator rozwiązań**rozwiń węzeł **App. XAML** (C#) lub **Application. XAML** (Visual Basic) i Otwórz plik **App.XAML.cs** lub **App. XAML. vb** .

2. W edytorze kodu Dodaj następujące `using` lub **importuje** dyrektywy na początku pliku:

    ```csharp
    using Microsoft.WindowsAzure.MobileServices;
    ```

    ```vb
    Imports Microsoft.WindowsAzure.MobileServices
    ```

3. Dodaj następującą deklarację do klasy, zastępując wartość *-SERVICE_HERE* nazwą adresu URL usługi i zastępując *klucz* aplikacji, który został skopiowany w ramach poprzedniej procedury:

    ```csharp
    public static MobileServiceClient MobileService = new MobileServiceClient(
                 "https://YOUR-SERVICE-HERE.azure-mobile.net/",
                 "YOUR-KEY-HERE"
             );
    ```

    ```vb
    Public Shared MobileService As New MobileServiceClient("https://YOUR-SERVICE-HERE.azure-mobile.net/", "YOUR-KEY-HERE")
    ```

     Ten kod umożliwia aplikacji dostęp do usługi mobilnej działającej na Microsoft Azure.

## <a name="test-the-application"></a>Testowanie aplikacji
 To wszystko — utworzono aplikację klasyczną WPF, która uzyskuje dostęp do usługi mobilnej platformy Azure. Teraz wystarczy uruchomić aplikację i zobaczyć ją w działaniu.

#### <a name="to-run-the-application"></a>Aby uruchomić aplikację

1. Na pasku menu wybierz **Debuguj**, **Rozpocznij debugowanie** (lub naciśnij klawisz F5).

2. W polu tekstowym **Wstaw TodoItem** wprowadź `Do something`, a następnie wybierz przycisk **Zapisz** .

3. Wprowadź `Do something else`, a następnie ponownie wybierz przycisk **Zapisz** .

     Zwróć uwagę, że dwa wpisy są dodawane do listy **zapytanie i dane aktualizacji** , jak pokazano na poniższej ilustracji.

     ![Elementy do wykonania zostaną dodane do listy.](../designers/media/wpfquickstart3.PNG "WPFQuickStart3")

4. Zaznacz pole wyboru dla wpisu **Zrób coś innego** na liście.

     Powoduje to wywołanie metody **UpdateCheckedTodoItem** i usunięcie elementu z listy i bazy danych.

## <a name="next-steps"></a>Następne kroki
 Uproszczony przykładową aplikację klasyczną WPF z zapleczem platformy Azure. Oczywiście rzeczywista aplikacja może być znacznie bardziej złożona, ale te same podstawowe koncepcje mają zastosowanie. Zobacz [WPF w .NET Framework](https://msdn.microsoft.com/library/ms754130\(v=vs.100\).aspx).

 Można zwiększyć atrakcyjność interfejsu użytkownika przez dodanie kolorów, kształtów, grafiki, a nawet animacji. Zobacz [Designing XAML in Visual Studio i Blend for Visual Studio](../designers/designing-xaml-in-visual-studio.md).

 Możesz połączyć się z istniejącymi bazami danych SQL lub innymi źródłami danych przy użyciu usługi Azure Mobile Services. Zobacz [dokumentację Mobile Services](https://azure.microsoft.com/services/app-service/mobile/).

## <a name="see-also"></a>Zobacz też
 [Przewodnik: moja pierwsza aplikacja klasyczna WPF](../designers/walkthrough-my-first-wpf-desktop-application2.md) [tworzenie nowoczesnych aplikacji klasycznych za pomocą Windows Presentation Foundation](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md)
