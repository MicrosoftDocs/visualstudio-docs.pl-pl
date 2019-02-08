---
title: Nagraj ekran i głos podczas testów
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, recording desktop video
ms.assetid: 2cefe8c2-430a-4cb4-bbe0-f3edb2e5bc03
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9043411cd6681078e9e4d0418e6f3686aa37fc17
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55949814"
---
# <a name="how-to-include-recordings-of-the-screen-and-voice-during-tests-using-test-settings"></a>Instrukcje: Obejmują nagrań ekranu i głosu podczas testów przy użyciu ustawień testu

Z edytora konfiguracji w programie Visual Studio można skonfigurować adapter danych diagnostycznych, który nagrywa ekran i głos użytkownika, który uruchamia test. Ten adapter danych diagnostycznych zapisuje nagrywanie ekranu i głosu z sesji pulpitu podczas testu. Nagranie jest zapisywane z wynikiem testu lub mogą być dołączane do błędów. Inni członkowie zespołu można użyć rejestrowania, aby wyizolować defekty aplikacji, które są trudne do odtworzenia.

> [!WARNING]
> Nagrania ekranu i głosu nie obsługują wielu konfiguracji monitora.

Nagrywanie ekranu i głosu może służyć za pomocą testów ręcznych i automatycznych. Na przykład zdalne uruchamianie kodowanego testu interfejsu użytkownika można nagrać pulpit, aby zobaczyć kodowany test interfejsu użytkownika podczas jego wykonywania. Aby uzyskać więcej informacji o sposobie przechwytywania nagrywania ekranu i głosu zdalnie, zobacz [jak: Konfigurowanie agenta testowego do uruchamiania testów, które współdziałają z pulpitem](../test/how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-configure-screen-and-voice-recording-for-your-test-settings"></a>Aby skonfigurować nagrywanie w ustawieniach testu ekranu i głosu

1.  Otwórz ustawienia testu, które chcesz skonfigurować do nagrywania ekranu i głosu. Aby uzyskać więcej informacji, zobacz [zbieranie danych diagnostycznych podczas testowania (plany testów platformy Azure)](/azure/devops/test/collect-diagnostic-data?view=vsts) lub [zbieranie informacji diagnostycznych przy użyciu ustawień testu](../test/collect-diagnostic-information-using-test-settings.md).

2.  W ustawieniach testu wybierz **roli** służące do nagrywania ekranu i głosu.

    > [!NOTE]
    > Dla ręcznych i automatycznych testów będzie to komputer który uruchamia testy.

3.  Wybierz **nagrywanie ekranu i głosu** , a następnie wybierz **Konfiguruj**.

     **Konfigurowanie adaptera danych diagnostycznych — nagrywanie ekranu i głosu** zostanie wyświetlone okno dialogowe.

     ![Konfiguracja wideo](../test/media/testsettingvideoconfiggdr.png)

4.  (Opcjonalnie) Wybierz **Włącz nagrywanie głosu** Aby przechwytywać zawartość audio podczas rejestracji.

5.  (Opcjonalnie) Zaznacz pole wyboru obok pozycji **Zapisz nagrywanie, jeżeli przypadek testowy jest zaliczony** Aby określić zapisywanie nagrania ekranu i głosu dla obu nie powiodło się i przeszedł testy.

    > [!WARNING]
    > Jeśli wybierzesz **Zapisz nagrywanie, jeżeli przypadek testowy jest zaliczony**, nagranie jest przechowywane z wynikami testów, który używa miejsce do magazynowania na serwerze. Możesz użyć **Test Attachment Cleaner** narzędzie, aby wyczyścić załączniki.

6.  W obszarze **jakość nagrania ekranu**, skonfiguruj następujące opcje listy rozwijanej:

    1.  **Szybkość klatek:** Określ liczbę klatek na sekundę, które mają być używane w nagrywaniu ekranu i głosu. Wartość domyślna to 4 klatki na sekundę. Można określić wartości z zakresu od 2 do 20.

    2.  **Szybkość transmisji bitów:** Określ liczbę kilobitów na sekundę do użycia w nagrywaniu ekranu i głosu. Wartość domyślna to 512. Można określić wartości z zakresu od 512 do 10 000.

    3.  **Quality(1-100):** Można określić jakość nagrywania ekranu i głosu, wybierając zakres od 1 do 100. Wartością domyślną jest 50 (zakres średni).

7.  Wybierz **OK**. Ustawienia modułu zbierającego śledzenia diagnostycznego są teraz skonfigurowane i zapisane w ustawieniach testu.

    > [!TIP]
    > Aby zresetować konfigurację tego adaptera danych diagnostycznych, wybierz opcję **Przywróć domyślną konfigurację** dla programu Visual Studio i **Przywróć domyślne** dla programu Microsoft Test Manager.

## <a name="see-also"></a>Zobacz także

- [Zbieranie danych diagnostycznych podczas testowania (planów testowych platformy Azure)](/azure/devops/test/collect-diagnostic-data?view=vsts)
- [Zbieranie danych diagnostycznych podczas wykonywania testów ręcznych (planów testowych platformy Azure)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)
- [Zbieranie informacji diagnostycznych za pomocą ustawień testów](../test/collect-diagnostic-information-using-test-settings.md)
- [Uruchamianie testów ręcznych (planów testowych platformy Azure)](/azure/devops/test/run-manual-tests?view=vsts)