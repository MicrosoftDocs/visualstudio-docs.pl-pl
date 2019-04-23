---
title: 'Przewodnik: Złożone powiązanie danych w projekcie na poziomie dokumentu'
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
ms.openlocfilehash: aabd45871e55fd22b9b9e35597555fd13b15d6eb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60052535"
---
# <a name="walkthrough-complex-data-binding-in-a-document-level-project"></a>Przewodnik: Złożone powiązanie danych w projekcie na poziomie dokumentu
  W tym instruktażu przedstawiono podstawowe informacje o złożone powiązanie danych w projekcie na poziomie dokumentu. Pola w bazie danych Northwind programu SQL Server można powiązać wiele komórek w arkuszu programu Microsoft Office Excel.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Dodawanie źródła danych do projektu skoroszytu.

- Dodawanie formantów powiązanych z danymi do arkusza.

- Zapisywanie zmian danych w bazie danych.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Dostęp do serwera z przykładową bazą danych Northwind programu SQL Server.

- Uprawnienia do odczytu i zapisu w bazie danych programu SQL Server.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu
 Pierwszym krokiem jest utworzenie projektu skoroszytu programu Excel.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projektu skoroszytu programu Excel o nazwie **Moje złożone powiązanie danych**. W kreatorze Wybierz **Utwórz nowy dokument**.

     Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w programie Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio zostanie otwarty nowy skoroszyt programu Excel w Projektancie i dodaje **Moje złożone powiązanie danych** projekt **Eksploratora rozwiązań**.

## <a name="create-the-data-source"></a>Utwórz źródło danych
 Użyj **źródeł danych** okna, aby dodać typizowany zestaw danych do projektu.

### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych

1. Jeśli **źródeł danych** okno nie jest widoczne, wyświetlić je, na pasku menu, wybierając **widoku** > **Windows inne**  >   **Źródła danych**.

2. Wybierz **Dodaj nowe źródło danych** można uruchomić **Kreatora konfiguracji źródła danych**.

3. Wybierz **bazy danych** a następnie kliknij przycisk **dalej**.

4. Wybierz połączenie danych z bazie danych programu SQL Server Northwind lub Dodaj nowe połączenie przy użyciu **nowe połączenie** przycisku.

5. Po zostało wybrane lub utworzyć połączenie, kliknij przycisk **dalej**.

6. Usuń zaznaczenie opcji, aby zapisać połączenie, jeśli jest ono zaznaczone, a następnie kliknij **dalej**.

7. Rozwiń **tabel** w węźle **obiektów bazy danych** okna.

8. Zaznacz pole wyboru obok pozycji **pracowników** tabeli.

9. Kliknij przycisk **Zakończ**.

   Kreator dodaje **pracowników** do tabeli **źródeł danych** okna. Dodaje także typizowany zestaw danych do projektu, który jest widoczny w **Eksploratora rozwiązań**.

## <a name="add-controls-to-the-worksheet"></a>Dodawanie formantów do arkusza
 Arkusz zostanie wyświetlona **pracowników** tabeli po otwarciu skoroszytu. Użytkownicy będą mogli dokonać zmian danych, a następnie zapisz te zmiany w bazie danych przez kliknięcie przycisku.

 Aby powiązać automatycznie arkusza do tabeli, możesz dodać <xref:Microsoft.Office.Tools.Excel.ListObject> formantu do arkusza z **źródeł danych** okna. Aby przyznać użytkownikowi opcję, aby zapisać zmiany, należy dodać <xref:System.Windows.Forms.Button> z kontrolować **przybornika**.

#### <a name="to-add-a-list-object"></a>Aby dodać obiekt listy

1. Upewnij się, że **Moje Binding.xlsx danych złożonych** skoroszyt jest otwarty w Projektancie Visual Studio za pomocą **Arkusz1** wyświetlane.

2. Otwórz **źródeł danych** okna, a następnie wybierz pozycję **pracowników** węzła.

3. Kliknij strzałkę listy rozwijanej, która pojawia się.

4. Wybierz **ListObject** na liście rozwijanej.

5. Przeciągnij **pracowników** tabeli do komórki **A6**.

     A <xref:Microsoft.Office.Tools.Excel.ListObject> formantu o nazwie `EmployeesListObject` jest tworzony w komórce **A6**. W tym samym czasie <xref:System.Windows.Forms.BindingSource> o nazwie `EmployeesBindingSource`, karty tabeli, a <xref:System.Data.DataSet> wystąpienia są dodawane do projektu. Kontrolka jest powiązana z <xref:System.Windows.Forms.BindingSource>, która z kolei jest powiązana <xref:System.Data.DataSet> wystąpienia.

### <a name="to-add-a-button"></a>Aby dodać przycisk

1. Z **wspólnych formantów** karcie **przybornika**, Dodaj <xref:System.Windows.Forms.Button> kontrolkę komórki **A4** arkusza.

   Następnym krokiem jest do dodawania tekstu przycisku, po otwarciu arkusza.

## <a name="initialize-the-control"></a>Inicjowanie kontrolki
 Dodawanie tekstu do przycisku w <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> programu obsługi zdarzeń.

### <a name="to-initialize-the-control"></a>Aby zainicjować formant

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Sheet1.vb** lub **Sheet1.cs**, a następnie kliknij przycisk **Wyświetl kod** w menu skrótów.

