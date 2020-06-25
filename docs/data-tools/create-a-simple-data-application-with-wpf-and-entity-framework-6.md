---
title: Prosta aplikacja danych z WPF i Entity Framework 6
ms.date: 08/22/2017
ms.topic: conceptual
dev_langs:
- CSharp
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4aa978098c459d9e55ef0dc1423080357e067a5b
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282764"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Tworzenie prostej aplikacji do obsługi danych za pomocą platform WPF i Entity Framework 6

W tym instruktażu pokazano, jak utworzyć podstawową aplikację "formularze dla danych" w programie Visual Studio. Aplikacja używa SQL Server LocalDB, bazy danych Northwind, Entity Framework 6 (nie Entity Framework Core) i Windows Presentation Foundation dla .NET Framework (nie .NET Core). Pokazano, jak wykonać podstawowe powiązania danych z widokiem wzorzec-szczegóły i ma także niestandardowy Nawigator powiązań z przyciskami **Przenieś dalej**, **Przenieś poprzedni**, **Przenieś na początek**, **Przenieś do końca**, **Aktualizuj** i **Usuń**.

Ten artykuł koncentruje się na korzystaniu z narzędzi danych w programie Visual Studio i nie próbuje wyjaśnić podstawowych technologii na dowolnym poziomie. Przyjęto założenie, że masz podstawową wiedzę na temat języka XAML, Entity Framework i SQL. W tym przykładzie nie przedstawiono również architektury Model-View-ViewModel (MVVM), która jest standardowa dla aplikacji WPF. Można jednak skopiować ten kod do własnej aplikacji MVVM przy użyciu kilku modyfikacji.

## <a name="install-and-connect-to-northwind"></a>Instalowanie programu Northwind i nawiązywanie z nim połączenia

Ten przykład używa SQL Server Express LocalDB i przykładowej bazy danych Northwind. Jeśli dostawca danych ADO.NET dla tego produktu obsługuje Entity Framework, powinien również działać z innymi produktami usługi SQL Database.

1. Jeśli nie masz SQL Server Express LocalDB, zainstaluj go na [stronie pobierania SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)lub za pośrednictwem **Instalator programu Visual Studio**. W **Instalator programu Visual Studio**można zainstalować SQL Server Express LocalDB w ramach obciążeń **programistycznych programu .NET Desktop** lub pojedynczego składnika.

