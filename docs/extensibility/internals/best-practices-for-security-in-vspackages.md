---
title: Najlepsze rozwiązania dotyczące zabezpieczeń pakietów VSPackage | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 308832522b4badde661d4132410ca8366856d7b9
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56635660"
---
# <a name="best-practices-for-security-in-vspackages"></a>Najlepsze rozwiązania dotyczące zabezpieczeń pakietów VSPackage
Aby zainstalować [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] na komputerze, użytkownik musi być uruchomiona w kontekście przy użyciu poświadczeń administracyjnych. Podstawowa jednostka zabezpieczeń i wdrażania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aplikacja jest [pakietu VSPackage](../../extensibility/internals/vspackages.md). Pakietu VSPackage muszą być zarejestrowane przy użyciu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], które również wymaga poświadczeń administracyjnych.

 Administratorzy mają pełne uprawnienia do zapisu do rejestru i systemu plików, a także wykonywać żadnego kodu. Musi mieć tych uprawnień do tworzenia, wdrażania lub zainstalować pakietu VSPackage.

 Jak najszybciej po jego zainstalowaniu pakietu VSPackage jest w pełni zaufany. Ze względu na wysokim poziomie uprawnień skojarzonych z pakietu VSPackage jest możliwość przypadkowo zainstalowania pakietu VSPackage, który ma złośliwymi działaniami.

 Użytkownikom należy upewnić się, ich instalację pakietów VSPackage tylko z zaufanych źródeł. Firmom tworzenie pakietów VSPackage należy zdecydowanie nazwy i je podpisać, zapewnienie użytkownika, w tym naruszeniu nie będzie mógł. Firmom tworzenie pakietów VSPackage należy sprawdzić ich zależności zewnętrznych, takich jak usługi sieci web i instalacji zdalnej, aby ocenić i rozwiązać wszelkie problemy z zabezpieczeniami.

 Aby uzyskać więcej informacji, zobacz [bezpieczny, wytyczne dotyczące programowania dla platformy .NET Framework](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90)).

## <a name="see-also"></a>Zobacz także
- [Dodatek zabezpieczeń](https://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)
- [DDEX zabezpieczeń](https://msdn.microsoft.com/library/44a52a70-5c98-450e-993d-4a3b32f69ba8)