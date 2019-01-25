---
title: 'Przewodnik: Aktualizacja wykresu w arkuszu za pomocą przycisków radiowych'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, updating using managed controls
- controls [Office development in Visual Studio], updating worksheets
- worksheets, using radio buttons
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ae451b42642cd3c124b3fe9d5df627c2306a2020
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54873876"
---
# <a name="walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons"></a>Przewodnik: Aktualizacja wykresu w arkuszu za pomocą przycisków radiowych
  W tym przewodniku przedstawiono podstawowe informacje dotyczące za pomocą przycisków radiowych w arkuszu kalkulacyjnym programu Microsoft Office Excel, aby dać użytkownikowi możliwość szybkiego przełączania się między opcjami. W tym przypadku opcje zmieniają styl wykresu.  

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  

 Aby wyświetlić wynik, jako przykład ukończone, zobacz przykład formanty programu Excel w [Office development ― przykłady i wskazówki dotyczące](../vsto/office-development-samples-and-walkthroughs.md).  

 W instruktażu przedstawiono następujące zagadnienia:  

-   Dodawanie grup przycisków radiowych do arkusza.  

-   Zmiana stylu wykresu, gdy opcja jest zaznaczona.  

> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  

## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  

-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  

## <a name="add-a-chart-to-a-worksheet"></a>Dodawanie wykresu do arkusza  
 Można utworzyć projektu skoroszytu programu Excel, który dostosowuje istniejący skoroszyt. W tym przewodniku będzie dodać wykres do skoroszytu, a następnie użyć tego skoroszytu w nowym rozwiązaniu programu Excel. Źródło danych, w tym instruktażu jest arkusza o nazwie **danych wykresu**.  

### <a name="to-add-the-data"></a>Aby dodać dane  

1. Otwórz program Microsoft Excel.  

2. Kliknij prawym przyciskiem myszy **sheet3 —** kartę, a następnie kliknij przycisk **Zmień nazwę** w menu skrótów.  

3. Zmień nazwę arkusza **danych wykresu**.  

4. Dodaj następujące dane do **danych wykresu** z komórki A4 jest lewy górny róg i E8 prawym dolnym rogu.  

   ||1.|Q2|K3|KWARTAŁ 4|  
   |-|--------|--------|--------|--------|  
   |Zachód|500|550|550|600|  
   |Wschodnie Stany|600|625|675|700|  
   |Północna|450|470|490|510|  
   |Południowa|800|750|775|790|  

   Następnie dodaj wykres do pierwszego arkusza, aby wyświetlić dane.  

### <a name="to-add-a-chart-in-excel"></a>Aby dodać wykres w programie Excel  

1.  Na **Wstaw** na karcie **wykresy** grupy, kliknij przycisk **kolumny**, a następnie kliknij przycisk **wszystkie typy wykresów**.  

2.  W **Wstaw wykres** okno dialogowe, kliknij przycisk **OK**.  

3.  Na **projektowania** na karcie **danych** grupy, kliknij przycisk **wybierz dane**.  

4.  W **wybierz źródło danych** okno dialogowe, kliknij przycisk w **zakres Chartdata** i wyczyść wszystkie wybór domyślny.  

5.  W **danych wykresu** arkusz, wybierz bloku komórek, który zawiera liczby, która obejmuje A4 w lewym górnym rogu do E8 w prawym dolnym rogu.  

6.  W **wybierz źródło danych** okno dialogowe, kliknij przycisk **OK**.  

7.  Zmienianie położenia wykres, aby prawy górny róg wyrównuje komórki zawierającej **E2**.  

8.  Zapisz plik na dysku C i nadaj mu nazwę **ExcelChart.xlsx**.  

9. Zakończ działanie programu Excel.  

## <a name="create-a-new-project"></a>Tworzenie nowego projektu  
 W tym kroku utworzysz projekt skoroszyt programu Excel na podstawie **ExcelChart** skoroszytu.  

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  

1.  Utwórz projektu skoroszytu programu Excel o nazwie **Moje wykresu programu Excel**. W kreatorze Wybierz **Kopiuj istniejący dokument**.  

     Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  

2.  Kliknij przycisk **Przeglądaj** przycisk, a następnie przejdź do skoroszytu, utworzonej we wcześniejszej części tego przewodnika.  

3.  Kliknij przycisk **OK**.  

     Visual Studio zostanie otwarty nowy skoroszyt programu Excel w Projektancie i dodaje **Moje wykresu programu Excel** projekt **Eksploratora rozwiązań**.  

