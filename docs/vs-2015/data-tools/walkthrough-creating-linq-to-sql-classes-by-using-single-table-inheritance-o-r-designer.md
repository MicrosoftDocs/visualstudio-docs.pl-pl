---
title: 'Wskazówki: tworzenie klas LINQ to SQL przy użyciu dziedziczenia pojedynczej tabeli (Projektant O-R) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 695378404e27b64f269fe4e9820b6b9e520c9d0f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660153"
---
# <a name="walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>Przewodnik: tworzenie klas LINQ to SQL przy użyciu dziedziczenia pojedynczej tabeli (Projektant O/R)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) obsługują dziedziczenie pojedynczej tabeli, ponieważ są one zazwyczaj zaimplementowane w systemach relacyjnych. Ten Instruktaż rozszerza się po ogólnych krokach przedstawionych w temacie [How to: Configure dziedziczenie przy użyciu projektanta o/R](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) i zawiera pewne prawdziwe dane, które pokazują, jak używać dziedziczenia w [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 W tym instruktażu wykonasz następujące zadania:

- Utwórz tabelę bazy danych i Dodaj do niej dane.

- Utwórz aplikację Windows Formsową.

- Dodaj plik [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] do projektu.

- Utwórz nowe klasy jednostek.

- Skonfiguruj klasy jednostek do używania dziedziczenia.

- Wykonaj zapytanie dotyczące dziedziczonej klasy.

- Wyświetl dane w formularzu systemu Windows.

## <a name="create-a-table-to-inherit-from"></a>Utwórz tabelę do dziedziczenia
 Aby zobaczyć, jak działa dziedziczenie, należy utworzyć małą tabelę osób, użyć jej jako klasy bazowej, a następnie utworzyć obiekt pracownika, który go dziedziczy.

#### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>Aby utworzyć tabelę bazową w celu zademonstrowania dziedziczenia

