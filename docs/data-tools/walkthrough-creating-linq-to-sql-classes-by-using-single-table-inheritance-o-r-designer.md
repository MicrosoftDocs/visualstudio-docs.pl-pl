---
title: Klasy LINQ to SQL z dziedziczeniem pojedynczej tabeli
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b0b5319cb36179e51b34eacce56282b97ad4a4bb
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036759"
---
# <a name="walkthrough-create-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>Przewodnik: tworzenie klas LINQ to SQL przy użyciu dziedziczenia pojedynczej tabeli (Projektant O/R)
[Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) obsługują dziedziczenie pojedynczej tabeli, ponieważ są one zazwyczaj zaimplementowane w systemach relacyjnych. W tym instruktażu rozwijane są ogólne kroki opisane w temacie [How to: Configure dziedziczenie przy użyciu projektanta o/R](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) i zawiera pewne prawdziwe dane umożliwiające zaprezentowanie użycia dziedziczenia w programie [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] .

W tym instruktażu wykonasz następujące zadania:

- Utwórz tabelę bazy danych i Dodaj do niej dane.

- Utwórz aplikację Windows Formsową.

- Dodaj [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] plik do projektu.

- Utwórz nowe klasy jednostek.

- Skonfiguruj klasy jednostek do używania dziedziczenia.

- Wykonaj zapytanie dotyczące dziedziczonej klasy.

- Wyświetl dane w formularzu systemu Windows.

## <a name="create-a-table-to-inherit-from"></a>Utwórz tabelę do dziedziczenia
Aby zobaczyć, jak działa dziedziczenie, należy utworzyć małą `Person` tabelę, użyć jej jako klasy bazowej, a następnie utworzyć `Employee` obiekt, który z niego dziedziczy.

### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>Aby utworzyć tabelę bazową w celu zademonstrowania dziedziczenia

1. W **Eksplorator serwera** lub **Eksplorator bazy danych**, kliknij prawym przyciskiem myszy węzeł **tabele** , a następnie kliknij polecenie **Dodaj nową tabelę**.

    > [!NOTE]
    > Możesz użyć bazy danych Northwind lub innej bazy danych, do której można dodać tabelę.

2. W **Projektancie tabel**Dodaj następujące kolumny do tabeli:

    |Nazwa kolumny|Typ danych|Zezwalaj na wartości null|
    |-----------------|---------------|-----------------|
    |**ID (Identyfikator)**|**int**|**False**|
    |**Typ**|**int**|**True**|
    |**FirstName (Imię)**|**nvarchar (200)**|**False**|
    |**LastName (Nazwisko)**|**nvarchar (200)**|**False**|
    |**Manager**|**int**|**True**|

3. Ustaw wartość kolumny ID jako klucz podstawowy.

4. Zapisz tabelę **i nadaj jej nazwę.**

## <a name="add-data-to-the-table"></a>Dodawanie danych do tabeli
Aby można było sprawdzić, czy dziedziczenie jest prawidłowo skonfigurowane, tabela wymaga pewnych danych dla każdej klasy w dziedziczeniu pojedynczej tabeli.

### <a name="to-add-data-to-the-table"></a>Aby dodać dane do tabeli

1. Otwórz tabelę w widoku danych. (Kliknij prawym przyciskiem myszy tabelę **osoby** w **Eksplorator serwera** lub **Eksplorator bazy danych** a następnie kliknij polecenie **Pokaż dane tabeli**.)

2. Skopiuj następujące dane do tabeli. (Można go skopiować, a następnie wkleić do tabeli, zaznaczając cały wiersz w okienku **wyników** ).

    |**ID (Identyfikator)**|**Typ**|**FirstName (Imię)**|**LastName (Nazwisko)**|**Manager**|
    |-|-|-|-|-|
    |**1**|**1**|**Anne**|**Wallace**|**NULL**|
    |**2**|**1**|**Carlos**|**Grilo**|**NULL**|
    |**3**|**1**|**Yael**|**Peled**|**NULL**|
    |**4**|**2**|**Gatis**|**Ozolins**|**1**|
    |**5**|**2**|**Panu**|**Hauser**|**1**|
    |**6**|**2**|**Tiffany**|**Phuvasate**|**1**|
    |**7**|**2**|**Alexey**|**Orekhov**|**2**|
    |**8**|**2**|**Michał**|**Poliszkiewicz**|**2**|
    |**9**|**2**|**Pism**|**Yee**|**2**|
    |**10**|**2**|**Fabricio**|**Noriega**|**3**|
    |**11**|**2**|**Mindy**|**Martin**|**3**|
    |**12**|**2**|**Krzysztof**|**Kwok**|**3**|

## <a name="create-a-new-project"></a>Tworzenie nowego projektu
Po utworzeniu tabeli Utwórz nowy projekt, aby zademonstrować Konfigurowanie dziedziczenia.

### <a name="to-create-the-new-windows-forms-application"></a>Aby utworzyć nową aplikację Windows Forms

