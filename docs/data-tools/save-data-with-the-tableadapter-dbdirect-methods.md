---
title: Zapisywanie danych za pomocą metod DBDirect adaptera TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 88590c49938ef61344a1092dffb42565a81755d1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53920144"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Zapisywanie danych za pomocą metod DBDirect adaptera TableAdapter

Ten przewodnik zawiera szczegółowe instrukcje na temat uruchamiania instrukcji SQL bezpośrednio w odniesieniu do bazy danych przy użyciu dbdirect — metody TableAdapter. Dbdirect — metody TableAdapter zapewniają wystarczające poziom kontroli nad aktualizacje bazy danych. Umożliwia ich uruchamianie określonych instrukcji języka SQL i procedur składowanych, wywołując poszczególnych `Insert`, `Update`, i `Delete` metody, stosownie do potrzeb przez aplikację (w przeciwieństwie przeciążone `Update` metodę, która wykonuje AKTUALIZACJĘ Instrukcjami INSERT i DELETE wszystko w jednym wywołaniu).

Z tego instruktażu dowiesz się jak:

-   Utwórz nową **aplikacja interfejsu Windows Forms**.

-   Tworzenie i konfigurowanie zestawu danych za pomocą [Kreatora konfiguracji źródła danych](../data-tools/media/data-source-configuration-wizard.png).