1. W **Eksplorator serwera** /**Eksplorator bazy danych**kliknij prawym przyciskiem myszy węzeł **tabele** , a następnie kliknij polecenie **Dodaj nową tabelę**.

    > [!NOTE]
    > Możesz użyć bazy danych Northwind lub innej bazy danych, do której można dodać tabelę.

2. W Projektancie tabel Dodaj następujące kolumny do tabeli:

    |Nazwa kolumny|Typ danych|Zezwalaj na wartości null|
    |-----------------|---------------|-----------------|
    |**#C1**|**int**|**False**|
    |**Wprowadź**|**int**|**Oznacza**|
    |**Imię**|**nvarchar (200)**|**False**|
    |**Nazwisko**|**nvarchar (200)**|**False**|
    |**Menedżera**|**int**|**Oznacza**|

3. Ustaw wartość kolumny ID jako klucz podstawowy.

4. Zapisz tabelę **i nadaj jej nazwę.**

## <a name="add-data-to-the-table"></a>Dodawanie danych do tabeli
 Aby można było sprawdzić, czy dziedziczenie jest prawidłowo skonfigurowane, tabela wymaga pewnych danych dla każdej klasy w dziedziczeniu pojedynczej tabeli.

#### <a name="to-add-data-to-the-table"></a>Aby dodać dane do tabeli

1. Otwórz tabelę w widoku danych. (Kliknij prawym przyciskiem myszy tabelę **Person** w **Eksplorator serwera** /**Eksplorator bazy danych** a następnie kliknij pozycję **Pokaż dane tabeli**.)

2. Skopiuj następujące dane do tabeli. (Można go skopiować, a następnie wkleić do tabeli, zaznaczając cały wiersz w okienku wyników).

    ||||||
    |-|-|-|-|-|
    |**#C1**|**Wprowadź**|**Imię**|**Nazwisko**|**Menedżera**|
    |**jedno**|**jedno**|**Anne**|**Wallace**|**NULL**|
    |**dwóch**|**jedno**|**Carlos**|**Grilo**|**NULL**|
    |**r.3**|**jedno**|**Yael**|**Peled**|**NULL**|
    |**czwart**|**dwóch**|**Gatis**|**Ozolins**|**jedno**|
    |**5000**|**dwóch**|**Panu**|**Hauser**|**jedno**|
    |**ust**|**dwóch**|**Tiffany**|**Phuvasate**|**jedno**|
    |**7**|**dwóch**|**Alexey**|**Orekhov**|**dwóch**|
    |**0,8**|**dwóch**|**Michał**|**Poliszkiewicz**|**dwóch**|
    |**9**|**dwóch**|**Pism**|**Yee**|**dwóch**|
    |**dziesięć**|**dwóch**|**Fabricio**|**Noriega**|**r.3**|
    |**11**|**dwóch**|**Mindy**|**Martin**|**r.3**|
    |**dwunastomiesięcznych**|**dwóch**|**Krzysztof**|**Kwok**|**r.3**|

## <a name="create-a-new-project"></a>Utwórz nowy projekt
 Po utworzeniu tabeli Utwórz nowy projekt, aby zademonstrować Konfigurowanie dziedziczenia.

#### <a name="to-create-the-new-windows-application"></a>Aby utworzyć nową aplikację systemu Windows

1. Z menu **plik** Utwórz nowy projekt.

2. Nazwij projekt **InheritanceWalkthrough**.

    > [!NOTE]
    > @No__t_0 jest obsługiwana w Visual Basic i C# projektach. Utwórz nowy projekt w jednym z tych języków.

3. Kliknij szablon **aplikacji Windows Forms** a następnie kliknij przycisk **OK**. Aby uzyskać więcej informacji, zobacz [aplikacje klienckie](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

4. Projekt InheritanceWalkthrough został utworzony i dodany do **Eksplorator rozwiązań**.

## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>Dodawanie pliku LINQ to SQL klas do projektu

#### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>Aby dodać plik LINQ to SQL do projektu

1. W menu **projekt** kliknij polecenie **Dodaj nowy element**.

2. Kliknij szablon **LINQ to SQL klasy** , a następnie kliknij przycisk **Dodaj**.

     Plik. dbml zostanie dodany do projektu i zostanie otwarty [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

## <a name="create-the-inheritance-by-using-the-or-designer"></a>Tworzenie dziedziczenia przy użyciu projektanta O/R
 Skonfiguruj dziedziczenie, przeciągając obiekt **dziedziczenia** z **przybornika** na powierzchnię projektu.

#### <a name="to-create-the-inheritance"></a>Aby utworzyć dziedziczenie

1. W **Eksplorator serwera** /**Eksplorator bazy danych**przejdź do utworzonej wcześniej tabeli **Person** .

2. Przeciągnij tabelę **Person** na powierzchnię projektu [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

3. Przeciągnij drugą tabelę **osób** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] i zmień jej nazwę na **pracownika**.

4. Usuń właściwość **Menedżera** z obiektu **osoba** .

5. Usuń właściwości **Type**, **ID**, **FirstName**i **LastName** z obiektu **Employee** . (Innymi słowy, Usuń wszystkie właściwości poza **menedżerem**).

6. Na karcie **Object Relational Designer** **przybornika**Utwórz **dziedziczenie** między obiektami **osoby** i **pracownika** . Aby to zrobić, kliknij element **dziedziczenia** w **przyborniku** i zwolnij przycisk myszy. Następnie kliknij obiekt **Employee** , a następnie obiekt **Person** w [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Strzałka w linii dziedziczenia wskaże obiekt **osoby** .

7. Kliknij linię **dziedziczenia** na powierzchni projektowej.

8. Ustaw właściwość **właściwości rozróżniacza** na **Typ**.

9. Ustaw właściwość **wartość rozróżniacza klasy pochodnej** na **2**.

10. Ustaw właściwość **wartość rozróżniacza klasy bazowej** na **1**.

11. Ustaw **domyślną właściwość dziedziczenia** na **Person**.

12. Skompiluj projekt.

## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>Wykonaj zapytanie dotyczące dziedziczonej klasy i Wyświetl dane w formularzu
 Teraz dodasz kod do formularza służącego do wykonywania zapytań dotyczących określonej klasy w modelu obiektów.

#### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>Aby utworzyć zapytanie LINQ i wyświetlić wyniki w formularzu

1. Przeciągnij element **ListBox** na formularz Form1.

2. Kliknij dwukrotnie formularz, aby utworzyć procedurę obsługi zdarzeń `Form1_Load`.

3. Dodaj następujący kod do programu obsługi zdarzeń `Form1_Load`:

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
 Uruchom aplikację i sprawdź, czy rekordy wyświetlane w polu listy to wszyscy pracownicy (rekordy mające wartość 2 w kolumnie Typ).

#### <a name="to-test-the-application"></a>Aby przetestować aplikację

1. Naciśnij F5.

2. Sprawdź, czy są wyświetlane tylko rekordy, które mają wartość 2 w kolumnie Typ.

3. Zamknij formularz. (W menu **debugowanie** kliknij polecenie **Zatrzymaj debugowanie**).

## <a name="see-also"></a>Zobacz też
 [LINQ to SQL narzędzia w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [: Dodawanie klas LINQ to SQL do projektu (Projektant-r Designer)](https://msdn.microsoft.com/library/7bb184ab-ec54-4cda-b706-604b2b4a3ed6) wskazówki [: tworzenie klas LINQ to SQL (Projektant o-r Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [instrukcje: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawianych i usuwanych (o/r Projektant)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [instrukcje: generowanie modelu obiektów w Visual Basic lub C# ](https://msdn.microsoft.com/library/a0c73b33-5650-420c-b9dc-f49310c201ee)
