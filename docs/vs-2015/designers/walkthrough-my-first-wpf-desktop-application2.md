---
title: 'Przewodnik: moje pierwsze Application2 w usłudze WPF Desktop | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 3c460fa9-2ea1-413f-ae54-54a1f2a499d1
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e800fe651d32435351b2338b4da2f9c55158b3a0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663995"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>Przewodnik: moja pierwsza aplikacja klasyczna WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

a Name = "Introduction" > </a> ten Instruktaż zawiera wprowadzenie do tworzenia Windows Presentation Foundation (WPF). Utworzysz podstawową aplikację obejmującą elementy, które są wspólne dla większości aplikacji klasycznych WPF: oznakowanie XAML, powiązane z kodem, definicje aplikacji, formanty, układ, powiązanie danych i style.

## <a name="Create_The_Application_Code_Files"></a>Tworzenie projektu aplikacji
 W tej sekcji utworzysz infrastrukturę aplikacji, która obejmuje projekt i główne okno lub formularz.

#### <a name="to-create-the-project"></a>Aby utworzyć projekt

1. Na pasku menu wybierz **plik**, **Nowy**, **projekt**.

2. W oknie dialogowym **Nowy projekt** rozwiń węzeł  **C# Wizualizacja** lub **Visual Basic** i wybierz węzeł **systemu Windows** , a następnie rozwiń węzeł **Windows** i wybierz węzeł **klasyczny pulpit** .

3. Z listy szablon wybierz szablon **Aplikacja WPF** .

4. W polu tekstowym **Nazwa** wprowadź `ExpenseIt`, a następnie wybierz przycisk **OK** .

     Projekt zostanie utworzony, a pliki projektu zostaną dodane do **Eksplorator rozwiązań**i zostanie wyświetlony Projektant domyślnego okna aplikacji o nazwie **MainWindow. XAML** .

#### <a name="to-modify-the-main-window"></a>Aby zmodyfikować okno główne

1. W Projektancie wybierz kartę **MainWindow. XAML** , jeśli nie jest jeszcze aktywna karta projektanta.

2. Jeśli używasz C#programu, znajdź wiersz `<Window x:Class="ExpenseIt.MainWindow"` i zastąp go `<NavigationWindow x:Class="ExpenseIt.MainWindow"`.

     Jeśli używasz Visual Basic, Znajdź wiersz `<Window x:Class=" MainWindow"` i zastąp go `<NavigationWindow x:Class="MainWindow"`.

     Zauważ, że po zmianie znacznika `<Window` na `<NavigationWindow`, funkcja IntelliSense automatycznie zmieni tag zamykający, aby `</NavigationWindow>`.

    > [!NOTE]
    > Po zmianie znacznika, jeśli okno **Lista błędów** jest otwarte, może być zauważalne kilka błędów. Nie martw się, zmiany wprowadzone w następnych kilku krokach spowodują przechodzenie między nimi.

3. Wybierz Tagi `<Grid>` i `</Grid>` i usuń je.

     Element **NavigationWindow** nie może zawierać innych elementów interfejsu użytkownika, takich jak **Siatka**.

4. W oknie **Właściwości** rozwiń węzeł **wspólnych** kategorii i wybierz właściwość **Title** , a następnie wprowadź `ExpenseIt` i naciśnij klawisz **Enter** .

     Zwróć uwagę, że element **title** w oknie XAML zmienia się w taki sposób, aby odpowiadał nowej wartości. Właściwości XAML można modyfikować w oknie XAML lub w oknie **Właściwości** , a zmiany są synchronizowane.

5. W oknie XAML ustaw wartość elementu **Height** na `375` i ustaw wartość właściwości **Width** na `500`.

     Te elementy odpowiadają właściwościom **wysokości** i **szerokości** , które znajdują się w kategorii **Układ** w oknie **Właściwości** .

     Plik **MainWindow. XAML** powinien teraz wyglądać następująco C#:

    ```xaml
    <NavigationWindow x:Class="ExpenseIt.MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
            xmlns:local="clr-namespace:ExpenseIt"
            mc:Ignorable="d"
            Title="ExpenseIt" Height="375" Width="500">

    </NavigationWindow>
    ```

     Lub takie jak w Visual Basic:

    ```xaml
    <NavigationWindow x:Class="MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
            xmlns:local="clr-namespace:ExpenseIt"
            mc:Ignorable="d"
            Title="ExpenseIt" Height="375" Width="500">

    </NavigationWindow>
    ```

#### <a name="to-modify-the-code-behind-file-c"></a>Aby zmodyfikować plik związany z kodem (C#)

1. W **Eksplorator rozwiązań**rozwiń węzeł **MainWindow. XAML** i Otwórz plik **MainWindow.XAML.cs** .

2. Znajdź wiersz `public partial class MainWindow : Window` i zastąp go `public partial class MainWindow : NavigationWindow`.

     Spowoduje to zmianę klasy `MainWindow` na pochodną z `NavigationWindow`. W Visual Basic, dzieje się to automatycznie po zmianie okna w języku XAML, więc nie są wymagane żadne zmiany w kodzie.

## <a name="add_files_to_the_application"></a>Dodawanie plików do aplikacji
 W tej sekcji dodasz dwie strony i obraz do aplikacji.

