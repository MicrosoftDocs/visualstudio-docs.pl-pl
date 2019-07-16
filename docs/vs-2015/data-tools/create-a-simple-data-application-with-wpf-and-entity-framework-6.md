---
title: Tworzenie prostej aplikacji danych przy użyciu platformy WPF i Entity Framework 6 | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 65929fab-5d78-4e04-af1e-cf4957f230f6
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: decb17be7caa4ea0a300ddb4378ac0ad11520109
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68145747"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Tworzenie prostej aplikacji do obsługi danych za pomocą platform WPF i Entity Framework 6
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

To walkthough pokazuje, jak utworzyć aplikację podstawowe "formularzy nad danymi" w programie Visual Studio przy użyciu programu SQL Server LocalDB, bazy danych Northwind, platformy Entity Framework 6 i Windows Presentation Foundation. Pokazano, jak wykonać podstawowe powiązanie danych z widokiem wzorzec / szczegół i ma on także niestandardowe "powiązanie Nawigator" za pomocą przycisków dla "Przenieś dalej", "Przenieś poprzedni," "Przenieś na początek," "Przenieś na koniec," "Aktualizuj" i "Usuń".  
  
 Ten artykuł koncentruje się na użyciu narzędzia danych programu Visual Studio i nie jest podejmowana próba wyjaśnić podstawowej technologii, w dowolnym poziomie. Przyjęto założenie, że masz podstawowe znajomość XAML, platformy Entity Framework i SQL. W tym przykładzie również nie przedstawiono tu architektury MVVM, który jest standardem dla aplikacji WPF. Jednak możesz skopiować ten kod do własnej aplikacji MVVM za pomocą bardzo mało modyfikacji.  
  
## <a name="install-and-connect-to-northwind"></a>Instalacja i nawiązywanie Northwind  
 W tym przykładzie użyto programu SQL Server Express LocalDB i przykładowej bazy danych Northwind. Powinien działać z innymi produktami do bazy danych SQL równie dobrze w przypadku dostawcy danych ADO.NET dla danego produktu obsługuje platformy Entity Framework.  
  