## <a name="set-properties-of-the-chart"></a>Ustawianie właściwości wykresu  
 Podczas tworzenia nowego projektu skoroszytu programu Excel, który korzysta z istniejącego skoroszytu kontrolki hosta są tworzone automatycznie dla wszystkich nazwane zakresy, listę obiektów i wykresy w skoroszycie. Można zmienić nazwę <xref:Microsoft.Office.Tools.Excel.Chart> kontroli przy użyciu **właściwości** okna.  

### <a name="to-change-the-name-of-the-chart-control"></a>Aby zmienić nazwę formantu wykresu  

1.  Wybierz <xref:Microsoft.Office.Tools.Excel.Chart> kontroli w Projektancie i Zmień następujące właściwości w **właściwości** okna.  

    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**dataChart**|  
    |**HasLegend**|**false**|  

## <a name="add-controls"></a>Dodawanie formantów  
 Ten arkusz używa przycisków radiowych pozwala użytkownikom można szybko zmienić styl wykresu. Jednak przycisków radiowych muszą być wyłączny — po wybraniu jednego przycisku żaden inny przycisk w grupie można wybrać w tym samym czasie. To zachowanie nie jest realizowane domyślnie po dodaniu kilku przycisków radiowych do arkusza.  

 Jednym ze sposobów, aby dodać to zachowanie jest grupa przycisków radiowych w kontrolkę użytkownika, pisanie kodu pod kontrolkę użytkownika, a następnie dodaj formant użytkownika do arkusza.  

### <a name="to-add-a-user-control"></a>Aby dodać kontrolkę użytkownika  

1.  Wybierz **Moje wykresu programu Excel** projektu w **Eksploratora rozwiązań**.  

2.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  

3.  W **Dodaj nowy element** okno dialogowe, kliknij przycisk **kontrolki użytkownika**, nazwij kontrolkę **ChartOptions,** i kliknij przycisk **Dodaj**.  

### <a name="to-add-radio-buttons-to-the-user-control"></a>Aby dodać przycisków radiowych do kontrolki użytkownika  

1. Jeśli formant użytkownika nie jest widoczny w projektancie, kliknij dwukrotnie **ChartOptions** w **Eksploratora rozwiązań**.  

2. Z **wspólnych formantów** karcie **przybornika**, przeciągnij **przycisk radiowy** sterowania do formantu użytkownika, a następnie Zmień następujące właściwości.  


   | Właściwość | Wartość |
   |----------|------------------|
   | **Nazwa** | **columnChart** |
   | **Text** | **Wykres kolumnowy** |


3. Dodaj drugi przycisk radiowy do formantu użytkownika, a następnie Zmień następujące właściwości.  


   | Właściwość | Wartość |
   |----------|---------------|
   | **Nazwa** | **barChart** |
   | **Text** | **Wykres słupkowy** |


4. Dodaj trzeci przycisk radiowy do formantu użytkownika, a następnie Zmień następujące właściwości.  


   | Właściwość | Wartość |
   |----------|----------------|
   | **Nazwa** | **lineChart** |
   | **Text** | **Wykres liniowy** |


5. Dodaj czwarty przycisku radiowego do formantu użytkownika, a następnie Zmień następujące właściwości.  

   |Właściwość|Wartość|  
   |--------------|-----------|  
   |**Nazwa**|**areaBlockChart**|  
   |**Text**|**Wykres bloku**|  

   Następnie napisz kod, aby zaktualizować wykresu, gdy kliknięto przycisk radiowy.  

## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>Zmiana stylu wykresu, gdy przycisk radiowy zostanie wybrany  
 Teraz możesz dodać kod, aby zmienić styl wykresu. Aby to zrobić, Utwórz zdarzenie publiczne w kontrolce użytkownika, Dodaj właściwość można ustawić typ wyboru i utworzyć program obsługi zdarzeń dla `CheckedChanged` zdarzenia każdego przycisków radiowych.  

### <a name="to-create-an-event-and-property-on-a-user-control"></a>Aby utworzyć zdarzenie i właściwości w kontrolce użytkownika  

1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy formant użytkownika, a następnie kliknij przycisk **Wyświetl kod**.  

2.  Dodaj kod, aby `ChartOptions` klasy w celu utworzenia `SelectionChanged` zdarzeń i `Selection` właściwości.  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#13)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#13)]  

