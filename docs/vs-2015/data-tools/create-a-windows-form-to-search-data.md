---
title: Utwórz formularz systemu Windows, aby przeszukać dane | Microsoft Docs
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
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 81980f38cbd8fb595530cc52b2cf32056feb43a7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670061"
---
# <a name="create-a-windows-form-to-search-data"></a>Tworzenie formularza Windows Forms na potrzeby wyszukiwania danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Typowym scenariuszem aplikacji jest wyświetlenie wybranych danych w formularzu. Na przykład może być konieczne wyświetlenie zamówień dla określonego klienta lub szczegółowych informacji o określonej kolejności. W tym scenariuszu użytkownik wprowadza informacje w formularzu, a następnie wykonuje zapytanie z danymi wejściowymi użytkownika jako parametr; oznacza to, że dane są wybierane na podstawie zapytania parametrycznego. Zapytanie zwraca tylko dane, które spełniają kryteria wprowadzone przez użytkownika. W tym instruktażu pokazano, jak utworzyć zapytanie, które zwraca klientów w określonym mieście, i zmodyfikować interfejs użytkownika, tak aby użytkownicy mogli wprowadzić nazwę miasta i nacisnąć przycisk, aby wykonać zapytanie.

 Korzystanie z zapytań parametrycznych ułatwia wydajne działanie aplikacji, dzięki czemu baza danych może być najlepszym rozwiązaniem — szybkie filtrowanie rekordów. Z drugiej strony, Jeśli zażądasz całej tabeli bazy danych, przeniesiesz ją za pośrednictwem sieci, a następnie użyjesz logiki aplikacji w celu znalezienia żądanych rekordów, aplikacja może stać się niska i nieefektywna.

 Zapytania parametryczne można dodawać do dowolnych TableAdapter (i kontrolek do akceptowania wartości parametrów i wykonywania zapytania) przy użyciu okna dialogowego **Konstruktor kryteriów wyszukiwania** . Otwórz okno dialogowe, wybierając polecenie **Dodaj zapytanie** w menu **dane** (lub dowolny tag inteligentny TableAdapter).

 Zadania przedstawione w tym instruktażu obejmują:

- Tworzenie nowego projektu aplikacji Windows Forms.

- Tworzenie i Konfigurowanie źródła danych w aplikacji za pomocą kreatora **konfiguracji źródła danych** .

- Ustawianie typu upuszczania elementów w oknie **źródła danych** .

- Tworzenie kontrolek, które wyświetlają dane poprzez przeciąganie elementów z okna **źródła danych** na formularz.

- Dodawanie kontrolek do wyświetlania danych w formularzu.

- Wypełnienie okna dialogowego **Konstruktor kryteriów wyszukiwania** .

- Wprowadzanie parametrów do formularza i wykonywanie zapytania sparametryzowanego.

## <a name="prerequisites"></a>Wymagania wstępne
 Aby ukończyć ten Instruktaż, potrzebne są:

- Dostęp do przykładowej bazy danych Northwind.

## <a name="create-the-windows-application"></a>Tworzenie aplikacji systemu Windows
 Pierwszym krokiem jest utworzenie **aplikacji systemu Windows**. Przypisanie nazwy do projektu jest opcjonalne w tym kroku, ale podajesz tutaj nazwę, ponieważ zapiszesz ją później.

#### <a name="to-create-the-new-windows-application-project"></a>Aby utworzyć nowy projekt aplikacji systemu Windows

1. Z menu **plik** Utwórz nowy projekt.

2. Nadaj nazwę projektowi `WindowsSearchForm`.

3. Wybierz pozycję **aplikacja systemu Windows** i kliknij przycisk **OK**.

     Projekt **WindowsSearchForm** został utworzony i dodany do **Eksplorator rozwiązań**.

## <a name="create-the-data-source"></a>Tworzenie źródła danych
 Ten krok powoduje utworzenie źródła danych z bazy danych za pomocą kreatora **konfiguracji źródła danych** . Aby utworzyć połączenie, musisz mieć dostęp do przykładowej bazy danych Northwind. Aby uzyskać informacje na temat konfigurowania przykładowej bazy danych Northwind, zobacz [instalowanie SQL Server przykładowych baz danych](../data-tools/install-sql-server-sample-databases.md).

#### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych

