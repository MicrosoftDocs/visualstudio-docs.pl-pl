---
title: 'Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Excel'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Excel [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f803db23d868aa553ef4c1cd898428b64e998c3b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53831891"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-excel"></a>Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Excel
  Ten Przewodnik wprowadzający dowiesz się, jak utworzyć dodatek poziomu aplikacji dla programu Microsoft Office Excel. Funkcje, które tworzysz w tego rodzaju rozwiązania są dostępne dla aplikacji, niezależnie od tego, które są otwarte skoroszyty.  
  
 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
- Tworzenie projektu dodatku narzędzi VSTO programu Excel dla programu Excel.  
  
- Pisanie kodu, który używa modelu obiektów programu Excel Aby dodać tekst w skoroszycie, podczas zapisywania.  
  
- Tworzenie i uruchamianie projektu, aby ją przetestować.  
  
- Czyszczenie zakończone projektu tak, aby dodatku narzędzi VSTO już nie uruchamia automatycznie na komputerze deweloperskim.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="create-the-project"></a>Utwórz projekt  
  
#### <a name="to-create-a-new-excel-vsto-add-in-project-in-visual-studio"></a>Aby utworzyć nowy projekt dodatku narzędzi VSTO programu Excel w programie Visual Studio  
  
1.  Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.  
  
3.  W okienku szablonów, rozwiń **Visual C#** lub **języka Visual Basic**, a następnie rozwiń węzeł **Office/SharePoint**.  
  
4.  W rozwiniętym okienku **Office/SharePoint** węzeł **dodatków pakietu Office** węzła.  
  
5.  Na liście szablonów projektu wybierz **programu Excel 2010 dodatków** lub **Excel 2013 dodatków**.  
  
6.  W **nazwa** wpisz **FirstExcelAddIn**.  
  
7.  Kliknij przycisk **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tworzy **FirstExcelAddIn** projektu i otwiera plik kodu ThisAddIn w edytorze.  
  
## <a name="write-code-to-add-text-to-the-saved-workbook"></a>Pisanie kodu, aby dodać tekst zapisany skoroszyt  
 Następnie dodaj kod, aby plik kodu ThisAddIn. Nowy kod używa modelu obiektów programu Excel, aby wstawić standardowy tekst w pierwszym wierszu aktywnego arkusza. Aktywny arkusz jest arkusza, która jest otwarta, gdy użytkownik zapisuje skoroszyt. Domyślnie plik kodu ThisAddIn zawiera następujące wygenerowanego kodu:  
  
-   Częściową definicję `ThisAddIn` klasy. Ta klasa udostępnia punkt wejścia dla kodu i zapewnia dostęp do modelu obiektów programu Excel. Aby uzyskać więcej informacji, zobacz [dodatków narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md). W pozostałej części `ThisAddIn` klasa jest zdefiniowana w pliku ukryty kod, który nie należy modyfikować.  
  
-   `ThisAddIn_Startup` i `ThisAddIn_Shutdown` procedury obsługi zdarzeń. Te procedury obsługi zdarzeń są wywoływane, gdy program Excel ładuje i zwalnia dodatku narzędzi VSTO dla programów. Użyj tych programów obsługi zdarzeń, można zainicjować dodatku narzędzi VSTO dla programów, podczas jego ładowania oraz aby wyczyścić zasoby używane przez dodatek programu, gdy jest zwolniony. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).  
  
### <a name="to-add-a-line-of-text-to-the-saved-workbook"></a>Aby dodać wiersz tekstu do zapisanego skoroszytu  
  
