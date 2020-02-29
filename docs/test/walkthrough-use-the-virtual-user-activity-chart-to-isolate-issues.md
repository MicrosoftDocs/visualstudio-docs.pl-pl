---
title: Używanie wykresu aktywności wirtualnego użytkownika dla testów obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual user activity chart
- virtual user activity chart, isolating performance issues
ms.assetid: d1c10fb9-cfeb-4e7f-9991-2d1e1103699e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c58dd4f6e6a0c8fe1bd468053bf18c3635b1ee9d
ms.sourcegitcommit: 1efb6b219ade7c35068b79fbdc573a8771ac608d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78169381"
---
# <a name="walkthrough-using-the-virtual-user-activity-chart-to-isolate-issues"></a>Przewodnik: używanie wykresu aktywności wirtualnego użytkownika w celu wyizolowania problemów

W tym instruktażu dowiesz się, jak za pomocą wykresu aktywności wirtualnego użytkownika wyizolować błędy, które wystąpiły dla indywidualnych użytkowników wirtualnych, którzy uruchomili test obciążenia.

Wykres aktywności wirtualnego użytkownika umożliwia wizualizację aktywności wirtualnego użytkownika, która jest skojarzona z testem obciążenia. Każdy wiersz na wykresie reprezentuje poszczególnych użytkowników wirtualnych. Wykres aktywność użytkownika wirtualnego pokazuje, jak dokładnie każdy użytkownik wirtualny był wykonywany podczas testu. Dzięki temu można izolować problemy z wydajnością, sprawdzając wzorce aktywności użytkownika, wzorce obciążenia, skorelować Niepowodzenie lub powolne testy, a także żądania z innymi wirtualnymi działaniami użytkowników. Wykres aktywności wirtualnego użytkownika jest dostępny dopiero po zakończeniu ładowania po rozpoczęciu pracy.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="prerequisites"></a>Wymagania wstępne

- Visual Studio Enterprise