#### <a name="to-add-a-home-screen"></a>Aby dodać ekran główny

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła **ExpenseIt** i wybierz polecenie **Dodaj**, **Strona**.

2. W oknie dialogowym **Dodaj nowy element** wybierz pole tekstowe **nazwa** i wprowadź `ExpenseItHome`, a następnie wybierz przycisk **Dodaj** .

     Ta strona jest pierwszym oknem wyświetlanym podczas uruchamiania aplikacji.

3. W Projektancie wybierz kartę **ExpenseItHome. XAML** , jeśli nie jest jeszcze aktywna karta projektanta.

4. Wybierz element `<Title>` i zmień tytuł na **ExpenseIt — Strona główna**.

     Plik **ExpenseItHome. XAML** powinien teraz wyglądać następująco C#:

    ```xaml
    <Page x:Class="ExpenseIt.ExpenseItHome"
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
          xmlns:local="clr-namespace:ExpenseIt"
          mc:Ignorable="d"
          d:DesignHeight="300" d:DesignWidth="300"
          Title="ExpenseIt - Home">

        <Grid>

        </Grid>
    </Page>
    ```

     Lub takie jak w Visual Basic:

    ```xaml
    <Page x:Class="ExpenseItHome"
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
          xmlns:local="clr-namespace:ExpenseIt"
          mc:Ignorable="d"
          d:DesignHeight="300" d:DesignWidth="300"
          Title="ExpenseIt - Home">
        <Grid>

        </Grid>
    </Page>
    ```

5. W Projektancie wybierz kartę **MainWindow. XAML** .

6. Znajdź wiersz `Title="ExpenseIt" Height="375" Width="500">` elementu i Dodaj właściwość `Source="ExpenseItHome.xaml"`.

     Spowoduje to ustawienie **ExpenseItHome. XAML** jako pierwszej strony otwartej podczas uruchamiania aplikacji. Plik **MainWindow. XAML** powinien teraz wyglądać następująco C#:

    ```xaml
    <NavigationWindow x:Class="ExpenseIt.MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
            xmlns:local="clr-namespace:ExpenseIt"
            mc:Ignorable="d"
            Title="ExpenseIt" Height="375" Width="500" Source="ExpenseItHome.xaml">

    </NavigationWindow>
    ```

     Lub takie jak w Visual Basic:

    ```xaml
    <NavigationWindow x:Class="MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
            xmlns:local="clr-namespace:ExpenseIt"
            mc:Ignorable="d"
            Title="ExpenseIt" Height="375" Width="500" Source="ExpenseItHome.xaml">

    </NavigationWindow>
    ```

     Tak jak we właściwościach ustawionych wcześniej, można ustawić właściwość `Source` w kategorii **różne** okna **Właściwości** .

#### <a name="to-add-a-details-window"></a>Aby dodać okno szczegółów

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła **ExpenseIt** i wybierz polecenie **Dodaj**, **Strona**.

2. W oknie dialogowym **Dodaj nowy element** wybierz pole tekstowe **nazwa** i wprowadź `ExpenseReportPage`, a następnie wybierz przycisk **Dodaj** .

     W tym oknie zostanie wyświetlony pojedynczy raport z wydatków.

3. W Projektancie wybierz kartę **ExpenseReportPage. XAML** , jeśli nie jest jeszcze aktywna karta projektanta.

4. Wybierz element `<Title>` i zmień tytuł na **ExpenseIt — wyświetlanie wydatków**.

     Plik ExpenseReportPage. XAML powinien teraz wyglądać następująco C#:

    ```xaml
    <Page x:Class="ExpenseIt.ExpenseReportPage"
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
          xmlns:local="clr-namespace:ExpenseIt"
          mc:Ignorable="d"
          d:DesignHeight="300" d:DesignWidth="300"
          Title="ExpenseIt - View Expense">

        <Grid>

        </Grid>
    </Page>
    ```

     Lub takie jak w Visual Basic:

    ```xaml
    <Page x:Class="ExpenseReportPage"
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
          xmlns:local="clr-namespace:ExpenseIt"
          mc:Ignorable="d"
          d:DesignHeight="300" d:DesignWidth="300"
          Title="ExpenseIt - View Expense">
        <Grid>

        </Grid>
    </Page>
    ```

5. Na pasku menu wybierz **Debuguj**, **Rozpocznij debugowanie** (lub naciśnij klawisz F5), aby uruchomić aplikację.

     Na poniższej ilustracji przedstawiono aplikację z przyciskami okna nawigacyjnego.

     ![Zrzut ekranu przedstawiający przykładowy ExpenseIt](../designers/media/gettingstartedfigure1.png "GettingStartedFigure1")

6. Zamknij aplikację, aby powrócić do trybu projektowania.

## <a name="Add_Layout"></a>Tworzenie interfejsu użytkownika
 Układ zapewnia uporządkowany sposób umieszczania elementów, a także zarządza rozmiarem i położeniem tych elementów, gdy zmieniany jest rozmiar formularza. W tej sekcji utworzysz siatkę z jedną kolumną zawierającą trzy wiersze. Dodasz kontrolki do obu stron, dodasz kod, a wreszcie zdefiniujesz style do wielokrotnego użytku dla kontrolek.

