---
title: Okresy limitu czasu dla kontrolerów testów i agentów testowych
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- agents, configuring
- agetns, timeouts
- controllers, configuring
- controllers, timeouts
ms.assetid: 777d0db5-0073-458a-a2a3-58b1c1f24c60
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 64ce566369f2c60a52e9026e8f92fc30836d523c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594763"
---
# <a name="how-to-specify-timeout-periods-for-test-controllers-and-test-agents"></a>Jak: Określanie okresów limitu czasu dla kontrolerów testów i agentów testowych

Kontroler testów i agent testowy mają kilka ustawień limitu czasu, które określają, jak długo należy czekać na odpowiedzi od siebie nawzajem lub ze źródła danych przed niepowodzeniem z błędem. W pewnych okolicznościach może być konieczne edytowanie wartości limitu czasu w celu zaspokojenia potrzeb topologii lub innych problemów ze środowiskiem. Aby edytować wartości limitu czasu, edytuj plik konfiguracji XML skojarzony z kontrolerem testów lub agentem testowym, zgodnie z poniższymi procedurami.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Aby edytować kontroler testów lub różne ustawienia limitu czasu agenta testowego, zmodyfikuj następujące pliki konfiguracyjne przy użyciu nazw kluczy i wartości w tabelach:

- Kontroler testów: *QTController.exe.config*

    |Nazwa klucza|Opis|Wartość|
    |-|-----------------|-|
    |AgentConnectionTimeoutInSekundy|Liczba sekund oczekiwania na żądanie ping agenta, zanim połączenie zostanie uznane za utracone.|"n" sekund.|
    |AgentSyncTimeoutInSekundy|Po uruchomieniu przebiegu testu synchronizacji, liczba sekund oczekiwania na wszystkie agentów do synchronizacji przed przerwaniem uruchomienia.|"n" sekund.|
    |AgentInitializeTimeout|Liczba sekund oczekiwania na wszystkie agentów i ich modułów zbierających dane do zainicjowania na początku przebiegu testu, przed przerwaniem przebiegu testu. Ta wartość powinna być dość duża, jeśli używasz modułów zbierających dane.|"n" sekund. Domyślnie: "120" (dwie minuty).|
    |AgentCleanupTimeout|Liczba sekund oczekiwania na wszystkie agentów i ich modułów zbierających dane, aby oczyścić, przed zakończeniem przebiegu testu. Ta wartość powinna być dość duża, jeśli używasz modułów zbierających dane.|"n" sekund. Domyślnie: "120" (dwie minuty).|

- Agent testowy: *QTAgentService.exe.config*

    |Nazwa klucza|Opis|Wartość|
    |-|-----------------|-|
    |ControllerConnectionPeriodInSekundy|Liczba sekund między próbami nawiązania połączenia z kontrolerem.|"n" sekund. Domyślnie: "30" (trzydzieści sekund).|
    |Czas komunikacji zdalnejSekundy|Maksymalny czas, przez jaki połączenie komunikacji zdalnej może trwać w sekundach.|"n" sekund. Domyślnie: "600" (dziesięć minut).|
    |StopTestRunCallTimeoutInSekundy|Liczba sekund oczekiwania na wywołanie, aby zatrzymać przebieg testu.|"n" sekund. Domyślnie: "120" (dwie minuty).|
    |GetCollectorDataTimeout|Liczba sekund oczekiwania na moduł zbierający dane.|"n" sekund. Domyślnie: "300" (pięć minut).|

## <a name="to-specify-agent-timeout-options-for-a-test-controller"></a>Aby określić opcje limitu czasu agenta dla kontrolera testów

1. Otwórz plik konfiguracyjny *QTCcontroller.exe.config* XML znajdujący się w *pliku %ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

2. Znajdź `<appSettings>` znacznik.

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

3. Edytuj istniejącą wartość dla jednego z kluczy limitu czasu kontrolera testu. Na przykład można zmienić wartość domyślną klucza `AgentConnectionTimeoutInSeconds` z dwóch minut na trzy minuty:

    ```xml
    <add key="AgentConnectionTimeoutInSeconds" value="180"/>
    ```

    — lub —

    Dodaj dodatkowy klucz i określ wartość limitu czasu. Na przykład można dodać `AgentInitializeTimeout` klucz `<appSettings>` w sekcji i określić wartość pięciu minut:

    ```xml
    <appSettings>
            <add key="AgentInitializeTimeout" value="300"/>
    </appSettings>
    ```

## <a name="to-specify-agent-timeout-options-for-a-test-agent"></a>Aby określić opcje limitu czasu agenta dla agenta testowego

1. Otwórz plik konfiguracyjny *QTAgentService.exe.config* XML znajdujący się w *pliku %ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

2. Znajdź `<appSettings>` znacznik.

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

3. Edytuj istniejącą wartość dla jednego z kluczy limitu czasu agenta testowego. Na przykład można zmienić wartość domyślną klucza `ControllerConnectionPeriodInSeconds` z trzydziestu sekund na jedną minutę:

    ```xml
    <add key="ControllerConnectionPeriodInSeconds" value="60"/>
    ```

    — lub —

    Dodaj dodatkowy klucz i określ wartość limitu czasu. Na przykład można dodać `RemotingTimeoutSeconds` klucz `<appSettings>` w sekcji i określić wartość piętnaście minut:

    ```xml
    <appSettings>
            <add key=" RemotingTimeoutSeconds " value="900"/>
    </appSettings>
    ```

## <a name="see-also"></a>Zobacz też

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)
- [Modyfikowanie ustawień rejestrowania testu obciążenia](../test/modify-load-test-logging-settings.md)
- [Konfigurowanie portów dla kontrolerów testowych i agentów testowych](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [Jak: Powiązać kontroler testu lub agenta testowego z kartą sieciową](../test/how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter.md)
