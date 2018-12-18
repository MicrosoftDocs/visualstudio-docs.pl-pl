---
title: Typowe zadania w programowaniu pakietu Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, getting started
- FAQs (frequently asked questions) [Office development in Visual Studio]
- Office development in Visual Studio, frequently asked questions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 085ed1a4f430be957d96991798458e411bc22992
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672811"
---
# <a name="common-tasks-in-office-programming"></a>Typowe zadania w programowaniu pakietu Office
  Ten temat jest przeznaczony do pomóc w znalezieniu odpowiedzi na następujące kategorie często zadawane pytania dotyczące programowania rozwiązań pakietu Office przy użyciu programu Visual Studio.  
  
-   [Konfiguracja i ogólne zadania konfiguracyjne](#projects).  
  
-   [Zadania dostosowywania interfejsu użytkownika](#ui).  
  
-   [Automatyzacja zadań w programie Excel](#excel).  
  
-   [Word zadania automatyzacji](#word).  
  
-   [Zadania danych](#data).  
  
-   [Zadania zarządzania po stronie serwera dokumentów](#server).  
  
-   [Zadań związanych z zabezpieczeniami](#security).  
  
-   [Zadania związane z wdrażaniem](#deployment).  
  
##  <a name="projects"></a> Konfiguracja i ogólne zadania konfiguracyjne  
  
-   [Porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
-   [Porady: rozwiązań pakietu Office uaktualnienia](https://msdn.microsoft.com/a269e539-b717-4680-a568-2152b070347e).  
  
-   [Porady: podstawowe zestawy międzyoperacyjne pakietu Office instalacji](../vsto/how-to-install-office-primary-interop-assemblies.md).  
  
-   [Porady: aplikacje Office docelowej przy użyciu podstawowych zestawów międzyoperacyjnych](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).  
  
-   [Porady: tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
-   [Porady: rozwiązania Open Office bez uruchamiania kodu](../vsto/how-to-open-office-solutions-without-running-code.md).  
  
-   [Porady: Ustawianie informacji o konfiguracji dla rozwiązań pakietu Office](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md).  
  
-   [Porady: pokazywanie karty dewelopera na wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
-   [Porady: dodatek Pokaż błędy interfejsu użytkownika](../vsto/how-to-show-add-in-user-interface-errors.md).  
  
##  <a name="ui"></a> Zadania dostosowywania interfejsu użytkownika  
  
### <a name="controls-on-documents-and-worksheets"></a>Formanty w dokumentach i arkuszy  
  
-   [Porady: Dodawanie kontrolek formularzy Windows Forms do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).  
  
-   [Porady: dodawanie formantów NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md).  
  
-   [Porady: dodawanie formantów ListObject do arkuszy](../vsto/how-to-add-listobject-controls-to-worksheets.md).  
  
-   [Porady: Dodawanie kontrolek formularzy Windows Forms do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).  
  
-   [Porady: Dodawanie zawartości formantów do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md).  
  
-   [Porady: dodawanie formantów zakładek do dokumentów programu Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).  
  
### <a name="task-panes-in-document-level-customizations"></a>Okienka zadań w dostosowaniach na poziomie dokumentu  
  
-   [Porady: Dodawanie okienek akcji do dokumentów programu Word i skoroszytów programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
### <a name="task-panes-in-vsto-add-ins"></a>Okienka zadań w dodatkach VSTO  
  
-   [Porady: Dodawanie niestandardowego okienka zadań do aplikacji](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
### <a name="ribbon-customizations"></a>Dostosowań Wstążki  
  
-   [Porady: wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
-   [Porady: zmiana położenia zakładki na wstążce](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).  
  
-   [Porady: dostosowywanie wbudowanej karty](../vsto/how-to-customize-a-built-in-tab.md).  
  
-   [Porady: dodawanie formantów do widoku Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md).  
  
-   [Instrukcje: eksportowanie wstążki z projektanta wstążki do XML wstążki](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).  
  
### <a name="outlook-form-regions"></a>Regiony formularzy programu Outlook  
  
-   [Porady: dodawanie regionu formularza do projektu dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
-   [Porady: ochrona programu Outlook przed wyświetlaniem regionów formularzy](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).  
  
### <a name="custom-menus"></a>Niestandardowe menu  
  
-   [Porady: Dodawanie poleceń do menu skrótów](../vsto/how-to-add-commands-to-shortcut-menus.md).  
  
##  <a name="excel"></a> Zadania automatyzacji w programie Excel  
  
-   [Porady: programowane wyświetlanie ciągu w komórce arkusza](../vsto/how-to-programmatically-display-a-string-in-a-worksheet-cell.md).  
  
-   [Porady: programowane tworzenie nowych skoroszytów](../vsto/how-to-programmatically-create-new-workbooks.md).  
  
-   [Porady: programowane otwieranie skoroszytów](../vsto/how-to-programmatically-open-workbooks.md).  
  
-   [Porady: programowane zapisywanie skoroszytów](../vsto/how-to-programmatically-save-workbooks.md).  
  
-   [Porady: programowane zamykanie skoroszytów](../vsto/how-to-programmatically-close-workbooks.md).  
  
-   [Porady: programowane Dodawanie nowych arkuszy do skoroszytu](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).  
  
-   [Porady: programowane ukrywanie arkuszy](../vsto/how-to-programmatically-hide-worksheets.md).  
  
-   [Porady: programowane przenoszenie arkuszy w obrębie skoroszytu](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md).  
  
-   [Porady: programowane Włączanie ochrony skoroszytów](../vsto/how-to-programmatically-protect-workbooks.md).  
  
-   [Porady: programowane odwoływanie do zakresów arkusza w kodzie](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md).  
  
-   [Porady: programowane stosowanie stylów do zakresów arkusza w skoroszycie](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md).  
  
-   [Porady: programowane Zmienianie formatowania w wierszach arkusza zawierających zaznaczone komórki](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md).  
  
-   [Porady: programowane wyszukiwanie tekstu w zakresach arkusza](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md).  
  
-   [Porady: programowane Drukowanie arkuszy](../vsto/how-to-programmatically-print-worksheets.md).  
  
-   [Porady: programowane wykonywanie obliczeń programu Excel](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md).  
  
-   [Porady: programowane sortowanie danych w arkuszach](../vsto/how-to-programmatically-sort-data-in-worksheets.md).  
  
##  <a name="word"></a> Zadania automatyzacji programu Word  
  
-   [Porady: programowane tworzenie nowych dokumentów](../vsto/how-to-programmatically-create-new-documents.md).  
  
-   [Porady: programowane otwieranie istniejących dokumentów](../vsto/how-to-programmatically-open-existing-documents.md).  
  
-   [Porady: programowane zapisywanie dokumentów](../vsto/how-to-programmatically-save-documents.md).  
  
-   [Porady: programowane zamykanie dokumentów](../vsto/how-to-programmatically-close-documents.md).  
  
-   [Porady: programowane Wstawianie tekstu w dokumentach programu Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md).  
  
-   [Porady: programowane definiowanie i zaznaczanie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).  
  
-   [Porady: programowane Resetowanie zakresów w dokumentach programu Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md).  
  
-   [Porady: programowane formatowanie tekstu w dokumentach](../vsto/how-to-programmatically-format-text-in-documents.md).  
  
-   [Porady: dodawanie formantów XMLNode do dokumentów programu Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md).  
  
-   [Porady: programowane Aktualizowanie tekstu zakładki](../vsto/how-to-programmatically-update-bookmark-text.md).  
  
-   [Porady: programowane wyszukiwanie i zastępowanie tekstu w dokumentach](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md).  
  
-   [Porady: programowane drukowanie dokumentów](../vsto/how-to-programmatically-print-documents.md).  
  
-   [Instrukcje: programowe tworzenie tabel programu Word](../vsto/how-to-programmatically-create-word-tables.md).  
  
-   [Porady: programowane Dodawanie wierszy i kolumn do tabel programu Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md).  
  
-   [Porady: programowane zliczanie znaków w dokumentach](../vsto/how-to-programmatically-count-characters-in-documents.md).  
  
##  <a name="data"></a> Zadania danych  
  
### <a name="data-bound-controls"></a>Formanty powiązane z danymi  
  
-   [Porady: zapełnianie arkuszy danymi z bazy danych](../vsto/how-to-populate-worksheets-with-data-from-a-database.md).  
  
-   [Porady: zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md).  
  
-   [Porady: zapełnianie dokumentów danymi z usług](../vsto/how-to-populate-documents-with-data-from-services.md).  
  
-   [Porady: zapełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md).  
  
-   [Porady: zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md).  
  
-   [Porady: zapełnianie dokumentów danymi z usług](../vsto/how-to-populate-documents-with-data-from-services.md).  
  
-   [Porady: aktualizowanie źródła danych danymi z kontrolki hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
### <a name="cached-data-in-document-level-solutions"></a>Dane w pamięci podręcznej w rozwiązaniach na poziomie dokumentu  
  
-   [Porady: dane z pamięci podręcznej do użytku w trybie offline lub na serwerze](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   [Porady: programowane buforowanie źródła danych w dokumencie programu Word](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).  
  
-   [Porady: dane w dokumentach zabezpieczonych hasłem z pamięci podręcznej](../vsto/how-to-cache-data-in-a-password-protected-document.md).  
  
### <a name="custom-xml-data"></a>Niestandardowe dane XML  
  
-   [Porady: Dodawanie niestandardowych części XML do dostosowywania na poziomie dokumentu](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md).  
  
-   [Porady: Dodawanie niestandardowych części XML do dokumentów za pomocą dodatków narzędzi VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).  
  
##  <a name="server"></a> Zadania zarządzania dokumentu po stronie serwera  
  
-   [Porady: Usuwanie rozszerzenia kodu zarządzanego z dokumentów](../vsto/how-to-remove-managed-code-extensions-from-documents.md).  
  
-   [Porady: dołączanie rozszerzenia kodu do dokumentów zarządzanego](../vsto/how-to-attach-managed-code-extensions-to-documents.md).  
  
##  <a name="security"></a> Zadań związanych z zabezpieczeniami  
  
-   [Porady: podpisywanie rozwiązań pakietu Office](../vsto/how-to-sign-office-solutions.md).  
  
##  <a name="deployment"></a> Zadania związane z wdrażaniem  
  
-   [Porady: publikowanie rozwiązania do pakietu Office przy użyciu technologii ClickOnce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8).  
  
-   [Porady: publikowanie rozwiązania pakietu Office poziomu dokumentu na serwerze programu SharePoint przy użyciu technologii ClickOnce](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58).  
  
-   [Porady: Instalowanie rozwiązań pakietu ClickOnce Office](https://msdn.microsoft.com/14702f48-9161-4190-994c-78211fe18065).  
  
-   [Porady: Instalowanie wymagań wstępnych na komputerach użytkowników końcowych do uruchamiania rozwiązań pakietu Office](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
-   [Porady: Przygotowanie usługi IIS do wdrożenia rozwiązań dla pakietu Office](https://msdn.microsoft.com/f62bce70-81d4-4f8b-86e6-2f2afec5d9b4).  
  
-   [Porady: Aktualizacja wdrożony rozwiązań pakietu Office](https://msdn.microsoft.com/be96db53-b6ea-46ab-b8d9-b76b098b3b13).  
  
-   [Jak: zmienić ścieżkę instalacji rozwiązania do pakietu Office](https://msdn.microsoft.com/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).  
  
## <a name="see-also"></a>Zobacz także  
 [Rozpoczynanie pracy &#40;programowanie Office w Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Typ funkcji według aplikacji pakietu Office i projekt](../vsto/features-available-by-office-application-and-project-type.md)   
 [Office development ― przykłady i przewodniki](../vsto/office-development-samples-and-walkthroughs.md)  
  
  