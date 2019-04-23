---
title: 'Przewodnik: Tworzenie aplikacji WPF pulpitu podłączone do usługi mobilnej platformy Azure | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 8d42620f-553b-4b04-a38b-f6b306d73a50
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a4d4d6a8399d3d40eaefe86ed9cbb3105729f08a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60118022"
---
# <a name="walkthrough-create-a-wpf-desktop-application-connected-to-an-azure-mobile-service"></a>Przewodnik: Tworzenie aplikacji WPF pulpitu podłączone do usługi mobilnej Azure
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Presentation Foundation (WPF) umożliwia szybkie tworzenie nowoczesnych aplikacja komputerowa, która używa usług Azure Mobile do przechowywania i przekazywania danych.  
  
## <a name="Requirements"></a> Wymagania wstępne  
 Będą potrzebne następujące polecenie, aby ukończyć ten Instruktaż:  
  
- Visual Studio 2015 — dowolnej wersji, który obsługuje opracowywanie WPF.  
  
- Aktywne konto Microsoft Azure.  
  
    - Użytkownik może Załóż bezpłatne konto próbne [tutaj](http://azure.microsoft.com/pricing/free-trial/).  
  
    - Możesz aktywować [korzyści dla subskrybentów MSDN](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/?WT.mc_id=A261C142F). Subskrypcji sieci MSDN zapewnia środki na korzystanie z każdego miesiąca, używanego do płatne usługi platformy Azure.  
  
## <a name="create-a-project-and-add-references"></a>Tworzenie projektu i dodawanie odwołań  
 Pierwszym krokiem jest utworzenie projektu WPF i Dodaj pakiet NuGet, która umożliwia nawiązanie połączenia z usługą Azure Mobile Services.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
1. Na pasku menu wybierz **pliku**, **New**, **projektu**.  
  
2. W **nowy projekt** okna dialogowego, rozwiń węzeł **Visual C#** lub **języka Visual Basic** węzeł i wybierz polecenie **Windows** węzła, a następnie rozwiń węzeł **Windows** węzeł i wybierz polecenie **Classic Desktop** węzła.  
  
3. Na liście szablonów wybierz **aplikacji WPF** szablonu.  
  
4. W **nazwa** polu tekstowym wprowadź `WPFQuickStart`, a następnie wybierz **OK** przycisku.  
  
     Projekt zostanie utworzony i pliki projektu zostaną dodane do **Eksploratora rozwiązań**i Projektant dla domyślnego okna aplikacji o nazwie **MainWindow.xaml** jest wyświetlana.  
  
#### <a name="to-add-a-reference-to-the-windows-azure-mobile-services-sdk"></a>Aby dodać odwołanie do zestawu SDK Windows Azure Mobile Services  
  
1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **odwołania** węzeł i wybierz polecenie **Zarządzaj pakietami NuGet**.  
  
2. W **Menedżera pakietów NuGet**, wybierz **wyszukiwania** pola, a następnie wprowadź `mobileservices`.  
  
3. W okienku po lewej stronie wybierz **WindowsAzure.MobileServices**, a następnie w okienku po prawej stronie wybierz **zainstalować** przycisku.  
  
    > [!NOTE]
    >  Jeśli **Podgląd** zostanie wyświetlone okno dialogowe, przejrzyj proponowane zmiany, a następnie wybierz **OK** przycisku.  
  
4. W **akceptacja licencji** okno dialogowe, przejrzyj licencję warunki, a następnie zaakceptuj je, wybierając **akceptuję** przycisku.  
  
     Niezbędne odwołania zostaną dodane do **Eksploratora rozwiązań**.  
  
    > [!NOTE]
    >  Jeśli nie zgadzasz się z postanowieniami licencyjnymi, wybierz **odrzucam** przycisku. Nie można zakończyć pozostałej części przewodnika.  
  
## <a name="create-the-user-interface"></a>Tworzenie interfejsu użytkownika  
 Następnym krokiem jest do tworzenia interfejsu użytkownika dla aplikacji. Najpierw utworzysz formant użytkownika do wielokrotnego użytku, który wyświetla układ okienko dwa standardowe side-by-side. Można będzie Dodaj formant użytkownika do okna głównego aplikacji i dodawanie formantów do wprowadzania i wyświetlania danych, a następnie pisanie kodu służącego do definiowania interakcji z zapleczem usługi mobilnej.  
  
#### <a name="to-add-a-user-control"></a>Aby dodać kontrolkę użytkownika  
  
1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **WPFQuickStart** węzeł i wybierz polecenie **Dodaj**, **nowy Folder**.  
  
2. Nazwa folderu `Common`.  
  
3. Otwórz menu skrótów dla **typowe** folder i wybierz polecenie **Dodaj**, **kontrolki użytkownika**.  
  
4. W **Dodaj nowy element** okno dialogowe, wybierz pole nazwy, a następnie wprowadź `QuickStartTask`, a następnie wybierz **Dodaj** przycisku.  
  
     Formant użytkownika zostaną dodane do projektu i **QuickStartTask.xaml** plik zostanie otwarty w projektancie.  
  
5. W dolnym okienku projektanta wybierz `<Grid>` i `</Grid>` tagów i zamień następujący kod XAML:  
  
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
  
     Ten kod XAML tworzy wielokrotnego użytku układu przy użyciu symboli zastępczych dla pola Liczba, tytuł i opis. W czasie wykonywania można zastąpić symbole zastępcze z tekstem jak pokazano na poniższej ilustracji.  
  
     ![Kontrolki użytkownika QuickStartTask](../designers/media/wpfquickstart1.PNG "WPFQuickStart1")  
  
6. W **Eksploratora rozwiązań**, rozwiń węzeł **QuickStartTask.xaml** węzła i Otwórz **QuickStartTask.xaml.cs** lub **QuickStartTask.xaml.vb**pliku.  
  
7. W edytorze kodu Zastąp `namespace WPFQuickStart.Common` przestrzeni nazw (C#) lub `Public Class QuickStartTask` metody (VB) z następującym kodem:  
  
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
  
     Ten kod używa właściwości zależności można ustawić wartości dla pól numer, tytuł i opis w czasie wykonywania.  
  
8. Na pasku menu wybierz **kompilacji**, **kompilacji WPFQuickStart** do tworzenia kontrolki użytkownika.  
  
#### <a name="to-create-and-modify-the-main-window"></a>Tworzenie i modyfikowanie okna głównego  
  
1. W **Eksploratora rozwiązań**, otwórz **MainWindow.xaml** pliku.  
  
2. **Ważne**. Ten krok jest tylko dla języka C#. Jeśli używasz języka Visual Basic, przejdź do następnego kroku. W dolnym okienku projektanta, zlokalizuj wiersz `xmlns:local=”clr-namespace:WPFQuickStart”` i zastąp go następującym kodem XAML:  
  
    ```xaml  
    xmlns:local=”clr-namespace:WPFQuickStart.Common”  
    ```  
  
3. W **właściwości** okna, rozwiń węzeł **typowe** węzeł kategorii i wybierz polecenie **tytuł** właściwości, a następnie wprowadź `WPF Todo List` i naciśnij klawisz **Enter**  klucza.  
  
     Należy zauważyć, że **tytuł** element w oknie XAML zmieni się na pasowała do nowej wartości. Można zmodyfikować właściwości XAML w oknie XAML lub **właściwości** okna, a zmiany są synchronizowane.  
  
4. W oknie XAML, ustaw wartość **wysokość** elementu `768`i ustaw wartość **szerokość** właściwość `1280`.  
  
     Te elementy odnoszą się do **wysokość** i **szerokość** występują właściwości **układ** kategorii **właściwości** okna.  
  
5. Wybierz `<Grid>` i `</Grid>` tagów i zamień następujący kod XAML:  
  
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
  
     Należy zauważyć, że zmiany są widoczne w oknie projektu. Jeszcze raz, również można zdefiniowano interfejsu użytkownika przez dodanie formantów z **przybornika** okna i ustawianie właściwości w **właściwości** okna. Wszystko, co można zrobić w Projektancie może odbywać się w kodzie XAML i na odwrót.  
  
     W tym momencie projektu powinna wyglądać podobnie do poniższej ilustracji.  
  
     ![Główne w Projektancie](../designers/media/wpfquickstart2.PNG "WPFQuickStart2")  
  
    > [!NOTE]
    >  Podczas kolejnych kilku procedur mogą być wyświetlane błędy w **lista błędów** Jeśli jest otwarty. Nie martw się; te błędy znikną po zakończeniu procedury pozostałych.  
  
6. W **Eksploratora rozwiązań**, rozwiń węzeł **MainWindow.xaml** węzła i Otwórz **MainWindow.xaml.cs** lub **MainWindow.xaml.vb** pliku.  
  
7. W edytorze kodu Dodaj następujący `using` lub `Imports` dyrektywy górnej części pliku:  
  
    ```csharp  
    using Microsoft.WindowsAzure.MobileServices;  
    using Newtonsoft.Json;   
    ```  
  
    ```vb  
    Imports Microsoft.WindowsAzure.MobileServices  
    Imports Newtonsoft.Json  
    ```  
  
8. Zastąp cały kod w **WPFQuickStart** przestrzeni nazw (C#) lub **klasy MainWindow** klasy (VB) z następującym kodem:  
  
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
  
     Ten kod definiuje interakcji między interfejsu użytkownika i bazę danych w usłudze mobilnej, za pomocą metod asynchronicznych.  
  
## <a name="create-the-azure-mobile-service"></a>Tworzenie usługi mobilnej Azure  
 Ostatnim krokiem jest utworzenie usługi mobilnej w systemie Microsoft Azure Dodaj tabelę do przechowywania danych, a następnie odwoływać się do wystąpienia usługi z poziomu aplikacji.  
  
#### <a name="to-create-a-mobile-service"></a>Aby utworzyć usługę mobilną  
  
1. Otwórz przeglądarkę internetową i zaloguj się do portalu Microsoft Azure, a następnie wybierz **usług MOBILE SERVICES** kartę.  
  
2. Wybierz **NEW** przycisk, a następnie w wyświetlonym oknie dialogowym wybierz **obliczenia**, **usługi MOBILNEJ, tworzenie**.  
  
3. W **nowej usługi MOBILNEJ** okno dialogowe, wybierz **adresu URL** pole tekstowe i wpisz `wpfquickstart01`.  
  
    > [!NOTE]
    >  Może być konieczna zmiana liczbowej części adresu URL. Platforma Microsoft Azure wymaga unikatowego adresu URL dla każdej usługi mobilnej.  
  
     To ustawienie adresu URL usługi `https://wpfquickstart01.azure-mobile.net/`.  
  
4. W **bazy danych** , wybierz opcję bazy danych. Ponieważ jest to aplikacja, która prawdopodobnie nie będzie otrzymywał wiele użytkowania, należy wybrać **tworzenie bezpłatnej bazy danych SQL o rozmiarze 20MB** opcji lub wybierz bezpłatnej bazy danych już skojarzony z subskrypcją.  
  
5. W **REGION** wybierz centrum danych, w której chcesz wdrożyć usługę mobilną, a następnie wybierz **dalej** przycisku (Strzałka w prawo).  
  
    > [!NOTE]
    >  Dla tej usługi użyje domyślnej **ZAPLECZA** ustawienie **JavaScript**.  
  
6. W przypadku tworzenia nowej bazy danych na **Określ ustawienia bazy danych** strony w **serwera** listy wybierz **serwer bazy danych SQL na nowy**, wprowadź swoje **identyfikator logowania SQL Nazwa** i **hasło**, a następnie wybierz **Complete** przycisku (znacznik wyboru).  
  
7. W przypadku wybrania istniejącej bazy danych na **ustawienia bazy danych** wpisz swoje **hasło logowania** , a następnie wybierz **Complete** przycisku (znacznik wyboru).  
  
     Rozpocznie się proces tworzenia usługi mobilnej. Po ukończeniu procesu stan zmieni się na **gotowe** i możesz przejść do następnego kroku.  
  
8. W portalu, wybierz nowo utworzoną usługę mobilną, a następnie wybierz **Zarządzanie KLUCZAMI** przycisku.  
  
9. W **Zarządzaj kluczami dostępu** okno dialogowe, kopia **klucz aplikacji**.  
  
     Użyjesz tego w następnej procedurze.  
  
#### <a name="to-create-a-table"></a>Aby utworzyć tabelę  
  
1. W portalu Microsoft Azure, wybierz strzałkę w prawo obok nazwy usługi mobilnej, a na pasku menu, wybierz pozycję **danych**, a następnie wybierz **dodawania tabeli A** łącza.  
  
2. W **Utwórz nową tabelę** okna dialogowego w **nazwy tabeli** polu tekstowym wprowadź `TodoItem`, a następnie wybierz **Complete** przycisku (znacznik wyboru).  
  
     Poczekaj, aż tabeli, który ma zostać utworzony, a następnie przejść do ostatecznej procedurze.  
  
#### <a name="to-add-a-declaration-for-the-mobile-service"></a>Aby dodać deklarację dla usługi mobilnej  
  
1. Wróć do programu Visual Studio. W **Eksploratora rozwiązań**, rozwiń węzeł **App.xaml** (C#) lub **Application.xaml** węzła (Visual Basic) i Otwórz **App.xaml.cs** lub  **App.XAML.VB** pliku.  
  
2. W edytorze kodu Dodaj następujący `using` lub **Importy** dyrektywy górnej części pliku:  
  
    ```csharp  
    using Microsoft.WindowsAzure.MobileServices;  
    ```  
  
    ```vb  
    Imports Microsoft.WindowsAzure.MobileServices  
    ```  
  
3. Dodaj następującą deklarację klasy, zastępując *YOUR SERVICE_HERE* o nazwie adresu URL dla usługi i zastępowanie *YOUR klucz tutaj* przy użyciu klucza aplikacji, który został skopiowany w poprzednim Procedura:  
  
    ```csharp  
    public static MobileServiceClient MobileService = new MobileServiceClient(  
                 "https://YOUR-SERVICE-HERE.azure-mobile.net/",  
                 "YOUR-KEY-HERE"  
             );  
    ```  
  
    ```vb  
    Public Shared MobileService As New MobileServiceClient("https://YOUR-SERVICE-HERE.azure-mobile.net/", "YOUR-KEY-HERE")  
    ```  
  
     Ten kod umożliwia aplikacji dostęp do usługi mobilnej, w systemie Microsoft Azure.  
  
## <a name="test-the-application"></a>Testowanie aplikacji  
 To wszystko — zostanie utworzona aplikacja klasyczna WPF, która uzyskuje dostęp do usług Azure Mobile. Teraz pozostało jest uruchomienie aplikacji i sprawdzenie w działaniu.  
  
#### <a name="to-run-the-application"></a>Aby uruchomić aplikację  
  
1. Na pasku menu wybierz **debugowania**, **Rozpocznij debugowanie** (lub naciśnij klawisz F5).  
  
2. W **Wstaw czynność do wykonania** polu tekstowym wprowadź `Do something`, a następnie wybierz **Zapisz** przycisku.  
  
3. Wprowadź `Do something else`, a następnie wybierz **Zapisz** ponownie przycisk.  
  
     Należy zauważyć, że dwa wpisy są dodawane do **zapytań i aktualizacji danych** listy, jak pokazano na poniższej ilustracji.  
  
     ![Wykonania są dodawane do listy. ](../designers/media/wpfquickstart3.PNG "WPFQuickStart3")  
  
4. Zaznacz pole wyboru **czymś innym** wpisu na liście.  
  
     Powoduje to wywołanie **UpdateCheckedTodoItem** metody i usuwa element z listy i bazy danych.  
  
## <a name="next-steps"></a>Następne kroki  
 Ukończono dość uproszczony przykład aplikacji klasycznej WPF, przy użyciu zaplecza platformy Azure. Oczywiście rzeczywistej aplikacji będzie prawdopodobnie znacznie bardziej złożone, ale stosować te same podstawowe pojęcia. Zobacz [platformy WPF w programie .NET Framework](https://msdn.microsoft.com/library/ms754130\(v=vs.100\).aspx).  
  
 Można wprowadzić interfejsu użytkownika bardziej atrakcyjne, dodając kolor, kształty, grafiki i animacje nawet. Zobacz [projektowanie XAML w programie Visual Studio i Blend for Visual Studio](../designers/designing-xaml-in-visual-studio.md).  
  
 Możesz połączyć do istniejącej bazy danych SQL lub innych źródeł danych przy użyciu usług Azure Mobile Services. Zobacz [dokumentacja usług Mobile Services](http://azure.microsoft.com/services/app-service/mobile/).  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Mój pierwszy aplikacji klasycznej WPF](../designers/walkthrough-my-first-wpf-desktop-application2.md)   
 [Tworzenie nowoczesnych aplikacji klasycznych przy użyciu platformy Windows Presentation Foundation](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md)
