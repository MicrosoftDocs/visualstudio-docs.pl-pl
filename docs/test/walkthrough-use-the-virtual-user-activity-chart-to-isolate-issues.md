---
title: Używanie wykresu aktywności użytkownika wirtualnego do testów obciążenia
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "78169381"
---
# <a name="walkthrough-using-the-virtual-user-activity-chart-to-isolate-issues"></a>Przewodnik: Używanie wykresu aktywności użytkownika wirtualnego do izolowania problemów

W tym instruktażu dowiesz się, jak używać wykresu aktywności użytkownika wirtualnego do izolowania błędów, które wystąpiły dla poszczególnych użytkowników wirtualnych, którzy uruchomili test obciążenia.

Wykres aktywności użytkownika wirtualnego umożliwia wizualizację aktywności użytkownika wirtualnego skojarzonego z testem obciążenia. Każdy wiersz na wykresie reprezentuje indywidualnego użytkownika wirtualnego. Wykres aktywności użytkownika wirtualnego pokazuje dokładnie to, co każdy użytkownik wirtualny był wykonywany podczas testu. Dzięki temu można wyizolować problemy z wydajnością, widząc wzorce aktywności użytkownika, wzorce obciążenia, skorelować testy nie powiodło się lub powolne i zobaczyć żądania z inną aktywnością użytkownika wirtualnego. Wykres aktywności użytkownika wirtualnego jest dostępny tylko po zakończeniu uruchamiania obciążenia.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="prerequisites"></a>Wymagania wstępne

- Visual Studio Enterprise

- Wykonaj następujące procedury:

  - [Nagraj i uruchom test wydajności sieci](/azure/devops/test/load-test/run-performance-tests-app-before-release#recordtests).

  - [Tworzenie i uruchamianie testów obciążeniowych](/azure/devops/test/load-test/run-performance-tests-app-before-release#create-a-load-test)

## <a name="open-the-colorwebapp-solution-created-in-the-previous-walkthroughs"></a>Otwórz rozwiązanie ColorWebApp utworzone w poprzednich instruktażach

1. Otwórz program Visual Studio.

2. Otwórz rozwiązanie **ColorWebApp,** które zawiera *loadtest1.loadtest*. Ten test obciążenia wynika z przeprowadzenia kroków w trzech instruktaże, które są wymienione na początku tego tematu w sekcji wymagania wstępne.

     Pozostałe kroki w tym instruktażu zakładają aplikację sieci web o nazwie ColorWebApp, test wydajności sieci web o nazwie *ColorWebAppTest.webtest* i test obciążenia o nazwie *LoadTest1.loadtest*.

## <a name="run-the-load-test"></a>Uruchom test obciążenia

Uruchom test obciążenia, aby zebrać dane aktywności użytkownika wirtualnego.

- W **Edytorze testów obciążenia**wybierz przycisk **Uruchom** na pasku narzędzi. LoadTest1 zaczyna działać.

## <a name="isolate-issues-in-the-virtual-user-activity-chart"></a>Wyizolowanie problemów na wykresie aktywności użytkownika wirtualnego

Po uruchomieniu testu obciążenia i zebraniu danych aktywności użytkownika wirtualnego można wyświetlić dane w wynikach testu obciążenia przy użyciu widoku Szczegóły **analizatora testów obciążenia** w **tabeli aktywności użytkownika wirtualnego**. Ponadto można użyć **wykresu aktywności użytkownika wirtualnego,** aby ułatwić wyizolowanie problemów z wydajnością w teście obciążenia.

### <a name="to-use-the-virtual-user-activity-chart-in-your-load-test-results"></a>Aby użyć wykresu aktywności użytkownika wirtualnego w wynikach testu obciążenia

1. Po zakończeniu testu obciążenia w **analizatorze testu obciążenia**zostanie wyświetlona strona **Podsumowanie** wyników testu obciążenia. Wybierz przycisk **Wykresy** na pasku narzędzi.

     Zostanie wyświetlony widok Wykresy.

2. Na wykresie **Czas reakcji strony** kliknij prawym przyciskiem myszy jedną z ikon naruszenia progu i wybierz pozycję Przejdź do szczegółów **użytkownika**.

    > [!NOTE]
    > Przycisk **Szczegóły** można użyć na pasku narzędzi **Edytora testów obciążenia,** aby otworzyć również wykres aktywności użytkownika. Jeśli jednak użyjesz opcji **Przejdź do szczegółów użytkownika,** **wykres aktywności użytkownika wirtualnego** automatycznie powiększy część testu, którą kliknięno prawym przyciskiem myszy na wykresie.

     Widok Szczegóły jest wyświetlany z **wykresem aktywności użytkownika wirtualnego** skoncentrowanym na okresie, w którym wystąpiły naruszenia progu.

     Na osi y wykresy poziome reprezentują poszczególnych użytkowników wirtualnych. Oś x wyświetla linię czasu dla przebiegu testu obciążenia.

3. W narzędziu **Powiększenie do okresu poniżej** **wykresu aktywności użytkownika wirtualnego**dostosuj suwaki do lewej i prawej strony, aż oba będą zbliżone do ikony naruszenia progu. Spowoduje to zmianę skali czasu na **wykresie aktywności użytkownika wirtualnego**

4. W legendzie **szczegółów**zaznacz pole wyboru **(Wyróżnij błędy).** Należy zauważyć, że użytkownik wirtualny, który spowodował naruszenie progu jest wyróżniony.

5. W panelu **Wyniki filtru** wyczyść pola wyboru **Pokaż pomyślne wyniki** i **HttpError,** ale pozostaw zaznaczone pole wyboru **ValidationRuleError.**

     **Na wykresie aktywności użytkownika wirtualnego** są wyświetlane tylko użytkownicy wirtualni, którzy spędzili więcej niż 3 sekundy na stronie *Red.aspx,* zgodnie z zasadą naruszenia progu skonfigurowaną w poprzednim instruktażu.

6. Umieść wskaźnik myszy na linii poziomej, która reprezentuje użytkownika wirtualnego z błędem reguły sprawdzania poprawności dla naruszenia progu.

7. Zostanie wyświetlona etykietka narzędzia z następującymi informacjami:

    - **Identyfikator użytkownika**

    - **Scenariusz**

    - **Test**

    - **Wynik**

    - **Sieć**

    - **Godzina rozpoczęcia**

    - **Czas trwania**

    - **Agent**

    - **Dziennik testów**

8. Należy zauważyć, że **dziennik testu** jest łącze. Wybierz **łącze Dziennika testowego.**

9. Test wydajności sieci Web ColorWebTest skojarzony z dziennikiem zostanie otwarty w **przeglądarce wyników testów wydajności sieci Web.** Dzięki temu można wyizolować, gdzie wystąpiły naruszenia progu.

     Można użyć różnych ustawień w panelach **Legenda szczegółów** i **Filtr wyników,** aby pomóc w izolowaniu problemów z wydajnością i błędów w testach obciążenia. Poeksperymentuj z tymi ustawieniami i narzędziem **Okres powiększenia, aby** zobaczyć, jak dane wirtualnego użytkownika są prezentowane na **wykresie aktywności użytkownika wirtualnego**.

## <a name="see-also"></a>Zobacz też

- [Analizowanie aktywności użytkownika wirtualnego w widoku Szczegóły](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)
- [Jak: Tworzenie ustawienia testu dla testu obciążenia rozproszonego](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)
- [Zbieranie informacji diagnostycznych przy użyciu ustawień testu](../test/collect-diagnostic-information-using-test-settings.md)
