---
title: Tworzenie prostej aplikacji danych przy użyciu platformy WPF i Entity Framework 6
ms.date: 08/22/2017
ms.topic: conceptual
dev_langs:
- CSharp
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 0febbf31dcf9f0ae1e7a4e47dae2e9cf3d291dbf
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55909170"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Tworzenie prostej aplikacji danych przy użyciu platformy WPF i Entity Framework 6

W tym instruktażu przedstawiono sposób tworzenia aplikacji w języku basic "formularzy nad danymi" w programie Visual Studio. Aplikacja używa programu SQL Server LocalDB, bazy danych Northwind, platformy Entity Framework 6 i Windows Presentation Foundation. Pokazano, jak wykonać podstawowe powiązanie danych z widokiem wzorzec / szczegół i ma on także niestandardowe Nawigator powiązania za pomocą przycisków dla **Przenieś następny**, **Przenieś poprzednie**, **Przenieś na początek**, **Przenieś na koniec**, **aktualizacji** i **Usuń**.

Ten artykuł koncentruje się na użyciu narzędzia danych programu Visual Studio i nie jest podejmowana próba wyjaśnić podstawowej technologii, w dowolnym poziomie. Przyjęto założenie, że masz podstawowe znajomość XAML, platformy Entity Framework i SQL. W tym przykładzie również nie przedstawiono tu architektury Model-View-ViewModel (MVVM), który jest standardem dla aplikacji WPF. Jednak możesz skopiować ten kod do własnych aplikacji MVVM o kilka zmian.

## <a name="install-and-connect-to-northwind"></a>Instalacja i nawiązywanie Northwind

W tym przykładzie użyto programu SQL Server Express LocalDB i przykładowej bazy danych Northwind. Jeśli dostawcy danych ADO.NET dla danego produktu obsługuje platformy Entity Framework, jego powinny współpracować z innymi produktami do bazy danych SQL równie dobrze.

1.  Jeśli nie masz programu SQL Server Express LocalDB, zainstaluj go z [stronę pobierania programu SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), lub za pomocą **Instalatora programu Visual Studio**. W **Instalatora programu Visual Studio**, można zainstalować programu SQL Server Express LocalDB, jako część **programowanie aplikacji klasycznych dla platformy .NET** obciążenia lub jako poszczególnych składników.

