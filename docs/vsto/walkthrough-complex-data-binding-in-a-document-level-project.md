---
title: 'Przewodnik: złożone powiązanie danych w projekcie na poziomie dokumentu'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
- multiple column data binding [Office development in Visual Studio]
- data binding [Office development in Visual Studio], multiple columns
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 026dc77573bbedce7882f9b3cceab049ef1066e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "67692342"
---
# <a name="walkthrough-complex-data-binding-in-a-document-level-project"></a>Przewodnik: złożone powiązanie danych w projekcie na poziomie dokumentu
  W tym instruktażu przedstawiono podstawowe powiązanie złożonych danych w projekcie na poziomie dokumentu. W Microsoft Office arkuszu programu Excel można powiązać wiele komórek z polami w bazie danych Northwind SQL Server.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Dodawanie źródła danych do projektu skoroszytu.

- Dodawanie formantów powiązanych z danymi do arkusza.

- Zapisywanie zmian danych z powrotem w bazie danych.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Dostęp do serwera za pomocą przykładowej bazy danych Northwind SQL Server.

- Uprawnienia do odczytu i zapisu w bazie danych SQL Server.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu
 Pierwszym krokiem jest utworzenie projektu skoroszytu programu Excel.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt skoroszytu programu Excel o nazwie **Moje złożone powiązanie danych**. W kreatorze wybierz pozycję **Utwórz nowy dokument**.

     Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Program Visual Studio otwiera nowy skoroszyt programu Excel w Projektancie i dodaje projekt **Moje złożone powiązanie danych** do **Eksplorator rozwiązań**.

## <a name="create-the-data-source"></a>Tworzenie źródła danych
 Użyj okna **źródła danych** , aby dodać do projektu typ zestawu danych.

### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych

1. Jeśli okno **źródła danych** nie jest widoczne, Wyświetl je na pasku menu, wybierając opcję **Wyświetl**  >  **inne**  >  **źródła danych**systemu Windows.

2. Wybierz pozycję **Dodaj nowe źródło danych** , aby uruchomić **Kreatora konfiguracji źródła danych**.

3. Wybierz pozycję **baza danych** , a następnie kliknij przycisk **dalej**.

4. Wybierz połączenie danych z przykładową bazą danych Northwind SQL Server lub Dodaj nowe połączenie za pomocą przycisku **nowe połączenie** .

5. Po wybraniu lub utworzeniu połączenia kliknij przycisk **dalej**.

6. Usuń zaznaczenie opcji Zapisz połączenie, jeśli jest zaznaczone, a następnie kliknij przycisk **dalej**.

7. Rozwiń węzeł **tabele** w oknie **obiekty bazy danych** .

8. Zaznacz pole wyboru obok tabeli **Employees** .

9. Kliknij przycisk **Zakończ**.

   Kreator dodaje tabelę **Employees** do okna **źródła danych** . Dodaje również typ DataSet do projektu, który jest widoczny w **Eksplorator rozwiązań**.

## <a name="add-controls-to-the-worksheet"></a>Dodawanie formantów do arkusza
 Arkusz będzie wyświetlał tabelę **Employees (pracownicy** ), gdy skoroszyt zostanie otwarty. Użytkownicy będą mogli wprowadzać zmiany w danych, a następnie zapisywać te zmiany z powrotem w bazie danych, klikając przycisk.

 Aby automatycznie powiązać arkusz z tabelą, można dodać <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolkę do arkusza z okna **źródła danych** . Aby dać użytkownikowi możliwość zapisywania zmian, Dodaj <xref:System.Windows.Forms.Button> kontrolkę z **przybornika**.

#### <a name="to-add-a-list-object"></a>Aby dodać obiekt listy

1. Upewnij się, że skoroszyt **moje dane złożone Binding.xlsx** jest otwarty w projektancie programu Visual Studio z wyświetlonym arkuszem **Arkusz1** .

2. Otwórz okno **źródła danych** i wybierz węzeł **pracownicy** .

3. Kliknij strzałkę listy rozwijanej, która zostanie wyświetlona.

4. Na liście rozwijanej wybierz pozycję **Lista** .

5. Przeciągnij tabelę **Employees** do komórki **a6**.

     <xref:Microsoft.Office.Tools.Excel.ListObject> `EmployeesListObject` W komórce **a6**zostanie utworzony formant o nazwie. W tym samym czasie <xref:System.Windows.Forms.BindingSource> nazwa `EmployeesBindingSource` , karta tabeli i <xref:System.Data.DataSet> wystąpienie są dodawane do projektu. Formant jest powiązany z <xref:System.Windows.Forms.BindingSource> , który z kolei jest powiązany z <xref:System.Data.DataSet> wystąpieniem.

### <a name="to-add-a-button"></a>Aby dodać przycisk

1. Na karcie **Formanty standardowe** **przybornika**Dodaj <xref:System.Windows.Forms.Button> kontrolkę do komórki **a4** arkusza.

   Następnym krokiem jest dodanie tekstu do przycisku po otwarciu arkusza.

## <a name="initialize-the-control"></a>Inicjowanie kontrolki
 Dodaj tekst do przycisku w <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> obsłudze zdarzeń.

### <a name="to-initialize-the-control"></a>Aby zainicjować formant

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **Arkusz1. vb** lub **Sheet1.cs**, a następnie kliknij polecenie **Wyświetl kod** w menu skrótów.

