---
title: 'Przewodnik: Importowanie przepływu pracy wielokrotnego użytku programu SharePoint Designer do Visual Studio | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1552e45b13fbbd860a429238cf233bbfccbb3f02
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56603421"
---
# <a name="walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio"></a>Przewodnik: Importowanie przepływu pracy wielokrotnego użytku programu SharePoint Designer do Visual Studio
  W tym instruktażu przedstawiono sposób importowania przepływu pracy wielokrotnego użytku, utworzone w programie SharePoint Designer 2010 do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu przepływu pracy programu SharePoint.

 Przepływy pracy utworzone w programie SharePoint Designer lub *deklaratywne przepływy pracy*, składają się z [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] instrukcji zamiast kodu. Wprowadzono w programie SharePoint Designer 2010 *przepływów danych wielokrotnego użytku*, które są przenośne deklaratywne przepływów pracy, które mogą być używane przez różne listy, w witrynach programu SharePoint.

 Przepływy pracy utworzone w [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], takie jak przepływy pracy automatu stanów i sekwencyjny, są nazywane *kodu przepływy pracy*. Przepływy pracy kodu składają się z plikami XML i moduły kodu, w których użytkownicy mogą dostosować zachowanie przepływu pracy.

 Program Visual Studio umożliwia importowanie przepływów danych wielokrotnego użytku, utworzone w programie SharePoint Designer 2010 i konwertować je na przepływy pracy kodu do użycia w witrynach programu SharePoint.

 W tym instruktażu pokazano następujące zagadnienia:

- Tworzenie prostego, wielokrotnego użytku przepływu pracy w programie SharePoint Designer.

- Eksportowanie przepływu pracy wielokrotnego użytku programu SharePoint Designer do *.wsp* pliku do programu SharePoint.

- Importowanie *.wsp* mezzanine do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] za pomocą projektu przepływu pracy wielokrotnego użytku, do importowania.

- Zmienianie przepływu pracy przez dodanie kodu.

- Za pomocą zaimportowanych przepływu pracy w witrynie programu SharePoint.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

-   Obsługiwane edycje [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] i programu SharePoint.

-   Program Visual Studio.

-   Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010.

## <a name="create-target-sharepoint-subsites"></a>Utwórz podwitryny SharePoint docelowej
 Najpierw należy utworzyć dwa nowe Lokacje podrzędne programu SharePoint: jeden do hostowania przepływów danych wielokrotnego użytku z programu SharePoint Designer umożliwia hostowanie skonwertowane przepływy pracy.

#### <a name="to-create-sharepoint-subsites"></a>Aby utworzyć podwitrynę programu SharePoint

1. W programie SharePoint Designer 2010 na pasku menu wybierz **pliku** > **Nowa pusta witryna sieci Web**.

2. W **Nowa pusta witryna sieci Web** okno dialogowe, przejdź do witryny programu SharePoint, w której chcesz utworzyć przepływ pracy, lub użyj wartości http://<em>SystemName</em>/, a następnie wybierz **OK** przycisk.

    Zostanie wyświetlona strona główna.

3. W **podwitryny** wybierz pozycję **New** przycisku.

4. W **New** okna dialogowego wybierz **szablonów programu SharePoint** z listy w okienku po lewej stronie i wybierz polecenie **witryny zespołu** z listy w okienku po prawej stronie.

5. W **Określ lokalizację w witrynie sieci Web** Zastąp słowo **podwitryny** w adresie URL za pomocą **SPD1**, a następnie wybierz **OK** przycisku.

    Spowoduje to otwarcie nowej podwitryny do programu SharePoint Designer. Zamknij to wystąpienie programu SharePoint Designer i wróć do pierwszego wystąpienia (lokacja najwyższego poziomu).

6. Powtórz kroki od 3 do 5, do tworzenia drugiego podwitryny, tym razem, zastępując wyraz **podwitryny** w [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] z **SPD2**.

## <a name="create-a-sharepoint-designer-reusable-workflow"></a>Tworzenie przepływu pracy wielokrotnego użytku programu SharePoint Designer
 Ponieważ program SharePoint nie zawiera przepływów danych wielokrotnego użytku, które są dostępne w tym przykładzie, utworzysz jedną. W tym prosty przepływ pracy gdy użytkownik wprowadza nowe zadanie na liście zadań, która ma określonego tytułu zadanie zostanie przypisane do tego użytkownika.

