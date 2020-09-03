---
title: Utwórz plik bazy danych i użyj projektanta tabel
description: Samouczek opisujący sposób dodawania tabel i kluczy obcych do bazy danych przy użyciu projektanta tabel w programie Visual Studio. Przedstawiono w nim również sposób dodawania danych za pomocą interfejsu graficznego.
ms.date: 09/19/2019
ms.topic: conceptual
helpviewer_keywords:
- database tables, creating
- database files, creating
- table designer
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e31be90ff24f110fda66449187d3372976f269a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282725"
---
# <a name="create-a-database-and-add-tables-in-visual-studio"></a>Tworzenie bazy danych i Dodawanie tabel w programie Visual Studio

Możesz użyć programu Visual Studio do utworzenia i zaktualizowania lokalnego pliku bazy danych w SQL Server Express LocalDB. Bazę danych można również utworzyć, wykonując instrukcje języka Transact-SQL w oknie narzędzia **Eksplorator obiektów SQL Server** w programie Visual Studio. W tym temacie utworzymy plik *. mdf* i dodamy tabele i klucze przy użyciu projektanta tabel.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, konieczne będzie zainstalowanie **aplikacji klasycznych platformy .NET** oraz obciążeń związanych z tworzeniem **i przetwarzaniem danych** w programie Visual Studio. Aby je zainstalować, Otwórz **Instalator programu Visual Studio** a następnie wybierz pozycję **Modyfikuj** (lub **więcej**  >  **modyfikacji**) obok wersji programu Visual Studio, którą chcesz zmodyfikować.

> [!NOTE]
> Procedury przedstawione w tym artykule dotyczą tylko .NET Framework projektów Windows Forms, a nie do projektów Windows Forms .NET Core.

## <a name="create-a-project-and-a-local-database-file"></a>Tworzenie projektu i pliku lokalnej bazy danych

1. Utwórz nowy projekt **aplikacji Windows Forms (.NET Framework)** i nadaj mu nazwę **SampleDatabaseWalkthrough**.

2. Na pasku menu wybierz pozycję **projekt**  >  **Dodaj nowy element**.

3. Na liście szablonów elementów przewiń w dół i wybierz pozycję **baza danych oparta na usłudze**.

   ![Szablony elementów — okno dialogowe](../data-tools/media/raddata-vsitemtemplates.png)

4. Nazwij bazę danych **SampleDatabase**, a następnie kliknij przycisk **Dodaj**.

### <a name="add-a-data-source"></a>Dodawanie źródła danych

1. Jeśli okno **źródła danych** nie jest otwarte, otwórz je, naciskając klawisz **SHIFT** + **Alt** + **D** lub wybierając pozycję **Wyświetl**  >  **inne**  >  **źródła danych** systemu Windows na pasku menu.

1. W oknie **źródła danych** wybierz pozycję **Dodaj nowe źródło danych**.

   ![Dodawanie nowego źródła danych w programie Visual Studio](media/add-new-data-source.png)

   Zostanie otwarty **Kreator konfiguracji źródła danych** .

1. Na stronie **Wybierz typ źródła danych** wybierz pozycję **baza danych** , a następnie wybierz przycisk **dalej**.

1. Na stronie **Wybierz model bazy danych** wybierz pozycję **dalej** , aby zaakceptować wartość domyślną (DataSet).

1. Na stronie **Wybierz połączenie danych** wybierz plik **SampleDatabase. mdf** z listy rozwijanej, a następnie wybierz przycisk **dalej**.

1. Na stronie **Zapisz parametry połączenia do pliku konfiguracji aplikacji** wybierz pozycję **dalej**.

1. Na stronie **Wybierz obiekty bazy danych** zobaczysz komunikat informujący, że baza danych nie zawiera żadnych obiektów. Wybierz pozycję **Zakończ**.

### <a name="view-properties-of-the-data-connection"></a>Wyświetl właściwości połączenia danych

Parametry połączenia dla pliku *SampleDatabase. mdf* można wyświetlić, otwierając okno właściwości połączenia danych:

