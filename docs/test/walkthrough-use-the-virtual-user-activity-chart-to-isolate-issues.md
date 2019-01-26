---
title: W przypadku testów obciążenia za pomocą wykresu wirtualnego aktywności użytkownika
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual user activity chart
- virtual user activity chart, isolating performance issues
ms.assetid: d1c10fb9-cfeb-4e7f-9991-2d1e1103699e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.openlocfilehash: 7f7740e369ca3572a15a916b978c4de28d6593a5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55019388"
---
# <a name="walkthrough-using-the-virtual-user-activity-chart-to-isolate-issues"></a>Przewodnik: Za pomocą wykresu wirtualnego aktywności użytkownika umożliwiającego Wyizolowanie problemów

W tym przewodniku dowiesz się, jak izolowania błędów, które wystąpiły dla poszczególnych użytkowników wirtualnych, które uruchomiono testu obciążenia za pomocą wykresu wirtualnego aktywności użytkownika.

Wykres aktywności wirtualnych użytkowników umożliwia wizualizowanie aktywności wirtualnego użytkownika, który jest skojarzony z testu obciążenia. Każdy wiersz na wykresie reprezentuje poszczególnych użytkowników wirtualnych. Wykres aktywności wirtualnych użytkowników zawiera dokładnie co każdy użytkownik wirtualny był wykonywany podczas testu. Dzięki temu można wyizolować problemy z wydajnością, obserwując wzorce aktywności użytkowników, wzorce obciążenia, korelowanie testy zakończone niepowodzeniem lub wolne i zobacz żądań z innych działań wirtualnego użytkownika. Wykres aktywności wirtualnych użytkowników jest dostępna tylko po załadowaniu po zakończeniu wykonywania.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="prerequisites"></a>Wymagania wstępne

-   Visual Studio Enterprise