#### <a name="to-create-the-layout"></a>Aby utworzyć układ

1. Otwórz **ExpenseItHome. XAML** i wybierz element `<Grid>`.

2. W oknie **Właściwości** rozwiń węzeł Kategoria **układu** i ustaw wartości **marginesu** na `10`, `10`, `0` i `10`, które odnoszą się do lewego, prawego, górnego i dolnego marginesu.

     Element `Margin="10,0,10,10"` jest dodawany do elementu `<Grid>` w kodzie XAML. Ponownie można wprowadzić te wartości bezpośrednio w kodzie XAML zamiast w oknie **Właściwości** z tym samym wynikiem.

3. Dodaj następujący kod XAML do elementu `Grid`, aby utworzyć definicje wierszy i kolumn:

    ```xaml
    <Grid.ColumnDefinitions>
        <ColumnDefinition />
    </Grid.ColumnDefinitions>
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition />
        <RowDefinition Height="Auto"/>
    </Grid.RowDefinitions>
    ```

#### <a name="to-add-controls"></a>Aby dodać kontrolki

1. Otwórz **ExpenseItHome. XAML**.

2. Dodaj następujący kod XAML tuż nad tagiem `</Grid>`, aby utworzyć `Border`, `ListBox` i `Button` formantów.

    ```xaml
    <!-- People list -->
      <Border Grid.Column="0" Grid.Row="0" Height="35" Padding="5" Background="#4E87D4">
          <Label VerticalAlignment="Center" Foreground="White">Names</Label>
      </Border>
      <ListBox Name="peopleListBox" Grid.Column="0" Grid.Row="1">
          <ListBoxItem>Mike</ListBoxItem>
          <ListBoxItem>Lisa</ListBoxItem>
          <ListBoxItem>John</ListBoxItem>
          <ListBoxItem>Mary</ListBoxItem>
      </ListBox>

      <!-- View report button -->
      <Button Grid.Column="0" Grid.Row="2" Margin="0,10,0,0" Width="125"
    Height="25" HorizontalAlignment="Right">View</Button>

    ```

     Zauważ, że kontrolki pojawiają się w oknie projektowania. Można również tworzyć kontrolki, przeciągając je z okna **przybornika** do okna projektowania i ustawiając ich właściwości w oknie **Właściwości** .

3. Skompiluj i uruchom aplikację. Na poniższej ilustracji przedstawiono wygląd w czasie wykonywania formantów, które są tworzone przez kod XAML w tej procedurze.

     ![Zrzut ekranu przedstawiający przykładowy ExpenseIt](../designers/media/gettingstartedfigure2.png "GettingStartedFigure2")

4. Zamknij aplikację, aby powrócić do trybu projektowania.

#### <a name="to-add-a-background-image"></a>Aby dodać obraz tła

1. Wybierz Poniższy obraz i Zapisz go jako `watermark.png`.

     ![Obraz znaku wodnego dla przewodnika](../designers/media/wpf-watermark.png "WPF_watermark")

    > [!NOTE]
    > Alternatywnie możesz utworzyć własny obraz i zapisać go jako `watermark.png`.

2. W **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła **ExpenseIt** i wybierz polecenie **Dodaj**, **istniejący element**.

3. W oknie dialogowym **Dodawanie istniejącego elementu** Znajdź właśnie dodany **plik ze znakiem wodnego** , wybierz go, a następnie wybierz przycisk **Dodaj** .

    > [!NOTE]
    > Może być konieczne rozwinięcie listy **typów plików** i wybranie opcji **pliki obrazów**.

4. Otwórz plik **ExpenseItHome. XAML** i Dodaj następujący kod XAML tuż nad tagiem `</Grid>`, aby utworzyć obraz tła:

    ```xaml
    <Grid.Background>
        <ImageBrush ImageSource="watermark.png"/>
    </Grid.Background>

    ```

#### <a name="to-add-a-title"></a>Aby dodać tytuł

1. Otwórz **ExpenseItHome. XAML**.

2. Znajdź wiersz `<Grid.ColumnDefinitions>` i Dodaj następujący element poniżej:

    ```xaml
    <ColumnDefinition Width="230" />

    ```

     Spowoduje to utworzenie dodatkowej kolumny z lewej strony innych kolumn o stałej szerokości 230 pikseli.

3. Znajdź wiersz `<Grid.RowDefinitions>` i Dodaj następujący element poniżej:

    ```xaml
    <RowDefinition />

    ```

     Spowoduje to dodanie wiersza w górnej części siatki.

4. Przenieś kontrolki do drugiej kolumny, ustawiając wartość `Grid.Column` na 1. Przenieś każdy formant w dół do wiersza, zwiększając każdą `Grid.Row` wartość o 1.

    1. Znajdź wiersz `<Border Grid.Column="0" Grid.Row="0" Height="35" Padding="5" Background="#4E87D4">`. Zmień `Grid.Column="0"` na `Grid.Column="1"` i Zmień `Grid.Row="0"` na `Grid.Row="1"`.

    2. Znajdź wiersz `<ListBox Name="peopleListBox" Grid.Column="0" Grid.Row="1"`. Zmień `Grid.Column="0"` na `Grid.Column="1"` i Zmień `Grid.Row="1"` na `Grid.Row="2"`.

    3. Znajdź wiersz `<Button Grid.Column="0" Grid.Row="2" Margin="0,10,0,0" Width="125"`. Zmień `Grid.Column="0"` na `Grid.Column="1"` i Zmień `Grid.Row="2"` na `Grid.Row="3"`.

