---
title: Zapisywanie danych za pomocą metod DBDirect adaptera TableAdapter
description: W tym instruktażu należy uruchomić instrukcje SQL bezpośrednio dla bazy danych przy użyciu metod DBDirect klasy TableAdapter.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 4539d269f27cd09f96c8633d0efd603708f1f2e1
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215776"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Zapisywanie danych za pomocą metod DBDirect adaptera TableAdapter

Ten Instruktaż zawiera szczegółowe instrukcje dotyczące uruchamiania instrukcji SQL bezpośrednio w bazie danych przy użyciu metod DBDirect klasy TableAdapter. Metody DBDirect TableAdapter zapewniają poziom kontroli nad aktualizacjami bazy danych. Można ich używać do uruchamiania określonych instrukcji SQL i procedur składowanych przez wywoływanie pojedynczych `Insert` `Update` metod, i, w `Delete` zależności od potrzeb aplikacji (w przeciwieństwie do przeciążonej `Update` metody, która wykonuje instrukcje Update, INSERT i DELETE w jednym wywołaniu).

W tym instruktażu dowiesz się, jak:

- Utwórz nową **aplikację Windows Forms**.

- Utwórz i skonfiguruj zestaw danych za pomocą [Kreatora konfiguracji źródła danych](../data-tools/media/data-source-configuration-wizard.png).

