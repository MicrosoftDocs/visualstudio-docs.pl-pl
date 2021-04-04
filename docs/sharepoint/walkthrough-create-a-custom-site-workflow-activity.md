---
title: 'Przewodnik: Tworzenie niestandardowego działania przepływu pracy witryny | Microsoft Docs'
description: W tym instruktażu zapoznaj się z tematem jak utworzyć niestandardowe działanie dla przepływu pracy programu SharePoint na poziomie witryny przy użyciu programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 29a3cd6fe37ec824a3db3a2c83aad7434d0018cb
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106218051"
---
# <a name="walkthrough-create-a-custom-site-workflow-activity"></a>Przewodnik: Tworzenie niestandardowego działania przepływu pracy witryny
  W tym instruktażu pokazano, jak utworzyć niestandardowe działanie dla przepływu pracy na poziomie witryny przy użyciu programu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . (Przepływy pracy na poziomie witryny mają zastosowanie do całej lokacji, a nie tylko na liście w witrynie). Działanie niestandardowe tworzy listę anonsów kopii zapasowych, a następnie kopiuje do niej zawartość listy anonsów.

 W tym instruktażu przedstawiono następujące zadania:

- Tworzenie przepływu pracy na poziomie witryny.

- Tworzenie niestandardowego działania przepływu pracy.

- Tworzenie i usuwanie listy programu SharePoint.

- Kopiowanie elementów z jednej listy do innej.

- Wyświetlanie listy na pasku szybkiego uruchamiania.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Obsługiwane wersje programów [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] i SharePoint.

- Programu Visual Studio.

## <a name="create-a-site-workflow-custom-activity-project"></a>Tworzenie projektu niestandardowego działania przepływu pracy witryny
 Najpierw utwórz projekt, aby wstrzymać i przetestować działanie niestandardowego przepływu pracy.

#### <a name="to-create-a-site-workflow-custom-activity-project"></a>Aby utworzyć projekt niestandardowego działania przepływu pracy witryny

1. Na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt** , aby wyświetlić okno dialogowe **Nowy projekt** .

2. Rozwiń węzeł **SharePoint** w **Visual C#** lub **Visual Basic**, a następnie wybierz węzeł **2010** .

3. W okienku **Szablony** wybierz szablon **projektu programu SharePoint 2010** .

4. W polu **Nazwa** wprowadź **AnnouncementBackup**, a następnie wybierz przycisk **OK** .

     Zostanie wyświetlony **Kreator dostosowania programu SharePoint** .

5. Na stronie **Określanie poziomu lokacji i zabezpieczeń na potrzeby debugowania** wybierz przycisk opcji **Wdróż jako farmę** , a następnie wybierz przycisk **Zakończ** , aby zaakceptować poziom zaufania i domyślną lokację.

     Ten krok powoduje ustawienie poziomu zaufania dla rozwiązania jako rozwiązania farmy — jedynej dostępnej opcji dla projektów przepływu pracy.

6. W **Eksplorator rozwiązań** wybierz węzeł projektu, a następnie na pasku menu wybierz **projekt**  >  **Dodaj nowy element**.

7. W obszarze **Visual C#** lub **Visual Basic** rozwiń węzeł **SharePoint** , a następnie wybierz węzeł **2010** .

8. W okienku **Szablony** wybierz szablon **sekwencyjny przepływ pracy (tylko rozwiązanie farmy)** , a następnie wybierz przycisk **Dodaj** .

     Zostanie wyświetlony **Kreator dostosowania programu SharePoint** .

9. Na stronie **Określanie nazwy przepływu pracy na potrzeby debugowania** Zaakceptuj nazwę domyślną (AnnouncementBackup-Workflow1). Zmień typ szablonu przepływu pracy na **przepływ pracy witryny**, a następnie wybierz przycisk **dalej** .

10. Wybierz przycisk **Zakończ** , aby zaakceptować pozostałe ustawienia domyślne.

## <a name="add-a-custom-workflow-activity-class"></a>Dodaj niestandardową klasę działań przepływu pracy
 Następnie Dodaj klasę do projektu, aby zawierała kod dla niestandardowego działania przepływu pracy.

#### <a name="to-add-a-custom-workflow-activity-class"></a>Aby dodać niestandardową klasę działań przepływu pracy

1. Na pasku menu wybierz **projekt**  >  **Dodaj nowy element** , aby wyświetlić okno dialogowe **Dodaj nowy element** .

2. W widoku drzewa **zainstalowanych szablonów** wybierz węzeł **kod** , a następnie wybierz szablon **klasy** z listy szablonów elementów projektu. Użyj nazwy domyślnej Class1. Wybierz przycisk **Dodaj**.

3. Zastąp cały kod w Class1 następującym:

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/announcementbackup/class1.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/announcementbackupvb/class1.vb" id="Snippet1":::

4. Zapisz projekt, a następnie na pasku menu wybierz opcję **Kompiluj**  >  **kompilację rozwiązania**.

     Class1 pojawia się jako akcja niestandardowa w **przyborniku** na karcie **składniki AnnouncementBackup** .

## <a name="add-the-custom-activity-to-the-site-workflow"></a>Dodawanie działania niestandardowego do przepływu pracy lokacji
 Następnie Dodaj działanie do przepływu pracy, aby zawierać kod niestandardowy.

#### <a name="to-add-a-custom-activity-to-the-site-workflow"></a>Aby dodać działanie niestandardowe do przepływu pracy lokacji

1. Otwórz Workflow1 w Projektancie przepływu pracy w widoku projektu.

2. Przeciągnij Class1 z **przybornika** , tak aby pojawił się w obszarze `onWorkflowActivated1` działania, lub Otwórz menu skrótów dla Class1, wybierz **Kopiuj**, otwórz menu skrótów dla wiersza pod `onWorkflowActivated1` działaniem, a następnie wybierz **Wklej**.

3. Zapisz projekt.

## <a name="test-the-site-workflow-custom-activity"></a>Testowanie działania niestandardowego przepływu pracy witryny
 Następnie Uruchom projekt i Uruchom przepływ pracy witryny. Działanie niestandardowe tworzy listę anonsów kopii zapasowych i kopiuje zawartość z listy bieżących anonsów do niej. Kod sprawdza również, czy istnieje już lista kopii zapasowych przed jej utworzeniem. Jeśli lista kopii zapasowych już istnieje, zostanie usunięta. Kod dodaje również link do nowej listy na pasku szybkiego uruchamiania witryny programu SharePoint.

#### <a name="to-test-the-site-workflow-custom-activity"></a>Aby przetestować działanie niestandardowe przepływu pracy witryny

1. Wybierz klawisz **F5** , aby uruchomić projekt i wdrożyć go w programie SharePoint.

2. Na pasku szybkiego uruchamiania wybierz link **listy** , aby wyświetlić wszystkie listy, które są dostępne w witrynie programu SharePoint. Należy zauważyć, że dla anonsów o nazwie **Anonsy** jest tylko jedna lista.

3. W górnej części strony sieci Web programu SharePoint wybierz łącze **przepływy pracy witryny** .

4. W sekcji Rozpocznij nowy przepływ pracy wybierz łącze **AnnouncementBackup-Workflow1** . Spowoduje to uruchomienie przepływu pracy lokacji i uruchomienie kodu w akcji niestandardowej.

5. Na pasku szybkiego uruchamiania wybierz łącze **anonse kopii zapasowej** . Zwróć uwagę, że wszystkie anonse zawarte na liście **anonsów** zostały skopiowane na tę nową listę.

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Tworzenie odbiorcy zdarzeń](../sharepoint/how-to-create-an-event-receiver.md)
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
