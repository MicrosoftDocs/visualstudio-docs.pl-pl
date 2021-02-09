---
title: Konfigurowanie portów dla kontrolerów testów i agentów testowych
description: Dowiedz się, jak zmienić domyślne porty przychodzące używane przez kontroler testów, agenta testowego i klienta, aby uniknąć konfliktów z innym oprogramowaniem.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- firewalls, configuring for test agents
- firewalls, configuring for test controllers
- test agents, firewalls
- test controllers, firewalls
- agents, firewalls
- controllers, firewalls
ms.assetid: 211edbd7-9fe4-4251-ba85-8bec4363261b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 78c6dd0f9ffa89f7b1a2ac7ac7a2344b67a47970
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868052"
---
# <a name="configure-ports-for-test-controllers-and-test-agents"></a>Konfigurowanie portów dla kontrolerów testów i agentów testowych

Można zmienić domyślne porty przychodzące używane przez kontroler testów, agenta testowego i klienta. Może to być konieczne, jeśli próbujesz użyć kontrolera testów, agenta testowego lub klienta wraz z innym oprogramowaniem, które powoduje konflikt z ustawieniami portu. Kolejną przyczyną zmiany portów jest ograniczenie zapory między kontrolerem testów a klientem. W takim przypadku warto ręcznie skonfigurować port, aby włączyć go dla zapory, aby kontroler testów mógł wysyłać wyniki do klienta.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Poniższa ilustracja przedstawia punkty połączenia między kontrolerem testów, agentem testowym i klientem. Przedstawia on, które porty są używane do połączeń przychodzących i wychodzących, a także ograniczenia zabezpieczeń używane na tych portach.

![Porty kontrolerów testów i agentów testowych oraz zabezpieczenia](../test/media/test-controller-agent-firewall.png)

## <a name="incoming-connections"></a>Połączenia przychodzące

Domyślnym portem używanym przez kontroler testów jest 6901, a domyślnym portem agenta testowego jest 6910. Klient domyślnie używa portu losowego, który jest używany do odbierania wyników testów z kontrolera testów. W przypadku wszystkich połączeń przychodzących kontroler testów uwierzytelnia osobę wywołującą i weryfikuje, czy należy ona do określonej grupy zabezpieczeń.

- **Test Controller** Połączenia przychodzące są na porcie TCP 6901. Jeśli zachodzi taka potrzeba, można skonfigurować port przychodzący. Aby uzyskać więcej informacji, zobacz [Konfigurowanie portów przychodzących](#configure-the-incoming-ports).

    Kontroler testów musi być w stanie wykonać połączenie wychodzące do agentów testowych i do klienta.

    > [!NOTE]
    > Kontroler testów wymaga otwartego połączenia **udostępniania plików i drukarek** .

- **Agent testowy** Połączenia przychodzące są na porcie TCP 6910. Jeśli zachodzi taka potrzeba, można skonfigurować port przychodzący. Aby uzyskać więcej informacji, zobacz [Konfigurowanie portów przychodzących](#configure-the-incoming-ports).

   Agent testowy musi być w stanie nawiązać połączenie wychodzące z kontrolerem testów.

- **Klient** Domyślnie losowy port TCP jest używany dla połączeń przychodzących. Jeśli zachodzi taka potrzeba, można skonfigurować port przychodzący. Aby uzyskać więcej informacji, zobacz [Konfigurowanie portów przychodzących](#configure-the-incoming-ports).

   Możesz otrzymywać powiadomienia zapory, gdy kontroler testów próbuje nawiązać połączenie z klientem po raz pierwszy.

   W systemie Windows Server 2008 powiadomienia dotyczące zapory są domyślnie wyłączone i należy ręcznie dodać wyjątki zapory dla programów klienckich (*devenv.exe*, *mstest.exe*, *mlm.exe*), aby umożliwić akceptowanie połączeń przychodzących.

## <a name="outgoing-connections"></a>Połączenia wychodzące

Losowe porty TCP są używane dla wszystkich połączeń wychodzących.

- **Test Controller** Kontroler testów musi być w stanie wykonać połączenie wychodzące do agentów i do klienta.

- **Agent testowy** Agent testowy musi być w stanie wykonać połączenie wychodzące do kontrolera.

- **Klient** Klient musi mieć możliwość nawiązania połączenia wychodzącego z kontrolerem.

## <a name="configure-the-incoming-ports"></a>Konfigurowanie portów przychodzących

Postępuj zgodnie z tymi instrukcjami, aby skonfigurować porty dla kontrolera testów i agentów testowych.

- **Usługa kontrolera** Zmodyfikuj wartość portu, edytując plik *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTCcontroller.exe.config* :

    ```xml
    <appSettings>
      <add key="ControllerServicePort" value="6901"/>
    </appSettings>
    ```

- **Usługa agenta** Zmodyfikuj port, edytując plik *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTAgentService.exe.config* :

    ```xml
    <appSettings>
      <add key="AgentServicePort" value="6910"/>
    </appSettings>
    ```

- **Klient** Użyj edytora rejestru, aby dodać następujące wartości rejestru (**DWORD**). Klient użyje jednego z portów z określonego zakresu na potrzeby otrzymywania danych z kontrolera testów:

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeStart**

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeEnd**

## <a name="see-also"></a>Zobacz też

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)
