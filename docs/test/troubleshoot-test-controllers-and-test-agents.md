---
title: Rozwiązywanie problemów z kontrolerami testów i agentami testowymi
description: Poznaj typowe problemy, które można napotkać podczas pracy z kontrolerami testów i agentami testowymi w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 10/20/2016
ms.topic: troubleshooting
helpviewer_keywords:
- load tests, test controllers
- load tests, troubleshooting
- load tests, test agents
- troubleshooting, test controllers and agents in load tests
ms.assetid: 77329348-3a5d-43de-b6cb-90f93296a081
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e86811739df2d59e3de7980cfa346da68cc0eb43
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/30/2020
ms.locfileid: "96330150"
---
# <a name="strategies-for-troubleshooting-test-controllers-and-test-agents-in-load-tests"></a>Strategie rozwiązywania problemów z kontrolerami testów i agentami testowymi w testach obciążenia

W tym artykule opisano niektóre typowe problemy, które można napotkać podczas pracy z kontrolerami testów i agentami testowymi w programie Visual Studio.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="unable-to-collect-performance-counters-on-test-agent-computer"></a>Nie można zebrać liczników wydajności na komputerze agenta testowego

Po uruchomieniu testu obciążenia mogą wystąpić błędy podczas próby nawiązania połączenia z komputerem agenta testowego i zebrania liczników wydajności. Usługa Rejestr zdalny to usługa odpowiedzialna za dostarczanie danych licznika wydajności do komputera zdalnego. W niektórych systemach operacyjnych usługa Rejestr zdalny nie zostanie uruchomiona automatycznie. Aby rozwiązać ten problem, należy ręcznie uruchomić usługę Rejestr zdalny.

> [!NOTE]
> Dostęp do usługi Rejestr zdalny można uzyskać w **Panelu sterowania.** Wybierz pozycję **Narzędzia administracyjne** , a następnie wybierz pozycję **usługi**.

Inną przyczyną tego problemu jest to, że nie masz wystarczających uprawnień do odczytu liczników wydajności. Dla lokalnych przebiegów testowych konto użytkownika, który uruchamia test, musi być członkiem grupy Użytkownicy zaawansowani lub wyższą lub być członkiem grupy Użytkownicy monitora wydajności. W przypadku przebiegów testów zdalnych konto, na którym jest skonfigurowany kontroler, musi być członkiem grupy Użytkownicy zaawansowani lub wyższą lub być członkiem grupy Użytkownicy monitora wydajności.

## <a name="set-the-logging-level-on-a-test-controller-computer"></a>Ustawianie poziomu rejestrowania na komputerze kontrolera testów

Można kontrolować poziom rejestrowania na komputerze kontrolera testów. Jest to przydatne w przypadku próby zdiagnozowania problemu w przypadku uruchamiania testu obciążenia w środowisku.

### <a name="to-set-the-logging-level-on-a-test-controller-computer"></a>Aby ustawić poziom rejestrowania na komputerze kontrolera testów

1. Zatrzymaj usługę kontrolera testów. W wierszu polecenia wpisz polecenie `net stop vsttcontroller` .

2. Otwórz plik *QTController.exe.config*. Ten plik znajduje się w katalogu instalacyjnym kontrolera.

3. Edytuj wpis dla `EqtTraceLevel` przełącznika w sekcji Diagnostyka systemu pliku. Kod powinien wyglądać następująco:

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

5. Uruchom usługę kontrolera. W wierszu polecenia wpisz polecenie `net start vsttcontroller` .

Dotyczy to kontrolera testów, usługi agenta testowego i procesu agenta testowego. Podczas diagnozowania problemów warto włączyć rejestrowanie dla wszystkich trzech procesów. Procedura ustawiania poziomu rejestrowania jest taka sama dla wszystkich trzech procesów, jak określono wcześniej dla kontrolera testów. Aby ustawić poziomy rejestrowania dla usługi agenta testowego i procesu agenta, użyj następujących plików konfiguracji:

