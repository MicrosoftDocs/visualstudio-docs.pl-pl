---
title: Konfigurowanie portów dla kontrolerów testowych i agentów testowych
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2228f5ac4dce4743fa6dafbb321f0106b5d6cc11
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595946"
---
# <a name="configure-ports-for-test-controllers-and-test-agents"></a>Konfigurowanie portów dla kontrolerów testowych i agentów testowych

Można zmienić domyślne porty przychodzące używane przez kontrolera testów, agenta testowego i klienta. Może to być konieczne, jeśli próbujesz użyć kontrolera testów, agenta testowego lub klienta wraz z innym oprogramowaniem, które powoduje konflikt z ustawieniami portu. Innym powodem, aby zmienić porty jest ze względu na ograniczenie zapory między kontrolerem testów i klienta. W takim przypadku można ręcznie skonfigurować port, aby pomieścić włączenie go dla zapory, tak aby kontroler testów może wysyłać wyniki do klienta.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Na poniższej ilustracji przedstawiono punkty połączenia między kontrolerem testów, agentem testowym a klientem. Określa, które porty są używane do połączeń przychodzących i wychodzących, a także ograniczenia zabezpieczeń stosowane w tych portach.

![Porty i zabezpieczenia kontrolera testowego i agenta testowego](../test/media/test-controller-agent-firewall.png)

## <a name="incoming-connections"></a>Połączenia przychodzące

Domyślny port używany przez kontroler testowy to 6901, a domyślny port agenta testowego to 6910. Klient domyślnie używa losowego portu, który jest używany do odbierania wyników testów z kontrolera testów. Dla wszystkich połączeń przychodzących kontroler testu uwierzytelnia stronę wywołującą i sprawdza, czy należy do określonej grupy zabezpieczeń.

- **Kontroler testowy** Połączenia przychodzące znajdują się na porcie TCP 6901. W razie potrzeby można skonfigurować port przychodzący. Aby uzyskać więcej informacji, zobacz [Konfigurowanie portów przychodzących](#configure-the-incoming-ports).

    Kontroler testów musi mieć możliwość nawiązywać połączenia wychodzącego z agentami testowymi i klientem.

    > [!NOTE]
    > Kontroler testowy wymaga otwartego połączenia **udostępniania plików i drukarek.**

- **Agent testowy** Połączenia przychodzące są na porcie TCP 6910. W razie potrzeby można skonfigurować port przychodzący. Aby uzyskać więcej informacji, zobacz [Konfigurowanie portów przychodzących](#configure-the-incoming-ports).

   Agent testowy musi mieć możliwość nawiązywać połączenia wychodzącego z kontrolerem testów.

- **Klient** Domyślnie losowy port TCP jest używany dla połączeń przychodzących. W razie potrzeby można skonfigurować port przychodzący. Aby uzyskać więcej informacji, zobacz [Konfigurowanie portów przychodzących](#configure-the-incoming-ports).

   Możesz otrzymywać powiadomienia zapory, gdy kontroler testów próbuje połączyć się z klientem po raz pierwszy.

   W systemie Windows Server 2008 powiadomienia zapory są domyślnie wyłączone i należy ręcznie dodać wyjątki zapory dla programów klienckich (*devenv.exe*, *mstest.exe*, *mlm.exe*), aby mogła akceptować połączenia przychodzące.

## <a name="outgoing-connections"></a>Połączenia wychodzące

Losowe porty TCP są używane dla wszystkich połączeń wychodzących.

- **Kontroler testowy** Kontroler testu musi mieć możliwość nawiązywać połączenia wychodzącego z agentami i klientem.

- **Agent testowy** Agent testowy musi mieć możliwość nawiązywać połączenia wychodzącego z kontrolerem.

- **Klient** Klient musi mieć możliwość nawiązywać połączenia wychodzącego z kontrolerem.

## <a name="configure-the-incoming-ports"></a>Konfigurowanie portów przychodzących

Postępuj zgodnie z tymi wskazówkami, aby skonfigurować porty dla kontrolera testów i agentów testowych.

- **Usługa kontrolera** Zmodyfikuj wartość portu, edytując plik *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTCcontroller.exe.config:*

    ```xml
    <appSettings>
      <add key="ControllerServicePort" value="6901"/>
    </appSettings>
    ```

- **Usługa agenta** Zmodyfikuj port, edytując plik *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTAgentService.exe.config:*

    ```xml
    <appSettings>
      <add key="AgentServicePort" value="6910"/>
    </appSettings>
    ```

- **Klient** Użyj edytora rejestru, aby dodać następujące wartości rejestru (**DWORD**). Klient użyje jednego z portów z określonego zakresu do odbierania danych z kontrolera testów:

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeStart**

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeEnd**

## <a name="see-also"></a>Zobacz też

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)
