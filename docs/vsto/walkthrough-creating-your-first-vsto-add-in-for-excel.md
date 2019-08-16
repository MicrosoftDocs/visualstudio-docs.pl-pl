---
title: 'Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Excel'
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Excel [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 52b683b1f75f2967807f171c204fbf02a2e5db69
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69548019"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-excel"></a>Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Excel
  W tym instruktażu wprowadzającym pokazano, jak utworzyć dodatek na poziomie aplikacji dla programu Microsoft Office Excel. Funkcje, które tworzysz w tym rodzaju rozwiązanie, są dostępne dla samej aplikacji, niezależnie od tego, które skoroszyty są otwarte.

 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie projektu dodatku VSTO dla programu Excel dla programu Excel.

- Pisanie kodu, który używa modelu obiektów programu Excel do dodawania tekstu do skoroszytu po jego zapisaniu.

- Kompilowanie i uruchamianie projektu w celu jego przetestowania.

- Czyszczenie ukończonego projektu, aby dodatek VSTO nie był już automatycznie uruchamiany na komputerze deweloperskim.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)]lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Utwórz projekt

#### <a name="to-create-a-new-excel-vsto-add-in-project-in-visual-studio"></a>Aby utworzyć nowy projekt dodatku narzędzi VSTO dla programu Excel w programie Visual Studio

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.

3. W okienku szablony rozwiń pozycję **Wizualizacja C#**  lub **Visual Basic**, a następnie rozwiń węzeł **Office/SharePoint**.

4. W rozwiniętym węźle **Office/SharePoint** wybierz węzeł **Dodatki pakietu Office** .

5. Na liście szablonów projektu wybierz dodatek **excel 2010** , dodatek do programu Excel **2013**.

6. W polu **Nazwa** wpisz **FirstExcelAddIn**.

7. Kliknij przycisk **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]tworzy projekt **FirstExcelAddIn** i otwiera plik kodu ThisAddIn w edytorze.

## <a name="write-code-to-add-text-to-the-saved-workbook"></a>Napisz kod, aby dodać tekst do zapisanego skoroszytu
 Następnie Dodaj kod do pliku kodu ThisAddIn. Nowy kod używa modelu obiektów programu Excel do wstawiania tekstu standardowego w pierwszym wierszu aktywnego arkusza. Aktywny arkusz jest arkuszem otwartym, gdy użytkownik zapisuje skoroszyt. Domyślnie plik kodu ThisAddIn zawiera następujący wygenerowany kod:

- Częściowa definicja `ThisAddIn` klasy. Ta klasa udostępnia punkt wejścia dla kodu i zapewnia dostęp do modelu obiektów programu Excel. Aby uzyskać więcej informacji, zobacz [dodatki narzędzi VSTO dla programu](../vsto/programming-vsto-add-ins.md). Pozostała część `ThisAddIn` klasy jest zdefiniowana w ukrytym pliku kodu, który nie powinien być modyfikowany.

- Programy obsługi `ThisAddIn_Shutdown` zdarzeń i.`ThisAddIn_Startup` Te programy obsługi zdarzeń są wywoływane, gdy program Excel ładuje i zwalnia dodatek narzędzi VSTO. Te programy obsługi zdarzeń umożliwiają zainicjowanie dodatku VSTO podczas jego ładowania oraz oczyszczenie zasobów używanych przez dodatek po jego zwolnieniu. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).

### <a name="to-add-a-line-of-text-to-the-saved-workbook"></a>Aby dodać wiersz tekstu do zapisanego skoroszytu

