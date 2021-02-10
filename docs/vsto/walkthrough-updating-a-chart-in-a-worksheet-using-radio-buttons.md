---
title: Aktualizowanie wykresu w arkuszu za pomocą przycisków radiowych
description: Poznaj podstawy używania przycisków radiowych w arkuszu programu Microsoft Excel, aby dać użytkownikowi możliwość szybkiego przełączania się między opcjami.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b1c9da3b1d019c77988ef01e1b3c019dd3f1d775
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937319"
---
# <a name="walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons"></a>Wskazówki: aktualizacja wykresu w arkuszu za pomocą przycisków radiowych
  W tym instruktażu przedstawiono podstawowe informacje dotyczące używania przycisków radiowych w arkuszu programu Excel Microsoft Office, aby dać użytkownikowi możliwość szybkiego przełączania się między opcjami. W takim przypadku opcje zmieniają styl wykresu.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Aby zobaczyć wynik jako ukończony przykład, zobacz przykład kontrolki programu Excel w programie [Office przykłady i przewodniki dotyczące projektowania](../vsto/office-development-samples-and-walkthroughs.md).

 W instruktażu przedstawiono następujące zagadnienia:

- Dodawanie grupy przycisków radiowych do arkusza.

- Zmiana stylu wykresu w przypadku wybrania opcji.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="add-a-chart-to-a-worksheet"></a>Dodawanie wykresu do arkusza
 Można utworzyć projekt skoroszytu programu Excel, który dostosowuje istniejący skoroszyt. W tym instruktażu dodasz wykres do skoroszytu, a następnie użyjesz tego skoroszytu w nowym rozwiązaniu programu Excel. Źródło danych w tym instruktażu jest arkusz o nazwie **dane dla wykresu**.

### <a name="to-add-the-data"></a>Aby dodać dane

1. Otwórz program Microsoft Excel.

2. Kliknij prawym przyciskiem myszy kartę **Sheet3** , a następnie kliknij polecenie **Zmień nazwę** w menu skrótów.

3. Zmień nazwę arkusza na **dane dla wykresu**.

4. Dodaj następujące dane do **danych dla wykresu** z komórką A4 w lewym górnym rogu, a następnie E8 prawym dolnym rogu.

   |Region/kwartał|Q1|Q2|Q3|Q4|
   |-|--------|--------|--------|--------|
   |Zachód|500|550|550|600|
   |Wschód|600|625|675|700|
   |Północ|450|470|490|510|
   |Południowa|800|750|775|790|

   Następnie Dodaj wykres do pierwszego arkusza, aby wyświetlić dane.

### <a name="to-add-a-chart-in-excel"></a>Aby dodać wykres w programie Excel

1. Na karcie **Wstawianie** w grupie **wykresy** kliknij pozycję **kolumna**, a następnie kliknij pozycję **wszystkie typy wykresów**.

2. W oknie dialogowym **Wstawianie wykresu** kliknij przycisk **OK**.

3. Na karcie **projekt** w grupie **dane** kliknij przycisk **Wybierz dane**.

4. W oknie dialogowym **Wybierz źródło danych** kliknij pole **zakres plik ChartData** i wyczyść wszystkie wybrane ustawienia domyślne.

5. W arkuszu **dane dla wykresu** wybierz blok komórek zawierający liczby, w tym A4 w lewym górnym rogu do E8 w prawym dolnym rogu.

6. W oknie dialogowym **Wybierz źródło danych** kliknij przycisk **OK**.

7. Zmień położenie wykresu tak, aby prawy górny róg wyrównuje z komórką **E2**.

8. Zapisz plik na dysku C i nadaj mu nazwę **ExcelChart.xlsx**.

9. Zamknij program Excel.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu
 W tym kroku utworzysz projekt skoroszytu programu Excel na podstawie skoroszytu **ExcelChart** .

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt skoroszytu programu Excel o nazwie **My Excel Chart**. W kreatorze wybierz pozycję **Kopiuj istniejący dokument**.

     Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Kliknij przycisk **Przeglądaj** i przejdź do skoroszytu utworzonego wcześniej w tym instruktażu.

3. Kliknij przycisk **OK**.

     Program Visual Studio otwiera nowy skoroszyt programu Excel w Projektancie i dodaje projekt **wykresu programu Excel** do **Eksplorator rozwiązań**.

