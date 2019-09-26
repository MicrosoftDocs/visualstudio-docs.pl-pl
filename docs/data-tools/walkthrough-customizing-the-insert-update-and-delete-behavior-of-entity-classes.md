---
title: Dostosuj zachowanie funkcji Insert/Update/Delete dla klas jednostek
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
ms.openlocfilehash: cb6bbde145317d737afdbf819dba8ee53f805f72
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252968"
---
# <a name="walkthrough-customize-the-insert-update-and-delete-behavior-of-entity-classes"></a>Przewodnik: Dostosowywanie zachowania wstawiania, aktualizacji i usuwania dla klas jednostek

[Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) oferują wizualną powierzchnię projektową do tworzenia i edytowania klas LINQ to SQL (klasy jednostek), które są oparte na obiektach w bazie danych. Korzystając z [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index), można używać technologii LINQ do uzyskiwania dostępu do baz danych SQL. Aby uzyskać więcej informacji, zobacz [LINQ (zapytanie zintegrowane z językiem)](/dotnet/csharp/linq/).

Domyślnie logika do wykonywania aktualizacji jest zapewniana przez środowisko uruchomieniowe LINQ to SQL. Środowisko uruchomieniowe tworzy `Insert`domyślne `Update`, i `Delete` instrukcje na podstawie schematu tabeli (definicje kolumn i informacje o kluczu podstawowym). Jeśli nie chcesz używać zachowania domyślnego, możesz skonfigurować zachowanie aktualizacji i wyznaczyć określone procedury składowane do wykonywania niezbędnych operacji wstawiania, aktualizacji i usuwania wymaganych do pracy z danymi w bazie danych. Można to również zrobić, gdy domyślne zachowanie nie jest generowane, na przykład gdy klasy jednostek mapują się na widoki. Ponadto można zastąpić domyślne zachowanie aktualizacji, gdy baza danych wymaga dostępu do tabeli za pomocą procedur składowanych. Aby uzyskać więcej informacji, zobacz [Dostosowywanie operacji za pomocą procedur składowanych](/dotnet/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures).

> [!NOTE]
> Ten Instruktaż wymaga dostępności procedur składowanych **InsertCustomer**, **UpdateCustomer**i **DeleteCustomer** dla bazy danych Northwind.

W tym instruktażu przedstawiono kroki, które należy wykonać, aby zastąpić domyślny LINQ to SQL zachowanie w czasie wykonywania zapisywania danych z powrotem do bazy danych za pomocą procedur składowanych.

W tym instruktażu dowiesz się, jak wykonywać następujące zadania:

- Utwórz nową aplikację Windows Forms i Dodaj do niej plik LINQ to SQL.

- Utwórz klasę jednostki, która jest mapowana na tabelę Northwind `Customers` .

- Utwórz źródło danych obiektu, które odwołuje się `Customer` do klasy LINQ to SQL.

- Utwórz formularz systemu Windows, który zawiera <xref:System.Windows.Forms.DataGridView> element, który jest powiązany `Customer` z klasą.

- Implementowanie funkcji Save dla formularza.

- Utwórz <xref:System.Data.Linq.DataContext> metody, dodając procedury składowane do **projektanta O/R**.

- `Customer` Skonfiguruj klasę, aby używać procedur składowanych do wykonywania operacji wstawiania, aktualizacji i usuwania.

## <a name="prerequisites"></a>Wymagania wstępne

W tym instruktażu jest stosowana SQL Server Express LocalDB i Przykładowa baza danych Northwind.

1. Jeśli nie masz SQL Server Express LocalDB, zainstaluj go na [stronie pobierania SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)lub za pośrednictwem **Instalator programu Visual Studio**. W **Instalator programu Visual Studio**można zainstalować SQL Server Express LocalDB jako część obciążenia **magazynu danych i przetwarzania** lub jako pojedynczy składnik.