-   Wykonaj następujące procedury:

    -   [Rejestrowanie i uruchamianie testu wydajności sieci web](/azure/devops/test/load-test/run-performance-tests-app-before-release#recordtests).

    -   [Tworzenie i uruchamianie testu obciążenia](/azure/devops/test/load-test/run-performance-tests-app-before-release#create-a-load-test)

## <a name="open-the-colorwebapp-solution-created-in-the-previous-walkthroughs"></a>Otwórz rozwiązanie ColorWebApp utworzony w poprzednich — wskazówki

1.  Uruchom program Visual Studio.

2.  Otwórz **ColorWebApp** rozwiązanie, które zawiera *testy LoadTest1.loadtest*. Obciążenie wyniki testów z czynności w trzech instruktażach wymienionych na początku tego tematu, w sekcji wymagania wstępne.

     Pozostałe kroki w tym przewodniku zakładają aplikację sieci web o nazwie ColorWebApp, test wydajności sieci web o nazwie *ColorWebAppTest.webtest* i obciążenia, test o nazwie *testy LoadTest1.loadtest*.

## <a name="run-the-load-test"></a>Uruchom test obciążenia

Uruchom test obciążeniowy, aby zbierać dane o aktywności użytkownika wirtualnego.

-   W **edytora testu obciążenia**, wybierz **Uruchom** przycisk na pasku narzędzi. LoadTest1 zaczyna być uruchamiana.

## <a name="isolate-issues-in-the-virtual-user-activity-chart"></a>Wyizolować problemy z wykres aktywności wirtualnych użytkowników

Po uruchomić test obciążenia i zebrane dane o aktywności wirtualnego użytkownika danych można wyświetlić w wynikach testów obciążenia za pomocą **analizatora testu obciążenia** widok szczegółów w **wykres aktywności wirtualnych użytkowników** . Ponadto można użyć **wykres aktywności wirtualnych użytkowników** Aby wyizolować problemy z wydajnością w teście obciążenia.

### <a name="to-use-the-virtual-user-activity-chart-in-your-load-test-results"></a>Aby użyć wykres aktywności wirtualnych użytkowników, w wynikach testu obciążenia

1.  Po załadowaniu zakończenia testu uruchomiony, **Podsumowanie** wyświetlana jest strona wyników testów obciążenia w **analizatora testu obciążenia**. Wybierz **wykresów** przycisk na pasku narzędzi.

     Wyświetlany jest widok wykresów.

2.  Na **czas odpowiedzi strony** wykres, kliknij prawym przyciskiem myszy w pobliżu jednej ikony naruszenia progu i wybierz **przejdź do szczegółów użytkownika**.

    > [!NOTE]
    > Możesz użyć **szczegóły** znajdujący się w **edytora testu obciążenia** narzędzi, aby otworzyć zbyt wykresu aktywności użytkownika. Jednak jeśli używasz **przejdź do szczegółów użytkownika** opcji **wykres aktywności wirtualnych użytkowników** zostanie automatycznie powiększyć część testu, który kliknięto prawym przyciskiem myszy na wykresie.

     Będzie ona wyświetlana w widoku szczegółów **wykres aktywności wirtualnych użytkowników** koncentruje się na okres czasu, kiedy wystąpił naruszenia progu.

     Na osi y poziome wykresy reprezentują poszczególnych użytkowników wirtualnych. Oś x przedstawia oś czasu dla przebiegu testu obciążeniowego.

3.  W **Powiększ do okresu czasu** narzędzie poniżej **wykres aktywności wirtualnych użytkowników**, dostosować po lewej stronie i prawego suwaki, dopóki oba są Zamknij, aby ikona naruszenia progu. Spowoduje to zmianę skali czasu w **wykres aktywności wirtualnych użytkowników**

4.  W **Legenda szczegółów**, zaznacz pole wyboru dla **(Podświetl błędy)**. Należy zauważyć, że jest wyróżniona wirtualnego użytkownika, który spowodował naruszenie progu.

5.  W **filtrowanie wyników** panelu, usuń zaznaczenie pól wyboru dla **Pokaż pomyślne wyniki** i **HttpError** , ale pozostawić **ValidationRuleError**zaznaczone pole wyboru.

     **Wykres aktywności wirtualnych użytkowników** wyświetla tylko użytkowników wirtualnych zrealizowanych przez więcej niż 3 sekundy *Red.aspx* stronie określony przez naruszenie progu skonfigurowana w poprzednim przewodniku.

6.  Zatrzymaj wskaźnik myszy nad linii poziomej, reprezentujący wirtualnego użytkownika za pomocą błąd reguły sprawdzania poprawności dla naruszenie progu.

7.  Etykietka narzędzia jest wyświetlana z następującymi informacjami:

    -   **Identyfikator użytkownika**

    -   **Scenariusz**

    -   **Test**

    -   **Wynik**

    -   **Sieci**

    -   **Godzina rozpoczęcia**

    -   **Czas trwania**

    -   **Agent**

    -   **Dziennik testu**

8.  Należy zauważyć, że **Dziennik testu** łącze. Wybierz **Dziennik testu** łącza.

9. Test wydajności sieci web ColorWebTest, który jest skojarzony z dziennika zostanie otwarty w **Podgląd wyników testu wydajności sieci Web**. To pozwala izolować, gdzie wystąpiło naruszenie progowe.

     Za pomocą różnych ustawień w obu **Legenda szczegółów** i **filtrowanie wyników** panele pomagające w izolowania problemów z wydajnością oraz błędy w testach obciążenia. Eksperymentu przy użyciu tych ustawień i **Powiększ do okresu czasu** narzędzia, aby zobaczyć, jak dane użytkownika wirtualnego są prezentowane w **wykres aktywności wirtualnych użytkowników**.

## <a name="see-also"></a>Zobacz także

- [Analizowanie aktywności wirtualnego użytkownika w widoku szczegółów](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)
- [Instrukcje: Utwórz ustawienie testu dla testu obciążenia rozłożonego](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)
- [Zbieranie informacji diagnostycznych za pomocą ustawień testów](../test/collect-diagnostic-information-using-test-settings.md)
