---
title: 'Przewodnik: proste powiązanie danych w projekcie na poziomie dokumentu'
description: Poznaj podstawowe informacje o powiązaniu danych w projekcie na poziomie dokumentu i czy pojedyncze pole danych w bazie danych SQL Server jest powiązane z nazwanym zakresem w programie Microsoft Excel.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], worksheet cell to Database field
- worksheets [Office development in Visual Studio], binding worksheet cell to Database field
- Database field [Office development in Visual Studio]
- data [Office development in Visual Studio], binding data
- simple data binding [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 868a120baa8207d922d3dee55e10c8e903381e19
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524101"
---
# <a name="walkthrough-simple-data-binding-in-a-document-level-project"></a>Przewodnik: proste powiązanie danych w projekcie na poziomie dokumentu
  W tym instruktażu przedstawiono podstawowe informacje o powiązaniu danych w projekcie na poziomie dokumentu. Pojedyncze pole danych w bazie danych SQL Server jest powiązane z nazwanym zakresem w programie Microsoft Office Excel. W tym przewodniku pokazano również, jak dodać kontrolki, które umożliwiają przewijanie wszystkich rekordów w tabeli.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie źródła danych dla projektu programu Excel.

- Dodawanie formantów do arkusza.

- Przewijanie rekordów bazy danych.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Dostęp do serwera za pomocą przykładowej bazy danych Northwind SQL Server.

- Uprawnienia do odczytu i zapisu w bazie danych SQL Server.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu
 W tym kroku utworzysz projekt skoroszytu programu Excel.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt skoroszytu programu Excel o nazwie **My prostego powiązania danych** przy użyciu Visual Basic lub C#. Upewnij się, że wybrano **Utwórz nowy dokument** . Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

   Program Visual Studio otwiera nowy skoroszyt programu Excel w Projektancie i dodaje projekt **My Simple Data Binding** do **Eksplorator rozwiązań**.

## <a name="create-the-data-source"></a>Tworzenie źródła danych
 Użyj okna **źródła danych** , aby dodać do projektu typ zestawu danych.

### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych

1. Jeśli okno **źródła danych** nie jest widoczne, Wyświetl je na pasku menu, wybierając opcję **Wyświetl**  >  **inne**  >  **źródła danych** systemu Windows.

2. Wybierz pozycję **Dodaj nowe źródło danych** , aby uruchomić **Kreatora konfiguracji źródła danych**.

3. Wybierz pozycję **baza danych** , a następnie kliknij przycisk **dalej**.

4. Wybierz połączenie danych z przykładową bazą danych Northwind SQL Server lub Dodaj nowe połączenie za pomocą przycisku **nowe połączenie** .

5. Po wybraniu lub utworzeniu połączenia kliknij przycisk **dalej**.

6. Usuń zaznaczenie opcji Zapisz połączenie, jeśli jest zaznaczone, a następnie kliknij przycisk **dalej**.

7. Rozwiń węzeł **tabele** w oknie **obiekty bazy danych** .

8. Zaznacz pole wyboru obok tabeli **Customers** .

9. Kliknij przycisk **Finish** (Zakończ).

   Kreator dodaje tabelę **Customers** do okna **źródła danych** . Dodaje również typ DataSet do projektu, który jest widoczny w **Eksplorator rozwiązań**.

## <a name="add-controls-to-the-worksheet"></a>Dodawanie formantów do arkusza
 W tym instruktażu potrzebne są dwa nazwane zakresy i cztery przyciski w pierwszym arkuszu. Najpierw Dodaj dwa nazwane zakresy z okna **źródła danych** , aby były one automatycznie powiązane ze źródłem danych. Następnie Dodaj przyciski z **przybornika**.

### <a name="to-add-two-named-ranges"></a>Aby dodać dwa nazwane zakresy

1. Upewnij się, że skoroszyt *moje dane proste Binding.xlsx* jest otwarty w projektancie programu Visual Studio z wyświetlonym arkuszem **Arkusz1** .

2. Otwórz okno **źródła danych** i rozwiń węzeł **klienci** .

3. Wybierz kolumnę **NazwaFirmy** , a następnie kliknij strzałkę listy rozwijanej, która zostanie wyświetlona.

4. Na liście rozwijanej wybierz pozycję **NamedRange** , a następnie przeciągnij kolumnę **NazwaFirmy** do komórki **a1**.

     <xref:Microsoft.Office.Tools.Excel.NamedRange>Kontrolka o nazwie `companyNameNamedRange` została utworzona w komórce **a1**. W tym samym czasie <xref:System.Windows.Forms.BindingSource> nazwa `customersBindingSource` , karta tabeli i <xref:System.Data.DataSet> wystąpienie są dodawane do projektu. Formant jest powiązany z <xref:System.Windows.Forms.BindingSource> , który z kolei jest powiązany z <xref:System.Data.DataSet> wystąpieniem.

5. Wybierz kolumnę **CustomerID** w oknie **źródła danych** , a następnie kliknij strzałkę listy rozwijanej, która zostanie wyświetlona.

6. Kliknij pozycję **NamedRange** na liście rozwijanej, a następnie przeciągnij kolumnę **CustomerID** do komórki **B1**.

7. Inna <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolka o nazwie `customerIDNamedRange` została utworzona w komórce **B1** i powiązana z <xref:System.Windows.Forms.BindingSource> .

### <a name="to-add-four-buttons"></a>Aby dodać cztery przyciski

1. Na karcie **Formanty standardowe** **przybornika** Dodaj <xref:System.Windows.Forms.Button> kontrolkę do komórki **a3** arkusza.

    Ten przycisk ma nazwę `Button1` .

2. Dodaj trzy więcej przycisków do następujących komórek w tej kolejności, tak aby nazwy były wyświetlane:

   |Komórka|(Nazwa)|
   |----------|--------------|
   |B3|Button2|
   |C3|Button3|
   |D3|Button4|

   Następnym krokiem jest dodanie tekstu do przycisków i w języku C# obsługa zdarzeń.

## <a name="initialize-the-controls"></a>Inicjowanie formantów
 Ustaw tekst przycisku i Dodaj obsługę zdarzeń podczas <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> zdarzenia.

### <a name="to-initialize-the-controls"></a>Aby zainicjować formanty

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **Arkusz1. vb** lub **Sheet1.cs**, a następnie kliknij polecenie **Wyświetl kod** w menu skrótów.

2. Dodaj następujący kod do metody, `Sheet1_Startup` Aby ustawić tekst dla każdego przycisku.

    [!code-csharp[Trin_VstcoreDataExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#2)]
    [!code-vb[Trin_VstcoreDataExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#2)]

3. W przypadku tylko języka C# Dodaj obsługę zdarzeń dla przycisku kliknij zdarzenia do `Sheet1_Startup` metody.

    [!code-csharp[Trin_VstcoreDataExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#3)]

   Teraz Dodaj kod obsługujący <xref:System.Windows.Forms.Control.Click> zdarzenia przycisków, aby użytkownik mógł przeglądać rekordy.

## <a name="add-code-to-enable-scrolling-through-the-records"></a>Dodaj kod, aby włączyć przewijanie rekordów
 Dodaj kod do <xref:System.Windows.Forms.Control.Click> procedury obsługi zdarzeń każdego przycisku, aby przejść przez rekordy.

### <a name="to-move-to-the-first-record"></a>Aby przejść do pierwszego rekordu

1. Dodaj program obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia `Button1` przycisku i Dodaj następujący kod, aby przejść do pierwszego rekordu:

     [!code-csharp[Trin_VstcoreDataExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#4)]

### <a name="to-move-to-the-previous-record"></a>Aby przejść do poprzedniego rekordu

1. Dodaj procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia `Button2` przycisku, a następnie Dodaj następujący kod, aby przenieść pozycję ponownie o jeden:

     [!code-csharp[Trin_VstcoreDataExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#5)]

### <a name="to-move-to-the-next-record"></a>Aby przejść do następnego rekordu

1. Dodaj procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia `Button3` przycisku i Dodaj następujący kod, aby przejść do pozycji o jeden:

     [!code-csharp[Trin_VstcoreDataExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#6)]

### <a name="to-move-to-the-last-record"></a>Aby przejść do ostatniego rekordu

1. Dodaj program obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia `Button4` przycisku i Dodaj następujący kod, aby przejść do ostatniego rekordu:

     [!code-csharp[Trin_VstcoreDataExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#7)]

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz możesz przetestować skoroszyt, aby upewnić się, że można przeglądać rekordy w bazie danych.

### <a name="to-test-your-workbook"></a>Aby przetestować skoroszyt

1. Naciśnij klawisz **F5** , aby uruchomić projekt.

2. Upewnij się, że pierwszy rekord pojawia się w komórkach **a1** i **B1**.

3. Kliknij **>** przycisk ( `Button3` ) i upewnij się, że następny rekord pojawia się w komórce **a1** i **B1**.

4. Kliknij inne przyciski przewijania, aby potwierdzić, że rekord zostanie zmieniony zgodnie z oczekiwaniami.

## <a name="next-steps"></a>Następne kroki
 W tym instruktażu przedstawiono podstawowe informacje o powiązaniu nazwanego zakresu do pola w bazie danych. Poniżej przedstawiono kilka zadań, które mogą wystąpić poniżej:

- Buforuj dane, aby można było ich używać w trybie offline. Aby uzyskać więcej informacji, zobacz [jak: dane pamięci podręcznej do użycia w trybie offline lub na serwerze](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Powiąż komórki z wieloma kolumnami w tabeli zamiast do jednego pola. Aby uzyskać więcej informacji, zobacz [Przewodnik: złożone powiązanie danych w projekcie na poziomie dokumentu](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md).

- Użyj <xref:System.Windows.Forms.BindingNavigator> kontrolki, aby przewijać rekordy. Aby uzyskać więcej informacji, zobacz [How to: nawigowanie po danych za pomocą kontrolki Windows Forms BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).

## <a name="see-also"></a>Zobacz też
- [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)
- [Przewodnik: złożone powiązanie danych w projekcie na poziomie dokumentu](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
