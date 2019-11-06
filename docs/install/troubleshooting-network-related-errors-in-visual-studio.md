---
title: Rozwiązywanie problemów z błędami sieci lub serwera proxy
description: Znajdź rozwiązania błędów związanych z siecią lub serwerem proxy, które mogą wystąpić podczas instalowania programu Visual Studio lub korzystania z niego za zaporą lub serwerem proxy.
ms.date: 10/29/2019
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
ms.openlocfilehash: f585a4ee58408e5f48c875602ba5531419dfd2ff
ms.sourcegitcommit: 77ef1dcc71057cd5fdc4733ff0cb6085bd6113e0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/06/2019
ms.locfileid: "73661826"
---
# <a name="troubleshoot-network-related-errors-when-you-install-or-use-visual-studio"></a>Rozwiązywanie problemów związanych z siecią podczas instalowania programu Visual Studio lub korzystania z niego

Mamy rozwiązania typowych błędów związanych z siecią lub serwerem proxy, które mogą wystąpić podczas instalowania programu Visual Studio lub korzystania z niego za zaporą lub serwerem proxy.

## <a name="error-proxy-authorization-required"></a>Błąd: "wymagane autoryzacja serwera proxy"

Ten błąd występuje zazwyczaj, gdy użytkownicy są połączeni z Internetem za pomocą serwera proxy, a serwer proxy blokuje wywołania, które program Visual Studio wprowadza do niektórych zasobów sieciowych.

### <a name="to-fix-this-proxy-error"></a>Aby naprawić ten błąd serwera proxy

- Uruchom ponownie program Visual Studio. Powinno zostać wyświetlone okno dialogowe uwierzytelnianie serwera proxy. Wprowadź swoje poświadczenia po wyświetleniu monitu w oknie dialogowym.

- Jeśli ponowne uruchomienie programu Visual Studio nie rozwiąże problemu, może to oznaczać, że serwer proxy nie wyświetli monitu o&#47;&#47;podanie poświadczeń dla adresów http: &#42;go.Microsoft.com, ale jest to dla adresów visualStudio.Microsoft.com. W przypadku tych serwerów rozważ dodanie następujących adresów URL do listy dozwolonych, aby odblokować wszystkie scenariusze logowania w programie Visual Studio:

  - &#42;. windows.net

  - &#42;. microsoftonline.com

  - &#42;. visualstudio.microsoft.com

  - &#42;. microsoft.com

  - &#42;. live.com

- Można w przeciwnym razie usunąć adres http&#47;&#47;: go.Microsoft.com z listy dozwolonych, tak aby w oknie dialogowym uwierzytelniania serwera proxy pojawia się zarówno adres&#47;&#47;http: go.Microsoft.com, jak i punkty końcowe serwera, gdy program Visual Studio jest uruchomieniu.

  Oraz

- Jeśli chcesz użyć domyślnych poświadczeń z serwerem proxy, możesz wykonać następujące czynności:

::: moniker range="vs-2017"

  1. Znajdź **devenv. exe. config** (plik konfiguracyjny devenv. exe) w: **%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** lub **% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE**.

  2. W pliku konfiguracji Znajdź blok `<system.net>`, a następnie Dodaj następujący kod:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Należy wstawić prawidłowy adres serwera proxy dla sieci w `proxyaddress="<http://<yourproxy:port#>`.

     > [!NOTE]
     > Aby uzyskać więcej informacji, zobacz [&lt;defaultProxy&gt; elementu (Ustawienia sieci)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) i [&lt;elementu&gt; proxy (Ustawienia sieci)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings) .

::: moniker-end

::: moniker range="vs-2019"

  1. Znajdź **devenv. exe. config** (plik konfiguracyjny devenv. exe) w: **%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE** lub **% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Enterprise\Common7\IDE**.

  2. W pliku konfiguracji Znajdź blok `<system.net>`, a następnie Dodaj następujący kod:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Należy wstawić prawidłowy adres serwera proxy dla sieci w `proxyaddress="<http://<yourproxy:port#>`.

     > [!NOTE]
     > Aby uzyskać więcej informacji, zobacz [&lt;defaultProxy&gt; elementu (Ustawienia sieci)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) i [&lt;elementu&gt; proxy (Ustawienia sieci)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings) .

::: moniker-end

## <a name="error-the-underlying-connection-was-closed"></a>Błąd: "Połączenie podstawowe zostało zamknięte"

