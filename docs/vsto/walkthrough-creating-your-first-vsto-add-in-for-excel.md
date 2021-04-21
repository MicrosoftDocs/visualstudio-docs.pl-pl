---
title: 'Przewodnik: tworzenie pierwszego dodatku VSTO dla programu Excel'
description: Utwórz dodatek na poziomie aplikacji dla programu Microsoft Excel. Funkcje, które tworzysz, są dostępne dla samej aplikacji, niezależnie od tego, które skoroszyty są otwarte.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fcb2bcc91eb1d19309904caae16701b814113089
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824409"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-excel"></a>Przewodnik: tworzenie pierwszego dodatku VSTO dla programu Excel
  W tym przewodniku wprowadzającym pokazano, jak utworzyć dodatek na poziomie aplikacji dla programu Microsoft Office Excel. Funkcje, które tworzysz w tego typu rozwiązaniu, są dostępne dla samej aplikacji, niezależnie od tego, które skoroszyty są otwarte.

 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie projektu dodatku VSTO programu Excel dla programu Excel.

- Pisanie kodu, który używa modelu obiektów programu Excel do dodawania tekstu do skoroszytu po jego zapisaniu.

- Budowania i uruchamiania projektu w celu przetestowania go.

- Czyszczenie ukończonego projektu tak, aby dodatek VSTO nie był już automatycznie uruchamiany na komputerze dewelopera.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Tworzenie projektu

#### <a name="to-create-a-new-excel-vsto-add-in-project-in-visual-studio"></a>Aby utworzyć nowy projekt dodatku VSTO programu Excel w programie Visual Studio

1. Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. W menu **File (Plik)** wskaż pozycję **New (Nowy),** a następnie kliknij pozycję **Project (Projekt).**

3. W okienku szablonów rozwiń pozycję **Visual C#** **lub Visual Basic**, a następnie rozwiń pozycję **Office/SharePoint.**

4. W rozwiniętym **węźle Office/SharePoint** wybierz węzeł **Dodatki pakietu Office.**

5. Na liście szablonów projektów wybierz pozycję Dodatek programu **Excel 2010** lub Dodatek programu **Excel 2013.**

6. W polu **Nazwa** wpisz **FirstExcelAddIn**.

7. Kliknij przycisk **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tworzy projekt **FirstExcelAddIn** i otwiera plik kodu ThisAddIn w edytorze.

## <a name="write-code-to-add-text-to-the-saved-workbook"></a>Pisanie kodu w celu dodania tekstu do zapisanego skoroszytu
 Następnie dodaj kod do pliku kodu ThisAddIn. Nowy kod używa modelu obiektów programu Excel do wstawiania tekstu wzorcowego w pierwszym wierszu aktywnego arkusza. Aktywny arkusz to arkusz, który jest otwarty, gdy użytkownik zapisze skoroszyt. Domyślnie plik kodu ThisAddIn zawiera następujący wygenerowany kod:

- Częściowa definicja `ThisAddIn` klasy. Ta klasa zapewnia punkt wejścia dla kodu i zapewnia dostęp do modelu obiektów programu Excel. Aby uzyskać więcej informacji, zobacz [Program VSTO Add-ins (Dodatki programu VSTO).](../vsto/programming-vsto-add-ins.md) Pozostała część klasy `ThisAddIn` jest zdefiniowana w ukrytym pliku kodu, który nie powinien być modyfikowany.

- Programy `ThisAddIn_Startup` `ThisAddIn_Shutdown` obsługi zdarzeń i . Te procedury obsługi zdarzeń są wywoływane, gdy program Excel ładuje i zwalnia dodatek VSTO. Użyj tych programów obsługi zdarzeń, aby zainicjować dodatek VSTO podczas ładowania i wyczyścić zasoby używane przez dodatek, gdy zostanie zwolniony. Aby uzyskać więcej informacji, zobacz [Zdarzenia w projektach pakietu Office.](../vsto/events-in-office-projects.md)

### <a name="to-add-a-line-of-text-to-the-saved-workbook"></a>Aby dodać wiersz tekstu do zapisanego skoroszytu

1. W pliku kodu ThisAddIn dodaj następujący kod do `ThisAddIn` klasy . Nowy kod definiuje program obsługi zdarzeń dla zdarzenia, który jest <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> wywoływany podczas zapisania skoroszytu.

    Gdy użytkownik zapisze skoroszyt, program obsługi zdarzeń doda nowy tekst na początku aktywnego arkusza.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ExcelAddInTutorial/ThisAddIn.vb" id="Snippet1":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs" id="Snippet1":::

