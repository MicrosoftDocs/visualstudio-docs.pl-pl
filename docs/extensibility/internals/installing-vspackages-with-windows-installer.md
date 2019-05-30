---
title: Instalowanie pakietów VSPackage przy użyciu Instalatora Windows | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94dcb85e3cfef9c44cb8e88720f53c296f8bf997
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349855"
---
# <a name="installing-vspackages-with-windows-installer"></a>Instalowanie pakietów VSPackage przy użyciu Instalatora Windows
Integrowanie usługi pakietu VSPackage do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wymaga więcej niż tylko kopiowanie plików na komputerze użytkownika. Instalator usługi pakietu VSPackage, należy zainstalować pakietu VSPackage i jego plików zależnych i zarejestrować i zintegrować je do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Usługi pakietu VSPackage korzystać z zalet integracji funkcji, takich jak wyświetlanie ikony na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] powitalny ekranu i wkrótce — okno dialogowe.

 Pliki Instalatora systemu Microsoft Windows są zalecanym sposobem dystrybucji z pakietami VSPackage. Łatwe w użyciu, pakietów Instalatora Windows można uruchamiać w dowolnym systemie operacyjnym Windows, obsługiwane przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Aby uzyskać więcej informacji, zobacz [Instalatora Windows](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).

## <a name="in-this-section"></a>W tej sekcji
- [Podstawowe informacje dotyczące Instalatora Windows](../../extensibility/internals/windows-installer-basics.md)

 Zawiera omówienie Instalatora Windows.

- [Scenariusze instalacji pakietu VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)

 W tym artykule omówiono różne sposoby, może obsługiwać instalacje side-by-side zarówno z pakietami VSPackage i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- [Tworzenie pakietu Instalatora Windows](../../extensibility/internals/authoring-a-windows-installer-package.md)

 Omówiono typowe etapy instalatory należy wykonać, aby poprawnie zainstalować i integrowanie pakietów VSPackage do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- [Wykrywanie wymagań systemowych](../../extensibility/internals/detecting-system-requirements.md)

 W tym artykule opisano, jak może wykryć Instalatora [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , a jej komponentach i Anuluj instalację, jeśli nie są spełnione wymagania pakietu VSPackage.

- [Zarządzanie składnikami](../../extensibility/internals/component-management.md)

 Opisano sposób tworzenia Instalator, który będzie utrzymywać integralność poprzednich wersji produktu.

- [Wybieranie katalogu instalacyjnego dla pakietu VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)

 Zawiera podsumowanie opcji do lokalizowania pakietów VSPackage.

- [Rejestracja pakietu VSPackage](../../extensibility/internals/vspackage-registration.md)

 W tym artykule omówiono, jak pakietów VSPackage są rejestrowane w czasie instalacji i dlaczego Autorejestracja to zły pomysł.

- [Wdrażanie typów projektów](../../extensibility/internals/deploying-project-types.md)

 W tym artykule omówiono sposób używania nowego agregatora typów projektów dla typów projektów kodu zarządzanego.

- [Instrukcje: generowanie informacji rejestru dla instalatora](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)

 Opis sposobu użycia RegPkg.exe do generowania manifestu rejestracji dla zarządzanych pakietu VSPackage.

- [Polecenia, które należy uruchomić po instalacji](../../extensibility/internals/commands-that-must-be-run-after-installation.md)

 Wyjaśnia sposób uruchamiania poleceń po instalacji, aby zintegrować pakietów VSPackage do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- [Odinstalowywanie pakietów VSPackage przy użyciu Instalatora Windows](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)

 W tym artykule opisano kroki, które swój Instalatora, należy wykonać, jeśli użytkownicy odinstalują Twojego pakietu VSPackage.