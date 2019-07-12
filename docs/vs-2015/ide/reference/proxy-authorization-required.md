---
title: Wymaga autoryzacji serwera proxy | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f2de40c520bca0ea04f50ec782fec2dda531172e
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67822068"
---
# <a name="proxy-authorization-required"></a>Wymagana autoryzacja serwera proxy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Wymaga autoryzacji serwera Proxy** błąd występuje zazwyczaj, gdy użytkownicy są połączeni zasoby online programu Visual Studio za pośrednictwem serwera proxy i serwer proxy blokuje wywołania.

Aby rozwiązać ten problem, spróbuj wykonać co najmniej jeden z następujących czynności:

- Uruchom ponownie program Visual Studio. Powinna zostać wyświetlona okno dialogowe uwierzytelniania serwera proxy. Wprowadź swoje poświadczenia w oknie dialogowym.

- Jeśli powyższy krok nie rozwiąże problemu, może to być spowodowane serwera proxy nie jest wyświetlany monit o poświadczenia dla http://go.microsoft.com adresy, ale jest to spowodowane *. adresów visualStudio.com. Na tych serwerach należy dodać następujące adresy URL do listy dozwolonych, aby odblokować wszystkie w scenariuszach logowania w programie Visual Studio:

  - *.windows.net

  - *.microsoftonline.com

  - *.visualstudio.com

  - *.microsoft.com

  - *.live.com

- Możesz usunąć http://go.microsoft.com adresów z listy dozwolonych, aby w oknie dialogowym uwierzytelniania serwera proxy, pojawia się dla obu http://go.microsoft.com adres i punkty końcowe serwera, po ponownym uruchomieniu programu Visual Studio.

- Poświadczenia domyślne za pomocą serwera proxy, wykonaj następujące czynności:

   1. Znajdź devenv.exe.config (plik devenv.exe w konfiguracji): **%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE** (lub **% ProgramFiles (x86) %\Microsoft Visual Studio 14.0\Common7\IDE**) .

   2. Plik konfiguracyjny zawiera `<system.net>` zablokować, a następnie dodaj następujący kod:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Wstaw adres prawidłowy serwer proxy dla Twojej sieci w `proxyaddress="<http://<yourproxy:port#>`.

- Postępuj zgodnie z instrukcjami w [ten wpis w blogu](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx) można dodać kod, który pozwala na używanie serwera proxy.
