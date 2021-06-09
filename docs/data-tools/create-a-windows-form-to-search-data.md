---
title: Tworzenie formularza Windows Forms na potrzeby wyszukiwania danych
description: Przeczytaj przykład sposobu tworzenia formularza systemu Windows do wyszukiwania danych. Utwórz aplikację Formularz systemu Windows, źródło danych i formularz. Dodaj parametryzację. Testowanie aplikacji.
ms.custom: SEO-VS-2020
ms.date: 06/07/2021
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 2ce9d3eeebf42855ad69f02b2d72330190a2b390
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111761098"
---
# <a name="create-a-windows-form-to-search-data"></a>Tworzenie formularza Windows Forms na potrzeby wyszukiwania danych

Powszechnym scenariuszem aplikacji jest wyświetlanie wybranych danych w formularzu. Możesz na przykład wyświetlić zamówienia określonego klienta lub szczegóły określonego zamówienia. W tym scenariuszu użytkownik wprowadza informacje w formularzu, a następnie zapytanie jest wykonywane przy użyciu danych wejściowych użytkownika jako parametru; oznacza to, że dane są wybierane na podstawie zapytania sparametryzowanego. Zapytanie zwraca tylko dane spełniające kryteria wprowadzone przez użytkownika. W tym przewodniku pokazano, jak utworzyć zapytanie, które zwraca klientów z określonego miasta, i zmodyfikować interfejs użytkownika, aby użytkownicy mogą wprowadzić nazwę miasta i nacisnąć przycisk w celu wykonania zapytania.

Użycie zapytań sparametryzowanej pomaga zwiększyć wydajność aplikacji, umożliwiając bazie danych pracę, w przypadku których najlepiej — szybkie filtrowanie rekordów. Natomiast jeśli zażądasz całej tabeli bazy danych, przekieruj ją za pośrednictwem sieci, a następnie użyj logiki aplikacji, aby znaleźć rekordy, których potrzebujesz, aplikacja może stać się powolna i nieefektywna.

Zapytania sparametryzowane można dodać do dowolnego narzędzia TableAdapter (i kontrolek w celu akceptowania wartości parametrów i wykonywania zapytania) przy użyciu okna dialogowego **Konstruktor kryteriów** wyszukiwania. Otwórz okno dialogowe, wybierając polecenie **Dodaj zapytanie** w menu **Dane** (lub w dowolnym tagu inteligentnym TableAdapter).

Zadania przedstawione w tym przewodniku obejmują:

- Tworzenie i konfigurowanie źródła danych w aplikacji za pomocą kreatora **Konfiguracja źródła** danych.

- Ustawianie typu upuszczania elementów w **oknie Źródła** danych.

- Tworzenie kontrolek wyświetlających dane przez przeciągnięcie elementów z **okna Źródła** danych do formularza.

- Dodawanie kontrolek w celu wyświetlenia danych w formularzu.

- Ukończenie **okna dialogowego Konstruktor kryteriów** wyszukiwania.

- Wprowadzanie parametrów w formularzu i wykonywanie zapytania sparametryzowanego.

> [!NOTE]
> Procedury w tym artykule mają zastosowanie tylko do .NET Framework Windows Forms, a nie do projektów Windows Forms .NET Core.

## <a name="prerequisites"></a>Wymagania wstępne

Musisz mieć zainstalowane **obciążenie Magazyn danych i** przetwarzanie. Zobacz [Modyfikowanie Visual Studio](../install/modify-visual-studio.md).

W tym przewodniku użyto SQL Server Express LocalDB i przykładowej bazy danych Northwind.

