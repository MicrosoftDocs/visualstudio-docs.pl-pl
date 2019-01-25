---
title: 'Przewodnik: Mój pierwszy Aplikacja2 pulpitu WPF | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 3c460fa9-2ea1-413f-ae54-54a1f2a499d1
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3607bac8d8cd9808a54e4c8956b3c4d41df8aecb
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54795948"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>Przewodnik: Mój pierwszy aplikacji klasycznej WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

name = "wprowadzenie" ></a> ten przewodnik zawiera wprowadzenie do programowania Windows Presentation Foundation (WPF). Utworzysz Podstawowa aplikacja, która zawiera elementy, które są wspólne dla większości aplikacji klasycznej WPF: Znaczników XAML związanym z kodem, definicji aplikacji, formanty, układ, powiązanie danych i stylów.  
  
##  <a name="Create_The_Application_Code_Files"></a> Tworzenie projektu aplikacji  
 W tej sekcji utworzysz infrastruktury aplikacji, która zawiera projekt i okna głównego lub formularza.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
1.  Na pasku menu wybierz **pliku**, **New**, **projektu**.  
  
2.  W **nowy projekt** okna dialogowego, rozwiń węzeł **Visual C#** lub **języka Visual Basic** węzeł i wybierz polecenie **Windows** węzła, a następnie rozwiń węzeł **Windows** węzeł i wybierz polecenie **Classic Desktop** węzła.  
  
3.  Na liście szablonów wybierz **aplikacji WPF** szablonu.  
  
4.  W **nazwa** polu tekstowym wprowadź `ExpenseIt`, a następnie wybierz **OK** przycisku.  
  
     Projekt zostanie utworzony i pliki projektu zostaną dodane do **Eksploratora rozwiązań**i Projektant dla domyślnego okna aplikacji o nazwie **MainWindow.xaml** jest wyświetlana.  
  
#### <a name="to-modify-the-main-window"></a>Aby zmodyfikować okna głównego  
  
1.  W projektancie, wybierz **MainWindow.xaml** kartę, jeśli nie jest już aktywną kartę projektanta.  
  
2.  Jeśli używasz języka C#, znajdź wiersz `<Window x:Class="ExpenseIt.MainWindow"` i zastąp go wartością `<NavigationWindow x:Class="ExpenseIt.MainWindow"`.  
  
     Jeśli używasz języka Visual Basic, znajdź wiersz `<Window x:Class=" MainWindow"` i zastąp go wartością `<NavigationWindow x:Class="MainWindow"`.  
  
     Należy zauważyć, że po zmianie `<Window` tag `<NavigationWindow`, technologia Intellisense automatycznie zmieni tag zamykający do `</NavigationWindow>` także.  
  
    > [!NOTE]
    >  Po zmianie znacznika, jeśli **lista błędów** jest otwarte okno możesz zauważyć kilka błędów. Nie martw się — zmiany wprowadzone w ciągu następnych kilku krokach spowoduje, że te go natychmiast.  
  
3.  Wybierz `<Grid>` i `</Grid>` tagów i usuń je.  
  
     A **NavigationWindow** nie mogą zawierać inne elementy interfejsu użytkownika, takie jak **siatki**.  
  
4.  W **właściwości** okna, rozwiń węzeł **typowe** węzeł kategorii i wybierz polecenie **tytuł** właściwości, a następnie wprowadź `ExpenseIt` i naciśnij klawisz **Enter**  klucza.  
  
     Należy zauważyć, że **tytuł** element w oknie XAML zmieni się na pasowała do nowej wartości. Można zmodyfikować właściwości XAML w oknie XAML lub **właściwości** okna, a zmiany są synchronizowane.  
  
5.  W oknie XAML, ustaw wartość **wysokość** elementu `375`i ustaw wartość **szerokość** właściwość `500`.  
  
     Te elementy odnoszą się do **wysokość** i **szerokość** występują właściwości **układ** kategorii **właściwości** okna.  
  
     Twoje **MainWindow.xaml** plik powinien teraz wyglądać następująco w języku C#:  
  
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
  
     Lub tak jak poniżej w języku Visual Basic:  
  
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
  
#### <a name="to-modify-the-code-behind-file-c"></a>Modyfikowanie pliku związanego z kodem (C#)  
  
