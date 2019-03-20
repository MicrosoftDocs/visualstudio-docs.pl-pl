---
title: Tworzenie formularza Windows Forms na potrzeby wyszukiwania danych
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: aa8b91ccdf4aaa5b46f167673007723938fc62ef
ms.sourcegitcommit: 5af29226aef0a3b4a506b69a08a97cfd21049521
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2019
ms.locfileid: "58268782"
---
# <a name="create-a-windows-form-to-search-data"></a>Tworzenie formularza Windows Forms na potrzeby wyszukiwania danych

Typowy scenariusz aplikacji jest wyświetlany wybranych danych w formularzu. Na przykład można wyświetlić zamówienia dla konkretnego klienta lub szczegóły określonej kolejności. W tym scenariuszu użytkownik wprowadza informacje w formie, a następnie zapytanie jest wykonywane przy użyciu danych wprowadzonych przez użytkownika jako parametr; oznacza to, że dane wybiera się na podstawie sparametryzowanych zapytań. Zapytanie zwraca tylko dane, które nie spełnia kryteriów wprowadzonej przez użytkownika. W tym instruktażu pokazano, jak utworzyć zapytanie, które zwraca klientów w określonym mieście i modyfikowania interfejsu użytkownika, dzięki czemu użytkownicy mogą wprowadzić nazwę miejscowości i naciśnij przycisk, aby wykonać zapytanie.

Używanie zapytań sparametryzowanych ułatwia aplikacji wydajne pozwalając bazy danych, wykonują pracę, najlepiej na — szybkie filtrowanie rekordów. Z kolei żądania do tabeli całej bazy danych, jej transfer za pośrednictwem sieci i następnie użyj logiki aplikacji, aby znaleźć rekordy, które chcesz, aby aplikacja może być powolne i nieefektywna.

Można dodać sparametryzowanych zapytań do TableAdapter (i formantów aby zaakceptować wartości parametrów i wykonaj zapytanie), za pomocą **Konstruktor kryteriów wyszukiwania** okno dialogowe. Otwórz okno dialogowe, wybierając **Dodaj zapytanie** polecenie **danych** menu (lub na dowolny tag inteligentny TableAdapter).

Zadania zilustrowane w tym przewodniku obejmują:

- Tworzenie i konfigurowanie źródła danych w aplikacji za pomocą **konfiguracji źródła danych** kreatora.

- Ustawienie upuszczany typ elementów w **źródeł danych** okna.

- Tworzenie formantów, które wyświetlają dane przez przeciąganie elementów z **źródeł danych** okna w formularzu.

- Dodawanie formantów do wyświetlania danych w formularzu.

- Kończenie **Konstruktor kryteriów wyszukiwania** okno dialogowe.

- Wprowadzanie parametrów do formularza i wykonywanie sparametryzowanych zapytań.

## <a name="prerequisites"></a>Wymagania wstępne

Ten przewodnik korzysta z programu SQL Server Express LocalDB i bazie danych Northwind.

1. Jeśli nie masz programu SQL Server Express LocalDB, zainstaluj go z [stronę pobierania programu SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), lub za pomocą **Instalatora programu Visual Studio**. W **Instalatora programu Visual Studio**, można zainstalować programu SQL Server Express LocalDB, jako część **przechowywanie i przetwarzanie danych** obciążenie, lub jako poszczególnych składników.

