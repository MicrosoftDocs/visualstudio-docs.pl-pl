---
title: 'Przewodnik: Importowanie przepływu pracy wielokrotnego użytku programu SharePoint Designer | Microsoft Docs'
titleSuffix: ''
description: W tym instruktażu zaimportuj przepływ pracy wielokrotnego użytku utworzony w programie SharePoint Designer do projektu przepływu pracy programu Visual Studio SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.WSPImport.ImportWF
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing reusable workflows
- reusable workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d4c12626550e36acc1a135258750f2d96ac5e81d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952593"
---
# <a name="walkthrough-import-a-sharepoint-designer-reusable-workflow"></a>Przewodnik: Importowanie przepływu pracy wielokrotnego użytku programu SharePoint Designer

  W tym instruktażu przedstawiono sposób importowania przepływu pracy wielokrotnego użytku utworzonego w programie SharePoint Designer 2010 do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu przepływu pracy programu SharePoint.

 Przepływy pracy utworzone w projektancie programu SharePoint lub *deklaracyjne przepływy pracy* składają się z [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] instrukcji zamiast kodu. Program SharePoint Designer 2010 wprowadza *przepływy pracy wielokrotnego użytku*, które są przenośnymi, deklaratywnymi przepływami pracy, które mogą być używane przez różne listy w witrynach programu SharePoint.

 Przepływy pracy utworzone w programie [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] , takie jak sekwencyjne i przepływy pracy automatu, są nazywane *przepływami pracy kodu*. Przepływy pracy kodu składają się z plików XML i modułów kodu, w których użytkownicy mogą dostosować zachowanie przepływu pracy.

 Program Visual Studio umożliwia importowanie przepływów pracy wielokrotnego użytku utworzonych w programie SharePoint Designer 2010 i konwertowanie ich na przepływy pracy kodu do użycia w witrynach programu SharePoint.

 W tym instruktażu przedstawiono następujące zadania:

- Tworzenie prostego przepływu pracy wielokrotnego użytku w programie SharePoint Designer.

- Eksportowanie przepływu pracy wielokrotnego użytku programu SharePoint Designer do pliku *. wsp* i do programu SharePoint.

- Importowanie pliku *. wsp* do programu przy [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] użyciu importu przepływu pracy do wielokrotnego użytku.

- Modyfikowanie przepływu pracy przez dodanie kodu.

- Używanie zaimportowanego przepływu pracy w witrynie programu SharePoint.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Obsługiwane wersje programów [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] i SharePoint.

- Programu Visual Studio.

- Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010.

## <a name="create-target-sharepoint-subsites"></a>Tworzenie docelowych podwitryn programu SharePoint
 Najpierw utworzysz dwie nowe podwitryny programu SharePoint: jeden do hostowania przepływów pracy wielokrotnego użytku z programu SharePoint Designer, drugi do hostowania przekonwertowanych przepływów pracy.

#### <a name="to-create-sharepoint-subsites"></a>Aby utworzyć podwitrynę programu SharePoint

1. W programie SharePoint Designer 2010 na pasku menu wybierz pozycję **plik**  >  **Nowa pusta witryna sieci Web**.

2. W oknie dialogowym **Nowa pusta witryna sieci Web** przejdź do witryny programu SharePoint, w której chcesz utworzyć przepływ pracy, lub użyj wartości http://<em>SystemName</em>/, a następnie wybierz przycisk **OK** .

    Zostanie wyświetlona strona główna.

3. W sekcji **podwitryny** wybierz przycisk **Nowy** .

4. W oknie dialogowym **Nowy** wybierz pozycję **Szablony programu SharePoint** z listy w okienku po lewej stronie, a następnie wybierz pozycję **Witryna zespołu** z listy w okienku po prawej stronie.

5. W polu **Określ lokalizację witryny sieci Web** Zamień **podwitrynę** programu Word w adresie URL na **SPD1**, a następnie wybierz przycisk **OK** .

    Spowoduje to otwarcie nowej podwitryny w programie SharePoint Designer. Zamknij to wystąpienie programu SharePoint Designer i wróć do pierwszego wystąpienia (lokacji najwyższego poziomu).

6. Powtórz kroki 3-5, aby utworzyć drugą podlokację, tym razem zastępując **podlokację** programu Word [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] w **SPD2**.

