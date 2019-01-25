---
title: 'Przewodnik: Utwórz niestandardową witrynę działanie przepływu pracy | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, custom workflow activities
- site workflows [SharePoint development in Visual Studio]
- workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, site workflows
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4cf57ccb62d5a87a3dfb516cc1d7b03f45d609ad
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875189"
---
# <a name="walkthrough-create-a-custom-site-workflow-activity"></a>Przewodnik: Utwórz niestandardową witrynę działanie przepływu pracy
  W tym instruktażu pokazano, jak utworzyć niestandardowe działanie na poziomie witryny przepływu pracy przy użyciu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. (Przepływy pracy poziomie witryny dotyczą całej lokacji, a nie tylko listy w witrynie). Niestandardowe działanie tworzy kopię zapasową listy anonsów i następnie kopiuje zawartość listy ogłoszeń tę sytuację.  
  
 W tym instruktażu pokazano następujące zagadnienia:  
  
- Tworzenie na poziomie witryny przepływu pracy.  
  
- Tworzenie działań niestandardowych przepływów pracy.  
  
- Tworzenie i usuwanie listy programu SharePoint.  
  
- Kopiuje elementy z jednej listy do innego.  
  
- Wyświetlanie listy na pasku szybkiego uruchamiania.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   Obsługiwane edycje [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] i programu SharePoint.
  
-   Program Visual Studio.  
  
## <a name="create-a-site-workflow-custom-activity-project"></a>Tworzenie projektu niestandardowego działania przepływu pracy witryny
 Najpierw utwórz projekt do przechowywania i przetestować działanie niestandardowego przepływu pracy.  
  
#### <a name="to-create-a-site-workflow-custom-activity-project"></a>Aby utworzyć projekt niestandardowego działania przepływu pracy witryny  
  
1.  Na pasku menu wybierz **pliku** > **New** > **projektu** do wyświetlenia **nowy projekt** okno dialogowe.  
  
2.  Rozwiń **SharePoint** węźle albo **Visual C#** lub **języka Visual Basic**, a następnie wybierz **2010** węzła.  
  
3.  W **szablony** okienku wybierz **projekt programu SharePoint 2010** szablonu.  
  
4.  W **nazwa** wprowadź **AnnouncementBackup**, a następnie wybierz **OK** przycisku.  
  
     **Kreator ustawień niestandardowych SharePoint** pojawia się.  
  
5.  Na **Określanie witryny i poziomu zabezpieczeń dla debugowania** wybierz **Wdróż jako rozwiązanie farmy** przycisk opcji, a następnie wybierz **Zakończ** przycisk, aby zaakceptować Witryna poziom i domyślne zaufanie.  
  
     W tym kroku ustawia poziom zaufania dla rozwiązania jako rozwiązanie farmy, jedyną dostępną opcją w przypadku projektów przepływu pracy.  
  
6.  W **Eksploratora rozwiązań**, wybierz węzeł projektu, a następnie na pasku menu wybierz **projektu** > **Dodaj nowy element**.  
  
7.  W obszarze **Visual C#** lub **języka Visual Basic**, rozwiń węzeł **SharePoint** węzła, a następnie wybierz **2010** węzła.  
  
8.  W **szablony** okienku wybierz **sekwencyjnego przepływu pracy (tylko rozwiązanie farmy)** szablonu, a następnie wybierz **Dodaj** przycisku.  
  
     **Kreator ustawień niestandardowych SharePoint** pojawia się.  
  
9. Na **Określ nazwę przepływu pracy debugowania** strona, zaakceptuj nazwę domyślną (AnnouncementBackup - Workflow1). Zmień typ szablonu przepływu pracy na **przepływ pracy witryny**, a następnie wybierz **dalej** przycisku.  
  
10. Wybierz **Zakończ** przycisk, aby zaakceptować ustawienia domyślne w pozostałych.  
  
## <a name="add-a-custom-workflow-activity-class"></a>Dodaj klasę działanie niestandardowego przepływu pracy
 Następnie należy dodać klasę do projektu, który zawiera kod działanie niestandardowego przepływu pracy.  
  
