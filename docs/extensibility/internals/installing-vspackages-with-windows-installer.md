---
title: Instalowanie pakietów VSPackages z Instalatorem Windows | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2eb90dbffa9f04cd17afa70d2bdfc59205bc99cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707459"
---
# <a name="installing-vspackages-with-windows-installer"></a>Instalowanie pakietów VSPackage przy użyciu Instalatora Windows
Integracja vsPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] z wymaga czegoś więcej niż tylko kopiowania plików na komputer użytkownika. Instalator vspackage musi zainstalować VSPackage i jego zależne pliki, i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]zarejestrować i zintegrować je w . Program VSPackage może korzystać z funkcji integracji, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] takich jak wyświetlanie ikony na ekranie powitanym i okno dialogowe Informacje.

 Pliki Instalatora Windows firmy Microsoft są zalecanym sposobem dystrybucji pakietów VSPackages. Łatwe w użyciu pakiety Instalatora Windows mogą być uruchamiane w dowolnym systemie operacyjnym Windows obsługiwanym przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]program . Aby uzyskać więcej informacji, zobacz [Instalator Windows](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).

## <a name="in-this-section"></a>W tej sekcji
- [Podstawowe informacje dotyczące Instalatora Windows](../../extensibility/internals/windows-installer-basics.md)

 Zawiera omówienie Instalatora Windows.

- [Scenariusze instalacji pakietu VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)

 W tym artykule omówiono różne sposoby obsługi instalacji obok [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]siebie zarówno vspackages i .

- [Tworzenie pakietu Instalatora Windows](../../extensibility/internals/authoring-a-windows-installer-package.md)

 Zawiera omówienie typowych kroków instalatorów, aby poprawnie zainstalować [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]i zintegrować pakiety VSPackages z programem .

- [Wykrywanie wymagań systemowych](../../extensibility/internals/detecting-system-requirements.md)

 W tym artykule [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] opisano, jak instalator może wykryć i jego składniki i anulować konfigurację, jeśli wymagania VSPackage nie są spełnione.

- [Zarządzanie składnikami](../../extensibility/internals/component-management.md)

 W tym artykule omówiono sposób tworzenia instalatora, który zachowa integralność poprzednich wersji produktu.

- [Wybieranie katalogu instalacyjnego dla pakietu VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)

 Podsumowuje opcje lokalizowania pakietów VSPackages.

- [Rejestracja pakietu VSPackage](../../extensibility/internals/vspackage-registration.md)

 W tym artykule omówiono, jak VSPackages są rejestrowane w czasie instalacji i dlaczego samorejestracji jest złym pomysłem.

- [Wdrażanie typów projektów](../../extensibility/internals/deploying-project-types.md)

 W tym artykule omówiono sposób używania nowego agregatora typu projektu dla typów projektów kodu zarządzanego.

- [Instrukcje: generowanie informacji rejestru dla instalatora](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)

 W tym artykule wyjaśniono, jak używać programu RegPkg.exe do generowania manifestu rejestracji dla zarządzanego programu VSPackage.

- [Polecenia, które należy uruchomić po instalacji](../../extensibility/internals/commands-that-must-be-run-after-installation.md)

 W tym artykule wyjaśniono, jak uruchamiać [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]polecenia po instalacji, aby zintegrować pakiety VSPackages z programem .

- [Odinstalowywanie pakietów VSPackage przy użyciu Instalatora Windows](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)

 W tym artykule opisano kroki, które instalator musi wykonać, gdy użytkownicy odinstalowują pakiet VSPackage.
