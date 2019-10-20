---
title: Tworzenie bazy danych SQL przy użyciu projektanta | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- SQL Server Express
- local data
- LocalDB
- SQLEXPRESS
- data [Visual Studio], Local data
- SQL Express
- data [Visual Studio], walkthroughs
- databases, creating
- database files, creating
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
caps.latest.revision: 54
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 33b97050f04fd23a9fa3b6c3c641faa5dfe4802f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651060"
---
# <a name="create-a-sql-database-by-using-a-designer"></a>Tworzenie bazy danych SQL za pomocą projektanta
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz eksplorować podstawowe zadania, takie jak Dodawanie tabel i Definiowanie kolumn, przy użyciu programu Visual Studio do tworzenia i aktualizowania lokalnego pliku bazy danych w SQL Server Express LocalDB. Po zakończeniu tego instruktażu można odkryć więcej zaawansowanych możliwości przy użyciu lokalnej bazy danych jako punkt wyjścia dla innych instruktaży, które tego wymagają.

 Bazę danych można również utworzyć przy użyciu SQL Server Management Studio (oddzielnego pobierania) lub instrukcji języka Transact-SQL w oknie narzędzia **Eksplorator obiektów SQL Server** w programie Visual Studio.

 W czasie instruktażu dowiesz się o następujących zadaniach:

- [Tworzenie projektu i pliku lokalnej bazy danych](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewSQLDB)

- [Tworzenie tabel, kolumn, kluczy podstawowych i kluczy obcych](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewTbls)

- [Wypełnianie tabel danymi](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_Populating)

## <a name="prerequisites"></a>Wymagania wstępne
 Aby ukończyć ten przewodnik, upewnij się, że zainstalowano narzędzia do SQL Server Data Tools. W menu **Widok** powinien zostać wyświetlony **Eksplorator obiektów SQL Server**. Jeśli go nie ma, przejdź do pozycji **Dodaj lub usuń programy**, kliknij pozycję **Visual Studio 2015**, wybierz pozycję **Zmień**, a następnie zaznacz pole wyboru obok **SQL Server narzędzia danych**.

## <a name="BKMK_CreateNewSQLDB"></a>Tworzenie projektu i pliku lokalnej bazy danych

#### <a name="to-create-a-project-and-a-database-file"></a>Aby utworzyć projekt i plik bazy danych

1. Utwórz projekt Windows Forms o nazwie `SampleDatabaseWalkthrough`.

2. Na pasku menu wybierz pozycję **projekt**  > **Dodaj nowy element**.

3. Na liście szablonów elementów przewiń w dół i wybierz pozycję **baza danych oparta na usłudze**.

    ![Szablony elementów — okno dialogowe](../data-tools/media/raddata-vsitemtemplates.png "raddata VSItemTemplates")

4. Nazwij bazę danych **SampleDatabase**, a następnie wybierz przycisk **Dodaj** .

5. Jeśli okno **źródła danych** nie jest otwarte, otwórz je, wybierając klawisze Shift + Alt + D lub na pasku menu wybierz opcję **Wyświetl**  >  inne**źródła danych** **systemu Windows**  > .

6. W oknie **źródła danych** wybierz łącze **Dodaj nowe źródło danych** .

7. W **Kreatorze konfiguracji źródła danych**wybierz przycisk **dalej** cztery razy, aby zaakceptować ustawienia domyślne, a następnie wybierz przycisk **Zakończ** .

   Otwierając okno właściwości bazy danych, możesz wyświetlić parametry połączenia i lokalizację głównego pliku bazy danych (mdf). Zobaczysz, że plik bazy danych znajduje się w folderze projektu.

- W programie Visual Studio wybierz pozycję **wyświetl**  > **Eksplorator obiektów SQL Server** , jeśli to okno nie jest jeszcze otwarte. Otwórz okno właściwości, rozwijając węzeł **połączenia danych** , otwierając menu skrótów dla SampleDatabase. mdf, a następnie wybierając **Właściwości**.

- Alternatywnie można wybrać opcję **wyświetl**  > **Eksplorator serwera**, jeśli to okno nie jest jeszcze otwarte. Otwórz okno właściwości, rozwijając węzeł **połączenia danych** . Otwórz menu skrótów dla SampleDatabase. mdf, a następnie wybierz polecenie **Właściwości**.

## <a name="BKMK_CreateNewTbls"></a>Tworzenie tabel, kolumn, kluczy podstawowych i kluczy obcych
 W tej sekcji utworzysz kilka tabel, klucz podstawowy w każdej tabeli i kilka wierszy przykładowych danych. W następnym instruktażu dowiesz się, jak te informacje mogą pojawiać się w aplikacji. Utworzysz też klucz obcy, aby określić, jak rekordy w jednej tabeli mogą odpowiadać rekordom w drugiej tabeli.

#### <a name="to-create-the-customers-table"></a>Aby utworzyć tabelę Customers

1. W **Eksplorator serwera** lub **Eksplorator obiektów SQL Server**rozwiń węzeł **połączenia danych** , a następnie rozwiń węzeł **SampleDatabase. mdf** .

2. Otwórz menu skrótów dla **tabel**, a następnie wybierz polecenie **Dodaj nową tabelę**.

     Zostanie otwarty **Projektant tabel** i zostanie wyświetlona siatka z jednym wierszem domyślnym, który reprezentuje pojedynczą kolumnę w tworzonej tabeli. Przez dodawanie wierszy do siatki dodajesz kolumny w tabeli.

