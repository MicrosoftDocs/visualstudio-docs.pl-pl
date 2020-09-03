---
title: Limity czasu dla kontrolerów testów i agentów testowych
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- agents, configuring
- agetns, timeouts
- controllers, configuring
- controllers, timeouts
ms.assetid: 777d0db5-0073-458a-a2a3-58b1c1f24c60
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7b06dc7d363cefd568a6e1432582744f486fa222
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287288"
---
# <a name="how-to-specify-timeout-periods-for-test-controllers-and-test-agents"></a>Instrukcje: Określanie okresów limitu czasu dla kontrolerów testów i agentów testowych

Kontroler testów i agent testowy mają kilka ustawień limitu czasu, które określają, jak długo powinny czekać na odpowiedzi ze sobą lub ze źródła danych przed błędem. W pewnych okolicznościach może być konieczne Edytowanie wartości limitu czasu w celu spełnienia wymagań topologii lub innych problemów ze środowiskiem. Aby edytować wartości limitu czasu, edytuj plik konfiguracyjny XML, który jest skojarzony z kontrolerem testów lub agentem testowym, zgodnie z poniższymi procedurami.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Aby edytować kontroler testów lub różne ustawienia limitu czasu agenta testowego, należy zmodyfikować następujące pliki konfiguracji przy użyciu nazw kluczy i wartości w tabelach:

- Kontroler testów: *QTController.exe.config*

    |Nazwa klucza|Opis|Wartość|
    |-|-----------------|-|
    |AgentConnectionTimeoutInSeconds|Liczba sekund oczekiwania na żądanie ping agenta przed utratą połączenia.|"n" s.|
    |AgentSyncTimeoutInSeconds|Po uruchomieniu synchronizacji przebiegu testowego, liczba sekund oczekiwania na synchronizację wszystkich agentów przed przerwaniem przebiegu.|"n" s.|
    |AgentInitializeTimeout|Liczba sekund oczekiwania na zainicjowanie wszystkich agentów i ich modułów zbierających dane na początku przebiegu testowego, przed przerwaniem przebiegu testu. Ta wartość powinna być odpowiednio duża, jeśli są używane moduły zbierające dane.|"n" s. Wartość domyślna: "120" (dwie minuty).|
    |AgentCleanupTimeout|Liczba sekund oczekiwania na oczyszczenie wszystkich agentów i ich modułów zbierających dane przed ukończeniem przebiegu testu. Ta wartość powinna być odpowiednio duża, jeśli są używane moduły zbierające dane.|"n" s. Wartość domyślna: "120" (dwie minuty).|

- Agent testowy: *QTAgentService.exe.config*

    |Nazwa klucza|Opis|Wartość|
    |-|-----------------|-|
    |ControllerConnectionPeriodInSeconds|Liczba sekund między próbami połączenia z kontrolerem.|"n" s. Wartość domyślna: "30" (trzydzieści sekund).|
    |RemotingTimeoutSeconds|Maksymalny czas, przez jaki połączenie zdalne może trwać w kilka sekund.|"n" s. Wartość domyślna: "600" (dziesięć minut).|
    |StopTestRunCallTimeoutInSeconds|Liczba sekund oczekiwania na wywołanie zatrzymania przebiegu testowego.|"n" s. Wartość domyślna: "120" (dwie minuty).|
    |GetCollectorDataTimeout|Liczba sekund oczekiwania na moduł zbierający dane.|"n" s. Wartość domyślna: "300" (pięć minut).|

## <a name="to-specify-agent-timeout-options-for-a-test-controller"></a>Aby określić opcje limitu czasu agenta dla kontrolera testów

1. Otwórz plik konfiguracji XML *QTCcontroller.exe.config* znajdujący się w lokalizacji *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

2. Znajdź `<appSettings>` tag.

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

3. Edytuj istniejącą wartość dla jednego z kluczy limitu czasu kontrolera testów. Na przykład można zmienić wartość domyślną dla klucza `AgentConnectionTimeoutInSeconds` z dwóch minut na trzy minuty:

    ```xml
    <add key="AgentConnectionTimeoutInSeconds" value="180"/>
    ```

    -lub-

    Dodaj dodatkowy klucz i określ wartość limitu czasu. Na przykład można dodać `AgentInitializeTimeout` klucz w `<appSettings>` sekcji i określić wartość pięć minut:

    ```xml
    <appSettings>
            <add key="AgentInitializeTimeout" value="300"/>
    </appSettings>
    ```

## <a name="to-specify-agent-timeout-options-for-a-test-agent"></a>Aby określić opcje limitu czasu agenta dla agenta testowego

1. Otwórz plik konfiguracji XML *QTAgentService.exe.config* znajdujący się w lokalizacji *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

2. Znajdź `<appSettings>` tag.

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

3. Edytuj istniejącą wartość dla jednego z kluczy limitu czasu agenta testowego. Na przykład można zmienić wartość domyślną dla klucza `ControllerConnectionPeriodInSeconds` z 30 sekund na jedną minutę:

    ```xml
    <add key="ControllerConnectionPeriodInSeconds" value="60"/>
    ```

    -lub-

    Dodaj dodatkowy klucz i określ wartość limitu czasu. Na przykład można dodać `RemotingTimeoutSeconds` klucz w `<appSettings>` sekcji i określić wartość 15 minut:

    ```xml
    <appSettings>
            <add key=" RemotingTimeoutSeconds " value="900"/>
    </appSettings>
    ```

## <a name="see-also"></a>Zobacz też

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)
- [Modyfikowanie ustawień rejestrowania testu obciążenia](../test/modify-load-test-logging-settings.md)
- [Konfigurowanie portów dla kontrolerów testów i agentów testowych](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [Instrukcje: powiązanie kontrolera testów lub agenta testowego z kartą sieciową](../test/how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter.md)
