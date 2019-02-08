---
title: 'Przewodnik: Dostosowywanie wstawiania, aktualizowania i usuwania zachowanie klas jednostek'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 27c2677b8afef1f1e2cd035acb3038b42a4ef56d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55948605"
---
# <a name="walkthrough-customize-the-insert-update-and-delete-behavior-of-entity-classes"></a>Przewodnik: Dostosowywanie zachowania wstawiania, aktualizacji i usuwania dla klas jednostek

[LINQ to SQL tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) zapewnia powierzchnia projektowania wizualnego służące do tworzenia i edytowania zapytań LINQ do klas SQL (klas jednostek), które są oparte na obiektach w bazie danych. Za pomocą [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index), można użyć technologii LINQ do dostępu do bazy danych z programu SQL. Aby uzyskać więcej informacji, zobacz [LINQ (Language-Integrated query)](/dotnet/csharp/linq/).

Domyślnie logikę do przeprowadzania aktualizacji znajduje się w składniku LINQ to SQL w czasie wykonywania. Środowisko uruchomieniowe tworzy domyślne `Insert`, `Update`, i `Delete` instrukcji na podstawie schematu tabeli (definicje kolumn i informacje o kluczu podstawowym). Gdy użytkownik nie chce Użyj zachowania domyślnego, można skonfigurować zachowanie aktualizacji i wyznaczyć określonych procedur składowanych do wykonywania niezbędne operacje wstawiania, aktualizacji i usuwania wymagane do pracy z danymi w bazie danych. Ponadto można to zrobić, jeśli domyślne zachowanie nie jest generowany, na przykład, gdy Twoje klas jednostek mapy do widoków. Ponadto można zastąpić domyślne zachowanie aktualizacji, gdy baza danych wymaga dostępu do tabel za pomocą procedur składowanych. Aby uzyskać więcej informacji, zobacz [Dostosowywanie operacji przy użyciu procedur składowanych](/dotnet/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures).

> [!NOTE]
> Ten poradnik wymaga dostępności **InsertCustomer**, **UpdateCustomer**, i **DeleteCustomer** procedury składowane dla bazy danych Northwind.

Ten przewodnik zawiera kroki, które należy wykonać, aby zastąpić domyślne LINQ do zachowania w czasie wykonywania SQL do zapisywania danych do bazy danych przy użyciu procedur składowanych.

Z tego instruktażu dowiesz się, jak wykonywać następujące zadania:

-   Tworzenie nowej aplikacji Windows Forms i Dodaj LINQ do pliku SQL do niego.

-   Utwórz klasę jednostki, który jest zamapowany Northwind `Customers` tabeli.

-   Utwórz źródło danych obiektu, który odwołuje się do programu LINQ to SQL `Customer` klasy.

-   Tworzenie formularza Windows, który zawiera <xref:System.Windows.Forms.DataGridView> , jest powiązany z `Customer` klasy.

-   Implementowanie zapisać funkcjonalności formularza.

-   Tworzenie <xref:System.Data.Linq.DataContext> metod, dodając przechowywane procedury, aby **O/R Designer**.

-   Konfigurowanie `Customer` klasy na potrzeby wykonywania procedur składowanych wstawiania, aktualizacji i usuwania.

## <a name="prerequisites"></a>Wymagania wstępne

Ten przewodnik korzysta z programu SQL Server Express LocalDB i bazie danych Northwind.

1.  Jeśli nie masz programu SQL Server Express LocalDB, zainstaluj go z [stronę pobierania programu SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), lub za pomocą **Instalatora programu Visual Studio**. W **Instalatora programu Visual Studio**, można zainstalować programu SQL Server Express LocalDB, jako część **przechowywanie i przetwarzanie danych** obciążenie, lub jako poszczególnych składników.

