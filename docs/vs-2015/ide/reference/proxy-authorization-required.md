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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74297817"
---
# <a name="proxy-authorization-required"></a>Wymagana autoryzacja serwera proxy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Niezbędny Błąd autoryzacji serwera proxy** występuje, gdy użytkownicy są połączeni z zasobami usługi Visual Studio Online za pomocą serwera proxy, a serwer proxy blokuje wywołania.

Aby naprawić ten błąd, spróbuj wykonać co najmniej jedną z następujących czynności:

- Uruchom ponownie program Visual Studio. Powinno zostać wyświetlone okno dialogowe uwierzytelnianie serwera proxy. Wprowadź swoje poświadczenia w oknie dialogowym.

- Jeśli powyższy krok nie rozwiąże problemu, może to być spowodowane faktem, że serwer proxy nie wyświetla monitu o podanie poświadczeń dla https://go.microsoft.com adresów, ale tak dla adresów *. visualStudio.com. W przypadku tych serwerów należy dodać następujące adresy URL do listy dozwolonych, aby odblokować wszystkie scenariusze logowania w programie Visual Studio:

  - *.windows.net

  - *.microsoftonline.com

  - *.visualstudio.com

  - *.microsoft.com

  - *.live.com

- Można usunąć https://go.microsoft.com adres z listy dozwolonych, tak aby okno dialogowe uwierzytelniania serwera proxy było wyświetlane zarówno dla https://go.microsoft.com adresu, jak i punktów końcowych serwera po ponownym uruchomieniu programu Visual Studio.

- Jeśli chcesz użyć domyślnych poświadczeń z serwerem proxy, wykonaj następujące czynności:

   1. Znajdź devenv.exe.config (plik konfiguracji devenv.exe) w: **%ProgramFiles%\Microsoft Visual Studio 14.0 \ Common7\IDE** (lub **% ProgramFiles (x86)% \ Microsoft Visual Studio 14.0 \ Common7\IDE**).

   2. W pliku konfiguracji Znajdź `<system.net>` blok i Dodaj następujący kod:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Wstaw poprawny adres serwera proxy dla sieci w programie `proxyaddress="<http://<yourproxy:port#>` .

- Postępuj zgodnie z instrukcjami w [tym wpisie w blogu](https://blogs.msdn.microsoft.com/rido/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy/) , aby dodać kod, który umożliwia korzystanie z serwera proxy.