## <a name="set-properties-of-the-chart"></a>Ustawianie właściwości wykresu
 Podczas tworzenia nowego projektu skoroszytu programu Excel, który używa istniejącego skoroszytu, formanty hosta są tworzone automatycznie dla wszystkich nazwanych zakresów, obiektów list i wykresów w skoroszycie. Nazwę kontrolki można zmienić przy <xref:Microsoft.Office.Tools.Excel.Chart> użyciu okna **Właściwości** .

### <a name="to-change-the-name-of-the-chart-control"></a>Aby zmienić nazwę kontrolki wykresu

1. Zaznacz <xref:Microsoft.Office.Tools.Excel.Chart> kontrolkę w Projektancie i Zmień następujące właściwości w oknie **Właściwości** .

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**Wykres datagrafu**|
    |**HasLegend**|**false**|

## <a name="add-controls"></a>Dodawanie kontrolek
 Ten arkusz używa przycisków radiowych, aby umożliwić użytkownikom szybkie zmienianie stylu wykresu. Jednak przyciski radiowe muszą być wyłączne — po wybraniu jednego przycisku nie można wybrać żadnego innego przycisku w grupie. To zachowanie nie jest wykonywane domyślnie po dodaniu kilku przycisków radiowych do arkusza.

 Jednym ze sposobów na dodanie tego zachowania jest Grupowanie przycisków radiowych w kontrolce użytkownika, napisanie kodu za kontrolką użytkownika, a następnie dodanie kontrolki użytkownika do arkusza.

### <a name="to-add-a-user-control"></a>Aby dodać kontrolkę użytkownika

1. Wybierz projekt **wykresu programu Excel** w **Eksplorator rozwiązań**.

2. W menu **projekt** kliknij polecenie **Dodaj nowy element**.

3. W oknie dialogowym **Dodaj nowy element** kliknij pozycję **kontrolka użytkownika**, nazwij formant **ChartOptions,** a następnie kliknij przycisk **Dodaj**.

### <a name="to-add-radio-buttons-to-the-user-control"></a>Aby dodać przyciski radiowe do kontrolki użytkownika

1. Jeśli formant użytkownika nie jest widoczny w projektancie, kliknij dwukrotnie pozycję **ChartOptions** w **Eksplorator rozwiązań**.

2. Na karcie **Formanty standardowe** **przybornika** przeciągnij kontrolkę **przycisk radiowy** do kontrolki użytkownika i Zmień następujące właściwości.

   | Właściwość | Wartość |
   |----------|------------------|
   | **Nazwa** | **columnChart (wykres kolumnowy)** |
   | **Tekst** | **Wykres kolumnowy** |

3. Dodaj drugi przycisk radiowy do kontrolki użytkownika i Zmień następujące właściwości.

   | Właściwość | Wartość |
   |----------|---------------|
   | **Nazwa** | **barChart (wykres słupkowy)** |
   | **Tekst** | **Wykres słupkowy** |

4. Dodaj trzeci przycisk radiowy do kontrolki użytkownika i Zmień następujące właściwości.

   | Właściwość | Wartość |
   |----------|----------------|
   | **Nazwa** | **lineChart (wykres liniowy)** |
   | **Tekst** | **Wykres liniowy** |

5. Dodaj czwarty przycisk radiowy do kontrolki użytkownika i Zmień następujące właściwości.

   |Właściwość|Wartość|
   |--------------|-----------|
   |**Nazwa**|**areaBlockChart**|
   |**Tekst**|**Wykres blokowy obszaru**|

   Następnie napisz kod w celu zaktualizowania wykresu po kliknięciu przycisku radiowego.

## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>Zmień styl wykresu, gdy zostanie wybrany przycisk radiowy
 Teraz można dodać kod, aby zmienić styl wykresu. W tym celu należy utworzyć zdarzenie publiczne na kontrolce użytkownika, dodać właściwość w celu ustawienia typu zaznaczenia i utworzyć procedurę obsługi zdarzeń dla `CheckedChanged` każdego przycisku radiowego.

### <a name="to-create-an-event-and-property-on-a-user-control"></a>Aby utworzyć zdarzenie i właściwość na kontrolce użytkownika

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy kontrolkę użytkownika, a następnie kliknij polecenie **Wyświetl kod**.

2. Dodaj kod do `ChartOptions` klasy, aby utworzyć `SelectionChanged` zdarzenie i `Selection` Właściwość.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#13)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#13)]

