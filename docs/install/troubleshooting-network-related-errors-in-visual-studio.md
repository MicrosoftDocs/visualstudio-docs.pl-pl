---
title: Rozwiązywanie problemów z błędami sieci lub serwera proxy
description: Rozwiązania związane z siecią lub serwer proxy błędy, które można napotkać podczas instalowania lub użyć programu Visual Studio za zaporą lub serwerem proxy.
ms.date: 05/22/2019
ms.topic: troubleshooting
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs, Visual Studio
- proxy errors, Visual Studio
ms.assetid: ''
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 27364bd028d9fb493da354d3bff7f11efe5f459d
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67825709"
---
# <a name="troubleshooting-network-related-errors-when-you-install-or-use-visual-studio"></a>Rozwiązywanie problemów z błędami związanych z siecią, podczas instalowania lub użyć programu Visual Studio

Mamy rozwiązań dla najbardziej typowe błędy związane z siecią lub serwera proxy, które można napotkać podczas instalowania lub używania programu Visual Studio za zaporą lub serwerem proxy.

## <a name="error-proxy-authorization-required"></a>Błąd: "Wymaga autoryzacji serwera proxy"

Ten błąd występuje zazwyczaj, gdy użytkownicy są połączeni z Internetem za pośrednictwem serwera proxy i serwer proxy blokuje wywołania, które program Visual Studio sprawia, że do niektórych zasobów sieciowych.

### <a name="to-fix-this-proxy-error"></a>Aby naprawić ten błąd serwera proxy

- Uruchom ponownie program Visual Studio. Powinna zostać wyświetlona okno dialogowe uwierzytelniania serwera proxy. Wprowadź swoje poświadczenia, po wyświetleniu monitu w oknie dialogowym.

- Jeśli ponowne uruchomienie programu Visual Studio nie rozwiązuje ten problem, może to oznaczać, serwer proxy nie jest wyświetlany monit o poświadczenia dla protokołu http:&#47;&#47;go.microsoft.com adresy, ale jest to spowodowane &#42;. visualStudio.microsoft.com adresów. Na tych serwerach należy rozważyć dodanie następujących adresów URL do listy dozwolonych, aby odblokować wszystkie w scenariuszach logowania w programie Visual Studio:

  - &#42;.windows.net

  - &#42;.microsoftonline.com

  - &#42;.visualstudio.microsoft.com

  - &#42;.microsoft.com

  - &#42;.live.com

- W przeciwnym razie możesz usunąć http:&#47;&#47;go.microsoft.com adresów z listy dozwolonych, aby w oknie dialogowym uwierzytelniania serwera proxy, pojawia się dla obu protokołu http:&#47;&#47;go.microsoft.com adres i punkty końcowe serwera, gdy program Visual Studio ponownie uruchomione.

  -LUB-

- Jeśli chcesz używać Twoich poświadczeń domyślne na serwerze proxy, należy wykonać następujące czynności:

::: moniker range="vs-2017"

  1. Znajdź **devenv.exe.config** (plik devenv.exe w konfiguracji) w: **%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** lub **% ProgramFiles (x86) %\Microsoft Wizualne Studio\2017\Enterprise\Common7\IDE**.

  2. Plik konfiguracyjny zawiera `<system.net>` zablokować, a następnie dodaj ten kod:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Adres serwera proxy poprawne należy wstawić dla sieci w `proxyaddress="<http://<yourproxy:port#>`.

     > [!NOTE]
     > Aby uzyskać więcej informacji, zobacz [ &lt;defaultProxy&gt; — Element (ustawienia sieci)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) i [ &lt;proxy&gt; — Element (ustawienia sieci)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings) stron.

::: moniker-end

::: moniker range="vs-2019"

  1. Znajdź **devenv.exe.config** (plik devenv.exe w konfiguracji) w: **%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE** lub **% ProgramFiles (x86) %\Microsoft Wizualne Studio\2019\Enterprise\Common7\IDE**.

  2. Plik konfiguracyjny zawiera `<system.net>` zablokować, a następnie dodaj ten kod:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Adres serwera proxy poprawne należy wstawić dla sieci w `proxyaddress="<http://<yourproxy:port#>`.

     > [!NOTE]
     > Aby uzyskać więcej informacji, zobacz [ &lt;defaultProxy&gt; — Element (ustawienia sieci)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) i [ &lt;proxy&gt; — Element (ustawienia sieci)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings) stron.

::: moniker-end

## <a name="error-the-underlying-connection-was-closed"></a>Błąd: "Połączenie podstawowe zostało zamknięte"

Jeśli używasz programu Visual Studio w sieci prywatnej z zaporą, Visual Studio nie można nawiązać połączenia z niektórych zasobów sieciowych. Te zasoby mogą obejmować usługom DevOps platformy Azure do logowania i licencjonowania NuGet i usług platformy Azure. Visual Studio nie może połączyć się z tych zasobów, może zostać wyświetlony następujący komunikat o błędzie:

  **Połączenie podstawowe zostało zamknięte: Wystąpił nieoczekiwany błąd podczas wysyłania**

Visual Studio używa protokołu Transport Layer Security (TLS) 1.2, połączyć się z zasobami sieciowymi. Gdy program Visual Studio używa protokołu TLS 1.2, urządzenia zabezpieczeń w prywatnych sieciach zablokować niektóre połączenia z serwerem.

### <a name="to-fix-this-connection-error"></a>Aby naprawić ten błąd połączenia

Włącz połączenia dla następujących adresów URL:

- https:&#47;&#47;management.core.windows.net

- https:&#47;&#47;app.vssps.visualstudio.com

- https:&#47;&#47;login.microsoftonline.com

- https:&#47;&#47;login.live.com

- https:&#47;&#47;go.microsoft.com

- https:&#47;&#47;graph.windows.net

- https:&#47;&#47;app.vsspsext.visualstudio.com

- &#42;. azurewebsites.net (dla połączenia platformy Azure)

- &#42;.visualstudio.microsoft.com

- CDN.vsassets.IO (hosty usługa content delivery network lub sieci CDN, zawartości)

- &#42;. gallerycdn.vsassets.io (hosty rozszerzenia usługom DevOps platformy Azure)

- static2.sharepointonline.com (hosty zasobów używanych przez program Visual Studio w zestawie danych sieci szkieletowej interfejsu użytkownika pakietu Office, takie jak czcionki)

- &#42;. nuget.org (w przypadku połączenia narzędzia NuGet)

  > [!NOTE]
  > Prywatnego, że adresy URL serwerów NuGet mogą nie zostać zawarte na tej liście. Możesz sprawdzić, czy dla serwerów NuGet, które korzystasz z % APPData%\Nuget\NuGet.Config.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Instalowanie i używanie programu Visual Studio za zaporą lub serwerem proxy](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Podręcznik administratora w usłudze Visual Studio](visual-studio-administrator-guide.md)
* [Instalowanie programu Visual Studio](install-visual-studio.md)
