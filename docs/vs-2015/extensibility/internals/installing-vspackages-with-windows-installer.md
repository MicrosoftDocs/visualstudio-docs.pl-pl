---
title: Instalowanie pakietów VSPackage przy użyciu Instalatora Windows | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
caps.latest.revision: 31
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8d5b22479996bca6ee69c1334d79f012024b865d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54782677"
---
# <a name="installing-vspackages-with-windows-installer"></a>Instalowanie pakietów VSPackage przy użyciu Instalatora Windows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Integrowanie usługi pakietu VSPackage do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] wymaga więcej niż tylko kopiowanie plików na komputerze użytkownika. Instalator usługi pakietu VSPackage, należy zainstalować pakietu VSPackage i jego plików zależnych i zarejestrować i zintegrować je do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Usługi pakietu VSPackage korzystać z zalet integracji funkcji, takich jak wyświetlanie ikony na [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] powitalny ekranu i wkrótce — okno dialogowe.  
  
 Pliki Instalatora systemu Microsoft Windows są zalecanym sposobem dystrybucji z pakietami VSPackage. Łatwe w użyciu, pakietów Instalatora Windows można uruchamiać w dowolnym systemie operacyjnym Windows, obsługiwane przez [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Aby uzyskać więcej informacji, zobacz [Instalatora Windows](http://msdn.microsoft.com/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Podstawowe informacje dotyczące Instalatora Windows](../../extensibility/internals/windows-installer-basics.md)  
 Zawiera omówienie Instalatora Windows.  
  
 [Scenariusze instalacji pakietu VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)  
 W tym artykule omówiono różne sposoby, może obsługiwać instalacje side-by-side zarówno z pakietami VSPackage i [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Tworzenie pakietu Instalatora Windows](../../extensibility/internals/authoring-a-windows-installer-package.md)  
 Omówiono typowe etapy instalatory należy wykonać, aby poprawnie zainstalować i integrowanie pakietów VSPackage do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Wykrywanie wymagań systemowych](../../extensibility/internals/detecting-system-requirements.md)  
 W tym artykule opisano, jak może wykryć Instalatora [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , a jej komponentach i Anuluj instalację, jeśli nie są spełnione wymagania pakietu VSPackage.  
  
 [Zarządzanie składnikami](../../extensibility/internals/component-management.md)  
 Opisano sposób tworzenia Instalator, który będzie utrzymywać integralność poprzednich wersji produktu.  
  
 [Wybieranie katalogu instalacyjnego dla pakietu VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)  
 Zawiera podsumowanie opcji do lokalizowania pakietów VSPackage.  
  
 [Rejestracja pakietu VSPackage](../../extensibility/internals/vspackage-registration.md)  
 W tym artykule omówiono, jak pakietów VSPackage są rejestrowane w czasie instalacji i dlaczego Autorejestracja to zły pomysł.  
  
 [Wdrażanie typów projektów](../../extensibility/internals/deploying-project-types.md)  
 W tym artykule omówiono sposób używania nowego agregatora typów projektów dla typów projektów kodu zarządzanego.  
  
 [Instrukcje: Generowanie informacji rejestru dla Instalatora](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 Opis sposobu użycia RegPkg.exe do generowania manifestu rejestracji dla zarządzanych pakietu VSPackage.  
  
 [Polecenia, które należy uruchomić po instalacji](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 Wyjaśnia sposób uruchamiania poleceń po instalacji, aby zintegrować pakietów VSPackage do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Odinstalowywanie pakietów VSPackage przy użyciu Instalatora Windows](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 W tym artykule opisano kroki, które swój Instalatora, należy wykonać, jeśli użytkownicy odinstalują Twojego pakietu VSPackage.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Instalowanie pakietów VSPackage](../../misc/installing-vspackages.md)  
 W tym artykule omówiono sposób tworzenia i instalowania pakietów VSPackage i sposób obsługi użytkowników korzystających z wieloma wersjami programu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] w tym samym czasie.