### <a name="to-handle-the-checkedchanged-event-of-the-radio-buttons"></a>Aby obsłużyć zdarzenie CheckedChanged przycisków radiowych

1. Ustaw typ wykresu w `CheckedChanged` obsłudze zdarzeń `areaBlockChart` przycisku radiowego, a następnie zgłoś zdarzenie.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#14)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#14)]

2. Ustaw typ wykresu w `CheckedChanged` obsłudze zdarzeń `barChart` przycisku radiowego.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#15)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#15)]

3. Ustaw typ wykresu w `CheckedChanged` obsłudze zdarzeń `columnChart` przycisku radiowego.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#16)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#16)]

4. Ustaw typ wykresu w `CheckedChanged` obsłudze zdarzeń `lineChart` przycisku radiowego.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#17)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#17)]

5. W języku C# należy dodać procedury obsługi zdarzeń dla przycisków radiowych. Możesz dodać kod do `ChartOptions` konstruktora, pod wywołaniem `InitializeComponent` . Informacje o sposobach tworzenia programów obsługi zdarzeń znajdują się [w temacie How to: Create Event Handles in Office projects](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-cs[Trin_VstcoreProgrammingControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#18)]

## <a name="add-the-user-control-to-the-worksheet"></a>Dodaj kontrolkę użytkownika do arkusza
 Podczas kompilowania rozwiązania Nowa kontrolka użytkownika jest automatycznie dodawana do **przybornika**. Następnie możesz przeciągnąć formant z **przybornika** do arkusza.

### <a name="to-add-the-user-control-your-worksheet"></a>Aby dodać kontrolkę użytkownika do arkusza

1. W menu **Kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.

     Kontrolka użytkownika **ChartOptions** jest dodawana do **przybornika**.

2. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **Arkusz1. vb** lub **Sheet1.cs**, a następnie kliknij pozycję **Projektant widoków**.

3. Przeciągnij formant **ChartOptions** z **przybornika** do arkusza.

     Nowa kontrolka o nazwie `my_Excel_Chart_ChartOptions1` zostanie dodana do projektu.

4. Zmień nazwę kontrolki na **ChartOptions1**.

## <a name="change-the-chart-type"></a>Zmień typ wykresu
 Aby zmienić typ wykresu, Utwórz procedurę obsługi zdarzeń, która ustawia styl zgodnie z opcją wybraną w kontrolce użytkownika.

### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-worksheet"></a>Aby zmienić typ wykresu wyświetlanego w arkuszu

1. Dodaj do klasy następujący program obsługi zdarzeń `Sheet1` .

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#19)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#19)]

2. W języku C# należy dodać procedurę obsługi zdarzeń dla kontrolki użytkownika do <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> zdarzenia, jak pokazano poniżej. Informacje o sposobach tworzenia programów obsługi zdarzeń znajdują się [w temacie How to: Create Event Handles in Office projects](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-cs[Trin_VstcoreProgrammingControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#20)]

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz można testować skoroszyt, aby sprawdzić, czy wykres jest prawidłowo skonfigurowany, gdy wybierzesz przycisk radiowy.

### <a name="to-test-your-workbook"></a>Aby przetestować skoroszyt

1. Naciśnij klawisz **F5** , aby uruchomić projekt.

2. Wybierz różne przyciski radiowe.

3. Upewnij się, że styl wykresu zmieni się, aby dopasować zaznaczenie.

## <a name="next-steps"></a>Następne kroki
 W tym instruktażu przedstawiono podstawowe informacje na temat używania przycisków radiowych i stylów wykresu w arkuszach. Poniżej przedstawiono kilka zadań, które mogą wystąpić poniżej:

- Wdrażanie projektu. Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązania biurowego](../vsto/deploying-an-office-solution.md).

- Wypełnienie pola tekstowego za pomocą przycisku. Aby uzyskać więcej informacji, zobacz [Przewodnik: wyświetlanie tekstu w polu tekstowym w arkuszu za pomocą przycisku](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).

- Zmień formatowanie arkusza przy użyciu pól wyboru. Aby uzyskać więcej informacji, zobacz [Przewodnik: zmiana formatowania arkusza za pomocą kontrolek CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>Zobacz też
- [Wskazówki dotyczące korzystania z programu Excel](../vsto/walkthroughs-using-excel.md)
