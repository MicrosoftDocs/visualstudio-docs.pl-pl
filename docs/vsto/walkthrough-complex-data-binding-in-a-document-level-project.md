---
title: 'Przewodnik: złożone powiązanie danych w projekcie na poziomie dokumentu'
description: Dowiedz się, jak powiązać wiele komórek w arkuszu programu Microsoft Excel z polami w bazie danych Northwind SQL Server danych.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a85f46cf9c234ad662966372a8d014ae0f98be84
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826372"
---
# <a name="walkthrough-complex-data-binding-in-a-document-level-project"></a>Przewodnik: złożone powiązanie danych w projekcie na poziomie dokumentu
  W tym przewodniku pokazano podstawy złożonego powiązania danych w projekcie na poziomie dokumentu. Wiele komórek w arkuszu programu Excel można powiązać Microsoft Office excel z polami w bazie danych Northwind SQL Server danych.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Dodawanie źródła danych do projektu skoroszytu.

- Dodawanie kontrolek powiązanych z danymi do arkusza.

- Zapisywanie zmian danych w bazie danych.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Dostęp do serwera przy użyciu bazy danych Northwind SQL Server przykładowej bazy danych.

- Uprawnienia do odczytu i zapisu w SQL Server danych.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu
 Pierwszym krokiem jest utworzenie projektu skoroszytu programu Excel.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt skoroszytu programu Excel o nazwie **Moje złożone powiązanie danych.** W kreatorze wybierz **pozycję Utwórz nowy dokument.**

     Aby uzyskać więcej informacji, [zobacz How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio nowy skoroszyt programu Excel w projektancie i dodaje projekt **Moje złożone** powiązanie danych do **Eksplorator rozwiązań**.

## <a name="create-the-data-source"></a>Tworzenie źródła danych
 Użyj okna **Źródła danych,** aby dodać typowany zestaw danych do projektu.

### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych

1. Jeśli **okno Źródła danych** nie jest widoczne, wyświetl je na pasku menu, wybierając pozycję **Wyświetl** inne źródła  >  danych systemu **Windows.**  >  

2. Wybierz **pozycję Dodaj nowe źródło danych,** aby uruchomić Kreatora konfiguracji źródła **danych.**

3. Wybierz **pozycję Baza danych,** a następnie kliknij przycisk **Dalej.**

4. Wybierz połączenie danych z przykładową bazą danych Northwind SQL Server lub dodaj nowe połączenie przy użyciu **przycisku Nowe** połączenie.

5. Po wybraniu lub utworzeniu połączenia kliknij przycisk **Dalej.**

6. Wyczyść opcję zapisywania połączenia, jeśli jest zaznaczone, a następnie kliknij przycisk **Dalej.**

7. Rozwiń **węzeł Tabele** w **oknie Obiekty bazy** danych.

8. Zaznacz pole wyboru obok tabeli **Employees.**

9. Kliknij przycisk **Finish** (Zakończ).

   Kreator dodaje **tabelę Employees** do **okna Źródła** danych. Dodaje również typowany zestaw danych do projektu, który jest widoczny w **Eksplorator rozwiązań**.

## <a name="add-controls-to-the-worksheet"></a>Dodawanie kontrolek do arkusza
 Arkusz będzie wyświetlać **tabelę Employees** po otwarciu skoroszytu. Użytkownicy będą mogli wprowadzać zmiany w danych, a następnie zapisywać je z powrotem w bazie danych, klikając przycisk.

 Aby automatycznie powiązać arkusz z tabelą, możesz dodać do arkusza <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolkę z **okna Źródła** danych. Aby dać użytkownikowi możliwość zapisywania zmian, dodaj <xref:System.Windows.Forms.Button> kontrolkę z **przybornika**.

#### <a name="to-add-a-list-object"></a>Aby dodać obiekt listy

1. Sprawdź, czy **skoroszyt Mój Binding.xlsx** danych jest otwarty w projektancie Visual Studio z **wyświetlonym arkuszem Sheet1.**

2. Otwórz okno **Źródła danych** i wybierz węzeł **Pracownicy.**

3. Kliknij strzałkę listy rozwijanej, która zostanie wyświetlona.

4. Wybierz **pozycję ListObject** na liście rozwijanej.

5. Przeciągnij **tabelę Employees** do komórki **A6**.

     Kontrolka <xref:Microsoft.Office.Tools.Excel.ListObject> o `EmployeesListObject` nazwie jest tworzona w **komórce A6**. W tym samym czasie do projektu są dodawane nazwane karty tabeli i <xref:System.Windows.Forms.BindingSource> `EmployeesBindingSource` <xref:System.Data.DataSet> wystąpienie. Kontrolka jest powiązana z <xref:System.Windows.Forms.BindingSource> wystąpieniem <xref:System.Data.DataSet> .

### <a name="to-add-a-button"></a>Aby dodać przycisk

1. Na karcie **Wspólne kontrolki** **przybornika** dodaj kontrolkę <xref:System.Windows.Forms.Button> do komórki **A4** arkusza.

   Następnym krokiem jest dodanie tekstu do przycisku po otworze arkusza.

## <a name="initialize-the-control"></a>Inicjowanie kontrolki
 Dodaj tekst do przycisku w <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> programie obsługi zdarzeń.

### <a name="to-initialize-the-control"></a>Aby zainicjować kontrolkę

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **Sheet1.vb** lub **Sheet1.cs,** a następnie kliknij polecenie **Wyświetl** kod w menu skrótów.

2. Dodaj następujący kod do metody `Sheet1_Startup` , aby ustawić tekst dla b `utton` .

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs" id="Snippet8":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb" id="Snippet8":::

3. Tylko w przypadku języka C# dodaj program obsługi zdarzeń <xref:System.Windows.Forms.Control.Click> dla zdarzenia do metody `Sheet1_Startup` .

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs" id="Snippet9":::

   Teraz dodaj kod <xref:System.Windows.Forms.Control.Click> obsługujący zdarzenie przycisku.

## <a name="save-changes-to-the-database"></a>Zapisywanie zmian w bazie danych
 Wszelkie zmiany wprowadzone w danych istnieją tylko w lokalnym zestawie danych, dopóki nie zostaną jawnie zapisane z powrotem w bazie danych.

### <a name="to-save-changes-to-the-database"></a>Aby zapisać zmiany w bazie danych

1. Dodaj program obsługi zdarzeń dla zdarzenia i dodaj następujący kod, aby zatwierdzić wszystkie zmiany wprowadzone w zestawie danych z <xref:System.Windows.Forms.Control.Click> `button` powrotem do bazy danych.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb" id="Snippet10":::

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz możesz przetestować skoroszyt, aby sprawdzić, czy dane są wyświetlane zgodnie z oczekiwaniami i czy można manipulować danymi w obiekcie listy.

### <a name="to-test-the-data-binding"></a>Aby przetestować powiązanie danych

- Naciśnij klawisz **F5**.

     Sprawdź, czy po otworzonej stronie skoroszytu obiekt listy jest wypełniany danymi z **tabeli Employees.**

### <a name="to-modify-data"></a>Aby zmodyfikować dane

1. Kliknij **komórkę B7,** która powinna zawierać nazwę **Davolio**.

2. Wpisz nazwę **Anderson**, a następnie naciśnij klawisz **Enter**.

### <a name="to-modify-a-column-header"></a>Aby zmodyfikować nagłówek kolumny

1. Kliknij komórkę zawierającą nagłówek **kolumny LastName**.

2. Wpisz **nazwisko**, w tym spację między dwoma wyrazami, a następnie naciśnij **klawisz Enter**.

### <a name="to-save-data"></a>Aby zapisać dane

1. Kliknij **przycisk** Zapisz w arkuszu.

2. Zamknij program Excel. Po **wyświetleniu** monitu kliknij przycisk Nie, aby zapisać wprowadzone zmiany.

3. Naciśnij **klawisz F5,** aby ponownie uruchomić projekt.

     Obiekt listy jest wypełniany danymi z **tabeli Employees.**

4. Zwróć uwagę, że nazwa w komórce **B7** to **nadal Anderson**, czyli zmiana danych, którą wpisano i zapisano z powrotem w bazie danych. Nagłówek **kolumny LastName** został zmieniony z powrotem na oryginalny formularz bez spacji, ponieważ nagłówek kolumny nie jest powiązany z bazą danych i nie zostały zapisanie zmian wprowadzonych w arkuszu.

### <a name="to-add-new-rows"></a>Aby dodać nowe wiersze

1. Zaznacz komórkę wewnątrz obiektu listy.

    W dolnej części listy zostanie wyświetlony nowy wiersz z gwiazdką ( ) w pierwszej **\*** komórce nowego wiersza.

2. Dodaj następujące informacje w pustym wierszu.

   |EmployeeID (Identyfikator pracownika)|LastName (Nazwisko)|FirstName (Imię)|Tytuł|
   |----------------|--------------|---------------|-----------|
   |10|Ito|Shu|Kierownik ds. sprzedaży|

### <a name="to-delete-rows"></a>Aby usunąć wiersze

- Kliknij prawym przyciskiem myszy liczbę 16 (wiersz 16) po lewej stronie arkusza, a następnie kliknij polecenie **Usuń.**

### <a name="to-sort-the-rows-in-the-list"></a>Aby posortować wiersze na liście

1. Wybierz komórkę na liście.

     Przyciski strzałek są wyświetlane w nagłówku każdej kolumny.

2. Kliknij przycisk strzałki w **nagłówku kolumny Nazwisko.**

3. Kliknij **pozycję Sortuj rosnąco.**

     Wiersze są sortowane alfabetycznie według nazwisk.

### <a name="to-filter-information"></a>Aby filtrować informacje

1. Wybierz komórkę na liście.

2. Kliknij przycisk strzałki w **nagłówku kolumny** Tytuł.

3. Kliknij **pozycję Przedstawiciel sprzedaży.**

     Lista zawiera tylko te wiersze, które mają **kolumnę Sales Representative** w **kolumnie** Tytuł.

4. Ponownie kliknij przycisk strzałki w **nagłówku** kolumny Tytuł.

5. Kliknij **pozycję (Wszystkie)**.

     Filtrowanie zostanie usunięte i zostaną wyświetlone wszystkie wiersze.

## <a name="next-steps"></a>Następne kroki
 W tym przewodniku przedstawiono podstawy powiązania tabeli w bazie danych z obiektem listy. Oto kilka zadań, które mogą pojawić się w następnej części:

- Buforuj dane, aby można było ich używać w trybie offline. Aby uzyskać więcej informacji, [zobacz How to: Cache data for use offline or on a server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Wdrażanie rozwiązania. Aby uzyskać więcej informacji, zobacz [Wdrażanie rozwiązania pakietu Office.](../vsto/deploying-an-office-solution.md)

- Utwórz relację wzorzec/szczegół między polem a tabelą. Aby uzyskać więcej informacji, zobacz [Walkthrough: Create a master detail relation using a cached dataset (Przewodnik: tworzenie relacji szczegółów wzorca przy użyciu buforowanych zestawów danych).](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)

## <a name="see-also"></a>Zobacz też
- [Wiązanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)
- [Przewodnik: proste powiązanie danych w projekcie na poziomie dokumentu](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
