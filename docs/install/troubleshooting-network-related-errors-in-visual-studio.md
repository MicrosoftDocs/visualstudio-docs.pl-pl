---
title: Rozwiązywanie problemów z błędami sieci lub serwera proxy
description: Znajdź rozwiązania dla błędów związanych z siecią lub serwerem proxy, które mogą wystąpić podczas instalowania lub używania programu Visual Studio za zaporą lub serwerem proxy.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114987"
---
# <a name="troubleshoot-network-related-errors-when-you-install-or-use-visual-studio"></a>Rozwiązywanie problemów z błędami związanymi z siecią podczas instalowania lub używania programu Visual Studio

Mamy rozwiązania dla najbardziej typowych błędów związanych z siecią lub serwerem proxy, które mogą wystąpić podczas instalowania lub używania programu Visual Studio za zaporą lub serwerem proxy.

## <a name="error-proxy-authorization-required"></a>Błąd: "Wymagana autoryzacja serwera proxy"

Ten błąd zazwyczaj występuje, gdy użytkownicy są połączeni z Internetem za pośrednictwem serwera proxy, a serwer proxy blokuje wywołania, które program Visual Studio wykonuje do niektórych zasobów sieciowych.

### <a name="to-fix-this-proxy-error"></a>Aby naprawić ten błąd serwera proxy

- Uruchom ponownie program Visual Studio. Powinno zostać wyświetlone okno dialogowe uwierzytelniania serwera proxy. Wprowadź poświadczenia po wyświetleniu monitu w oknie dialogowym.

- Jeśli ponowne uruchomienie programu Visual Studio nie rozwiąże problemu, może to oznaczać, że serwer proxy nie monituje o poświadczenia dla adresów http:&#47;&#47;go.microsoft.com, ale robi to dla adresów &#42;.visualStudio.microsoft.com. W przypadku tych serwerów należy rozważyć dodanie następujących adresów URL do listy dozwolonych w celu odblokowania wszystkich scenariuszy logowania w programie Visual Studio:

  - &#42;.windows.net

  - witryna &#42;.microsoftonline.com

  - witryny &#42;.visualstudio.microsoft.com

  - witryna &#42;.microsoft.com

  - &#42;.live.com

- W przeciwnym razie można usunąć adres go.microsoft.com http:&#47;&#47;z listy dozwolonych, tak aby okno dialogowe uwierzytelniania serwera proxy było wyświetlane zarówno dla adresu http:&#47;&#47;go.microsoft.com, jak i dla punktów końcowych serwera po ponownym uruchomieniu programu Visual Studio.

  — Lub —

- Jeśli chcesz używać poświadczeń domyślnych z serwerem proxy, możesz wykonać następujące akcje:

::: moniker range="vs-2017"

  1. Znajdź **devenv.exe.config** (plik konfiguracyjny devenv.exe) w: **%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** or **%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**.

  2. W pliku konfiguracyjnym `<system.net>` znajdź blok, a następnie dodaj ten kod:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      W pliku `proxyaddress="<http://<yourproxy:port#>`.

     > [!NOTE]
     > Aby uzyskać więcej informacji, zobacz [ &lt;domyślny elementproxy&gt; (ustawienia sieciowe)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) i [ &lt;serwer proxy&gt; Element (Ustawienia sieciowe).](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings)

::: moniker-end

::: moniker range="vs-2019"

  1. Znajdź **devenv.exe.config** (plik konfiguracyjny devenv.exe) w: **%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE** or **%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE**.

  2. W pliku konfiguracyjnym `<system.net>` znajdź blok, a następnie dodaj ten kod:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      W pliku `proxyaddress="<http://<yourproxy:port#>`.

     > [!NOTE]
     > Aby uzyskać więcej informacji, zobacz [ &lt;domyślny elementproxy&gt; (ustawienia sieciowe)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) i [ &lt;serwer proxy&gt; Element (Ustawienia sieciowe).](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings)

::: moniker-end

## <a name="error-the-underlying-connection-was-closed"></a>Błąd: "Połączenie podstawowe zostało zamknięte"

