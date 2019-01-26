---
title: Zabezpieczenia
ms.date: 06/01/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio], applications
- application design, securability
ms.assetid: 7d32c4cf-8bec-4307-a2a8-42f0ceddf3eb
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f3acc9f198467694f17918e44ca0d8fff45b5f38
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55033391"
---
# <a name="secure-applications"></a>Zabezpieczanie aplikacji

Należy rozważyć bezpieczeństwo we wszystkich aspektach programowania aplikacji, od projektowania do wdrożenia. Rozpocznij od uruchamianie programu Visual Studio w bezpieczny sposób. Zobacz [uprawnienia użytkownika](../ide/user-permissions-and-visual-studio.md).

Aby efektywnie rozwijać bezpieczne aplikacje, powinieneś rozumieć podstawy pojęć związanych z bezpieczeństwem i funkcji zabezpieczeń platform, dla których tworzysz. Należy również mieć świadomość bezpiecznych technik kodowania.

## <a name="code-for-security"></a>Kod zabezpieczeń

Większość błędów kodowania, które powodują powstanie luk w zabezpieczeniach występują, ponieważ deweloperzy tworzą nieprawidłowe wartości domyślne podczas pracy z danymi wejściowymi użytkownika lub nie w pełni rozumieją platformę, dla której tworzą.

- [Bezpieczne, wytyczne dotyczące kodowania](/dotnet/standard/security/secure-coding-guidelines) w tym artykule opisano różne sposoby kodu platformy .NET może być przeznaczona do pracy z systemu zabezpieczeń.
- [Najlepsze rozwiązania dotyczące C++](/cpp/top/security-best-practices-for-cpp) zawiera informacje dotyczące narzędzi zabezpieczeń i praktyki dla deweloperów C++.

## <a name="build-for-security"></a>Tworzenie dla zabezpieczeń

Zabezpieczenia są również ważną kwestią w procesie kompilacji. Kilka dodatkowych kroków, można zwiększyć bezpieczeństwo wdrożonej aplikacji i zapobiec nieautoryzowanemu odtwarzania, fałszowanie lub innymi atakami:

- [System Dotfuscator](dotfuscator/index.md) jest dostępny bezpłatnie i pomaga chronić zestawów platformy .NET z odtwarzania i nieautoryzowanego użycia, takich jak nieautoryzowanego debugowania.
- [Podpisywania silnymi](managing-assembly-and-manifest-signing.md) może służyć do unikatowego identyfikowania składników oprogramowania i zapobiec fałszowanie nazwy.

## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia w programie .NET Framework](/dotnet/standard/security/index)
- [Zabezpieczenia platformy Azure](/azure/security/)
- [Przewodnik po zabezpieczeniach systemu Windows 10 Mobile](/windows/security/threat-protection/windows-10-mobile-security-guide)
- [Funkcje zabezpieczeń platformy Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/security/best-practices?view=toolsforcordova-2017)
- [Zabezpieczenia programu ASP.NET Core](/aspnet/core/security/?view=aspnetcore-2.1)
- [Zabezpieczenia formularzy Windows](/dotnet/framework/winforms/windows-forms-security)