-   Wybierz kontrolkę do utworzenia w formularzu podczas przeciągania elementów z **źródeł danych** okna. Aby uzyskać więcej informacji, zobacz [Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

-   Tworzenie formularza powiązanych z danymi przez przeciąganie elementów z **źródeł danych** okna na formularzu.

-   Dodaj metody do bezpośredniego dostępu do bazy danych oraz wykonać wstawiania, aktualizacji i usuwania.

## <a name="prerequisites"></a>Wymagania wstępne

Ten przewodnik korzysta z programu SQL Server Express LocalDB i bazie danych Northwind.

1. Jeśli nie masz programu SQL Server Express LocalDB, zainstaluj go z [stronę pobierania programu SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), lub za pomocą **Instalatora programu Visual Studio**. W **Instalatora programu Visual Studio**, można zainstalować programu SQL Server Express LocalDB, jako część **przechowywanie i przetwarzanie danych** obciążenie, lub jako poszczególnych składników.

2. Instalowanie przykładowej bazy danych Northwind, wykonaj następujące czynności:

    1. W programie Visual Studio, otwórz **Eksplorator obiektów SQL Server** okna. (Eksplorator obiektów SQL Server jest instalowany jako część **przechowywanie i przetwarzanie danych** obciążenie w Instalatorze programu Visual Studio.) Rozwiń **programu SQL Server** węzła. Kliknij prawym przyciskiem myszy w ramach wystąpienia LocalDB, a następnie wybierz pozycję **nowe zapytanie**.

       Zostanie otwarte okno edytora zapytań.

    2. Kopiuj [skryptów języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt języka T-SQL tworzy bazę danych Northwind od podstaw i wypełnia ją z danymi.

    3. Wklej skrypt języka T-SQL do edytora zapytań, a następnie wybierz **Execute** przycisku.

       Po pewnym czasie odliczania zapytania i utworzeniu bazy danych Northwind.

## <a name="create-a-windows-forms-application"></a>Tworzenie aplikacji Windows Forms

Pierwszym krokiem jest utworzenie **aplikacja interfejsu Windows Forms**.

1. W programie Visual Studio na **pliku** menu, wybierz opcję **New** > **projektu**.

2. Rozwiń **Visual C#** lub **języka Visual Basic** w okienku po lewej stronie, a następnie zaznacz **pulpitu Windows**.

3. W środkowym okienku wybierz **Windows Forms App** typ projektu.

4. Nadaj projektowi nazwę **TableAdapterDbDirectMethodsWalkthrough**, a następnie wybierz **OK**.

     **TableAdapterDbDirectMethodsWalkthrough** projekt zostanie utworzony i dodany do **Eksploratora rozwiązań**.

## <a name="create-a-data-source-from-your-database"></a>Utwórz źródło danych z bazy danych

Ten krok używa **Kreatora konfiguracji źródła danych** można utworzyć źródła danych, na podstawie `Region` tabeli w bazie danych Northwind. Musi mieć dostęp do przykładowej bazy danych Northwind do utworzenia połączenia. Aby uzyskać informacje dotyczące konfigurowania przykładowej bazy danych Northwind, zobacz [jak: Zainstalować przykładowe bazy danych](../data-tools/installing-database-systems-tools-and-samples.md).

### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych

1. Na **danych** menu, wybierz opcję **Pokaż źródła danych**.

   **Źródeł danych** zostanie otwarte okno.

2. W **źródeł danych** wybierz **Dodaj nowe źródło danych** można uruchomić **Kreatora konfiguracji źródła danych**.

3. Na **wybierz typ źródła danych** ekranu, wybierz opcję **bazy danych**, a następnie wybierz pozycję **dalej**.

4. Na **wybierz połączenie danych** ekranu, wykonaj jedną z następujących czynności:

    -   Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

         —lub—

    -   Wybierz **nowe połączenie** można uruchomić **Dodawanie/modyfikowanie połączenia** okno dialogowe.

5. Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie wybierz **dalej**.

6. Na **Zapisz parametry połączenia do pliku konfiguracji aplikacji** ekranu, wybierz opcję **dalej**.

7. Na **wybierz obiekty bazy danych** ekranu, a następnie rozwiń **tabel** węzła.

8. Wybierz `Region` tabeli, a następnie wybierz **Zakończ**.

     **NorthwindDataSet** zostanie dodany do projektu i `Region` tabela zostanie wyświetlona w **źródeł danych** okna.

## <a name="add-controls-to-the-form-to-display-the-data"></a>Dodawanie formantów do formularza, aby wyświetlić dane

Tworzenie formantów powiązanych z danymi przez przeciąganie elementów z **źródeł danych** okna do formularza.

Aby utworzyć formanty powiązane z danymi w formularzu Windows, przeciągnij główny **Region** węzła z **źródeł danych** okna na formularzu.

A <xref:System.Windows.Forms.DataGridView> kontroli i pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>) do nawigowania między rekordami wyświetlanymi w formularzu. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `RegionTableAdapter`, <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane w zasobniku składnika.

### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Aby dodać przyciski, który będzie wybierany poszczególnych TableAdapter dbdirect — metody

1. Przeciągnij trzy <xref:System.Windows.Forms.Button> kontrolki z **przybornika** na **Form1** (poniżej **RegionDataGridView**).

2. Ustaw następujące **nazwa** i **tekstu** właściwości dla każdego przycisku.

    |Nazwa|Tekst|
    |----------|----------|
    |`InsertButton`|**Wstaw**|
    |`UpdateButton`|**Aktualizacja**|
    |`DeleteButton`|**Delete**|

### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Aby dodać kod, aby wstawianie nowych rekordów do bazy danych

1. Wybierz **InsertButton** utworzyć program obsługi zdarzeń dla zdarzenia kliknięcia i Otwórz formularz w edytorze kodu.

2. Zastąp `InsertButton_Click` programu obsługi zdarzeń z następującym kodem:

     [!code-vb[VbRaddataSaving#1](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_1.vb)]
     [!code-csharp[VbRaddataSaving#1](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_1.cs)]

### <a name="to-add-code-to-update-records-in-the-database"></a>Aby dodać kod do aktualizowania rekordów w bazie danych

1. Kliknij dwukrotnie **UpdateButton** utworzyć program obsługi zdarzeń dla zdarzenia kliknięcia i Otwórz formularz w edytorze kodu.

2. Zastąp `UpdateButton_Click` programu obsługi zdarzeń z następującym kodem:

     [!code-vb[VbRaddataSaving#2](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_2.vb)]
     [!code-csharp[VbRaddataSaving#2](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_2.cs)]

### <a name="to-add-code-to-delete-records-from-the-database"></a>Aby dodać kod do usuwania rekordów z bazy danych

1. Wybierz **DeleteButton** utworzyć program obsługi zdarzeń dla zdarzenia kliknięcia i Otwórz formularz w edytorze kodu.

2. Zastąp `DeleteButton_Click` programu obsługi zdarzeń z następującym kodem:

     [!code-vb[VbRaddataSaving#3](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_3.vb)]
     [!code-csharp[VbRaddataSaving#3](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_3.cs)]

## <a name="run-the-application"></a>Uruchamianie aplikacji

-   Wybierz **F5** do uruchomienia aplikacji.

-   Wybierz **Wstaw** przycisk i sprawdź, czy nowy rekord jest wyświetlany w siatce.

-   Wybierz **aktualizacji** przycisk, a następnie sprawdź, czy rekord zostanie zaktualizowany w siatce.

-   Wybierz **Usuń** przycisk, a następnie sprawdź, czy rekord zostanie usunięty z siatki.

## <a name="next-steps"></a>Następne kroki

W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po utworzeniu formularza powiązanych z danymi. Niektóre udoskonalenia, których można dokonać w tym instruktażu obejmują:

-   Dodawanie funkcji wyszukiwania do formularza.

-   Dodawanie dodatkowych tabel do zestawu danych, wybierając **Konfigurowanie zestawu danych za pomocą kreatora** z poziomu **źródeł danych** okna. Można dodawać formanty, które wyświetlają pokrewne dane, przeciągając pokrewne węzły na formularzu. Aby uzyskać więcej informacji, zobacz [relacje w zestawach danych](relationships-in-datasets.md).

## <a name="see-also"></a>Zobacz także

- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)