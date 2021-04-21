---
title: 'Przewodnik: zbieranie danych przy użyciu formularza systemu Windows'
description: Otwórz formularz systemu Windows z poziomu dostosowania na poziomie dokumentu dla programu Microsoft Excel, zbierz informacje od użytkownika i zapisz te informacje w komórce arkusza.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], Windows Forms
- Windows Forms [Office development in Visual Studio], collecting data
- forms [Office development in Visual Studio], walkthroughs
- worksheets [Office development in Visual Studio], collecting data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 62a49919522c5d4a88b6f4b6876b567c8d275dec
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826424"
---
# <a name="walkthrough-collect-data-by-using-a-windows-form"></a>Przewodnik: zbieranie danych przy użyciu formularza systemu Windows
  W tym przewodniku pokazano, jak otworzyć formularz systemu Windows z dostosowania na poziomie dokumentu dla programu Microsoft Office Excel, zebrać informacje od użytkownika i zapisać te informacje w komórce arkusza.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Mimo że w tym przewodniku jest używany projekt na poziomie dokumentu dla programu Excel, koncepcje demonstrowane w tym przewodniku mają zastosowanie do innych projektów pakietu Office.

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [Personalizowanie środowiska IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="create-a-new-project"></a>Tworzenie nowego projektu
 Pierwszym krokiem jest utworzenie projektu skoroszytu programu Excel.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt skoroszytu programu Excel o nazwie **WinFormInput** i wybierz pozycję **Utwórz nowy dokument** w kreatorze. Aby uzyskać więcej informacji, [zobacz Jak tworzyć projekty pakietu Office w programie Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio nowy skoroszyt programu Excel w projektancie i dodaje projekt **WinFormInput** do **Eksplorator rozwiązań**.

## <a name="add-a-namedrange-control-to-the-worksheet"></a>Dodawanie kontrolki NamedRange do arkusza

### <a name="to-add-a-named-range-to-sheet1"></a>Aby dodać nazwany zakres do arkusza Sheet1

1. Wybierz **komórkę A1 na** `Sheet1` stronie .

2. W polu **Nazwa** wpisz **formInput**.

     Pole **Nazwa** znajduje się z lewej strony paska formuły, tuż nad kolumną **A** arkusza.

3.  Naciśnij klawisz **Enter**.

     Kontrolka <xref:Microsoft.Office.Tools.Excel.NamedRange> jest dodawana do komórki **A1**. W arkuszu nie ma widocznego wskazania, ale  element **formInput** pojawia się w polu Nazwa  (tuż nad arkuszem po lewej stronie) i w oknie Właściwości, gdy komórka **A1** jest zaznaczona.

## <a name="add-a-windows-form-to-the-project"></a>Dodawanie formularza systemu Windows do projektu
 Utwórz formularz systemu Windows, aby monitować użytkownika o informacje.

### <a name="to-add-a-windows-form"></a>Aby dodać formularz systemu Windows

1. Wybierz projekt **WinFormInput w** **Eksplorator rozwiązań**.

2. W menu **Project (Projekt)** kliknij pozycję **Add Windows Form (Dodaj formularz systemu Windows).**

3. Nadaj **formularzowi nazwę GetInputString.vb** lub **GetInputString.cs,** a następnie kliknij przycisk **Dodaj**.

    Nowy formularz zostanie otwarty w projektancie.

4. Dodaj do <xref:System.Windows.Forms.TextBox> <xref:System.Windows.Forms.Button> formularza i .

5. Wybierz przycisk , znajdź właściwość **Text** w oknie **Właściwości** i zmień tekst na **OK.**

   Następnie dodaj kod do `ThisWorkbook.vb` lub , aby zebrać informacje o `ThisWorkbook.cs` użytkowniku.

## <a name="display-the-windows-form-and-collecting-information"></a>Wyświetlanie formularza systemu Windows i zbieranie informacji
 Utwórz wystąpienie formularza systemu Windows i wyświetl go, a następnie zapisz informacje o użytkowniku `GetInputString` w komórce w arkuszu.

#### <a name="to-display-the-form-and-collect-information"></a>Aby wyświetlić formularz i zebrać informacje

1. Kliknij prawym przyciskiem myszy **pozycję ThisWorkbook.vb** lub **ThisWorkbook.cs** w Eksplorator rozwiązań **,** a następnie kliknij polecenie Wyświetl **kod.**

2. W programie obsługi zdarzeń dodaj następujący kod, aby zadeklarować zmienną dla <xref:Microsoft.Office.Tools.Excel.Workbook.Open> `ThisWorkbook` formularza, a `GetInputString` następnie wyświetlić formularz.

   > [!NOTE]
   > W języku C# należy dodać program obsługi zdarzeń, jak pokazano w poniższym <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> zdarzeniu. Aby uzyskać informacje na temat tworzenia programów obsługi zdarzeń, zobacz [Jak tworzyć procedury obsługi zdarzeń w projektach pakietu Office.](../vsto/how-to-create-event-handlers-in-office-projects.md)

    :::code language="csharp" source="../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs" id="Snippet1":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb" id="Snippet1":::

3. Utwórz metodę o `WriteStringToCell` nazwie , która zapisuje tekst do nazwanego zakresu. Ta metoda jest wywoływana z formularza, a dane wejściowe użytkownika są przekazywane do kontrolki <xref:Microsoft.Office.Tools.Excel.NamedRange> `formInput` , w komórce **A1**.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs" id="Snippet2":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb" id="Snippet2":::

   Następnie dodaj kod do formularza w celu obsługi zdarzenia kliknięcia przycisku.

## <a name="send-information-to-the-worksheet"></a>Wysyłanie informacji do arkusza

### <a name="to-send-information-to-the-worksheet"></a>Aby wysłać informacje do arkusza

1. Kliknij prawym przyciskiem **myszy pozycję GetInputString** **w Eksplorator rozwiązań**, a następnie kliknij **Projektant widoków**.

2. Kliknij dwukrotnie przycisk, aby otworzyć plik kodu z dodanym programem <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń przycisku.

3. Dodaj kod do procedury obsługi zdarzeń, aby wprowadzić dane wejściowe z pola tekstowego, wysłać go do funkcji `WriteStringToCell` , a następnie zamknąć formularz.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/WinFormInputCS/GetInputString.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/WinFormInput/GetInputString.vb" id="Snippet3":::

## <a name="test"></a>Testowanie
 Teraz możesz uruchomić projekt. Zostanie wyświetlony formularz systemu Windows, a dane wejściowe będą wyświetlane w arkuszu.

### <a name="to-test-your-workbook"></a>Aby przetestować skoroszyt

1. Naciśnij **klawisz F5,** aby uruchomić projekt.

2. Upewnij się, że zostanie wyświetlony formularz systemu Windows.

3. Wpisz **Hello world** w polu tekstowym, a następnie kliknij przycisk **OK.**

4. Upewnij **się Hello world** że Hello world w **komórce A1** arkusza.

## <a name="next-steps"></a>Następne kroki
 W tym przewodniku przedstawiono podstawy wyświetlania formularza systemu Windows i przekazywania danych do arkusza. Inne zadania, które możesz chcieć wykonać, to:

- Używanie Windows Forms kontrolek w skoroszycie programu Excel lub dokumencie programu Word. Aby uzyskać więcej informacji, zobacz [Windows Forms kontroli w dokumentach pakietu Office — omówienie.](../vsto/windows-forms-controls-on-office-documents-overview.md)

- Zmodyfikuj interfejs użytkownika aplikacji Microsoft Office dostosowania na poziomie dokumentu lub dodatku VSTO. Aby uzyskać więcej informacji, zobacz [Dostosowywanie interfejsu użytkownika pakietu Office.](../vsto/office-ui-customization.md)

## <a name="see-also"></a>Zobacz też
- [Opracowywanie rozwiązań pakietu Office](../vsto/developing-office-solutions.md)
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
- [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md)
- [Zaprogramowanie dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)
- [Wskazówki dotyczące korzystania z programu Word](../vsto/walkthroughs-using-word.md)
- [Wskazówki dotyczące korzystania z programu Excel](../vsto/walkthroughs-using-excel.md)