1.  W **Eksploratora rozwiązań**, rozwiń węzeł **MainWindow.xaml** węzła i Otwórz **MainWindow.xaml.cs** pliku.  
  
2.  Znajdź wiersz `public partial class MainWindow : Window` i zastąp go wartością `public partial class MainWindow : NavigationWindow`.  
  
     Spowoduje to zmianę `MainWindow` pochodzi od klasy `NavigationWindow`. W języku Visual Basic to odbywa się automatycznie po zmianie okna w XAML, bez zmian w kodzie jest zbędny.  
  
##  <a name="add_files_to_the_application"></a> Dodawanie plików do aplikacji  
 W tej sekcji należy dodać dwie strony i obrazu do aplikacji.  
  
#### <a name="to-add-a-home-screen"></a>Aby dodać ekran domowy  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla **programu ExpenseIt** węzeł i wybierz polecenie **Dodaj**, **strony**.  
  
2.  W **Dodaj nowy element** okno dialogowe, wybierz **nazwa** tekst i wpisz `ExpenseItHome`, a następnie wybierz **Dodaj** przycisku.  
  
     Ta strona jest pierwsze okno, które jest wyświetlane, gdy aplikacja zostanie uruchomiona.  
  
3.  W projektancie, wybierz **ExpenseItHome.xaml** kartę, jeśli nie jest już aktywną kartę projektanta.  
  
4.  Wybierz `<Title>` elementu i Zmień tytuł na **programu ExpenseIt — strona główna**.  
  
     Twoje **ExpenseItHome.xaml** plik powinien teraz wyglądać następująco w języku C#:  
  
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
  
     Lub tak jak poniżej w języku Visual Basic:  
  
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
  
5.  W projektancie, wybierz **MainWindow.xaml** kartę.  
  
6.  Znajdź wiersz `Title="ExpenseIt" Height="375" Width="500">` elementu i Dodaj `Source="ExpenseItHome.xaml"` właściwości.  
  
     To ustawienie **ExpenseItHome.xaml** jako pierwsza strona otwarty podczas uruchamiania aplikacji. Twoje **MainWindow.xaml** plik powinien teraz wyglądać następująco w języku C#:  
  
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
  
     Lub tak jak poniżej w języku Visual Basic:  
  
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
  
     Za pomocą właściwości, które zostały ustawione wcześniej, można mieć po ustawieniu `Source` właściwość **różne** kategorii **właściwości** okna.  
  
#### <a name="to-add-a-details-window"></a>Aby dodać okno Szczegóły  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla **programu ExpenseIt** węzeł i wybierz polecenie **Dodaj**, **strony**.  
  
2.  W **Dodaj nowy element** okno dialogowe, wybierz **nazwa** tekst i wpisz `ExpenseReportPage`, a następnie wybierz **Dodaj** przycisku.  
  
     W tym oknie będą wyświetlane raportu wydatków indywidualnych.  
  
3.  W projektancie, wybierz **ExpenseReportPage.xaml** kartę, jeśli nie jest już aktywną kartę projektanta.  
  
4.  Wybierz `<Title>` elementu i Zmień tytuł na **programu ExpenseIt — widok wydatków**.  
  
     Plik ExpenseReportPage.xaml powinien teraz wyglądać następująco w języku C#:  
  
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
  
     Lub tak jak poniżej w języku Visual Basic:  
  
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
  
5.  Na pasku menu wybierz **debugowania**, **Rozpocznij debugowanie** (lub naciśnij klawisz F5) do uruchamiania aplikacji.  
  
     Na poniższej ilustracji przedstawiono aplikację za pomocą przycisków nawigacyjnych okna.  
  
     ![Zrzut ekranu przedstawiający przykładowy programu ExpenseIt](../designers/media/gettingstartedfigure1.png "GettingStartedFigure1")  
  
6.  Zamknij aplikację, aby powrócić do trybu projektowania.  
  
##  <a name="Add_Layout"></a> Tworzenie interfejsu użytkownika  
 Układ zapewnia uporządkowany sposób umieszczania elementów, a także zarządza rozmiar i położenie tych elementów, gdy zmieniany jest rozmiar formularza. W tej sekcji utworzysz siatki jedna kolumna z trzema wierszami. Będzie dodać formanty do dwóch stronach, dodawanie kodu i na koniec zdefiniuj wielokrotnego użytku stylów dla kontrolki.  
  
