---
title: 'Przewodnik: Zbieranie danych za pomocą formularza Windows'
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 11e9b73671a8c4b03c33169739ea8fd02b486568
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53926636"
---
# <a name="walkthrough-collect-data-by-using-a-windows-form"></a>Przewodnik: Zbieranie danych przy użyciu formularza Windows
  W tym instruktażu pokazano, jak otworzyć formularz Windows z dostosowywania poziomie dokumentu dla programu Microsoft Office Excel, zbiera informacje o użytkowniku i zapisanie tych informacji w komórce arkusza.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Chociaż w tym instruktażu wykorzystano specjalnie projektem na poziomie dokumentu dla programu Excel, koncepcje dowodzą Instruktaż mają zastosowanie do innych projektów pakietu Office.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="create-a-new-project"></a>Tworzenie nowego projektu  
 Pierwszym krokiem jest utworzenie projektu skoroszytu programu Excel.  
  
### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1.  Utwórz projektu skoroszytu programu Excel o nazwie **WinFormInput**i wybierz **Utwórz nowy dokument** w kreatorze. Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio zostanie otwarty nowy skoroszyt programu Excel w Projektancie i dodaje **WinFormInput** projekt **Eksploratora rozwiązań**.  
  
## <a name="add-a-namedrange-control-to-the-worksheet"></a>Dodaj kontrolkę NamedRange do arkusza  
  
### <a name="to-add-a-named-range-to-sheet1"></a>Aby dodać nazwany zakres do Arkusz1  
  
1.  Zaznacz komórkę **A1** na `Sheet1`.  
  
2.  W **nazwa** wpisz **formInput**.  
  
     **Nazwa** pole znajduje się po lewej stronie paska formuły, tuż nad kolumny **A** arkusza.  
  
3.  Naciśnij klawisz **wprowadź**.  
  
     A <xref:Microsoft.Office.Tools.Excel.NamedRange> formant jest dodawany do komórki **A1**. Nie ma żadnego wskazania widoczne w arkuszu, ale **formInput** pojawia się w **nazwa** pole (tuż nad arkusz po lewej stronie) i w **właściwości** okna po komórka **A1** jest zaznaczone.  
  
## <a name="add-a-windows-form-to-the-project"></a>Dodaj formularz Windows do projektu  
 Tworzenie formularza Windows na monitowanie użytkownika o informacje.  
  
### <a name="to-add-a-windows-form"></a>Aby dodać formularz Windows  
  
1. Wybierz projekt **WinFormInput** w **Eksploratora rozwiązań**.  
  
2. Na **projektu** menu, kliknij przycisk **Dodaj formularz Windows**.  
  
3. Nazwa formularza **GetInputString.vb** lub **GetInputString.cs**, a następnie kliknij przycisk **Dodaj**.  
  
    Nowy formularz zostanie otwarty w projektancie.  
  
4. Dodaj <xref:System.Windows.Forms.TextBox> i <xref:System.Windows.Forms.Button> do formularza.  
  
5. Wybierz przycisk, znaleźć właściwości **tekstu** w **właściwości** okna i zmień tekst, który ma **OK**.  
  
   Następnie dodaj kod, aby `ThisWorkbook.vb` lub `ThisWorkbook.cs` umożliwiają zebranie informacji dotyczących użytkownika.  
  
## <a name="display-the-windows-form-and-collecting-information"></a>Wyświetl formularz Windows i używana do zbierania informacji  
 Utwórz wystąpienie obiektu `GetInputString` formularza Windows i wyświetlenia go, a następnie wpisz informacje o użytkowniku do komórki w arkuszu.  
  
#### <a name="to-display-the-form-and-collect-information"></a>Formularz wyświetlania i zbierać informacje  
  
1. Kliknij prawym przyciskiem myszy **ThisWorkbook.vb** lub **ThisWorkbook.cs** w **Eksploratora rozwiązań**, a następnie kliknij przycisk **Wyświetl kod**.  
  
