---
title: Instalowanie pakietów VSPackage przy użyciu Instalatora Windows | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
caps.latest.revision: 31
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5a43f48c337751c989af37c49a361ae011aa4e16
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733906"
---
# <a name="installing-vspackages-with-windows-installer"></a>Instalowanie pakietów VSPackage przy użyciu Instalatora Windows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Integrowanie usługi pakietu VSPackage do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] wymaga więcej niż tylko kopiowanie plików na komputerze użytkownika. Instalator usługi pakietu VSPackage, należy zainstalować pakietu VSPackage i jego plików zależnych i zarejestrować i zintegrować je do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Usługi pakietu VSPackage korzystać z zalet integracji funkcji, takich jak wyświetlanie ikony na [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] powitalny ekranu i wkrótce — okno dialogowe.  
  
 Pliki Instalatora systemu Microsoft Windows są zalecanym sposobem dystrybucji z pakietami VSPackage. Łatwe w użyciu, pakietów Instalatora Windows można uruchamiać w dowolnym systemie operacyjnym Windows, obsługiwane przez [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Aby uzyskać więcej informacji, zobacz [Instalatora Windows](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
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
  
 [Instrukcje: generowanie informacji rejestru dla instalatora](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 Opis sposobu użycia RegPkg.exe do generowania manifestu rejestracji dla zarządzanych pakietu VSPackage.  
  
 [Polecenia, które należy uruchomić po instalacji](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 Wyjaśnia sposób uruchamiania poleceń po instalacji, aby zintegrować pakietów VSPackage do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Odinstalowywanie pakietów VSPackage przy użyciu Instalatora Windows](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 W tym artykule opisano kroki, które swój Instalatora, należy wykonać, jeśli użytkownicy odinstalują Twojego pakietu VSPackage.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Instalowanie pakietów VSPackage](../../misc/installing-vspackages.md)  
 W tym artykule omówiono sposób tworzenia i instalowania pakietów VSPackage i sposób obsługi użytkowników korzystających z wieloma wersjami programu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] w tym samym czasie.