1. W programie Visual Studio w menu **plik** wybierz pozycję **Nowy**  >  **projekt**.

2. Rozwiń pozycję **Visual C#** lub **Visual Basic** w okienku po lewej stronie, a następnie wybierz pozycję **Windows Desktop**.

3. W środkowym okienku wybierz typ projektu **aplikacji Windows Forms** .

4. Nazwij projekt **InheritanceWalkthrough**, a następnie wybierz przycisk **OK**.

     Projekt **InheritanceWalkthrough** został utworzony i dodany do **Eksplorator rozwiązań**.

## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>Dodawanie pliku LINQ to SQL klas do projektu

### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>Aby dodać plik LINQ to SQL do projektu

1. W menu **projekt** kliknij polecenie **Dodaj nowy element**.

2. Kliknij szablon **LINQ to SQL klasy** , a następnie kliknij przycisk **Dodaj**.

     Plik *. dbml* jest dodawany do projektu i zostanie otwarty **Projektant o/R** .

## <a name="create-the-inheritance-by-using-the-or-designer"></a>Tworzenie dziedziczenia przy użyciu projektanta O/R
Skonfiguruj dziedziczenie, przeciągając obiekt **dziedziczenia** z **przybornika** na powierzchnię projektu.

### <a name="to-create-the-inheritance"></a>Aby utworzyć dziedziczenie

1. W **Eksplorator serwera** lub **Eksplorator bazy danych**przejdź do utworzonej wcześniej tabeli **Person** .

2. Przeciągnij tabelę **Person** na powierzchnię projektu **projektanta o/R** .

3. Przeciągnij drugą tabelę **osób** do **projektanta o/R** i zmień jej nazwę na **pracownika**.

4. Usuń właściwość **Menedżera** z obiektu **osoba** .

5. Usuń właściwości **Type**, **ID**, **FirstName**i **LastName** z obiektu **Employee** . (Innymi słowy, Usuń wszystkie właściwości poza **menedżerem**).

6. Na karcie **Object Relational Designer** **przybornika**Utwórz **dziedziczenie** między obiektami **osoby** i **pracownika** . Aby to zrobić, kliknij element **dziedziczenia** w **przyborniku** i zwolnij przycisk myszy. Następnie kliknij obiekt **Employee** , a następnie obiekt **osoba** w **Projektancie O/R**. Strzałka w linii dziedziczenia wskazuje obiekt **osoby** .

7. Kliknij linię **dziedziczenia** na powierzchni projektowej.

8. Ustaw właściwość **właściwości rozróżniacza** na **Typ**.

9. Ustaw właściwość **wartość rozróżniacza klasy pochodnej** na **2**.

10. Ustaw właściwość **wartość rozróżniacza klasy bazowej** na **1**.

11. Ustaw **domyślną właściwość dziedziczenia** na **Person**.

12. Skompiluj projekt.

## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>Wykonaj zapytanie dotyczące dziedziczonej klasy i Wyświetl dane w formularzu
Teraz można dodać kod do formularza, który wykonuje zapytania dotyczące określonej klasy w modelu obiektów.

### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>Aby utworzyć zapytanie LINQ i wyświetlić wyniki w formularzu

1. Przeciągnij element **ListBox** na **formularz Form1**.

2. Kliknij dwukrotnie formularz, aby utworzyć `Form1_Load` procedurę obsługi zdarzeń.

3. Dodaj następujący kod do `Form1_Load` programu obsługi zdarzeń:

    ```vb
    Dim dc As New DataClasses1DataContext
    Dim results = From emp In dc.Persons _
        Where TypeOf emp Is Employee _
        Select emp

    For Each Emp As Employee In results
        ListBox1.Items.Add(Emp.LastName)
    Next
    ```

    ```csharp
    NorthwindDataContext dc = new DataClasses1DataContext();
    var results = from emp in dc.Persons
                  where emp is Employee
                  select emp;

    foreach(Employee Emp in results)
    {
        listBox1.Items.Add(Emp.LastName)
    }
    ```

## <a name="test-the-application"></a>Testowanie aplikacji
Uruchom aplikację i sprawdź, czy rekordy wyświetlane w polu listy to wszyscy pracownicy (rekordy mające wartość 2 w kolumnie **Typ** ).

### <a name="to-test-the-application"></a>Aby przetestować aplikację

1. Naciśnij klawisz **F5**.

2. Sprawdź, czy są wyświetlane tylko rekordy, które mają wartość 2 w kolumnie **Typ** .

3. Zamknij formularz. (W menu **debugowanie** kliknij polecenie **Zatrzymaj debugowanie**).

## <a name="see-also"></a>Zobacz także

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Przewodnik: tworzenie klas LINQ to SQL (Projektant O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Instrukcje: przypisywanie procedur składowanych na potrzeby wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ do SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Instrukcje: Generowanie modelu obiektów w Visual Basic lub C #](/dotnet/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp)
