---
title: Tworzenie prostej aplikacji do danych za pomocą WPF i Entity Framework 6 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 65929fab-5d78-4e04-af1e-cf4957f230f6
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 403415eaf8a882efdd63fdb9a73b5489b91f2529
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651082"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Tworzenie prostej aplikacji do obsługi danych za pomocą platform WPF i Entity Framework 6
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym walkthough pokazano, jak utworzyć podstawową aplikację "Formularze danych" w programie Visual Studio z SQL Server LocalDB, bazą danych Northwind, Entity Framework 6 i Windows Presentation Foundation. Pokazano, jak wykonać podstawowe powiązania danych z widokiem wzorzec-szczegóły i ma także niestandardowy "Nawigator powiązań" z przyciskami "Przenieś dalej", "Przenieś poprzedni", "Przenieś do początku", "Przenieś do końca", "Update" i "Usuń".

 Ten artykuł koncentruje się na korzystaniu z narzędzi danych w programie Visual Studio i nie próbuje wyjaśnić podstawowych technologii na dowolnym poziomie. Przyjęto założenie, że masz podstawową wiedzę na temat języka XAML, Entity Framework i SQL. W tym przykładzie nie przedstawiono również architektury MVVM, która jest standardowa dla aplikacji WPF. Można jednak skopiować ten kod do własnej aplikacji MVVM przy użyciu nielicznych modyfikacji.

## <a name="install-and-connect-to-northwind"></a>Instalowanie programu Northwind i nawiązywanie z nim połączenia
 Ten przykład używa SQL Server Express LocalDB i przykładowej bazy danych Northwind. Należy również współpracować z innymi produktami usługi SQL Database, jeśli dostawca danych ADO.NET dla tego produktu obsługuje Entity Framework.