## <a name="create-a-sharepoint-designer-reusable-workflow"></a>Tworzenie przepływu pracy wielokrotnego użytku projektanta programu SharePoint
 Ponieważ program SharePoint nie zawiera żadnych przepływów pracy wielokrotnego użytku, których można użyć do tego przykładu, utworzysz go. W tym prostym przepływie pracy, gdy użytkownik wprowadzi nowe zadanie na liście zadań z określonym tytułem, zadanie zostanie przypisane do tego użytkownika.

#### <a name="to-create-a-sharepoint-designer-reusable-workflow"></a>Aby utworzyć wielokrotny przepływ danych programu SharePoint Designer

1. W sekcji **lokacje podrzędne** wybierz witrynę **SPD1** , aby ją zmodyfikować.

2. Na wstążce wybierz przycisk **przepływu pracy wielokrotnego użytku** .

     Zostanie wyświetlony Kreator tworzenia przepływu pracy wielokrotnego użytku.

3. W polu **Nazwa** wprowadź **przepływ pracy zadania bazy danych SPD**.

4. Na liście **Typ zawartości** wybierz **zadanie**, a następnie wybierz przycisk **OK** .

     Przepływ pracy zostanie otwarty w Projektancie przepływów pracy programu SharePoint Designer.

5. W Projektancie przepływu pracy wybierz krok 1, a następnie na wstążce wybierz przycisk **warunek** .

6. Na liście warunków wybierz, **czy bieżące pole elementu jest równe wartość**.

     Ten krok powoduje dodanie warunku o nazwie, **Jeśli pole ma wartość Equals**.

7. W warunku **wartość pola równa** się wybierz łącze **pola** .

8. Na liście wartości wybierz pozycję **tytuł**.

9. W warunku **wartość pola równa** się wybierz łącze **wartość** .

10. W polu wprowadź **nowe zadanie**.

     Instrukcja Condition jest teraz odczytywana, **Jeśli bieżący element: tytuł ma wartość nowe zadanie**.

11. Wybierz wiersz pod instrukcją Condition, a następnie na wstążce wybierz przycisk **akcji** .

12. Na liście akcji wybierz opcję **Ustaw pole w bieżącym elemencie**.

13. W akcji **Ustaw wartość pola na wartości** wybierz łącze **pole** , a następnie na liście wybierz pozycję **przypisano do**.

14. W **Ustaw wartość pola** Akcja wybierz łącze **wartość** , a następnie na liście istniejących użytkowników i grup wybierz pozycję **użytkownik, który utworzył element**.

15. Wybierz przycisk **Dodaj** , a następnie wybierz przycisk **OK** .

     Instrukcja Action odczytuje teraz **zestaw przypisano do do bieżącego elementu: CreatedBy**.

## <a name="save-and-deploy-the-reusable-workflow"></a>Zapisz i Wdróż przepływ pracy wielokrotnego użytku
 Ponieważ [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] program może importować tylko pliki *. wsp* , należy zapisać przepływ pracy wielokrotnego użytku jako plik *. wsp* i wdrożyć go w programie SharePoint przed zaimportowaniem go do programu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

> [!IMPORTANT]
> Jeśli wystąpi błąd w czasie wykonywania poniższej procedury, należy wykonać procedurę w systemie, który ma dostęp do witryny programu SharePoint.

#### <a name="to-save-and-deploy-the-reusable-workflow"></a>Aby zapisać i wdrożyć wielokrotny przepływ danych

1. W górnej części programu SharePoint Designer wybierz przycisk **Zapisz** , aby zapisać postęp, a następnie wybierz przycisk **Publikuj** , aby wdrożyć przepływ pracy w witrynie programu SharePoint **SPD1** .

2. W okienku nawigacji wybierz obiekt **przepływy pracy** .

3. W obszarze **przepływ pracy wielokrotnego użytku** wybierz pozycję **przepływ pracy zadania bazy** danych.

4. Na wstążce wybierz przycisk **Zapisz jako szablon** , aby zapisać przepływ pracy jako plik *. wsp* .

5. Otwórz witrynę programu SharePoint **SPD1** w przeglądarce, aby wyświetlić plik *. wsp* w programie SharePoint.

6. Na pasku szybkiego uruchamiania wybierz łącze **biblioteki** .

7. W sekcji **biblioteki dokumentów** wybierz łącze **zasoby lokacji** .

     Plik **przepływu pracy zadania SPD** znajduje się na liście innych zasobów lokacji.

8. Na liście plików wybierz nazwę tego pliku

