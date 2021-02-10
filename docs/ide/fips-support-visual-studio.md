---
title: Obsługa standardu FIPS w programie Visual Studio
titleSuffix: ''
description: Dowiedz się, w jaki sposób program Visual Studio obsługuje publikacje w standardowej zgodności z przetwarzaniem danych federalnym 140-2 zatwierdzony tryb operacji dla systemu Windows, platformy Azure i platformy .NET.
ms.custom: SEO-VS-2020
ms.date: 04/14/2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3d6cb0d2bbcb1ec1d13f5916a7c2b1cd97824fb5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945542"
---
# <a name="visual-studio-support-for-the-fips-140-2-approved-mode-of-operation"></a>Obsługa programu Visual Studio dla zatwierdzonego trybu działania FIPS 140-2

Począwszy od [wersji 16,4](/visualstudio/releases/2019/release-notes-v16.4/), Visual Studio 2019 obsługuje publikacje Federal Information Processing Standard (FIPS) 140-2 zatwierdzone trybu operacji dla systemu Windows, platformy Azure i platformy .NET. I w [wersji 16,5](/visualstudio/releases/2019/release-notes-archive-v16.5)program Visual Studio obsługuje teraz tryb zatwierdzania FIPS 140-2 w przypadku tworzenia [aplikacji w języku C++ przeznaczonych dla zdalnego systemu Linux](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/).

Aby skonfigurować tryb systemu operacyjnego FIPS 140-2 dla programu Visual Studio, [zainstaluj .NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48) , a następnie włącz ustawienie zasady grupy, **Kryptografia systemu: Użyj zgodnych algorytmów FIPS do szyfrowania, mieszania i podpisywania**.

Aby uzyskać więcej informacji na temat zatwierdzonego trybu działania FIPS 140-2 i sposobu jego włączania, zobacz [Walidacja fips 140-2](/windows/security/threat-protection/fips-140-validation/).

> [!NOTE]
> Narzędzia używane do tworzenia aplikacji dla platform innych niż Microsoft, takich jak iOS lub Android, mogą nie używać algorytmów zgodnych ze standardem FIPS. Oprogramowanie innej firmy dołączone do programu Visual Studio lub rozszerzenia, które można zainstalować, również może nie używać algorytmów zgodnych ze standardem FIPS. Ponadto programowanie rozwiązań [programu SharePoint](/sharepoint/security-for-sharepoint-server/federal-information-processing-standard-security-standards/) nie obsługuje zatwierdzonego trybu działania FIPS 140-2.

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej o zatwierdzonym trybie obsługi trybu FIPS 140-2 dla programu Visual Studio i innych produktów i usług firmy Microsoft, zobacz następujące linki:

- [Visual Studio: Konfigurowanie bezpiecznego zdalnego tworzenia systemu Linux zgodnego ze standardem FIPS przy użyciu języka C++](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)
- [System Windows: Kryptografia systemu i użycie algorytmów zgodnych ze standardem FIPS do szyfrowania, mieszania i podpisywania](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
- [.NET Core: zgodność ze standardem FIPS](/dotnet/standard/security/fips-compliance/)

## <a name="see-also"></a>Zobacz też

[Zabezpieczanie aplikacji](securing-applications.md)