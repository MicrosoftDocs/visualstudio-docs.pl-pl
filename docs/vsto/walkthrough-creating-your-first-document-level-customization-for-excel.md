---
title: 'Przewodnik: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Excel'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9cc23e140f0bfa2654cef1c3faeb805620a683b0
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438525"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-excel"></a>Przewodnik: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Excel
  Ten Przewodnik wprowadzający dowiesz się, jak utworzyć dostosowywania poziomie dokumentu dla programu Microsoft Office Excel. Funkcje, które tworzysz w tego rodzaju rozwiązania są dostępne tylko wtedy, gdy wybrany skoroszyt jest otwarty. Nie możesz użyć dostosowywania poziomie dokumentu do zmiany całej aplikacji, na przykład wyświetlanie Nowa karta wstążki, gdy dowolny skoroszyt jest otwarty.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie projektu skoroszytu programu Excel.

- Dodawanie tekstu do arkusza, który znajduje się w Projektancie Visual Studio.

- Pisanie kodu, który używa modelu obiektów programu Excel do dodawania tekstu w arkuszu dostosowany po jego otwarciu.

- Tworzenie i uruchamianie projektu, aby ją przetestować.

- Czyszczenie zakończone projekt, aby usunąć z komputera dewelopera kompilacji niepotrzebne pliki i ustawienia zabezpieczeń.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Utwórz projekt

### <a name="to-create-a-new-excel-workbook-project-in-visual-studio"></a>Aby utworzyć nowy projekt arkusza Excel w programie Visual Studio

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.

3. W okienku szablonów, rozwiń **Visual C#** lub **języka Visual Basic**, a następnie rozwiń węzeł **Office/SharePoint**.

4. W rozwiniętym okienku **Office/SharePoint** węzeł **dodatków pakietu Office** węzła.

5. Na liście szablonów projektu wybierz projekt dodatku narzędzi VSTO programu Excel.

6. W **nazwa** wpisz **FirstWorkbookCustomization**.

7. Kliknij przycisk **OK**.

    **Visual Studio Tools dla pakietu Office, Kreator projektu** zostanie otwarty.