2. Dodaj następujący kod do `Sheet1_Startup` metodę, aby ustawić tekst za b`utton`.

    [!code-csharp[Trin_VstcoreDataExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#8)]
    [!code-vb[Trin_VstcoreDataExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#8)]

3. W przypadku tylko język C#, należy dodać program obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia `Sheet1_Startup` metody.

    [!code-csharp[Trin_VstcoreDataExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#9)]

   Teraz Dodaj kod, aby obsłużyć <xref:System.Windows.Forms.Control.Click> zdarzenia przycisku.

## <a name="save-changes-to-the-database"></a>Zapisz zmiany w bazie danych
 Wprowadzono zmiany dane istnieją tylko w przypadku lokalnego zestawu danych, aż jawnie są zapisywane w bazie danych.

### <a name="to-save-changes-to-the-database"></a>Aby zapisać zmiany w bazie danych

1. Dodawanie obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia `button`i Dodaj następujący kod, aby zatwierdzić wszystkie zmiany wprowadzone w zestawie danych w bazie danych.

     [!code-csharp[Trin_VstcoreDataExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#10)]

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz można przetestować skoroszytu, aby sprawdzić, czy dane są wyświetlane zgodnie z oczekiwaniami i że można manipulować danymi w obiekcie listy.

### <a name="to-test-the-data-binding"></a>Aby przetestować powiązanie danych

- Naciśnij klawisz **F5**.

     Sprawdź, czy po otwarciu skoroszytu na obiekt listy jest wypełniony przy użyciu danych z **pracowników** tabeli.

### <a name="to-modify-data"></a>Aby zmodyfikować dane

1. Kliknij komórkę **B7**, który powinien zawierać nazwę **Davolio**.

2. Wpisz nazwę **Anderson**, a następnie naciśnij klawisz **Enter**.

### <a name="to-modify-a-column-header"></a>Aby zmodyfikować nagłówek kolumny

1. Kliknij komórkę, która zawiera nagłówek kolumny **LastName**.

2. Typ **nazwisko**, co obejmuje miejsce między dwoma słowami, a następnie naciśnij klawisz **Enter**.

### <a name="to-save-data"></a>W celu zapisywania danych

1. Kliknij przycisk **Zapisz** w arkuszu.

2. Zakończ działanie programu Excel. Kliknij przycisk **nie** po wyświetleniu monitu, aby zapisać wprowadzone zmiany.

3. Naciśnij klawisz **F5** ponownie uruchomić projekt.

     Obiekt listy jest wypełniony przy użyciu danych z **pracowników** tabeli.

4. Należy zauważyć, że nazwa w komórce **B7** jest nadal **Anderson**, czyli danych zmiany wprowadzone, a następnie zapisywana w bazie danych. Nagłówek kolumny **LastName** został zmieniony powrót do ich oryginalnej postaci, bez spacji, ponieważ nagłówek kolumny nie jest powiązany z bazy danych, a nie zapisał zmiany wprowadzone do arkusza.

### <a name="to-add-new-rows"></a>Aby dodać nowe wiersze

1. Zaznacz komórkę w obiekcie listy.

    W dolnej części listy z gwiazdką pojawi się nowy wiersz (**\\***) w pierwszej komórki nowego wiersza.

2. Dodaj następujące informacje w pusty wiersz.

   |employeeID|LastName|FirstName|Tytuł|
   |----------------|--------------|---------------|-----------|
   |10|Pawłowski|Marek|Kierownikiem ds. sprzedaży|

### <a name="to-delete-rows"></a>Aby usunąć wiersze

- Kliknij prawym przyciskiem myszy numer 16 (wiersz 16) po lewej stronie arkusza, a następnie kliknij przycisk **Usuń**.

### <a name="to-sort-the-rows-in-the-list"></a>Sortowanie wierszy na liście

1. Zaznacz komórkę wewnątrz listy.

     Przycisk strzałki pojawiają się w poszczególne nagłówki kolumn.

2. Kliknij przycisk strzałki w **nazwisko** nagłówek kolumny.

3. Kliknij przycisk **posortować zawartość rosnąco**.

     Wiersze są sortowane alfabetycznie według nazwiska.

### <a name="to-filter-information"></a>Do filtrowania informacji

1. Zaznacz komórkę wewnątrz listy.

2. Kliknij przycisk strzałki w **tytuł** nagłówek kolumny.

3. Kliknij przycisk **przedstawiciel handlowy**.

     Lista zawiera tylko wiersze, które mają **przedstawicielem handlowym firmy** w **tytuł** kolumny.

4. Kliknij przycisk strzałki w **tytuł** ponownie nagłówek kolumny.

5. Kliknij przycisk **(wszystkie)**.

     Filtrowanie jest usuwany, a wszystkie wiersze będą widoczne.

## <a name="next-steps"></a>Następne kroki
 W tym przewodniku przedstawiono podstawowe informacje dotyczące powiązania tabeli w bazie danych na obiekt listy. Poniżej przedstawiono niektóre zadania, które mogą pochodzić dalej:

- Buforuje te dane, dzięki czemu mogą być używane w trybie offline. Aby uzyskać więcej informacji, zobacz [jak: Dane z pamięci podręcznej do użytku w trybie offline lub na serwerze](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Wdrażanie rozwiązania. Aby uzyskać więcej informacji, zobacz [wdrożyć rozwiązanie Office](../vsto/deploying-an-office-solution.md).

- Tworzenie relacji wzorzec/szczegół między polem i tabelę. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie relacji wzorzec szczegół za pomocą pamięci podręcznej zestawu danych](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md).

## <a name="see-also"></a>Zobacz także
- [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)
- [Przewodnik: Proste powiązanie danych w projekcie na poziomie dokumentu](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
