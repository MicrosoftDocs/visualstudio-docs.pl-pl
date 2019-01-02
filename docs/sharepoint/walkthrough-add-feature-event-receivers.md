---
title: 'Przewodnik: Dodawanie odbiorców zdarzeń funkcji | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, advanced packaging tools
- SharePoint development in Visual Studio, event receivers
- SharePoint development in Visual Studio, feature event receivers
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b7e3471329c6ea798d9d86c594baec2e33815524
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53853337"
---
# <a name="walkthrough-add-feature-event-receivers"></a>Przewodnik: Dodawanie odbiorców zdarzeń funkcji
  Funkcji odbiorcy zdarzeń są metodami wykonywanymi gdy wystąpi jedno z następujących zdarzeń związanych z funkcji w programie SharePoint:

- Funkcja zostanie zainstalowana.

- Funkcja jest aktywowana.

- Dezaktywacją funkcji.

- Funkcja zostanie usunięta.

  W tym instruktażu przedstawiono sposób dodawania odbiorców zdarzenia do funkcji w projekcie programu SharePoint. Pokazuje następujące zadania:

- Tworzenie pustego projektu za pomocą odbiorcy zdarzeń funkcji.

- Obsługa **FeatureDeactivating** metody.

- Dodawanie anonsu do listy anonsów przy użyciu modelu obiektu projektu programu SharePoint.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

-   Obsługiwane wersje systemu Microsoft Windows i programu SharePoint.

-   Program Visual Studio.

## <a name="create-a-feature-event-receiver-project"></a>Tworzenie projektu funkcji odbiorcy zdarzeń
 Najpierw utwórz projekt, który zawiera odbiorcę zdarzeń funkcji.

#### <a name="to-create-a-project-with-a-feature-event-receiver"></a>Aby utworzyć projekt za pomocą odbiorcy zdarzeń funkcji

1.  Na pasku menu wybierz **pliku** > **New** > **projektu** do wyświetlenia **nowy projekt** okno dialogowe.

2.  Rozwiń **SharePoint** węźle albo **Visual C#** lub **języka Visual Basic**, a następnie wybierz **2010** węzła.

3.  W **szablony** okienku wybierz **projekt programu SharePoint 2010** szablonu.

     Użyjesz tego typu projektu dla odbiorców zdarzeń funkcji, ponieważ mają one nie szablonu projektu.

4.  W **nazwa** wprowadź **FeatureEvtTest**, a następnie wybierz **OK** przycisk, aby wyświetlić **Kreator ustawień niestandardowych SharePoint**.

5.  Na **Określanie witryny i poziomu zabezpieczeń dla debugowania** strony, wprowadź adres URL witryny serwera programu SharePoint, do której chcesz dodać nowy element pole niestandardowe lub użyj domyślnej lokalizacji (http://\<*systemu Nazwa*> /).

6.  W **co to jest poziom zaufania dla tego rozwiązania programu SharePoint?** wybierz pozycję **Wdróż jako rozwiązanie farmy** przycisku opcji.

     Aby uzyskać więcej informacji dotyczących rozwiązań sandbox w porównaniu z rozwiązaniami farmy, zobacz [uwagi dotyczące rozwiązania typu piaskownica](../sharepoint/sandboxed-solution-considerations.md).

7.  Wybierz **Zakończ** przycisk, a następnie zwróć uwagę, że funkcja, która nosi nazwę Feature1 pojawia się w obszarze **funkcji** węzła.

## <a name="add-an-event-receiver-to-the-feature"></a>Dodaj odbiorcę zdarzeń funkcji
 Następnie dodaj odbiorcę zdarzeń funkcji i Dodaj kod, który jest wykonywany po dezaktywowaniu tej funkcji.

#### <a name="to-add-an-event-receiver-to-the-feature"></a>Aby dodać odbiorcę zdarzeń funkcji

1.  Otwórz menu skrótów dla węzła funkcji, a następnie wybierz **Dodaj funkcję** Aby utworzyć funkcję.

2.  W obszarze **funkcji** węzła, otwórz menu skrótów dla **Feature1**, a następnie wybierz **Dodaj odbiorcę zdarzeń** do dodawania odbiorców zdarzenia dla funkcji.

     Spowoduje to dodanie pliku z kodem w ramach Feature1. W tym przypadku jest on nazwany albo *Feature1.EventReceiver.cs* lub *Feature1.EventReceiver.vb*, w zależności od języka programowania Twojego projektu.

3.  Jeśli projekt został napisany w [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)], Dodaj następujący kod w górnej części odbiorcy zdarzeń, jeśli nie jest już istnieje:

     [!code-csharp[SP_FeatureEvt#1](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#1)]

4.  Klasy odbiorcy zdarzeń zawiera kilka metod zakomentowany, które działają jako wydarzenia. Zastąp **FeatureDeactivating** metoda następującym kodem:

     [!code-vb[SP_FeatureEvt#2](../sharepoint/codesnippet/VisualBasic/featureevt2vb/features/feature1/feature1.eventreceiver.vb#2)]
     [!code-csharp[SP_FeatureEvt#2](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#2)]

## <a name="test-the-feature-event-receiver"></a>Testowanie funkcji odbiorcy zdarzeń
 Następnie zdezaktywować funkcję do testowania czy **FeatureDeactivating** metoda generuje powiadomienia na liście programu SharePoint anonsów.

#### <a name="to-test-the-feature-event-receiver"></a>Aby przetestować odbiorcę zdarzeń funkcji

1.  Ustaw wartość projektu **aktywnej konfiguracji wdrożenia** właściwości **aktywacji nie**.

     Ustawienie tej właściwości zapobiega funkcji aktywacji w programie SharePoint i umożliwia debugowanie odbiorców zdarzeń funkcji. Aby uzyskać więcej informacji, zobacz [rozwiązań SharePoint debugowania](../sharepoint/debugging-sharepoint-solutions.md).

2.  Wybierz **F5** klawisz, aby uruchomić projekt i wdrożyć ją w programie SharePoint.

3.  W górnej części strony sieci Web programu SharePoint, należy otworzyć **Akcje witryny** menu, a następnie wybierz **ustawienia lokacji**.

4.  W obszarze **Akcje witryny** części **ustawienia lokacji** wybierz **Zarządzanie funkcjami witryny** łącza.

5.  Na **funkcji** wybierz **Aktywuj** znajdujący się obok **FeatureEvtTest Feature1** funkcji.

6.  Na **funkcji** wybierz **Dezaktywuj** znajdujący się obok **FeatureEvtTest Feature1** funkcji, a następnie wybierz **Dezaktywuj tę funkcję**  potwierdzenie link, aby zdezaktywować funkcję.

7.  Wybierz **Home** przycisku.

     Należy zauważyć, że anons pojawi się w **anonsów** listę po dezaktywowaniu tej funkcji.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie obsługiwanego odbiornika](../sharepoint/how-to-create-an-event-receiver.md)
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)