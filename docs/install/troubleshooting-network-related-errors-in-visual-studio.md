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
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 0abe51b9f01d0c1f380c4762a7d0d4f457964aa7
ms.sourcegitcommit: bccc6503542e1517e0e96a9f02f5a89d69c60c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2020
ms.locfileid: "91135134"
---
# <a name="troubleshoot-network-related-errors-when-you-install-or-use-visual-studio"></a>Rozwiązywanie problemów związanych z siecią podczas instalowania programu Visual Studio lub korzystania z niego

Mamy rozwiązania typowych błędów związanych z siecią lub serwerem proxy, które mogą wystąpić podczas instalowania programu Visual Studio lub korzystania z niego za zaporą lub serwerem proxy.

## <a name="error-proxy-authorization-required"></a>Błąd: "wymagane autoryzacja serwera proxy"

Ten błąd występuje zazwyczaj, gdy użytkownicy są połączeni z Internetem za pomocą serwera proxy, a serwer proxy blokuje wywołania, które program Visual Studio wprowadza do niektórych zasobów sieciowych.

### <a name="to-fix-this-proxy-error"></a>Aby naprawić ten błąd serwera proxy

- Uruchom ponownie program Visual Studio. Powinno zostać wyświetlone okno dialogowe uwierzytelnianie serwera proxy. Wprowadź swoje poświadczenia po wyświetleniu monitu w oknie dialogowym.

- Jeśli ponowne uruchomienie programu Visual Studio nie rozwiąże problemu, może to oznaczać, że serwer proxy nie wyświetli monitu o podanie poświadczeń dla protokołu http: &#47;&#47;adresy go.microsoft.com, ale robi to w przypadku adresów &#42;. visualStudio.microsoft.com. W przypadku tych serwerów rozważ dodanie następujących adresów URL do listy dozwolonych, aby odblokować wszystkie scenariusze logowania w programie Visual Studio:

  - &#42;. windows.net

  - &#42;. microsoftonline.com

  - &#42;. visualstudio.microsoft.com

  - &#42;. microsoft.com

  - &#42;. live.com

- Można w przeciwnym razie usunąć adres http: &#47;&#47;go.microsoft.com z listy dozwolonych, tak aby w oknie dialogowym uwierzytelniania serwera proxy pojawia się zarówno adres http: &#47;&#47;go.microsoft.com, jak i punkty końcowe serwera po ponownym uruchomieniu programu Visual Studio.

  — Lub —

- Jeśli chcesz użyć domyślnych poświadczeń z serwerem proxy, możesz wykonać następujące czynności:

::: moniker range="vs-2017"

  1. Znajdź **devenv.exe.config** (plik konfiguracji devenv.exe) w: **%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** lub **% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE**.

  2. W pliku konfiguracji Znajdź `<system.net>` blok, a następnie Dodaj następujący kod:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Należy wstawić prawidłowy adres serwera proxy dla sieci w programie `proxyaddress="<http://<yourproxy:port#>` .

     > [!NOTE]
     > Aby uzyskać więcej informacji, zobacz strony [ &lt; defaultProxy &gt; (Ustawienia sieci)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) i [ &lt; &gt; element proxy (Ustawienia sieci)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings) .

::: moniker-end

::: moniker range="vs-2019"

  1. Znajdź **devenv.exe.config** (plik konfiguracji devenv.exe) w: **%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE** lub **% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Enterprise\Common7\IDE**.

  2. W pliku konfiguracji Znajdź `<system.net>` blok, a następnie Dodaj następujący kod:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Należy wstawić prawidłowy adres serwera proxy dla sieci w programie `proxyaddress="<http://<yourproxy:port#>` .

     > [!NOTE]
     > Aby uzyskać więcej informacji, zobacz strony [ &lt; defaultProxy &gt; (Ustawienia sieci)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) i [ &lt; &gt; element proxy (Ustawienia sieci)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings) .

::: moniker-end

## <a name="error-disconnected-from-visual-studio-when-attempting-to-report-a-problem"></a>Błąd: "odłączono od programu Visual Studio" podczas próby zgłoszenia problemu

Ten błąd występuje zazwyczaj, gdy użytkownik jest połączony z Internetem za pomocą serwera proxy, a serwer proxy blokuje wywołania, które program Visual Studio wprowadza do niektórych zasobów sieciowych.

### <a name="to-fix-this-proxy-error"></a>Aby naprawić ten błąd serwera proxy

1. Znajdź **feedback.exe.config** (plik konfiguracyjny feedback.exe) w folderze **% ProgramFiles (x86)% \ Microsoft Visual Studio\Installer** lub **%ProgramFiles%\Microsoft Visual Studio\Installer**.

