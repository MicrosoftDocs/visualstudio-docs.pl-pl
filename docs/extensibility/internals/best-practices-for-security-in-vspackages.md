---
title: Najlepsze rozwiązania dotyczące zabezpieczeń w programie pakietów VSPackage | Microsoft Docs
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
ms.openlocfilehash: e73be2af3d24a6a719f353fbd0ab25dbdf86fe09
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012142"
---
# <a name="best-practices-for-security-in-vspackages"></a>Najlepsze rozwiązania dotyczące zabezpieczeń w programie pakietów VSPackage
Aby zainstalować [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] program na komputerze, musisz być uruchomiony w kontekście z poświadczeniami administracyjnymi. Podstawową jednostką zabezpieczeń i wdrażania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aplikacji jest [pakietu VSPackage](../../extensibility/internals/vspackages.md). Pakietu VSPackage musi być zarejestrowany przy użyciu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , co wymaga również poświadczeń administracyjnych.

 Administratorzy mają pełne uprawnienia do zapisu w rejestrze i systemie plików oraz do uruchamiania dowolnego kodu. Musisz mieć te uprawnienia, aby opracowywać, wdrażać lub instalować pakietu VSPackage.

 Gdy tylko zostanie zainstalowana, pakietu VSPackage jest w pełni zaufany. Ze względu na ten wysoki poziom uprawnień skojarzonych z pakietu VSPackage można przypadkowo zainstalować pakietu VSPackage, który ma złośliwe intencje.

 Użytkownicy powinni upewnić się, że instalują pakietów VSPackage tylko z zaufanych źródeł. Firmy, które opracowują pakietów VSPackage, powinny silnie nawiązać nazwę i podpisać je, aby zapewnić użytkownikowi możliwość naruszenia ochrony. Firmy, które opracowują pakietów VSPackage, powinny sprawdzić ich zależności zewnętrzne, takie jak usługi sieci Web i instalacja zdalna, aby ocenić i rozwiązać wszelkie problemy z zabezpieczeniami.

 Aby uzyskać więcej informacji, zobacz [zasady bezpiecznego kodowania dla .NET Framework](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90)).

## <a name="see-also"></a>Zobacz także
- [Zabezpieczenia dodatku](/previous-versions/1326zbk3(v=vs.140))
- [Zabezpieczenia DDEX](/previous-versions/bb163703(v=vs.140))