2. Zainstaluj przykładową bazę danych Northwind, wykonując następujące kroki:

    1. W programie Visual Studio Otwórz okno **Eksplorator obiektów SQL Server** . (**Eksplorator obiektów SQL Server** jest instalowany jako część obciążenia **magazynu i przetwarzania danych** w **Instalator programu Visual Studio**). Rozwiń węzeł **SQL Server** . Kliknij prawym przyciskiem myszy wystąpienie LocalDB i wybierz pozycję **nowe zapytanie**.

       Zostanie otwarte okno edytora zapytań.

    2. Skopiuj [skrypt języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt T-SQL tworzy bazę danych Northwind od podstaw i wypełnia ją danymi.

    3. Wklej skrypt T-SQL do edytora zapytań, a następnie wybierz przycisk Execute ( **Wykonaj** ).

       Po krótkim czasie zapytanie kończy działanie i zostanie utworzona baza danych Northwind.

3. [Dodaj nowe połączenia](../data-tools/add-new-connections.md) dla Northwind.

## <a name="configure-the-project"></a>Konfigurowanie projektu

1. W programie Visual Studio Utwórz nowy projekt **aplikacji WPF** w języku C#.

2. Dodaj pakiet NuGet dla Entity Framework 6. W **Eksplorator rozwiązań**wybierz węzeł projektu. W menu głównym wybierz kolejno pozycje **projekt**  >  **Zarządzaj pakietami NuGet**.

     ![Element menu Zarządzaj pakietami NuGet](../data-tools/media/raddata_vs2015_manage_nuget_packages.png)

3. W **Menedżerze pakietów NuGet**kliknij link **Przeglądaj** . Najprawdopodobniej najwyższego pakietu na liście znajduje się Entity Framework. Kliknij przycisk **Instaluj** w okienku po prawej stronie i postępuj zgodnie z monitami. Okno dane wyjściowe informuje o zakończeniu instalacji.

     ![Entity Framework pakiet NuGet](../data-tools/media/raddata_vs2015_nuget_ef.png)

4. Teraz można użyć programu Visual Studio do utworzenia modelu opartego na bazie danych Northwind.

## <a name="create-the-model"></a>Tworzenie modelu

1. Kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**  >  **nowy element**. W lewym okienku w węźle C# wybierz pozycję **dane** , a następnie w środkowym okienku wybierz pozycję **ADO.NET Entity Data Model**.

   ![Nowy element modelu Entity Framework](../data-tools/media/raddata-ef-new-project-item.png)

2. Wywołaj model `Northwind_model` i wybierz **przycisk OK**. Zostanie otwarty **kreator Entity Data Model** . Wybierz opcję **Dr Designer z bazy danych** , a następnie kliknij przycisk **dalej**.

   ![Model EF z bazy danych](../data-tools/media/raddata-ef-model-from-database.png)

3. Na następnym ekranie wprowadź lub wybierz swoje połączenie LocalDB Northwind (na przykład (LocalDB) \MSSQLLocalDB), określ bazę danych Northwind, a następnie kliknij przycisk **dalej**.

4. Na następnej stronie kreatora wybierz tabele, procedury składowane i inne obiekty bazy danych, które mają być uwzględnione w modelu Entity Framework. Rozwiń węzeł dbo w widoku drzewa, a następnie wybierz pozycję **Customers**, **Orders**i **Order Details**. Pozostaw zaznaczone wartości domyślne i kliknij przycisk **Zakończ**.

    ![Wybierz obiekty bazy danych dla modelu](../data-tools/media/raddata-choose-ef-objects.png)

5. Kreator generuje klasy języka C#, które reprezentują model Entity Framework. Klasy to zwykłe stare klasy C# i są to elementy, które są używane do interfejsu użytkownika WPF. Plik *. edmx* opisuje relacje i inne metadane, które kojarzą klasy z obiektami w bazie danych. Pliki *. tt* są szablonami T4, które generują kod, który działa w modelu i zapisuje zmiany w bazie danych. Wszystkie te pliki można zobaczyć w **Eksplorator rozwiązań** w węźle Northwind_model:

      ![Eksplorator rozwiązań pliki modelu EF](../data-tools/media/raddata-solution-explorer-ef-model-files.png)

    Powierzchnia projektanta dla pliku *. edmx* umożliwia modyfikowanie niektórych właściwości i relacji w modelu. Nie będziemy używać projektanta w tym instruktażu.

6. Pliki *. tt* są ogólnego przeznaczenia i należy dostosować jeden z nich do pracy z danymi DataBinding WPF, które wymagają ObservableCollections. W **Eksplorator rozwiązań**rozwiń węzeł Northwind_model do momentu znalezienia *Northwind_model. tt*. (Upewnij się, że nie jesteś w *. Plik Context.tt* , który znajduje się bezpośrednio poniżej pliku *. edmx* .

   - Zastąp dwa wystąpienia elementu <xref:System.Collections.ICollection> <xref:System.Collections.ObjectModel.ObservableCollection%601> .

   - Zastąp pierwsze wystąpienie <xref:System.Collections.Generic.HashSet%601> z <xref:System.Collections.ObjectModel.ObservableCollection%601> wokół wiersza 51. Nie zamieniaj drugiego wystąpienia HashSet —.

   - Zamień tylko wystąpienie <xref:System.Collections.Generic> (wokół wiersza 431) na <xref:System.Collections.ObjectModel> .

7. Naciśnij **klawisze CTRL** + **SHIFT** + **B** , aby skompilować projekt. Po zakończeniu kompilacji klasy modelu są widoczne dla Kreatora źródeł danych.

Teraz możesz przystąpić do przyłączania tego modelu do strony XAML, aby można było wyświetlać, nawigować i modyfikować dane.

## <a name="databind-the-model-to-the-xaml-page"></a>Wywołaniu modelu na stronie XAML

Istnieje możliwość napisania własnego kodu wiązania, ale znacznie łatwiej jest pozwolić programowi Visual Studio.

1. Z menu głównego wybierz polecenie **projekt**  >  **Dodaj nowe źródło danych** , aby wyświetlić **Kreatora konfiguracji źródła danych**. Wybierz **obiekt** , ponieważ tworzysz powiązania z klasami modelu, a nie z bazą danych:

     ![Kreator konfiguracji źródła danych z obiektem źródłowym](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png)

2. Rozwiń węzeł projektu, a następnie wybierz pozycję **Klient**. (Źródła dla zamówień są generowane automatycznie na podstawie właściwości nawigacji Orders w kliencie).

     ![Dodawanie klas jednostek jako źródeł danych](../data-tools/media/raddata-add-entity-classes-as-data-sources.png)

3. Kliknij przycisk **Zakończ**.

4. Przejdź do *MainWindow. XAML* w widoku kodu. Zachowujemy prostą XAML na potrzeby tego przykładu. Zmień tytuł MainWindow na coś bardziej opisowego i zwiększ jego wysokość i szerokość do 600 x 800. Zawsze możesz ją później zmienić. Teraz Dodaj te trzy definicje wierszy do siatki głównej, jeden wiersz dla przycisków nawigacji, jeden dla szczegółów klienta i jeden dla siatki, który pokazuje ich zamówienia:

    ```xaml
        <Grid.RowDefinitions>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
    ```

5. Teraz otwórz plik *MainWindow. XAML* , aby wyświetlić go w projektancie. Powoduje to wyświetlenie okna **źródła danych** jako opcji w marginesie okna programu Visual Studio obok **przybornika**. Kliknij kartę, aby otworzyć okno, lub naciśnij klawisze **SHIFT** + **Alt** + **D** lub przycisk **Przeglądaj**  >  **inne**  >  **źródła danych**systemu Windows. Będziemy wyświetlać każdą właściwość w klasie Customers we własnym polu tekstowym. Najpierw kliknij strzałkę w polu kombi **klienci** i wybierz pozycję **szczegóły**. Następnie przeciągnij węzeł do środkowej części powierzchni projektowej, aby Projektant wiedział, że chce go umieścić w środkowym wierszu. Jeśli go umieścisz, możesz określić wiersz ręcznie później w kodzie XAML. Domyślnie formanty są umieszczane w pionie w elemencie siatki, ale w tym momencie można je rozmieścić w formularzu. Na przykład może być zrozumiałe umieszczenie pola tekstowego **Nazwa** na górze, nad adresem. Przykładowa aplikacja w tym artykule zmienia kolejność pól i rozmieszcza je w dwóch kolumnach.

     ![Powiązanie źródła danych klientów z indywidualnymi kontrolkami](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png)

     W widoku Kod można teraz zobaczyć nowy `Grid` element w wierszu 1 (środkowym wierszu) siatki nadrzędnej. Siatka nadrzędna ma `DataContext` atrybut, który odwołuje się do CollectionViewSource, który został dodany do `Windows.Resources` elementu. Uwzględniając ten kontekst danych, gdy pierwsze pole tekstowe wiąże się z **adresem**, ta nazwa jest mapowana na `Address` Właściwość w bieżącym `Customer` obiekcie w CollectionViewSource.

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6. Gdy klient jest widoczny w górnej połowie okna, chcesz zobaczyć swoje zamówienia w dolnej połowie. Zamówienia są wyświetlane w jednym formancie widoku siatki. Aby wiązania danych master-detail działały zgodnie z oczekiwaniami, ważne jest, aby utworzyć powiązanie z właściwością Orders w klasie Customers, a nie z osobnym węzłem Orders. Przeciągnij Właściwość Orders klasy Customers na niższą połowę formularza, aby Projektant umieści ją w wierszu 2:

     ![Przeciąganie klas zamówień jako siatki](../data-tools/media/raddata-drag-orders-classes-as-grid.png)

7. Program Visual Studio wygenerował cały kod powiązania, który łączy kontrolki interfejsu użytkownika ze zdarzeniami w modelu. Wszystko, co musisz zrobić, aby zobaczyć pewne dane, napisanie kodu w celu wypełnienia modelu. Najpierw przejdź do *MainWindow.XAML.cs* i Dodaj element członkowski danych do klasy MainWindow dla kontekstu danych. Ten obiekt, który został wygenerowany dla Ciebie, działa podobnie jak kontrolka, która śledzi zmiany i zdarzenia w modelu. Dodasz również do CollectionViewSource członków danych dla klientów i zamówień oraz logiki inicjalizacji skojarzonego konstruktora. Góra klasy powinna wyglądać następująco:

     [!code-csharp[MainWindow#1](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#1)]

     Dodaj `using` dyrektywę dla elementu System. Data. Entity, aby przenieść metodę rozszerzenia Load do zakresu:

     ```csharp
     using System.Data.Entity;
     ```

     Teraz przewiń w dół i Znajdź `Window_Loaded` procedurę obsługi zdarzeń. Zwróć uwagę, że program Visual Studio dodał obiekt CollectionViewSource. Reprezentuje obiekt NorthwindEntities, który został wybrany podczas tworzenia modelu. Dodano już ten element, więc nie potrzebujesz go tutaj. Zastąp kod w, `Window_Loaded` Aby Metoda teraz wyglądała następująco:

     [!code-csharp[Window_Loaded#2](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#2)]

8. Naciśnij klawisz **F5**. Powinny zostać wyświetlone szczegóły pierwszego klienta, który został pobrany do CollectionViewSource. W siatce danych powinny również być widoczne ich zamówienia. Formatowanie nie jest doskonałe, dlatego należy rozwiązać ten problem. Można również utworzyć sposób wyświetlania innych rekordów i wykonywać podstawowe operacje CRUD.

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Dostosuj projekt strony i Dodaj siatki dla nowych klientów i zamówień

Domyślne rozmieszczenie utworzone przez program Visual Studio nie jest idealnym rozwiązaniem dla aplikacji, dlatego w tym miejscu będzie dostępny końcowy kod XAML umożliwiający skopiowanie do kodu. Potrzebne są również niektóre "formularze" (w rzeczywistości siatki) umożliwiające użytkownikowi dodanie nowego klienta lub zamówienia. Aby można było dodać nowego klienta i zamówienie, potrzebny jest oddzielny zestaw pól tekstowych, które nie są powiązane z danymi `CollectionViewSource` . Należy określić, która siatka będzie widoczna dla użytkownika w dowolnym momencie, ustawiając właściwość Visible w metodach obsługi. Na koniec Dodaj przycisk usuwania do każdego wiersza w siatce Orders (zamówienia), aby umożliwić użytkownikowi usunięcie poszczególnych zamówień.

Najpierw Dodaj te style do `Windows.Resources` elementu w *MainWindow. XAML*:

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
<Grid>
     <Grid.RowDefinitions>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="*"/>
     </Grid.RowDefinitions>
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
         <TextBox x:Name="customerIDTextBox" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="companyNameTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Name:" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact title:" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0" Style="{StaticResource Label}"/>
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
         <TextBox x:Name="add_customerIDTextBox" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_companyNameTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true }"/>
         <Label Content="Contact Name:" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact title:" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0" Style="{StaticResource Label}"/>
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
                         <Button Content="Delete" Command="{StaticResource DeleteOrderCommand}" CommandParameter="{Binding}"/>
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

W Windows Forms aplikacje otrzymujesz obiekt BindingNavigator z przyciskami służącymi do nawigowania po wierszach w bazie danych i wykonywania podstawowych operacji CRUD. Funkcja WPF nie udostępnia elementu BindingNavigator, ale jest to bardzo proste, aby go utworzyć. Można to zrobić za pomocą przycisków wewnątrz poziome StackPanel i skojarzyć przyciski z poleceniami, które są powiązane z metodami w kodzie.

Istnieją cztery części logiki poleceń: (1) polecenia, (2) powiązania, (3) przyciski i (4) programy obsługi poleceń w kodzie.

### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Dodawanie poleceń, powiązań i przycisków w języku XAML

1. Najpierw Dodaj polecenia w pliku *MainWindow. XAML* wewnątrz `Windows.Resources` elementu:

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

2. Poleceniebinding mapuje `RoutedUICommand` zdarzenie do metody w kodzie. Dodaj ten `CommandBindings` element po `Windows.Resources` tagu zamykającym:

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

3. Teraz Dodaj `StackPanel` przyciski nawigacyjne, Dodawanie, usuwanie i aktualizowanie. Najpierw Dodaj ten styl do `Windows.Resources` :

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     Następnie wklej ten kod tuż po `RowDefinitions` elemencie dla elementu zewnętrznego w `Grid` kierunku górnej części strony XAML:

    ```xaml
    <StackPanel Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnPrev" Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnNext" Content="►" Command="{StaticResource NextCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnLast" Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>
        <Button Name="btnAdd" Content="New Customer" Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>
        <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="Cancel" Name="btnCancel" Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
    </StackPanel>
    ```

### <a name="add-command-handlers-to-the-mainwindow-class"></a>Dodawanie programów obsługi poleceń do klasy MainWindow

Kod źródłowy jest minimalny z wyjątkiem metod dodawania i usuwania. Nawigacja jest wykonywana przez wywoływanie metod we właściwości widoku CollectionViewSource. `DeleteOrderCommandHandler`Pokazuje, jak wykonać kaskadowe usuwanie w kolejności. Musimy najpierw usunąć Order_Details, które są z nim skojarzone. `UpdateCommandHandler`Dodaje nowego klienta lub zamówienie do kolekcji lub po prostu aktualizuje istniejącego klienta lub zamówienie ze zmianami wprowadzonymi przez użytkownika w polach tekstowych.

Dodaj te metody obsługi do klasy MainWindow w *MainWindow.XAML.cs*. Jeśli CollectionViewSource dla tabeli Customers ma inną nazwę, należy dostosować nazwę w każdej z tych metod:

[!code-csharp[CommandHandlers#3](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#3)]

## <a name="run-the-application"></a>Uruchamianie aplikacji

Aby rozpocząć debugowanie, naciśnij klawisz **F5**. Powinny pojawić się dane klienta i zamówienia wypełnione w siatce, a przyciski nawigacji powinny funkcjonować zgodnie z oczekiwaniami. Kliknij przycisk **Zatwierdź** , aby dodać nowego klienta lub zamówienie do modelu po wprowadzeniu danych. Kliknij przycisk **Anuluj** , aby wycofać się z nowego klienta lub formularza nowego zamówienia bez zapisywania danych. Można wprowadzać zmiany w istniejących klientach i zamówieniach bezpośrednio w polach tekstowych i są one automatycznie zapisywane w modelu.

## <a name="see-also"></a>Zobacz też

- [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Dokumentacja Entity Framework](/ef/)
