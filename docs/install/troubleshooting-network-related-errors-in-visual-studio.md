---
title: Rozwiązywanie problemów z siecią lub serwerem proxy
description: Znajdź rozwiązania błędów związanych z siecią lub serwerem proxy, które mogą wystąpić podczas instalowania lub używania Visual Studio za zaporą lub serwerem proxy.
ms.date: 10/29/2019
ms.topic: troubleshooting
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs, Visual Studio
- proxy errors, Visual Studio
ms.assetid: ''
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 5e7d54b4e7777b3569031e96760699e7c075245f
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306829"
---
# <a name="troubleshoot-network-related-errors-when-you-install-or-use-visual-studio"></a>Rozwiązywanie problemów z błędami związanymi z siecią podczas instalowania lub używania Visual Studio

Mamy rozwiązania typowych błędów związanych z siecią lub serwerem proxy, które mogą wystąpić podczas instalowania lub używania serwera Visual Studio za zaporą lub serwerem proxy.

## <a name="error-proxy-authorization-required"></a>Błąd: "Wymagana autoryzacja serwera proxy"

Ten błąd zazwyczaj występuje, gdy użytkownicy są połączeni z Internetem za pośrednictwem serwera proxy, a serwer proxy blokuje wywołania, które Visual Studio do niektórych zasobów sieciowych.

### <a name="to-fix-this-proxy-error"></a>Aby naprawić ten błąd serwera proxy

- Uruchom ponownie program Visual Studio. Powinno zostać wyświetlone okno dialogowe uwierzytelniania serwera proxy. Po wyświetleniu monitu w oknie dialogowym wprowadź swoje poświadczenia.

- Jeśli ponowne Visual Studio nie rozwiąże problemu, może to oznaczać, że serwer proxy nie monituje o poświadczenia dla adresów http:&#47;&#47;go.microsoft.com, ale robi to dla adresów &#42;.visualStudio.microsoft.com. W przypadku tych serwerów rozważ dodanie następujących adresów URL do listy zezwalania, aby odblokować wszystkie scenariusze logowania w Visual Studio:

  - &#42;.windows.net

  - &#42;.microsoftonline.com

  - &#42;.visualstudio.microsoft.com

  - &#42;.microsoft.com

  - &#42;.live.com

- W przeciwnym razie możesz usunąć adres http:&#47;&#47;go.microsoft.com z listy zezwalań, aby okno dialogowe uwierzytelniania serwera proxy było wyświetlane zarówno dla adresu http:&#47;&#47;go.microsoft.com, jak i punktów końcowych serwera po ponownym uruchomieniu Visual Studio serwera.

  — Lub —

- Jeśli chcesz używać poświadczeń domyślnych z serwerem proxy, możesz wykonać następujące czynności:

::: moniker range="vs-2017"

  1. Znajdź **devenv.exe.config** (plik konfiguracji devenv.exe) w folderze: **%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** lub **%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE.**

  2. W pliku konfiguracji znajdź `<system.net>` blok, a następnie dodaj ten kod:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Należy wstawić prawidłowy adres serwera proxy dla sieci w `proxyaddress="<http://<yourproxy:port#>` .

     > [!NOTE]
     > Aby uzyskać więcej informacji, zobacz [ &lt; strony defaultProxy &gt; , element (ustawienia sieci)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) i [ &lt; element serwera proxy &gt; (ustawienia sieci).](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings)

::: moniker-end

::: moniker range=">=vs-2019"

  1. Znajdź **devenv.exe.config** (plik konfiguracji programu devenv.exe) w folderze: **%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE** lub **%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE.**

  2. W pliku konfiguracji znajdź `<system.net>` blok, a następnie dodaj ten kod:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Należy wstawić prawidłowy adres serwera proxy dla sieci w `proxyaddress="<http://<yourproxy:port#>` .

     > [!NOTE]
     > Aby uzyskać więcej informacji, zobacz [ &lt; strony defaultProxy &gt; , element (ustawienia sieci)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) i [ &lt; element serwera proxy &gt; (ustawienia sieci).](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings)

::: moniker-end

## <a name="error-disconnected-from-visual-studio-when-attempting-to-report-a-problem"></a>Błąd: "Odłączony od Visual Studio" podczas próby zgłoszenia problemu

Ten błąd zazwyczaj występuje, gdy użytkownik jest połączony z Internetem za pośrednictwem serwera proxy, a serwer proxy blokuje wywołania, które Visual Studio do niektórych zasobów sieciowych.