5. Tuż przed elementem `<Border` Dodaj następujący kod XAML, aby wyświetlić tytuł:

    ```xaml
    <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"
            FontWeight="Bold" FontSize="18" Foreground="#0066cc">
        View Expense Report
    </Label>

    ```

     Zawartość pliku **ExpenseItHome. XAML** powinna teraz wyglądać następująco C#:

    ```xaml
    <Page x:Class="ExpenseIt.ExpenseItHome"
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
          xmlns:local="clr-namespace:ExpenseIt"
          mc:Ignorable="d"
          d:DesignHeight="300" d:DesignWidth="300"
          Title="ExpenseIt - Home">
        <Grid Margin="10,0,10,10">
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="230" />
                <ColumnDefinition />
            </Grid.ColumnDefinitions>
            <Grid.RowDefinitions>
                <RowDefinition />
                <RowDefinition Height="Auto"/>
                <RowDefinition />
                <RowDefinition Height="Auto"/>
            </Grid.RowDefinitions>
            <Border Grid.Column="1" Grid.Row="1" Height="35" Padding="5" Background="#4E87D4">
                <Label VerticalAlignment="Center" Foreground="White">Names</Label>
            </Border>
            <!-- People list -->
            <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"
            FontWeight="Bold" FontSize="18" Foreground="#0066cc">
                View Expense Report
            </Label>
            <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2">
                <ListBoxItem>Mike</ListBoxItem>
                <ListBoxItem>Lisa</ListBoxItem>
                <ListBoxItem>John</ListBoxItem>
                <ListBoxItem>Mary</ListBoxItem>
            </ListBox>

            <!-- View report button -->
            <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125"
    Height="25" HorizontalAlignment="Right">View</Button>
            <Grid.Background>
                <ImageBrush ImageSource="watermark.png"/>
            </Grid.Background>
        </Grid>
    </Page>
    ```

     Lub takie jak w Visual Basic:

    ```xaml
    <Page x:Class="ExpenseItHome"
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
          xmlns:local="clr-namespace:ExpenseIt"
          mc:Ignorable="d"
          d:DesignHeight="300" d:DesignWidth="300"
          Title="ExpenseIt - Home" >
        <Grid Margin="10,0,10,10">
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="230" />
                <ColumnDefinition />
            </Grid.ColumnDefinitions>
            <Grid.RowDefinitions>
                <RowDefinition />
                <RowDefinition Height="Auto"/>
                <RowDefinition />
                <RowDefinition Height="Auto"/>
            </Grid.RowDefinitions>
            <Border Grid.Column="1" Grid.Row="1" Height="35" Padding="5" Background="#4E87D4">
                <Label VerticalAlignment="Center" Foreground="White">Names</Label>
            </Border>
            <!-- People list -->
            <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"
            FontWeight="Bold" FontSize="18" Foreground="#0066cc">
                View Expense Report
            </Label>
            <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2">
                <ListBoxItem>Mike</ListBoxItem>
                <ListBoxItem>Lisa</ListBoxItem>
                <ListBoxItem>John</ListBoxItem>
                <ListBoxItem>Mary</ListBoxItem>
            </ListBox>

            <!-- View report button -->
            <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125"
    Height="25" HorizontalAlignment="Right">View</Button>
            <Grid.Background>
                <ImageBrush ImageSource="watermark.png"/>
            </Grid.Background>
        </Grid>
    </Page>
    ```

6. W przypadku kompilowania i uruchamiania aplikacji w tym momencie powinna wyglądać tak jak na poniższej ilustracji:

     ![Zrzut ekranu przedstawiający przykładowy ExpenseIt](../designers/media/gettingstartedfigure3.png "GettingStartedFigure3")

#### <a name="to-add-code-to-the-button"></a>Aby dodać kod do przycisku

1. Otwórz **ExpenseItHome. XAML**.

2. Wybierz element `<Button` i Dodaj następujący kod XAML bezpośrednio po elemencie **HorizontalAlignment = "Right"** : `Click="Button_Click"`.

     Spowoduje to dodanie programu obsługi zdarzeń dla zdarzenia `Click` przycisku. Kod elementu **przycisku <** powinien teraz wyglądać następująco:

    ```
    <!-- View report button -->
      <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125"
    Height="25" HorizontalAlignment="Right" Click="Button_Click">View</Button>
    ```

3. Otwórz plik **ExpenseItHome.XAML.cs** lub **ExpenseItHome. XAML. vb** .

4. Dodaj następujący kod do klasy `ExpenseItHome`:

    ```csharp
    private void Button_Click(object sender, RoutedEventArgs e)
    {
        // View Expense Report
        ExpenseReportPage expenseReportPage = new ExpenseReportPage();
        this.NavigationService.Navigate(expenseReportPage);

    }
    ```

    ```vb
    Private Sub Button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)
        ' View Expense Report
        Dim expenseReportPage As New ExpenseReportPage()
    Me.NavigationService.Navigate(expenseReportPage)
    End Sub
    ```

     Ta procedura obsługi zdarzeń otwiera stronę Raport z wydatków po kliknięciu przycisku.