### <a name="to-handle-the-checkedchanged-event-of-the-radio-buttons"></a>Do obsługi zdarzenia CheckedChanged przycisków radiowych  

1.  Ustaw typ wykresu w `CheckedChanged` program obsługi zdarzeń `areaBlockChart` przycisk radiowy, a następnie wywołaj zdarzenie.  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#14)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#14)]  

2.  Ustaw typ wykresu w `CheckedChanged` program obsługi zdarzeń `barChart` przycisku radiowego.  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#15)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#15)]  

3.  Ustaw typ wykresu w `CheckedChanged` program obsługi zdarzeń `columnChart` przycisku radiowego.  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#16)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#16)]  

4.  Ustaw typ wykresu w `CheckedChanged` program obsługi zdarzeń `lineChart` przycisku radiowego.  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#17)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#17)]  

5.  W języku C# należy dodać obsługę zdarzeń dla przycisków radiowych. Możesz dodać kod do `ChartOptions` Konstruktor poniżej wywołania `InitializeComponent`. Aby uzyskać informacje o sposobie tworzenia procedury obsługi zdarzeń, zobacz [jak: Tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  

     [!code-cs[Trin_VstcoreProgrammingControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#18)]  

## <a name="add-the-user-control-to-the-worksheet"></a>Dodaj kontrolkę użytkownika do arkusza  
 Podczas kompilowania rozwiązania nowej kontrolki użytkownika jest automatycznie dodawany do **przybornika**. Następnie można przeciągać formantu z **przybornika** do arkusza.  

### <a name="to-add-the-user-control-your-worksheet"></a>Aby dodać kontrolkę użytkownika arkusza  

1.  Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  

     **ChartOptions** formant użytkownika jest dodawany do **przybornika**.  

2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Sheet1.vb** lub **Sheet1.cs**, a następnie kliknij przycisk **Projektant widoków**.  

3.  Przeciągnij **ChartOptions** z kontrolować **przybornika** do arkusza.  

     Nowy formant o nazwie `my_Excel_Chart_ChartOptions1` zostanie dodany do projektu.  

4.  Zmień nazwę kontrolki na **ChartOptions1**.  

## <a name="change-the-chart-type"></a>Zmień typ wykresu  
 Aby zmienić typ wykresu, należy utworzyć program obsługi zdarzeń, który ustawia styl zgodnie z opcją wybrana w kontrolce użytkownika.  

### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-worksheet"></a>Aby zmienić typ wykresu, który jest wyświetlany w arkuszu  

1.  Dodaj następującą obsługę zdarzeń w celu `Sheet1` klasy.  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#19)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#19)]  

2.  W języku C#, należy dodać program obsługi zdarzeń dla formantu użytkownika, aby <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> zdarzeń, jak pokazano poniżej. Aby uzyskać informacje o sposobie tworzenia procedury obsługi zdarzeń, zobacz [jak: Tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  

     [!code-cs[Trin_VstcoreProgrammingControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#20)]  

## <a name="test-the-application"></a>Testowanie aplikacji  
 Teraz możesz przetestować skoroszytu, aby sprawdzić, czy wykres wyglądzie prawidłowo po wybraniu przycisku radiowego.  

### <a name="to-test-your-workbook"></a>Aby przetestować skoroszytu  

1.  Naciśnij klawisz **F5** Aby uruchomić projekt.  

2.  Wybierz różne przycisków radiowych.  

3.  Upewnij się, że styl wykresu zmienia się zgodnie z wyborem.  

## <a name="next-steps"></a>Następne kroki  
 W tym instruktażu przedstawiono podstawy używania przycisków radiowych i style wykresu w arkuszu. Poniżej przedstawiono niektóre zadania, które mogą pochodzić dalej:  

-   Wdrażanie projektu. Aby uzyskać więcej informacji, zobacz [wdrożyć rozwiązanie Office](../vsto/deploying-an-office-solution.md).  

-   Za pomocą przycisku, aby wypełnić pole tekstowe. Aby uzyskać więcej informacji, zobacz [instruktażu: Wyświetlanie tekstu w polu tekstowym w arkuszu za pomocą przycisku](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  

-   Zmiana formatowania arkusza za pomocą pola wyboru. Aby uzyskać więcej informacji, zobacz [instruktażu: Arkusz Zmienianie formatowania za pomocą formantów CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).  

## <a name="see-also"></a>Zobacz także  
 [Wskazówki dotyczące za pomocą programu Excel](../vsto/walkthroughs-using-excel.md)  
