---
title: Zabezpieczenia
ms.date: 06/01/2018
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio], applications
- application design, securability
ms.assetid: 7d32c4cf-8bec-4307-a2a8-42f0ceddf3eb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87f06746901baaaf14f91032f8968a0d99fc20c2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595452"
---
# <a name="secure-applications"></a>Zabezpieczanie aplikacji

Należy rozważyć bezpieczeństwo we wszystkich aspektach programowania aplikacji, od projektowania do wdrożenia. Zacznij od uruchomienia programu Visual Studio tak bezpiecznie, jak to możliwe. Zobacz [Uprawnienia użytkownika](../ide/user-permissions-and-visual-studio.md).

Aby efektywnie rozwijać bezpieczne aplikacje, powinieneś rozumieć podstawy pojęć związanych z bezpieczeństwem i funkcji zabezpieczeń platform, dla których tworzysz. Należy również mieć świadomość bezpiecznych technik kodowania.

## <a name="code-for-security"></a>Kod zabezpieczeń

Większość błędów kodowania, które powodują luki w zabezpieczeniach występują, ponieważ deweloperzy popełniają nieprawidłowe założenia podczas pracy z danych wejściowych użytkownika lub ponieważ nie w pełni zrozumieć platformę, dla której są one opracowywania.

- [Wskazówki dotyczące bezpiecznego kodowania](/dotnet/standard/security/secure-coding-guidelines) opisują różne sposoby, w jakie kod .NET może być zaprojektowany do pracy z systemem zabezpieczeń.
- [Najważniejsze wskazówki dotyczące zabezpieczeń dla języka C++](/cpp/top/security-best-practices-for-cpp) zawierają informacje o narzędziach zabezpieczeń i rozwiązaniach dla deweloperów języka C++.

## <a name="build-for-security"></a>Kompilacja dla bezpieczeństwa

Bezpieczeństwo jest również ważnym czynnikiem w procesie kompilacji. Kilka dodatkowych kroków może poprawić bezpieczeństwo wdrożonej aplikacji i zapobiec nieautoryzowanemu inżynierii odwrotnej, fałszowaniu lub innym atakom:

- [Dotfuscator](dotfuscator/index.md) jest wolny i pomaga chronić zestawy .NET przed inżynierii odwrotnej i nieautoryzowanego użycia, takich jak nieautoryzowane debugowanie.
- [Podpisywanie silnej nazwy](managing-assembly-and-manifest-signing.md) może służyć do jednoznacznej identyfikacji składników oprogramowania i zapobiegania fałszowaniu nazw.

## <a name="see-also"></a>Zobacz też

- [Zabezpieczenia w .NET](/dotnet/standard/security/index)
- [Zabezpieczenia platformy Azure](/azure/security/)
- [Przewodnik po zabezpieczeniach systemu Windows 10 Mobile](/windows/security/threat-protection/windows-10-mobile-security-guide)
- [Funkcje zabezpieczeń platformy Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/security/best-practices?view=toolsforcordova-2017)
- [ASP.NET Podstawowe zabezpieczenia](/aspnet/core/security/?view=aspnetcore-2.1)
- [Zabezpieczenia formularzy systemu Windows](/dotnet/framework/winforms/windows-forms-security)