1. Jeśli nie jest jeszcze zainstalować program SQL Server 2014 LocalDB Express 32-bitowe z [stronę pobierania wersji programu SQL Server](https://www.microsoft.com/sql-server/sql-server-editions-express).  
  
2. Instalowanie przykładowej bazy danych Northwind, zgodnie z instrukcjami w tym miejscu: [Instalowanie programu SQL Server przykładowych baz danych](../data-tools/install-sql-server-sample-databases.md).  
  
3. [Dodaj nowe połączenia](../data-tools/add-new-connections.md) dla Northwind.  
  
## <a name="configure-the-project"></a>Konfigurowanie projektu  
  
1. W programie Visual Studio, wybierz **pliku &#124; nowy projekt** , a następnie utwórz nową aplikację WPF języka C#.  
  
2. Następnie dodamy pakiet NuGet dla platformy Entity Framework 6. W Eksploratorze rozwiązań wybierz węzeł projektu. W menu głównym wybierz **projektu &#124; Zarządzaj pakietami NuGet...**  
  
     ![Zarządzanie pakietami NuGet element menu](../data-tools/media/raddata-vs2015-manage-nuget-packages.png "raddata_vs2015_manage_nuget_packages")  
  
3. W Menedżerze pakietów NuGet, kliknij polecenie **Przeglądaj** łącza. Entity Framework jest prawdopodobnie pakiet na liście. Kliknij przycisk **zainstalować** w okienku po prawej stronie i postępuj zgodnie z monitami. W oknie danych wyjściowych poinformuje, po zakończeniu instalacji.  
  
     ![Pakiet NuGet programu Entity Framework](../data-tools/media/raddata-vs2015-nuget-ef.png "raddata_vs2015_Nuget_EF")  
  
4. Teraz możemy użyć programu Visual Studio, aby utworzyć model na podstawie bazy danych Northwind.  
  
## <a name="create-the-model"></a>Tworzenie modelu  
  
1. Kliknij prawym przyciskiem myszy węzeł projektu w Eksploratorze rozwiązań i wybierz polecenie **Dodaj &#124; nowy element**. W okienku po lewej stronie w węźle C#, wybierz **danych** i w środkowym okienku wybierz **ADO.NET Entity Data Model**.  
  
    ![Entity Framework modelu nowy element projektu](../data-tools/media/raddata-ef-new-project-item.png "raddata EF nowy element projektu")  
  
2. Wywoływanie modelu `Northwind_model` i wybierz przycisk OK. Spowoduje to przejście **Kreator modelu Entity Data Model**. Wybierz **projektancie platformy EF z bazy danych** a następnie kliknij przycisk **dalej**.  
  
    ![Modelu platformy EF z bazy danych](../data-tools/media/raddata-ef-model-from-database.png "raddata modelu platformy EF z bazy danych")  
  
3. Na następnym ekranie Wybierz połączenie i kliknij pozycję usługi LocalDB Northwind **dalej**.  
  
4. Na następnej stronie kreatora firma Microsoft wybierz tabele, procedury składowane i innych obiektów bazy danych, które mają zostać objęte modelu Entity Framework. Rozwiń węzeł dbo w widoku drzewa i wybierz klienci i zamówienia szczegóły zamówienia. Pozostaw wartości domyślne, zaznaczone, a następnie kliknij przycisk **Zakończ**.  
  
    ![Wybierz obiekty bazy danych dla modelu](../data-tools/media/raddata-choose-ef-objects.png "raddata wybierz obiekty EF")  
  
5. Kreator generuje klas języka C#, które reprezentują model Entity Framework. Są to zwykłe stare klas języka C# i są one, firma Microsoft będzie powiązać z danymi interfejsu użytkownika WPF. Plik edmx opisano relacje i inne metadane, które kojarzy klas obiektów w bazie danych.  .TT — pliki są szablony T4, które generują kod, które będą działać na podstawie modelu i zapisać zmiany w bazie danych. Możesz zobaczyć wszystkie te pliki w Eksploratorze rozwiązań w węźle Northwind_model:  
  
    ![Pliki modelu platformy EF Eksploratora rozwiązania](../data-tools/media/raddata-solution-explorer-ef-model-files.png "plików modelu platformy EF Eksploratora rozwiązań raddata")  
  
    Powierzchni projektanta dla pliku edmx umożliwia modyfikowanie niektórych właściwości i relacje w modelu. Nie będziemy korzystać z projektanta, w tym przewodniku.  
  
6. .TT — pliki są ogólnego przeznaczenia i musimy dostosować jeden z nich do pracy z powiązanie danych WPF, która wymaga ObservableCollections.  W Eksploratorze rozwiązań rozwiń węzeł Northwind_model, aż znajdziesz Northwind_model.tt. (Upewnij się, że jesteś **nie** w *. Kontekst .tt plik jest bezpośrednio poniżej pliku edmx).  
  
   - Zastąp dwa wystąpienia <xref:System.Collections.ICollection> z <xref:System.Collections.ObjectModel.ObservableCollection%601>.  
  
   - Zamień na pierwsze wystąpienie <xref:System.Collections.Generic.HashSet%601> z <xref:System.Collections.ObjectModel.ObservableCollection%601> całym wierszu 51. Nie zastępuj drugie wystąpienie hashset —  
  
   - Zastąpić tylko wystąpienie <xref:System.Collections.Generic> (około wiersza 334) przy użyciu <xref:System.Collections.ObjectModel>.  
  
7. Naciśnij klawisz **Ctrl + Shift + B** do skompilowania projektu. Po zakończeniu kompilacji, klasy modelu są widoczne w Kreatorze źródła danych.  
  
   Teraz jesteśmy gotowi zaczepić tego modelu do strony XAML, dzięki temu możemy wyświetlić, przejdź i modyfikować dane.  
  
## <a name="databind-the-model-to-the-xaml-page"></a>Elementu DataBind modelu do strony XAML  
 Można napisać własny kod wiązania danych, ale jest znacznie łatwiejsze umożliwić programowi Visual Studio zrobił dla Ciebie.  
  
1. W menu głównym wybierz **projektu &#124; Dodaj nowe źródło danych** aby przywołać **Kreatora konfiguracji źródła danych**. Wybierz **obiektu** ponieważ możemy dokonywane jest wiązanie modelu klasy, nie bazy danych:  
  
     ![Kreator konfiguracji źródła danych z obiektu źródłowego](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png "raddata Kreatora konfiguracji źródła danych z obiektu źródłowego")  
  
2. Wybierz klienta.  (Źródeł dla zamówienia zostanie automatycznie wygenerowany na podstawie właściwości nawigacji zamówień klientów.)  
  
     ![Dodawanie klas jednostek jako źródła danych](../data-tools/media/raddata-add-entity-classes-as-data-sources.png "raddata jednostki Dodaj klasy jako źródła danych")  
  
3. Kliknij przycisk **Zakończ**  
  
4. Przejdź do pliku MainWindow.xaml w widoku kodu. Firma Microsoft zamierza zachować XAML na potrzeby tego przykładu jest bardzo proste. Zmienianie tytułu MainWindow na bardziej opisową i zwiększenie jego wysokości i szerokości do 600 x 800 teraz. Można zawsze zmienić go później. Teraz należy dodać te definicje trzech wierszy do głównej siatki jeden wiersz przycisków nawigacji, jeden dla szczegóły klienta, jeden dla siatki, pokazujący zamówienia:  
  
    ```xaml  
    <Grid.RowDefinitions>  
               <RowDefinition Height="auto"/>  
               <RowDefinition Height="auto"/>  
               <RowDefinition Height="*"/>  
           </Grid.RowDefinitions>  
    ```  
  
5. Teraz można otworzyć pliku MainWindow.xaml, tak, aby wyświetlanych w projektancie. Spowoduje to okna źródeł danych pojawiało się jako opcję na marginesie okna programu Visual Studio obok przybornika. Kliknij kartę, aby otworzyć okno lub inne naciśnij **Shift + Alt + D** lub wybierz **widoku &#124; Windows inne &#124; źródeł danych**. Użyjemy do wyświetlania każdej właściwości w klasie klientów w jego własnej poszczególnych tekst. Najpierw kliknij strzałkę w polu kombi klientów i wybierz polecenie **szczegóły**. Następnie przeciągnij węzeł na środkowej części powierzchni projektowej, tak aby projektanta wie, że chcesz, aby przejść w środkowym rzędzie.  Jeśli użytkownik zostanie zgubiony przez użytkownika go, można określić wiersz ręcznie później w XAML. Domyślnie przez formanty są umieszczane w pionie w elemencie siatki, ale w tym momencie można rozmieścić je jednak na formularzu, takich jak.  Na przykład sensowne do umieszczenia w polu tekstowym Nazwa u góry powyżej adresu. Przykładowa aplikacja w tym artykule zmienia kolejność pól i Reorganizuje je na dwie kolumny.  
  
     ![Powiązanie źródła danych klientów do poszczególnych formantów](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png "raddata klientów źródło powiązania danych poszczególnych formantów")  
  
     W widoku kodu będą teraz widoczne nowe `Grid` elementu w wierszu 1 (środkowym rzędzie) elementu nadrzędnego siatki. Siatka zawiera element nadrzędny `DataContext` atrybut, który odwołuje się do CollectionViewSource, która została dodana do `Windows.Resources` elementu. Biorąc pod uwagę ten kontekst danych, pole tekstowe pierwszy, na przykład powiązania przy użyciu tej nazwy "rozwiązania" jest mapowany na `Address` właściwości w bieżącym `Customer` obiektu w CollectionViewSource.  
  
    ```xaml  
    <Grid DataContext="{StaticResource customerViewSource}">  
    ```  
  
6. Gdy klient jest widoczna na górze okna, chcemy zobaczyć jego zamówienia, w dolnej połowie. Pokażemy zamówienia w kontrolce widok pojedynczego siatki. Elementy główne szczegóły wiązania z danymi do pracy zgodnie z oczekiwaniami ważne jest, możemy powiązać właściwości zamówienia w klasie klientów z osobny węzeł zamówienia. Należy zwrócić uwagę na poniższej ilustracji! Przeciągnij zamówienia właściwości klasy klientów do dolnej części formularza, dzięki czemu Projektant umieści go w wierszu 2:  
  
     ![Przeciągnij klasy zamówienia jako siatkę](../data-tools/media/raddata-drag-orders-classes-as-grid.png "raddata zamówienia przeciągnij klasy jako siatkę")  
  
7. Program Visual Studio został wygenerowany cały kod powiązania, który łączy z kontrolek interfejsu użytkownika dla zdarzeń w modelu. Wszystko, co należy zrobić, aby można było wyświetlić dane, jest pisanie kodu w celu wypełnienia modelu. Pierwszy teraz przejdź do MainWindow.xaml.cs i Dodaj element członkowski danych do klasy MainWindow kontekstu danych. Ten obiekt, który został wygenerowany dla nas, działa podobny do formantu, który śledzi zmiany i zdarzeń w modelu. Chociaż jesteśmy gotowi, dodamy dwa elementy członkowskie, które będą używane później można dodać nowego klienta lub nowe zamówienie. Ponadto dodamy logiki inicjowania konstruktora. Górnej części klasy Nasze powinien wyglądać następująco:  
  
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
  
     Dodaj `using` dyrektywy dla System.Data.Entity do wprowadzenia metody rozszerzenia obciążenia w zakresie:  
  
    ```csharp  
    using System.Data.Entity;  
    ```  
  
     Teraz przewiń w dół i Znajdź Window_Loaded obsługi zdarzeń. Zwróć uwagę, czy program Visual Studio dodał obiektu CollectionViewSource dla nas. Reprezentuje obiekt NorthwindEntities, który wybrano podczas tworzenia modelu. Dodajmy kodu do Window_loaded, tak aby całą metodę wygląda teraz następująco:  
  
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
  
8. Naciśnij klawisz **F5**. Szczegóły powinny być widoczne dla pierwszego klienta, który został pobrany do CollectionViewSource i zamówienia w siatce danych. Formatowanie jest doskonałym, więc zmienimy. pozwala na tworzenie sposób, aby wyświetlić inne rekordy i wykonywać podstawowe operacje CRUD.  
  
## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Dostosuj wygląd strony i dodawanie siatki dla nowych klientów i zamówień  
 Domyślnym rozmieszczeniu generowane przez program Visual Studio nie jest idealnym rozwiązaniem dla naszej aplikacji, więc firma Microsoft będzie ręcznie wprowadzić pewne zmiany w XAML. Firma Microsoft będzie również trzeba niektórych "Form", (które są rzeczywiście siatki) umożliwia użytkownikowi dodanie nowego klienta lub nowego zamówienia.    Aby można było dodać nowego klienta i zamówienia, potrzebujemy oddzielny zestaw pól tekstowych, które nie są powiązane z danymi do `CollectionViewSource`. Firma Microsoft będzie kontrolować siatki, które użytkownik zobaczy w danym momencie przez ustawienie właściwości widocznych w metody programu obsługi.  
  
 Na koniec w poszczególnych wierszy w siatce zleceń umożliwia użytkownikowi usuwanie określone zamówienie dodamy przycisk Usuń.  
  
 Najpierw dodaj te style do Windows.Resources:  
  
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
  
## <a name="add-buttons-to-navigate-add-update-and-delete"></a>Dodawanie przycisków, aby przejść, dodawanie, aktualizowanie i usuwanie  
 W aplikacjach Windows Forms możesz uzyskać obiekt BindingNavigator za pomocą przycisków przechodzenia między wierszy w bazie danych i wykonywania podstawowych operacji CRUD. WPF nie zapewnia BindingNavigator, ale są one łatwe się. Możemy to zrobić za pomocą przycisków w poziomie StackPanel w dolnym wierszu siatki strony i przyciski będą powiązane z poleceniami, które są powiązane z metody w kodzie.  
  
 Istnieją fours części logiki polecenia: (1) poleceń, (2 powiązania, (3 przycisków i (4 programy obsługi poleceń w związanym z kodem.  
  
#### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Dodawanie poleceń, powiązania i przycisków w XAML  
  
1. Najpierw Dodajmy polecenia w naszym pliku MainWindow.XAML w elemencie Windows.Resources:  
  
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
  
2. Klasą CommandBinding mapuje zdarzeń RoutedUICommand metody w kodzie. Dodaj ten element CommandBindings po Windows.Resources tag zamykający:  
  
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
  
3. Teraz Dodajmy StackPanel z nawigacji, Dodaj, Usuń i zaktualizuj przycisków. Najpierw należy dodać ten styl do Windows.Resources:  
  
    ```xaml  
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">  
        <Setter Property="FontSize" Value="24"/>  
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>  
        <Setter Property="Margin" Value="2,2,2,0"/>  
        <Setter Property="Width" Value="40"/>  
        <Setter Property="Height" Value="auto"/>  
    </Style>  
    ```  
  
     Teraz wklej ten kod zaraz po RowDefinitions dla elementu zewnętrznego siatki w górnej części strony XAML:  
  
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
  
#### <a name="add-command-handlers-to-the-mainwindow-class"></a>Dodaj programy obsługi poleceń do klasy MainWindow  
  
1. Związane z kodem jest minimalny, z wyjątkiem metody dodawania i usuwania. Należy pamiętać, że nawigacji odbywa się przez wywołanie metody w widoku własności CollectionViewSource. DeleteOrderCommandHandler pokazuje sposób wykonywania usuwanie kaskadowe na zamówienie. Musimy najpierw usunąć szczegóły zamówienia, które są skojarzone z nim. UpdateCommandHandler dodaje nowego klienta do kolekcji, w przeciwnym razie po prostu aktualizuje istniejący obiekt niezależnie od rodzaju zmiany wprowadził w polach tekstowych.  
  
2. Dodaj do klasy MainWindow w MainWindow.xaml.cs, te metody obsługi, jeśli Twoja CollectionViewSource dla tabeli Customers ma pod inną nazwą, a następnie musisz dostosować nazwę w każdej z tych metod:  
  
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
  
3. Naciśnij klawisz **F5**. Twoje dane powinny być widoczne i przycisków nawigacji powinien działać zgodnie z oczekiwaniami. Kliknij pozycję "Commit", aby dodać nowego klienta lub kolejności do modelu, po wprowadzeniu danych.  Kliknij przycisk "Anuluj", aby utworzyć kopię poza nowego formularza lub nowego zamówienia klienta bez zapisywania zmian. Wprowadzone zmiany dla istniejących klientów i zamówienia bezpośrednio w polach tekstowych, a te zmiany modelu zostaną zapisane automatycznie.  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia Visual Studio data tools dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md) [dokumentacja programu Entity Framework](https://msdn.microsoft.com/data/ee712907.aspx)
