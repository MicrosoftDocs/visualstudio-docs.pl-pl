---
title: Powiąż kontroler testów lub agenta testowego z kartą sieciową
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- controllers, netwrok adapter
- agents, configuring
- agents, network adapter
- controllers, configuring
ms.assetid: 7eb9290a-f9f6-4e41-9caa-796fcfaf0610
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dfcbac0bb9188826804ba13884f0f57962dddeab
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60086497"
---
# <a name="how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter"></a>Instrukcje: Powiąż kontroler testów lub agenta testowego z kartą sieciową

Jeśli komputer zawierający kontroler testów lub zainstalowane oprogramowanie agenta testowego ma kilka kart sieciowych, należy określić adres IP zamiast nazwy komputera w celu identyfikacji tego testu kontrolera lub agenta testowego.

> [!WARNING]
> Podczas konfigurowania agenta testowego, może pojawić się następujący błąd:
>
> **Błąd 8110. Nie może połączyć się z komputerem określony kontroler ani uzyskać dostępu do obiektu kontrolera**
>
> Ten błąd może być spowodowany przez zainstalowanie kontrolera testów na komputerze, który ma więcej niż jedną kartę sieciową. Jest również możliwe, aby pomyślnie zainstalować agentów i nie widzieć tego problemu, dopóki nie zostanie podjęta próba uruchomienia testu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="bind-a-test-controller-to-a-specific-network-adapter"></a>Kontroler testów należy powiązać z konkretnym adapterem sieciowym

### <a name="to-obtain-the-ip-addresses-of-the-network-adapters"></a>Do uzyskiwania adresów IP kart sieciowych

1. Z Microsoft Windows, wybierz **Start**, wybierz **Rozpocznij wyszukiwanie** wpisz **cmd**, a następnie wybierz **Enter**.

2. Typ **ipconfig/all**.

     Adresy IP dla karty sieciowe są wyświetlane. Zapisz adres IP karty sieciowej, którą chcesz powiązać kontroler.

### <a name="to-bind-a-network-adapter-to-a-test-controller"></a>Aby powiązać kartę sieciową z kontrolerem testów

1. Z Microsoft Windows, wybierz **Start**, wybierz **Rozpocznij wyszukiwanie** wpisz **services.msc**, a następnie wybierz **Enter**.

     **Usług** zostanie wyświetlone okno dialogowe.

2. W okienku wyników w obszarze **nazwa** kolumny, kliknij prawym przyciskiem myszy **Visual Studio Test Controller** usługi, a następnie wybierz **zatrzymać**.

     —lub—

     Otwórz wiersz polecenia z podwyższonym poziomem uprawnień i uruchom następujące polecenie w poleceniu:

     `net stop vsttcontroller`

3. Otwórz *QTCcontroller.exe.config* plik konfiguracyjny XML znajdujący się w *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\\\<edition > \Common7\IDE*.

4. Znajdź `<appSettings>` tagu.

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

5. Dodaj `BindTo` klawisz, aby określić kartę sieciową, której można używać w `<appSettings>` sekcji.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6. Uruchom usługę kontrolera testu. Aby to zrobić, uruchom następujące polecenie w wierszu polecenia:

    `net start vsttcontroller`

    > [!WARNING]
    > Należy uruchomić instalację agenta testowego, ponownie, aby połączyć agenta testowego z kontrolerem. Tym razem, określ adres IP dla kontrolera a nie nazwę kontrolera.

     Dotyczy to kontrolera, usługi agenta i procesu agenta. `BindTo` Właściwość musi być ustawiona dla każdego procesu, który jest uruchomiony na komputerze, który ma więcej niż jedną kartę sieciową. Procedury ustanawiania `BindTo` właściwości jest taka sama dla wszystkich trzech procesów, jak określono wcześniej w tym temacie przeznaczonym dla kontrolera testów.

### <a name="to-bind-a-network-interface-card-to-a-test-agent"></a>Aby powiązać kartę interfejsu sieciowego z agenta testowego

1. Z Microsoft Windows, wybierz **Start**, wybierz **Rozpocznij wyszukiwanie** wpisz **services.msc**, a następnie wybierz **Enter**.

    **Usług** zostanie wyświetlone okno dialogowe.

2. W okienku wyników w obszarze **nazwa** kolumny, kliknij prawym przyciskiem myszy **Visual Studio Test Agent** usługi, a następnie wybierz **zatrzymać**.

     —lub—

     Otwórz wiersz polecenia z podwyższonym poziomem uprawnień i uruchom następujące polecenie w poleceniu:

     **polecenie net stop vsttagent**

3. Otwórz *QTAgentService.exe.config* plik konfiguracyjny XML znajdujący się w *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\\\<edition > \Common7\IDE*.

4. Znajdź `<appSettings>` tagu.

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

5. Dodaj `BindTo` klawisz, aby określić kartę sieciową, której można używać w `<appSettings>` sekcji.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6. Uruchom usługę agenta testowego. Aby to zrobić, uruchom następujące polecenie w wierszu polecenia:

    `net start vsttagent`

## <a name="see-also"></a>Zobacz także

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)
- [Modyfikowanie ustawień rejestrowania testu obciążeniowego](../test/modify-load-test-logging-settings.md)
- [Konfigurowanie portów dla kontrolerów testów i agentów testowych](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [Instrukcje: Określanie limitów czasu dla kontrolerów testów i agentów testowych](../test/how-to-specify-timeout-periods-for-test-controllers-and-test-agents.md)