#### <a name="to-create-the-layout"></a>Aby utworzyć układ  
  
1.  Otwórz **ExpenseItHome.xaml** i wybierz polecenie `<Grid>` elementu.  
  
2.  W **właściwości** okna, rozwiń węzeł **układ** węzeł kategorii i ustaw **margines** wartości `10`, `10`, `0`i `10`, która odnosi się do lewej, po prawej stronie, górny i dolny marginesy.  
  
     Element `Margin="10,0,10,10"` jest dodawany do `<Grid>` elementu w XAML. Jeszcze raz można wprowadzono te wartości bezpośrednio w kodzie XAML, a nie w **właściwości** okno z takiego samego wyniku.  
  
3.  Dodaj następujący kod XAML, aby `Grid` elementu do utworzenia definicji wierszy i kolumn:  
  
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
  
#### <a name="to-add-controls"></a>Aby dodać formanty  
  
1.  Otwórz **ExpenseItHome.xaml**.  
  
2.  Dodaj następujący kod XAML tuż nad `</Grid>` tag, aby utworzyć `Border`, `ListBox` i `Button` kontrolki.  
  
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
  
     Należy zauważyć, że formanty są wyświetlane w oknie projektu. Można również utworzono kontrolki, przeciągając je z **przybornika** okna na oknie projektowania i ustawiania ich właściwości w **właściwości** okna.  
  
3.  Skompiluj i uruchom aplikację. Poniższa ilustracja przedstawia wyglądu kontrolki, które są tworzone przez XAML w tej procedurze w czasie wykonywania.  
  
     ![Zrzut ekranu przedstawiający przykładowy programu ExpenseIt](../designers/media/gettingstartedfigure2.png "GettingStartedFigure2")  
  
4.  Zamknij aplikację, aby powrócić do trybu projektowania.  
  
#### <a name="to-add-a-background-image"></a>Aby dodać obraz tła  
  
1.  Wybierz następujące obrazu i zapisz go jako `watermark.png`.  
  
     ![Obraz znaku wodnego przewodnik](../designers/media/wpf-watermark.png "WPF_watermark")  
  
    > [!NOTE]
    >  Alternatywnie można utworzyć własny obraz i zapisz go jako `watermark.png`.  
  
2.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla **programu ExpenseIt** węzeł i wybierz polecenie **Dodaj**, **istniejący element**.  
  
3.  W **Dodaj istniejący element** okno dialogowe, Znajdź **watermark.png** obraz, który właśnie został dodany, wybierz go, a następnie wybierz **Dodaj** przycisku.  
  
    > [!NOTE]
    >  Może być konieczne rozszerzenie **typów plików** i wybierz polecenie **pliki obrazów**.  
  
4.  Otwórz **ExpenseItHome.xaml** pliku i Dodaj następujący kod XAML tuż nad `</Grid>` tag, aby utworzyć obraz tła:  
  
    ```xaml  
    <Grid.Background>  
        <ImageBrush ImageSource="watermark.png"/>  
    </Grid.Background>  
  
    ```  
  
#### <a name="to-add-a-title"></a>Aby dodać tytuł  
  
1.  Otwórz **ExpenseItHome.xaml**.  
  
2.  Znajdź wiersz `<Grid.ColumnDefinitions>` i dodaj następujące po prostu poniżej:  
  
    ```xaml  
    <ColumnDefinition Width="230" />  
  
    ```  
  
     Spowoduje to utworzenie dodatkową kolumnę na lewo od innych kolumn o stałej szerokości 230 pikseli.  
  
3.  Znajdź wiersz `<Grid.RowDefinitions>` i dodaj następujące po prostu poniżej:  
  
    ```xaml  
    <RowDefinition />  
  
    ```  
  
     Spowoduje to dodanie wiersza do początku siatki.  
  