2. W pliku konfiguracji Sprawdź, czy znajduje się w nim następujący kod; Jeśli kod nie istnieje, należy go dodać przed ostatnim `</configuration>` wierszem.

   ```xml
   <system.net>
       <defaultProxy useDefaultCredentials="true" />
   </system.net>
   ```

## <a name="error-the-underlying-connection-was-closed"></a>Błąd: "Połączenie podstawowe zostało zamknięte"

Jeśli używasz programu Visual Studio w sieci prywatnej, która ma zaporę, program Visual Studio może nie być w stanie połączyć się z niektórymi zasobami sieciowymi. Te zasoby mogą obejmować Azure DevOps Services logowania i licencjonowania, NuGet i usług platformy Azure. Jeśli program Visual Studio nie może nawiązać połączenia z jednym z tych zasobów, może zostać wyświetlony następujący komunikat o błędzie:

  **Połączenie podstawowe zostało zamknięte: Wystąpił nieoczekiwany błąd podczas wysyłania**

Program Visual Studio używa protokołu Transport Layer Security (TLS) 1,2 do nawiązywania połączenia z zasobami sieciowymi. Urządzenia zabezpieczeń w niektórych sieciach prywatnych blokują niektóre połączenia z serwerem, gdy program Visual Studio używa protokołu TLS 1,2.

### <a name="to-fix-this-connection-error"></a>Aby naprawić ten błąd połączenia

Włącz połączenia dla następujących adresów URL:

- https: &#47;&#47;management.core.windows.net

- https: &#47;&#47;app.vssps.visualstudio.com

- https: &#47;&#47;login.microsoftonline.com

- https: &#47;&#47;login.live.com

- https: &#47;&#47;go.microsoft.com

- https: &#47;&#47;graph.windows.net

- https: &#47;&#47;app.vsspsext.visualstudio.com

- &#42;. azurewebsites.net (dla połączeń platformy Azure)

- &#42;. visualstudio.microsoft.com

- cdn.vsassets.io (hosty usługi Content Delivery Network lub sieci CDN, zawartość)

- &#42;. gallerycdn.vsassets.io (hostuje rozszerzenia Azure DevOps Services)

- static2.sharepointonline.com (hostuje zasoby używane przez program Visual Studio w zestawie Office UI Fabric Kit, takie jak czcionki)

- &#42;. nuget.org (dla połączeń NuGet)

  > [!NOTE]
  > Adresy URL serwera NuGet należące do użytkownika mogą nie być uwzględnione na tej liście. Możesz sprawdzić, czy serwery NuGet są używane w% APPData% \Nuget\NuGet.Config.

## <a name="error-failed-to-parse-id-from-parent-process"></a>Błąd: "nie można przeanalizować identyfikatora z procesu nadrzędnego"

Ten komunikat o błędzie może pojawić się podczas korzystania z programu inicjującego programu Visual Studio i response.jsw pliku na dysku sieciowym. Źródłem błędu jest Kontrola konta użytkownika w systemie Windows.

Przyczyny tego błędu mogą być następujące: zamapowany dysk sieciowy lub udział [UNC](/dotnet/standard/io/file-path-formats#unc-paths) jest połączony z tokenem dostępu użytkownika. Po włączeniu funkcji Kontrola konta użytkownika tworzone są dwa [tokeny dostępu](/windows/win32/secauthz/access-tokens) użytkowników: jeden *z* dostępem administratora i jeden *bez* dostępu administratora. Po utworzeniu dysku sieciowego lub udziału jest z nim połączony bieżący token dostępu użytkownika. Ponieważ program inicjujący musi być uruchomiony jako administrator, nie będzie mógł uzyskać dostępu do dysku sieciowego ani udziału, jeśli dysk lub udział nie są połączone z tokenem dostępu użytkownika, który ma dostęp administratora.

### <a name="to-fix-this-error"></a>Aby naprawić ten błąd

Możesz użyć `net use` polecenia lub zmienić ustawienie zasady grupy kontroli konta użytkownika. Aby uzyskać więcej informacji o tych obejść i sposobach ich implementacji, zobacz następujące artykuły pomocy technicznej firmy Microsoft:

* [Zamapowane dyski nie są dostępne z poziomu monitu o podniesionych uprawnieniach, jeśli kontrola konta użytkownika jest skonfigurowana pod kątem "Monituj o poświadczenia" w systemie Windows](https://support.microsoft.com/help/3035277/mapped-drives-are-not-available-from-an-elevated-prompt-when-uac-is-co)
* [Programy mogą nie być w stanie uzyskać dostępu do niektórych lokalizacji sieciowych po włączeniu kontroli konta użytkownika w systemach operacyjnych Windows](https://support.microsoft.com/en-us/help/937624/programs-may-be-unable-to-access-some-network-locations-after-you-turn)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Instalowanie i używanie programu Visual Studio za zaporą lub serwerem proxy](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Instalowanie programu Visual Studio](install-visual-studio.md)