### <a name="to-fix-this-proxy-error"></a>Aby naprawić ten błąd serwera proxy

1. Znajdź **feedback.exe.config** (plik konfiguracji feedback.exe) w folderze: **%ProgramFiles(x86)%\Microsoft Visual Studio\Installer** lub **%ProgramFiles%\Microsoft Visual Studio\Installer.**

2. W pliku konfiguracji sprawdź, czy jest obecny następujący kod: Jeśli kod nie jest obecny, dodaj go przed ostatnim `</configuration>` wierszem.

   ```xml
   <system.net>
       <defaultProxy useDefaultCredentials="true" />
   </system.net>
   ```

## <a name="error-the-underlying-connection-was-closed"></a>Błąd: "Połączenie bazowe zostało zamknięte"

Jeśli używasz usługi Visual Studio sieci prywatnej, która ma zaporę, Visual Studio może nie być w stanie nawiązać połączenia z niektórymi zasobami sieci. Te zasoby mogą obejmować Azure DevOps Services logowania i licencjonowania, nuGet i usług platformy Azure. Jeśli Visual Studio nawiązać połączenia z jednym z tych zasobów, może zostać wyświetlony następujący komunikat o błędzie:

  **Połączenie bazowe zostało zamknięte: Wystąpił nieoczekiwany błąd podczas wysyłania**

Visual Studio używa Transport Layer Security (TLS) 1.2 do łączenia się z zasobami sieci. Urządzenia zabezpieczające w niektórych sieciach prywatnych blokują niektóre połączenia serwera, Visual Studio używa TLS 1.2.

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

- &#42;.visualstudio.microsoft.com

- cdn.vsassets.io (hostuje sieć dostarczania zawartości lub sieć CDN, zawartość)

- &#42;.gallerycdn.vsassets.io (hosty Azure DevOps Services rozszerzenia)

- static2.sharepointonline.com (hostuje zasoby używane Visual Studio w zestawie Office UI Fabric, takie jak czcionki)

- &#42;.nuget.org (dla połączeń NuGet)

  > [!NOTE]
  > Prywatne adresy URL serwerów NuGet mogą nie zostać uwzględnione na tej liście. Możesz sprawdzić serwery NuGet, których używasz w %APPData%\Nuget\NuGet.Config.

## <a name="error-failed-to-parse-id-from-parent-process"></a>Błąd: "Nie można analizowania identyfikatora z procesu nadrzędnego"

Ten komunikat o błędzie może wystąpić podczas używania programu inicjjącego Visual Studio i response.jspliku na dysku sieciowym. Źródłem błędu jest kontrola konta użytkownika (UAC) w systemie Windows.

Oto dlaczego ten błąd może wystąpić: Zamapowany dysk sieciowy lub udział [UNC](/dotnet/standard/io/file-path-formats#unc-paths) jest połączony z tokenem dostępu użytkownika. Po włączeniu funkcji kontroli konta użytkownika tworzone są dwa [tokeny](/windows/win32/secauthz/access-tokens) dostępu użytkownika: jeden z dostępem *administratora* i jeden *bez* dostępu administratora. Po utworzeniu dysku sieciowego lub udziału bieżący token dostępu użytkownika jest połączony z nim. Ponieważ program inicjujący musi być uruchomiony jako administrator, nie będzie mógł uzyskać dostępu do dysku sieciowego ani udziału, jeśli dysk lub udział nie jest połączony z tokenem dostępu użytkownika, który ma dostęp administratora.

### <a name="to-fix-this-error"></a>Aby naprawić ten błąd

Możesz użyć polecenia lub zmienić ustawienie zasady grupy `net use` UAC. Aby uzyskać więcej informacji na temat tych obejść i sposobu ich wdrażania, zobacz następujące artykuły pomocy technicznej firmy Microsoft:

* [Zamapowane dyski nie są dostępne w wierszu z podwyższonym poziomem uprawnień, gdy funkcja UAC jest skonfigurowana na "Monituj o poświadczenia" w systemie Windows](https://support.microsoft.com/help/3035277/mapped-drives-are-not-available-from-an-elevated-prompt-when-uac-is-co)
* [Programy mogą nie mieć dostępu do niektórych lokalizacji sieciowych po włączeniu kontroli konta użytkownika w systemach operacyjnych Windows](https://support.microsoft.com/en-us/help/937624/programs-may-be-unable-to-access-some-network-locations-after-you-turn)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalowanie i używanie programu Visual Studio za zaporą lub serwerem proxy](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Instalowanie programu Visual Studio](install-visual-studio.md)
