---
title: 'Przewodnik: Dodawanie odbiorników zdarzeń funkcji | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, advanced packaging tools
- SharePoint development in Visual Studio, event receivers
- SharePoint development in Visual Studio, feature event receivers
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f40358c157ec24557947f36b0c6eadb6d8a2622d
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015357"
---
# <a name="walkthrough-add-feature-event-receivers"></a>Przewodnik: dodawanie odbiorców zdarzeń funkcji
  Odbiorcy zdarzeń funkcji to metody, które są wykonywane po wystąpieniu jednego z następujących zdarzeń związanych z funkcjami w programie SharePoint:

- Zainstalowana jest funkcja.

- Funkcja jest aktywowana.

- Funkcja została zdezaktywowana.

- Funkcja jest usuwana.

  W tym instruktażu pokazano, jak dodać odbiorcę zdarzeń do funkcji w projekcie programu SharePoint. Przedstawiono w nim następujące zadania:

- Tworzenie pustego projektu z odbiorcą zdarzeń funkcji.

- Obsługa metody **FeatureDeactivating** .

- Za pomocą modelu obiektów projektu programu SharePoint do dodania anonsu do listy anonsów.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Obsługiwane wersje systemu Microsoft Windows i programu SharePoint.

- Program Visual Studio.

## <a name="create-a-feature-event-receiver-project"></a>Utwórz projekt odbiorcy zdarzeń funkcji
 Najpierw utwórz projekt, aby zawierał odbiorcę zdarzeń funkcji.

#### <a name="to-create-a-project-with-a-feature-event-receiver"></a>Aby utworzyć projekt z odbiorcą zdarzeń funkcji

1. Na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt** , aby wyświetlić okno dialogowe **Nowy projekt** .

2. Rozwiń węzeł **SharePoint** w **Visual C#** lub **Visual Basic**, a następnie wybierz węzeł **2010** .

3. W okienku **Szablony** wybierz szablon **projektu programu SharePoint 2010** .

     Ten typ projektu jest używany dla odbiorników zdarzeń funkcji, ponieważ nie mają szablonu projektu.

4. W polu **Nazwa** wprowadź **FeatureEvtTest**, a następnie wybierz przycisk **OK** , aby wyświetlić **Kreatora dostosowania programu SharePoint**.

5. Na stronie **Określanie poziomu lokacji i zabezpieczeń na potrzeby debugowania** wprowadź adres URL witryny programu SharePoint Server, do której chcesz dodać nowy element pola niestandardowego, lub Użyj domyślnej lokalizacji (http:// \<*system name*> /).

6. W sekcji **co to jest poziom zaufania dla tego rozwiązania programu SharePoint?** wybierz przycisk opcji **Wdróż jako farmę** .

     Aby uzyskać więcej informacji o rozwiązaniach w trybie piaskownicy a rozwiązaniach farmy, zobacz [zagadnienia dotyczące rozwiązania w trybie piaskownicy](../sharepoint/sandboxed-solution-considerations.md).

7. Wybierz przycisk **Zakończ** , a następnie Zwróć uwagę, że funkcja o nazwie Feature1 pojawia się w węźle **funkcje** .

## <a name="add-an-event-receiver-to-the-feature"></a>Dodawanie odbiorcy zdarzeń do funkcji
 Następnie dodaj odbiorcę zdarzeń do funkcji i Dodaj kod, który jest wykonywany, gdy funkcja zostanie zdezaktywowana.

#### <a name="to-add-an-event-receiver-to-the-feature"></a>Aby dodać odbiorcę zdarzeń do funkcji

1. Otwórz menu skrótów dla węzła funkcje, a następnie wybierz polecenie **Dodaj funkcję** , aby utworzyć funkcję.

2. W węźle **funkcje** Otwórz menu skrótów dla **Feature1**, a następnie wybierz polecenie **Dodaj odbiorcę zdarzeń** , aby dodać do funkcji odbiorcę zdarzeń.

     Spowoduje to dodanie pliku kodu w obszarze Feature1. W tym przypadku jest to nazwa *Feature1.EventReceiver.cs* lub *Feature1. EventReceiver. vb*, w zależności od języka deweloperskiego projektu.

3. Jeśli projekt jest zapisany [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] , Dodaj poniższy kod u góry odbiorcy zdarzeń, jeśli jeszcze nie istnieje:

     [!code-csharp[SP_FeatureEvt#1](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#1)]

4. Klasa odbiorcy zdarzeń zawiera kilka metod z komentarzem, które działają jako zdarzenia. Zastąp metodę **FeatureDeactivating** poniższymi:

     [!code-vb[SP_FeatureEvt#2](../sharepoint/codesnippet/VisualBasic/featureevt2vb/features/feature1/feature1.eventreceiver.vb#2)]
     [!code-csharp[SP_FeatureEvt#2](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#2)]

## <a name="test-the-feature-event-receiver"></a>Testowanie odbiorcy zdarzeń funkcji
 Następnie Dezaktywuj funkcję, aby sprawdzić, czy metoda **FeatureDeactivating** wyprowadza anons na listę anonsów programu SharePoint.

#### <a name="to-test-the-feature-event-receiver"></a>Aby przetestować odbiorcę zdarzeń funkcji

1. Ustaw wartość właściwości **Konfiguracja aktywnego wdrożenia** projektu na **Brak aktywacji**.

     Ustawienie tej właściwości uniemożliwia Aktywowanie funkcji w programie SharePoint i umożliwia debugowanie odbiorników zdarzeń funkcji. Aby uzyskać więcej informacji, zobacz [Debugowanie rozwiązań programu SharePoint](../sharepoint/debugging-sharepoint-solutions.md).

2. Wybierz klawisz **F5** , aby uruchomić projekt i wdrożyć go w programie SharePoint.

3. W górnej części strony sieci Web programu SharePoint otwórz menu **Akcje witryny** , a następnie wybierz pozycję **Ustawienia lokacji**.

4. W sekcji **Akcje witryny** na stronie **Ustawienia witryny** wybierz łącze **Zarządzaj funkcjami lokacji** .

5. Na stronie **funkcje** wybierz przycisk **Aktywuj** obok funkcji **FeatureEvtTest Feature1** .

6. Na stronie **funkcje** wybierz przycisk **Dezaktywuj** obok funkcji **FeatureEvtTest Feature1** , a następnie wybierz link **Dezaktywuj tę funkcję** , aby dezaktywować tę funkcję.

7. Wybierz przycisk **Strona główna** .

     Zwróć uwagę, że anons pojawia się na liście **Anonsy** Po zdezaktywowaniu funkcji.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie odbiorcy zdarzeń](../sharepoint/how-to-create-an-event-receiver.md)
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)