9. W oknie dialogowym **Pobieranie pliku** wybierz przycisk **Zapisz** , aby zapisać plik *. wsp* w systemie lokalnym.

## <a name="import-the-wsp-file-into-visual-studio"></a>Zaimportuj plik wsp do programu Visual Studio
 Zaimportuj plik *wsp* do programu przy [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] użyciu importu przepływu pracy do wielokrotnego użytku. Ten projekt konwertuje przepływ pracy na podstawie deklaratywnego przepływu pracy do kodu w przepływie pracy. Po przekonwertowaniu przepływu pracy zostanie użyty kod modyfikujący jego zachowanie.

#### <a name="to-import-a-workflow-from-a-wsp-file-and-modify-it"></a>Aby zaimportować przepływu danych z pliku .wsp, a następnie go zmodyfikować

1. W programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**.

2. W oknie dialogowym **Nowy projekt** rozwiń węzeł **SharePoint** w obszarze **Visual C#** lub **Visual Basic**, a następnie wybierz węzeł **2010** .

3. W okienku **Szablony** wybierz szablon **przepływu pracy wielokrotnego użytku programu SharePoint 2010** , pozostaw nazwę projektu jako **WorkflowImportProject1**, a następnie wybierz przycisk **OK** .

    Zostanie wyświetlony Kreator dostosowania programu SharePoint.

4. Na stronie **Określanie poziomu lokacji i zabezpieczeń na potrzeby debugowania** wprowadź [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] nazwę dla drugiej podwitryny programu SharePoint, która została wcześniej utworzona: http://<em>system Name</em>/SPD2.

5. W sekcji **co to jest poziom zaufania dla tego rozwiązania programu SharePoint?** wybierz przycisk opcji **Wdróż jako farmę** , a następnie wybierz przycisk **dalej** .

    Aby uzyskać więcej informacji o rozwiązaniach w trybie piaskownicy i farmie, zobacz [zagadnienia dotyczące rozwiązania w trybie piaskownicy](../sharepoint/sandboxed-solution-considerations.md).

6. Na stronie **Określanie źródła nowego projektu** przejdź do lokalizacji w systemie, w której zapisano wcześniej plik *. wsp* , Otwórz plik, a następnie wybierz przycisk **dalej** .

   > [!NOTE]
   > Wybierz przycisk **Zakończ** , aby zaimportować wszystkie dostępne elementy w pliku *. wsp* .

    Zostanie wyświetlona lista przepływów pracy wielokrotnego użytku dostępnych do zaimportowania.

7. W polu **Wybierz elementy do zaimportowania** wybierz przepływ pracy **zadania SPD** , a następnie wybierz przycisk **Zakończ** .

    Po zakończeniu operacji importowania zostanie utworzony projekt o nazwie **WorkflowImportProject1** zawierający przepływ pracy o nazwie **SPD_Workflow_TestFT**. W tym folderze jest plikiem definicji przepływu pracy *Elements.xml* i plikiem projektanta przepływu pracy (*. xoml*). Projektant zawiera dwa pliki: plik reguł (. Rules) i plik związany z kodem ( *. cs* lub *. vb*, w zależności od języka programowania projektu).

8. W **Eksplorator rozwiązań** Usuń folder **inne zaimportowane pliki** .

9. W pliku *Elements.xml* Usuń `InstantiationURL="_layouts/IniErkflIP.sspx"` .

10. W **Eksplorator rozwiązań** wybierz pozycję **WorkflowImportProject1**, a następnie na pasku menu wybierz pozycję **projekt**  >  **Ustaw jako projekt startowy** , aby ustawić **WorkflowImportProject1** jako element startowy.

     Spowoduje to wyświetlenie listy natychmiast podczas debugowania projektu.

11. Ponieważ szablon **przepływu pracy zaimportuj programu SharePoint 2010** nie importuje wartości właściwości skojarzenia dla zaimportowanego przepływu pracy, należy je wprowadzić. W tym celu:

    1. W **Eksplorator rozwiązań** wybierz węzeł **SPD_Workflow_TestFT** .

    2. Wybierz przycisk wielokropka (![ASP.net Mobile Designer](../sharepoint/media/mwellipsis.gif "Wielokropek projektanta ASP.NET Mobile")) obok jednej z właściwości listy, takich jak Właściwość **listy docelowej** .

    3. Wypełnij brakujące wartości w Kreatorze dostosowywania programu SharePoint, a następnie wybierz przycisk **Zakończ** .

