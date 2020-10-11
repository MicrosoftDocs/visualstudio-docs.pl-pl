---
title: Nagrywanie ekranu i głosu podczas testów
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- test settings, recording desktop video
ms.assetid: 2cefe8c2-430a-4cb4-bbe0-f3edb2e5bc03
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2366e77b0b66e2a31ce17e1aefb9240e4f45df2d
ms.sourcegitcommit: 754133c68ad841f7d7962e0b7a575e133289d8a8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2020
ms.locfileid: "91928648"
---
# <a name="how-to-include-recordings-of-the-screen-and-voice-during-tests-using-test-settings"></a>Instrukcje: uwzględnianie nagrań ekranu i głosu podczas testów przy użyciu ustawień testu

Z poziomu edytora konfiguracji w programie Visual Studio można skonfigurować adapter danych diagnostycznych, który rejestruje ekran i głos użytkownika, który uruchamia test. Ten adapter danych diagnostycznych zapisuje nagrywanie ekranu i głosu sesji pulpitu podczas testu. Nagranie jest zapisywane z wynikiem testu lub może być dołączone do usterki. Inni członkowie zespołu mogą używać nagrań do izolowania usterek aplikacji, które są trudne do odtworzenia.

> [!WARNING]
> Nagrania ekranu i głosu nie obsługują wielu konfiguracji monitora.

Rejestrator ekranu i głosu może być używany z testami ręcznymi lub zautomatyzowanymi. Na przykład w przypadku uruchamiania kodowanego testu interfejsu użytkownika zdalnie możesz chcieć nagrać pulpit, aby zobaczyć kodowany test interfejsu użytkownika w trakcie jego działania. Aby uzyskać więcej informacji na temat zdalnego przechwytywania nagrania ekranu i głosu, zobacz [How to: set up the test agent do uruchamiania testów, które współdziałają z pulpitem](../test/how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-configure-screen-and-voice-recording-for-your-test-settings"></a>Aby skonfigurować nagrywanie ekranu i głosu dla ustawień testu

1. Otwórz ustawienia testu, które chcesz skonfigurować do nagrywania ekranu i głosu. Aby uzyskać więcej informacji, zobacz [zbieranie danych diagnostycznych podczas testowania (Azure test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts&preserve-view=true) lub [zbieranie informacji diagnostycznych przy użyciu ustawień testu](../test/collect-diagnostic-information-using-test-settings.md).

2. W ustawieniach testu wybierz **rolę** , która ma być używana do rejestrowania ekranu i głosu.

    > [!NOTE]
    > W przypadku testów ręcznych i testów automatycznych może to być maszyna, na której są wykonywane testy.

3. Wybierz pozycję **rejestrator ekranu i głosu** , a następnie wybierz pozycję **Konfiguruj**.

     Zostanie wyświetlone okno dialogowe **Konfigurowanie karty danych diagnostycznych — ekranu i rejestratora głosu** .

     ![Konfiguracja wideo](../test/media/testsettingvideoconfiggdr.png)

4. Obowiązkowe Wybierz pozycję **Włącz nagrywanie głosu** , aby przechwycić zawartość audio w nagraniu.

5. Obowiązkowe Zaznacz pole wyboru obok pozycji **Zapisz nagranie, jeśli przypadek testowy zostanie** określony, aby określić zapisywanie nagrań ekranu i głosu dla testów zakończonych niepowodzeniem i zakończonych pomyślnie.

    > [!WARNING]
    > Jeśli wybierzesz opcję **Zapisz nagrywanie, jeśli przypadek testowy**jest zapisywany, nagranie jest przechowywane z wynikami testu, które korzystają z miejsca do magazynowania na serwerze. Aby wyczyścić te załączniki, można użyć narzędzia do **czyszczenia załączników testów** .

6. W obszarze **jakość nagrywania ekranu**skonfiguruj następujące opcje listy rozwijanej:

    1. **Szybkość klatek:** Określ liczbę ramek na sekundę, które mają być używane na potrzeby nagrania ekranu i głosu. Wartość domyślna to 4 klatki na sekundę. Można określić wartości z zakresu od 2 do 20.

    2. **Szybkość transmisji bitów:** Określ, ile kilobajtów na sekundę ma używać w nagrywaniu ekranu i głosu. Wartość domyślna to 512. Można określić wartości z zakresu od 512 do 10 000.

    3. **Jakość (1 – 100):** Możesz określić jakość nagrywania ekranu i głosu, wybierając zakres z zakresu od 1 do 100. Wartość domyślna to 50 (średni zakres).

7. Wybierz przycisk **OK**. Ustawienia modułu zbierającego dane śledzenia diagnostyki zostały teraz skonfigurowane i zapisane dla ustawień testu.

    ::: moniker range="vs-2017"
    > [!TIP]
    > Aby zresetować konfigurację tego adaptera danych diagnostycznych, wybierz pozycję **Zresetuj do konfiguracji domyślnej** dla programu Visual Studio i **Przywróć wartość domyślną** dla Microsoft Test Manager.
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    > [!TIP]
    > Aby zresetować konfigurację tego adaptera danych diagnostycznych, wybierz pozycję **Zresetuj do konfiguracji domyślnej** w programie Visual Studio.
    ::: moniker-end

## <a name="see-also"></a>Zobacz też

- [Zbieraj dane diagnostyczne podczas testowania (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts&preserve-view=true)
- [Zbieranie danych diagnostycznych w testach ręcznych (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts&preserve-view=true)
- [Zbieranie informacji diagnostycznych za pomocą ustawień testu](../test/collect-diagnostic-information-using-test-settings.md)
- [Uruchom testy ręczne (Azure Test Plans)](/azure/devops/test/run-manual-tests?view=vsts&preserve-view=true)