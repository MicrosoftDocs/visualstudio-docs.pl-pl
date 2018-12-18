---
title: Tworzenie formularza Windows wyszukiwanie danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e42c86cf94115d317eb20df66f4cef005e05eba9
ms.sourcegitcommit: c9a01c599ce19a5845605b3b28c0229fd0abb93f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2018
ms.locfileid: "52281800"
---
# <a name="create-a-windows-form-to-search-data"></a>Tworzenie formularza Windows Forms na potrzeby wyszukiwania danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Typowy scenariusz aplikacji jest wyświetlany wybranych danych w formularzu. Na przykład można wyświetlić zamówienia dla konkretnego klienta lub szczegóły określonej kolejności. W tym scenariuszu użytkownik wprowadza informacje w formie, a następnie zapytanie jest wykonywane przy użyciu danych wprowadzonych przez użytkownika jako parametr; oznacza to, że dane wybiera się na podstawie sparametryzowanych zapytań. Zapytanie zwraca tylko dane, które nie spełnia kryteriów wprowadzonej przez użytkownika. W tym instruktażu pokazano, jak utworzyć zapytanie, które zwraca klientów w określonym mieście i modyfikowania interfejsu użytkownika, dzięki czemu użytkownicy mogą wprowadzić nazwę miejscowości i naciśnij przycisk, aby wykonać zapytanie.  
  
 Używanie zapytań sparametryzowanych ułatwia aplikacji wydajne pozwalając bazy danych, wykonują pracę, najlepiej na — szybkie filtrowanie rekordów. Z kolei żądania do tabeli całej bazy danych, jej transfer za pośrednictwem sieci i następnie użyj logiki aplikacji, aby znaleźć rekordy, które chcesz, aby aplikacja może być powolne i nieefektywna.  
  
 Można dodać sparametryzowanych zapytań do TableAdapter (i formantów aby zaakceptować wartości parametrów i wykonaj zapytanie), za pomocą **Konstruktor kryteriów wyszukiwania** okno dialogowe. Otwórz okno dialogowe, wybierając **Dodaj zapytanie** polecenie **danych** menu (lub na dowolny tag inteligentny TableAdapter).  
  
 Zadania zilustrowane w tym przewodniku obejmują:  
  
-   Tworzenie nowego projektu aplikacja interfejsu Windows Forms.  
  
-   Tworzenie i konfigurowanie źródła danych w aplikacji za pomocą **konfiguracji źródła danych** kreatora.  
  
-   Ustawienie upuszczany typ elementów w **źródeł danych** okna.  
  
-   Tworzenie formantów, które wyświetlają dane przez przeciąganie elementów z **źródeł danych** okna w formularzu.  
  
-   Dodawanie formantów do wyświetlania danych w formularzu.  
  
-   Kończenie **Konstruktor kryteriów wyszukiwania** okno dialogowe.  
  
-   Wprowadzanie parametrów do formularza i wykonywanie sparametryzowanych zapytań.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W celu przeprowadzenia tego instruktażu, należy:  
  
-   Dostęp do przykładowej bazy danych Northwind.  
  
## <a name="create-the-windows-application"></a>Tworzenie aplikacji Windows  
 Pierwszym krokiem jest utworzenie **aplikacji Windows**. Przypisanie nazwy do projektu jest opcjonalny w tym kroku, ale należy nadać jej tutaj nazwę ponieważ będzie zapisać ją później.  
  
#### <a name="to-create-the-new-windows-application-project"></a>Aby utworzyć nowy projekt aplikacji Windows  
  
1.  Z **pliku** menu, Utwórz nowy projekt.  
  
2.  Nadaj projektowi nazwę `WindowsSearchForm`.  
  
3.  Wybierz **aplikacji Windows** i kliknij przycisk **OK**.  
  
     **WindowsSearchForm** projekt zostanie utworzony i dodany do **Eksploratora rozwiązań**.  
  