2. W <xref:Microsoft.Office.Tools.Excel.Workbook.Open> program obsługi zdarzeń `ThisWorkbook`, Dodaj następujący kod, aby zadeklarować zmienną formularza `GetInputString` i wyświetlić formularz.  
  
   > [!NOTE]  
   >  W języku C#, należy dodać program obsługi zdarzeń, jak pokazano na <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> poniższe zdarzenie. Aby dowiedzieć się, jak tworzenie procedur obsługi zdarzeń, zobacz [jak: Tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
    [!code-csharp[Trin_VstcoreProgrammingCollectingData#1](../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs#1)]
    [!code-vb[Trin_VstcoreProgrammingCollectingData#1](../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb#1)]  
  
3. Utwórz metodę o nazwie `WriteStringToCell` , zapisuje tekst z nazwanym zakresem. Ta metoda jest wywoływana z formularza i danych wejściowych użytkownika jest przekazywany do <xref:Microsoft.Office.Tools.Excel.NamedRange> kontroli `formInput`, w komórce **A1**.  
  
    [!code-csharp[Trin_VstcoreProgrammingCollectingData#2](../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs#2)]
    [!code-vb[Trin_VstcoreProgrammingCollectingData#2](../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb#2)]  
  
   Następnie dodaj kod do formularza w celu obsługi kliknięcia przycisku zdarzeń.  
  
## <a name="send-information-to-the-worksheet"></a>Wysyłanie informacji do arkusza  
  
### <a name="to-send-information-to-the-worksheet"></a>Do wysyłania informacji do arkusza  
  
1.  Kliknij prawym przyciskiem myszy **GetInputString** w **Eksploratora rozwiązań**, a następnie kliknij przycisk **Projektant widoków**.  
  
2.  Kliknij dwukrotnie przycisk aby otworzyć plik kodu przy użyciu przycisku <xref:System.Windows.Forms.Control.Click> dodać program obsługi zdarzeń.  
  
3.  Dodaj kod do narzędzia obsługi zdarzeń, aby pobrać dane wejściowe z pola tekstowego, przesłać ją do funkcji `WriteStringToCell`, a następnie zamknij formularz.  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#3](../vsto/codesnippet/CSharp/WinFormInputCS/GetInputString.cs#3)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#3](../vsto/codesnippet/VisualBasic/WinFormInput/GetInputString.vb#3)]  
  
## <a name="test"></a>Test  
 Możesz teraz uruchomić projekt. Zostanie wyświetlony formularz Windows, a dane wejściowe pojawia się w arkuszu.  
  
### <a name="to-test-your-workbook"></a>Aby przetestować skoroszytu  
  
1.  Naciśnij klawisz **F5** Aby uruchomić projekt.  
  
2.  Upewnij się, że zostanie wyświetlony formularz Windows.  
  
3.  Typ **Witaj, świecie** w polu tekstowym, a następnie kliknij przycisk **OK**.  
  
4.  Upewnij się, że **Witaj, świecie** jest wyświetlana w komórce **A1** arkusza.  
  
## <a name="next-steps"></a>Następne kroki  
 W tym instruktażu przedstawiono podstawowe informacje dotyczące przedstawiająca formularz Windows i przekazywanie danych do arkusza. Inne zadania, które chcesz wykonać obejmują:  
  
-   Formanty Windows Forms w skoroszycie programu Excel lub dokumentu programu Word. Aby uzyskać więcej informacji, zobacz [kontrolek formularzy Windows w przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
-   Zmodyfikuj interfejsu użytkownika aplikacji z dostosowywania poziomie dokumentu lub dodatku narzędzi VSTO dla pakietu Microsoft Office. Aby uzyskać więcej informacji, zobacz [dostosowywania interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Opracowywania rozwiązań pakietu Office](../vsto/developing-office-solutions.md)   
 [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)   
 [Program dodatków narzędzi VSTO](../vsto/programming-vsto-add-ins.md)   
 [Program dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)   
 [Wskazówki dotyczące przy użyciu programu Word](../vsto/walkthroughs-using-word.md)   
 [Wskazówki dotyczące za pomocą programu Excel](../vsto/walkthroughs-using-excel.md)  