Jeśli używasz programu Visual Studio w sieci prywatnej, która ma zaporę, program Visual Studio może nie być w stanie połączyć się z niektórymi zasobami sieciowymi. Te zasoby mogą obejmować Azure DevOps Services logowania i licencjonowania, NuGet i usług platformy Azure. Jeśli program Visual Studio nie może nawiązać połączenia z jednym z tych zasobów, może zostać wyświetlony następujący komunikat o błędzie:

  **Połączenie podstawowe zostało zamknięte: Wystąpił nieoczekiwany błąd podczas wysyłania**

Program Visual Studio używa protokołu Transport Layer Security (TLS) 1,2 do nawiązywania połączenia z zasobami sieciowymi. Urządzenia zabezpieczeń w niektórych sieciach prywatnych blokują niektóre połączenia z serwerem, gdy program Visual Studio używa protokołu TLS 1,2.

### <a name="to-fix-this-connection-error"></a>Aby naprawić ten błąd połączenia

Włącz połączenia dla następujących adresów URL:

- https:&#47;&#47;Management.Core.Windows.NET

- https:&#47;&#47;App.vssps.VisualStudio.com

- https:&#47;&#47;login.microsoftonline.com

- https:&#47;&#47;login.Live.com

- https:&#47;&#47;go.Microsoft.com

- https:&#47;&#47;Graph.Windows.NET

- https:&#47;&#47;App.vsspsext.VisualStudio.com

- &#42;. azurewebsites.net (dla połączeń platformy Azure)

- &#42;. visualstudio.microsoft.com

- cdn.vsassets.io (hosty usługi Content Delivery Network lub sieci CDN, zawartość)

- &#42;. gallerycdn.vsassets.io (hostuje rozszerzenia Azure DevOps Services)

- static2.sharepointonline.com (hostuje zasoby używane przez program Visual Studio w zestawie Office UI Fabric Kit, takie jak czcionki)

- &#42;. nuget.org (dla połączeń NuGet)

  > [!NOTE]
  > Adresy URL serwera NuGet należące do użytkownika mogą nie być uwzględnione na tej liście. Możesz sprawdzić, czy serwery NuGet są używane w%APPData%\Nuget\NuGet.Config.

## <a name="error-failed-to-parse-id-from-parent-process"></a>Błąd: "nie można przeanalizować identyfikatora z procesu nadrzędnego"

Ten komunikat o błędzie może pojawić się podczas korzystania z programu inicjującego programu Visual Studio i pliku Response. JSON na dysku sieciowym. Źródłem błędu jest Kontrola konta użytkownika w systemie Windows.

Przyczyny tego błędu mogą być następujące: zamapowany dysk sieciowy lub udział [UNC](/dotnet/standard/io/file-path-formats#unc-paths) jest połączony z tokenem dostępu użytkownika. Po włączeniu funkcji Kontrola konta użytkownika tworzone są dwa [tokeny dostępu](/windows/win32/secauthz/access-tokens) użytkowników: jeden *z* dostępem administratora i jeden *bez* dostępu administratora. Po utworzeniu dysku lub udziału sieciowego jest z nim połączony bieżący token dostępu użytkownika. Ponieważ program inicjujący musi być uruchomiony jako administrator, nie będzie mógł uzyskać dostępu do dysku sieciowego ani udziału, jeśli dysk lub udział nie są połączone z tokenem dostępu użytkownika, który ma dostęp administratora.

### <a name="to-fix-this-error"></a>Aby naprawić ten błąd

Możesz użyć polecenia `net use` lub zmienić ustawienia funkcji Kontrola konta zasady grupy użytkownika. Aby uzyskać więcej informacji o tych obejść i sposobach ich implementacji, zobacz następujące artykuły pomocy technicznej firmy Microsoft:

* [Zamapowane dyski nie są dostępne z poziomu monitu o podniesionych uprawnieniach, jeśli kontrola konta użytkownika jest skonfigurowana pod kątem "Monituj o poświadczenia" w systemie Windows](https://support.microsoft.com/help/3035277/mapped-drives-are-not-available-from-an-elevated-prompt-when-uac-is-co)
* [Programy mogą nie być w stanie uzyskać dostępu do niektórych lokalizacji sieciowych po włączeniu kontroli konta użytkownika w systemach operacyjnych Windows](https://support.microsoft.com/en-us/help/937624/programs-may-be-unable-to-access-some-network-locations-after-you-turn)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Instalowanie i używanie programu Visual Studio za zaporą lub serwerem proxy](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Przewodnik administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Instalowanie programu Visual Studio](install-visual-studio.md)
