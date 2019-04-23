---
title: Rozwiązywanie problemów z kontrolerami testów i agentów testowych
ms.date: 10/20/2016
ms.topic: troubleshooting
helpviewer_keywords:
- load tests, test controllers
- load tests, troubleshooting
- load tests, test agents
- troubleshooting, test controllers and agents in load tests
ms.assetid: 77329348-3a5d-43de-b6cb-90f93296a081
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3ca2a69fc0f5777c34857f6f3da0c7faabcd81ce
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60088902"
---
# <a name="strategies-for-troubleshooting-test-controllers-and-test-agents-in-load-tests"></a>Strategie rozwiązywania problemów kontrolerów testów i agentów testowych w testach obciążenia

W tym artykule omówiono niektóre typowe problemy, które można napotkać podczas pracy z kontrolerami testów i agentów testowych w programie Visual Studio.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="unable-to-collect-performance-counters-on-test-agent-computer"></a>Nie można zebrać liczników wydajności na komputerze agenta testowego

Po uruchomieniu testu obciążenia, może być wystąpią błędy, gdy użytkownik próbuje nawiązać połączenie z komputerem agenta testowego i zbierania liczników wydajności. Usługa Rejestr zdalny jest usługą odpowiedzialną za dostarczanie danych licznika wydajności na komputerze zdalnym. W niektórych systemach operacyjnych usługa Rejestr zdalny nie zostanie uruchomiona automatycznie. Aby rozwiązać ten problem, należy ręcznie uruchomić usługę Rejestr zdalny.

> [!NOTE]
> Uzyskać dostęp do usługi Rejestr zdalny, w **Panelu sterowania.** Wybierz **narzędzia administracyjne** , a następnie wybierz **usług**.

Inną przyczyną tego problemu jest to, że nie masz wystarczających uprawnień do odczytu liczników wydajności. Dla lokalnych przebiegów testowych konto użytkownika, który uruchamia test musi być członkiem grupy Użytkownicy zaawansowani lub wyższej lub być członkiem grupy Użytkownicy monitora wydajności. Zdalny testu jest uruchomiony, konto administratora jest skonfigurowany do uruchamiania jako musi być członkiem grupy Użytkownicy zaawansowani lub wyższej, lub być członkiem grupy Użytkownicy monitora wydajności.

## <a name="set-the-logging-level-on-a-test-controller-computer"></a>Poziom rejestrowania na komputerze kontrolera testu

Można kontrolować poziom rejestrowania na komputerze kontrolera testów. Jest to przydatne, gdy chcesz zdiagnozować problem po uruchomieniu testu obciążenia w środowisku.

### <a name="to-set-the-logging-level-on-a-test-controller-computer"></a>Aby ustawić poziom rejestrowania na komputerze kontrolera testu

1. Zatrzymaj usługę kontrolera testu. W wierszu polecenia wpisz `net stop vsttcontroller`.

2. Otwórz plik *QTController.exe.config*. Ten plik znajduje się w katalogu instalacyjnym kontrolera.

3. Edytuj wpis dla `EqtTraceLevel` przełączyć się w sekcji Diagnostyka systemu pliku. Kod powinien wyglądać następująco:

    ```xml
    <system.diagnostics>
        <trace autoflush="true" indentsize="4">
            <listeners>
                <add name="myListener" type="System.Diagnostics.TextWriterTraceListener" initializeData="d:\VSTestHost.log" />
            </listeners>
        </trace>
        <switches>
            <!-- You must use integral values for "value":
                    0 = off,
                    1 = error,
                    2 = warn,
                    3 = info,
                    4 = verbose. -->
            <add name="EqtTraceLevel" value="4" />
        </switches>
    </system.diagnostics>
    ```

4. Zapisz plik.

5. Uruchom usługę kontrolera. W wierszu polecenia wpisz `net start vsttcontroller`.

Dotyczy to kontrolera testów, Usługa agenta testowego i procesu agenta testowego. Podczas diagnozowania problemów, warto włączyć rejestrowanie na wszystkich trzech procesów. Procedury ustanawiania poziomów rejestrowania jest taka sama dla wszystkich trzech procesów, jak określono wcześniej dla kontrolera testów. Aby ustawić poziomy rejestrowania dla agenta testowego, usługi i procesu agenta, należy użyć następujących plików konfiguracyjnych:

- *QTController.exe.config* Usługa kontrolera

