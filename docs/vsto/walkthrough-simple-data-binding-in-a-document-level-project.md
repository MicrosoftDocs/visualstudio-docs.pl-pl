---
title: 'Przewodnik: proste powiązanie danych w projekcie na poziomie dokumentu'
description: Poznaj podstawy powiązania danych w projekcie na poziomie dokumentu i że pojedyncze pole danych w bazie danych SQL Server jest powiązane z nazwanego zakresu w programie Microsoft Excel.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 36d4da65a6cd39c53f1f9d8edf4f9d9b1fe46284
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826853"
---
# <a name="walkthrough-simple-data-binding-in-a-document-level-project"></a>Przewodnik: proste powiązanie danych w projekcie na poziomie dokumentu
  W tym przewodniku pokazano podstawy powiązania danych w projekcie na poziomie dokumentu. Pojedyncze pole danych w bazie danych SQL Server jest powiązane z nazwanego zakresu w Microsoft Office Excel. Przewodnik przedstawia również sposób dodawania kontrolek, które umożliwiają przewijanie wszystkich rekordów w tabeli.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie źródła danych dla projektu programu Excel.

- Dodawanie kontrolek do arkusza.

- Przewijanie rekordów bazy danych.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Dostęp do serwera przy użyciu bazy danych Northwind SQL Server przykładowej bazy danych.

- Uprawnienia do odczytu i zapisu w SQL Server danych.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu
 W tym kroku utworzysz projekt skoroszytu programu Excel.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt skoroszytu programu Excel o nazwie **Moje proste powiązanie danych** przy użyciu Visual Basic lub C#. Upewnij się, **że wybrano opcję Utwórz** nowy dokument. Aby uzyskać więcej informacji, [zobacz How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

   Visual Studio nowy skoroszyt programu Excel w projektancie i dodaje projekt **Moje proste** powiązanie danych do **Eksplorator rozwiązań**.

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

8. Zaznacz pole wyboru obok tabeli **Customers.**

9. Kliknij przycisk **Finish** (Zakończ).

   Kreator dodaje **tabelę Customers** do **okna Źródła** danych. Dodaje również typowany zestaw danych do projektu, który jest widoczny w **Eksplorator rozwiązań**.

## <a name="add-controls-to-the-worksheet"></a>Dodawanie kontrolek do arkusza
 W tym przewodniku potrzebne są dwa nazwane zakresy i cztery przyciski w pierwszym arkuszu. Najpierw dodaj dwa nazwane zakresy z okna **Źródła** danych, aby zostały automatycznie powiązane ze źródłem danych. Następnie dodaj przyciski z **przybornika**.

### <a name="to-add-two-named-ranges"></a>Aby dodać dwa nazwane zakresy

1. Sprawdź, czy *skoroszyt Mój Binding.xlsx* dane jest otwarty w projektancie Visual Studio, z **wyświetlonym arkuszem Sheet1.**

2. Otwórz okno **Źródła danych** i rozwiń węzeł **Klienci.**

3. Wybierz **kolumnę CompanyName,** a następnie kliknij strzałkę listy rozwijanej, która zostanie wyświetlona.

4. Wybierz **pozycję NamedRange** z listy rozwijanej, a następnie przeciągnij kolumnę **CompanyName** do komórki **A1**.

     Kontrolka <xref:Microsoft.Office.Tools.Excel.NamedRange> o nazwie jest `companyNameNamedRange` tworzona w **komórce A1**. W tym samym czasie do projektu są dodawane nazwane , adapter tabeli i <xref:System.Windows.Forms.BindingSource> `customersBindingSource` wystąpienie <xref:System.Data.DataSet> . Kontrolka jest powiązana z <xref:System.Windows.Forms.BindingSource> wystąpieniem <xref:System.Data.DataSet> .

5. Wybierz **kolumnę CustomerID** w **oknie Źródła** danych, a następnie kliknij strzałkę listy rozwijanej, która zostanie wyświetlona.

6. Kliknij **pozycję NamedRange** na liście rozwijanej, a następnie przeciągnij kolumnę **CustomerID** do komórki **B1**.

7. Inna <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolka `customerIDNamedRange` o nazwie jest tworzona w **komórce B1** i powiązana z <xref:System.Windows.Forms.BindingSource> .

### <a name="to-add-four-buttons"></a>Aby dodać cztery przyciski

1. Na karcie **Typowe kontrolki** **przybornika** dodaj kontrolkę <xref:System.Windows.Forms.Button> do komórki **A3** arkusza.

    Ten przycisk ma nazwę `Button1` .

