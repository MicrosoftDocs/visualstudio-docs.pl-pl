---
title: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Excel
description: Utwórz dostosowanie na poziomie dokumentu dla programu Microsoft Excel. Funkcje, które tworzysz w tego typu rozwiązaniu, są dostępne tylko wtedy, gdy jest otwarty określony skoroszyt.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, creating your first project
- Excel [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9254aa5fd465c14e24133df59bbcee46f3c1acf4
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826905"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-excel"></a>Przewodnik: tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Excel

  W tym przewodniku wprowadzającym pokazano, jak utworzyć dostosowanie na poziomie dokumentu dla Microsoft Office Excel. Funkcje, które tworzysz w tego typu rozwiązaniu, są dostępne tylko wtedy, gdy jest otwarty określony skoroszyt. Dostosowania na poziomie dokumentu nie można używać do wprowadzania zmian w całej aplikacji, na przykład wyświetlania nowej karty Wstążki, gdy dowolny skoroszyt jest otwarty.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie projektu skoroszytu programu Excel.

- Dodawanie tekstu do arkusza, który jest hostowany w Visual Studio projektanta.

- Pisanie kodu, który używa modelu obiektów programu Excel do dodawania tekstu do dostosowanego arkusza po jego otwarciu.

- Budowania i uruchamiania projektu w celu przetestowania go.

- Czyszczenie ukończonego projektu w celu usunięcia niepotrzebnych plików kompilacji i ustawień zabezpieczeń z komputera dewelopera.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne

 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Tworzenie projektu

### <a name="to-create-a-new-excel-workbook-project-in-visual-studio"></a>Aby utworzyć nowy projekt skoroszytu programu Excel w programie Visual Studio

1. Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. W menu **File (Plik)** wskaż pozycję **New (Nowy),** a następnie kliknij pozycję **Project (Projekt).**
::: moniker range="vs-2017"
3. W okienku szablonów rozwiń pozycję **Visual C#** **lub Visual Basic**, a następnie rozwiń pozycję **Office/SharePoint.**

4. W rozwiniętym **węźle Office/SharePoint** wybierz węzeł Dodatki **VSTO.**

5. Na liście szablonów projektów wybierz projekt skoroszytu VSTO programu Excel.

6. W polu **Nazwa** wpisz **FirstWorkbookCustomization**.

7. Kliknij przycisk **OK**.

8. Wybierz **pozycję Utwórz nowy dokument w** **kreatorze Visual Studio Tools projektu pakietu Office,** a następnie kliknij przycisk **OK.**
::: moniker-end
::: moniker range=">=vs-2019"
3. W **oknie dialogowym Create a New Project (Tworzenie** nowego projektu) wybierz **projekt Excel VSTO Workbook (Skoroszyt VSTO programu Excel).**

     [!INCLUDE[new-project-dialog-search](../vsto/includes/new-project-dialog-search-md.md)]

4. Kliknij przycisk **Dalej**.

5. Wpisz **FirstWorkbookCustomization w** **polu Nazwa** w **oknie dialogowym Konfigurowanie nowego projektu** i kliknij pozycję **Utwórz**.

6. Wybierz **pozycję Utwórz nowy dokument w** **kreatorze Visual Studio Tools projektu pakietu Office,** a następnie kliknij przycisk **OK.**
::: moniker-end
   - [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tworzy projekt **FirstWorkbookCustomization** i dodaje do projektu następujące pliki.

   - *FirstWorkbookCustomization*.xlsx — reprezentuje skoroszyt programu Excel w projekcie. Zawiera wszystkie arkusze i wykresy.

   - Sheet1 (plik *vb* dla Visual Basic lub *cs* dla visual C#) — arkusz, który zapewnia powierzchnię projektową i kod pierwszego arkusza w skoroszycie. Aby uzyskać więcej informacji, zobacz [Arkusz elementu hosta](../vsto/worksheet-host-item.md).

   - Sheet2 (plik *vb* dla Visual Basic lub *cs* dla Visual C#) — arkusz, który zapewnia powierzchnię projektową i kod drugiego arkusza w skoroszycie.

   - Sheet3 (plik *vb* dla Visual Basic lub *cs* dla Visual C#) — arkusz, który zapewnia powierzchnię projektową i kod trzeciego arkusza w skoroszycie.

   - ThisWorkbook ( plik *vb* dla Visual Basic lub *cs* dla programu Visual C#) — zawiera powierzchnię projektową i kod dostosowań na poziomie skoroszytu. Aby uzyskać więcej informacji, zobacz [Element hosta skoroszytu](../vsto/workbook-host-item.md).

     Plik kodu Sheet1 jest otwierany automatycznie w projektancie.

## <a name="close-and-reopen-worksheets-in-the-designer"></a>Zamykanie i ponowne otwieranie arkuszy w projektancie

 Jeśli podczas tworzenia projektu celowo lub przypadkowo zamkniesz skoroszyt lub arkusz w projektancie, możesz otworzyć go ponownie.

### <a name="to-close-and-reopen-a-worksheet-in-the-designer"></a>Aby zamknąć i ponownie otworzyć arkusz w projektancie

1. Zamknij skoroszyt, klikając przycisk **Zamknij** (X) w oknie projektanta.

2. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy plik kodu **Sheet1,** a następnie kliknij **Projektant widoków**.

     \- lub —

     W **Eksplorator rozwiązań** kliknij dwukrotnie plik kodu **Sheet1.**

## <a name="add-text-to-a-worksheet-in-the-designer"></a>Dodawanie tekstu do arkusza w projektancie

 Interfejs użytkownika (UI) dostosowania można zaprojektować, modyfikując arkusz otwarty w projektancie. Na przykład możesz dodać tekst do komórek, zastosować formuły lub dodać kontrolki programu Excel. Aby uzyskać więcej informacji na temat korzystania z projektanta, zobacz Office projects in the Visual Studio environment (Projekty pakietu [Office w środowisku Visual Studio office).](../vsto/office-projects-in-the-visual-studio-environment.md)

### <a name="to-add-text-to-a-worksheet-by-using-the-designer"></a>Aby dodać tekst do arkusza przy użyciu projektanta

1. W arkuszu otwartym w projektancie wybierz komórkę **A1, a** następnie wpisz następujący tekst.

     **Ten tekst został dodany przy użyciu projektanta.**

> [!WARNING]
> Jeśli dodasz ten wiersz tekstu do komórki **A2**, zostanie on zastąpiony innym kodem w tym przykładzie.

## <a name="add-text-to-a-worksheet-programmatically"></a>Programowe dodawanie tekstu do arkusza

 Następnie dodaj kod do pliku kodu Sheet1. Nowy kod używa modelu obiektów programu Excel, aby dodać drugi wiersz tekstu do skoroszytu. Domyślnie plik kodu Sheet1 zawiera następujący wygenerowany kod:

- Częściowa definicja klasy, która reprezentuje model programowania arkusza i zapewnia dostęp do `Sheet1` modelu obiektów programu Excel. Aby uzyskać więcej informacji, [omówienie elementu hosta arkusza](../vsto/worksheet-host-item.md) i modelu obiektu programu [Word](../vsto/word-object-model-overview.md). Pozostała część klasy `Sheet1` jest zdefiniowana w ukrytym pliku kodu, który nie powinien być modyfikowany.

- Programy `Sheet1_Startup` obsługi zdarzeń i `Sheet1_Shutdown` . Te procedury obsługi zdarzeń są wywoływane, gdy program Excel ładuje i zwalnia dostosowanie. Użyj tych programów obsługi zdarzeń, aby zainicjować dostosowanie podczas ładowania i wyczyścić zasoby używane przez dostosowanie po jego zwolniniu. Aby uzyskać więcej informacji, zobacz [Zdarzenia w projektach pakietu Office.](../vsto/events-in-office-projects.md)

### <a name="to-add-a-second-line-of-text-to-the-worksheet-by-using-code"></a>Aby dodać drugi wiersz tekstu do arkusza przy użyciu kodu

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy **pozycję Arkusz1**, a następnie kliknij polecenie Wyświetl **kod.**

     Plik kodu zostanie otwarty w Visual Studio.

2. Zastąp program `Sheet1_Startup` obsługi zdarzeń następującym kodem. Po otwarciu arkusza Sheet1 ten kod dodaje drugi wiersz tekstu do arkusza.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelWorkbookTutorial/Sheet1.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ExcelWorkbookTutorial/Sheet1.vb" id="Snippet1":::

## <a name="test-the-project"></a>Testowanie projektu

### <a name="to-test-your-workbook"></a>Aby przetestować skoroszyt

1. Naciśnij **klawisz F5,** aby skompilować i uruchomić projekt.

     Podczas kompilowania projektu kod jest kompilowany w zestawie skojarzonym ze skoroszytem. Visual Studio umieszcza kopię skoroszytu i zestawu w folderze danych wyjściowych kompilacji dla projektu i konfiguruje ustawienia zabezpieczeń na komputerze dewelopera, aby umożliwić uruchomienie dostosowania. Aby uzyskać więcej informacji, zobacz [Build Office solutions (Tworzenie rozwiązań pakietu Office).](../vsto/building-office-solutions.md)

2. W skoroszycie sprawdź, czy widzisz następujący tekst.

     **Ten tekst został dodany przy użyciu projektanta.**

     **Ten tekst został dodany przy użyciu kodu.**

3. Zamknij skoroszyt.

## <a name="clean-up-the-project"></a>Czyszczenie projektu

 Po zakończeniu tworzenia projektu należy usunąć pliki z folderu wyjściowego kompilacji oraz ustawienia zabezpieczeń utworzone w procesie kompilacji.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Aby wyczyścić ukończony projekt na komputerze dewelopera

1. W Visual Studio menu Build  (Kompilacja) kliknij pozycję **Clean Solution (Wyczyść rozwiązanie).**

## <a name="next-steps"></a>Następne kroki

 Teraz, po utworzeniu podstawowego dostosowania na poziomie dokumentu dla programu Excel, możesz dowiedzieć się więcej na temat tworzenia dostosowań z tych tematów:

- Ogólne zadania programistyczne, które można wykonywać w dostosowaniach na poziomie dokumentu: [Programowanie dostosowań na poziomie dokumentu.](../vsto/programming-document-level-customizations.md)

- Zadania programistyczne specyficzne dla dostosowań na poziomie dokumentu dla programu Excel: [rozwiązania programu Excel.](../vsto/excel-solutions.md)

- Korzystanie z modelu obiektów programu Excel: [Omówienie modelu obiektów programu Excel.](../vsto/excel-object-model-overview.md)

- Dostosowywanie interfejsu użytkownika programu Excel, na przykład przez dodanie karty niestandardowej do wstążki lub utworzenie własnego okienka akcji: Dostosowywanie interfejsu [użytkownika pakietu Office.](../vsto/office-ui-customization.md)

- Używanie rozszerzonych obiektów programu Excel dostarczanych przez narzędzia programowe pakietu Office w programie Visual Studio do wykonywania zadań, które nie są możliwe przy użyciu modelu obiektów programu Excel (na przykład hostowanie zarządzanych kontrolek dokumentów i powiązanie kontrolek programu Excel z danymi przy użyciu modelu powiązania danych programu Windows Forms): [automatyzowanie](../vsto/automating-excel-by-using-extended-objects.md)programu Excel przy użyciu obiektów rozszerzonych.

- Kompilowanie i debugowanie dostosowań na poziomie dokumentu dla programu Excel: [Tworzenie rozwiązań pakietu Office.](../vsto/building-office-solutions.md)

- Wdrażanie dostosowań na poziomie dokumentu dla programu Excel: [wdrażanie rozwiązania pakietu Office.](../vsto/deploying-an-office-solution.md)

## <a name="see-also"></a>Zobacz też

- [Omówienie tworzenia rozwiązań pakietu Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Rozwiązania programu Excel](../vsto/excel-solutions.md)
- [Zaprogramowanie dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)
- [Omówienie modelu obiektów programu Excel](../vsto/excel-object-model-overview.md)
- [Automatyzowanie programu Excel przy użyciu obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)
- [Wdrażanie rozwiązania pakietu Office](../vsto/deploying-an-office-solution.md)
- [Omówienie szablonów projektów pakietu Office](../vsto/office-project-templates-overview.md)
