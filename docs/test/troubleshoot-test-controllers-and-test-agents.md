---
title: Rozwiązywanie problemów z kontrolerami testów i agentami testowymi
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
ms.openlocfilehash: 51d7e15ec71eec7134dfc49b3515385970e593a0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565958"
---
# <a name="strategies-for-troubleshooting-test-controllers-and-test-agents-in-load-tests"></a>Strategie rozwiązywania problemów z kontrolerami testów i agentami testowymi w testach obciążenia

W tym artykule opisano niektóre typowe problemy, które mogą wystąpić podczas pracy z kontrolerami testów i agentami testowymi w programie Visual Studio.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="unable-to-collect-performance-counters-on-test-agent-computer"></a>Nie można zebrać liczników wydajności na komputerze agenta testowego

Po uruchomieniu testu obciążenia mogą pojawić się błędy podczas próby połączenia się z komputerem agenta testowego i zbierania liczników wydajności. Usługa Rejestr zdalny jest usługą odpowiedzialną za dostarczanie danych licznika wydajności do komputera zdalnego. W niektórych systemach operacyjnych usługa Rejestr zdalny nie uruchamia się automatycznie. Aby rozwiązać ten problem, należy ręcznie uruchomić usługę Rejestr zdalny.

> [!NOTE]
> Dostęp do usługi Rejestr zdalny można uzyskać w **Panelu sterowania.** Wybierz **pozycję Narzędzia administracyjne,** a następnie wybierz pozycję **Usługi**.

Inną przyczyną tego problemu jest to, że nie masz wystarczających uprawnień do odczytu liczników wydajności. W przypadku lokalnych przebiegów testowych konto użytkownika, który uruchamia test, musi być członkiem grupy Użytkownicy zaaranżeni lub wyższe lub być członkiem grupy Użytkownicy Monitora wydajności. W przypadku zdalnych przebiegów testowych konto skonfigurowane do uruchamiania kontrolera musi być członkiem grupy Użytkownicy zaaranżeni lub wyższe lub być członkiem grupy Użytkownicy Monitora wydajności.

## <a name="set-the-logging-level-on-a-test-controller-computer"></a>Ustawianie poziomu rejestrowania na komputerze kontrolera testów

Można kontrolować poziom logowania na komputerze kontrolera testów. Jest to przydatne podczas próby zdiagnozowania problemu podczas uruchamiania testu obciążenia w środowisku.

### <a name="to-set-the-logging-level-on-a-test-controller-computer"></a>Aby ustawić poziom rejestrowania na komputerze kontrolera testów

1. Zatrzymaj usługę kontrolera testów. W wierszu polecenia `net stop vsttcontroller`wpisz polecenie .

2. Otwórz plik *QTController.exe.config*. Ten plik znajduje się w katalogu instalacji kontrolera.

3. Edytuj wpis przełącznika `EqtTraceLevel` w sekcji diagnostyki systemu pliku. Kod powinien przypominać następującą:

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

5. Uruchom usługę kontrolera. W wierszu polecenia `net start vsttcontroller`wpisz polecenie .

Dotyczy to kontrolera testów, usługi agenta testowego i procesu agenta testowego. Podczas diagnozowania problemów warto włączyć rejestrowanie wszystkich trzech procesów. Procedura ustawiania poziomu rejestrowania jest taka sama dla wszystkich trzech procesów, jak określono wcześniej dla kontrolera testów. Aby ustawić poziomy rejestrowania dla usługi agenta testowego i procesu agenta, użyj następujących plików konfiguracyjnych:

- Usługa *QTController.exe.config* Conttoller

- Usługa *QTAgentService.exe.config* Agent

- *QTDCAgent(32).exe.config* Proces karty danych agenta dla architektury 32-bitowej.

- *QTDCAgent(64).exe.config* Proces karty danych agenta dla architektury 64-bitowej.

- *QTAgent(32).exe.config* Proces testowania agenta dla architektury 32-bitowej.

- *QTAgent(64).exe.config* Proces testowania agenta dla architektury 64-bitowej.

## <a name="bind-a-test-controller-to-a-network-adapter"></a>Powiąż kontroler testów z kartą sieciową

Podczas próby skonfigurowania agenta testowego może pojawić się następujący błąd:

**Błąd 8110. Nie można połączyć się z określonym komputerem kontrolera ani uzyskać dostępu do obiektu kontrolera.**

Ten błąd może być spowodowany zainstalowaniem kontrolera testów na komputerze, który ma więcej niż jedną kartę sieciową.

> [!NOTE]
> Istnieje również możliwość pomyślnego zainstalowania agentów testowych i nie widać tego problemu, dopóki nie spróbujesz uruchomić testu.

Aby naprawić ten błąd, należy powiązać kontroler testów z jedną z kart sieciowych. Należy ustawić `BindTo` właściwość na kontrolerze testów, a następnie zmienić agenta testowego, aby odwoływać się do kontrolera testów według adresu IP, a nie według nazwy. Kroki są podane w poniższych procedurach.

### <a name="to-obtain-the-ip-address-of-the-network-adapter"></a>Aby uzyskać adres IP karty sieciowej

1. Wybierz **pozycję Start**, a następnie wybierz pozycję **Uruchom**.

     Zostanie wyświetlone okno dialogowe **Uruchom.**

2. Wpisz, `cmd` a następnie wybierz przycisk **OK**.

     Zostanie wyświetlony wiersz polecenia.

3. Wpisz polecenie `ipconfig /all`.

     Zostaną wyświetlone adresy IP kart sieciowych. Zapisz adres IP karty sieciowej, z którą chcesz powiązać kontroler.

### <a name="to-bind-a-test-controller-to-a-network-adapter"></a>Aby powiązać kontroler testów z kartą sieciową

1. Zatrzymaj usługę kontrolera testów. W wierszu polecenia `net stop vsttcontroller`wpisz polecenie .

2. Otwórz plik *QTController.exe.config*. Ten plik znajduje się w *pliku %ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

3. Dodaj wpis dla `BindTo` właściwości do ustawień aplikacji. Określ adres IP karty sieciowej, z którą ma zostać powiązany kontroler. Kod powinien przypominać następującą:

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

5. Uruchom usługę kontrolera testów. W wierszu polecenia `net start vsttcontroller`wpisz polecenie .

### <a name="to-connect-a-test-agent-to-a-bound-controller"></a>Aby podłączyć agenta testowego do powiązanego kontrolera

- Uruchom ponownie instalację agenta testowego. Tym razem należy określić adres IP kontrolera testów zamiast nazwy kontrolera testów.

Dotyczy to kontrolera testów, usługi agenta testowego i procesu agenta testowego. Właściwość musi być ustawiona `BindTo` dla każdego procesu, który jest uruchomiony na komputerze, który ma więcej niż jedną kartę sieciową. Procedura ustawiania `BindTo` właściwości jest taka sama dla wszystkich trzech procesów, jak określono wcześniej dla kontrolera testów. Aby ustawić poziomy rejestrowania dla usługi agenta testowego i procesu agenta testowego, użyj plików konfiguracyjnych wymienionych w [ustaw poziom rejestrowania na komputerze kontrolera testów](#set-the-logging-level-on-a-test-controller-computer).

## <a name="see-also"></a>Zobacz też

- [Kontrolerzy testów i agenci testowi](../test/configure-test-agents-and-controllers-for-load-tests.md)