2.  Instalowanie przykładowej bazy danych Northwind, wykonaj następujące czynności:

    1. W programie Visual Studio, otwórz **Eksplorator obiektów SQL Server** okna. (**Eksplorator obiektów SQL Server** jest instalowany jako część **przechowywanie i przetwarzanie danych** obciążenie w **Instalatora programu Visual Studio**.) Rozwiń **programu SQL Server** węzła. Kliknij prawym przyciskiem myszy w ramach wystąpienia LocalDB, a następnie wybierz pozycję **nowe zapytanie**.

       Zostanie otwarte okno edytora zapytań.

    2. Kopiuj [skryptów języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt języka T-SQL tworzy bazę danych Northwind od podstaw i wypełnia ją z danymi.

    3. Wklej skrypt języka T-SQL do edytora zapytań, a następnie wybierz **Execute** przycisku.

       Po pewnym czasie odliczania zapytania i utworzeniu bazy danych Northwind.

3.  [Dodaj nowe połączenia](../data-tools/add-new-connections.md) dla Northwind.

## <a name="configure-the-project"></a>Konfigurowanie projektu

1.  W programie Visual Studio, wybierz **pliku** > **New** > **projektu** , a następnie utwórz nową C# aplikacji WPF.

2.  Następnie dodaj pakiet NuGet dla platformy Entity Framework 6. W **Eksploratora rozwiązań**, wybierz węzeł projektu. W menu głównym wybierz **projektu** > **Zarządzaj pakietami NuGet**.

     ![Zarządzanie pakietami NuGet elementu menu](../data-tools/media/raddata_vs2015_manage_nuget_packages.png)

3.  W **Menedżera pakietów NuGet**, kliknij pozycję **Przeglądaj** łącza. Entity Framework jest prawdopodobnie pakiet na liście. Kliknij przycisk **zainstalować** w okienku po prawej stronie i postępuj zgodnie z monitami. W oknie danych wyjściowych informuje, kiedy instalacja się zakończy.

     ![Pakiet NuGet programu Entity Framework](../data-tools/media/raddata_vs2015_nuget_ef.png)

4.  Teraz można użyć programu Visual Studio, aby utworzyć model na podstawie bazy danych Northwind.

## <a name="create-the-model"></a>Tworzenie modelu

1. Kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj** > **nowy element**. W okienku po lewej stronie w obszarze C# węzła, wybierz **danych** i w środkowym okienku wybierz **ADO.NET Entity Data Model**.

   ![Entity Framework modelu nowy element projektu](../data-tools/media/raddata-ef-new-project-item.png)

2. Wywoływanie modelu `Northwind_model` i wybierz polecenie **OK**. **Kreator modelu Entity Data Model** zostanie otwarty. Wybierz **projektancie platformy EF z bazy danych** a następnie kliknij przycisk **dalej**.

   ![Modelu platformy EF z bazy danych](../data-tools/media/raddata-ef-model-from-database.png)

3. Na następnym ekranie Wybierz połączenie i kliknij pozycję usługi LocalDB Northwind **dalej**.

4. Na następnej stronie kreatora wybierz tabele, procedury składowane i innych obiektów bazy danych, które mają zostać objęte modelu Entity Framework. Rozwiń węzeł dbo w widoku drzewa i wybierz polecenie **klientów**, **zamówienia**, i **Orderdetails**. Pozostaw wartości domyślne, zaznaczone, a następnie kliknij przycisk **Zakończ**.

    ![Wybierz obiekty bazy danych dla modelu](../data-tools/media/raddata-choose-ef-objects.png)

5. Kreator generuje klas języka C#, które reprezentują model Entity Framework. Klasy są plain old C# klasy są one efekcie powiązań danych interfejsu użytkownika WPF. *Edmx* pliku w tym artykule opisano relacje i inne metadane, które kojarzy klas obiektów w bazie danych. *.Tt* pliki są szablony T4, które generują kod, który działa na podstawie modelu, a następnie zapisz zmiany w bazie danych. Widzisz wszystkie te pliki w **Eksploratora rozwiązań** w węźle Northwind_model:

      ![Pliki modelu EF Eksploratora rozwiązań](../data-tools/media/raddata-solution-explorer-ef-model-files.png)

    Powierzchni projektanta dla *edmx* plik umożliwia modyfikowanie niektórych właściwości i relacje w modelu. Nie będziemy korzystać z projektanta, w tym przewodniku.

6. *.Tt* pliki są ogólnego przeznaczenia i musisz dostosować jeden z nich do pracy z powiązanie danych WPF, która wymaga ObservableCollections. W **Eksploratora rozwiązań**, rozwiń węzeł Northwind_model, aż znajdziesz *Northwind_model.tt*. (Upewnij się, że nie jesteś w *. Context.TT* pliku, który jest bezpośrednio poniżej *edmx* pliku.)

   -   Zastąp dwa wystąpienia <xref:System.Collections.ICollection> z <xref:System.Collections.ObjectModel.ObservableCollection%601>.

   -   Zamień na pierwsze wystąpienie <xref:System.Collections.Generic.HashSet%601> z <xref:System.Collections.ObjectModel.ObservableCollection%601> całym wierszu 51. Nie zastępuj drugie wystąpienie hashset —.

   -   Zastąpić tylko wystąpienie <xref:System.Collections.Generic> (około wiersza 431) przy użyciu <xref:System.Collections.ObjectModel>.

7. Naciśnij klawisz **Ctrl**+**Shift**+**B** do skompilowania projektu. Po zakończeniu kompilacji, klasy modelu są widoczne w Kreatorze źródła danych.

Teraz możesz przystąpić do podpiąć tego modelu do strony XAML, aby wyświetlić, przejdź i modyfikować dane.

## <a name="databind-the-model-to-the-xaml-page"></a>Elementu DataBind modelu do strony XAML

Można napisać własny kod wiązania danych, ale jest znacznie łatwiejsze umożliwić programowi Visual Studio zrobił dla Ciebie.

1.  W menu głównym wybierz **projektu** > **Dodaj nowe źródło danych** aby przywołać **Kreatora konfiguracji źródła danych**. Wybierz **obiektu** ponieważ dokonywane jest wiązanie dla klasy modelu nie do bazy danych:

     ![Kreator konfiguracji źródła danych z obiektu źródłowego](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png)

2.  Wybierz **klienta**. (Źródeł dla zamówienia są automatycznie generowane z właściwości nawigacji zamówień klientów).

     ![Dodawanie klas jednostek jako źródła danych](../data-tools/media/raddata-add-entity-classes-as-data-sources.png)

3.  Kliknij przycisk **Zakończ**.

4.  Przejdź do *MainWindow.xaml* w widoku kodu. XAML utrzymujemy prostotę na potrzeby tego przykładu. Zmienianie tytułu MainWindow na bardziej opisową i zwiększenie jego wysokości i szerokości do 600 x 800 teraz. Można zawsze zmienić go później. Teraz należy dodać te definicje trzech wierszy do głównej siatki, jeden wiersz przycisków nawigacji, jeden dla szczegóły klienta i w siatce, która pokazuje jego zamówienia:

    ```xaml
    <Grid.RowDefinitions>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
    ```

5.  Teraz Otwórz *MainWindow.xaml* tak, że jest wyświetlana w projektancie. Powoduje to, że **źródeł danych** okna, aby opcja pojawia się na marginesie okna programu Visual Studio obok **przybornika**. Kliknij kartę, aby otworzyć okno lub inne naciśnij **Shift**+**Alt**+**D** lub wybierz **widoku**  >  **Innych Windows** > **źródeł danych**. Użyjemy do wyświetlania każdej właściwości w klasie klientów w jego własnej poszczególnych tekst. Po pierwsze, kliknąć strzałkę w **klientów** kombi pole, a następnie wybierz **szczegóły**. Następnie przeciągnij węzeł na środkowej części powierzchni projektowej, tak aby projektanta wie, że chcesz, aby przejść w środkowym rzędzie. Jeśli użytkownik zostanie zgubiony przez użytkownika go, można określić wiersz ręcznie później w XAML. Domyślnie przez formanty są umieszczane w pionie w elemencie siatki, ale w tym momencie można rozmieścić je jednak na formularzu, takich jak. Na przykład może być uzasadnione, aby umieścić **nazwa** polu tekstowym u góry powyżej adresu. Przykładowa aplikacja w tym artykule zmienia kolejność pól i Reorganizuje je na dwie kolumny.

     ![Powiązanie źródła danych klientów do pojedynczych formantów](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png)

     W widoku kodu będą teraz widoczne nowe `Grid` elementu w wierszu 1 (środkowym rzędzie) elementu nadrzędnego siatki. Siatka zawiera element nadrzędny `DataContext` atrybut, który odwołuje się do CollectionViewSource, zostały dodane do `Windows.Resources` elementu. Podane tego kontekstu danych podczas pierwszego pola tekstowego, który tworzy powiązanie z **adres**, tej nazwie jest mapowany na `Address` właściwości w bieżącym `Customer` obiektu w CollectionViewSource.

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6.  Gdy klient jest widoczna na górze okna, chcesz zobaczyć jego zamówienia, w dolnej połowie. Możesz wyświetlić zamówienia w kontrolce widok pojedynczego siatki. Elementy główne szczegóły wiązania z danymi do pracy zgodnie z oczekiwaniami ważne jest powiązać właściwości zamówienia w klasie klientów z osobny węzeł zamówienia. Przeciągnij zamówienia właściwości klasy klientów do dolnej części formularza, dzięki czemu Projektant umieści go w wierszu 2:

     ![Przeciągnij klasy zamówienia w postaci siatki](../data-tools/media/raddata-drag-orders-classes-as-grid.png)

7.  Program Visual Studio został wygenerowany cały kod powiązania, który łączy z kontrolek interfejsu użytkownika dla zdarzeń w modelu. Wszystko, co należy zrobić, aby można było wyświetlić dane, jest pisanie kodu w celu wypełnienia modelu. Przejdź do *MainWindow.xaml.cs* i Dodaj element członkowski danych do klasy MainWindow kontekstu danych. Ten obiekt, który został wygenerowany dla Ciebie, działa podobny do formantu, który śledzi zmiany i zdarzeń w modelu. Należy również dodać logikę inicjowania konstruktora. Początku klasy powinna wyglądać następująco:

     [!code-csharp[MainWindow#1](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#1)]

     Dodaj `using` dyrektywy dla System.Data.Entity do wprowadzenia metody rozszerzenia obciążenia w zakresie:

     ```csharp
     using System.Data.Entity;
     ```

     Teraz przewiń w dół i Znajdź `Window_Loaded` programu obsługi zdarzeń. Należy zauważyć, że program Visual Studio dodał obiektu CollectionViewSource. Reprezentuje obiekt NorthwindEntities, który wybrano podczas tworzenia modelu. Teraz Dodaj kod, aby `Window_Loaded` tak, aby całą metodę wygląda teraz następująco:

     [!code-csharp[Window_Loaded#2](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#2)]

8.  Naciśnij klawisz **F5**. Szczegóły powinny być widoczne dla pierwszego klienta, który został pobrany do CollectionViewSource. Należy również zobaczyć jego zamówienia w siatce danych. Formatowanie jest doskonałym, więc zmienimy. Można również utworzyć sposób, aby wyświetlić inne rekordy i wykonywać podstawowe operacje CRUD.

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Dostosuj wygląd strony i dodawanie siatki dla nowych klientów i zamówień

Domyślnym rozmieszczeniu generowane przez program Visual Studio nie jest idealnym rozwiązaniem dla twojej aplikacji, więc wprowadzisz pewne zmiany ręcznie w XAML. Należy również pewne "Form", (które są rzeczywiście siatki) umożliwia użytkownikowi dodanie nowego klienta i zamówienia. Aby można było dodać nowego klienta i zamówienia, konieczne będzie oddzielny zestaw pól tekstowych, które nie są powiązane z danymi do `CollectionViewSource`. Będzie kontrolować siatki, które użytkownik zobaczy w danym momencie przez ustawienie właściwości widocznych w metody programu obsługi. Na koniec Dodaj przycisk usuwania dla każdego wiersza w siatce zleceń umożliwia użytkownikowi usuwanie określone zamówienie.

Najpierw dodaj te style `Windows.Resources` element *MainWindow.xaml*:

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

Następnie zastąp cały zewnętrzny siatki ten kod znaczników:

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
         <Label Content="Contact Title:" Grid.Row="3" Style="{StaticResource Label}"/>
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
         <Label Content="Contact Title:" Grid.Row="3" Style="{StaticResource Label}"/>
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

## <a name="add-buttons-to-navigate-add-update-and-delete"></a>Dodawanie przycisków, aby przejść, dodawanie, aktualizowanie i usuwanie

W aplikacjach Windows Forms możesz uzyskać obiekt BindingNavigator za pomocą przycisków przechodzenia między wierszy w bazie danych i wykonywania podstawowych operacji CRUD. WPF nie zapewnia BindingNavigator, ale to proste go utworzyć. To zrobić za pomocą przycisków w poziomie StackPanel i skojarzyć przyciski, za pomocą poleceń, które są powiązane z metody w kodzie.

Istnieją fours części logiki polecenia: (1) poleceń, (2 powiązania, (3 przycisków i (4 programy obsługi poleceń w związanym z kodem.

### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Dodawanie poleceń, powiązania i przycisków w XAML

1.  Najpierw dodaj poleceń w *MainWindow.xaml* pliku wewnątrz `Windows.Resources` elementu:

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

2.  Mapuje klasą CommandBinding `RoutedUICommand` zdarzeń do metody w kodzie. Dodaj tę `CommandBindings` elementu po `Windows.Resources` tag zamykający:

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

3.  Teraz Dodaj `StackPanel` z nawigacją, dodawanie, usuwanie i aktualizowanie przycisków. Najpierw dodaj ten styl do `Windows.Resources`:

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     Po drugie, wklej ten kod tuż za `RowDefinitions` dla zewnętrzny `Grid` elementu, w górnej części strony XAML:

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

### <a name="add-command-handlers-to-the-mainwindow-class"></a>Dodaj programy obsługi poleceń do klasy MainWindow

Związane z kodem jest minimalny, z wyjątkiem metody dodawania i usuwania. Nawigacja odbywa się przez wywołanie metody w widoku własności CollectionViewSource. `DeleteOrderCommandHandler` Pokazuje, jak wykonać usuwanie kaskadowe na zamówienie. Musimy najpierw usunąć szczegóły zamówienia, które są skojarzone z nim. `UpdateCommandHandler` Dodaje nowego klienta i zamówienia w kolekcji; w przeciwnym razie po prostu aktualizuje istniejący klient lub kolejność zmiany wprowadzone przez użytkownika w polach tekstowych.

Dodaj następujące metody obsługi do klasy MainWindow w *MainWindow.xaml.cs*. Jeśli Twoje CollectionViewSource dla tabeli Customers ma inną nazwę, należy dostosować nazwę w każdej z tych metod:

[!code-csharp[CommandHandlers#3](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#3)]

## <a name="run-the-application"></a>Uruchamianie aplikacji

Aby rozpocząć debugowanie, naciśnij klawisz **F5**. Powinien zostać wyświetlony dane klienta i zamówienia w siatce i przycisków nawigacji powinien działać zgodnie z oczekiwaniami. Kliknij pozycję **zatwierdzić** można dodać nowego klienta i zamówienia w modelu, po wprowadzeniu danych. Kliknij pozycję **anulować** kopii poza nowego klienta lub nowego formularza zamówienia bez zapisywania danych. Możesz wprowadzić zmiany istniejący klienci i zamówienia bezpośrednio w polach tekstowych, a te zmiany są automatycznie zapisywane w modelu.

## <a name="see-also"></a>Zobacz także

- [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Dokumentacja programu Entity Framework](/ef/)