---
title: Najlepsze rozwiązania dotyczące zabezpieczeń pakietów VSPackage | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1db578f62e6fe42ba3d74df5870ca727bd884aaf
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54772186"
---
# <a name="best-practices-for-security-in-vspackages"></a>Najlepsze rozwiązania dotyczące zabezpieczeń pakietów VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aby zainstalować [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] na komputerze, użytkownik musi być uruchomiona w kontekście przy użyciu poświadczeń administracyjnych. Podstawowa jednostka zabezpieczeń i wdrażania [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] aplikacja jest [pakietów VSPackage](../../extensibility/internals/vspackages.md). Pakietu VSPackage muszą być zarejestrowane przy użyciu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], które również wymaga poświadczeń administracyjnych.  
  
 Administratorzy mają pełne uprawnienia do zapisu do rejestru i systemu plików, a także wykonywać żadnego kodu. Musi mieć tych uprawnień do tworzenia, wdrażania lub zainstalować pakietu VSPackage.  
  
 Jak najszybciej po jego zainstalowaniu pakietu VSPackage jest w pełni zaufany. Ze względu na wysokim poziomie uprawnień skojarzonych z pakietu VSPackage jest możliwość przypadkowo zainstalowania pakietu VSPackage, który ma złośliwymi działaniami.  
  
 Użytkownikom należy upewnić się, ich instalację pakietów VSPackage tylko z zaufanych źródeł. Firmom tworzenie pakietów VSPackage należy zdecydowanie nazwy i je podpisać, zapewnienie użytkownika, w tym naruszeniu nie będzie mógł. Firmom tworzenie pakietów VSPackage należy sprawdzić ich zależności zewnętrznych, takich jak usługi sieci web i instalacji zdalnej, aby ocenić i rozwiązać wszelkie problemy z zabezpieczeniami.  
  
 Aby uzyskać więcej informacji, zobacz Secure wytycznych kodowania dla platformy .NET Framework ([http://msdn.microsoft.com/library/d55zzx87.aspx](http://msdn.microsoft.com/library/d55zzx87.aspx)).  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia dodatku](http://msdn.microsoft.com/library/44a5c651-6246-4310-b371-65378917c799)   
 [DDEX zabezpieczeń](http://msdn.microsoft.com/44a52a70-5c98-450e-993d-4a3b32f69ba8)
