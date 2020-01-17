---
title: Rozwiązywanie problemów z błędami sieci lub serwera proxy
description: Rozwiązania związane z siecią lub serwer proxy błędy, które można napotkać podczas instalowania lub użyć programu Visual Studio za zaporą lub serwerem proxy.
ms.date: 10/29/2019
ms.topic: troubleshooting
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs, Visual Studio
- proxy errors, Visual Studio
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 0e127006976c484d1e4fc2fe011af979af7eb7a9
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114987"
---
# <a name="troubleshoot-network-related-errors-when-you-install-or-use-visual-studio"></a>Rozwiązywanie problemów związanych z siecią podczas instalowania programu Visual Studio lub korzystania z niego

Mamy rozwiązań dla najbardziej typowe błędy związane z siecią lub serwera proxy, które można napotkać podczas instalowania lub używania programu Visual Studio za zaporą lub serwerem proxy.

## <a name="error-proxy-authorization-required"></a>Błąd: "serwer Proxy wymaga autoryzacji"

Ten błąd występuje zazwyczaj, gdy użytkownicy są połączeni z Internetem za pośrednictwem serwera proxy i serwer proxy blokuje wywołania, które program Visual Studio sprawia, że do niektórych zasobów sieciowych.

### <a name="to-fix-this-proxy-error"></a>Aby naprawić ten błąd serwera proxy

- Uruchom ponownie program Visual Studio. Powinna zostać wyświetlona okno dialogowe uwierzytelniania serwera proxy. Wprowadź swoje poświadczenia, po wyświetleniu monitu w oknie dialogowym.

- Jeśli ponowne uruchomienie programu Visual Studio nie rozwiąże problemu, może to oznaczać, że serwer proxy nie wyświetli monitu o&#47;&#47;podanie poświadczeń dla adresów http: &#42;go.Microsoft.com, ale jest to dla adresów visualStudio.Microsoft.com. W przypadku tych serwerów rozważ dodanie następujących adresów URL do listy dozwolonych, aby odblokować wszystkie scenariusze logowania w programie Visual Studio:

  - &#42;.windows.net

  - &#42;.microsoftonline.com

  - &#42;.visualstudio.microsoft.com

  - &#42;.microsoft.com

  - &#42;.live.com

- Można w przeciwnym razie usunąć adres http&#47;&#47;: go.Microsoft.com z listy dozwolonych, tak aby w oknie dialogowym uwierzytelniania serwera proxy pojawia się zarówno adres&#47;&#47;http: go.Microsoft.com, jak i punkty końcowe serwera po ponownym uruchomieniu programu Visual Studio.

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
     > Aby uzyskać więcej informacji, zobacz [&lt;defaultProxy&gt; elementu (Ustawienia sieci)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) i [&lt;elementu&gt; proxy (Ustawienia sieci)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings) .

::: moniker-end

::: moniker range="vs-2019"

  1. Znajdź **devenv. exe. config** (plik konfiguracyjny devenv. exe) w: **%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE** lub **% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Enterprise\Common7\IDE**.

  2. Plik konfiguracyjny zawiera `<system.net>` zablokować, a następnie dodaj ten kod:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Adres serwera proxy poprawne należy wstawić dla sieci w `proxyaddress="<http://<yourproxy:port#>`.

     > [!NOTE]
     > Aby uzyskać więcej informacji, zobacz [&lt;defaultProxy&gt; elementu (Ustawienia sieci)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) i [&lt;elementu&gt; proxy (Ustawienia sieci)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings) .

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

## <a name="error-failed-to-parse-id-from-parent-process"></a>Błąd: "nie można przeanalizować identyfikatora z procesu nadrzędnego"

Ten komunikat o błędzie może pojawić się podczas korzystania z programu inicjującego programu Visual Studio i pliku Response. JSON na dysku sieciowym. Źródłem błędu jest Kontrola konta użytkownika w systemie Windows.

Przyczyny tego błędu mogą być następujące: zamapowany dysk sieciowy lub udział [UNC](/dotnet/standard/io/file-path-formats#unc-paths) jest połączony z tokenem dostępu użytkownika. Po włączeniu funkcji Kontrola konta użytkownika tworzone są dwa [tokeny dostępu](/windows/win32/secauthz/access-tokens) użytkowników: jeden *z* dostępem administratora i jeden *bez* dostępu administratora. Po utworzeniu dysku sieciowego lub udziału jest z nim połączony bieżący token dostępu użytkownika. Ponieważ program inicjujący musi być uruchomiony jako administrator, nie będzie mógł uzyskać dostępu do dysku sieciowego ani udziału, jeśli dysk lub udział nie są połączone z tokenem dostępu użytkownika, który ma dostęp administratora.

### <a name="to-fix-this-error"></a>Aby naprawić ten błąd

Możesz użyć polecenia `net use` lub zmienić ustawienia funkcji Kontrola konta zasady grupy użytkownika. Aby uzyskać więcej informacji o tych obejść i sposobach ich implementacji, zobacz następujące artykuły pomocy technicznej firmy Microsoft:

* [Zamapowane dyski nie są dostępne z poziomu monitu o podniesionych uprawnieniach, jeśli kontrola konta użytkownika jest skonfigurowana pod kątem "Monituj o poświadczenia" w systemie Windows](https://support.microsoft.com/help/3035277/mapped-drives-are-not-available-from-an-elevated-prompt-when-uac-is-co)
* [Programy mogą nie być w stanie uzyskać dostępu do niektórych lokalizacji sieciowych po włączeniu kontroli konta użytkownika w systemach operacyjnych Windows](https://support.microsoft.com/en-us/help/937624/programs-may-be-unable-to-access-some-network-locations-after-you-turn)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Instalowanie i używanie programu Visual Studio za zaporą lub serwerem proxy](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Podręcznik administratora w usłudze Visual Studio](visual-studio-administrator-guide.md)
* [Instalowanie programu Visual Studio](install-visual-studio.md)