4.  Przenieś kontrolki do drugiej kolumny, ustawiając `Grid.Column` wartości 1. Przenieś każdy formant wiersz w dół, zwiększając każdego `Grid.Row` wartość o 1.  
  
    1.  Znajdź wiersz `<Border Grid.Column="0" Grid.Row="0" Height="35" Padding="5" Background="#4E87D4">`. Zmień `Grid.Column="0"` do `Grid.Column="1"` i zmień `Grid.Row="0"` do `Grid.Row="1"`.  
  
    2.  Znajdź wiersz `<ListBox Name="peopleListBox" Grid.Column="0" Grid.Row="1"`. Zmień `Grid.Column="0"` do `Grid.Column="1"` i zmień `Grid.Row="1"` do `Grid.Row="2"`.  
  
    3.  Znajdź wiersz `<Button Grid.Column="0" Grid.Row="2" Margin="0,10,0,0" Width="125"`. Zmień `Grid.Column="0"` do `Grid.Column="1"` i zmień `Grid.Row="2"` do `Grid.Row="3"`.  
  
5.  Tuż przed `<Border` element Dodaj następujący kod XAML, aby wyświetlić tytuł:  
  
    ```xaml  
    <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"   
            FontWeight="Bold" FontSize="18" Foreground="#0066cc">  
        View Expense Report  
    </Label>  
  
    ```  
  
     Zawartość **ExpenseItHome.xaml** powinien teraz wyglądać następująco w języku C#:  
  
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
  
     Lub tak jak poniżej w języku Visual Basic:  
  
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
  
6.  Jeśli utworzysz i uruchomić aplikację na tym etapie, powinno to wyglądać podobnie do poniższej ilustracji:  
  
     ![Zrzut ekranu przedstawiający przykładowy programu ExpenseIt](../designers/media/gettingstartedfigure3.png "GettingStartedFigure3")  
  
#### <a name="to-add-code-to-the-button"></a>Aby dodać kod do przycisku  
  
1.  Otwórz **ExpenseItHome.xaml**.  
  
2.  Wybrana opcja `<Button` elementu i Dodaj następujący kod XAML natychmiast po **HorizontalAlignment = "Right"** element: `Click="Button_Click"`.  
  
     Spowoduje to dodanie obsługi zdarzeń dla przycisku `Click` zdarzeń. **< Przycisk** element kod powinien teraz wyglądać następująco:  
  
    ```  
    <!-- View report button -->  
      <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125"  
    Height="25" HorizontalAlignment="Right" Click="Button_Click">View</Button>  
    ```  
  
3.  Otwórz **ExpenseItHome.xaml.cs** lub **ExpenseItHome.xaml.vb** pliku.  
  
4.  Dodaj następujący kod do `ExpenseItHome` klasy:  
  
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
  
     Ta procedura obsługi zdarzeń zostanie otwarta strona raportu wydatków po kliknięciu przycisku.  
  
#### <a name="to-create-the-ui-for-the-report-page"></a>Do tworzenia interfejsu użytkownika dla strony raportu  
  
1.  Otwórz **ExpenseReportPage.xaml**.  
  
     Tej strony wyświetli raportu wydatków dla osób, które wybrano na stronie głównej.  
  
2.  Dodaj następujący kod XAML między `<Grid>` i `</Grid>` tagi:  
  
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
  
     Ten interfejs jest podobny do Interfejsu, który został utworzony dla strony głównej, ale dane raportu są wyświetlane w **DataGrid** kontroli.  
  
3.  Skompiluj i uruchom aplikację.  
  
4.  Wybierz **widoku** przycisku.  
  
     Zostanie wyświetlona strona raportu wydatków.  
  
     Poniższa ilustracja przedstawia strony raportu wydatków. Należy zauważyć, że zostanie włączony przycisk przeglądania do tyłu.  
  
     ![Zrzut ekranu przedstawiający przykładowy programu ExpenseIt](../designers/media/gettingstartedfigure4.png "GettingStartedFigure4")  
  
#### <a name="to-style-controls"></a>Style formantów  
  
