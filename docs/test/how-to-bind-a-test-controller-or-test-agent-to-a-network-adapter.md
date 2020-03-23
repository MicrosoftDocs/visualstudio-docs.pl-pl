---
title: Powiąż kontroler testu lub agenta testowego z kartą sieciową
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- controllers, netwrok adapter
- agents, configuring
- agents, network adapter
- controllers, configuring
ms.assetid: 7eb9290a-f9f6-4e41-9caa-796fcfaf0610
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6383d7a16839ba8934bb7f91664379e99da17a36
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594789"
---
# <a name="how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter"></a>Jak: Powiązać kontroler testu lub agenta testowego z kartą sieciową

Jeśli komputer z zainstalowanym kontrolerem testów lub oprogramowaniem agenta testowego ma wiele kart sieciowych, należy określić adres IP zamiast nazwy komputera, aby zidentyfikować ten kontroler testu lub agenta testowego.

> [!WARNING]
> Podczas próby skonfigurowania agenta testowego może pojawić się następujący błąd:
>
> **Błąd 8110. Nie można połączyć się z określonym komputerem kontrolera ani uzyskać dostępu do obiektu kontrolera**
>
> Ten błąd może być spowodowany zainstalowaniem kontrolera testów na komputerze, który ma więcej niż jedną kartę sieciową. Istnieje również możliwość pomyślnej instalacji agentów i nie widać tego problemu, dopóki nie spróbujesz uruchomić testu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="bind-a-test-controller-to-a-specific-network-adapter"></a>Powiąż kontroler testów z określoną kartą sieciową

### <a name="to-obtain-the-ip-addresses-of-the-network-adapters"></a>Aby uzyskać adresy IP kart sieciowych

1. W systemie Microsoft Windows wybierz pozycję **Start**, wybierz w polu **Rozpocznij wyszukiwanie,** wpisz **polecenie cmd**, a następnie wybierz pozycję **Enter**.

2. Wpisz polecenie **ipconfig /all**.

     Zostaną wyświetlone adresy IP kart sieciowych. Zapisz adres IP karty sieciowej, z którą chcesz powiązać kontroler.

### <a name="to-bind-a-network-adapter-to-a-test-controller"></a>Aby powiązać kartę sieciową z kontrolerem testowym

1. W systemie Microsoft Windows wybierz pozycję **Start**, wybierz w polu **Rozpocznij wyszukiwanie,** wpisz **services.msc**, a następnie wybierz pozycję **Enter**.

     Zostanie wyświetlone okno dialogowe **Usługi.**

2. W okienku wyników w kolumnie **Nazwa** kliknij prawym przyciskiem myszy usługę **kontroler testów programu Visual Studio,** a następnie wybierz polecenie **Zatrzymaj**.

     — lub —

     Otwórz wiersz polecenia z podwyższonym poziomem uprawnień i uruchom następujące polecenie w poleceniu:

     `net stop vsttcontroller`

3. Otwórz plik konfiguracyjny *QTCcontroller.exe.config* XML znajdujący się w *pliku %ProgramFiles(x86)%\Microsoft Visual Studio\2017\\\<edition>\Common7\IDE*.

4. zlokalizować `<appSettings>` znacznik.

    ```xml
    <appSettings>
      <add key="LogSizeLimitInMegs" value="20"/>
      <add key="AgentConnectionTimeoutInSeconds" value="120"/>
      <add key="AgentSyncTimeoutInSeconds" value="300"/>
      <add key="ControllerServicePort" value="6901"/>
      <add key="ControllerUsersGroup" value="TeamTestControllerUsers"/>
      <add key="ControllerAdminsGroup" value="TeamTestControllerAdmins"/>
      <add key="CreateTraceListener" value="no"/>
    </appSettings>
    ```

5. Dodaj `BindTo` klucz, aby określić, która `<appSettings>` karta sieciowa ma być używana w sekcji.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6. Uruchom usługę kontrolera testów. Aby to zrobić, uruchom następujące polecenie w wierszu polecenia:

    `net start vsttcontroller`

    > [!WARNING]
    > Aby podłączyć agenta testowego do kontrolera, należy ponownie uruchomić instalację agenta testowego. Tym razem należy określić adres IP kontrolera zamiast nazwy kontrolera.

     Dotyczy to kontrolera, usługi agenta i procesu agenta. Właściwość musi być ustawiona `BindTo` dla każdego procesu, który jest uruchomiony na komputerze, który ma więcej niż jedną kartę sieciową. Procedura ustawiania `BindTo` właściwości jest taka sama dla wszystkich trzech procesów, jak określono wcześniej w tym temacie dla kontrolera testów.

### <a name="to-bind-a-network-interface-card-to-a-test-agent"></a>Aby powiązać kartę interfejsu sieciowego z agentem testowym

1. W systemie Microsoft Windows wybierz pozycję **Start**, wybierz w polu **Rozpocznij wyszukiwanie,** wpisz **services.msc**, a następnie wybierz pozycję **Enter**.

    Zostanie wyświetlone okno dialogowe **Usługi.**

2. W okienku wyników w kolumnie **Nazwa** kliknij prawym przyciskiem myszy usługę **Programu Visual Studio Test Agent,** a następnie wybierz polecenie **Zatrzymaj**.

     — lub —

     Otwórz wiersz polecenia z podwyższonym poziomem uprawnień i uruchom następujące polecenie w poleceniu:

     **net stop vsttagent**

3. Otwórz plik konfiguracyjny *QTAgentService.exe.config* XML znajdujący się w *pliku %ProgramFiles(x86)%\Microsoft Visual Studio\2017\\\<edition>\Common7\IDE*.

4. zlokalizować `<appSettings>` znacznik.

    ```xml
    <appSettings>
      <appSettings>
      <add key="LogSizeLimitInMegs" value="20"/>
      <add key="AgentServicePort" value="6910"/>
      <add key="ControllerConnectionPeriodInSeconds" value="30"/>
      <add key="StopTestRunCallTimeoutInSeconds" value="120"/>
      <add key="CreateTraceListener" value="no"/>
      <add key="GetCollectorDataTimeout" value="300"/>
    </appSettings>  </appSettings>
    ```

5. Dodaj `BindTo` klucz, aby określić, która `<appSettings>` karta sieciowa ma być używana w sekcji.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6. Uruchom usługę agenta testowego. Aby to zrobić, uruchom następujące polecenie w wierszu polecenia:

    `net start vsttagent`

## <a name="see-also"></a>Zobacz też

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)
- [Modyfikowanie ustawień rejestrowania testu obciążenia](../test/modify-load-test-logging-settings.md)
- [Konfigurowanie portów dla kontrolerów testowych i agentów testowych](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [Jak: Określanie okresów limitu czasu dla kontrolerów testów i agentów testowych](../test/how-to-specify-timeout-periods-for-test-controllers-and-test-agents.md)
