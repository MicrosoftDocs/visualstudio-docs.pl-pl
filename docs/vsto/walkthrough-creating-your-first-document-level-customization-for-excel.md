---
title: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Excel
description: Utwórz dostosowanie na poziomie dokumentu dla programu Microsoft Excel. Funkcje tworzone w tym rodzaju rozwiązaniu są dostępne tylko wtedy, gdy określony skoroszyt jest otwarty.
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
ms.openlocfilehash: ae0f4982ca325970b8b7965c956a7d2dea4bf60f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966672"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-excel"></a>Przewodnik: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Excel

  W tym instruktażu wprowadzającym pokazano, jak utworzyć dostosowanie na poziomie dokumentu dla programu Excel Microsoft Office. Funkcje tworzone w tym rodzaju rozwiązaniu są dostępne tylko wtedy, gdy określony skoroszyt jest otwarty. Nie można użyć dostosowania na poziomie dokumentu w celu wprowadzania zmian w całej aplikacji, na przykład wyświetlania nowej karty wstążki, gdy dowolny skoroszyt jest otwarty.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie projektu skoroszytu programu Excel.

- Dodawanie tekstu do arkusza hostowanego w programie Visual Studio Designer.

- Pisanie kodu, który używa modelu obiektów programu Excel do dodawania tekstu do niestandardowego arkusza podczas jego otwierania.

- Kompilowanie i uruchamianie projektu w celu jego przetestowania.

- Czyszczenie ukończonego projektu w celu usunięcia niepotrzebnych plików kompilacji i ustawień zabezpieczeń z komputera deweloperskiego.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne

 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Tworzenie projektu

### <a name="to-create-a-new-excel-workbook-project-in-visual-studio"></a>Aby utworzyć nowy projekt skoroszytu programu Excel w programie Visual Studio

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.
::: moniker range="vs-2017"
3. W okienku szablony rozwiń pozycję **Visual C#** lub **Visual Basic**, a następnie rozwiń węzeł **Office/SharePoint**.

4. W rozwiniętym węźle **Office/SharePoint** wybierz węzeł **dodatki narzędzi VSTO** .

5. Na liście szablonów projektu wybierz projekt programu Excel VSTO.

6. W polu **Nazwa** wpisz **FirstWorkbookCustomization**.

7. Kliknij przycisk **OK**.

8. Wybierz pozycję **Utwórz nowy dokument** w **Kreatorze programu Visual Studio Tools dla pakietu Office**, a następnie kliknij przycisk **OK**.
::: moniker-end
::: moniker range=">=vs-2019"
3. W oknie dialogowym **Tworzenie nowego projektu** wybierz projekt **programu Excel VSTO** .

     [!INCLUDE[new-project-dialog-search](../vsto/includes/new-project-dialog-search-md.md)]

4. Kliknij przycisk **Dalej**.

5. Wpisz **FirstWorkbookCustomization** w polu **Nazwa** w oknie dialogowym **Konfigurowanie nowego projektu** , a następnie kliknij przycisk **Utwórz**.

