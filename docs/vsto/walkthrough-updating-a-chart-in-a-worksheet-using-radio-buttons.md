---
title: Aktualizowanie wykresu w arkuszu przy użyciu przycisków radiowych
description: Poznaj podstawy używania przycisków radiowych w arkuszu programu Microsoft Excel, aby zapewnić użytkownikowi sposób szybkiego przełączania się między opcjami.
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
ms.openlocfilehash: 3d61579181f00d97a74cc48e022bb5d93a05c0f0
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828179"
---
# <a name="walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons"></a>Wskazówki: aktualizacja wykresu w arkuszu za pomocą przycisków radiowych
  W tym przewodniku przedstawiono podstawowe informacje dotyczące używania przycisków radiowych w Microsoft Office programu Excel, aby zapewnić użytkownikowi sposób szybkiego przełączania się między opcjami. W tym przypadku opcje zmieniają styl wykresu.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Aby zobaczyć wynik jako ukończony przykład, zobacz Przykład formantów programu Excel w przykładach i przewodnikach dla programistów [pakietu Office.](../vsto/office-development-samples-and-walkthroughs.md)

 W instruktażu przedstawiono następujące zagadnienia:

- Dodawanie grupy przycisków radiowych do arkusza.

- Zmiana stylu wykresu po wybraniu opcji.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [Personalizowanie środowiska IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="add-a-chart-to-a-worksheet"></a>Dodawanie wykresu do arkusza
 Możesz utworzyć projekt skoroszytu programu Excel, który dostosowuje istniejący skoroszyt. W tym przewodniku dodasz wykres do skoroszytu, a następnie użyjemy tego skoroszytu w nowym rozwiązaniu programu Excel. Źródło danych w tym przewodniku to arkusz o nazwie **Dane dla wykresu**.

### <a name="to-add-the-data"></a>Aby dodać dane

1. Otwórz program Microsoft Excel.

2. Kliknij prawym przyciskiem myszy **arkusz3** kartę, a następnie kliknij przycisk **Zmień nazwę** w menu skrótów.

3. Zmień nazwę arkusza na **Dane dla wykresu**.

4. Dodaj następujące dane do tabeli **Dane dla wykresu** z komórką A4 w lewym górnym rogu, a komórką E8 w prawym dolnym rogu.

   |Region/kwartał|Q1|Q2|Q3|Q4|
   |-|--------|--------|--------|--------|
   |Zachód|500|550|550|600|
   |Wschód|600|625|675|700|
   |Północ|450|470|490|510|
   |Południowa|800|750|775|790|

   Następnie dodaj wykres do pierwszego arkusza, aby wyświetlić dane.

### <a name="to-add-a-chart-in-excel"></a>Aby dodać wykres w programie Excel

1. Na karcie **Wstawianie** w grupie **Wykresy** kliknij pozycję **Kolumna**, a następnie kliknij **pozycję Wszystkie typy wykresów.**

2. W **oknie dialogowym Wstaw wykres** kliknij przycisk **OK.**

3. Na karcie **Projekt** w grupie **Dane** kliknij pozycję **Wybierz dane.**

4. W **oknie dialogowym Wybieranie źródła** danych kliknij pole **Zakres danych wykresu** i wyczyść zaznaczenie domyślne.

5. W arkuszu **Dane** dla wykresu wybierz blok komórek zawierający liczby, w tym A4 w lewym górnym rogu do wartości E8 w prawym dolnym rogu.

6. W **oknie dialogowym Wybieranie źródła** danych kliknij przycisk **OK.**

7. Dostosuj położenie wykresu tak, aby prawy górny róg był wyrównany z **komórką E2**.

8. Zapisz plik na dysku C i nadaj jego **nazwęExcelChart.xlsx**.

9. Zamknij program Excel.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu
 W tym kroku utworzysz projekt skoroszytu programu Excel na podstawie **skoroszytu ExcelChart.**

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt skoroszytu programu Excel o nazwie **Mój wykres programu Excel.** W kreatorze wybierz pozycję **Kopiuj istniejący dokument.**

     Aby uzyskać więcej informacji, [zobacz How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Kliknij przycisk **Przeglądaj** i przejdź do skoroszytu utworzonego wcześniej w tym przewodniku.

3. Kliknij przycisk **OK**.

     Visual Studio nowy skoroszyt programu Excel w projektancie i dodaje projekt **Mój wykres programu Excel** do Eksplorator rozwiązań . 

## <a name="set-properties-of-the-chart"></a>Ustawianie właściwości wykresu
 Podczas tworzenia nowego projektu skoroszytu programu Excel, który korzysta z istniejącego skoroszytu, kontrolki hosta są automatycznie tworzone dla wszystkich nazwanych zakresów, obiektów listy i wykresów w skoroszycie. Nazwę kontrolki można zmienić <xref:Microsoft.Office.Tools.Excel.Chart> przy  użyciu okna Właściwości.

### <a name="to-change-the-name-of-the-chart-control"></a>Aby zmienić nazwę kontrolki Wykres

1. Wybierz <xref:Microsoft.Office.Tools.Excel.Chart> kontrolkę w projektancie i zmień następujące właściwości w **oknie** Właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**dataChart (wykres danych)**|
    |**HasLegend**|**False**|

## <a name="add-controls"></a>Dodawanie kontrolek
 Ten arkusz używa przycisków radiowych, aby dać użytkownikom sposób na szybką zmianę stylu wykresu. Przyciski radiowe muszą być jednak wyłączne — po wybraniu jednego przycisku nie można jednocześnie wybrać żadnego innego przycisku w grupie. To zachowanie nie występuje domyślnie w przypadku dodawania kilku przycisków radiowych do arkusza.

 Jednym ze sposobów dodania tego zachowania jest zgrupowanie przycisków radiowych w kontrolce użytkownika, napisanie kodu za kontrolką użytkownika, a następnie dodanie kontrolki użytkownika do arkusza.

### <a name="to-add-a-user-control"></a>Aby dodać kontrolkę użytkownika

1. Wybierz projekt **Mój wykres programu Excel** w **Eksplorator rozwiązań**.

2. W menu **Project (Projekt)** kliknij pozycję **Add New Item (Dodaj nowy element).**

3. W **oknie dialogowym Dodawanie nowego** elementu kliknij pozycję **Kontrola użytkownika,** nadaj **kontrolce nazwę ChartOptions, a** następnie kliknij przycisk **Dodaj**.

### <a name="to-add-radio-buttons-to-the-user-control"></a>Aby dodać przyciski radiowe do kontrolki użytkownika

1. Jeśli kontrolka użytkownika nie jest widoczna w projektancie, kliknij dwukrotnie pozycję **ChartOptions** w **Eksplorator rozwiązań**.

2. Na karcie **Typowe kontrolki** **przybornika** przeciągnij kontrolkę **Przycisk** radiowy do kontrolki użytkownika i zmień następujące właściwości.

   | Właściwość | Wartość |
   |----------|------------------|
   | **Nazwa** | **columnChart (wykres kolumnowy)** |
   | **Tekst** | **Wykres kolumnowy** |

3. Dodaj drugi przycisk radiowy do kontrolki użytkownika i zmień następujące właściwości.

   | Właściwość | Wartość |
   |----------|---------------|
   | **Nazwa** | **barChart (wykres słupkowy)** |
   | **Tekst** | **Wykres słupkowy** |

4. Dodaj trzeci przycisk radiowy do kontrolki użytkownika i zmień następujące właściwości.

   | Właściwość | Wartość |
   |----------|----------------|
   | **Nazwa** | **lineChart (wykres liniowy)** |
   | **Tekst** | **Wykres liniowy** |

5. Dodaj czwarty przycisk radiowy do kontrolki użytkownika i zmień następujące właściwości.

   |Właściwość|Wartość|
   |--------------|-----------|
   |**Nazwa**|**areaBlockChart (wykres obszarowy)**|
   |**Tekst**|**Wykres blokowy obszaru**|

   Następnie napisz kod aktualizujący wykres po kliknięciu przycisku radiowego.

## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>Zmienianie stylu wykresu po wybraniu przycisku radiowego
 Teraz możesz dodać kod, aby zmienić styl wykresu. W tym celu utwórz zdarzenie publiczne w kontrolce użytkownika, dodaj właściwość w celu ustawienia typu wyboru i utwórz program obsługi zdarzeń dla zdarzenia każdego z `CheckedChanged` przycisków radiowych.

### <a name="to-create-an-event-and-property-on-a-user-control"></a>Aby utworzyć zdarzenie i właściwość w kontrolce użytkownika

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy kontrolkę użytkownika, a następnie kliknij polecenie **Wyświetl kod.**

2. Dodaj kod do `ChartOptions` klasy , aby utworzyć zdarzenie i właściwość `SelectionChanged` `Selection` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb" id="Snippet13":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs" id="Snippet13":::

### <a name="to-handle-the-checkedchanged-event-of-the-radio-buttons"></a>Aby obsłużyć zdarzenie CheckedChanged przycisków radiowych

1. Ustaw typ wykresu w `CheckedChanged` programie obsługi zdarzeń `areaBlockChart` przycisku radiowego, a następnie podnieś zdarzenie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb" id="Snippet14":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs" id="Snippet14":::

2. Ustaw typ wykresu w `CheckedChanged` programie obsługi zdarzeń `barChart` przycisku radiowego.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb" id="Snippet15":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs" id="Snippet15":::

3. Ustaw typ wykresu w `CheckedChanged` programie obsługi zdarzeń `columnChart` przycisku radiowego.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb" id="Snippet16":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs" id="Snippet16":::

4. Ustaw typ wykresu w `CheckedChanged` programie obsługi zdarzeń `lineChart` przycisku radiowego.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb" id="Snippet17":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs" id="Snippet17":::

5. W języku C# należy dodać procedury obsługi zdarzeń dla przycisków radiowych. Możesz dodać kod do konstruktora `ChartOptions` poniżej wywołania . `InitializeComponent` Aby uzyskać informacje na temat tworzenia programów obsługi zdarzeń, zobacz [Jak tworzyć procedury obsługi zdarzeń w projektach pakietu Office.](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs" id="Snippet18":::

## <a name="add-the-user-control-to-the-worksheet"></a>Dodawanie kontrolki użytkownika do arkusza
 Podczas kompilowania rozwiązania nowa kontrolka użytkownika jest automatycznie dodawana do **przybornika**. Następnie możesz przeciągnąć kontrolkę z **przybornika** do arkusza.

### <a name="to-add-the-user-control-your-worksheet"></a>Aby dodać kontrolkę użytkownika do arkusza

1. W menu **Kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.

     Kontrolka **użytkownika ChartOptions** jest dodawana do **przybornika**.

2. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy **pozycję Sheet1.vb** lub **Sheet1.cs,** a następnie kliknij **Projektant widoków**.

3. Przeciągnij **kontrolkę ChartOptions** z **przybornika** do arkusza.

     Do projektu `my_Excel_Chart_ChartOptions1` zostanie dodana nowa kontrolka o nazwie .

4. Zmień nazwę kontrolki na **ChartOptions1.**

## <a name="change-the-chart-type"></a>Zmienianie typu wykresu
 Aby zmienić typ wykresu, utwórz program obsługi zdarzeń, który ustawia styl zgodnie z opcją wybraną w kontrolce użytkownika.

### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-worksheet"></a>Aby zmienić typ wykresu wyświetlanego w arkuszu

1. Dodaj następującą obsługę zdarzeń do `Sheet1` klasy .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet19":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet19":::

2. W języku C# musisz dodać program obsługi zdarzeń dla kontrolki użytkownika do <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> zdarzenia, jak pokazano poniżej. Aby uzyskać informacje na temat tworzenia programów obsługi zdarzeń, zobacz [Jak tworzyć procedury obsługi zdarzeń w projektach pakietu Office.](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet20":::

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz możesz przetestować skoroszyt, aby sprawdzić, czy wykres ma prawidłowy styl po wybraniu przycisku radiowego.

### <a name="to-test-your-workbook"></a>Aby przetestować skoroszyt

1. Naciśnij **klawisz F5,** aby uruchomić projekt.

2. Wybierz różne przyciski radiowe.

3. Upewnij się, że styl wykresu zmienia się w celu dopasowania do zaznaczenia.

## <a name="next-steps"></a>Następne kroki
 W tym przewodniku przedstawiono podstawy używania przycisków radiowych i stylów wykresu w arkuszach. Oto kilka zadań, które mogą się pojawić w następnej części:

- Wdrażanie projektu. Aby uzyskać więcej informacji, zobacz [Wdrażanie rozwiązania pakietu Office.](../vsto/deploying-an-office-solution.md)

- Wypełnianie pola tekstowego za pomocą przycisku. Aby uzyskać więcej informacji, zobacz Przewodnik: wyświetlanie tekstu w polu tekstowym w [arkuszu przy użyciu przycisku](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).

- Zmień formatowanie arkusza przy użyciu pól wyboru. Aby uzyskać więcej informacji, zobacz [Przewodnik: zmienianie formatowania arkusza przy użyciu kontrolek CheckBox.](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)

## <a name="see-also"></a>Zobacz też
- [Wskazówki dotyczące korzystania z programu Excel](../vsto/walkthroughs-using-excel.md)
