---
title: Powiąż kontroler testów/agenta testowego z kartą sieciową
description: Dowiedz się, jak powiązać kontroler testów lub agenta testowego z kartą sieciową przy użyciu adresu IP, na wypadek gdy jest zainstalowany dla wielu kart sieciowych.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- controllers, netwrok adapter
- agents, configuring
- agents, network adapter
- controllers, configuring
ms.assetid: 7eb9290a-f9f6-4e41-9caa-796fcfaf0610
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: f35e870e625a0f494692d082494ee0c2511ffd8f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966841"
---
# <a name="how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter"></a>Instrukcje: powiązanie kontrolera testów lub agenta testowego z kartą sieciową

Jeśli komputer, na którym jest zainstalowany kontroler testów lub oprogramowanie agenta testowego, ma wiele kart sieciowych, należy określić adres IP zamiast nazwy komputera, aby zidentyfikować kontrolera testów lub agenta testowego.

> [!WARNING]
> Podczas próby skonfigurowania agenta testowego może zostać wyświetlony następujący błąd:
>
> **Błąd 8110. Nie można nawiązać połączenia z określonym komputerem kontrolera lub uzyskać dostępu do obiektu kontrolera**
>
> Ten błąd może być spowodowany przez zainstalowanie kontrolera testów na komputerze, który ma więcej niż jedną kartę sieciową. Istnieje również możliwość pomyślnego zainstalowania agentów i niezobaczenia tego problemu, dopóki nie zostanie podjęta próba uruchomienia testu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="bind-a-test-controller-to-a-specific-network-adapter"></a>Powiąż kontroler testów z konkretną kartą sieciową

### <a name="to-obtain-the-ip-addresses-of-the-network-adapters"></a>Aby uzyskać adresy IP kart sieciowych

1. W systemie Microsoft Windows, wybierz **Start**, wybierz w polu **Rozpocznij wyszukiwanie** , wpisz **cmd**, a następnie wybierz **Enter**.

2. Wpisz polecenie **ipconfig /all**.

     Wyświetlane są adresy IP kart sieciowych. Zapisz adres IP karty sieciowej, z którą chcesz powiązać kontroler.

### <a name="to-bind-a-network-adapter-to-a-test-controller"></a>Aby powiązać kartę sieciową z kontrolerem testów

1. W systemie Microsoft Windows wybierz polecenie **Start**, wybierz w polu **Rozpocznij wyszukiwanie** , wpisz polecenie **Services. msc**, a następnie wybierz **klawisz ENTER**.

     Zostanie wyświetlone okno dialogowe **usługi** .

2. W okienku wyników w kolumnie **Nazwa** kliknij prawym przyciskiem myszy usługę **Test Controller Visual Studio** , a następnie wybierz polecenie **Zatrzymaj**.

     -lub-

     Otwórz wiersz polecenia z podwyższonym poziomem uprawnień i uruchom następujące polecenie przy użyciu polecenia:

     `net stop vsttcontroller`

3. Otwórz plik konfiguracji XML *QTCcontroller.exe.config* znajdujący się w lokalizacji *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017 \\ \<edition> \Common7\IDE*.

4. Znajdź `<appSettings>` tag.

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

5. Dodaj `BindTo` klucz, aby określić, która karta sieciowa ma być używana w `<appSettings>` sekcji.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6. Uruchom usługę kontrolera testów. Aby to zrobić, uruchom następujące polecenie w wierszu polecenia:

    `net start vsttcontroller`

    > [!WARNING]
    > Aby połączyć agenta testowego z kontrolerem, należy ponownie uruchomić instalację agenta testowego. Tym razem Określ adres IP kontrolera, a nie nazwę kontrolera.

     Dotyczy to kontrolera, usługi agenta i procesu agenta. `BindTo`Właściwość musi być ustawiona dla każdego procesu, który jest uruchomiony na komputerze, który ma więcej niż jedną kartę sieciową. Procedura ustawiania `BindTo` właściwości jest taka sama dla wszystkich trzech procesów, jak określono wcześniej w tym temacie dla kontrolera testów.

### <a name="to-bind-a-network-interface-card-to-a-test-agent"></a>Aby powiązać kartę sieciową z agentem testowym

1. W systemie Microsoft Windows wybierz polecenie **Start**, wybierz w polu **Rozpocznij wyszukiwanie** , wpisz polecenie **Services. msc**, a następnie wybierz **klawisz ENTER**.

    Zostanie wyświetlone okno dialogowe **usługi** .

2. W okienku wyników w kolumnie **Nazwa** kliknij prawym przyciskiem myszy usługę **agenta testowego programu Visual Studio** , a następnie wybierz polecenie **Zatrzymaj**.

     -lub-

     Otwórz wiersz polecenia z podwyższonym poziomem uprawnień i uruchom następujące polecenie przy użyciu polecenia:

     **polecenie net stop vsttagent**

3. Otwórz plik konfiguracji XML *QTAgentService.exe.config* znajdujący się w lokalizacji *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017 \\ \<edition> \Common7\IDE*.

4. Znajdź `<appSettings>` tag.

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

5. Dodaj `BindTo` klucz, aby określić, która karta sieciowa ma być używana w `<appSettings>` sekcji.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6. Uruchom usługę agenta testowego. Aby to zrobić, uruchom następujące polecenie w wierszu polecenia:

    `net start vsttagent`

## <a name="see-also"></a>Zobacz też

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)
- [Modyfikowanie ustawień rejestrowania testu obciążenia](../test/modify-load-test-logging-settings.md)
- [Konfigurowanie portów dla kontrolerów testów i agentów testowych](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [Instrukcje: Określanie okresów limitu czasu dla kontrolerów testów i agentów testowych](../test/how-to-specify-timeout-periods-for-test-controllers-and-test-agents.md)
