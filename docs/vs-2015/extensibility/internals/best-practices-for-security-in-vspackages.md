---
title: Najlepsze rozwiązania dotyczące zabezpieczeń w programie pakietów VSPackage | Microsoft Docs
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
ms.openlocfilehash: 940644cd3950c38c6383371c1844b54b328acd0c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697266"
---
# <a name="best-practices-for-security-in-vspackages"></a>Najlepsze rozwiązania dotyczące zabezpieczeń pakietów VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aby zainstalować [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] program na komputerze, musisz być uruchomiony w kontekście z poświadczeniami administracyjnymi. Podstawową jednostką zabezpieczeń i wdrażania [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] aplikacji jest [pakietów VSPackage](../../extensibility/internals/vspackages.md). Pakietu VSPackage musi być zarejestrowany przy użyciu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , co wymaga również poświadczeń administracyjnych.  
  
 Administratorzy mają pełne uprawnienia do zapisu w rejestrze i systemie plików oraz do uruchamiania dowolnego kodu. Musisz mieć te uprawnienia, aby opracowywać, wdrażać lub instalować pakietu VSPackage.  
  
 Gdy tylko zostanie zainstalowana, pakietu VSPackage jest w pełni zaufany. Ze względu na ten wysoki poziom uprawnień skojarzonych z pakietu VSPackage można przypadkowo zainstalować pakietu VSPackage, który ma złośliwe intencje.  
  
 Użytkownicy powinni upewnić się, że instalują pakietów VSPackage tylko z zaufanych źródeł. Firmy, które opracowują pakietów VSPackage, powinny silnie nawiązać nazwę i podpisać je, aby zapewnić użytkownikowi możliwość naruszenia ochrony. Firmy, które opracowują pakietów VSPackage, powinny sprawdzić ich zależności zewnętrzne, takie jak usługi sieci Web i instalacja zdalna, aby ocenić i rozwiązać wszelkie problemy z zabezpieczeniami.  
  
 Aby uzyskać więcej informacji, zobacz zasady bezpiecznego kodowania dla .NET Framework ( [https://msdn.microsoft.com/library/d55zzx87.aspx](https://msdn.microsoft.com/library/d55zzx87.aspx) ).  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia dodatku](https://msdn.microsoft.com/library/44a5c651-6246-4310-b371-65378917c799)   
 [Zabezpieczenia DDEX](https://msdn.microsoft.com/44a52a70-5c98-450e-993d-4a3b32f69ba8)