- Wybierz pozycję **Wyświetl**  >  **Eksplorator obiektów SQL Server** , aby otworzyć okno **Eksplorator obiektów SQL Server** . Rozwiń **(LocalDB) \MSSQLLocalDB**  >  **bazy danych**, a następnie kliknij prawym przyciskiem myszy *SampleDatabase. mdf* i wybierz pozycję **Właściwości**.

- Alternatywnie możesz wybrać opcję **Wyświetl**  >  **Eksplorator serwera**, jeśli to okno nie jest jeszcze otwarte. Otwórz okno Właściwości, rozwijając węzeł **połączenia danych** , kliknij prawym przyciskiem myszy pozycję *SampleDatabase. mdf*, a następnie wybierz polecenie **Właściwości**.

  > [!TIP]
  > Jeśli nie można rozwinąć węzła połączenia danych lub nie ma na liście połączenia SampleDatabase. mdf, wybierz przycisk **Połącz z bazą danych** na pasku narzędzi Eksplorator serwera. W oknie dialogowym **Dodawanie połączenia** upewnij się, że w obszarze **Źródło danych**została wybrana opcja **Microsoft SQL Server plik bazy danych** , a następnie wyszukaj i wybierz plik SampleDatabase. mdf. Zakończ Dodawanie połączenia, wybierając **przycisk OK**.

## <a name="create-tables-and-keys-by-using-table-designer"></a>Tworzenie tabel i kluczy za pomocą projektanta tabel

W tej sekcji utworzysz dwie tabele, klucz podstawowy w każdej tabeli i kilka wierszy przykładowych danych. Utworzysz również klucz obcy, aby określić, jak rekordy w jednej tabeli odpowiadają rekordom w drugiej tabeli.

### <a name="create-the-customers-table"></a>Tworzenie tabeli Customers

1. W **Eksplorator serwera**rozwiń węzeł **połączenia danych** , a następnie rozwiń węzeł **SampleDatabase. mdf** .

   Jeśli nie można rozwinąć węzła połączenia danych lub nie ma na liście połączenia SampleDatabase. mdf, wybierz przycisk **Połącz z bazą danych** na pasku narzędzi Eksplorator serwera. W oknie dialogowym **Dodawanie połączenia** upewnij się, że w obszarze **Źródło danych**została wybrana opcja **Microsoft SQL Server plik bazy danych** , a następnie wyszukaj i wybierz plik SampleDatabase. mdf. Zakończ Dodawanie połączenia, wybierając **przycisk OK**.

2. Kliknij prawym przyciskiem myszy pozycję **tabele** i wybierz polecenie **Dodaj nową tabelę**.

   Zostanie otwarty projektant tabel i zostanie wyświetlona siatka z jednym wierszem domyślnym, który reprezentuje pojedynczą kolumnę w tworzonej tabeli. Przez dodawanie wierszy do siatki dodajesz kolumny w tabeli.

3. W siatce dodaj wiersz dla każdego z poniższych wpisów:

   |Nazwa kolumny|Typ danych|Zezwalaj na wartości null|
   |-----------------|---------------|-----------------|
   |`CustomerID`|`nchar(5)`|False (usunięty)|
   |`CompanyName`|`nvarchar(50)`|False (usunięty)|
   |`ContactName`|`nvarchar (50)`|True (wybrane)|
   |`Phone`|`nvarchar (24)`|True (wybrane)|

4. Kliknij prawym przyciskiem myszy `CustomerID` wiersz, a następnie wybierz pozycję **Ustaw klucz podstawowy**.

5. Kliknij prawym przyciskiem myszy wiersz domyślny ( `Id` ), a następnie wybierz polecenie **Usuń**.

6. Nadaj tabeli nazwę Customers, aktualizując pierwszy wiersz w okienku skryptu, aby dopasować następujący przykład:

   ```sql
   CREATE TABLE [dbo].[Customers]
   ```

   Powinny zostać wyświetlone informacje podobne do następujących:

   ![Projektant tabel](../data-tools/media/table-designer.png)

7. W lewym górnym rogu **projektanta tabeli**wybierz pozycję **Aktualizuj**.