- Wybierz kontrolkę, która ma zostać utworzona w formularzu podczas przeciągania elementów z okna **źródła danych** . Aby uzyskać więcej informacji, zobacz [Ustawianie kontrolki do utworzenia podczas przeciągania z okna źródła danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Utwórz formularz powiązany z danymi, przeciągając elementy z okna **źródła danych** na formularz.

- Dodawanie metod w celu bezpośredniego dostępu do bazy danych i wykonywania operacji wstawiania, aktualizacji i usuwania.

## <a name="prerequisites"></a>Wymagania wstępne

W tym instruktażu jest stosowana SQL Server Express LocalDB i Przykładowa baza danych Northwind.

1. Jeśli nie masz SQL Server Express LocalDB, zainstaluj go na [stronie pobierania SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)lub za pośrednictwem **Instalator programu Visual Studio**. W **Instalator programu Visual Studio** można zainstalować SQL Server Express LocalDB jako część obciążenia **magazynu danych i przetwarzania** lub jako pojedynczy składnik.

2. Zainstaluj przykładową bazę danych Northwind, wykonując następujące kroki:

    1. W programie Visual Studio Otwórz okno **Eksplorator obiektów SQL Server** . (Eksplorator obiektów SQL Server jest instalowany jako część obciążenia **magazynu i przetwarzania danych** w Instalator programu Visual Studio). Rozwiń węzeł **SQL Server** . Kliknij prawym przyciskiem myszy wystąpienie LocalDB i wybierz pozycję **nowe zapytanie**.

       Zostanie otwarte okno edytora zapytań.

    2. Skopiuj [skrypt języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt T-SQL tworzy bazę danych Northwind od podstaw i wypełnia ją danymi.

    3. Wklej skrypt T-SQL do edytora zapytań, a następnie wybierz przycisk Execute ( **Wykonaj** ).

       Po krótkim czasie zapytanie kończy działanie i zostanie utworzona baza danych Northwind.

## <a name="create-a-windows-forms-application"></a>Tworzenie aplikacji Windows Forms

Pierwszym krokiem jest utworzenie **aplikacji Windows Forms**.

1. W programie Visual Studio w menu **plik** wybierz pozycję **Nowy**  >  **projekt**.

2. Rozwiń pozycję **Visual C#** lub **Visual Basic** w okienku po lewej stronie, a następnie wybierz pozycję **Windows Desktop**.

3. W środkowym okienku wybierz typ projektu **aplikacji Windows Forms** .

4. Nazwij projekt **TableAdapterDbDirectMethodsWalkthrough**, a następnie wybierz przycisk **OK**.

     Projekt **TableAdapterDbDirectMethodsWalkthrough** został utworzony i dodany do **Eksplorator rozwiązań**.

## <a name="create-a-data-source-from-your-database"></a>Tworzenie źródła danych na podstawie bazy danych

Ten krok powoduje użycie **Kreatora konfiguracji źródła danych** w celu utworzenia źródła danych na podstawie `Region` tabeli w przykładowej bazie danych Northwind. Aby utworzyć połączenie, musisz mieć dostęp do przykładowej bazy danych Northwind. Aby uzyskać informacje o konfigurowaniu przykładowej bazy danych Northwind, zobacz [How to: Install Sample Bases](../data-tools/installing-database-systems-tools-and-samples.md).

### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych

1. W menu **dane** wybierz pozycję **Pokaż źródła danych**.

   Zostanie otwarte okno **źródła danych** .

2. W oknie **źródła danych** wybierz pozycję **Dodaj nowe źródło danych** , aby uruchomić **Kreatora konfiguracji źródła danych**.

3. Na ekranie **Wybierz typ źródła danych** wybierz pozycję **baza danych**, a następnie wybierz przycisk **dalej**.

4. Na ekranie **Wybierz połączenie danych** wykonaj jedną z następujących czynności:

    - Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

         -lub-

    - Wybierz pozycję **nowe połączenie** , aby uruchomić okno dialogowe **Dodawanie/modyfikowanie połączenia** .

5. Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie wybierz przycisk **dalej**.

6. Na ekranie **Zapisz parametry połączenia do pliku konfiguracji aplikacji** wybierz pozycję **dalej**.

7. Na ekranie **Wybierz obiekty bazy danych** rozwiń węzeł **tabele** .

8. Wybierz `Region` tabelę, a następnie wybierz pozycję **Zakończ**.

     **NorthwindDataSet** jest dodawany do projektu, a `Region` tabela pojawia się w oknie **źródła danych** .

## <a name="add-controls-to-the-form-to-display-the-data"></a>Dodawanie kontrolek do formularza w celu wyświetlenia danych

Utwórz formanty powiązane z danymi, przeciągając elementy z okna **źródła danych** na formularz.

Aby utworzyć formanty powiązane z danymi w formularzu systemu Windows, przeciągnij węzeł **region** główny z okna **źródła danych** na formularz.

<xref:System.Windows.Forms.DataGridView>Kontrolka i pasek narzędzi ( <xref:System.Windows.Forms.BindingNavigator> ) na potrzeby nawigowania po rekordach pojawiają się w formularzu. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `RegionTableAdapter` , <xref:System.Windows.Forms.BindingSource> i <xref:System.Windows.Forms.BindingNavigator> pojawia się na pasku składnika.

### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Aby dodać przyciski, które będą wywoływały poszczególne metody TableAdapter DBDirect

1. Przeciągnij trzy <xref:System.Windows.Forms.Button> kontrolki z **przybornika** na **formularz Form1** (poniżej **RegionDataGridView**).

2. Dla każdego przycisku Ustaw następujące właściwości **nazwy** i **tekstu** .

    |Nazwa|Tekst|
    |----------|----------|
    |`InsertButton`|**Insert**|
    |`UpdateButton`|**Aktualizowanie**|
    |`DeleteButton`|**Usuwanie**|

### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Aby dodać kod umożliwiający wstawianie nowych rekordów do bazy danych

1. Wybierz pozycję **InsertButton** , aby utworzyć procedurę obsługi zdarzeń dla zdarzenia kliknięcia i otworzyć formularz w edytorze kodu.

2. Zastąp `InsertButton_Click` procedurę obsługi zdarzeń następującym kodem:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb" id="Snippet1":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs" id="Snippet1":::

### <a name="to-add-code-to-update-records-in-the-database"></a>Aby dodać kod w celu zaktualizowania rekordów w bazie danych

1. Kliknij dwukrotnie **UpdateButton** , aby utworzyć procedurę obsługi zdarzeń dla zdarzenia kliknięcia i otworzyć formularz w edytorze kodu.

2. Zastąp `UpdateButton_Click` procedurę obsługi zdarzeń następującym kodem:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb" id="Snippet2":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs" id="Snippet2":::

### <a name="to-add-code-to-delete-records-from-the-database"></a>Aby dodać kod do usuwania rekordów z bazy danych

1. Wybierz pozycję **DeleteButton** , aby utworzyć procedurę obsługi zdarzeń dla zdarzenia kliknięcia i otworzyć formularz w edytorze kodu.

2. Zastąp `DeleteButton_Click` procedurę obsługi zdarzeń następującym kodem:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb" id="Snippet3":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs" id="Snippet3":::

## <a name="run-the-application"></a>Uruchamianie aplikacji

- Wybierz klawisz **F5** , aby uruchomić aplikację.

- Wybierz przycisk **Wstaw** i sprawdź, czy nowy rekord pojawia się w siatce.

- Wybierz przycisk **Aktualizuj** i sprawdź, czy rekord został zaktualizowany w siatce.

- Wybierz przycisk **Usuń** i sprawdź, czy rekord został usunięty z siatki.

## <a name="next-steps"></a>Następne kroki

W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po utworzeniu formularza powiązanego z danymi. Niektóre udoskonalenia, których można dokonać w tym instruktażu obejmują:

- Dodawanie funkcji wyszukiwania do formularza.

- Dodając dodatkowe tabele do zestawu danych, wybierając pozycję **Konfiguruj zestaw danych z kreatorem** w oknie **źródła danych** . Można dodać kontrolki, które wyświetlają powiązane dane, przeciągając powiązane węzły do formularza. Aby uzyskać więcej informacji, zobacz [relacje w zestawach danych](relationships-in-datasets.md).

## <a name="see-also"></a>Zobacz też

- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