1. W pliku kodu ThisAddIn, Dodaj następujący kod do `ThisAddIn` klasy. Nowy kod definiuje zdarzenia obsługi dla <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> zdarzenie, które jest wywoływane, gdy skoroszyt jest zapisywany.  
  
    Gdy użytkownik zapisuje skoroszyt, program obsługi zdarzeń dodaje nowy tekst na początku aktywnego arkusza.  
  
    [!code-vb[Trin_ExcelAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_ExcelAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs#1)]  
  
2. Jeśli używasz języka C#, Dodaj następujący kod wymagany do `ThisAddIn_Startup` programu obsługi zdarzeń. Ten kod służy do łączenia `Application_WorkbookBeforeSave` programu obsługi zdarzeń z <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> zdarzeń.  
  
    [!code-csharp[Trin_ExcelAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs#2)]  
  
   Aby zmodyfikować skoroszytu, po zapisaniu go, w poprzednich przykładach kodu za pomocą następujących obiektów:  
  
-   `Application` Pole `ThisAddIn` klasy. `Application` Pole zwraca <xref:Microsoft.Office.Interop.Excel.Application> reprezentujący bieżące wystąpienie programu Excel.  
  
-   `Wb` Parametrów programu obsługi zdarzeń <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> zdarzeń. `Wb` Parametr <xref:Microsoft.Office.Interop.Excel.Workbook> obiektu, który reprezentuje zapisany skoroszyt. Aby uzyskać więcej informacji, zobacz [model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md).  
  
## <a name="test-the-project"></a>Projekt testowy  
  
### <a name="to-test-the-project"></a>Aby przetestować projekt  
  
1.  Naciśnij klawisz **F5** Aby skompilować i uruchomić projekt.  
  
     Gdy tworzysz projekt, kod jest kompilowany do zestawu, który znajduje się w folderze wyjściowym kompilacji dla projektu. Visual Studio tworzy również zestaw wpisów rejestru, umożliwiające wykrycie i załadowanie dodatku narzędzi VSTO dla programów Excel i konfiguruje ustawienia zabezpieczeń na komputerze deweloperskim, aby włączyć dodatek narzędzi VSTO dla programów do uruchomienia. Aby uzyskać więcej informacji, zobacz [rozwiązań kompilacji pakietu Office](../vsto/building-office-solutions.md).  
  
2.  W programie Excel Zapisz skoroszyt.  
  
3.  Sprawdź, czy następujący tekst został dodany do skoroszytu.  
  
     **Ten tekst został dodany przy użyciu kodu.**  
  
4.  Zamknij program Excel.  
  
## <a name="clean-up-the-project"></a>Czyszczenie projektu  
 Po zakończeniu tworzenia projektu dodatku narzędzi VSTO zestaw, wpisy rejestru i ustawienia zabezpieczeń należy usunąć z komputera dewelopera. W przeciwnym razie dodatku narzędzi VSTO będzie kontynuował pracę każdym razem, gdy po otwarciu programu Excel na komputerze deweloperskim.  
  
### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Aby wyczyścić ukończone projektu na komputerze deweloperskim  
  
1.  W programie Visual Studio na **kompilacji** menu, kliknij przycisk **czyste rozwiązanie**.  
  
## <a name="next-steps"></a>Następne kroki  
 Teraz, gdy utworzono podstawowe dodatku narzędzi VSTO dla programu Excel, można dowiedzieć się więcej o tworzeniu dodatków narzędzi VSTO dla programów w tych tematach:  
  
-   Ogólne zadań programistycznych, które można wykonywać w dodatkach VSTO: [Program dodatków narzędzi VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Zadania programowania, które są specyficzne dla dodatków narzędzi VSTO programu Excel: [Rozwiązania w programie Excel](../vsto/excel-solutions.md).  
  
-   Za pomocą modelu obiektów programu Excel: [Model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md).  
  
-   Dostosowywanie interfejsu użytkownika (UI) programu Excel, na przykład przez dodawanie kart niestandardowych do Wstążki lub tworzenia własnego niestandardowego okienka zadań: [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).  
  
-   Kompilowanie i debugowanie dodatków narzędzi VSTO dla programu Excel: [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md).  
  
-   Wdrażanie dodatków narzędzi VSTO dla programu Excel: [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Rozwiązania programu Excel](../vsto/excel-solutions.md)   
 [Program dodatków narzędzi VSTO](../vsto/programming-vsto-add-ins.md)   
 [Model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md)   
 [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)   
 [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)   
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)   
 [Omówienie szablonów projektu pakietu Office](../vsto/office-project-templates-overview.md)  
