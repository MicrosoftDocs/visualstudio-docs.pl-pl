---
title: Typowe zadania w programowaniu pakietu Office
description: Dowiedz się, jak programować względem danych w dostosowaniu na poziomie dokumentu bez konieczności używania modelu obiektów programu Microsoft Office Word lub Office Excel.
ms.custom: SEO-VS-2020SS
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, getting started
- FAQs (frequently asked questions) [Office development in Visual Studio]
- Office development in Visual Studio, frequently asked questions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4f6fae2b7d446035a08e3fcb77bcffaaed6de3a9
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846301"
---
# <a name="common-tasks-in-office-programming"></a>Typowe zadania w programowaniu pakietu Office
  Ten temat ma pomóc w znalezieniu odpowiedzi na następujące kategorie typowych pytań dotyczących programowania rozwiązań pakietu Office przy użyciu programu Visual Studio.

- [Konfiguracja i zadania ogólne](#projects).

- [Zadania dostosowywania interfejsu użytkownika](#ui).

- [Zadania automatyzacji programu Excel](#excel).

- [Zadania automatyzacji programu Word](#word).

- [Zadania danych](#data).

- [Zadania zarządzania dokumentami po stronie serwera](#server).

- [Zadania zabezpieczeń](#security).

- [Zadania wdrażania](#deployment).

## <a name="setup-and-general-tasks"></a><a name="projects"></a> Konfiguracja i zadania ogólne

- [Instrukcje: Tworzenie projektów pakietu Office w programie Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

- [Instrukcje: Uaktualnianie rozwiązań pakietu Office](/previous-versions/4bez6837(v=vs.140)).

- [Instrukcje: Instalowanie podstawowych zestawów międzyoperacyjnych pakietu Office](../vsto/how-to-install-office-primary-interop-assemblies.md).

- [Jak: docelowa aplikacja pakietu Office przy użyciu podstawowych zestawów międzyoperacyjnych](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).

- [Instrukcje: Tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

- [Instrukcje: otwieranie rozwiązań pakietu Office bez uruchamiania kodu](../vsto/how-to-open-office-solutions-without-running-code.md).

- [Instrukcje: Konfigurowanie informacji o konfiguracji dla rozwiązań pakietu Office](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md).

- [Instrukcje: pokazywanie karty dewelopera na Wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

- [Instrukcje: pokazywanie błędów interfejsu użytkownika dodatku](../vsto/how-to-show-add-in-user-interface-errors.md).

## <a name="user-interface-customization-tasks"></a><a name="ui"></a> Zadania dostosowywania interfejsu użytkownika

### <a name="controls-on-documents-and-worksheets"></a>Kontrolki dokumentów i arkuszy

- [Instrukcje: Dodawanie formantów Windows Forms do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).

- [Instrukcje: Dodawanie kontrolek NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md).

- [Instrukcje: Dodawanie formantów ListObject do arkuszy](../vsto/how-to-add-listobject-controls-to-worksheets.md).

- [Instrukcje: Dodawanie formantów Windows Forms do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).

- [Instrukcje: Dodawanie kontrolek zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md).

- [Instrukcje: Dodawanie kontrolek zakładek do dokumentów programu Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).

### <a name="task-panes-in-document-level-customizations"></a>Okienka zadań w dostosowaniach na poziomie dokumentu

- [Instrukcje: Dodawanie okienka akcji do dokumentów programu Word lub skoroszytów programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

### <a name="task-panes-in-vsto-add-ins"></a>Okienka zadań w dodatkach narzędzi VSTO

- [Instrukcje: Dodawanie niestandardowego okienka zadań do aplikacji](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

### <a name="ribbon-customizations"></a>Dostosowania wstążki

- [Instrukcje: wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md).

- [Jak zmienić pozycję karty na Wstążce](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).

- [Instrukcje: dostosowywanie wbudowanej karty](../vsto/how-to-customize-a-built-in-tab.md).

- [Instrukcje: Dodawanie kontrolek do widoku Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md).

- [Instrukcje: Eksportowanie wstążki z projektanta wstążki do kodu XML wstążki](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).

### <a name="outlook-form-regions"></a>Regiony formularzy programu Outlook

- [Instrukcje: Dodawanie regionu formularza do projektu dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

- [Instrukcje: zapobieganie wyświetlaniu przez program Outlook regionu formularza](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).

### <a name="custom-menus"></a>Menu niestandardowe

- [Instrukcje: Dodawanie poleceń do menu skrótów](../vsto/how-to-add-commands-to-shortcut-menus.md).

## <a name="excel-automation-tasks"></a><a name="excel"></a> Zadania automatyzacji programu Excel

- [Instrukcje: programowe wyświetlanie ciągu w komórce arkusza](../vsto/how-to-programmatically-display-a-string-in-a-worksheet-cell.md).

- [Instrukcje: programowe tworzenie nowych skoroszytów](../vsto/how-to-programmatically-create-new-workbooks.md).

- [Instrukcje: programowe otwieranie skoroszytów](../vsto/how-to-programmatically-open-workbooks.md).

- [Instrukcje: programowe zapisywanie skoroszytów](../vsto/how-to-programmatically-save-workbooks.md).

- [Instrukcje: programowe zamykanie skoroszytów](../vsto/how-to-programmatically-close-workbooks.md).

- [Instrukcje: programowe Dodawanie nowych arkuszy do skoroszytów](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).

- [Instrukcje: programowe ukrywanie arkuszy](../vsto/how-to-programmatically-hide-worksheets.md).

- [Instrukcje: Programowane przenoszenie arkuszy w skoroszytach](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md).

- [Instrukcje: Programowane ochronę skoroszytów](../vsto/how-to-programmatically-protect-workbooks.md).

- [Instrukcje: programowe odwoływanie się do zakresów arkusza w kodzie](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md).

- [Instrukcje: Programowane stosowanie stylów do zakresów w skoroszytach](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md).

- [Instrukcje: Programowane zmienianie formatowania w wierszach arkusza zawierających zaznaczone komórki](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md).

- [Instrukcje: programowe wyszukiwanie tekstu w zakresach arkusza](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md).

- [Instrukcje: Programowane drukowanie arkuszy](../vsto/how-to-programmatically-print-worksheets.md).

- [Instrukcje: Programowane uruchamianie obliczeń w programie Excel](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md).

- [Instrukcje: programowane sortowanie danych w arkuszach](../vsto/how-to-programmatically-sort-data-in-worksheets.md).

## <a name="word-automation-tasks"></a><a name="word"></a> Zadania automatyzacji programu Word

- [Instrukcje: programowe tworzenie nowych dokumentów](../vsto/how-to-programmatically-create-new-documents.md).

- [Instrukcje: programowe otwieranie istniejących dokumentów](../vsto/how-to-programmatically-open-existing-documents.md).

- [Instrukcje: programowe zapisywanie dokumentów](../vsto/how-to-programmatically-save-documents.md).

- [Instrukcje: programowe Zamykanie dokumentów](../vsto/how-to-programmatically-close-documents.md).

- [Instrukcje: Programowane wstawianie tekstu do dokumentów programu Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md).

- [Instrukcje: programowe Definiowanie i wybieranie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).

- [Instrukcje: programowe Resetowanie zakresów w dokumentach programu Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md).

- [Instrukcje: Programowane formatowanie tekstu w dokumentach](../vsto/how-to-programmatically-format-text-in-documents.md).

- [Instrukcje: Dodawanie formantów XMLNode do dokumentów programu Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md).

- [Instrukcje: Programowane aktualizowanie tekstu zakładki](../vsto/how-to-programmatically-update-bookmark-text.md).

- [Instrukcje: programowe wyszukiwanie i zastępowanie tekstu w dokumentach](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md).

- [Instrukcje: programowe drukowanie dokumentów](../vsto/how-to-programmatically-print-documents.md).

- [Instrukcje: Programowane tworzenie tabel programu Word](../vsto/how-to-programmatically-create-word-tables.md).

- [Instrukcje: programowe Dodawanie wierszy i kolumn do tabel programu Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md).

- [Instrukcje: Programowane zliczanie znaków w dokumentach](../vsto/how-to-programmatically-count-characters-in-documents.md).

## <a name="data-tasks"></a><a name="data"></a> Zadania danych

### <a name="data-bound-controls"></a>Formanty powiązane z danymi

- [Instrukcje: zapełnianie arkuszy danymi z bazy danych](../vsto/how-to-populate-worksheets-with-data-from-a-database.md).

- [Instrukcje: zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md).

- [Instrukcje: zapełnianie dokumentów danymi z usług](../vsto/how-to-populate-documents-with-data-from-services.md).

- [Instrukcje: zapełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md).

- [Instrukcje: zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md).

- [Instrukcje: zapełnianie dokumentów danymi z usług](../vsto/how-to-populate-documents-with-data-from-services.md).

- [Instrukcje: aktualizowanie źródła danych przy użyciu danych z kontrolki hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

### <a name="cached-data-in-document-level-solutions"></a>Buforowane dane w rozwiązaniach na poziomie dokumentu

- [Instrukcje: dane pamięci podręcznej do użycia w trybie offline lub na serwerze](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- [Instrukcje: programowane buforowanie źródła danych w dokumencie pakietu Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).

- [Instrukcje: buforowanie danych w dokumencie chronionym hasłem](../vsto/how-to-cache-data-in-a-password-protected-document.md).

### <a name="custom-xml-data"></a>Niestandardowe dane XML

- [Instrukcje: Dodawanie niestandardowych części XML do dostosowywania na poziomie dokumentu](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md).

- [Instrukcje: Dodawanie niestandardowych części XML do dokumentów za pomocą dodatków narzędzi VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).

## <a name="server-side-document-management-tasks"></a><a name="server"></a> Zadania zarządzania dokumentami po stronie serwera

- [Instrukcje: usuwanie rozszerzeń kodu zarządzanego z dokumentów](../vsto/how-to-remove-managed-code-extensions-from-documents.md).

- [Instrukcje: dołączanie rozszerzeń kodu zarządzanego do dokumentów](../vsto/how-to-attach-managed-code-extensions-to-documents.md).

## <a name="security-tasks"></a><a name="security"></a> Zadania zabezpieczeń

- [Instrukcje: podpisywanie rozwiązań pakietu Office](../vsto/how-to-sign-office-solutions.md).

## <a name="deployment-tasks"></a><a name="deployment"></a> Zadania wdrażania

- [Instrukcje: publikowanie rozwiązania pakietu Office przy użyciu technologii ClickOnce](/previous-versions/bb386095(v=vs.110)).

- [Instrukcje: publikowanie rozwiązania Office na poziomie dokumentu na serwerze programu SharePoint przy użyciu technologii ClickOnce](/previous-versions/bb608595(v=vs.110)).

- [Instrukcje: Instalowanie rozwiązania Office ClickOnce](/previous-versions/bb608592(v=vs.110)).

- [Instrukcje: Instalowanie wymagań wstępnych na komputerach użytkowników końcowych w celu uruchamiania rozwiązań pakietu Office](/previous-versions/bb608608(v=vs.110)).

- [Instrukcje: przygotowanie usług IIS do wdrożenia rozwiązań pakietu Office](/previous-versions/bb608629(v=vs.110)).

- [Instrukcje: aktualizowanie wdrożonych rozwiązań pakietu Office](/previous-versions/bb157871(v=vs.110)).

- [Instrukcje: zmiana ścieżki instalacji rozwiązania pakietu Office](/previous-versions/bb608626(v=vs.110)).

## <a name="see-also"></a>Zobacz także
- [Wprowadzenie &#40;Programowanie Office w programie Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Funkcje dostępne według aplikacji pakietu Office i typu projektu](../vsto/features-available-by-office-application-and-project-type.md)
- [Przykłady i przewodniki dotyczące programowania pakietu Office](../vsto/office-development-samples-and-walkthroughs.md)