8. W oknie dialogowym **Podgląd aktualizacji bazy danych** wybierz pozycję **Aktualizuj bazę danych**.

   Tabela Customers jest tworzona w lokalnym pliku bazy danych.

### <a name="create-the-orders-table"></a>Tworzenie tabeli Orders

1. Dodaj inną tabelę, a następnie dodaj wiersz dla każdego wpisu w tabeli poniżej:

   |Nazwa kolumny|Typ danych|Zezwalaj na wartości null|
   |-----------------|---------------|-----------------|
   |`OrderID`|`int`|False (usunięty)|
   |`CustomerID`|`nchar(5)`|False (usunięty)|
   |`OrderDate`|`datetime`|True (wybrane)|
   |`OrderQuantity`|`int`|True (wybrane)|

2. Ustaw pozycję **IDZamówienia** jako klucz podstawowy, a następnie Usuń wiersz domyślny.

3. Nadaj tabeli nazwę Orders, aktualizując pierwszy wiersz w okienku skryptu, aby dopasować następujący przykład:

   ```sql
   CREATE TABLE [dbo].[Orders]
   ```

4. W lewym górnym rogu **projektanta tabel**wybierz pozycję **Aktualizuj**.

5. W oknie dialogowym **Podgląd aktualizacji bazy danych** wybierz pozycję **Aktualizuj bazę danych**.

   Tabela Orders jest tworzona w lokalnym pliku bazy danych. Jeśli rozszerzasz węzeł **tabele** w Eksplorator serwera, zobaczysz dwie tabele:

   ![Węzeł tabel rozwinięty w Eksplorator serwera](media/server-explorer-tables-node.png)

### <a name="create-a-foreign-key"></a>Tworzenie klucza obcego

1. W okienku kontekstowym po prawej stronie siatki projektanta tabel dla tabeli Orders (zamówienia) kliknij prawym przyciskiem myszy pozycję **klucze obce** i wybierz polecenie **Dodaj nowy klucz obcy**.

   ![Dodawanie klucza obcego w Projektancie tabel w programie Visual Studio](../data-tools/media/add-foreign-key.png)

2. W wyświetlonym polu tekstowym Zamień tekst **ToTable** na **klientów**.

3. W okienku T-SQL zaktualizuj ostatni wiersz, aby dopasować go do poniższego przykładu:

   ```sql
   CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])
   ```

4. W lewym górnym rogu **projektanta tabel**wybierz pozycję **Aktualizuj**.

5. W oknie dialogowym **Podgląd aktualizacji bazy danych** wybierz pozycję **Aktualizuj bazę danych**.

   Zostanie utworzony klucz obcy.

## <a name="populate-the-tables-with-data"></a>Wypełnianie tabel danymi

1. W **Eksplorator serwera** lub **Eksplorator obiektów SQL Server**rozwiń węzeł przykładowej bazy danych.

2. Otwórz menu skrótów dla węzła **tabele** , wybierz **Odśwież**, a następnie rozwiń węzeł **tabele** .

3. Otwórz menu skrótów dla tabeli Customers, a następnie wybierz polecenie **Pokaż dane tabeli**.

4. Dodaj dowolne dane dla niektórych klientów.

    Można określić dowolne pięć znaków jako identyfikatory klienta, ale należy wybrać co najmniej jeden, który można zapamiętać do użycia w dalszej części tej procedury.

5. Otwórz menu skrótów dla tabeli Orders, a następnie wybierz polecenie **Pokaż dane tabeli**.

6. Dodaj dane dla niektórych zamówień.

    > [!IMPORTANT]
    > Upewnij się, że wszystkie identyfikatory zamówień i ilości zamówień są liczbami całkowitymi i że każdy identyfikator klienta odpowiada wartości określonej w kolumnie **IDKlienta** tabeli Customers.

7. Na pasku menu wybierz pozycję **plik**  >  **Zapisz wszystko**.

## <a name="see-also"></a>Zobacz też

- [Uzyskiwanie dostępu do danych w programie Visual Studio](accessing-data-in-visual-studio.md)