Jeśli używasz programu Visual Studio w sieci prywatnej, która ma zaporę, program Visual Studio może nie być w stanie połączyć się z niektórymi zasobami sieciowymi. Te zasoby mogą obejmować usługi Azure DevOps dla usług logowania i licencjonowania, NuGet i usługi platformy Azure. Jeśli program Visual Studio nie może połączyć się z jednym z tych zasobów, może zostać wyświetlony następujący komunikat o błędzie:

  **Połączenie podstawowe zostało zamknięte: wystąpił nieoczekiwany błąd podczas wysyłania**

Program Visual Studio używa protokołu TLS (Transport Layer Security) 1.2 do łączenia się z zasobami sieciowymi. Urządzenia zabezpieczające w niektórych sieciach prywatnych blokują niektóre połączenia z serwerem, gdy program Visual Studio używa protokołu TLS 1.2.

### <a name="to-fix-this-connection-error"></a>Aby naprawić ten błąd połączenia

Włącz połączenia dla następujących adresów URL:

- https:&#47;&#47;management.core.windows.net

- https:&#47;&#47;app.vssps.visualstudio.com

- https:&#47;&#47;login.microsoftonline.com

- https:&#47;&#47;login.live.com

- https:&#47;&#47;go.microsoft.com

- https:&#47;&#47;graph.windows.net

- https:&#47;&#47;app.vsspsext.visualstudio.com

- &#42;.azurewebsites.net (dla połączeń platformy Azure)

- witryny &#42;.visualstudio.microsoft.com

- cdn.vsassets.io (hostuje sieć dostarczania zawartości lub sieć CDN, zawartość)

- &#42;.gallerycdn.vsassets.io (hostuje rozszerzenia usług Azure DevOps)

- static2.sharepointonline.com (hostuje zasoby używane przez program Visual Studio w zestawie Office UI Fabric kit, takie jak czcionki)

- &#42;.nuget.org (dla połączeń NuGet)

  > [!NOTE]
  > Adresy URL serwera NuGet należące do prywatnej firmy Może nie zostać uwzględnione na tej liście. Serwery NuGet, których używasz, można sprawdzić w pliku %APPData%\Nuget\NuGet.Config.

## <a name="error-failed-to-parse-id-from-parent-process"></a>Błąd: "Nie można przeanalizować identyfikatora z procesu nadrzędnego"

Ten komunikat o błędzie może wystąpić podczas korzystania z programu inikuscyjny programu Visual Studio i pliku response.json na dysku sieciowym. Źródłem błędu jest kontrola konta użytkownika (UAC) w systemie Windows.

Oto dlaczego ten błąd może się zdarzyć: zamapowany dysk sieciowy lub udział [UNC](/dotnet/standard/io/file-path-formats#unc-paths) jest połączony z tokenem dostępu użytkownika. Gdy kontrola konta użytkownika jest włączona, two user [access tokens](/windows/win32/secauthz/access-tokens) są tworzone: jeden *z* dostępem administratora i jeden *bez* dostępu administratora. Po utworzeniu dysku sieciowego lub udziału bieżący token dostępu użytkownika jest z nim połączony. Ponieważ program uruchamiany musi być uruchomiony jako administrator, nie będzie mógł uzyskać dostępu do dysku sieciowego ani udostępnić, jeśli dysk lub udział nie jest połączony z tokenem dostępu użytkownika, który ma dostęp administratora.

### <a name="to-fix-this-error"></a>Aby naprawić ten błąd

Można użyć `net use` polecenia lub zmienić ustawienie zasady grupy UAC. Aby uzyskać więcej informacji na temat tych obejść i sposobu ich zaimplementowania, zobacz następujące artykuły pomocy technicznej firmy Microsoft:

* [Zamapowane dyski nie są dostępne z monitu z podwyższonym poziomem uprawnień, gdy funkcja Kontrola konta użytkownika jest skonfigurowana jako "Monitowanie o poświadczenia" w systemie Windows](https://support.microsoft.com/help/3035277/mapped-drives-are-not-available-from-an-elevated-prompt-when-uac-is-co)
* [Programy mogą nie mieć dostępu do niektórych lokalizacji sieciowych po włączeniu kontroli konta użytkownika w systemach operacyjnych Windows](https://support.microsoft.com/en-us/help/937624/programs-may-be-unable-to-access-some-network-locations-after-you-turn)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalowanie i używanie programu Visual Studio za zaporą lub serwerem proxy](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Przewodnik dla administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Instalacja programu Visual Studio](install-visual-studio.md)
