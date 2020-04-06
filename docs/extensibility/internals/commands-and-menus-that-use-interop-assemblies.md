---
title: Polecenia i menu, które używają zestawów interop | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6c381abe9b4c6ea2a58342e185d7427fa56a180
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709488"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Polecenia i menu korzystające z zestawów Interop
VsPackage, który implementuje polecenia menu i paska narzędzi przy użyciu zestawów Interop musi:

- Poinformuj [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE) o poleceniach, które obsługuje i czy są one obecnie włączone.

- Przestrzegaj zasad (umowy) dotyczących obsługi poleceń.

- Jawnie implementuj obsługę poleceń przy użyciu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfejsu.

  W poniższej sekcji opisano sposób wykonywania tych zadań.

## <a name="in-this-section"></a>W tej sekcji
- [Określanie stanu polecenia przy użyciu zestawów Interop](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)

 W tym artykule opisano, jak VSPackage powiadamia IDE o tym, które polecenia obsługuje i czy są one obecnie włączone.

- [Kontrakty dowodzenia w zespołach Interop](../../extensibility/internals/command-contracts-in-interop-assemblies.md)

 Zawiera definicję podstawowego kontraktu polecenia używanego przez wszystkie polecenia VSPackages implementujące polecenia przy użyciu zestawów Interop.

- [Implementacja polecenia](../../extensibility/internals/command-implementation.md)

 Zawiera omówienie sposobu, w jaki vspackage implementuje polecenie.

- [Rejestrowanie programów obsługi poleceń zestawu Interop](../../extensibility/internals/registering-interop-assembly-command-handlers.md)

 W tym artykule opisano wpisy rejestru wymagane do powiadomienia IDE, że VSPackage udostępnia program obsługi poleceń.

## <a name="related-sections"></a>Powiązane sekcje
- [Dostępność poleceń](../../extensibility/internals/command-availability.md)

 W tym artykule opisano kryteria, które są używane przez IDE do określenia, które polecenia VSPackage są dostępne i jaki obiekt je obsługuje.

- [Jak vspackages dodać elementy interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Zawiera szczegółowe informacje na temat tworzenia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika, który używa obsługi poleceń.

- [Routing poleceń w pakietach VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)

 Omówienie procesu używanego do powiązania obiektu z prawidłowym żądaniem polecenia.
