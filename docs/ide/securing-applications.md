---
title: Zabezpieczenia
description: Poznaj pewne pojęcia dotyczące zabezpieczeń i funkcje zabezpieczeń, które mogą ułatwić efektywne opracowywanie bezpiecznych aplikacji.
ms.custom: SEO-VS-2020
ms.date: 06/01/2018
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio], applications
- application design, securability
ms.assetid: 7d32c4cf-8bec-4307-a2a8-42f0ceddf3eb
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f3dcd034a76fbc371c95a2bbf386687830e3b63d
ms.sourcegitcommit: 63cb90e8cea112aa2ce8741101b309dbc709e393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2021
ms.locfileid: "110687651"
---
# <a name="secure-applications"></a>Zabezpieczanie aplikacji

Należy rozważyć bezpieczeństwo we wszystkich aspektach programowania aplikacji, od projektowania do wdrożenia. Rozpocznij od uruchomienia Visual Studio tak bezpiecznie, jak to możliwe. Zobacz [User permissions (Uprawnienia użytkownika).](../ide/user-permissions-and-visual-studio.md)

Aby efektywnie rozwijać bezpieczne aplikacje, powinieneś rozumieć podstawy pojęć związanych z bezpieczeństwem i funkcji zabezpieczeń platform, dla których tworzysz. Należy również mieć świadomość bezpiecznych technik kodowania.

## <a name="code-for-security"></a>Kod zabezpieczeń

Większość błędów kodowania, które są wynikiem luk w zabezpieczeniach, występuje, ponieważ deweloperzy nie podają nieprawidłowych założeń podczas pracy z użytkownikami lub nie w pełni rozumieją platformę, dla której programują.

- [Wskazówki dotyczące bezpiecznego kodowania](/dotnet/standard/security/secure-coding-guidelines) opisują różne sposoby, w jakie można zaprojektować kod .NET do pracy z systemem zabezpieczeń.
- [Najlepsze rozwiązania w zakresie zabezpieczeń dla języka C++](/cpp/top/security-best-practices-for-cpp) zawierają informacje o narzędziach zabezpieczeń i rozwiązaniach dla deweloperów języka C++.

## <a name="build-for-security"></a>Kompilowanie w celu zabezpieczenia

Bezpieczeństwo jest również ważną kwestią w procesie kompilacji. Kilka dodatkowych kroków może zwiększyć bezpieczeństwo wdrożonej aplikacji i zapobiec nieautoryzowanej inżynierii odwrotnej, fałszersowi lub innym atakom:

- [Program Dotfuscator](dotfuscator/index.md) jest bezpłatny i pomaga chronić zestawy .NET przed odwrotnym i nieautoryzowanym użyciem, takim jak nieautoryzowane debugowanie.
- [Podpisywanie za pomocą silnych](managing-assembly-and-manifest-signing.md) nazw może służyć do unikatowego identyfikowania składników oprogramowania i zapobiegania fałszowania nazw.

## <a name="see-also"></a>Zobacz też

- [Zabezpieczenia w .NET](/dotnet/standard/security/index)
- [Zabezpieczenia platformy Azure](/azure/security/)
- [Windows 10 Mobile zabezpieczeń](/windows/security/threat-protection/windows-10-mobile-security-guide)
- [Apache Cordova zabezpieczeń platformy](/previous-versions/visualstudio/cross-platform/tools-for-cordova/security/best-practices?view=toolsforcordova-2017&preserve-view=true)
- [ASP.NET Podstawowe zabezpieczenia](/aspnet/core/security/?view=aspnetcore-2.1&preserve-view=true)
- [Windows Forms zabezpieczeń](/dotnet/framework/winforms/windows-forms-security)