- *QTAgentService.exe.config* Usługa agenta

- *QTDCAgent (32).exe.config* proces adaptera danych agenta dla architektury 32-bitowych.

- *QTDCAgent (64).exe.config* proces adaptera danych agenta dla architektury 64-bitowych.

- *QTAgent (32).exe.config* proces testowania agenta dla architektury 32-bitowych.

- *QTAgent (64).exe.config* proces testowania agenta dla architektury 64-bitowych.

## <a name="bind-a-test-controller-to-a-network-adapter"></a>Powiąż kontroler testów z kartą sieciową

Podczas konfigurowania agenta testowego, może pojawić się następujący błąd:

**Błąd 8110. Nie można podłączenia do komputera kontrolera lub uzyskać dostępu do obiektu kontrolera.**

Ten błąd może być spowodowany przez zainstalowanie kontrolera testów na komputerze, który ma więcej niż jedną kartę sieciową.

> [!NOTE]
> Jest również możliwe, aby pomyślnie zainstalować agentów testowych i nie widzieć tego problemu, dopóki nie zostanie podjęta próba uruchomienia testu.

Aby naprawić ten błąd, można powiązać kontroler testów do jednej z kart sieciowych. Należy ustawić `BindTo` właściwości kontrolera testów, a następnie zmień agenta testowego do odwoływania się do kontrolera testów według adresu IP adres zamiast według nazwy. Kroki są zapewniane w poniższych procedurach.

### <a name="to-obtain-the-ip-address-of-the-network-adapter"></a>Aby uzyskać adres IP karty sieciowej

1. Wybierz **Start**, a następnie wybierz **Uruchom**.

     **Uruchom** zostanie wyświetlone okno dialogowe.

2. Typ `cmd` , a następnie wybierz **OK**.

     Otwiera wiersz poleceń.

3. Typ `ipconfig /all`.

     Adresy IP dla karty sieciowe są wyświetlane. Zapisz adres IP karty sieciowej, którą chcesz powiązać kontroler.

### <a name="to-bind-a-test-controller-to-a-network-adapter"></a>Aby powiązać kontroler testów z kartą sieciową

1. Zatrzymaj usługę kontrolera testu. W wierszu polecenia wpisz `net stop vsttcontroller`.

2. Otwórz plik *QTController.exe.config*. Ten plik znajduje się w *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

3. Dodaj wpis dla `BindTo` właściwości do ustawień aplikacji. Określ adres IP karty sieciowej, którą chcesz powiązać kontroler. Kod powinien wyglądać następująco:

    ```xml
    <appSettings>
        <add key="LogSizeLimitInMegs" value="20" />
        <add key="AgentSyncTimeoutInSeconds" value="120" />
        <add key="ControllerServicePort" value="6901" />
        <add key="ControllerUsersGroup" value="TeamTestControllerUsers" />
        <add key="ControllerAdminsGroup" value="TeamTestControllerAdmins" />
        <add key="CreateTraceListener" value="no" />
        <add key="BindTo" value="<YOUR IP ADDRESS>" />
    </appSettings>
    ```

4. Zapisz plik.

5. Uruchom usługę kontrolera testu. W wierszu polecenia wpisz `net start vsttcontroller`.

### <a name="to-connect-a-test-agent-to-a-bound-controller"></a>Aby połączyć agenta testowego z kontrolerem powiązania

- Uruchom ponownie instalację agenta testowego. Tym razem, określ adres IP dla kontrolera testów, a nie nazwę kontrolera testów.

Dotyczy to kontrolera testów, Usługa agenta testowego i procesu agenta testowego. `BindTo` Właściwość musi być ustawiona dla każdego procesu, który jest uruchomiony na komputerze, który ma więcej niż jedną kartę sieciową. Procedury ustanawiania `BindTo` właściwości jest taka sama dla wszystkich trzech procesów, jak określono wcześniej dla kontrolera testów. Aby ustawić poziomów rejestrowania dla usługi agenta testowego i procesu agenta testowego, należy użyć plików konfiguracyjnych, które są wymienione w [ustawić poziom rejestrowania na komputerze kontrolera testu](#set-the-logging-level-on-a-test-controller-computer).

## <a name="see-also"></a>Zobacz także

- [Kontrolerzy testów i agenci testowi](../test/configure-test-agents-and-controllers-for-load-tests.md)