1. Jeśli jeszcze tego nie zrobiono, zainstaluj SQL Server 2014 LocalDB Express 32 bit na [stronie pobierania SQL Server wersje](https://www.microsoft.com/sql-server/sql-server-editions-express).

2. Zainstaluj przykładową bazę danych Northwind, postępując zgodnie z instrukcjami tutaj: [Install SQL Server Sample Bases](../data-tools/install-sql-server-sample-databases.md).

3. [Dodaj nowe połączenia](../data-tools/add-new-connections.md) dla Northwind.

## <a name="configure-the-project"></a>Konfigurowanie projektu

1. W programie Visual Studio wybierz **pozycję &#124; plik nowy projekt** , a następnie Utwórz C# nową aplikację WPF.

2. Następnie dodamy pakiet NuGet dla Entity Framework 6. W Eksplorator rozwiązań wybierz węzeł projektu. W menu głównym wybierz kolejno **pozycje &#124; projekt Zarządzaj pakietami NuGet...**

     ![Element menu Zarządzaj pakietami NuGet](../data-tools/media/raddata-vs2015-manage-nuget-packages.png "raddata_vs2015_manage_nuget_packages")

3. W Menedżerze pakietów NuGet kliknij link **Przeglądaj** . Najprawdopodobniej najwyższego pakietu na liście znajduje się Entity Framework. Kliknij przycisk **Instaluj** w okienku po prawej stronie i postępuj zgodnie z monitami. Okno dane wyjściowe informuje o zakończeniu instalacji.

     ![Entity Framework pakiet NuGet](../data-tools/media/raddata-vs2015-nuget-ef.png "raddata_vs2015_Nuget_EF")

4. Teraz możemy użyć programu Visual Studio do utworzenia modelu opartego na bazie danych Northwind.

## <a name="create-the-model"></a>Tworzenie modelu

1. Kliknij prawym przyciskiem myszy węzeł projektu w Eksplorator rozwiązań i wybierz polecenie  **&#124; Dodaj nowy element**. W lewym okienku w C# węźle wybierz pozycję **dane** , a następnie w środkowym okienku wybierz pozycję **ADO.NET Entity Data Model**.

    ![Nowy element projektu Entity Framework model](../data-tools/media/raddata-ef-new-project-item.png "raddata Dr — nowy element projektu")

2. Wywołaj model `Northwind_model` i wybierz przycisk OK. Spowoduje to wyświetlenie **kreatora Entity Data Model**. Wybierz opcję **Dr Designer z bazy danych** , a następnie kliknij przycisk **dalej**.

    ![Model EF z bazy danych](../data-tools/media/raddata-ef-model-from-database.png "Model raddata EF z bazy danych")

3. Na następnym ekranie wybierz połączenie LocalDB Northwind i kliknij przycisk **dalej**.

4. Na następnej stronie kreatora wybieramy tabele, procedury składowane i inne obiekty bazy danych, które mają być uwzględnione w modelu Entity Framework. Rozwiń węzeł dbo w widoku drzewa, a następnie wybierz pozycję Customers, Orders i Order Details. Pozostaw zaznaczone wartości domyślne i kliknij przycisk **Zakończ**.

    ![Wybierz obiekty bazy danych dla modelu](../data-tools/media/raddata-choose-ef-objects.png "raddata wybierz obiekty EF")

5. Kreator generuje C# klasy, które reprezentują model Entity Framework. Są to zwykłe stare C# klasy, które będą wiązać się z interfejsem użytkownika WPF. Plik. edmx opisuje relacje i inne metadane, które kojarzą klasy z obiektami w bazie danych.  Pliki. TT są szablonami T4, które generują kod, który będzie działać w modelu i zapisuje zmiany w bazie danych. Wszystkie te pliki można zobaczyć w Eksplorator rozwiązań w węźle Northwind_model:

    ![Eksplorator rozwiązań pliki modelu EF](../data-tools/media/raddata-solution-explorer-ef-model-files.png "raddata Eksplorator rozwiązań pliki modelu EF")

    Powierzchnia projektanta dla pliku. edmx umożliwia modyfikowanie niektórych właściwości i relacji w modelu. Nie będziemy używać projektanta w tym instruktażu.

6. Pliki. TT są ogólnego przeznaczenia i musimy dostosować jedną z nich do pracy z danymi DataBinding WPF, które wymagają ObservableCollections.  W Eksplorator rozwiązań rozwiń węzeł Northwind_model, dopóki nie znajdziesz Northwind_model. tt. (Upewnij się, że **nie** masz znaku *. Plik Context. TT, który znajduje się bezpośrednio poniżej pliku. edmx).

   - Zastąp dwa wystąpienia <xref:System.Collections.ICollection> z <xref:System.Collections.ObjectModel.ObservableCollection%601>.

   - Zastąp pierwsze wystąpienie <xref:System.Collections.Generic.HashSet%601> z <xref:System.Collections.ObjectModel.ObservableCollection%601> wokół wiersza 51. Nie zamieniaj drugiego wystąpienia elementu HashSet —

   - Zamień tylko wystąpienie <xref:System.Collections.Generic> (wokół wiersza 334) z <xref:System.Collections.ObjectModel>.

7. Naciśnij **kombinację klawiszy Ctrl + Shift + B** , aby skompilować projekt. Po zakończeniu kompilacji klasy modelu są widoczne dla Kreatora źródeł danych.

   Teraz możemy przystąpić do przyłączania tego modelu do strony XAML, aby można było wyświetlać, nawigować i modyfikować dane.

## <a name="databind-the-model-to-the-xaml-page"></a>Wywołaniu modelu na stronie XAML
 Istnieje możliwość napisania własnego kodu wiązania, ale znacznie łatwiej jest pozwolić programowi Visual Studio.

1. Z menu głównego wybierz polecenie **projekt &#124; Dodaj nowe źródło danych** , aby wyświetlić **Kreatora konfiguracji źródła danych**. Wybierz **obiekt** , ponieważ są wiązanie z klasami modelu, a nie z bazą danych:

     ![Kreator konfiguracji źródła danych z obiektem źródłowym](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png "Kreator konfiguracji źródła danych raddata z obiektem źródłowym")

2. Wybierz pozycję Klient.  (Źródła dla zamówień zostaną automatycznie wygenerowane na podstawie właściwości nawigacji Orders w kliencie).

     ![Dodawanie klas jednostek jako źródeł danych](../data-tools/media/raddata-add-entity-classes-as-data-sources.png "raddata Dodaj klasy jednostek jako źródła danych")

3. Kliknij przycisk **Zakończ** .

4. Przejdź do MainWindow. XAML w widoku kodu. Będziemy bardzo prostować kod XAML na potrzeby tego przykładu. Zmień tytuł MainWindow na coś bardziej opisowego i zwiększ jego wysokość i szerokość do 600 x 800. Zawsze możesz ją później zmienić. Teraz Dodaj te trzy definicje wierszy do siatki głównej, jeden wiersz dla przycisków nawigacji, jeden dla szczegółów klienta, jeden dla siatki, który pokazuje ich zamówienia:

    ```xaml
    <Grid.RowDefinitions>
               <RowDefinition Height="auto"/>
               <RowDefinition Height="auto"/>
               <RowDefinition Height="*"/>
           </Grid.RowDefinitions>
    ```

5. Teraz otwórz plik MainWindow. XAML, aby wyświetlić go w projektancie. Spowoduje to wyświetlenie okna źródła danych jako opcji w marginesie okna programu Visual Studio obok przybornika. Kliknij kartę, aby otworzyć okno, lub naciśnij klawisze **Shift + Alt + D** lub przycisk **Przeglądaj &#124; inne źródła danych systemu &#124; Windows**. Będziemy wyświetlać każdą właściwość w klasie Customers we własnym polu tekstowym. Najpierw kliknij strzałkę w polu kombi klienci i wybierz pozycję **szczegóły**. Następnie przeciągnij węzeł do środkowej części powierzchni projektowej, aby Projektant wiedział, że chce go umieścić w środkowym wierszu.  Jeśli go umieścisz, możesz określić wiersz ręcznie później w kodzie XAML. Domyślnie formanty są umieszczane w pionie w elemencie siatki, ale w tym momencie można je rozmieścić w formularzu.  Na przykład może być zrozumiałe umieszczenie pola tekstowego nazwa na górze, nad adresem. Przykładowa aplikacja w tym artykule zmienia kolejność pól i rozmieszcza je w dwóch kolumnach.

     ![Powiązanie źródła danych klientów z indywidualnymi kontrolkami](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png "powiązanie źródła danych klientów raddata z indywidualnymi kontrolkami")

     W widoku Kod można teraz zobaczyć nowy element `Grid` w wierszu 1 (środkowym wierszu) siatki nadrzędnej. Siatka nadrzędna ma atrybut `DataContext`, który odwołuje się do CollectionViewSource, który został dodany do elementu `Windows.Resources`. Uwzględniając ten kontekst danych, gdy pierwsze pole tekstowe, na przykład tworzy powiązanie z "Address", nazwa jest zamapowana na Właściwość `Address` w bieżącym obiekcie `Customer` w CollectionViewSource.

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6. Gdy klient jest widoczny w górnej połowie okna, chcemy zobaczyć swoje zamówienia w dolnej połowie. Pokażemy zamówienia w jednym formancie widoku siatki. Aby wiązania danych master-detail działały zgodnie z oczekiwaniami, ważne jest, aby utworzyć powiązanie z właściwością Orders w klasie Customers, a nie z osobnym węzłem Orders. Zwróć uwagę na poniższą ilustrację. Przeciągnij Właściwość Orders klasy Customers na niższą połowę formularza, aby Projektant umieści ją w wierszu 2:

     ![Przeciąganie klas zamówień jako siatki](../data-tools/media/raddata-drag-orders-classes-as-grid.png "raddata przeciąganie klas zamówień jako siatki")

7. Program Visual Studio wygenerował cały kod powiązania, który łączy kontrolki interfejsu użytkownika ze zdarzeniami w modelu. Aby można było wyświetlić pewne dane, należy napisać kod, aby wypełnić model. Najpierw przejdźmy do MainWindow.xaml.cs i Dodaj element członkowski danych do klasy MainWindow dla kontekstu danych. Ten obiekt, który został wygenerowany dla nas, działa podobnie jak kontrolka, która śledzi zmiany i zdarzenia w modelu. W tym miejscu dodamy dwa elementy członkowskie, których będziemy używać później, aby dodać nowy klient lub nowe zamówienie. Dodamy również logikę inicjowania konstruktora. Góra naszej klasy powinna wyglądać następująco:

    ```csharp
    public partial class MainWindow : Window
       {
           public Customer newCustomer { get; set; }
           public Order newOrder { get; set; }

           NorthwindEntities context = new NorthwindEntities();
           CollectionViewSource custViewSource;
           CollectionViewSource ordViewSource;

           public MainWindow()
           {
               InitializeComponent();
               newCustomer = new Customer();
               newOrder = new Order();
               custViewSource = ((CollectionViewSource)
                   (FindResource("customerViewSource")));
               ordViewSource = ((CollectionViewSource)
                   (FindResource("customerOrdersViewSource")));
               DataContext = this;
           }
    ```

     Dodaj dyrektywę `using` dla elementu System. Data. Entity, aby przenieść metodę rozszerzenia Load do zakresu:

    ```csharp
    using System.Data.Entity;
    ```

     Teraz przewiń w dół i Znajdź procedurę obsługi zdarzeń Window_Loaded. Zwróć uwagę, że program Visual Studio dodał do nas obiekt CollectionViewSource. Reprezentuje obiekt NorthwindEntities, który został wybrany podczas tworzenia modelu. Dodajmy kod do Window_loaded, dzięki czemu cała Metoda będzie wyglądać następująco:

    ```csharp
    private void Window_Loaded(object sender, RoutedEventArgs e)
        {
            // Load is an extension method on IQueryable,
            // defined in the System.Data.Entity namespace.
            // This method enumerates the results of the query,
            // similar to ToList but without creating a list.
            // When used with Linq to Entities this method
            // creates entity objects and adds them to the context.
            context.Customers.Load();

            // After the data is loaded call the DbSet<T>.Local property
            // to use the DbSet<T> as a binding source.
            custViewSource.Source = context.Customers.Local;
        }
    ```

8. Naciśnij klawisz **F5**. Należy zobaczyć szczegóły pierwszego klienta, który został pobrany do CollectionViewSource i ich zamówienia w siatce danych. Formatowanie nie jest doskonałe, dlatego należy rozwiązać ten problem. i podsumuje sposób wyświetlania innych rekordów i wykonywać podstawowe operacje CRUD.

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Dostosuj projekt strony i Dodaj siatki dla nowych klientów i zamówień
 Domyślne rozmieszczenie utworzone przez program Visual Studio nie jest idealne dla naszej aplikacji, więc wprowadzimy pewne zmiany ręcznie w kodzie XAML. Potrzebujemy również niektórych "formularzy" (które są w rzeczywistości siatkami), aby umożliwić użytkownikowi dodanie nowego klienta lub nowej kolejności.    Aby można było dodać nowego klienta i zamówienie, potrzebny jest oddzielny zestaw pól tekstowych, które nie są powiązane z `CollectionViewSource`. Będziemy kontrolować, którą siatkę widzi użytkownik w dowolnym momencie, ustawiając właściwość Visible w metodach obsługi.

 Na koniec dodamy przycisk usuwania do każdego wiersza w siatce Orders, aby umożliwić użytkownikowi usunięcie poszczególnych zamówień.

 Najpierw Dodaj te style do systemu Windows. zasoby:

```xaml
<Style x:Key="Label" TargetType="{x:Type Label}" BasedOn="{x:Null}">
    <Setter Property="HorizontalAlignment" Value="Left"/>
    <Setter Property="VerticalAlignment" Value="Center"/>
    <Setter Property="Margin" Value="3"/>
    <Setter Property="Height" Value="23"/>
</Style>
<Style x:Key="CustTextBox" TargetType="{x:Type TextBox}" BasedOn="{x:Null}">
    <Setter Property="HorizontalAlignment" Value="Right"/>
    <Setter Property="VerticalAlignment" Value="Center"/>
    <Setter Property="Margin" Value="3"/>
    <Setter Property="Height" Value="26"/>
    <Setter Property="Width" Value="120"/>
</Style>
```

 Następnie zastąp całą siatkę zewnętrzną tą adiustacją:

```xaml
<Grid >
     <Grid.RowDefinitions>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="*"/>
     </Grid.RowDefinitions>
     <StackPanel  Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">
         <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"  />
         <Button Name="btnPrev"  Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>
         <Button Name="btnNext"  Content="►" Command="{StaticResource NextCommand}"     Style="{StaticResource NavButton}"/>
         <Button Name="btnLast"  Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>
         <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>
         <Button  Name="btnAdd"   Content="New Customer"  Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
         <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>
         <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
         <Button Content="Cancel" Name="btnCancel"  Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
     </StackPanel>
     <Grid x:Name="existingCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" Margin="5" Visibility="Visible" VerticalAlignment="Top" Background="AntiqueWhite" DataContext="{StaticResource customerViewSource}">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="customerIDTextBox"  Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:"  Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="companyNameTextBox"  Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Name:"  Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Title:"  Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0"  Style="{StaticResource Label}"/>
         <TextBox x:Name="cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>
         <TextBox x:Name="postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <Grid x:Name="newCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding RelativeSource={RelativeSource FindAncestor, AncestorType={x:Type Window}}, Path=newCustomer, UpdateSourceTrigger=Explicit}" Visibility="Collapsed" Background="CornflowerBlue">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_customerIDTextBox"  Grid.Row="0"  Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:"  Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_companyNameTextBox"  Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true }"/>
         <Label Content="Contact Name:"  Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Title:"  Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0"  Style="{StaticResource Label}"/>
         <TextBox x:Name="add_cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <Grid x:Name="newOrderGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding Path=newOrder, Mode=TwoWay}" Visibility="Collapsed" Background="LightGreen">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="New Order Form" FontWeight="Bold"/>
         <Label Content="Employee ID:"  Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_employeeIDTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding EmployeeID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Order Date:"  Grid.Row="2" Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_orderDatePicker" Grid.Row="2"  HorizontalAlignment="Right" Width="120"
                 SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Required Date:" Grid.Row="3" Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_requiredDatePicker" Grid.Row="3" HorizontalAlignment="Right" Width="120"
                  SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Shipped Date:"  Grid.Row="4"  Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_shippedDatePicker"  Grid.Row="4"  HorizontalAlignment="Right" Width="120"
                 SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Ship Via:"  Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_ShipViaTextBox"  Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding ShipVia, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Freight"  Grid.Row="6" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_freightTextBox" Grid.Row="6" Style="{StaticResource CustTextBox}"
                  Text="{Binding Freight, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <DataGrid x:Name="ordersDataGrid" SelectionUnit="Cell" SelectionMode="Single" AutoGenerateColumns="False" CanUserAddRows="false" IsEnabled="True" EnableRowVirtualization="True" Width="auto" ItemsSource="{Binding Source={StaticResource customerOrdersViewSource}}" Margin="10,10,10,10" Grid.Row="2" RowDetailsVisibilityMode="VisibleWhenSelected">
         <DataGrid.Columns>
             <DataGridTemplateColumn>
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <Button Content="Delete"  Command="{StaticResource DeleteOrderCommand}" CommandParameter="{Binding}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="customerIDColumn" Binding="{Binding CustomerID}" Header="Customer ID" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="employeeIDColumn" Binding="{Binding EmployeeID}" Header="Employee ID" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="freightColumn" Binding="{Binding Freight}" Header="Freight" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="orderDateColumn" Header="Order Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="orderIDColumn" Binding="{Binding OrderID}" Header="Order ID" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="requiredDateColumn" Header="Required Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="shipAddressColumn" Binding="{Binding ShipAddress}" Header="Ship Address" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipCityColumn" Binding="{Binding ShipCity}" Header="Ship City" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipCountryColumn" Binding="{Binding ShipCountry}" Header="Ship Country" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipNameColumn" Binding="{Binding ShipName}" Header="Ship Name" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="shippedDateColumn" Header="Shipped Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="shipPostalCodeColumn" Binding="{Binding ShipPostalCode}" Header="Ship Postal Code" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipRegionColumn" Binding="{Binding ShipRegion}" Header="Ship Region" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipViaColumn" Binding="{Binding ShipVia}" Header="Ship Via" Width="SizeToHeader"/>
         </DataGrid.Columns>
     </DataGrid>
 </Grid>
```

## <a name="add-buttons-to-navigate-add-update-and-delete"></a>Dodawanie przycisków do nawigowania, dodawania, aktualizowania i usuwania
 W Windows Forms aplikacje otrzymujesz obiekt BindingNavigator z przyciskami służącymi do nawigowania po wierszach w bazie danych i wykonywania podstawowych operacji CRUD. Funkcja WPF nie udostępnia elementu BindingNavigator, ale jest za mało do wprowadzenia. Będziemy wykonywać te działania z przyciskami wewnątrz poziome StackPanel w dolnym wierszu siatki stron i kojarzą przyciski z poleceniami, które są powiązane z metodami w kodzie.

 Istnieją cztery części do logiki poleceń: (1) polecenia, (2) powiązania, (3) przyciski i (4) programy obsługi poleceń w kodzie.

#### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Dodawanie poleceń, powiązań i przycisków w języku XAML

1. Po pierwsze Dodajmy polecenia do pliku MainWindow. XAML w elemencie Windows. Resources:

    ```xaml

     <RoutedUICommand x:Key="FirstCommand" Text="First"/>
    <RoutedUICommand x:Key="LastCommand" Text="Last"/>
    <RoutedUICommand x:Key="NextCommand" Text="Next"/>
    <RoutedUICommand x:Key="PreviousCommand" Text="Previous"/>
    <RoutedUICommand x:Key="DeleteCustomerCommand" Text="Delete Customer"/>
    <RoutedUICommand x:Key="DeleteOrderCommand" Text="Delete Order"/>
    <RoutedUICommand x:Key="UpdateCommand" Text="Update"/>
    <RoutedUICommand x:Key="AddCommand" Text="Add"/>
    <RoutedUICommand x:Key="CancelCommand" Text="Cancel"/>
    ```

2. Poleceniebinding mapuje zdarzenie RoutedUICommand na metodę w kodzie. Dodaj ten element CommandBindings po tagu zamykającym Windows. Resources:

    ```xaml

        <Window.CommandBindings>
        <CommandBinding Command="{StaticResource FirstCommand}" Executed="FirstCommandHandler"/>
        <CommandBinding Command="{StaticResource LastCommand}" Executed="LastCommandHandler"/>
        <CommandBinding Command="{StaticResource NextCommand}" Executed="NextCommandHandler"/>
        <CommandBinding Command="{StaticResource PreviousCommand}" Executed="PreviousCommandHandler"/>
        <CommandBinding Command="{StaticResource DeleteCustomerCommand}" Executed="DeleteCustomerCommandHandler"/>
        <CommandBinding Command="{StaticResource DeleteOrderCommand}" Executed="DeleteOrderCommandHandler"/>
        <CommandBinding Command="{StaticResource UpdateCommand}" Executed="UpdateCommandHandler"/>
        <CommandBinding Command="{StaticResource AddCommand}" Executed="AddCommandHandler"/>
        <CommandBinding Command="{StaticResource CancelCommand}" Executed="CancelCommandHandler"/>
    </Window.CommandBindings>
    ```

3. Teraz Dodajmy StackPanel za pomocą przycisków nawigacji, dodawania, usuwania i aktualizowania. Najpierw Dodaj ten styl do systemu Windows. zasoby:

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     Teraz wklej ten kod tuż po RowDefinitions dla elementu zewnętrzna Siatka w górnej części strony XAML:

    ```xaml
    <StackPanel  Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"  />
        <Button Name="btnPrev"  Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnNext"  Content="►" Command="{StaticResource NextCommand}"     Style="{StaticResource NavButton}"/>
        <Button Name="btnLast"  Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>
        <Button  Name="btnAdd"   Content="New Customer"  Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>
        <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="Cancel" Name="btnCancel"  Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
    </StackPanel>
    ```

#### <a name="add-command-handlers-to-the-mainwindow-class"></a>Dodawanie programów obsługi poleceń do klasy MainWindow

1. Kod źródłowy jest minimalny z wyjątkiem metod dodawania i usuwania. Należy zauważyć, że nawigacja jest wykonywana przez wywoływanie metod we właściwości widoku CollectionViewSource. DeleteOrderCommandHandler pokazuje, jak wykonać kaskadowe usuwanie w kolejności. Musimy najpierw usunąć Order_Details, które są z nim skojarzone. UpdateCommandHandler dodaje nowego klienta do kolekcji lub po prostu aktualizuje istniejący obiekt o wszelkie zmiany wprowadzone przez użytkownika w polach tekstowych.

2. Dodaj te metody obsługi do klasy MainWindow w MainWindow.xaml.cs, jeśli CollectionViewSource dla tabeli Customers ma inną nazwę, należy dostosować nazwę w każdej z tych metod:

    ```csharp
       private void LastCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        custViewSource.View.MoveCurrentToLast();
    }

    private void PreviousCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        custViewSource.View.MoveCurrentToPrevious();
    }

    private void NextCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        custViewSource.View.MoveCurrentToNext();
    }

    private void FirstCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        custViewSource.View.MoveCurrentToFirst();
    }

    private void DeleteCustomerCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        // If existing window is visible, then delete the customer and all their orders.
        // In a real application, you should add warnings and allow a user to cancel the operation.
        var cur = custViewSource.View.CurrentItem as Customer;

        var cust = (from c in context.Customers
                    where c.CustomerID == cur.CustomerID
                    select c).FirstOrDefault();

        if (cust != null)
        {
            foreach (var ord in cust.Orders.ToList())
            {
                Delete_Order(ord);
            }
            context.Customers.Remove(cust);
        }
        context.SaveChanges();
        custViewSource.View.Refresh();
    }

    // Commit changes from the new customer form, the new order form,
    // or edits made to the existing customer form.
    private void UpdateCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        if (newCustomerGrid.IsVisible)
        {
            // Create a new object because the old one
            // is being tracked by EF now.
            newCustomer = new Customer();
            newCustomer.Address = add_addressTextBox.Text;
            newCustomer.City = add_cityTextBox.Text;
            newCustomer.CompanyName = add_companyNameTextBox.Text;
            newCustomer.ContactName = add_contactNameTextBox.Text;
            newCustomer.ContactTitle = add_contactTitleTextBox.Text;
            newCustomer.Country = add_countryTextBox.Text;
            newCustomer.CustomerID = add_customerIDTextBox.Text;
            newCustomer.Fax = add_faxTextBox.Text;
            newCustomer.Phone = add_phoneTextBox.Text;
            newCustomer.PostalCode = add_postalCodeTextBox.Text;
            newCustomer.Region = add_regionTextBox.Text;

            // Perform very basic validation
            if (newCustomer.CustomerID.Length == 5)
            {
                // Insert the new customer at correct position:
                int len = context.Customers.Local.Count();
                int pos = len;
                for (int i = 0; i < len; ++i)
                {
                    if (String.CompareOrdinal(newCustomer.CustomerID, context.Customers.Local[i].CustomerID) < 0)
                    {
                        pos = i;
                        break;
                    }
                }
                context.Customers.Local.Insert(pos, newCustomer);
                custViewSource.View.Refresh();
                custViewSource.View.MoveCurrentTo(newCustomer);
            }
            else
            {
                MessageBox.Show("CustomerID must have 5 characters.");
            }

            newCustomerGrid.Visibility = Visibility.Collapsed;
            existingCustomerGrid.Visibility = Visibility.Visible;
        }
        else if (newOrderGrid.IsVisible)
        {
            // Order ID is auto-generated so we don't set it here.
            // For CustomerID, address, etc we use the values from current customer.
            // User can modify these in the datagrid after the order is entered.

            newOrder.OrderDate = add_orderDatePicker.SelectedDate;
            newOrder.RequiredDate = add_requiredDatePicker.SelectedDate;
            newOrder.ShippedDate = add_shippedDatePicker.SelectedDate;
            try
            {
                // Exercise for the reader if you are using Northwind:
                // Add the Northwind Shippers table to the model.
                // Acceptable ShipperID values are 1, 2, or 3.
                if (add_ShipViaTextBox.Text == "1" || add_ShipViaTextBox.Text == "2"
                    || add_ShipViaTextBox.Text == "3")
                {
                    newOrder.ShipVia = Convert.ToInt32(add_ShipViaTextBox.Text);
                }
                else
                {
                    MessageBox.Show("Shipper ID must be 1, 2, or 3 in Northwind.");
                    return;
                }
            }
            catch
            {
                MessageBox.Show("Ship Via must be convertible to int");
                return;
            }
            try
            {
                newOrder.Freight = Convert.ToDecimal(add_freightTextBox.Text);
            }
            catch
            {
                MessageBox.Show("Freight must be convertible to decimal.");
                return;
            }

            // Add the order into the EF model
            context.Orders.Add(newOrder);
            ordViewSource.View.Refresh();
        }

        // Save the changes, either for a new customer, a new order
        // or an edit in an existing customer or order
        context.SaveChanges();
    }

    // Sets up the form so that user can enter data. Data is later
    // saved when user clicks Commit.
    private void AddCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        existingCustomerGrid.Visibility = Visibility.Collapsed;
        newOrderGrid.Visibility = Visibility.Collapsed;
        newCustomerGrid.Visibility = Visibility.Visible;

        // Clear all the text boxes before adding a new customer.
        foreach (var child in newCustomerGrid.Children)
        {
            var tb = child as TextBox;
            if (tb != null)
            {
                tb.Text = "";
            }
        }
    }

    private void NewOrder_click(object sender, RoutedEventArgs e)
    {
        var cust = custViewSource.View.CurrentItem as Customer;
        if (cust == null)
        {
            MessageBox.Show("No customer selected.");
            return;
        }

        newOrder.CustomerID = cust.CustomerID;

        // Get address and other mostly constant fields from
        // an existing order, if one exists
        var coll = custViewSource.Source as IEnumerable<Customer>;
        var lastOrder = (from c in coll
                         from ord in c.Orders
                         select ord).LastOrDefault();
        if (lastOrder != null)
        {
            newOrder.ShipAddress = lastOrder.ShipAddress;
            newOrder.ShipCity = lastOrder.ShipCity;
            newOrder.ShipCountry = lastOrder.ShipCountry;
            newOrder.ShipName = lastOrder.ShipName;
            newOrder.ShipPostalCode = lastOrder.ShipPostalCode;
            newOrder.ShipRegion = lastOrder.ShipRegion;
        }

        existingCustomerGrid.Visibility = Visibility.Collapsed;
        newCustomerGrid.Visibility = Visibility.Collapsed;
        newOrderGrid.UpdateLayout();
        newOrderGrid.Visibility = Visibility.Visible;
    }

    // Cancels any input into the new customer form
    private void CancelCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        add_addressTextBox.Text = "";
        add_cityTextBox.Text = "";
        add_companyNameTextBox.Text = "";
        add_contactNameTextBox.Text = "";
        add_contactTitleTextBox.Text = "";
        add_countryTextBox.Text = "";
        add_customerIDTextBox.Text = "";
        add_faxTextBox.Text = "";
        add_phoneTextBox.Text = "";
        add_postalCodeTextBox.Text = "";
        add_regionTextBox.Text = "";

        existingCustomerGrid.Visibility = Visibility.Visible;
        newCustomerGrid.Visibility = Visibility.Collapsed;
        newOrderGrid.Visibility = Visibility.Collapsed;
    }

    private void Delete_Order(Order order)
    {
        // Find the order in the EF model.
        var ord = (from o in context.Orders.Local
                   where o.OrderID == order.OrderID
                   select o).FirstOrDefault();

        // Delete all the order_details that have
        // this Order as a foreign key
        foreach (var detail in ord.Order_Details.ToList())
        {
            context.Order_Details.Remove(detail);
        }

        // Now it's safe to delete the order.
        context.Orders.Remove(ord);
        context.SaveChanges();

        // Update the data grid.
        ordViewSource.View.Refresh();
    }

    private void DeleteOrderCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        // Get the Order in the row in which the Delete button was clicked.
        Order obj = e.Parameter as Order;
        Delete_Order(obj);
    }
    ```

3. Naciśnij klawisz **F5**. Powinny być widoczne Twoje dane, a przyciski nawigacji powinny funkcjonować zgodnie z oczekiwaniami. Kliknij pozycję "Zatwierdź", aby dodać nowego klienta lub zamówienie do modelu po wprowadzeniu danych.  Kliknij przycisk "Anuluj", aby wycofać się z nowego klienta lub formularz nowej kolejności bez zapisywania. Można wprowadzać zmiany do istniejących klientów i zamówień bezpośrednio w polach tekstowych, a ich zmiana zostanie zapisywana automatycznie w modelu.

## <a name="see-also"></a>Zobacz też
 Dokumentacja programu [Visual Studio Data Tools for .net](../data-tools/visual-studio-data-tools-for-dotnet.md) [Entity Framework](https://msdn.microsoft.com/data/ee712907.aspx)