- Wykonaj następujące procedury:

  - [Rejestrowanie i uruchamianie testu wydajności sieci Web](/azure/devops/test/load-test/run-performance-tests-app-before-release#recordtests).

  - [Utwórz i uruchom test obciążenia](/azure/devops/test/load-test/run-performance-tests-app-before-release#create-a-load-test)

## <a name="open-the-colorwebapp-solution-created-in-the-previous-walkthroughs"></a>Otwórz rozwiązanie ColorWebApp utworzone w poprzednich przewodnikach

1. Otwórz program Visual Studio.

2. Otwórz rozwiązanie **ColorWebApp** , które zawiera *LoadTest1. LoadTest*. Ten test obciążenia wynika z przeprowadzenia kroków z trzech instruktaży wymienionych na początku tego tematu w sekcji wymagania wstępne.

     W pozostałych krokach w tym instruktażu przyjęto założenie, że aplikacja sieci Web o nazwie ColorWebApp, test wydajności sieci Web o nazwie *ColorWebAppTest. webtest* i test obciążenia o nazwie *LoadTest1. LoadTest*.

## <a name="run-the-load-test"></a>Uruchom test obciążenia

Uruchom test obciążenia, aby zebrać dane aktywności wirtualnego użytkownika.

- W **Edytor testu obciążeniowego**wybierz przycisk **Uruchom** na pasku narzędzi. LoadTest1 zaczyna działać.

## <a name="isolate-issues-in-the-virtual-user-activity-chart"></a>Izolowanie problemów na wykresie aktywności wirtualnego użytkownika

Po uruchomieniu testu obciążenia i zebraniu danych o aktywności użytkownika wirtualnego można wyświetlić dane w wynikach testu obciążenia, korzystając z widoku szczegółów **analizatora testu obciążenia** na **wykresie aktywności wirtualnego użytkownika**. Ponadto można użyć **wykresu aktywności wirtualnego użytkownika** , aby ułatwić wyizolowanie problemów z wydajnością w teście obciążenia.

### <a name="to-use-the-virtual-user-activity-chart-in-your-load-test-results"></a>Aby użyć wykresu aktywności wirtualnego użytkownika w wynikach testu obciążenia

1. Po zakończeniu testu obciążenia strona **Podsumowanie** wyników testu obciążenia jest wyświetlana w **analizatorze testu obciążenia**. Wybierz przycisk **wykresy** na pasku narzędzi.

     Zostanie wyświetlony widok wykresy.

2. Na wykresie **czasu odpowiedzi na stronie** kliknij prawym przyciskiem myszy obok jednej z ikon naruszenia progu, a następnie wybierz pozycję **Przejdź do szczegółów użytkownika**.

    > [!NOTE]
    > Możesz użyć przycisku **szczegóły** na pasku narzędzi **Edytor testu obciążeniowego** , aby otworzyć również wykres aktywności użytkownika. Jeśli jednak używasz opcji **Przejdź do szczegółów użytkownika** , **Wykres aktywności wirtualnego użytkownika** będzie automatycznie powiększał się na części testu, który został kliknięty prawym przyciskiem myszy na wykresie.

     Widok szczegółów jest wyświetlany z **wykresem aktywność użytkownika wirtualnego** , który jest ukierunkowany na czas, w którym wystąpiły naruszenia progu.

     Na osi y poziome wykresy reprezentują poszczególnych użytkowników wirtualnych. Oś x wyświetla wiersz czasu dla przebiegu testu obciążenia.

3. W narzędziu **Powiększ do okresu** poniżej **wykresu aktywności wirtualnego użytkownika**Dostosuj suwaki w lewo i w prawo do momentu, aż oba zostaną zamknięte ikonie naruszenie progu. Spowoduje to zmianę skali czasu na **wykresie aktywności wirtualnego użytkownika**

4. W **legendzie szczegółów**zaznacz pole wyboru **(Wyróżnij błędy)** . Należy zauważyć, że wyróżniono użytkownika wirtualnego, który spowodował naruszenie progu.

5. W panelu **wyników filtru** wyczyść pola wyboru dla opcji **Pokaż udane wyniki** i **HttpError** , ale pozostaw zaznaczone pole wyboru **ValidationRuleError** .

     Na **wykresie aktywności wirtualnego użytkownika** są wyświetlane tylko użytkownicy wirtualną, którzy wykorzystali więcej niż 3 sekundy na stronie *Red. aspx* , zgodnie z naruszeniem progu skonfigurowanym w poprzednim instruktażu.

6. Umieść wskaźnik myszy nad linią poziomą, która reprezentuje użytkownika wirtualnego z błędem reguły walidacji dla naruszenia progu.

7. Zostanie wyświetlona etykietka narzędzia z następującymi informacjami:

    - **Identyfikator użytkownika**

    - **Scenariusz**

    - **Test**

    - **Wynikiem**

    - **Sieć**

    - **Godzina rozpoczęcia**

    - **Trwania**

    - **Agent**

    - **Dziennik testu**

8. Zwróć uwagę, że **dziennik testu** jest łączem. Wybierz łącze **dziennik testu** .

9. Test wydajności sieci Web ColorWebTest skojarzony z dziennikiem zostanie otwarty w **przeglądarce wyniki testów wydajności sieci Web**. Pozwala to izolować miejsce wystąpienia naruszeń progowych.

     Aby ułatwić izolowanie problemów z wydajnością oraz błędy w testach obciążenia, można użyć różnych ustawień zarówno w **legendzie szczegółów** , jak i w panelu **wyników filtrowania** . Eksperymentuj z tymi ustawieniami oraz narzędziem **Powiększ do okresu** , aby zobaczyć, jak dane użytkownika wirtualnego są prezentowane na **wykresie aktywności wirtualnego użytkownika**.

## <a name="see-also"></a>Zobacz też

- [Analizowanie aktywności wirtualnego użytkownika w widoku szczegółów](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)
- [Instrukcje: Tworzenie ustawień testowych dla testu obciążenia rozłożonego](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)
- [Zbieranie informacji diagnostycznych za pomocą ustawień testu](../test/collect-diagnostic-information-using-test-settings.md)
