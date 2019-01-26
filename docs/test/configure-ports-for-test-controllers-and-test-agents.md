---
title: Konfigurowanie portów dla kontrolerów testów i agentów testowych
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- firewalls, configuring for test agents
- firewalls, configuring for test controllers
- test agents, firewalls
- test controllers, firewalls
- agents, firewalls
- controllers, firewalls
ms.assetid: 211edbd7-9fe4-4251-ba85-8bec4363261b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.openlocfilehash: 82c1c3b23e705246e4319ec18fed0b6abaf79a8e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031542"
---
# <a name="configure-ports-for-test-controllers-and-test-agents"></a>Konfigurowanie portów dla kontrolerów testów i agentów testowych

Można zmienić domyślne porty przychodzące używane przez kontroler testów, agentem testowym a klientem. Może to być konieczne, jeśli próbujesz użyć kontrolera testów, agenta testowego lub klienta wraz z innym oprogramowaniem powodującą konflikt z ustawieniami portu. To kolejny powód, aby zmienić porty z powodu ograniczeń zapory między kontrolerem testów i klientem. W takim przypadku można ręcznie skonfigurować port, aby zapewnić Włączanie go dla zapory, tak aby kontroler testów mógł wysyłać wyniki do klienta.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Poniższa ilustracja przedstawia punkty połączenia między kontrolerem testów, agentem testowym a klienta. Przedstawia, które porty są używane dla połączeń przychodzących i wychodzących, a także ograniczenia zabezpieczeń używane na tych portach.

![Testowanie sterownika i test agent portów i zabezpieczeń](../test/media/test-controller-agent-firewall.png)

## <a name="incoming-connections"></a>Połączenia przychodzące

Domyślnym portem używanym przez kontroler testów jest 6901, a port domyślny agenta testowego to 6910. Klient używa portu losowego domyślnie, który jest używany do odbierania wyników testów z kontrolera testów. Dla wszystkich połączeń przychodzących kontroler testów uwierzytelnia podmiot wywołujący i weryfikuje, czy należy on do określonej grupy zabezpieczeń.

- **Kontroler testów** połączenia przychodzące są na porcie TCP 6901. Jeśli zachodzi potrzeba, można skonfigurować port przychodzący. Aby uzyskać więcej informacji, zobacz [Skonfiguruj porty przychodzące](#configure-the-incoming-ports).

    Kontroler testów musi być w stanie wykonać połączenie wychodzące do agentów testowych i do klienta.

    > [!NOTE]
    > Kontroler testów musi przychodzących **plików i drukarek udostępnianie** otwartego połączenia.

- **Agent testowy** połączenia przychodzące są na porcie TCP 6910. Jeśli zachodzi potrzeba, można skonfigurować port przychodzący. Aby uzyskać więcej informacji, zobacz [Skonfiguruj porty przychodzące](#configure-the-incoming-ports).

   Agent testowy musi być w stanie wykonać połączenie wychodzące do kontrolera testów.

- **Klient** domyślnie losowy port TCP jest używany dla połączeń przychodzących. Jeśli zachodzi potrzeba, można skonfigurować port przychodzący. Aby uzyskać więcej informacji, zobacz [Skonfiguruj porty przychodzące](#configure-the-incoming-ports).

   Gdy kontroler testów próbuje połączyć się z czas klienta pierwszy, może otrzymać powiadomienia o zaporze.

   W systemie Windows Server 2008, powiadomienia zapory są domyślnie wyłączone i trzeba ręcznie dodać wyjątki zapory dla programów klienckich (*devenv.exe*, *mstest.exe*, *mlm.exe*) tak, aby umożliwić akceptowanie połączeń przychodzących.

## <a name="outgoing-connections"></a>Połączenia wychodzące

Losowe porty TCP są używane dla wszystkich połączeń wychodzących.

- **Kontroler testów** kontroler testów musi być w stanie wykonać połączenie wychodzące do agentów i do klienta.

- **Agent testowy** agent testowy musi być w stanie wykonać połączenie wychodzące do kontrolera.

- **Klient** klient musi być w stanie wykonać połączenie wychodzące do kontrolera.

## <a name="configure-the-incoming-ports"></a>Skonfiguruj porty przychodzące

Postępując następująco, skonfiguruj porty dla kontrolera testów i agentów testowych.

- **Usługa kontrolera** Modyfikuj wartość portu edytując *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTCcontroller.exe.config* pliku:

    ```xml
    <appSettings>
      <add key="ControllerServicePort" value="6901"/>
    </appSettings>
    ```

- **Usługa agenta** modyfikuje portu, edytując *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTAgentService.exe.config* pliku:

    ```xml
    <appSettings>
      <add key="AgentServicePort" value="6910"/>
    </appSettings>
    ```

- **Klient** Dodaj następującą rejestru za pomocą Edytora rejestru (**DWORD**) wartości. Klient użyje jednego z portów z określonego zakresu do odbierania danych z kontrolera testów:

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeStart**

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeEnd**

## <a name="see-also"></a>Zobacz także

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)