12. Wybierz plik xoml, a następnie na pasku menu wybierz polecenie   >  **Projektant** widoków, aby wyświetlić zaimportowany przepływ pracy w Projektancie przepływu pracy.

13. W węźle **Windows Workflow v 3.0** **przybornika** wykonaj jedną z następujących czynności:

    - Otwórz menu skrótów dla działania **kod** , a następnie wybierz **Kopiuj**. W Projektancie przepływu pracy Otwórz menu skrótów dla wiersza w ramach działania **SequenceActivity1** , a następnie wybierz **Wklej**.

    - Przeciągnij działanie **Code** z **przybornika** do projektanta przepływu pracy i połącz je z wierszem w obszarze działania **SequenceActivity1** .

      Spowoduje to dodanie działania do projektanta przepływu pracy o nazwie **CodeActivity1**. W tym działaniu zostanie dodana akcja kodowa, która tworzy anons na liście Anonsy, gdy użytkownik uruchamia przepływ pracy.

14. Wykonaj jeden z następujących zestawów czynności:

    - Kliknij dwukrotnie pozycję **CodeActivity1** , aby wygenerować procedurę obsługi zdarzeń i wyświetlić kod.

    - W oknie **Właściwości** dla **CodeActivity1** ustaw wartość właściwości **ExecuteCode** na **codeActivity_ExecuteCode**.

15. Dodaj następujące elementy pod istniejącymi dyrektywami **using** lub **Imports** :

     [!code-csharp[SP_SPDWFImport#1](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]

16. Zamień na `codeActivity1_ExecuteCode` następujące elementy:

     [!code-csharp[SP_SPDWFImport#2](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]

## <a name="deploy-the-project-and-associate-the-workflow"></a>Wdróż projekt i skojarz przepływ pracy
 Następnie uruchom program WorkflowImportProject1 w celu wdrożenia go w witrynie programu SharePoint, a następnie skojarz przepływ pracy z listą zadań, aby wyświetlić i przetestować zmodyfikowany, przekonwertowany przepływ pracy.

#### <a name="to-deploy-the-project-and-associate-the-workflow"></a>Aby wdrożyć projekt i skojarzyć przepływ danych

1. W programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Wybierz klawisz **F5** , aby uruchomić i wdrożyć przekonwertowany projekt przepływu pracy.

2. Na pasku szybkiego uruchamiania wybierz link **zadania** , aby wyświetlić listę zadań.

3. Na karcie **Narzędzia listy** wybierz przycisk **elementy** , a następnie wybierz przycisk **nowy element** .

     Zostanie otwarte okno dialogowe **zadania — nowy element** .

4. W polu **tytuł** wprowadź **nowe zadanie**, a następnie wybierz przycisk **Zapisz** .

5. Na karcie **Narzędzia listy** wybierz przycisk **listy** , a następnie wybierz przycisk **Ustawienia listy** .

     Zostanie wyświetlona strona **Ustawienia listy** .

6. W sekcji **uprawnienia i zarządzanie** wybierz łącze **Ustawienia przepływu pracy** .

     Zostanie wyświetlona strona **Ustawienia przepływu pracy** .

7. Wybierz łącze **Dodaj przepływ pracy** .

8. Na liście **przepływów pracy** wybierz **test przepływu pracy WorkflowImportProject1-SPD**.

9. W polu **Nazwa** wprowadź **test przepływu pracy SPD**, a następnie wybierz przycisk **OK** .

10. Na pasku szybkiego uruchamiania wybierz listę **zadania** .

11. Wybierz strzałkę obok pozycji **nowe zadanie**, a następnie na liście wybierz pozycję **przepływy pracy**.

12. W sekcji **Rozpocznij nowy przepływ pracy** wybierz łącze do **testu przepływu pracy bazy** danych, a następnie wybierz przycisk **Start** , aby zainicjować przepływ pracy.

    > [!NOTE]
    > Alternatywnie można utworzyć skojarzenie przepływu pracy z listą, uruchamiając Kreatora ustawień przepływu pracy i ustawiając przepływ pracy na wartość autoskojarzenie.

     Należy zauważyć, że dwie akcje są wykonywane przez przepływ pracy: nazwa zostanie wyświetlona w kolumnie **przypisano do** zadania, a na liście **anonsów** pojawi się ogłoszenie.

## <a name="see-also"></a>Zobacz też
- [Importuj elementy z istniejącej witryny programu SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Tworzenie kontrolek wielokrotnego użytku dla części sieci Web lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