1. W pliku kodu ThisAddIn Dodaj następujący kod do `ThisAddIn` klasy. Nowy kod definiuje procedurę obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> zdarzenia, które jest zgłaszane, gdy skoroszyt zostanie zapisany.

    Gdy użytkownik zapisuje skoroszyt, program obsługi zdarzeń dodaje nowy tekst na początku aktywnego arkusza.

    [!code-vb[Trin_ExcelAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_ExcelAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs#1)]

2. Jeśli używasz C#programu, Dodaj następujący kod wymagany do `ThisAddIn_Startup` programu obsługi zdarzeń. Ten kod służy do łączenia `Application_WorkbookBeforeSave` programu obsługi zdarzeń <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> ze zdarzeniem.

    [!code-csharp[Trin_ExcelAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs#2)]

   Aby zmodyfikować skoroszyt po jego zapisaniu, poprzednie przykłady kodu używają następujących obiektów:

- `Application` Pole`ThisAddIn` klasy. `Application` Pole<xref:Microsoft.Office.Interop.Excel.Application> zwraca obiekt, który reprezentuje bieżące wystąpienie programu Excel.

- Parametr programu obsługi zdarzeń <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> dla zdarzenia. `Wb` `Wb` Parametr<xref:Microsoft.Office.Interop.Excel.Workbook> jest obiektem, który reprezentuje zapisany skoroszyt. Aby uzyskać więcej informacji, zobacz [model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md).

## <a name="test-the-project"></a>Testowanie projektu

### <a name="to-test-the-project"></a>Aby przetestować projekt

1. Naciśnij klawisz **F5** , aby skompilować i uruchomić projekt.

     Podczas kompilowania projektu, kod jest kompilowany do zestawu, który jest dołączony do folderu danych wyjściowych kompilacji dla projektu. Program Visual Studio tworzy również zestaw wpisów rejestru, które umożliwiają programowi Excel odnajdywanie i ładowanie dodatku VSTO oraz Konfigurowanie ustawień zabezpieczeń na komputerze deweloperskim, aby umożliwić uruchomienie dodatku VSTO. Aby uzyskać więcej informacji, zobacz [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md).

2. W programie Excel Zapisz skoroszyt.

3. Sprawdź, czy do skoroszytu został dodany następujący tekst.

     **Ten tekst został dodany za pomocą kodu.**

4. Zamknij program Excel.

## <a name="clean-up-the-project"></a>Wyczyść projekt
 Po zakończeniu opracowywania projektu, Usuń zestaw dodatków VSTO, wpisy rejestru i ustawienia zabezpieczeń z komputera deweloperskiego. W przeciwnym razie dodatek narzędzi VSTO będzie nadal uruchamiany za każdym razem, gdy otworzysz program Excel na komputerze deweloperskim.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Aby wyczyścić ukończony projekt na komputerze deweloperskim

1. W programie Visual Studio w menu **kompilacja** kliknij pozycję **czyste rozwiązanie**.

## <a name="next-steps"></a>Następne kroki
 Po utworzeniu podstawowego dodatku narzędzi VSTO dla programu Excel można dowiedzieć się więcej na temat opracowywania dodatków VSTO z następujących tematów:

- Ogólne zadania programistyczne, które można wykonywać w dodatkach narzędzia VSTO: [Dodatki narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md)

- Zadania programistyczne specyficzne dla dodatków narzędzi VSTO programu Excel: [Rozwiązania programu Excel](../vsto/excel-solutions.md).

- Korzystanie z modelu obiektów programu Excel: [Model obiektów programu Excel — Omówienie](../vsto/excel-object-model-overview.md).

- Dostosowanie interfejsu użytkownika (UI) programu Excel, na przykład przez dodanie karty niestandardowej do wstążki lub utworzenie własnego niestandardowego okienka zadań: [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).

- Kompilowanie i debugowanie dodatków narzędzi VSTO dla programu Excel: [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md).

- Wdrażanie dodatków narzędzi VSTO dla programu Excel: [Wdróż rozwiązanie pakietu Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Zobacz także
- [Programowanie rozwiązań pakietu Office &#40;— Omówienie&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Rozwiązania programu Excel](../vsto/excel-solutions.md)
- [Dodatki narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md)
- [Model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)
- [Wdróż rozwiązanie pakietu Office](../vsto/deploying-an-office-solution.md)
- [Szablony projektów pakietu Office — omówienie](../vsto/office-project-templates-overview.md)