#### <a name="to-create-a-sharepoint-designer-reusable-workflow"></a>Aby utworzyć wielokrotny przepływ danych programu SharePoint Designer

1.  W **podwitryny** wybierz pozycję **SPD1** lokacji go zmodyfikować.

2.  Na Wstążce, wybierz **przepływu pracy wielokrotnego użytku** przycisku.

     Zostanie wyświetlony Kreator tworzenia przepływu pracy wielokrotnego użytku.

3.  W **nazwa** wprowadź **SPD zadania przepływu pracy**.

4.  W **typu zawartości** wybierz **zadań**, a następnie wybierz **OK** przycisku.

     Przepływ pracy zostanie otwarty w Projektancie przepływu pracy programu SharePoint Designer.

5.  W Projektancie przepływu pracy, wybierz krok 1, a następnie na Wstążce, wybierz **warunek** przycisku.

6.  Na liście warunków, wybierz opcję **Jeśli pola bieżącego elementu jest równa wartości**.

     Ten krok powoduje dodanie warunku, który nosi nazwę **Jeśli pole jest równa wartości**.

7.  W **Jeśli pole jest równa wartości** warunku, wybierz polecenie **pola** łącza.

8.  Na liście wartości, wybierz opcję **tytuł**.

9. W **Jeśli pole jest równa wartości** warunku, wybierz polecenie **wartość** łącza.

10. W oknie dialogowym wprowadź **nowe zadanie**.

     Instrukcja warunku teraz odczytuje **Jeśli bieżący element: tytuł jest równe nowe zadanie**.

11. Wybierz linii poniżej instrukcja warunku, a następnie na Wstążce, wybierz **akcji** przycisku.

12. Z listy akcji wybierz **pole zestawu w bieżącym elemencie**.

13. W **pole zestawu wartości** akcji, wybierz **pola** połączyć, a następnie na liście, wybierz **przypisane do**.

14. W **pole zestawu wartości** akcji, wybierz **wartość** połączyć, a następnie na liście istniejących użytkowników i grup, wybierz opcję **użytkownika, który utworzył element**.

15. Wybierz **Dodaj** przycisk, a następnie wybierz **OK** przycisku.

     Teraz za pomocą instrukcji akcji odczytuje **ustawić przypisany do do bieżącego elementu: CreatedBy**.

## <a name="save-and-deploy-the-reusable-workflow"></a>Zapisz i wdróż wielokrotny przepływ danych
 Ponieważ [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] można importować tylko *.wsp* plików, należy zapisać przepływu pracy wielokrotnego użytku jako *.wsp* pliku, a następnie wdrożyć go w programie SharePoint, przed zaimportowaniem ich do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

> [!IMPORTANT]
>  Jeśli zostanie wyświetlony błąd środowiska uruchomieniowego, wykonując następującą procedurę, musisz wykonać procedurę na komputerze, który ma dostęp do witryny programu SharePoint.

#### <a name="to-save-and-deploy-the-reusable-workflow"></a>Aby zapisać i wdrożyć wielokrotny przepływ danych

1.  W górnej części programu SharePoint Designer wybierz **Zapisz** przycisk, aby zapisać postęp, a następnie wybierz **Publikuj** przycisk, aby wdrożyć przepływ pracy, aby **SPD1** witryny programu SharePoint .

2.  W okienku nawigacji wybierz **przepływy pracy** obiektu.

3.  W obszarze **przepływu pracy wielokrotnego użytku**, wybierz **SPD zadania przepływu pracy**.

4.  Na Wstążce, wybierz **Zapisz jako szablon** przycisk, aby zapisać przepływ pracy jako *.wsp* pliku.

5.  Otwórz **SPD1** witryny programu SharePoint w przeglądarce, aby wyświetlić *.wsp* pliku w programie SharePoint.

6.  Na pasku szybkiego uruchamiania wybierz **bibliotek** łącza.

7.  W **biblioteki dokumentów** wybierz pozycję **zasobów witryn** łącza.

     **SPD zadania przepływu pracy** pliku jest wyświetlany na liście zasobów innych witryn.

8.  Na liście plików wybierz nazwę tego pliku

9. W **pobieranie pliku** okna dialogowego wybierz **Zapisz** przycisk, aby zapisać *.wsp* plików w systemie lokalnym.