2. Dodaj trzy kolejne przyciski do następujących komórek w tej kolejności, aby nazwy zostały przedstawione w następujący sposób:

   |Komórka|(Nazwa)|
   |----------|--------------|
   |B3|Przycisk 2|
   |C3|Przycisk 3|
   |D3|Przycisk 4|

   Następnym krokiem jest dodanie tekstu do przycisków, a w języku C# dodanie obsługi zdarzeń.

## <a name="initialize-the-controls"></a>Inicjowanie kontrolek
 Ustaw tekst przycisku i dodaj procedury obsługi zdarzeń podczas <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> zdarzenia.

### <a name="to-initialize-the-controls"></a>Aby zainicjować kontrolki

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **Sheet1.vb** lub **Sheet1.cs,** a następnie kliknij polecenie **Wyświetl** kod w menu skrótów.

2. Dodaj następujący kod do metody `Sheet1_Startup` , aby ustawić tekst dla każdego przycisku.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet2":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet2":::

3. Tylko w przypadku języka C# dodaj procedury obsługi zdarzeń dla zdarzeń kliknięcia przycisku do `Sheet1_Startup` metody .

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet3":::

   Teraz dodaj kod do obsługi <xref:System.Windows.Forms.Control.Click> zdarzeń przycisków, aby użytkownik może przeglądać rekordy.

## <a name="add-code-to-enable-scrolling-through-the-records"></a>Dodawanie kodu umożliwiającego przewijanie rekordów
 Dodaj kod do <xref:System.Windows.Forms.Control.Click> procedury obsługi zdarzeń każdego przycisku, aby przechodzić przez rekordy.

### <a name="to-move-to-the-first-record"></a>Aby przejść do pierwszego rekordu

1. Dodaj program obsługi zdarzeń dla zdarzenia przycisku i dodaj następujący <xref:System.Windows.Forms.Control.Click> `Button1` kod, aby przejść do pierwszego rekordu:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet4":::

### <a name="to-move-to-the-previous-record"></a>Aby przejść do poprzedniego rekordu

1. Dodaj program obsługi zdarzeń dla zdarzenia przycisku i dodaj następujący kod, aby przenieść <xref:System.Windows.Forms.Control.Click> pozycję z powrotem o `Button2` jeden:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet5":::

### <a name="to-move-to-the-next-record"></a>Aby przejść do następnego rekordu

1. Dodaj program obsługi zdarzeń dla zdarzenia przycisku i dodaj następujący kod, aby o jeden <xref:System.Windows.Forms.Control.Click> `Button3` przesunić pozycję:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet6":::

### <a name="to-move-to-the-last-record"></a>Aby przejść do ostatniego rekordu

1. Dodaj program obsługi zdarzeń dla zdarzenia przycisku i dodaj następujący <xref:System.Windows.Forms.Control.Click> `Button4` kod, aby przejść do ostatniego rekordu:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet7":::

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz możesz przetestować skoroszyt, aby upewnić się, że możesz przeglądać rekordy w bazie danych.

### <a name="to-test-your-workbook"></a>Aby przetestować skoroszyt

1. Naciśnij **klawisz F5,** aby uruchomić projekt.

2. Upewnij się, że pierwszy rekord występuje w komórkach **A1** i **B1**.

3. Kliknij przycisk ( ) i upewnij się, że następny rekord pojawia się w komórkach **>** `Button3` **A1** i **B1**.

4. Kliknij inne przyciski przewijania, aby potwierdzić, że rekord zmienia się zgodnie z oczekiwaniami.

## <a name="next-steps"></a>Następne kroki
 W tym przewodniku przedstawiono podstawy powiązania nazwanego zakresu z polem w bazie danych. Oto kilka zadań, które mogą się pojawić w następnej części:

- Buforuj dane, aby można było ich używać w trybie offline. Aby uzyskać więcej informacji, [zobacz How to: Cache data for use offline or on a server (Jak: buforować dane do użycia w trybie offline lub na serwerze).](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)

- Powiąż komórki z wieloma kolumnami w tabeli, a nie z jednym polem. Aby uzyskać więcej informacji, [zobacz Przewodnik: złożone powiązanie danych w projekcie na poziomie dokumentu.](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)

- Użyj <xref:System.Windows.Forms.BindingNavigator> kontrolki, aby przewijać rekordy. Aby uzyskać więcej informacji, [zobacz How to: Navigate data with the Windows Forms BindingNavigator (Jak](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms)nawigować po danych za pomocą Windows Forms BindingNavigator).

## <a name="see-also"></a>Zobacz też
- [Wiązanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)
- [Przewodnik: złożone powiązanie danych w projekcie na poziomie dokumentu](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
