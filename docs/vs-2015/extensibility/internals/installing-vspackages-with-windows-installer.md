---
title: Instalowanie pakietów VSPackage z Instalator Windows | Microsoft Docs
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
ms.openlocfilehash: 35942f6babf18967e11f268ef0412acb4cc8edf7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687465"
---
# <a name="installing-vspackages-with-windows-installer"></a>Instalowanie pakietów VSPackage przy użyciu Instalatora Windows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Integrowanie pakietu VSPackage w programie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] wymaga więcej niż tylko kopiowanie plików na komputer użytkownika. Instalator programu pakietu VSPackage musi zainstalować pakietu VSPackage i jego pliki zależne oraz zarejestrować i zintegrować je z usługą [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Pakietu VSPackage może korzystać z funkcji integracji, takich jak wyświetlanie ikony na [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ekranie powitalnym i okna dialogowego Informacje.  
  
 Pliki Instalator Windows firmy Microsoft to zalecany sposób dystrybucji pakietów VSPackage. Łatwe w użyciu pakiety Instalator Windows można uruchamiać w dowolnym systemie operacyjnym Windows obsługiwanym przez program [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Aby uzyskać więcej informacji, zobacz [Instalator Windows](https://msdn.microsoft.com/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Podstawowe informacje dotyczące Instalatora Windows](../../extensibility/internals/windows-installer-basics.md)  
 Zawiera przegląd Instalator Windows.  
  
 [Scenariusze instalacji pakietu VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)  
 W tym artykule omówiono różne sposoby obsługi równoległych instalacji programów pakietów VSPackage i [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Tworzenie pakietu Instalatora Windows](../../extensibility/internals/authoring-a-windows-installer-package.md)  
 Zawiera omówienie typowych instalatorów kroków, które należy wykonać, aby poprawnie zainstalować i zintegrować pakietów VSPackage z usługą [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Wykrywanie wymagań systemowych](../../extensibility/internals/detecting-system-requirements.md)  
 Opisuje, w jaki sposób Instalator może wykryć [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] i jego składniki oraz anulować instalację, jeśli nie są spełnione wymagania pakietu VSPackage.  
  
 [Zarządzanie składnikami](../../extensibility/internals/component-management.md)  
 W tym artykule omówiono sposób tworzenia Instalatora, który będzie zachować integralność poprzednich wersji produktu.  
  
 [Wybieranie katalogu instalacyjnego dla pakietu VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)  
 Podsumowuje opcje lokalizowania pakietów VSPackage.  
  
 [Rejestracja pakietu VSPackage](../../extensibility/internals/vspackage-registration.md)  
 W tym artykule omówiono sposób rejestrowania pakietów VSPackage w czasie instalacji i przyczyny nieprawidłowej rejestracji.  
  
 [Wdrażanie typów projektów](../../extensibility/internals/deploying-project-types.md)  
 W tym artykule omówiono sposób użycia nowego agregatora typu projektu dla typów projektów kodu zarządzanego.  
  
 [Instrukcje: generowanie informacji rejestru dla instalatora](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 Wyjaśnia, jak używać RegPkg.exe do generowania manifestu rejestracji dla zarządzanego pakietu VSPackage.  
  
 [Polecenia, które należy uruchomić po instalacji](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 Wyjaśnia, jak uruchomić polecenia po instalacji, aby zintegrować pakietów VSPackage z programem [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Odinstalowywanie pakietów VSPackage przy użyciu Instalatora Windows](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 Opisuje czynności, które Instalator musi wykonać, gdy użytkownicy odinstalowałą pakietu VSPackage.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Instalowanie pakietów VSPackage](../../misc/installing-vspackages.md)  
 W tym artykule omówiono sposób kompilowania i instalowania pakietów VSPackage oraz obsługi użytkowników z wieloma wersjami programu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] w tym samym czasie.
