---
title: Limitów czasu dla kontrolerów testów i agentów testowych
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- agents, configuring
- agetns, timeouts
- controllers, configuring
- controllers, timeouts
ms.assetid: 777d0db5-0073-458a-a2a3-58b1c1f24c60
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5d05ed422f5d08a1a8c7d4f1b2444d9b751aafaf
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55929235"
---
# <a name="how-to-specify-timeout-periods-for-test-controllers-and-test-agents"></a>Instrukcje: Określanie limitów czasu dla kontrolerów testów i agentów testowych

Kontroler testów i agenta testowego ma kilka ustawień limitu czasu, które określają, jak długo należy czekać na odpowiedzi od siebie lub ze źródła danych, zakończy się niepowodzeniem z powodu błędu. W pewnych okolicznościach może być konieczne edytowanie wartości limitu czasu, aby zaspokoić potrzeby topologii lub inne problemy środowiska. Aby edytować wartości limitu czasu, Edytuj plik konfiguracyjny XML, który jest skojarzony z kontrolerem testów lub agenta testowego, zgodnie z opisem w poniższych procedur.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Aby edytować kontroler testów lub różne ustawienia limitu czasu agenta testowego, zmodyfikuj następujące pliki konfiguracji, za pomocą nazw kluczy i wartości w tabelach:

-   Kontroler testów: *QTController.exe.config*

    |Nazwa klucza|Opis|Wartość|
    |-|-----------------|-|
    |AgentConnectionTimeoutInSeconds|Liczba sekund oczekiwania na żądanie ping do agenta przed połączenie jest uznawane za utracone.|"n" Liczba sekund.|
    |AgentSyncTimeoutInSeconds|Podczas uruchamiania synchronizacji testu, liczba sekund oczekiwania na wszystkich agentów do synchronizacji przed przerwaniem.|"n" Liczba sekund.|
    |AgentInitializeTimeout|Liczba sekund oczekiwania dla wszystkich agentów i ich modułów zbierających dane, aby zainicjować na początku testu uruchomić przed przerwaniem przebiegu testu. Ta wartość powinna być umiarkowanie duża, jeśli za pomocą modułów zbierających dane.|"n" Liczba sekund. Wartość domyślna: "120" (dwie minuty).|
    |AgentCleanupTimeout|Liczba sekund oczekiwania dla wszystkich agentów i ich modułów zbierających dane, aby wyczyścić, przed wykonaniem testów przebieg. Ta wartość powinna być umiarkowanie duża, jeśli za pomocą modułów zbierających dane.|"n" Liczba sekund. Wartość domyślna: "120" (dwie minuty).|

-   Agent testowy: *QTAgentService.exe.config*

    |Nazwa klucza|Opis|Wartość|
    |-|-----------------|-|
    |ControllerConnectionPeriodInSeconds|Liczba sekund między próbami nawiązania połączenia z kontrolerem.|"n" Liczba sekund. Wartość domyślna: "30" (trzydzieści sekund).|
    |RemotingTimeoutSeconds|Maksymalny czas wywołanie komunikacji zdalnej może trwać w sekundach.|"n" Liczba sekund. Wartość domyślna: "600" (dziesięć minut).|
    |StopTestRunCallTimeoutInSeconds|Liczba sekund oczekiwania, aż wywołanie zatrzyma przebieg testu.|"n" Liczba sekund. Wartość domyślna: "120" (dwie minuty).|
    |GetCollectorDataTimeout|Liczba sekund oczekiwania na moduł zbierający dane.|"n" Liczba sekund. Wartość domyślna: "300" (pięć minut).|

## <a name="to-specify-agent-timeout-options-for-a-test-controller"></a>Aby określić opcje limitu czasu agenta dla kontrolera testów

1. Otwórz *QTCcontroller.exe.config* plik konfiguracyjny XML znajdujący się w *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

2. Znajdź `<appSettings>` tagu.

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

    —lub—

    Dodaj dodatkowy klucz i określ wartość limitu czasu. Na przykład można dodać `AgentInitializeTimeout` w `<appSettings>` sekcji, a następnie określić wartość pięciu minut:

    ```xml
    <appSettings>
            <add key="AgentInitializeTimeout" value="300"/>
    </appSettings>
    ```

## <a name="to-specify-agent-timeout-options-for-a-test-agent"></a>Aby określić opcje limitu czasu agenta dla agenta testowego

1. Otwórz *QTAgentService.exe.config* plik konfiguracyjny XML znajdujący się w *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

2. Znajdź `<appSettings>` tagu.

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

3. Edytuj istniejącą wartość dla jednego z kluczy limitu czasu agenta testowego. Na przykład można zmienić wartość domyślną dla klucza `ControllerConnectionPeriodInSeconds` z trzydziestu sekund na jedną minutę:

    ```xml
    <add key="ControllerConnectionPeriodInSeconds" value="60"/>
    ```

    —lub—

    Dodaj dodatkowy klucz i określ wartość limitu czasu. Na przykład można dodać `RemotingTimeoutSeconds` w `<appSettings>` sekcji, a następnie określić wartość piętnastu minut:

    ```xml
    <appSettings>
            <add key=" RemotingTimeoutSeconds " value="900"/>
    </appSettings>
    ```

## <a name="see-also"></a>Zobacz także

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)
- [Modyfikowanie ustawień rejestrowania testu obciążeniowego](../test/modify-load-test-logging-settings.md)
- [Konfigurowanie portów dla kontrolerów testów i agentów testowych](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [Instrukcje: Określ maksymalny rozmiar pliku dziennika](../test/how-to-specify-the-maximum-size-for-the-log-file.md)
- [Instrukcje: Powiąż kontroler testów lub agenta testowego z kartą sieciową](../test/how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter.md)