8. Wybierz **Utwórz nowy dokument**i kliknij przycisk **OK**.

   - [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tworzy **FirstWorkbookCustomization** projektu i dodaje następujące pliki do projektu.

   - *FirstWorkbookCustomization*xlsx — reprezentuje skoroszyt programu Excel w projekcie. Zawiera wszystkie arkusze i wykresy.

   - Sheet1 (*.vb* pliku dla języka Visual Basic lub *.cs* pliku dla języka Visual C#) — arkusz, zapewniająca powierzchni projektowej i kod dla pierwszego arkusza w skoroszycie. Aby uzyskać więcej informacji, zobacz [element hosta arkusza](../vsto/worksheet-host-item.md).

   - Sheet2 — (*.vb* pliku dla języka Visual Basic lub *.cs* pliku dla języka Visual C#) — arkusz, zapewniająca powierzchni projektowej i kod dla drugiego arkusza w skoroszycie.

   - Sheet3 — (*.vb* pliku dla języka Visual Basic lub *.cs* pliku dla języka Visual C#) — arkusz, zapewniająca powierzchni projektowej i kod dla trzeciego arkusza w skoroszycie.

   - Ten skoroszyt (*.vb* pliku dla języka Visual Basic lub *.cs* pliku dla języka Visual C#) — zawiera powierzchnię projektu i kodu w przypadku dostosowań na poziomie skoroszytu. Aby uzyskać więcej informacji, zobacz [element hosta skoroszytu](../vsto/workbook-host-item.md).

     Plik kodu Arkusz1 zostanie automatycznie otwarty w projektancie.

## <a name="close-and-reopen-worksheets-in-the-designer"></a>Zamknij i otwórz ponownie arkuszy w Projektancie
 Jeśli celowo lub przypadkowo zamknięto skoroszytu lub arkusza w Projektancie podczas tworzenia projektu, można otworzyć go ponownie.

### <a name="to-close-and-reopen-a-worksheet-in-the-designer"></a>Aby zamknąć i ponownie otwórz arkusz w Projektancie

1. Zamknij skoroszyt, klikając przycisk **Zamknij** przycisku (X) dla okna projektanta.

2. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Arkusz1** plik kodu, a następnie kliknij przycisk **Projektant widoków**.

     \- lub —

     W **Eksploratora rozwiązań**, kliknij dwukrotnie **Arkusz1** pliku kodu.

## <a name="add-text-to-a-worksheet-in-the-designer"></a>Dodawanie tekstu do arkusza w Projektancie
 Interfejs użytkownika (UI) można zaprojektować swoje dostosowania, modyfikując arkusz kalkulacyjny, który jest otwarty w projektancie. Na przykład można dodać tekst do komórek, stosowanie formuł lub dodać kontrolki programu Excel. Aby uzyskać więcej informacji o sposobie korzystania z projektanta, zobacz [projekty pakietu Office w środowisku Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

### <a name="to-add-text-to-a-worksheet-by-using-the-designer"></a>Aby dodać tekst do arkusza za pomocą projektanta

1. W arkuszu, które jest otwarty w projektancie, zaznacz komórkę **A1**, a następnie wpisz następujący tekst.

     **Ten tekst został dodany za pomocą projektanta.**

> [!WARNING]
> Jeśli dodasz ten wiersz tekstu do komórki **A2**, zostanie on zastąpiony przez inny kod, w tym przykładzie.

## <a name="add-text-to-a-worksheet-programmatically"></a>Programowe Dodawanie tekstu do arkusza
 Następnie dodaj kod do pliku kodu Arkusz1. Nowy kod używa modelu obiektów programu Excel, można dodać drugi wiersz tekstu w skoroszycie. Domyślnie plik kodu Arkusz1 zawiera następujące wygenerowanego kodu:

- Częściową definicję `Sheet1` klasy, która reprezentuje model programowania arkusza i zapewnia dostęp do modelu obiektów programu Excel. Aby uzyskać więcej informacji [element hosta arkusza](../vsto/worksheet-host-item.md) i [model obiektu Word — omówienie](../vsto/word-object-model-overview.md). W pozostałej części `Sheet1` klasa jest zdefiniowana w pliku ukryty kod, który nie należy modyfikować.

- `Sheet1_Startup` i `Sheet1_Shutdown` procedury obsługi zdarzeń. Te procedury obsługi zdarzeń są wywoływane, gdy program Excel ładuje i zwalnia dostosowanie. Użyj tych programów obsługi zdarzeń, zainicjować dostosowanie podczas jego ładowania oraz aby wyczyścić zasoby używane przez dostosowanie, gdy jest zwolniony. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).

### <a name="to-add-a-second-line-of-text-to-the-worksheet-by-using-code"></a>Aby dodać drugi wiersz tekstu w arkuszu za pomocą kodu

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Arkusz1**, a następnie kliknij przycisk **Wyświetl kod**.

     Otwiera plik kodu w programie Visual Studio.

2. Zastąp `Sheet1_Startup` programu obsługi zdarzeń z następującym kodem. Po otwarciu Arkusz1 ten kod dodaje drugi wiersz tekstu do arkusza.

     [!code-csharp[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/CSharp/Trin_ExcelWorkbookTutorial/Sheet1.cs#1)]
     [!code-vb[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ExcelWorkbookTutorial/Sheet1.vb#1)]

## <a name="test-the-project"></a>Projekt testowy

### <a name="to-test-your-workbook"></a>Aby przetestować skoroszytu

1. Naciśnij klawisz **F5** Aby skompilować i uruchomić projekt.

     Gdy tworzysz projekt, kod jest kompilowany do zestawu, który jest skojarzony z skoroszytu. Program Visual Studio umieszcza kopię skoroszytu i zestawu w folderze danych wyjściowych kompilacji dla projektu i konfiguruje ustawienia zabezpieczeń na komputerze deweloperskim, aby włączyć dostosowywanie do uruchomienia. Aby uzyskać więcej informacji, zobacz [rozwiązań kompilacji pakietu Office](../vsto/building-office-solutions.md).

2. W skoroszycie Sprawdź, czy zostanie wyświetlony następujący tekst.

     **Ten tekst został dodany za pomocą projektanta.**

     **Ten tekst został dodany przy użyciu kodu.**

3. Zamknij skoroszyt.

## <a name="clean-up-the-project"></a>Czyszczenie projektu
 Po zakończeniu tworzenia projektu, należy usunąć pliki w folderze wyjściowym kompilacji i ustawienia zabezpieczeń utworzone w procesie kompilacji.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Aby wyczyścić ukończone projektu na komputerze deweloperskim

1. W programie Visual Studio na **kompilacji** menu, kliknij przycisk **czyste rozwiązanie**.

## <a name="next-steps"></a>Następne kroki
 Teraz, po utworzeniu podstawowego dostosowywania poziomie dokumentu dla programu Excel, można dowiedzieć się więcej o sposobie tworzenia dostosowań w tych tematach:

- Ogólne zadania programowania, które można wykonywać w dostosowaniach na poziomie dokumentu: [Program dostosowań poziomu dokumentu](../vsto/programming-document-level-customizations.md).

- Zadania związane z programowaniem, które są specyficzne dla dostosowywania poziomie dokumentu dla programu Excel: [Rozwiązania w programie Excel](../vsto/excel-solutions.md).

- Za pomocą modelu obiektów programu Excel: [Model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md).

- Dostosowywanie interfejsu użytkownika programu Excel, na przykład dodawania niestandardowej karty do Wstążki lub tworząc własne okienko akcji: [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).

- Do wykonywania zadań, która nie jest możliwa za pomocą modelu obiektów programu Excel (na przykład hostingu zarządzane formanty w dokumentach i powiązanie kontrolki programu Excel z danymi za pomocą formularzy Windows przy użyciu rozszerzonych obiektów programu Excel, udostępniane przez narzędzia programistyczne pakietu Office w programie Visual Studio model powiązania danych): [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md).

- Kompilowanie i debugowanie dostosowań poziomu dokumentu dla programu Excel: [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md).

- Wdrażanie dostosowań poziomu dokumentu dla programu Excel: [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Zobacz także
- [Rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Rozwiązania programu Excel](../vsto/excel-solutions.md)
- [Program dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)
- [Model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)
- [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)
- [Omówienie szablonów projektu pakietu Office](../vsto/office-project-templates-overview.md)
