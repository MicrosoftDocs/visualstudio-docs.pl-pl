---
title: Obsługa programu Visual Studio dla zatwierdzonego przez FIPS 140-2 trybu pracy
ms.date: 04/14/2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06d147397a168bb78a31a8fbe6929d6c2184d080
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81386450"
---
# <a name="visual-studio-support-for-the-fips-140-2-approved-mode-of-operation"></a>Obsługa programu Visual Studio dla zatwierdzonego przez FIPS 140-2 trybu pracy

Począwszy od [wersji 16.4,](/visualstudio/releases/2019/release-notes-v16.4/)program Visual Studio 2019 obsługuje zatwierdzony przez publikację 140-2 zatwierdzoną przez publikację federalną (FIPS) w trybie działania dla systemów Windows, Azure i .NET. A w [wersji 16.5](/visualstudio/releases/2019/release-notes-v16.5/)program Visual Studio obsługuje teraz zatwierdzony przez FIPS 140-2 tryb działania podczas opracowywania [aplikacji C++, które są przeznaczone dla zdalnego systemu Linux.](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)

Aby skonfigurować zatwierdzony przez program FIPS 140-2 tryb działania dla programu Visual Studio, [zainstaluj program .NET Framework 4.8,](https://dotnet.microsoft.com/download/dotnet-framework/net48) a następnie włącz ustawienie Zasad grupy, **Kryptografia systemu: Użyj algorytmów zgodnych ze standardem FIPS do szyfrowania, mieszania i podpisywania**.

Aby uzyskać więcej informacji na temat zatwierdzonego przez FIPS 140-2 trybu pracy i sposobu jego [włączania, zobacz FIPS 140-2 Validation](/windows/security/threat-protection/fips-140-validation/).

> [!NOTE]
> Narzędzia używane do tworzenia aplikacji dla platform innych firm, takich jak iOS lub Android, mogą nie używać algorytmów zgodnych ze standardem FIPS. Oprogramowanie innych firm dołączone do programu Visual Studio lub instalowane rozszerzenia również może nie używać algorytmów zgodnych ze standardem FIPS. Ponadto program rozwoju rozwiązań [programu SharePoint](/sharepoint/security-for-sharepoint-server/federal-information-processing-standard-security-standards/) nie obsługuje zatwierdzonego przez FIPS 140-2 trybu pracy.

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej o zatwierdzonym trybie działania fips 140-2 dla programu Visual Studio oraz innych produktów i usług firmy Microsoft, zobacz następujące łącza:

- [Visual Studio: Konfigurowanie bezpiecznego zdalnego rozwoju systemu Linux zgodnego ze standardem FIPS za pomocą języka C++](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)
- [Windows: kryptografia systemu i używanie algorytmów zgodnych ze standardem FIPS do szyfrowania, mieszania i podpisywania](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
- [.NET Core: Zgodność z FIPS](/dotnet/standard/security/fips-compliance/)

## <a name="see-also"></a>Zobacz też

[Zabezpieczanie aplikacji](securing-applications.md)