2. Dodaj następujący kod do metody, `Sheet1_Startup` Aby ustawić tekst dla b `utton` .

    [!code-csharp[Trin_VstcoreDataExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#8)]
    [!code-vb[Trin_VstcoreDataExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#8)]

3. Tylko w przypadku języka C# Dodaj do metody obsługę zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia `Sheet1_Startup` .

    [!code-csharp[Trin_VstcoreDataExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#9)]

   Teraz Dodaj kod, aby obsłużyć <xref:System.Windows.Forms.Control.Click> zdarzenie przycisku.

## <a name="save-changes-to-the-database"></a>Zapisz zmiany w bazie danych
 Wszystkie zmiany wprowadzone w danych istnieją tylko w lokalnym zestawie danych, dopóki nie zostaną jawnie zapisane z powrotem w bazie danych.

### <a name="to-save-changes-to-the-database"></a>Aby zapisać zmiany w bazie danych

1. Dodaj procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia `button` i Dodaj następujący kod, aby zatwierdzić wszystkie zmiany wprowadzone w zestawie danych z powrotem do bazy danych.

     [!code-csharp[Trin_VstcoreDataExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#10)]

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz można testować skoroszyt, aby sprawdzić, czy dane są wyświetlane zgodnie z oczekiwaniami, oraz czy można manipulować danymi w obiekcie list.

### <a name="to-test-the-data-binding"></a>Aby przetestować powiązanie danych

- Naciśnij klawisz **F5**.

     Upewnij się, że gdy skoroszyt zostanie otwarty, obiekt listy jest wypełniany danymi z tabeli **Employees** .

### <a name="to-modify-data"></a>Aby zmodyfikować dane

1. Kliknij komórkę **B7**, która powinna zawierać nazwę **Davolio**.

2. Wpisz nazwę **Anderson**, a następnie naciśnij klawisz **Enter**.

### <a name="to-modify-a-column-header"></a>Aby zmodyfikować nagłówek kolumny

1. Kliknij komórkę zawierającą nagłówek kolumny **LastName**.

2. Wpisz **nazwisko**, włącznie ze spacją między dwoma wyrazami, a następnie naciśnij klawisz **Enter**.

### <a name="to-save-data"></a>Aby zapisać dane

1. Kliknij przycisk **Zapisz** w arkuszu.

2. Zamknij program Excel. Kliknij przycisk **nie** po wyświetleniu monitu o zapisanie wprowadzonych zmian.

3. Naciśnij klawisz **F5** , aby ponownie uruchomić projekt.

     Obiekt list jest wypełniany danymi z tabeli **Employees** .

4. Zwróć uwagę, że nazwa w komórce **B7** jest wciąż **Anderson**, czyli zmianami danych, które zostały wprowadzone i zapisane z powrotem w bazie danych. Nagłówek kolumny **LastName** został zmieniony z powrotem na oryginalny formularz bez spacji, ponieważ nagłówek kolumny nie jest powiązany z bazą danych i nie zapisano zmian wprowadzonych w arkuszu.

### <a name="to-add-new-rows"></a>Aby dodać nowe wiersze

1. Zaznacz komórkę wewnątrz obiektu listy.

    Nowy wiersz pojawia się u dołu listy, a gwiazdka ( **\*** ) w pierwszej komórce nowego wiersza.

2. Dodaj następujące informacje w pustym wierszu.

   |EmployeeID (Identyfikator pracownika)|LastName (Nazwisko)|FirstName (Imię)|Tytuł|
   |----------------|--------------|---------------|-----------|
   |10|Pawłowski|Marek|Kierownik ds. sprzedaży|

### <a name="to-delete-rows"></a>Aby usunąć wiersze

- Kliknij prawym przyciskiem myszy liczbę 16 (wiersz 16) z lewej strony arkusza, a następnie kliknij pozycję **Usuń**.

### <a name="to-sort-the-rows-in-the-list"></a>Aby posortować wiersze na liście

1. Zaznacz komórkę wewnątrz listy.

     Przyciski strzałek pojawiają się w każdym nagłówku kolumny.

2. Kliknij przycisk strzałki w nagłówku kolumny **last name** .

3. Kliknij pozycję **Sortuj rosnąco**.

     Wiersze są sortowane alfabetycznie według nazwisk.

### <a name="to-filter-information"></a>Aby filtrować informacje

1. Zaznacz komórkę wewnątrz listy.

2. Kliknij przycisk strzałki w nagłówku kolumny **title** .

3. Kliknij pozycję **przedstawiciel handlowy**.

     Na liście są wyświetlane tylko te wiersze, które mają **przedstawiciela sprzedaży** w kolumnie **title** .

4. Kliknij przycisk strzałki w nagłówku kolumny **tytuł** .

5. Kliknij **(wszystkie)**.

     Filtrowanie zostanie usunięte i zostaną wyświetlone wszystkie wiersze.

## <a name="next-steps"></a>Następne kroki
 W tym instruktażu przedstawiono podstawowe informacje dotyczące wiązania tabeli w bazie danych z obiektem listy. Poniżej przedstawiono kilka zadań, które mogą wystąpić poniżej:

- Buforuj dane, aby można było ich używać w trybie offline. Aby uzyskać więcej informacji, zobacz [jak: dane pamięci podręcznej do użycia w trybie offline lub na serwerze](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Wdróż rozwiązanie. Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązania biurowego](../vsto/deploying-an-office-solution.md).

- Utwórz relację wzorzec/szczegóły między polem a tabelą. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie relacji głównej szczegółów przy użyciu buforowanego zestawu danych](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md).

## <a name="see-also"></a>Zobacz też
- [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)
- [Przewodnik: proste powiązanie danych w projekcie na poziomie dokumentu](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