3. W siatce dodaj wiersz dla każdego z poniższych wpisów:

    |Nazwa kolumny|Typ danych|Zezwalaj na wartości null|
    |-----------------|---------------|-----------------|
    |`CustomerID`|`nchar(5)`|False (usunięty)|
    |`CompanyName`|`nvarchar(50)`|False (usunięty)|
    |`ContactName`|`nvarchar (50)`|True (wybrane)|
    |`Phone`|`nvarchar (24)`|True (wybrane)|

4. Otwórz menu skrótów dla wiersza `CustomerID`, a następnie wybierz pozycję **Ustaw klucz podstawowy**.

5. Otwórz menu skrótów dla wiersza domyślnego, a następnie wybierz polecenie **Usuń**.

6. Nadaj tabeli nazwę Customers, aktualizując pierwszy wiersz w okienku skryptu, aby dopasować następujący przykład:

    ```
    CREATE TABLE [dbo].[Customers]
    ```

     Powinieneś wyglądać następująco:

     ![Projektant tabel](../data-tools/media/raddata-table-designer.png "Projektant tabel raddata")

7. W lewym górnym rogu **projektanta tabel**, wybierz przycisk **Aktualizuj** .

8. W oknie dialogowym **Podgląd aktualizacji bazy danych** wybierz przycisk **Aktualizuj bazę danych** .

     Wprowadzone zmiany są zapisywane w lokalnym pliku bazy danych.

#### <a name="to-create-the-orders-table"></a>Aby utworzyć tabelę Orders

1. Dodaj inną tabelę, a następnie dodaj wiersz dla każdego wpisu w tabeli poniżej:

    |Nazwa kolumny|Typ danych|Zezwalaj na wartości null|
    |-----------------|---------------|-----------------|
    |`OrderID`|`int`|False (usunięty)|
    |`CustomerID`|`nchar(5)`|False (usunięty)|
    |`OrderDate`|`datetime`|True (wybrane)|
    |`OrderQuantity`|`int`|True (wybrane)|

2. Ustaw pozycję **IDZamówienia** jako klucz podstawowy, a następnie Usuń wiersz domyślny.

3. Nadaj tabeli nazwę Orders, aktualizując pierwszy wiersz w okienku skryptu, aby dopasować następujący przykład:

    ```
    CREATE TABLE [dbo].[Orders]
    ```

4. W lewym górnym rogu **projektanta tabel**, wybierz przycisk **Aktualizuj** .

5. W oknie dialogowym **Podgląd aktualizacji bazy danych** wybierz przycisk **Aktualizuj bazę danych** .

     Wprowadzone zmiany są zapisywane w lokalnym pliku bazy danych.

#### <a name="to-create-a-foreign-key"></a>Aby utworzyć obcy klucz

1. W okienku kontekstowym po prawej stronie siatki, otwórz menu skrótów dla **kluczy obcych**, a następnie wybierz polecenie **Dodaj nowy klucz obcy**, jak pokazano na poniższej ilustracji.

     ![Dodawanie klucza obcego w Projektancie tabel](../data-tools/media/foreignkey.png "ForeignKey")

2. W wyświetlonym polu tekstowym Zamień **ToTable** na `Customers`.

3. W okienku T-SQL zaktualizuj ostatni wiersz, aby dopasować go do poniższego przykładu:

    ```
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])
    ```

4. W lewym górnym rogu **projektanta tabel**, wybierz przycisk **Aktualizuj** .

5. W oknie dialogowym **Podgląd aktualizacji bazy danych** wybierz przycisk **Aktualizuj bazę danych** .

     Wprowadzone zmiany są zapisywane w lokalnym pliku bazy danych.

## <a name="BKMK_Populating"></a>Wypełnianie tabel danymi

#### <a name="to-populate-the-tables-with-data"></a>Aby wypełnić tabele danymi

1. W **Eksplorator serwera** lub **Eksplorator obiektów SQL Server**rozwiń węzeł przykładowej bazy danych.

2. Otwórz menu skrótów dla węzła **tabele** , wybierz **Odśwież**, a następnie rozwiń węzeł **tabele** .

3. Otwórz menu skrótów dla tabeli Customers, a następnie wybierz polecenie **Pokaż dane tabeli**.

4. Dodaj wszelkie dane, jakie chcesz dla co najmniej trzech klientów.

     Można określić dowolne pięć znaków jako identyfikatory klienta, ale należy wybrać co najmniej jeden, który można zapamiętać do użycia w dalszej części tej procedury.

5. Otwórz menu skrótów dla tabeli Orders, a następnie wybierz polecenie **Pokaż dane tabeli**.

6. Dodawanie danych dla co najmniej trzech zamówień.

    > [!IMPORTANT]
    > Upewnij się, że wszystkie identyfikatory zamówień i ilości zamówienia są liczbami całkowitymi i że każdy identyfikator klienta odpowiada wartości określonej w kolumnie CustomerID w tabeli Customers.

7. Na pasku menu wybierz pozycję **plik**  > **Zapisz wszystko**.

8. Na pasku menu wybierz pozycję **plik**  > **Zamknij rozwiązanie**.

    > [!NOTE]
    > Zgodnie z zaleceniami można zrobić kopię zapasową pliku bazy danych, która właśnie została utworzona przez skopiowanie jej i następnie wklejenie kopii w innej lokalizacji lub nadając kopii pod inną nazwą.

## <a name="next-steps"></a>Następne kroki
 Teraz, gdy masz plik lokalnej bazy danych z niektórymi przykładowymi danymi, możesz wykonać dowolne z instruktaży, które demonstrują zadania bazy danych.