#### <a name="to-create-the-ui-for-the-report-page"></a>Aby utworzyć interfejs użytkownika dla strony raportu

1. Otwórz **ExpenseReportPage. XAML**.

     Na tej stronie zostanie wyświetlony raport wydatków dla osoby, która została wybrana na stronie głównej.

2. Dodaj następujący kod XAML między tagami `<Grid>` i `</Grid>`:

    ```xaml
    <Grid.Background>
        <ImageBrush ImageSource="watermark.png" />
    </Grid.Background>
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="230" />
        <ColumnDefinition />
    </Grid.ColumnDefinitions>
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto" />
        <RowDefinition />
    </Grid.RowDefinitions>

    <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"
    FontWeight="Bold" FontSize="18" Foreground="#0066cc">
        Expense Report For:
    </Label>
    <Grid Margin="10" Grid.Column="1" Grid.Row="1">

        <Grid.ColumnDefinitions>
            <ColumnDefinition />
            <ColumnDefinition />
        </Grid.ColumnDefinitions>
        <Grid.RowDefinitions>
            <RowDefinition Height="Auto" />
            <RowDefinition Height="Auto" />
            <RowDefinition />
        </Grid.RowDefinitions>

        <!-- Name -->
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">
            <Label Margin="0,0,0,5" FontWeight="Bold">Name:</Label>
            <Label Margin="0,0,0,5" FontWeight="Bold"></Label>
        </StackPanel>

        <!-- Department -->
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1" Orientation="Horizontal">
            <Label Margin="0,0,0,5" FontWeight="Bold">Department:</Label>
            <Label Margin="0,0,0,5" FontWeight="Bold"></Label>
        </StackPanel>

        <Grid Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="2" VerticalAlignment="Top"
              HorizontalAlignment="Left">
            <!-- Expense type and Amount table -->
            <DataGrid  AutoGenerateColumns="False" RowHeaderWidth="0" >
                <DataGrid.ColumnHeaderStyle>
                    <Style TargetType="{x:Type DataGridColumnHeader}">
                        <Setter Property="Height" Value="35" />
                        <Setter Property="Padding" Value="5" />
                        <Setter Property="Background" Value="#4E87D4" />
                        <Setter Property="Foreground" Value="White" />
                    </Style>
                </DataGrid.ColumnHeaderStyle>
                <DataGrid.Columns>
                    <DataGridTextColumn Header="ExpenseType" />
                    <DataGridTextColumn Header="Amount"  />
                </DataGrid.Columns>
            </DataGrid>
        </Grid>
    </Grid>
    ```

     Ten interfejs użytkownika jest podobny do interfejsu użytkownika utworzonego dla strony głównej, ale dane raportu są wyświetlane w kontrolce **DataGrid** .

3. Skompiluj i uruchom aplikację.

4. Wybierz przycisk **Wyświetl** .

     Zostanie wyświetlona strona raport o wydatkach.

     Na poniższej ilustracji przedstawiono stronę raport wydatków. Zwróć uwagę, że przycisk nawigacji wstecznej jest włączony.

     ![Zrzut ekranu przedstawiający przykładowy ExpenseIt](../designers/media/gettingstartedfigure4.png "GettingStartedFigure4")

#### <a name="to-style-controls"></a>Do kontrolek stylu