1. W menu **dane** kliknij przycisk **Pokaż źródła danych**.

2. W oknie **źródła danych** wybierz pozycję **Dodaj nowe źródło danych** , aby uruchomić kreatora **konfiguracji źródła danych** .

3. Wybierz pozycję **baza danych** na stronie **Wybierz typ źródła danych** , a następnie kliknij przycisk **dalej**.

4. Na stronie **Wybierz połączenie danych** wykonaj jedną z następujących czynności:

    - Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

    - Wybierz pozycję **nowe połączenie** , aby uruchomić okno dialogowe **Dodawanie/modyfikowanie połączenia** .

5. Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie kliknij przycisk **dalej**.

6. Na stronie **Zapisz parametry połączenia do pliku konfiguracji aplikacji** kliknij przycisk **dalej**.

7. Na stronie **Wybierz obiekty bazy danych** rozwiń węzeł **tabele** .

8. Wybierz tabelę **Customers** , a następnie kliknij przycisk **Zakończ**.

     **NorthwindDataSet** jest dodawany do projektu, a tabela **Customers** pojawia się w oknie **źródła danych** .

## <a name="create-the-form"></a>Utwórz formularz
 Można utworzyć formanty powiązane z danymi, przeciągając elementy z okna **źródła danych** na formularz.

#### <a name="to-create-data-bound-controls-on-the-form"></a>Aby utworzyć kontrolki powiązane z danymi w formularzu

1. W oknie **źródła danych** rozwiń węzeł **Customers** .

2. Przeciągnij węzeł **Customers** z okna **źródła danych** do formularza.

     W formularzu pojawiają się <xref:System.Windows.Forms.DataGridView> i pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>) służący do nawigowania po rekordach. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> i <xref:System.Windows.Forms.BindingNavigator> pojawiają się na pasku składnika.

## <a name="addparameterization-search-functionality-to-the-query"></a>Addparameterization (funkcja wyszukiwania) do zapytania
 Można dodać klauzulę WHERE do oryginalnego zapytania przy użyciu okna dialogowego **Konstruktor kryteriów wyszukiwania** .

#### <a name="to-create-a-parameterized-query-and-controls-to-enter-the-parameters"></a>Aby utworzyć zapytanie parametryczne i kontrolki do wprowadzania parametrów

1. Wybierz kontrolkę <xref:System.Windows.Forms.DataGridView>, a następnie wybierz polecenie **Dodaj zapytanie** w menu **dane** .

2. Wpisz `FillByCity` w obszarze **Nowa nazwa zapytania** w oknie dialogowym **Konstruktor kryteriów wyszukiwania** .

3. Dodaj `WHERE City = @City` do zapytania w obszarze **tekstu zapytania** .

     Zapytanie powinno być podobne do następujących:

     `SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax`

     `FROM Customers`

     `WHERE City = @City`

    > [!NOTE]
    > Dostęp i OLE DB źródła danych używają znaku zapytania ("?") do oznaczania parametrów, więc klauzula WHERE będzie wyglądać następująco: `WHERE City = ?`.

4. Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Konstruktor kryteriów wyszukiwania** .

     Do formularza zostanie dodany **FillByCityToolStrip** .

## <a name="testing-the-application"></a>Testowanie aplikacji
 Uruchomienie aplikacji otwiera formularz gotowy do przyłączenia parametru jako dane wejściowe.

#### <a name="to-test-the-application"></a>Aby przetestować aplikację

1. Naciśnij klawisz F5, aby uruchomić aplikację.

2. Wpisz **Londyn** w polu tekstowym **miasto** , a następnie kliknij pozycję **FillByCity**.

     Siatka danych zostanie wypełniona klientom spełniającym kryteria. W tym przykładzie siatka danych wyświetla tylko klientów, którzy mają wartość **Londyn** w ich kolumnie **miasto** .

## <a name="next-steps"></a>Następne kroki
 W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po utworzeniu formularza sparametryzowanego. Niektóre udoskonalenia, których można dokonać w tym instruktażu obejmują:

- Dodawanie kontrolek, które wyświetlają powiązane dane.

- Edytowanie zestawu danych w celu dodania lub usunięcia obiektów bazy danych. Aby uzyskać więcej informacji, zobacz [Tworzenie i konfigurowanie zestawów danych](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Zobacz też
 [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