## <a name="create-the-data-source"></a>Utwórz źródło danych  
 Spowoduje to utworzenie źródła danych z bazy danych za pomocą **konfiguracji źródła danych** kreatora. Musi mieć dostęp do przykładowej bazy danych Northwind do utworzenia połączenia. Aby uzyskać informacje na temat konfigurowania przykładowej bazy danych Northwind, zobacz [Instalowanie programu SQL Server przykładowych baz danych](../data-tools/install-sql-server-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych  
  
1.  Na **danych** menu, kliknij przycisk **Pokaż źródła danych**.  
  
2.  W **źródeł danych** wybierz **Dodaj nowe źródło danych** można uruchomić **konfiguracji źródła danych** kreatora.  
  
3.  Wybierz **bazy danych** na **wybierz typ źródła danych** strony, a następnie kliknij przycisk **dalej**.  
  
4.  Na **wybierz połączenie danych** wykonaj strony, jedną z następujących czynności:  
  
    -   Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.  
  
    -   Wybierz **nowe połączenie** można uruchomić **Dodawanie/modyfikowanie połączenia** okno dialogowe.  
  
5.  Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie kliknij przycisk **dalej**.  
  
6.  Na **Zapisz parametry połączenia do pliku konfiguracji aplikacji** kliknij **dalej**.  
  
7.  Na **wybierz obiekty bazy danych** rozwiń **tabel** węzła.  
  
8.  Wybierz **klientów** tabeli, a następnie kliknij przycisk **Zakończ**.  
  
     **NorthwindDataSet** zostanie dodany do projektu, a **klientów** tabela zostanie wyświetlona w **źródeł danych** okna.  
  
## <a name="create-the-form"></a>Tworzenie formularza  
 Można utworzyć formanty powiązane z danymi przez przeciąganie elementów z **źródeł danych** okna do formularza.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Aby utworzyć formanty powiązane z danymi formularza  
  
1.  Rozwiń **klientów** w węźle **źródeł danych** okna.  
  
2.  Przeciągnij **klientów** węzła z **źródeł danych** okna do formularza.  
  
     A <xref:System.Windows.Forms.DataGridView> i pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>) do nawigowania między rekordami wyświetlanymi w formularzu. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane w zasobniku składnika.  
  
## <a name="addparameterization-search-functionality-to-the-query"></a>Addparameterization (funkcji wyszukiwania) do zapytania  
 Możesz dodać klauzulę WHERE do oryginalnego zapytania za pomocą **Konstruktor kryteriów wyszukiwania** okno dialogowe.  
  
#### <a name="to-create-a-parameterized-query-and-controls-to-enter-the-parameters"></a>Aby utworzyć zapytanie parametryczne i kontrole w celu wprowadź parametry  
  
1.  Wybierz <xref:System.Windows.Forms.DataGridView> sterowania, a następnie wybierz **Dodaj zapytanie** na **danych** menu.  
  
2.  Typ `FillByCity` w **Nowa nazwa zapytania** obszar na **Konstruktor kryteriów wyszukiwania** okno dialogowe.  
  
3.  Dodaj `WHERE City = @City` do wykonywania zapytań w **tekst zapytania** obszaru.  
  
     Zapytanie powinny wyglądać podobnie do następującego:  
  
     `SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax`  
  
     `FROM Customers`  
  
     `WHERE City = @City`  
  
    > [!NOTE]
    >  Źródła danych programu Access i OLE DB użyć znaku zapytania ("?") do określenia parametrów, dlatego klauzuli WHERE będzie wyglądać następująco: `WHERE City = ?`.  
  
4.  Kliknij przycisk **OK** zamknąć **Konstruktor kryteriów wyszukiwania** okno dialogowe.  
  
     A **FillByCityToolStrip** zostanie dodany do formularza.  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Uruchomiona jest aplikacja zostanie otwarta gotowy do zastąpienia parametr jako dane wejściowe formularza.  
  
#### <a name="to-test-the-application"></a>Aby przetestować aplikację  
  
1.  Naciśnij klawisz F5, aby uruchomić aplikację.  
  
2.  Typ **Londyn** do **Miasto** polu tekstowym, a następnie kliknij przycisk **FillByCity**.  
  
     Siatka danych jest wypełniana przy użyciu klientów, które spełniają kryteria. W tym przykładzie dane tylko są wyświetlane w siatce klientów, którzy mają wartość **Londyn** w ich **Miasto** kolumny.  
  
## <a name="next-steps"></a>Następne kroki  
 W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po utworzeniu formularza sparametryzowanego. Niektóre udoskonalenia, których można dokonać w tym instruktażu obejmują:  
  
-   Dodawanie formantów, które wyświetlają pokrewne dane. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie powiązanych danych w aplikacji Windows Forms](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md).  
  
-   Edytowanie zestawu danych, aby dodać lub usunąć obiekty bazy danych. Aby uzyskać więcej informacji, zobacz [tworzenie i konfigurowanie zestawów danych](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)

