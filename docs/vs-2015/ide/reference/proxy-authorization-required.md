---
title: Wymagana autoryzacja serwera proxy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 848817691d7fae32f2240e3d6cac4451c4ce58c4
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297817"
---
# <a name="proxy-authorization-required"></a>Wymagana autoryzacja serwera proxy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Niezbędny Błąd autoryzacji serwera proxy** występuje, gdy użytkownicy są połączeni z zasobami usługi Visual Studio Online za pomocą serwera proxy, a serwer proxy blokuje wywołania.

Aby naprawić ten błąd, spróbuj wykonać co najmniej jedną z następujących czynności:

- Uruchom ponownie program Visual Studio. Powinna zostać wyświetlona okno dialogowe uwierzytelniania serwera proxy. Wprowadź swoje poświadczenia w oknie dialogowym.

- Jeśli powyższy krok nie rozwiąże problemu, może to być spowodowane faktem, że serwer proxy nie monituje o podanie poświadczeń dla adresów https://go.microsoft.com, ale dla adresów *. visualStudio.com. W przypadku tych serwerów należy dodać następujące adresy URL do listy dozwolonych, aby odblokować wszystkie scenariusze logowania w programie Visual Studio:

  - *.windows.net

  - *.microsoftonline.com

  - *.visualstudio.com

  - *.microsoft.com

  - *.live.com

- Adres https://go.microsoft.com można usunąć z listy dozwolonych, tak aby w oknie dialogowym uwierzytelniania serwera proxy pojawia się zarówno adres https://go.microsoft.com, jak i punkty końcowe serwera po ponownym uruchomieniu programu Visual Studio.

- Jeśli chcesz użyć domyślnych poświadczeń z serwerem proxy, wykonaj następujące czynności:

   1. Znajdź devenv. exe. config (plik konfiguracyjny devenv. exe) w: **%ProgramFiles%\Microsoft Visual Studio 14.0 \ Common7\IDE** (lub **% ProgramFiles (x86)% \ Microsoft Visual Studio 14.0 \ Common7\IDE**).

   2. W pliku konfiguracji Znajdź blok `<system.net>` i Dodaj następujący kod:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Wstaw poprawny adres serwera proxy dla sieci w `proxyaddress="<http://<yourproxy:port#>`.

- Postępuj zgodnie z instrukcjami w [tym wpisie w blogu](https://blogs.msdn.microsoft.com/rido/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy/) , aby dodać kod, który umożliwia korzystanie z serwera proxy.