2. Jeśli używasz języka C#, dodaj następujący wymagany kod do procedury `ThisAddIn_Startup` obsługi zdarzeń. Ten kod jest używany do łączenia programu `Application_WorkbookBeforeSave` obsługi zdarzeń ze <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> zdarzeniem.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs" id="Snippet2":::

   Aby zmodyfikować skoroszyt podczas jego zapisania, poprzednie przykłady kodu używają następujących obiektów:

- Pole `Application` klasy `ThisAddIn` . Pole `Application` zwraca <xref:Microsoft.Office.Interop.Excel.Application> obiekt, który reprezentuje bieżące wystąpienie programu Excel.

- Parametr `Wb` procedury obsługi zdarzeń <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> dla zdarzenia. Parametr `Wb` jest <xref:Microsoft.Office.Interop.Excel.Workbook> obiektem, który reprezentuje zapisany skoroszyt. Aby uzyskać więcej informacji, zobacz [Omówienie modelu obiektów programu Excel](../vsto/excel-object-model-overview.md).

## <a name="test-the-project"></a>Testowanie projektu

### <a name="to-test-the-project"></a>Aby przetestować projekt

1. Naciśnij **klawisz F5,** aby skompilować i uruchomić projekt.

     Podczas kompilowania projektu kod jest kompilowany w zestawie, który znajduje się w folderze danych wyjściowych kompilacji dla projektu. Visual Studio tworzy również zestaw wpisów rejestru, które umożliwiają programowi Excel odnajdywanie i ładowanie dodatku VSTO, a także konfiguruje ustawienia zabezpieczeń na komputerze dewelopera, aby umożliwić uruchamianie dodatku VSTO. Aby uzyskać więcej informacji, zobacz [Build Office solutions (Tworzenie rozwiązań pakietu Office).](../vsto/building-office-solutions.md)

2. W programie Excel zapisz skoroszyt.

3. Sprawdź, czy do skoroszytu został dodany następujący tekst.

     **Ten tekst został dodany przy użyciu kodu.**

4. Zamknij program Excel.

## <a name="clean-up-the-project"></a>Czyszczenie projektu
 Po zakończeniu tworzenia projektu usuń zestaw dodatku VSTO, wpisy rejestru i ustawienia zabezpieczeń z komputera dewelopera. W przeciwnym razie dodatek VSTO będzie nadal uruchamiany przy każdym otwarciu programu Excel na komputerze dewelopera.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Aby wyczyścić ukończony projekt na komputerze dewelopera

1. W Visual Studio menu **Build (Kompilacja)** kliknij pozycję **Clean Solution (Wyczyść rozwiązanie).**

## <a name="next-steps"></a>Następne kroki
 Po utworzeniu podstawowego dodatku VSTO dla programu Excel możesz dowiedzieć się więcej na temat tworzenia dodatków VSTO z tych tematów:

- Ogólne zadania programistyczne, które można wykonywać w dodatki VSTO: [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

- Zadania programistyczne specyficzne dla dodatków VSTO programu Excel: [rozwiązania programu Excel.](../vsto/excel-solutions.md)

- Korzystanie z modelu obiektów programu Excel: [Omówienie modelu obiektów programu Excel.](../vsto/excel-object-model-overview.md)

- Dostosowywanie interfejsu użytkownika programu Excel, na przykład przez dodanie karty niestandardowej do wstążki lub utworzenie własnego niestandardowego okienka zadań: Dostosowywanie interfejsu użytkownika [pakietu Office.](../vsto/office-ui-customization.md)

- Kompilowanie i debugowanie dodatków narzędzi VSTO dla programu Excel: [tworzenie rozwiązań pakietu Office.](../vsto/building-office-solutions.md)

- Wdrażanie dodatków VSTO dla programu Excel: [wdrażanie rozwiązania pakietu Office.](../vsto/deploying-an-office-solution.md)

## <a name="see-also"></a>Zobacz też
- [Omówienie tworzenia rozwiązań pakietu Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Rozwiązania programu Excel](../vsto/excel-solutions.md)
- [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md)
- [Omówienie modelu obiektu programu Excel](../vsto/excel-object-model-overview.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)
- [Wdrażanie rozwiązania pakietu Office](../vsto/deploying-an-office-solution.md)
- [Omówienie szablonów projektów pakietu Office](../vsto/office-project-templates-overview.md)
