---
title: Najważniejsze wskazówki dotyczące zabezpieczeń w pakietach VSPackage | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4309feeed3233d2149586afb1bf4efafacb21ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709907"
---
# <a name="best-practices-for-security-in-vspackages"></a>Najważniejsze wskazówki dotyczące zabezpieczeń w programie VSPackages
Aby zainstalować [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] na komputerze, należy uruchomić w kontekście z poświadczeniami administracyjnymi. Podstawową jednostką zabezpieczeń i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wdrażania aplikacji jest [VSPackage](../../extensibility/internals/vspackages.md). VsPackage musi być zarejestrowany [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]przy użyciu , który wymaga również poświadczeń administracyjnych.

 Administratorzy mają pełne uprawnienia do zapisywania w rejestrze i systemie plików oraz do uruchamiania dowolnego kodu. Musisz mieć te uprawnienia do tworzenia, wdrażania lub instalowania vsPackage.

 Jak tylko zostanie zainstalowany, VSPackage jest w pełni zaufany. Ze względu na ten wysoki poziom uprawnień skojarzonych z VSPackage, jest możliwe, aby przypadkowo zainstalować VSPackage, który ma złośliwe intencje.

 Użytkownicy powinni upewnić się, że instalują pakiety VSPackage tylko z zaufanych źródeł. Firmy opracowujące pakiety VSPackage powinny zdecydowanie nazwać je i podpisać, aby zapewnić użytkownika, że nie można zapobiec manipulowaniu. Firmy opracowujące pakiety VSPackage powinny zbadać ich zależności zewnętrzne, takie jak usługi sieci web i instalacja zdalna, aby ocenić i rozwiązać wszelkie problemy z zabezpieczeniami.

 Aby uzyskać więcej informacji, zobacz [wskazówki dotyczące bezpiecznego kodowania programu .NET Framework](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90)).

## <a name="see-also"></a>Zobacz też
- [Zabezpieczenia dodatków](https://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)
- [Zabezpieczenia DDEX](https://msdn.microsoft.com/library/44a52a70-5c98-450e-993d-4a3b32f69ba8)