- *QTController.exe.config* Usługa kontrolera

- *QTAgentService.exe.config* Usługa agenta

- *QTDCAgent (32) .exe.config* Proces adaptera danych agenta dla architektury 32-bitowej.

- *QTDCAgent (64) .exe.config* Proces adaptera danych agenta dla architektury 64-bitowej.

- *QTAgent (32) .exe.config* Proces testu agenta dla architektury 32-bitowej.

- *QTAgent (64) .exe.config* Proces testu agenta dla architektury 64-bitowej.

## <a name="bind-a-test-controller-to-a-network-adapter"></a>Powiąż kontroler testów z kartą sieciową

Podczas próby skonfigurowania agenta testowego może zostać wyświetlony następujący błąd:

**Błąd 8110. Nie można nawiązać połączenia z określonym komputerem kontrolera lub uzyskać dostępu do obiektu kontrolera.**

Ten błąd może być spowodowany przez zainstalowanie kontrolera testów na komputerze, który ma więcej niż jedną kartę sieciową.

> [!NOTE]
> Istnieje również możliwość pomyślnego zainstalowania agentów testowych i niezobaczenia tego problemu, dopóki nie zostanie podjęta próba uruchomienia testu.

Aby naprawić ten błąd, należy powiązać kontroler testów z jedną z kart sieciowych. Musisz ustawić `BindTo` Właściwość na kontrolerze testów, a następnie zmienić agenta testowego, aby odwołać się do kontrolera testów według adresu IP zamiast nazwy. Kroki są podane w poniższych procedurach.

### <a name="to-obtain-the-ip-address-of-the-network-adapter"></a>Aby uzyskać adres IP karty sieciowej

1. Wybierz przycisk **Start**, a następnie wybierz polecenie **Uruchom**.

     Zostanie wyświetlone okno dialogowe **Uruchom** .

2. Wpisz `cmd` , a następnie wybierz **OK**.

     Zostanie otwarty wiersz polecenia.

3. Wpisz `ipconfig /all`.

     Wyświetlane są adresy IP kart sieciowych. Zapisz adres IP karty sieciowej, z którą chcesz powiązać kontroler.

### <a name="to-bind-a-test-controller-to-a-network-adapter"></a>Aby powiązać kontroler testów z kartą sieciową

1. Zatrzymaj usługę kontrolera testów. W wierszu polecenia wpisz polecenie `net stop vsttcontroller` .

2. Otwórz plik *QTController.exe.config*. Ten plik znajduje się w lokalizacji *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

3. Dodaj wpis dla `BindTo` właściwości do ustawień aplikacji. Określ adres IP karty sieciowej, z którą chcesz powiązać kontroler. Kod powinien wyglądać następująco:

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

5. Uruchom usługę kontrolera testów. W wierszu polecenia wpisz polecenie `net start vsttcontroller` .

### <a name="to-connect-a-test-agent-to-a-bound-controller"></a>Aby połączyć agenta testowego z kontrolerem powiązanym

- Uruchom ponownie instalację agenta testowego. Tym razem Określ adres IP dla kontrolera testów, a nie nazwę kontrolera testów.

Dotyczy to kontrolera testów, usługi agenta testowego i procesu agenta testowego. `BindTo`Właściwość musi być ustawiona dla każdego procesu, który jest uruchomiony na komputerze, który ma więcej niż jedną kartę sieciową. Procedura ustawiania `BindTo` właściwości jest taka sama dla wszystkich trzech procesów, jak określono wcześniej dla kontrolera testów. Aby ustawić poziomy rejestrowania dla usługi agenta testowego i procesu agenta testowego, należy użyć plików konfiguracji, które są wymienione na liście [Ustaw poziom rejestrowania na komputerze kontrolera testów](#set-the-logging-level-on-a-test-controller-computer).

## <a name="see-also"></a>Zobacz też

- [Kontrolerzy testów i agenci testowi](../test/configure-test-agents-and-controllers-for-load-tests.md)