1.  Otwórz **App.xaml** pliku (C#) lub **Application.xaml** pliku (Visual Basic).  
  
2.  Dodaj następujące XAML między `<Application.Resources>` i `</Application.Resources>` tagi:  
  
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
  
     Ta XAML dodaje następujące style:  
  
    -   `headerTextStyle`: Aby sformatować tytuł strony `Label`.  
  
    -   `labelStyle`: Aby sformatować `Label` kontrolki.  
  
    -   `columnHeaderStyle`: Aby sformatować `DataGridColumnHeader`.  
  
    -   `listHeaderStyle`: Aby sformatować nagłówek listy `Border` kontrolki.  
  
    -   `listHeaderTextStyle`: Aby sformatować nagłówek listy **etykiety**.  
  
    -   `buttonStyle`: Aby sformatować `Button` na **ExpenseItHome.xaml** pppage.  
  
3.  Otwórz **ExpenseItHome.xaml** i Zamień wszystko pomiędzy `<Grid>` i `</Grid>` elementów za pomocą następujących XAML  
  
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
  
     Właściwości, takie jak `VerticalAlignment` i `FontFamily` definiują wygląd każdego formantu usunięty i zastąpiony, stosując style.  
  
4.  Otwórz **ExpenseReportPage.xaml** i Zamień wszystko pomiędzy `<Grid>` i końcowe `</Grid>` elementów za pomocą następujących XAML  
  
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
  
     Spowoduje to dodanie stylów `<Label>` i `<Border>` elementów.  
  
## <a name="connecting-to-data"></a>Łączenie z danymi  
 W tej sekcji będzie Tworzenie szablonu danych i dostawcę danych, a następnie połącz formantów do wyświetlania danych.  
  
#### <a name="to-bind-data-to-a-control"></a>Aby powiązać dane z kontrolką  
  
1.  Otwórz **ExpenseItHome.xaml** i wybierz polecenie `<Grid>` element...  
  
2.  Dodaj następujący kod XAML:  
  
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
  
     Ten kod tworzy `XmlDataProvider` klasy, która zawiera dane dla każdej osoby. Zwykle to będą ładowane jako plik, ale dla uproszczenia dane są dodawane na tekście.  
  
3.  Wewnątrz `<Grid.Resources>` elementu, Dodaj następujący kod XAML:  
  
    ```xaml  
    <!-- Name item template -->  
    <DataTemplate x:Key="nameItemTemplate">  
        <Label Content="{Binding XPath=@Name}"/>  
    </DataTemplate>  
    ```  
  
     Spowoduje to dodanie `Data Template` definiujący sposób wyświetlania danych w **ListBox**.  
  
4.  Zastąp istniejące `<ListBox>` element z następujących XAML.  
  
    ```xaml  
    <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2"   
             ItemsSource="{Binding Source={StaticResource ExpenseDataSource}, XPath=Person}"  
             ItemTemplate="{StaticResource nameItemTemplate}">  
    </ListBox>  
    ```  
  
     Kod ten powiąże `ItemsSource` właściwość `ListBox` ze źródłem danych i stosuje szablon danych jako `ItemTemplate`.  
  
#### <a name="to-connect-data-to-controls"></a>Aby połączyć danych z kontrolkami  
  
1.  Otwórz **ExpenseReportPage.xaml.vb** lub **ExpenseReportPage.xaml.cs**.  
  
2.  W języku C#, Dodaj następujący Konstruktor do **ExpenseReportPage** klasy lub w języku Visual Basic należy zastąpić istniejącej klasy następującym kodem:  
  
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
  
     Ten konstruktor przyjmuje obiekt danych jako parametr. W tym przypadku obiekt danych będzie zawierać nazwę wybranego użytkownika.  
  
3.  Otwórz **ExpenseItHome.xaml.vb** lub **ExpenseItHome.xaml.cs**.  
  
4.  Zastąp `Click` kod obsługi zdarzeń w następującym kodem:  
  
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
  
1.  Otwórz **ExpenseReportPage.xaml**.  
  
2.  Zastąp kod XAML dla **nazwa** i **działu** `<StackPanel` elementy następującym kodem:  
  
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
  
     Powoduje to powiązanie **etykiety** kontrolki do właściwości źródła danych.  
  
3.  Dodaj następujący kod XAML wewnątrz `<Grid>` elementu:  
  
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
  
4.  Zastąp `<DataGrid>` element następującym kodem:  
  
    ```xaml  
    <!-- Expense type and Amount table -->  
    <DataGrid ItemsSource="{Binding XPath=Expense}" ColumnHeaderStyle="{StaticResource columnHeaderStyle}" AutoGenerateColumns="False" RowHeaderWidth="0" >  
  
        <DataGrid.Columns>  
            <DataGridTextColumn Header="ExpenseType" Binding="{Binding XPath=@ExpenseType}"  />  
            <DataGridTextColumn Header="Amount" Binding="{Binding XPath=@ExpenseAmount}" />  
        </DataGrid.Columns>  
  
    </DataGrid>  
    ```  
  
     Spowoduje to dodanie **właściwości ItemSource** i definiuje powiązania dla elementów wydatków.  
  
5.  Skompiluj i uruchom aplikację.  
  
6.  Wybierz osobę, a następnie wybierz **widoku** przycisku.  
  
     Poniższa ilustracja przedstawia obie strony aplikacji programu ExpenseIt formanty, układ, style, powiązanie danych i zastosowanych szablonów danych.  
  
     ![Przykładowe zrzuty ekranu programu ExpenseIt](../designers/media/gettingstartedfigure5.png "GettingStartedFigure5")  
  
##  <a name="Best_Practices"></a> Najlepsze rozwiązania  
 W tym przykładzie przedstawiono podstawy WPF, a w związku z tym, nie jest zgodna z najlepszych rozwiązań projektowania aplikacji. Aby uzyskać kompleksowe informacje na temat WPF i .NET Framework stosowanie najlepszych rozwiązań programistycznych zobacz następujące tematy, zgodnie z potrzebami:  
  
-   Dostępność — [najlepsze rozwiązania w zakresie ułatwień dostępu](https://msdn.microsoft.com/library/aa350483\(v=vs.100\).aspx)  
  
-   Zabezpieczenia — [zabezpieczeń programu Windows Presentation Foundation](https://msdn.microsoft.com/library/aa970906\(v=vs.100\).aspx)  
  
-   Lokalizacja — [Przegląd lokalizacja i globalizacja WPF](https://msdn.microsoft.com/library/ms788718\(v=vs.100\).aspx)  
  
-   Wydajność — [Optymalizacja wydajności aplikacji WPF](https://msdn.microsoft.com/library/aa970683\(v=vs.100\).aspx)  
  
##  <a name="Whats_Next"></a> Jaka jest przyszłość  
 Masz teraz kilka technik do dyspozycji użytkownika służący do tworzenia klasycznych aplikacji za pomocą WPF. Teraz powinien mieć podstawową wiedzę na temat bloki konstrukcyjne aplikacji WPF powiązane z danymi. W tym temacie w żadnym wypadku nie jest wyczerpująca, ale miejmy nadzieję teraz również mają strukturę niektóre z możliwości, których można wykryć na własną rękę poza techniki przedstawione w tym temacie.  
  
 Aby uzyskać więcej informacji o modelach programowania i architektura WPF zobacz następujące tematy:  
  
- [Architektura WPF](https://msdn.microsoft.com/library/ms750441\(v=vs.100\).aspx)  
  
- [XAML — omówienie](https://msdn.microsoft.com/library/ms752059\(v=vs.100\).aspx)  
  
- [Przegląd właściwości zależności](https://msdn.microsoft.com/library/ms752914\(v=vs.100\).aspx)  
  
- [System układu](https://msdn.microsoft.com/library/ms745058\(v=vs.100\).aspx)  
  
- [Style i szablony](https://msdn.microsoft.com/library/bb613570\(v=vs.100\).aspx)  
  
  Aby uzyskać więcej informacji na temat tworzenia aplikacji zobacz następujące tematy:  
  
- [Omówienie tworzenia aplikacji](https://msdn.microsoft.com/library/bb613549\(v=vs.100\).aspx)  
  
- [Omówienie kontrolek](https://msdn.microsoft.com/library/bb613551\(v=vs.100\).aspx)  
  
- [Powiązanie danych — omówienie](https://msdn.microsoft.com/library/ms752347\(v=vs.100\).aspx)  
  
- [Przegląd Media, animacje i grafiki WPF](https://msdn.microsoft.com/library/ms742562\(v=vs.100\).aspx)  
  
- [Dokumenty w WPF](https://msdn.microsoft.com/library/ms748388\(v=vs.100\).aspx)  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Tworzenie aplikacji WPF pulpitu podłączone do usługi mobilnej Azure](../designers/walkthrough-create-a-wpf-desktop-application-connected-to-an-azure-mobile-service.md)   
 [Tworzenie nowoczesnych aplikacji klasycznych przy użyciu platformy Windows Presentation Foundation](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md)