## <a name="import-the-wsp-file-into-visual-studio"></a>Importuj plik .wsp do programu Visual Studio
 Importuj *.wsp* mezzanine do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] za pomocą projektu przepływu pracy wielokrotnego użytku, do importowania. Ten projekt konwertuje przepływu pracy z przepływu pracy wielokrotnego użytku, deklaratywne kodu przepływu pracy. Po przekonwertowaniu przepływu pracy, użyje kodu zmodyfikowania jego działania.

#### <a name="to-import-a-workflow-from-a-wsp-file-and-modify-it"></a>Aby zaimportować przepływu danych z pliku .wsp, a następnie go zmodyfikować

1. W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], na pasku menu wybierz **pliku** > **New** > **projektu**.

2. W **nowy projekt** okna dialogowego rozwiń **SharePoint** węźle albo **Visual C#** lub **języka Visual Basic**, a następnie wybierz polecenie **2010** węzła.

3. W **szablony** okienku wybierz **importowanie wielokrotnego użytku, do programu SharePoint 2010 z przepływu pracy** szablonu, pozostaw nazwę projektu jako **WorkflowImportProject1**, a następnie wybierz pozycję **OK** przycisku.

    Zostanie wyświetlony Kreator dostosowania programu SharePoint.

4. Na **Określanie witryny i poziomu zabezpieczeń dla debugowania** wpisz [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] drugi podwitryny programu SharePoint, który został utworzony wcześniej: http://<em>Nazwa systemowa</em>/SPD2.

5. W **co to jest poziom zaufania dla tego rozwiązania programu SharePoint?** wybierz pozycję **Wdróż jako rozwiązanie farmy** przycisk opcji, a następnie wybierz **dalej** przycisku.

    Aby uzyskać więcej informacji o trybie piaskownicy porównaniu z rozwiązaniami farmy, zobacz [uwagi dotyczące rozwiązania typu piaskownica](../sharepoint/sandboxed-solution-considerations.md).

6. W **Określanie nowego źródła projektu** strony, przejdź do lokalizacji w systemie, w której został wcześniej zapisany *.wsp* pliku, otwórz plik, a następnie wybierz **dalej** przycisk.

   > [!NOTE]
   >  Wybierz **Zakończ** przycisk, aby zaimportować wszystkie dostępne elementy w *.wsp* pliku.

    Spowoduje to wyświetlenie listy przepływów danych wielokrotnego użytku, które są dostępne do importowania.

7. W **Wybieranie elementów do zaimportowania** wybierz **SPD zadania przepływu pracy** przepływu pracy, a następnie wybierz **Zakończ** przycisku.

    Po zakończeniu operacji importowania projektu o nazwie **WorkflowImportProject1** jest tworzony, zawierającego przepływ pracy o nazwie **SPD_Workflow_TestFT**. W tym folderze jest plik definicji przepływu pracy *Elements.xml* i plik projektanta przepływu pracy (*xoml*). Projektant zawiera dwa pliki: plik reguł (Rules) i pliku związanego z kodem (albo *.cs* lub *.vb*, w zależności od języka programowania projektu).

8. W **Eksploratora rozwiązań**, Usuń **inne zaimportowane pliki** folderu.

9. W *Elements.xml* , Usuń `InstantiationURL="_layouts/IniErkflIP.sspx"`.

10. W **Eksploratora rozwiązań**, wybierz **WorkflowImportProject1**, a następnie na pasku menu wybierz **projektu** > **Ustaw jako projekt startowy**  można ustawić **WorkflowImportProject1** jako element startowy.

     Wyświetla listę, natychmiast, podczas debugowania projektu.

11. Ponieważ **Importowanie programu SharePoint 2010 przepływu pracy wielokrotnego użytku** szablonu nie importuje wartości właściwości skojarzenia dla importowanych przepływu pracy, należy wprowadzić je. W tym celu:

    1.  W **Eksploratora rozwiązań**, wybierz **SPD_Workflow_TestFT** węzła.

    2.  Wybierz przycisk wielokropka (![elipsy projektanta Mobile ASP.NET](../sharepoint/media/mwellipsis.gif "elipsy projektanta Mobile ASP.NET")) przycisk obok jednego z listy właściwości, takie jak **listy docelowej** właściwości.

    3.  Wypełnienie brakujących wartości w Kreatorze dostosowywania programu SharePoint, a następnie wybierz **Zakończ** przycisku.