2. Zainstaluj przykładową bazę danych Northwind, wykonując następujące kroki:

    1. W programie Visual Studio Otwórz okno **Eksplorator obiektów SQL Server** . (**Eksplorator obiektów SQL Server** instalowane w ramach obciążenia **magazynu i przetwarzania danych** w **Instalator programu Visual Studio**). Rozwiń węzeł **SQL Server** . Kliknij prawym przyciskiem myszy wystąpienie LocalDB i wybierz pozycję **nowe zapytanie**.

       Zostanie otwarte okno edytora zapytań.

    2. Skopiuj [skrypt języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt T-SQL tworzy bazę danych Northwind od podstaw i wypełnia ją danymi.

    3. Wklej skrypt języka T-SQL do edytora zapytań, a następnie wybierz **Execute** przycisku.

       Po krótkim czasie zapytanie kończy działanie i zostanie utworzona baza danych Northwind.

## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Tworzenie aplikacji i Dodawanie LINQ to SQL klas

Ponieważ pracujesz z klasami LINQ to SQL i wyświetlasz dane w formularzu systemu Windows, Utwórz nową aplikację Windows Forms i Dodaj plik LINQ to SQL klas.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-new-windows-forms-application-project-that-contains-linq-to-sql-classes"></a>Aby utworzyć nowy projekt aplikacji Windows Forms zawierający klasy LINQ to SQL

1. W programie Visual Studio w menu **plik** wybierz pozycję **Nowy** > **projekt**.

2. Rozwiń pozycję **Wizualizacja C#**  lub **Visual Basic** w okienku po lewej stronie, a następnie wybierz pozycję **pulpit systemu Windows**.

3. W środkowym okienku wybierz typ projektu **aplikacji Windows Forms** .

4. Nazwij projekt **UpdatingWithSProcsWalkthrough**, a następnie wybierz przycisk **OK**.

     Projekt **UpdatingWithSProcsWalkthrough** został utworzony i dodany do **Eksplorator rozwiązań**.

4. W menu **projekt** kliknij polecenie **Dodaj nowy element**.

5. Kliknij szablon **LINQ to SQL klas** i wpisz **Northwind. dbml** w polu **Nazwa** .

6. Kliknij przycisk **Dodaj**.

     Do projektu zostanie dodany pusty plik klas LINQ to SQL (**Northwind. dbml**) i zostanie otwarty **Projektant o/R** .

## <a name="create-the-customer-entity-class-and-object-data-source"></a>Utwórz klasę jednostki klienta i źródło danych obiektu

Utwórz klasy LINQ to SQL, które są mapowane na tabele bazy danych, przeciągając tabele z **Eksplorator serwera** lub **Eksplorator bazy danych** do **projektanta O/R**. Wynik jest LINQ to SQL klas jednostek, które są mapowane na tabele w bazie danych. Po utworzeniu klas jednostek mogą one być używane jako źródła danych obiektów, podobnie jak inne klasy z właściwościami publicznymi.

### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Aby utworzyć klasę jednostki klienta i skonfigurować dla niej źródło danych

1. W **Eksplorator serwera** lub **Eksplorator bazy danych**znajdź tabelę **Customer** w SQL Server wersji przykładowej bazy danych Northwind.

2. Przeciągnij węzeł **Customers** z **Eksplorator serwera** lub **Eksplorator bazy danych** na powierzchnię projektanta **O/R* .

     Utworzono klasę jednostki o nazwie **Klient** . Ma właściwości, które odpowiadają kolumnom w tabeli Customers. Klasa jednostki nosi nazwę **klienta** (nie **klientów**), ponieważ reprezentuje jednego klienta z tabeli Customers.

    > [!NOTE]
    > Takie zachowanie zmiany nazwy nosi nazwę *pluralizacja*. Można ją włączyć lub wyłączyć w oknie [dialogowym Opcje](../ide/reference/options-dialog-box-visual-studio.md). Aby uzyskać więcej informacji, zobacz [jak: Włącz i Wyłącz pluralizacja (Projektant O/R)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).

3. W menu **kompilacja** kliknij pozycję **Kompiluj UpdatingwithSProcsWalkthrough** , aby skompilować projekt.

4. Aby otworzyć okno **źródła danych** , w menu **dane** kliknij polecenie **Pokaż źródła danych**.

5. W oknie **źródła danych** kliknij pozycję **Dodaj nowe źródło danych**.

6. Kliknij pozycję **obiekt** na stronie **Wybierz typ źródła danych** , a następnie kliknij przycisk **dalej**.

7. Rozwiń węzeł **UpdatingwithSProcsWalkthrough** i Znajdź i wybierz klasę **Customer (klient** ).

    > [!NOTE]
    > Jeśli Klasa **Customer** jest niedostępna, Anuluj działanie kreatora, Skompiluj projekt i ponownie uruchom kreatora.
8. Kliknij przycisk **Zakończ** , aby utworzyć źródło danych i dodać klasę jednostki **klienta** do okna **źródła danych** .

## <a name="create-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Utwórz formant DataGridView, aby wyświetlić dane klienta w formularzu systemu Windows

Utwórz formanty, które są powiązane z klasami jednostek, przeciągając elementy LINQ to SQL źródła danych z okna **źródła danych** na formularz systemu Windows.

### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>Aby dodać formanty, które są powiązane z klasami jednostek

1. Otwórz **formularz Form1** w widok Projekt.

2. W oknie **źródła danych** przeciągnij węzeł **klienta** na **formularz Form1**.

    > [!NOTE]
    > Aby wyświetlić okno **źródła danych** , kliknij przycisk **Pokaż źródła danych** w menu **dane** .

3. Otwórz **formularz Form1** w edytorze kodu.

4. Dodaj następujący kod do formularza, który jest globalny do formularza, poza dowolną określoną metodą, ale wewnątrz `Form1` klasy:

    ```vb
    Private NorthwindDataContext1 As New NorthwindDataContext
    ```

    ```csharp
    private NorthwindDataContext northwindDataContext1
        = new NorthwindDataContext();
    ```

5. Utwórz procedurę obsługi zdarzeń dla `Form_Load` zdarzenia i Dodaj następujący kod do programu obsługi:

    ```vb
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers
    ```

    ```csharp
    customerBindingSource.DataSource
        = northwindDataContext1.Customers;
    ```

## <a name="implement-save-functionality"></a>Implementowanie funkcji zapisywania

Domyślnie przycisk Zapisz nie jest włączony i funkcja zapisywania nie jest zaimplementowana. Ponadto kod nie jest automatycznie dodawany do zapisywania zmienionych danych w bazie danych, gdy dla źródeł danych obiektów tworzone są kontrolki powiązane z danymi. W tej sekcji wyjaśniono, jak włączyć przycisk Zapisz i zaimplementować funkcję Save dla LINQ to SQL obiektów.

### <a name="to-implement-save-functionality"></a>Aby zaimplementować funkcję zapisywania

1. Otwórz **formularz Form1** w widok Projekt.

2. Wybierz przycisk Zapisz na **CustomerBindingNavigator** (przycisk z ikoną dyskietki).

3. W oknie **Właściwości** ustaw właściwość **Enabled** na **wartość true**.

4. Kliknij dwukrotnie przycisk Zapisz, aby utworzyć program obsługi zdarzeń i przełączyć się do edytora kodu.

5. Dodaj następujący kod do programu obsługi zdarzeń przycisku Zapisz:

    ```vb
    NorthwindDataContext1.SubmitChanges()
    ```

    ```csharp
    northwindDataContext1.SubmitChanges();
    ```

## <a name="override-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Zastąp domyślne zachowanie podczas wykonywania aktualizacji (wstawia, aktualizuje i usuwa)

### <a name="to-override-the-default-update-behavior"></a>Aby zastąpić domyślne zachowanie aktualizacji

1. Otwórz plik LINQ to SQL w **projektancie o/R**. (Kliknij dwukrotnie plik **Northwind. dbml** w **Eksplorator rozwiązań**).

2. W **Eksplorator serwera** lub **Eksplorator bazy danych**rozwiń węzeł **procedury składowane** bazy danych Northwind, a następnie zlokalizuj procedury składowane **InsertCustomers**, **UpdateCustomers**i **DeleteCustomers** .

3. Przeciągnij wszystkie trzy procedury składowane na **projektanta o/R**.

     Procedury składowane są dodawane do okienka metody jako <xref:System.Data.Linq.DataContext> metody. Aby uzyskać więcej informacji, zobacz [metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

4. Wybierz klasę jednostki **klienta** w **projektancie o/R**.

5. W oknie **Właściwości** wybierz właściwość **Wstaw** .

6. Kliknij przycisk wielokropka ( **...** ) obok pozycji **Użyj środowiska uruchomieniowego** , aby otworzyć okno dialogowe **Konfigurowanie zachowania** .

7. Wybierz **dostosować**.

8. Wybierz metodę **InsertCustomers** na liście **Dostosuj** .

9. Kliknij przycisk **Zastosuj** , aby zapisać konfigurację wybranej klasy i zachowania.

    > [!NOTE]
    > Można nadal skonfigurować zachowanie dla każdej kombinacji klas/zachowań, o ile po wprowadzeniu każdej zmiany klikniesz przycisk **Zastosuj** . Jeśli zmienisz klasę lub zachowanie przed kliknięciem przycisku **Zastosuj**, zostanie wyświetlone okno dialogowe z ostrzeżeniem z możliwością zastosowania wszelkich zmian.

10. Na liście **zachowanie** wybierz pozycję **Aktualizuj** .

11. Wybierz **dostosować**.

12. Wybierz metodę **UpdateCustomers** na liście **Dostosuj** .

     Sprawdź listę **argumentów metod** i **właściwości klasy** oraz Zwróć uwagę na to, że istnieją dwa **argumenty metody** i dwie **właściwości klasy** dla niektórych kolumn w tabeli. Ułatwia to śledzenie zmian i Tworzenie instrukcji, które sprawdzają naruszenia współbieżności.

13. Mapuj argument metody **Original_CustomerID** na właściwość klasy **CustomerID (oryginalna)** .

    > [!NOTE]
    > Domyślnie argumenty metody są mapowane na właściwości klasy, gdy nazwy są zgodne. Jeśli nazwy właściwości są zmieniane i nie są już zgodne między tabelą a klasą jednostki, może być konieczne wybranie równoważnej właściwości klasy do zamapowania, jeśli **Projektant o/R** nie może określić poprawnego mapowania. Ponadto jeśli argumenty metody nie mają prawidłowych właściwości klasy do zamapowania, można ustawić wartość **właściwości klasy** na **(brak)** .

14. Kliknij przycisk **Zastosuj** , aby zapisać konfigurację wybranej klasy i zachowania.

15. Na liście **zachowanie** wybierz pozycję **Usuń** .

16. Wybierz **dostosować**.

17. Wybierz metodę **DeleteCustomers** na liście **Dostosuj** .

18. Mapuj argument metody **Original_CustomerID** na właściwość klasy **CustomerID (oryginalna)** .

19. Kliknij przycisk **OK**.

> [!NOTE]
> Chociaż nie jest to problem z tym konkretnym instruktażem, warto zauważyć, że LINQ to SQL automatycznie obsługuje wartości generowane przez bazę danych dla tożsamości (Automatyczne zwiększenie), ROWGUIDCOL (GUID wygenerowanej przez bazę danych) i kolumn sygnatur czasowych podczas wstawiania i dostępności. Wartości wygenerowane przez bazę danych w innych typach kolumn nieoczekiwanie spowodują wartość null. Aby zwrócić wartości generowane przez bazę danych, należy ręcznie ustawić <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> na `true` i <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> jedną z następujących opcji: [AutoSync. Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync. OnInsert](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>)lub [AutoSync. OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

## <a name="test-the-application"></a>Testowanie aplikacji

Uruchom aplikację ponownie, aby sprawdzić, czy w ramach procedury składowanej **UpdateCustomers** prawidłowo Zaktualizowano rekord klienta w bazie danych.

1. Naciśnij klawisz **F5**.

2. Zmodyfikuj rekord w siatce, aby przetestować zachowanie aktualizacji.

3. Dodaj nowy rekord, aby przetestować zachowanie wstawiania.

4. Kliknij przycisk Zapisz, aby zapisać zmiany z powrotem w bazie danych.

5. Zamknij formularz.

6. Naciśnij klawisz **F5** i sprawdź, czy zaktualizowany rekord i nowo wstawionego rekordu zostały utrwalone.

7. Usuń nowy rekord utworzony w kroku 3, aby przetestować zachowanie usuwania.

8. Kliknij przycisk Zapisz, aby przesłać zmiany i usunąć usunięty rekord z bazy danych.

9. Zamknij formularz.

10. Naciśnij klawisz **F5** i sprawdź, czy usunięty rekord został usunięty z bazy danych.

    > [!NOTE]
    > Jeśli aplikacja używa wersji SQL Server Express, w zależności od wartości właściwości **Kopiuj do katalogu wyjściowego** pliku bazy danych, zmiany mogą nie pojawiać się po naciśnięciu klawisza **F5** w kroku 10.

## <a name="next-steps"></a>Następne kroki

W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po utworzeniu LINQ to SQL klas jednostek. Niektóre ulepszenia, które można wprowadzić w tej aplikacji, to m.in.:

- Zaimplementuj sprawdzanie współbieżności podczas aktualizacji. Aby uzyskać więcej informacji, zobacz [optymistyczne współbieżność: Omówienie](/dotnet/framework/data/adonet/sql/linq/optimistic-concurrency-overview).

- Dodaj zapytania LINQ do filtrowania danych. Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytańC#LINQ ()](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).

## <a name="see-also"></a>Zobacz także

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Metody DataContext](../data-tools/datacontext-methods-o-r-designer.md)
- [Instrukcje: Przypisz procedury składowane do wykonywania aktualizacji, wstawianych i usuwanych](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Zapytania LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/linq-to-sql-queries)