2. Instalowanie przykładowej bazy danych Northwind, wykonaj następujące czynności:

    1. W programie Visual Studio, otwórz **Eksplorator obiektów SQL Server** okna. (Eksplorator obiektów SQL Server jest instalowany jako część **przechowywanie i przetwarzanie danych** obciążenie w **Instalatora programu Visual Studio**.) Rozwiń **programu SQL Server** węzła. Kliknij prawym przyciskiem myszy w ramach wystąpienia LocalDB, a następnie wybierz pozycję **nowe zapytanie**.

       Zostanie otwarte okno edytora zapytań.

    2. Kopiuj [skryptów języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt języka T-SQL tworzy bazę danych Northwind od podstaw i wypełnia ją z danymi.

    3. Wklej skrypt języka T-SQL do edytora zapytań, a następnie wybierz **Execute** przycisku.

       Po pewnym czasie odliczania zapytania i utworzeniu bazy danych Northwind.

## <a name="create-the-windows-forms-application"></a>Tworzenie aplikacji Windows Forms

Utwórz nową **Windows Forms App** projekt albo C# lub Visual Basic. Nadaj projektowi nazwę **WindowsSearchForm**.

## <a name="create-the-data-source"></a>Utwórz źródło danych

Spowoduje to utworzenie źródła danych z bazy danych za pomocą **konfiguracji źródła danych** kreatora:

1.  Aby otworzyć **źródeł danych** okna na **danych** menu, kliknij przycisk **Pokaż źródła danych**.

2.  W **źródeł danych** wybierz **Dodaj nowe źródło danych** można uruchomić **konfiguracji źródła danych** kreatora.

3.  Wybierz **bazy danych** na **wybierz typ źródła danych** strony, a następnie kliknij przycisk **dalej**.

4.  Na **wybierz połączenie danych** wykonaj strony, jedną z następujących czynności:

    - Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

    - Wybierz **nowe połączenie** można uruchomić **Dodawanie/modyfikowanie połączenia** okno dialogowe.

5.  Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie kliknij przycisk **dalej**.

6.  Na **Zapisz parametry połączenia do pliku konfiguracji aplikacji** kliknij **dalej**.

7.  Na **wybierz obiekty bazy danych** rozwiń **tabel** węzła.

8.  Wybierz **klientów** tabeli, a następnie kliknij przycisk **Zakończ**.

     **NorthwindDataSet** zostanie dodany do projektu, a **klientów** tabela zostanie wyświetlona w **źródeł danych** okna.

## <a name="create-the-form"></a>Tworzenie formularza

Można utworzyć formanty powiązane z danymi przez przeciąganie elementów z **źródeł danych** okna na formularzu:

1.  Rozwiń **klientów** w węźle **źródeł danych** okna.

2.  Przeciągnij **klientów** węzła z **źródeł danych** okna do formularza.

     A <xref:System.Windows.Forms.DataGridView> i pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>) do nawigowania między rekordami wyświetlanymi w formularzu. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane w zasobniku składnika.

## <a name="add-parameterization-search-functionality-to-the-query"></a>Dodaj parametryzacji (funkcji wyszukiwania) do zapytania

Możesz dodać klauzulę WHERE do oryginalnego zapytania za pomocą **Konstruktor kryteriów wyszukiwania** okno dialogowe:

1.  Wybierz <xref:System.Windows.Forms.DataGridView> sterowania, a następnie wybierz **Dodaj zapytanie** na **danych** menu.

2.  Typ **FillByCity** w **Nowa nazwa zapytania** obszar na **Konstruktor kryteriów wyszukiwania** okno dialogowe.

3.  Dodaj `WHERE City = @City` do wykonywania zapytań w **tekst zapytania** obszaru.

     Zapytanie powinny wyglądać podobnie do następującego:

     ```sql
     SELECT CustomerID, CompanyName, ContactName, ContactTitle,
          Address, City, Region, PostalCode, Country, Phone, Fax
     FROM Customers
     WHERE City = @City
     ```

    > [!NOTE]
    > Źródła danych programu Access i OLE DB użyć znaku zapytania ("?") do określenia parametrów, dlatego klauzuli WHERE będzie wyglądać następująco: `WHERE City = ?`.

4.  Kliknij przycisk **OK** zamknąć **Konstruktor kryteriów wyszukiwania** okno dialogowe.

     A **FillByCityToolStrip** zostanie dodany do formularza.

## <a name="test-the-application"></a>Testowanie aplikacji

Uruchamianie aplikacji zostanie otwarty formularz i sprawia, że chcesz przenieść swoją parametr jako dane wejściowe:

1.  Naciśnij klawisz **F5** do uruchomienia aplikacji.

2.  Typ **Londyn** do **Miasto** polu tekstowym, a następnie kliknij przycisk **FillByCity**.

     Siatka danych jest wypełniana przy użyciu klientów, które spełniają kryteria. W tym przykładzie dane tylko są wyświetlane w siatce klientów, którzy mają wartość **Londyn** w ich **Miasto** kolumny.

## <a name="next-steps"></a>Następne kroki

W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po utworzeniu formularza sparametryzowanego. Niektóre udoskonalenia, których można dokonać w tym instruktażu obejmują:

- Dodawanie formantów, które wyświetlają pokrewne dane. Aby uzyskać więcej informacji, zobacz [relacje w zestawach danych](relationships-in-datasets.md).

- Edytowanie zestawu danych, aby dodać lub usunąć obiekty bazy danych. Aby uzyskać więcej informacji, zobacz [tworzenie i konfigurowanie zestawów danych](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Zobacz także

- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
