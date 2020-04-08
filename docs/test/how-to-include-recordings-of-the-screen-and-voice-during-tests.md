---
title: Nagrywanie ekranu i głosu podczas testów
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, recording desktop video
ms.assetid: 2cefe8c2-430a-4cb4-bbe0-f3edb2e5bc03
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d53f03ed711b613a44aaf7cd243bd9aadeb2c93b
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880328"
---
# <a name="how-to-include-recordings-of-the-screen-and-voice-during-tests-using-test-settings"></a>Jak: Dołączanie nagrań ekranu i głosu podczas testów przy użyciu ustawień testowych

Z edytora konfiguracji w programie Visual Studio można skonfigurować kartę danych diagnostycznych, która rejestruje ekran i głos użytkownika, który uruchamia test. Ta karta danych diagnostycznych zapisuje ekran i nagranie głosowe sesji pulpitu podczas testu. Nagranie jest zapisywane z wynikiem testu lub może być dołączone do błędu. Inni członkowie zespołu mogą używać nagrania do izolowania wad aplikacji, które są trudne do odtworzenia.

> [!WARNING]
> Nagrania ekranowe i głosowe nie obsługują wielu konfiguracji monitorów.

Ekran i dyktafon mogą być używane z testami ręcznymi lub automatycznymi. Na przykład po uruchomieniu kodowany test interfejsu użytkownika zdalnie można nagrać pulpitu, aby zobaczyć kodowany test interfejsu użytkownika, jak działa. Aby uzyskać więcej informacji na temat zdalnego przechwytywania ekranu i nagrywania głosu, zobacz [Jak: Konfigurowanie agenta testowego do uruchamiania testów, które współdziałają z pulpitem.](../test/how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop.md)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-configure-screen-and-voice-recording-for-your-test-settings"></a>Aby skonfigurować nagrywanie ekranu i głosu dla ustawień testowych

1. Otwórz ustawienia testu, które chcesz skonfigurować do nagrywania ekranu i głosu. Aby uzyskać więcej informacji, zobacz [Zbieranie danych diagnostycznych podczas testowania (plany testów platformy Azure)](/azure/devops/test/collect-diagnostic-data?view=vsts) lub [Zbieranie informacji diagnostycznych przy użyciu ustawień testu](../test/collect-diagnostic-information-using-test-settings.md).

2. W ustawieniach testu wybierz **rolę,** której chcesz nagrać ekran i głos.

    > [!NOTE]
    > W przypadku testów ręcznych i testów automatycznych będzie to maszyna, która uruchamia testy.

3. Wybierz **pozycję Ekran i dyktafon,** a następnie wybierz pozycję **Konfiguruj**.

     Zostanie wyświetlone okno dialogowe **Konfigurowanie karty danych diagnostycznych** — ekran i rejestrator głosu.

     ![Konfiguracja wideo](../test/media/testsettingvideoconfiggdr.png)

4. (Opcjonalnie) Wybierz **pozycję Włącz nagrywanie głosowe,** aby przechwytywać zawartość audio w nagraniu.

5. (Opcjonalnie) Zaznacz pole wyboru obok pozycji **Zapisz nagranie, jeśli przypadek testowy przejdzie,** aby określić zapisywanie nagrań ekranowych i głosowych dla testów, które nie powiodły się i przeszły pomyślnie.

    > [!WARNING]
    > Jeśli wybierzesz **zapisz nagrywanie, jeśli przypadek testowy przejdzie,** nagranie jest przechowywane wraz z wynikami testu, które wykorzystuje miejsce do magazynowania na serwerze. Do czyszczenia tych załączników można użyć narzędzia **Test Attachment Cleaner.**

6. W obszarze **Jakość nagrywania ekranu**skonfiguruj następujące opcje listy rozwijanej:

    1. **Liczba klatek na sekundę:** Określ liczbę klatek na sekundę, których chcesz używać na ekranie i nagrywanie głosu. Wartość domyślna to 4 klatki na sekundę. Można określić wartości z 2 do 20.

    2. **Szybkość transmisji bitów:** Określ liczbę kilobajtów na sekundę do użycia na ekranie i nagrywanie głosu. Wartość domyślna to 512. Można określić wartości z 512 do 10 000.

    3. **Jakość(1-100):** Jakość ekranu i nagrywania głosu można określić, wybierając zakres od 1 do 100. Wartość domyślna to 50 (średni zakres).

7. Wybierz pozycję **OK**. Ustawienia diagnostycznego modułu zbierającego śledzenie są teraz konfigurowane i zapisywane dla ustawień testu.

    ::: moniker range="vs-2017"
    > [!TIP]
    > Aby zresetować konfigurację tej karty danych diagnostycznych, wybierz pozycję **Resetuj do domyślnej konfiguracji** programu Visual Studio i **Resetuj domyślnie** dla menedżera testów firmy Microsoft.
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    > [!TIP]
    > Aby zresetować konfigurację tej karty danych diagnostycznych, wybierz pozycję **Resetuj do domyślnej konfiguracji** w programie Visual Studio.
    ::: moniker-end

## <a name="see-also"></a>Zobacz też

- [Zbieranie danych diagnostycznych podczas testowania (plany testów platformy Azure)](/azure/devops/test/collect-diagnostic-data?view=vsts)
- [Zbieranie danych diagnostycznych w testach ręcznych (plany testów platformy Azure)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)
- [Zbieranie informacji diagnostycznych przy użyciu ustawień testu](../test/collect-diagnostic-information-using-test-settings.md)
- [Uruchamianie testów ręcznych (plany testów platformy Azure)](/azure/devops/test/run-manual-tests?view=vsts)