2.  Instalowanie przykładowej bazy danych Northwind, wykonaj następujące czynności:

    1. W programie Visual Studio, otwórz **Eksplorator obiektów SQL Server** okna. (**Eksplorator obiektów SQL Server** jest instalowany jako część **przechowywanie i przetwarzanie danych** obciążenie w **Instalatora programu Visual Studio**.) Rozwiń **programu SQL Server** węzła. Kliknij prawym przyciskiem myszy w ramach wystąpienia LocalDB, a następnie wybierz pozycję **nowe zapytanie**.

       Zostanie otwarte okno edytora zapytań.

    2. Kopiuj [skryptów języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt języka T-SQL tworzy bazę danych Northwind od podstaw i wypełnia ją z danymi.

    3. Wklej skrypt języka T-SQL do edytora zapytań, a następnie wybierz **Execute** przycisku.

       Po pewnym czasie odliczania zapytania i utworzeniu bazy danych Northwind.

## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Tworzenie aplikacji i dodawanie LINQ do klas SQL

Ponieważ jesteś Praca z technologią LINQ do klas SQL i wyświetlanie danych w formularzu Windows, Utwórz nową aplikację Windows Forms i Dodaj LINQ do klas SQL pliku.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-new-windows-forms-application-project-that-contains-linq-to-sql-classes"></a>Aby utworzyć nowy projekt aplikacja interfejsu Windows Forms, który zawiera LINQ do klas SQL

1. W programie Visual Studio na **pliku** menu, wybierz opcję **New** > **projektu**.

2. Rozwiń **Visual C#** lub **języka Visual Basic** w okienku po lewej stronie, a następnie zaznacz **pulpitu Windows**.

3. W środkowym okienku wybierz **Windows Forms App** typ projektu.

4. Nadaj projektowi nazwę **UpdatingWithSProcsWalkthrough**, a następnie wybierz **OK**.

     **UpdatingWithSProcsWalkthrough** projekt zostanie utworzony i dodany do **Eksploratora rozwiązań**.

4.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.

5.  Kliknij przycisk **klasy LINQ do SQL** szablonu i typ **Northwind.dbml** w **nazwa** pole.

6.  Kliknij przycisk **Dodaj**.

     Pusty plik LINQ to SQL klas (**Northwind.dbml**) jest dodawany do projektu, a **O/R Designer** zostanie otwarty.

## <a name="create-the-customer-entity-class-and-object-data-source"></a>Tworzenie klienta jednostki klasy i obiektu źródła danych

Tworzenie typu LINQ do klas SQL, które są mapowane do tabel bazy danych, przeciągając tabel z **Eksploratora serwera** lub **Eksplorator bazy danych** na **O/R Designer**. Wynik jest LINQ do klas jednostek SQL, które mapują do tabel w bazie danych. Po utworzeniu klasy jednostek, możesz używać jako źródła danych obiektu, podobnie jak inne klasy, które mają właściwości publiczne.

### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Utwórz klasę jednostki klienta i skonfigurować źródło danych z nią

1.  W **Eksploratora serwera** lub **Eksplorator bazy danych**, zlokalizuj **klienta** tabeli w bazie danych Northwind w wersji programu SQL Server.

2.  Przeciągnij **klientów** węzła z **Eksploratora serwera** lub **Eksplorator bazy danych** na **O/R Designer* powierzchni.

     Klasa jednostki o nazwie **klienta** zostanie utworzony. Posiada właściwości, które odnoszą się do kolumn w tabeli Customers. Klasa jednostki nosi nazwę **klienta** (nie **klientów**), ponieważ reprezentuje on jednego klienta z tabeli Customers.

    > [!NOTE]
    > Zmiana nazwy jest to *pluralizacja*. Można je włączyć lub wyłączyć [okno dialogowe Opcje](../ide/reference/options-dialog-box-visual-studio.md). Aby uzyskać więcej informacji, zobacz [jak: Włącz pluralizacja włączać i wyłączać (O/R Designer)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).

3.  Na **kompilacji** menu, kliknij przycisk **kompilacji UpdatingwithSProcsWalkthrough** do skompilowania projektu.

4.  Aby otworzyć **źródeł danych** okna na **danych** menu, kliknij przycisk **Pokaż źródła danych**.

5.  W **źródeł danych** okna, kliknij przycisk **Dodaj nowe źródło danych**.

6.  Kliknij przycisk **obiektu** na **wybierz typ źródła danych** strony, a następnie kliknij przycisk **dalej**.

7.  Rozwiń **UpdatingwithSProcsWalkthrough** węzła i Znajdź i zaznacz **klienta** klasy.

    > [!NOTE]
    > Jeśli **klienta** klasy nie jest dostępna, Anuluj kreatora, skompiluj projekt i uruchom ponownie kreatora.
8.  Kliknij przycisk **Zakończ** Utwórz źródło danych i dodać **klienta** klasy jednostki **źródeł danych** okna.

## <a name="create-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Utwórz DataGridView do wyświetlania danych klientów w formularzu Windows

Tworzenie formantów, które są powiązane z klasami jednostki, przeciągając elementy źródeł danych SQL z LINQ **źródeł danych** okna w formularzu Windows.

### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>Aby dodać formanty powiązane z klasami jednostki

1.  Otwórz **Form1** w widoku Projekt.

2.  Z **źródeł danych** okna, przeciągnij **klienta** węzła na **Form1**.

    > [!NOTE]
    > Aby wyświetlić **źródeł danych** okna, kliknij przycisk **Pokaż źródła danych** na **danych** menu.

3.  Otwórz **Form1** w edytorze kodu.

4.  Dodaj następujący kod do formularza, globalne do formularza, poza określonej metody, ale wewnątrz `Form1` klasy:

    ```vb
    Private NorthwindDataContext1 As New NorthwindDataContext
    ```

    ```csharp
    private NorthwindDataContext northwindDataContext1
        = new NorthwindDataContext();
    ```

5.  Utwórz procedurę obsługi zdarzeń dla `Form_Load` zdarzeń i Dodaj następujący kod do narzędzia obsługi:

    ```vb
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers
    ```

    ```csharp
    customerBindingSource.DataSource
        = northwindDataContext1.Customers;
    ```

## <a name="implement-save-functionality"></a>Implementowanie funkcja zapisywania

Domyślnie, Zapisz przycisk nie jest włączona i nie jest zaimplementowana funkcja zapisywania. Ponadto kod nie jest automatycznie dodawane do zapisać zmienione dane w bazie danych podczas tworzenia formantów powiązanych z danymi dla źródła danych obiektu. W tej sekcji omówiono sposób umożliwienia zapisu znajdujący się i zaimplementować funkcja zapisywania dla programu LINQ do obiektów programu SQL.

### <a name="to-implement-save-functionality"></a>Aby zaimplementować funkcja zapisywania

1.  Otwórz **Form1** w widoku Projekt.

2.  Wybierz opcję Zapisz znajdujący się na **CustomerBindingNavigator** (przycisk z ikoną dyskietki).

3.  W **właściwości** oknie **włączone** właściwości **True**.

4.  Kliknij dwukrotnie przycisk Zapisz, aby utworzyć program obsługi zdarzeń i przejdź do edytora kodu.

5.  Dodaj następujący kod do zapisywania obsługi zdarzeń przycisku:

    ```vb
    NorthwindDataContext1.SubmitChanges()
    ```

    ```csharp
    northwindDataContext1.SubmitChanges();
    ```

## <a name="override-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Zastąpić domyślne zachowanie dla wykonywanie aktualizacji (operacje wstawiania, aktualizacji i usuwania)

### <a name="to-override-the-default-update-behavior"></a>Zastępowanie domyślnego zachowania aktualizacji

1.  Otwórz plik LINQ to SQL w **O/R Designer**. (Kliknij dwukrotnie **Northwind.dbml** w pliku **Eksploratora rozwiązań**.)

2.  W **Eksploratora serwera** lub **Eksplorator bazy danych**, rozwiń węzeł bazy danych Northwind **procedur składowanych** węzła i Znajdź **InsertCustomers**, **UpdateCustomers**, i **DeleteCustomers** procedur składowanych.

3.  Przeciągnij wszystkie trzy procedury przechowywane na **O/R Designer**.

     Procedury składowane są dodawane do okienka metod jako <xref:System.Data.Linq.DataContext> metody. Aby uzyskać więcej informacji, zobacz [metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

4.  Wybierz **klienta** Klasa jednostki w **O/R Designer**.

5.  W **właściwości** wybierz **Wstaw** właściwości.

6.  Kliknij przycisk wielokropka (**...** ) obok pozycji **Użyj środowiska uruchomieniowego** otworzyć **Konfigurowanie zachowania** okno dialogowe.

7.  Wybierz **dostosować**.

8.  Wybierz **InsertCustomers** method in Class metoda **Dostosuj** listy.

9. Kliknij przycisk **Zastosuj** można zapisać konfiguracji dla wybranej klasy lub zachowania.

    > [!NOTE]
    > Można kontynuować, skonfiguruj zachowanie dla każdej kombinacji klasy/zachowania, tak długo, jak możesz kliknąć pozycję **Zastosuj** po wprowadzeniu każdej zmiany. Jeśli zmienisz klasy lub zachowania przed kliknięciem przycisku **Zastosuj**, zapewniając możliwości, aby zastosować zmiany, pojawi się okno dialogowe ostrzeżenia.

10. Wybierz **aktualizacji** w **zachowanie** listy.

11. Wybierz **dostosować**.

12. Wybierz **UpdateCustomers** method in Class metoda **Dostosuj** listy.

     Sprawdź listę **argumenty metody** i **właściwości klasy** i zwróć uwagę, że istnieją dwa **argumenty metody** oraz dwóch **właściwości klasy**dla niektórych kolumn w tabeli. To ułatwia śledzenie zmian i tworzenie instrukcji, które sprawdzaj naruszeń współbieżności.

13. Mapa **Original_CustomerID** argument metody **CustomerID (oryginalny)** właściwości klasy.

    > [!NOTE]
    > Domyślnie argumenty metody będzie zmapowana do właściwości klasy, gdy nazwy są zgodne. Jeśli nazwy właściwości zostały zmienione, a nie są już zgodne w tabeli i Klasa jednostki, Niewykluczone, że właściwość odpowiednik klasy do mapowania, jeśli **O/R Designer** nie może określić poprawne mapowania. Ponadto, jeśli argumenty metody nie ma właściwości prawidłową klasę do mapowania, możesz ustawić **właściwości klasy** wartość **(Brak)**.

14. Kliknij przycisk **Zastosuj** można zapisać konfiguracji dla wybranej klasy lub zachowania.

15. Wybierz **Usuń** w **zachowanie** listy.

16. Wybierz **dostosować**.

17. Wybierz **DeleteCustomers** method in Class metoda **Dostosuj** listy.

18. Mapa **Original_CustomerID** argument metody **CustomerID (oryginalny)** właściwości klasy.

19. Kliknij przycisk **OK**.

> [!NOTE]
> Chociaż nie jest to problem dla tego konkretnego przewodnika, warto zauważyć, że LINQ to SQL obsługuje wygenerowanych w bazie danych wartości automatycznie tożsamości (automatycznego przyrostu), rowguidcol (identyfikator GUID generowany przez bazy danych) i kolumn sygnatur czasowych podczas wstawiania i aktualizacje. Wartości generowanych przez bazę danych w innych typów kolumn spowoduje nieoczekiwane wartości null. Aby zwrócić wartości wygenerowanych w bazie danych, należy ręcznie ustawić <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> do `true` i <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> do jednej z następujących czynności: [AutoSync.Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync.OnInsert](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>), lub [AutoSync.OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

## <a name="test-the-application"></a>Testowanie aplikacji

Uruchom aplikację ponownie, aby sprawdzić, czy **UpdateCustomers** procedury składowanej poprawnie aktualizuje rekord klienta w bazie danych.

1.  Naciśnij klawisz **F5**.

2.  Zmodyfikuj rekord w siatce, aby sprawdzić zachowanie aktualizacji.

3.  Dodaj nowy rekord do testowanie zachowania wstawiania.

4.  Kliknij przycisk Zapisz, aby zapisać zmiany w bazie danych.

5.  Zamknij formularz.

6.  Naciśnij klawisz **F5** i Sprawdź zaktualizowany rekord a nowo wstawionej rekord trwałość.

7.  Delete nowe rejestrowanie utworzonego w kroku 3, aby sprawdzić zachowanie dotyczące usuwania.

8.  Kliknij przycisk Zapisz przycisk, aby przesłać zmiany i Usuń rekord usuniętych z bazy danych.

9. Zamknij formularz.

10. Naciśnij klawisz **F5** i sprawdź, czy usunięto rekord został usunięty z bazy danych.

    > [!NOTE]
    > Jeśli aplikacja używa programu SQL Server Express Edition, w zależności od wartości **Kopiuj do katalogu wyjściowego** właściwości pliku bazy danych, zmiany nie może występować, gdy użytkownik naciśnie klawisz **F5** w kroku 10.

## <a name="next-steps"></a>Następne kroki

W zależności od wymagań aplikacji istnieje kilka kroków, które warto wykonać po Tworzenie typu LINQ to SQL klas jednostek. Niektóre udoskonalenia, których można dokonać w tej aplikacji są następujące:

- Implementowanie współbieżności sprawdzanie podczas aktualizacji. Aby uzyskać informacje, zobacz [Optymistyczna współbieżność: omówienie](/dotnet/framework/data/adonet/sql/linq/optimistic-concurrency-overview).

- Dodawanie zapytań LINQ do filtrowania danych. Aby uzyskać informacje, zobacz [wprowadzenie do zapytań LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).

## <a name="see-also"></a>Zobacz także

- [Narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Metody DataContext](../data-tools/datacontext-methods-o-r-designer.md)
- [Instrukcje: Przypisywanie procedur składowanych do wykonywania aktualizacji, wstawiania i usuwania](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Zapytania LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/linq-to-sql-queries)