6. Wybierz pozycję **Utwórz nowy dokument** w **Kreatorze programu Visual Studio Tools dla pakietu Office**, a następnie kliknij przycisk **OK**.
::: moniker-end
   - [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tworzy projekt **FirstWorkbookCustomization** i dodaje do projektu następujące pliki.

   - *FirstWorkbookCustomization*. xlsx — reprezentuje skoroszyt programu Excel w projekcie. Zawiera wszystkie arkusze i wykresy.

   - Arkusz1 (plik *. vb* dla plików Visual Basic lub *CS* dla programu Visual C#) — arkusz, który udostępnia powierzchnię projektu i kod dla pierwszego arkusza w skoroszycie. Aby uzyskać więcej informacji, zobacz [arkusz elementów hosta](../vsto/worksheet-host-item.md).

   - Arkusz Arkusz2 (plik *. vb* dla pliku Visual Basic lub *CS* dla programu Visual C#) — skoroszyt zawierający powierzchnię projektu i kod dla drugiego arkusza w skoroszycie.

   - Sheet3 (plik *. vb* dla pliku Visual Basic lub *CS* dla programu Visual C#) — arkusz, który udostępnia powierzchnię projektu i kod dla trzeciego arkusza w skoroszycie.

   - ThisWorkbook (plik *. vb* dla pliku Visual Basic lub *CS* dla programu Visual C#) — zawiera powierzchnię projektowania i kod dla dostosowań na poziomie skoroszytu. Aby uzyskać więcej informacji, zobacz [skoroszyt element hosta](../vsto/workbook-host-item.md).

     Plik kodu Arkusz1 zostanie automatycznie otwarty w projektancie.

## <a name="close-and-reopen-worksheets-in-the-designer"></a>Zamknij i ponownie otwórz arkusze w projektancie

 Jeśli zamierzasz celowo lub przypadkowo zamknąć skoroszyt lub arkusz w Projektancie podczas tworzenia projektu, możesz go otworzyć ponownie.

### <a name="to-close-and-reopen-a-worksheet-in-the-designer"></a>Aby zamknąć i ponownie otworzyć arkusz w projektancie

1. Zamknij skoroszyt, klikając przycisk **Zamknij** (X) dla okna projektanta.

2. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy plik kodu **Arkusz1** , a następnie kliknij pozycję **Projektant widoków**.

     \- oraz

     W **Eksplorator rozwiązań** kliknij dwukrotnie plik kodu **Arkusz1** .

## <a name="add-text-to-a-worksheet-in-the-designer"></a>Dodawanie tekstu do arkusza w projektancie

 Interfejs użytkownika można zaprojektować, modyfikując arkusz, który jest otwarty w projektancie. Na przykład można dodać tekst do komórek, zastosować formuły lub dodać kontrolki programu Excel. Aby uzyskać więcej informacji o sposobach korzystania z projektanta, zobacz [projekty pakietu Office w środowisku programu Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

### <a name="to-add-text-to-a-worksheet-by-using-the-designer"></a>Aby dodać tekst do arkusza przy użyciu narzędzia Projektant

1. W arkuszu, który jest otwarty w projektancie, zaznacz komórkę **a1**, a następnie wpisz następujący tekst.

     **Ten tekst został dodany za pomocą projektanta.**

> [!WARNING]
> Jeśli dodasz ten wiersz tekstu do komórki **a2**, zostanie on zastąpiony przez inny kod w tym przykładzie.

## <a name="add-text-to-a-worksheet-programmatically"></a>Programistyczne Dodawanie tekstu do arkusza

 Następnie Dodaj kod do pliku kodu Arkusz1. Nowy kod używa modelu obiektów programu Excel do dodawania drugiego wiersza tekstu do skoroszytu. Domyślnie plik kodu Arkusz1 zawiera następujący wygenerowany kod:

- Częściowa definicja `Sheet1` klasy, która reprezentuje model programowania arkusza i zapewnia dostęp do modelu obiektów programu Excel. Aby uzyskać więcej informacji, należy zapoznać się z [arkuszem elementów hosta](../vsto/worksheet-host-item.md) i [modelu obiektów programu Word](../vsto/word-object-model-overview.md). Pozostała część `Sheet1` klasy jest zdefiniowana w ukrytym pliku kodu, który nie powinien być modyfikowany.

- `Sheet1_Startup` `Sheet1_Shutdown` Programy obsługi zdarzeń i. Te programy obsługi zdarzeń są wywoływane, gdy program Excel ładuje i zwalnia dostosowanie. Te programy obsługi zdarzeń umożliwiają zainicjowanie dostosowania podczas ładowania i oczyszczenie zasobów używanych przez dostosowanie podczas jego zwalniania. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).

### <a name="to-add-a-second-line-of-text-to-the-worksheet-by-using-code"></a>Aby dodać drugi wiersz tekstu do arkusza przy użyciu kodu

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **Arkusz1**, a następnie kliknij polecenie **Wyświetl kod**.

     Plik kodu zostanie otwarty w programie Visual Studio.

2. Zastąp `Sheet1_Startup` procedurę obsługi zdarzeń poniższym kodem. Po otwarciu Arkusz1 ten kod dodaje drugi wiersz tekstu do arkusza.

     [!code-csharp[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/CSharp/Trin_ExcelWorkbookTutorial/Sheet1.cs#1)]
     [!code-vb[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ExcelWorkbookTutorial/Sheet1.vb#1)]

## <a name="test-the-project"></a>Testowanie projektu

### <a name="to-test-your-workbook"></a>Aby przetestować skoroszyt

1. Naciśnij klawisz **F5** , aby skompilować i uruchomić projekt.

     Podczas kompilowania projektu, kod jest kompilowany do zestawu, który jest skojarzony ze skoroszytem. Program Visual Studio umieszcza kopię skoroszytu i zestaw w folderze danych wyjściowych kompilacji dla projektu i konfiguruje ustawienia zabezpieczeń na komputerze deweloperskim w celu umożliwienia uruchomienia dostosowania. Aby uzyskać więcej informacji, zobacz [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md).

2. W skoroszycie Sprawdź, czy widzisz następujący tekst.

     **Ten tekst został dodany za pomocą projektanta.**

     **Ten tekst został dodany za pomocą kodu.**

3. Zamknij skoroszyt.

## <a name="clean-up-the-project"></a>Wyczyść projekt

 Po zakończeniu opracowywania projektu należy usunąć pliki z folderu danych wyjściowych kompilacji oraz ustawienia zabezpieczeń utworzone przez proces kompilacji.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Aby wyczyścić ukończony projekt na komputerze deweloperskim

1. W programie Visual Studio w menu **kompilacja** kliknij pozycję **czyste rozwiązanie**.

## <a name="next-steps"></a>Następne kroki

 Teraz, gdy utworzono podstawowe dostosowanie na poziomie dokumentu dla programu Excel, możesz dowiedzieć się więcej na temat opracowywania dostosowań z tych tematów:

- Ogólne zadania programistyczne, które można wykonać w dostosowaniu na poziomie dokumentu: [dostosowania na poziomie dokumentu programu](../vsto/programming-document-level-customizations.md).

- Zadania programistyczne, które są specyficzne dla dostosowań na poziomie dokumentu dla programu Excel: [rozwiązania programu Excel](../vsto/excel-solutions.md).

- Za pomocą modelu obiektów programu Excel: [Omówienie modelu obiektów programu](../vsto/excel-object-model-overview.md)Excel.

- Dostosowywanie interfejsu użytkownika programu Excel, na przykład przez dodanie karty niestandardowej do wstążki lub utworzenie własnego okienka akcji: [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).

- Używanie rozszerzonych obiektów programu Excel udostępnianych przez narzędzia deweloperskie pakietu Office w programie Visual Studio do wykonywania zadań, które nie są możliwe przy użyciu modelu obiektów programu Excel (na przykład hostowanie formantów zarządzanych w dokumentach i Powiązywanie formantów programu Excel z danymi przy użyciu modelu powiązań danych Windows Forms): [Automatyzuj program Excel przy użyciu obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md).

- Kompilowanie i debugowanie dostosowań na poziomie dokumentu dla programu Excel: [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md).

- Wdrażanie dostosowań na poziomie dokumentu dla programu Excel: [Wdróż rozwiązanie pakietu Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Zobacz też

- [Omówienie programowania rozwiązań dla pakietu Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Rozwiązania programu Excel](../vsto/excel-solutions.md)
- [Dostosowywanie na poziomie dokumentu programu](../vsto/programming-document-level-customizations.md)
- [Model obiektów programu Excel — Omówienie](../vsto/excel-object-model-overview.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)
- [Wdróż rozwiązanie pakietu Office](../vsto/deploying-an-office-solution.md)
- [Szablony projektów pakietu Office — omówienie](../vsto/office-project-templates-overview.md)