1. Otwórz plik **App. XAML** (C#) lub plik **Application. XAML** (Visual Basic).

2. Dodaj następujący kod XAML między tagami `<Application.Resources>` i `</Application.Resources>`:

    ```xaml
    <!-- Header text style -->
    <Style x:Key="headerTextStyle">
        <Setter Property="Label.VerticalAlignment" Value="Center"></Setter>
        <Setter Property="Label.FontFamily" Value="Trebuchet MS"></Setter>
        <Setter Property="Label.FontWeight" Value="Bold"></Setter>
        <Setter Property="Label.FontSize" Value="18"></Setter>
        <Setter Property="Label.Foreground" Value="#0066cc"></Setter>
    </Style>

    <!-- Label style -->
    <Style x:Key="labelStyle" TargetType="{x:Type Label}">
        <Setter Property="VerticalAlignment" Value="Top" />
        <Setter Property="HorizontalAlignment" Value="Left" />
        <Setter Property="FontWeight" Value="Bold" />
        <Setter Property="Margin" Value="0,0,0,5" />
    </Style>

    <!-- DataGrid header style -->
    <Style x:Key="columnHeaderStyle" TargetType="{x:Type DataGridColumnHeader}">
        <Setter Property="Height" Value="35" />
        <Setter Property="Padding" Value="5" />
        <Setter Property="Background" Value="#4E87D4" />
        <Setter Property="Foreground" Value="White" />
    </Style>

    <!-- List header style -->
    <Style x:Key="listHeaderStyle" TargetType="{x:Type Border}">
        <Setter Property="Height" Value="35" />
        <Setter Property="Padding" Value="5" />
        <Setter Property="Background" Value="#4E87D4" />
    </Style>

    <!-- List header text style -->
    <Style x:Key="listHeaderTextStyle" TargetType="{x:Type Label}">
        <Setter Property="Foreground" Value="White" />
        <Setter Property="VerticalAlignment" Value="Center" />
        <Setter Property="HorizontalAlignment" Value="Left" />
    </Style>

    <!-- Button style -->
    <Style x:Key="buttonStyle" TargetType="{x:Type Button}">
        <Setter Property="Width" Value="125" />
        <Setter Property="Height" Value="25" />
        <Setter Property="Margin" Value="0,10,0,0" />
        <Setter Property="HorizontalAlignment" Value="Right" />
    </Style>
    ```

     Ten kod XAML dodaje następujące style:

    - `headerTextStyle`: Formatowanie tytułu strony `Label`.

    - `labelStyle`: Aby sformatować kontrolki `Label`.

    - `columnHeaderStyle`: Aby sformatować `DataGridColumnHeader`.

    - `listHeaderStyle`: Aby sformatować kontrolki nagłówka listy `Border`.

    - `listHeaderTextStyle`: Aby sformatować **etykietę**nagłówka listy.

    - `buttonStyle`: Aby sformatować `Button` w **ExpenseItHome. XAML** pppage.

3. Otwórz **ExpenseItHome. XAML** i Zastąp wszystkie elementy `<Grid>` i `</Grid>` następującym XAML

    ```xaml
    <Grid.ColumnDefinitions>
                <ColumnDefinition Width="230" />
                <ColumnDefinition />
            </Grid.ColumnDefinitions>

            <Grid.RowDefinitions>
                <RowDefinition/>
                <RowDefinition Height="Auto"/>
                <RowDefinition />
                <RowDefinition Height="Auto"/>
            </Grid.RowDefinitions>
            <Label Grid.Column="1" Style="{StaticResource headerTextStyle}" >
                View Expense Report
            </Label>
            <!-- People list -->
                  <Border Grid.Column="1" Grid.Row="1" Style="{StaticResource listHeaderStyle}">
                <Label Style="{StaticResource listHeaderTextStyle}">Names</Label>
            </Border>
            <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2">
                <ListBoxItem>Mike</ListBoxItem>
                <ListBoxItem>Lisa</ListBoxItem>
                <ListBoxItem>John</ListBoxItem>
                <ListBoxItem>Mary</ListBoxItem>
            </ListBox>

            <!-- View report button -->
            <Button Grid.Column="1" Grid.Row="3" Click="Button_Click" Style="{StaticResource buttonStyle}">View</Button>
            <Grid.Background>
                <ImageBrush ImageSource="watermark.png"  />
            </Grid.Background>
    ```

     Właściwości, takie jak `VerticalAlignment` i `FontFamily` definiujące wygląd poszczególnych kontrolek, są usuwane i zastępowane przez zastosowanie stylów.

4. Otwórz **ExpenseReportPage. XAML** i Zastąp wszystkie elementy `<Grid>` i Final `</Grid>` elementami następującym XAML

    ```xaml
    <Grid.Background>
        <ImageBrush ImageSource="watermark.png" />
    </Grid.Background>
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="230" />
        <ColumnDefinition />
    </Grid.ColumnDefinitions>
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto" />
        <RowDefinition />
    </Grid.RowDefinitions>
    <Label Grid.Column="1" Style="{StaticResource headerTextStyle}">
        Expense Report For:
    </Label>
    <Grid Margin="10" Grid.Column="1" Grid.Row="1">
        <Grid.ColumnDefinitions>
            <ColumnDefinition />
            <ColumnDefinition />
        </Grid.ColumnDefinitions>
        <Grid.RowDefinitions>
            <RowDefinition Height="Auto" />
            <RowDefinition Height="Auto" />
            <RowDefinition />
        </Grid.RowDefinitions>

        <!-- Name -->
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">
            <Label Style="{StaticResource labelStyle}">Name:</Label>
            <Label Style="{StaticResource labelStyle}"></Label>
        </StackPanel>

        <!-- Department -->
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1"
    Orientation="Horizontal">
            <Label Style="{StaticResource labelStyle}">Department:</Label>
            <Label Style="{StaticResource labelStyle}"></Label>
        </StackPanel>

        <Grid Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="2" VerticalAlignment="Top"
              HorizontalAlignment="Left">
            <!-- Expense type and Amount table -->
            <DataGrid ColumnHeaderStyle="{StaticResource columnHeaderStyle}"
                      AutoGenerateColumns="False" RowHeaderWidth="0" >
                <DataGrid.Columns>
                    <DataGridTextColumn Header="ExpenseType" />
                    <DataGridTextColumn Header="Amount"  />
                </DataGrid.Columns>
            </DataGrid>
        </Grid>
    </Grid>

    ```

     Spowoduje to dodanie stylów do `<Label>` i `<Border>` elementów.

## <a name="connecting-to-data"></a>Łączenie z danymi
 W tej sekcji utworzysz dostawcę danych i szablon danych, a następnie połączysz kontrolki, aby wyświetlić dane.

#### <a name="to-bind-data-to-a-control"></a>Aby powiązać dane z kontrolką

1. Otwórz **ExpenseItHome. XAML** i wybierz element `<Grid>`.

2. Dodaj następujący kod XAML:

    ```xaml

    <Grid.Resources>
    <!-- Expense Report Data -->
    <XmlDataProvider x:Key="ExpenseDataSource" XPath="Expenses">
        <x:XData>
            <Expenses xmlns="">
                <Person Name="Mike" Department="Legal">
                    <Expense ExpenseType="Lunch" ExpenseAmount="50" />
                    <Expense ExpenseType="Transportation" ExpenseAmount="50" />
                </Person>
                <Person Name="Lisa" Department="Marketing">
                    <Expense ExpenseType="Document printing"
          ExpenseAmount="50"/>
                    <Expense ExpenseType="Gift" ExpenseAmount="125" />
                </Person>
                <Person Name="John" Department="Engineering">
                    <Expense ExpenseType="Magazine subscription"
         ExpenseAmount="50"/>
                    <Expense ExpenseType="New machine" ExpenseAmount="600" />
                    <Expense ExpenseType="Software" ExpenseAmount="500" />
                </Person>
                <Person Name="Mary" Department="Finance">
                    <Expense ExpenseType="Dinner" ExpenseAmount="100" />
                </Person>
            </Expenses>
        </x:XData>
    </XmlDataProvider>
    </Grid.Resources>
    ```

     Ten kod tworzy klasę `XmlDataProvider`, która zawiera dane dla każdej osoby. Zwykle zostanie to załadowane jako plik, ale dla uproszczenia dane są dodawane wewnętrznie.

3. Wewnątrz elementu `<Grid.Resources>` Dodaj następujący kod XAML:

    ```xaml
    <!-- Name item template -->
    <DataTemplate x:Key="nameItemTemplate">
        <Label Content="{Binding XPath=@Name}"/>
    </DataTemplate>
    ```

     Spowoduje to dodanie `Data Template`, który definiuje sposób wyświetlania danych w polu **listy**.

4. Zastąp istniejący element `<ListBox>` następującym XAML.

    ```xaml
    <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2"
             ItemsSource="{Binding Source={StaticResource ExpenseDataSource}, XPath=Person}"
             ItemTemplate="{StaticResource nameItemTemplate}">
    </ListBox>
    ```

     Ten kod wiąże `ItemsSource` Właściwość `ListBox` ze źródłem danych i stosuje szablon danych jako `ItemTemplate`.

#### <a name="to-connect-data-to-controls"></a>Aby połączyć dane z kontrolkami

1. Otwórz **ExpenseReportPage. XAML. vb** lub **ExpenseReportPage.XAML.cs**.

2. W C#programie Dodaj następujący Konstruktor do klasy **ExpenseReportPage** lub w Visual Basic Zastąp istniejącą klasę następującymi:

    ```csharp
    // Custom constructor to pass expense report data
        public ExpenseReportPage(object data):this()
        {
            // Bind to expense report data.
            this.DataContext = data;
        }
    ```

    ```vb
    Partial Public Class ExpenseReportPage
    Inherits Page
    Public Sub New()
    InitializeComponent()
    End Sub

    ' Custom constructor to pass expense report data
    Public Sub New(ByVal data As Object)
    Me.New()
    ' Bind to expense report data.
    Me.DataContext = data
    End Sub

    End Class
    ```

     Ten konstruktor przyjmuje obiekt danych jako parametr. W takim przypadku obiekt danych będzie zawierać nazwę wybranej osoby.

3. Otwórz **ExpenseItHome. XAML. vb** lub **ExpenseItHome.XAML.cs**.

4. Zastąp kod programu obsługi zdarzeń `Click` poniższym:

    ```csharp
    private void Button_Click(object sender, RoutedEventArgs e)
    {
        // View Expense Report
        ExpenseReportPage expenseReportPage = new ExpenseReportPage(this.peopleListBox.SelectedItem);
        this.NavigationService.Navigate(expenseReportPage);

    }
    ```

    ```vb
    Private Sub Button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)
        ' View Expense Report
        Dim expenseReportPage As New ExpenseReportPage(Me.peopleListBox.SelectedItem)
        Me.NavigationService.Navigate(expenseReportPage)
    End Sub
    ```

     Ten kod wywołuje nowego konstruktora.

#### <a name="to-update-the-ui-with-data-templates"></a>Aby zaktualizować interfejs użytkownika przy użyciu szablonów danych

1. Otwórz **ExpenseReportPage. XAML**.

2. Zastąp kod XAML dla **nazwy** i **działu** `<StackPanel` następującymi elementami:

    ```xaml
    <!-- Name -->
    <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">
        <Label Style="{StaticResource labelStyle}">Name:</Label>
        <Label Style="{StaticResource labelStyle}" Content="{Binding XPath=@Name}"></Label>
    </StackPanel>

    <!-- Department -->
    <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1" Orientation="Horizontal">
        <Label Style="{StaticResource labelStyle}">Department:</Label>
        <Label Style="{StaticResource labelStyle}" Content="{Binding XPath=@Department}"></Label>
    </StackPanel>

    ```

     Powoduje to powiązanie kontrolek **etykiet** z odpowiednimi właściwościami źródła danych.

3. Dodaj następujący kod XAML wewnątrz elementu `<Grid>`:

    ```xaml
    <!--Templates to display expense report data-->
    <Grid.Resources>
        <!-- Reason item template -->
        <DataTemplate x:Key="typeItemTemplate">
            <Label Content="{Binding XPath=@ExpenseType}"/>
        </DataTemplate>
        <!-- Amount item template -->
        <DataTemplate x:Key="amountItemTemplate">
            <Label Content="{Binding XPath=@ExpenseAmount}"/>
        </DataTemplate>
    </Grid.Resources>

    ```

     Definiuje sposób wyświetlania danych raportu wydatków.

4. Zastąp element `<DataGrid>` następującym:

    ```xaml
    <!-- Expense type and Amount table -->
    <DataGrid ItemsSource="{Binding XPath=Expense}" ColumnHeaderStyle="{StaticResource columnHeaderStyle}" AutoGenerateColumns="False" RowHeaderWidth="0" >

        <DataGrid.Columns>
            <DataGridTextColumn Header="ExpenseType" Binding="{Binding XPath=@ExpenseType}"  />
            <DataGridTextColumn Header="Amount" Binding="{Binding XPath=@ExpenseAmount}" />
        </DataGrid.Columns>

    </DataGrid>
    ```

     Spowoduje to dodanie elementu **ustawieniem właściwości ItemSource** i zdefiniowanie powiązań dla elementów wydatków.

5. Skompiluj i uruchom aplikację.

6. Wybierz osobę, a następnie wybierz przycisk **Wyświetl** .

     Na poniższej ilustracji przedstawiono obie strony aplikacji ExpenseIt z kontrolkami, układem, stylami, powiązaniem danych i szablonami danych.

     ![Zrzuty ekranu przykładowego ExpenseIt](../designers/media/gettingstartedfigure5.png "GettingStartedFigure5")

## <a name="Best_Practices"></a>Najlepsze rozwiązania
 W tym przykładzie przedstawiono podstawowe informacje dotyczące platformy WPF i w związku z tym nie są zgodne z najlepszymi rozwiązaniami dotyczącymi tworzenia aplikacji. Aby uzyskać kompleksową obsługę technologii WPF i .NET Framework najlepszych rozwiązań dotyczących tworzenia aplikacji, zapoznaj się z następującymi tematami:

- Ułatwienia dostępu — [najlepsze rozwiązania dotyczące ułatwień dostępu](https://msdn.microsoft.com/library/aa350483\(v=vs.100\).aspx)

- Zabezpieczenia — [Windows Presentation Foundation zabezpieczenia](https://msdn.microsoft.com/library/aa970906\(v=vs.100\).aspx)

- Lokalizacja — [Omówienie globalizacji i lokalizacji platformy WPF](https://msdn.microsoft.com/library/ms788718\(v=vs.100\).aspx)

- Wydajność — [Optymalizacja wydajności aplikacji WPF](https://msdn.microsoft.com/library/aa970683\(v=vs.100\).aspx)

## <a name="Whats_Next"></a>Co dalej
 Masz teraz kilka technik do dyspozycji do tworzenia aplikacji klasycznych za pomocą platformy WPF. Należy teraz dysponować podstawową wiedzą na temat bloków konstrukcyjnych aplikacji WPF powiązanej z danymi. Ten temat nie jest dostępny w sposób wyczerpujący, ale miejmy nadzieję również pewne możliwości, które mogą zostać odnalezione przez użytkownika poza technikami w tym temacie.

 Aby uzyskać więcej informacji na temat architektury WPF i modeli programowania, zobacz następujące tematy:

- [Architektura WPF](https://msdn.microsoft.com/library/ms750441\(v=vs.100\).aspx)

- [Omówienie XAML](https://msdn.microsoft.com/library/ms752059\(v=vs.100\).aspx)

- [Przegląd właściwości zależności](https://msdn.microsoft.com/library/ms752914\(v=vs.100\).aspx)

- [Układ układu](https://msdn.microsoft.com/library/ms745058\(v=vs.100\).aspx)

- [Style i szablony](https://msdn.microsoft.com/library/bb613570\(v=vs.100\).aspx)

  Aby uzyskać więcej informacji na temat tworzenia aplikacji, zobacz następujące tematy:

- [Omówienie tworzenia aplikacji](https://msdn.microsoft.com/library/bb613549\(v=vs.100\).aspx)

- [Przegląd formantów](https://msdn.microsoft.com/library/bb613551\(v=vs.100\).aspx)

- [Powiązanie danych — omówienie](https://msdn.microsoft.com/library/ms752347\(v=vs.100\).aspx)

- [Przegląd grafiki, animacji i multimediów WPF](https://msdn.microsoft.com/library/ms742562\(v=vs.100\).aspx)

- [Dokumenty w WPF](https://msdn.microsoft.com/library/ms748388\(v=vs.100\).aspx)

## <a name="see-also"></a>Zobacz też
 [Przewodnik: Tworzenie aplikacji klasycznej WPF połączonej z usługą mobilną platformy Azure](../designers/walkthrough-create-a-wpf-desktop-application-connected-to-an-azure-mobile-service.md) [tworzenie nowoczesnych aplikacji klasycznych za pomocą Windows Presentation Foundation](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md)