1. Jeśli nie masz jeszcze bazy SQL Server Express LocalDB, zainstaluj [](https://www.microsoft.com/sql-server/sql-server-editions-express)ją ze strony pobierania SQL Server Express lub za pomocą Instalator programu Visual Studio **.** W **Instalator programu Visual Studio** można zainstalować program SQL Server Express LocalDB jako część obciążenia  Magazynowanie i przetwarzanie danych lub jako pojedynczy składnik.

2. Zainstaluj przykładową bazę danych Northwind, wykonać następujące kroki:

    1. W Visual Studio otwórz okno **Eksplorator obiektów SQL Server** aplikacji. (Eksplorator obiektów SQL Server jest instalowany jako część obciążenia Magazyn danych i przetwarzanie **w** **Instalator programu Visual Studio.** Rozwiń **węzeł SQL Server** węzeł. Kliknij prawym przyciskiem myszy wystąpienie bazy danych LocalDB i wybierz **pozycję Nowe zapytanie.**

       Zostanie otwarte okno edytora zapytań.

    2. Skopiuj skrypt [Northwind Transact-SQL](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do schowka. Ten skrypt języka T-SQL tworzy bazę danych Northwind od podstaw i wypełnia ją danymi.

    3. Wklej skrypt T-SQL do edytora zapytań, a następnie wybierz **przycisk Wykonaj.**

       Po krótkiej chwili zapytanie zakończy działanie i zostanie utworzona baza danych Northwind.

## <a name="create-the-windows-forms-application"></a>Tworzenie Windows Forms aplikacji

:::moniker range="vs-2017"

Utwórz nowy **projekt Windows Forms App (.NET Framework)** dla języka C# lub Visual Basic. Nadaj **projektowi nazwę WindowsSearchForm**.

## <a name="create-the-data-source"></a>Tworzenie źródła danych

Ten krok powoduje utworzenie źródła danych z bazy danych przy użyciu kreatora **Konfiguracja źródła** danych:

1. Aby otworzyć **okno Źródła danych,** w menu **Dane** kliknij polecenie Pokaż **źródła danych.**

2. W **oknie Źródła** danych wybierz pozycję **Dodaj nowe źródło danych,** aby uruchomić **Kreatora konfiguracji źródła** danych.

3. Wybierz **pozycję Baza** danych na stronie Wybierz typ źródła danych, **a** następnie kliknij przycisk **Dalej.**

4. Na stronie **Wybieranie połączenia danych** wykonaj jedną z następujących czynności:

    - Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

    - Wybierz **pozycję Nowe połączenie,** aby uruchomić **okno dialogowe Dodawanie/modyfikowanie** połączenia.

5. Jeśli baza danych wymaga hasła, wybierz opcję dołączania poufnych danych, a następnie kliknij przycisk **Dalej.**

6. Na stronie **Zapisywanie parametrów połączenia w pliku konfiguracji aplikacji** kliknij przycisk **Dalej.**

7. Na stronie **Wybieranie obiektów bazy danych** rozwiń węzeł **Tabele.**

8. Wybierz **tabelę Customers** (Klienci), a następnie kliknij przycisk **Finish (Zakończ).**

     Zestaw **NorthwindDataSet** zostanie dodany do projektu, a tabela **Customers zostanie** wyświetlona w **oknie Źródła** danych.

:::moniker-end

:::moniker range=">=vs-2019"

Utwórz nowy **projekt Windows Forms App (.NET Framework)** dla języka C# lub Visual Basic. Nadaj **projektowi nazwę WindowsSearchForm**.

## <a name="create-the-data-source"></a>Tworzenie źródła danych

Ten krok powoduje utworzenie źródła danych z bazy danych przy użyciu kreatora **Konfiguracja źródła** danych:

1. Aby otworzyć okno **Źródła danych,** użyj szybkiego wyszukiwania **(Ctrl** + **Q)** i wyszukaj źródło **danych**.

1. W **oknie Źródła** danych wybierz pozycję **Dodaj nowe źródło danych,** aby uruchomić **Kreatora konfiguracji źródła** danych.

1. Wybierz **pozycję Baza** danych na stronie Wybierz typ źródła danych, **a** następnie kliknij przycisk **Dalej.**

1. Na **ekranie Choose a Database Model (Wybieranie modelu bazy** danych) wybierz pozycję **Dataset (Zestaw danych),** a następnie kliknij przycisk **Next (Dalej).**

1. Na stronie **Wybieranie połączenia danych** wykonaj jedną z następujących czynności:

    - Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

    - Wybierz **pozycję Nowe połączenie,** aby uruchomić **okno dialogowe Dodawanie/modyfikowanie** połączenia.

1. Na stronie **Zapisywanie parametrów połączenia w pliku konfiguracji aplikacji** kliknij przycisk **Dalej.**

1. Na stronie **Wybieranie obiektów bazy danych** rozwiń węzeł **Tabele.**

1. Wybierz **tabelę Customers** (Klienci), a następnie kliknij przycisk **Finish (Zakończ).**

     Zestaw **NorthwindDataSet** zostanie dodany do projektu, a tabela **Customers zostanie** wyświetlona w **oknie Źródła** danych.

:::moniker-end

## <a name="create-the-form"></a>Tworzenie formularza

Kontrolki powiązane z danymi można tworzyć, przeciągając elementy z okna **Źródła** danych do formularza:

1. Upewnij się, Windows Forms projektanta danych ma aktywny fokus, a okno **Źródła** danych jest otwarte i przypięte.

1. Rozwiń **węzeł Klienci** w **oknie Źródła** danych.

1. Przeciągnij węzeł **Klienci** z **okna Źródła danych** do formularza.

     Na formularzu jest wyświetlany pasek narzędzi () do <xref:System.Windows.Forms.DataGridView> nawigowania po <xref:System.Windows.Forms.BindingNavigator> rekordach. Zestaw [Danych NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> , i jest wyświetlany na pasku <xref:System.Windows.Forms.BindingNavigator> składników.

## <a name="add-parameterization-search-functionality-to-the-query"></a>Dodawanie parametryzacji (funkcji wyszukiwania) do zapytania

Klauzulę WHERE można dodać do oryginalnego zapytania przy użyciu okna dialogowego **Konstruktor** kryteriów wyszukiwania:

1. Tuż pod powierzchnią projektową formularza wybierz przycisk **customersTableAdapter,** a następnie w oknie **Właściwości** wybierz pozycję **Dodaj zapytanie...**.

2. Wpisz **FillByCity** w **obszarze Nazwa nowego** zapytania w **oknie dialogowym Konstruktor kryteriów** wyszukiwania.

3. Dodaj `WHERE City = @City` do zapytania w obszarze **Tekst** zapytania.

     Zapytanie powinno być podobne do następującego:

     ```sql
     SELECT CustomerID, CompanyName, ContactName, ContactTitle,
          Address, City, Region, PostalCode, Country, Phone, Fax
     FROM Customers
     WHERE City = @City
     ```

    > [!NOTE]
    > Dostęp i OLE DB źródła danych używają znaku zapytania ("?"") do oznaczania parametrów, więc klauzula WHERE będzie wyglądać tak: `WHERE City = ?` .

4. Kliknij **przycisk OK,** aby zamknąć **okno dialogowe Konstruktor** kryteriów wyszukiwania.

     Do formularza zostanie dodany formularz **FillByCityToolStrip.**

## <a name="test-the-application"></a>Testowanie aplikacji

Uruchomienie aplikacji otwiera formularz i przygotowuje go do użycia parametru jako danych wejściowych:

1. Naciśnij **klawisz F5,** aby uruchomić aplikację.

2. W **polu tekstowym** **City (Miasto)** wpisz London (Londyn), a następnie kliknij pozycję **FillByCity (FillByCity).**

     Siatka danych jest wypełniana klientami spełniającymi kryteria. W tym przykładzie siatka danych wyświetla tylko klientów, którzy w kolumnie **City** mają wartość **Londyn.**

## <a name="next-steps"></a>Następne kroki

W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po utworzeniu formularza sparametryzowanego. Niektóre udoskonalenia, których można dokonać w tym instruktażu obejmują:

- Dodawanie kontrolek, które wyświetlają powiązane dane. Aby uzyskać więcej informacji, zobacz [Relacje w zestawach danych.](relationships-in-datasets.md)

- Edytowanie zestawu danych w celu dodania lub usunięcia obiektów bazy danych. Aby uzyskać więcej informacji, zobacz [Tworzenie i konfigurowanie zestawów danych.](../data-tools/create-and-configure-datasets-in-visual-studio.md)

## <a name="see-also"></a>Zobacz też

- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