12. Wybierz Plik xoml, a następnie na pasku menu wybierz **widoku** > **projektanta** Aby wyświetlić zaimportowane przepływu pracy w Projektancie przepływu pracy.

13. W **Windows Workflow 3.0** węźle **przybornika**, wykonaj jedną z następujących czynności:

    - Otwórz menu skrótów dla **kodu** działania, a następnie wybierz **kopiowania**. W Projektancie przepływu pracy, otwórz menu skrótów dla linii poniżej **SequenceActivity1** działania, a następnie wybierz **Wklej**.

    - Przeciągnij **kodu** działanie z **przybornika** do projektanta przepływów pracy i podłącz go do nowego wiersza w obszarze **SequenceActivity1** działania.

      Spowoduje to dodanie do projektanta przepływów pracy o nazwie działanie **CodeActivity1**. W przypadku tego działania doda akcji kodu, który tworzy zawiadomienie do listy anonsów, gdy użytkownik uruchamia przepływ pracy.

14. Wykonaj jeden z następujących zestawów czynności:

    -   Kliknij dwukrotnie **CodeActivity1** do generowania procedury obsługi zdarzeń i przeglądania kodu.

    -   W **właściwości** okno **CodeActivity1**, ustaw wartość **ExecuteCode** właściwości **codeActivity_ExecuteCode**.

15. Dodaj następujący kod w ramach istniejącego **przy użyciu** lub **Importy** instrukcji:

     [!code-csharp[SP_SPDWFImport#1](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]

16. Zastąp `codeActivity1_ExecuteCode` następującym kodem:

     [!code-csharp[SP_SPDWFImport#2](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]

## <a name="deploy-the-project-and-associate-the-workflow"></a>Wdrażanie projektu i kojarzenie przepływu danych
 Następnie uruchom WorkflowImportProject1 wdrożyć ją w witrynie programu SharePoint i następnie skojarzyć przepływ pracy z listą zadań do wyświetlania i testowania zmodyfikowane, przekonwertować przepływu pracy.

#### <a name="to-deploy-the-project-and-associate-the-workflow"></a>Aby wdrożyć projekt i skojarzyć przepływ danych

1.  W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], wybierz **F5** klucza do uruchamiania i wdrażania projektu przekonwertowanego przepływu pracy.

2.  Na pasku szybkiego uruchamiania wybierz **zadania** łącze, aby wyświetlić listę zadań.

3.  Na **narzędzia do obsługi List** kartę, wybrać **elementów** przycisk, a następnie wybierz **nowy element** przycisku.

     **Zadania - nowy element** zostanie otwarte okno dialogowe.

4.  W **tytuł** wprowadź **nowe zadanie**, a następnie wybierz **Zapisz** przycisku.

5.  Na **narzędzia do obsługi List** kartę, wybrać **listy** przycisk, a następnie wybierz **ustawienia listy** przycisku.

     **Ustawienia listy** zostanie wyświetlona strona.

6.  W **uprawnienia i zarządzanie** wybierz pozycję **ustawienia przepływu pracy** łącza.

     **Ustawienia przepływu pracy** zostanie wyświetlona strona.

7.  Wybierz **Dodaj przepływ pracy** łącza.

8.  W **przepływu pracy** wybierz **WorkflowImportProject1 - Test przepływu pracy SPD**.

9. W **nazwa** wprowadź **SPD przepływ pracy Test**, a następnie wybierz **OK** przycisku.

10. Na pasku szybkiego uruchamiania wybierz **zadania** listy.

11. Wybierz strzałkę obok **nowe zadanie**, a następnie na liście, wybierz **przepływy pracy**.

12. W **uruchomić nowy przepływ pracy** sekcji, wybierz łącze **SPD przepływ pracy Test**, a następnie wybierz **Start** przycisk, aby zainicjować przepływ pracy.

    > [!NOTE]
    >  Alternatywnie możesz można-skojarzenie automatyczne przepływu pracy z listą, uruchamiając Kreatora ustawień przepływu pracy i ustawienia przepływu pracy skojarzenie automatyczne.

     Należy zauważyć, że dwie akcje są wykonywane przez przepływ pracy: Twoja nazwa pojawia się w zadania podrzędnego **przypisane do** kolumny i anonse zostaną wyświetlone w **anonsów** listy.

## <a name="see-also"></a>Zobacz także
- [Importowanie elementów z istniejącej witryny programu SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Tworzenie formantów wielokrotnych dla części sieciowych lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