#### <a name="to-add-a-custom-workflow-activity-class"></a>Aby dodać klasę działanie niestandardowego przepływu pracy  
  
1.  Na pasku menu wybierz **projektu** > **Dodaj nowy element** do wyświetlenia **Dodaj nowy element** okno dialogowe.  
  
2.  W **zainstalowane szablony** widoku drzewa, wybierz polecenie **kodu** węzła, a następnie wybierz **klasy** szablonu na liście szablonów elementów projektów. Użyj domyślnej nazwy Class1. Wybierz **Dodaj** przycisku.  
  
3.  Zastąp cały kod w Class1 następujących czynności:  
  
     [!code-csharp[SP_AnnBackup#1](../sharepoint/codesnippet/CSharp/announcementbackup/class1.cs#1)]
     [!code-vb[SP_AnnBackup#1](../sharepoint/codesnippet/VisualBasic/announcementbackupvb/class1.vb#1)]  
  
4.  Zapisz projekt, a następnie na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**.  
  
     Moduł Class1 jest wyświetlany jako akcję niestandardową w **przybornika** na **składniki AnnouncementBackup** kartę.  
  
## <a name="add-the-custom-activity-to-the-site-workflow"></a>Dodawanie działań niestandardowych do przepływu pracy witryny
 Następnie Dodaj działanie w przepływie pracy zawiera kod niestandardowy.  
  
#### <a name="to-add-a-custom-activity-to-the-site-workflow"></a>Do dodawania działań niestandardowych do przepływu pracy witryny
  
1.  Otwórz Workflow1 w Projektancie przepływu pracy w widoku Projekt.  
  
2.  Przeciągnij Moduł Class1 z **przybornika** tak, aby pojawiło się pod `onWorkflowActivated1` działania lub Otwórz menu skrótów dla klasa1, wybierz **kopiowania**, otwórz menu skrótów dla linii poniżej `onWorkflowActivated1` działanie, a następnie wybierz **Wklej**.  
  
3.  Zapisz projekt.  
  
## <a name="test-the-site-workflow-custom-activity"></a>Testowanie niestandardowego działania przepływu pracy witryny
 Następnie uruchom projekt i uruchomić przepływ pracy witryny. Niestandardowe działanie powoduje utworzenie kopii zapasowej listy anonsów i kopiuje zawartość z bieżącej listy ogłoszeń do niego. Kod sprawdza również, czy istnieje już listy kopii zapasowych przed utworzeniem jeden. Jeśli istnieje już lista kopii zapasowych, został usunięty. Ten kod dodaje także link do nowej listy na pasku Szybkie uruchamianie witryny programu SharePoint.  
  
#### <a name="to-test-the-site-workflow-custom-activity"></a>Aby przetestować niestandardowego działania przepływu pracy witryny  
  
1.  Wybierz **F5** klawisz, aby uruchomić projekt i wdrożyć ją w programie SharePoint.  
  
2.  Na pasku szybkiego uruchamiania wybierz **Wyświetla** łącze, aby wyświetlić wszystkie listy, które są dostępne w witrynie programu SharePoint. Zwróć uwagę, istnieje tylko jedna lista pojawiać ogłoszenia o nazwie **anonsów**.  
  
3.  W górnej części strony sieci Web programu SharePoint wybierz **przepływy pracy witryn** łącza.  
  
4.  W obszarze Start sekcji nowego przepływu pracy, wybierz opcję **AnnouncementBackup - Workflow1** łącza. Spowoduje to uruchomienie przepływu pracy witryny i uruchamia kod w akcji niestandardowej.  
  
5.  Na pasku szybkiego uruchamiania wybierz **kopii zapasowej anonsów** łącza. Należy zauważyć, że wszystkie anonsy, które są zawarte w **anonsów** listy zostały skopiowane do tej nowej listy.  
  
## <a name="see-also"></a>Zobacz także
 [Instrukcje: Tworzenie obsługiwanego odbiornika](../sharepoint/how-to-create-an-event-receiver.md)   
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
