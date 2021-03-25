---
title: Polecenia i menu używające zestawów międzyoperacyjnych | Microsoft Docs
description: Informacje o zadaniach, które należy wykonać podczas implementowania poleceń menu i pasków narzędzi w pakietu VSPackage za pomocą zestawów międzyoperacyjnych.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b5a487c2fe6f97e338924a0b8c682f9dd9798571
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057237"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Polecenia i menu używające zestawów międzyoperacyjnych
Pakietu VSPackage implementujący polecenia menu i paska narzędzi przy użyciu zestawów międzyoperacyjnych musi:

- Informowanie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowanego środowiska programistycznego (IDE) o obsługiwanych przez niego poleceniach oraz o tym, czy są one obecnie włączone.

- Przestrzegaj reguł (kontraktu) na potrzeby obsługi poleceń.

- Jawnie Implementuj obsługę poleceń za pomocą <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfejsu lub.

  W poniższej sekcji opisano, jak wykonać te zadania.

## <a name="in-this-section"></a>W tej sekcji
- [Określanie stanu polecenia przy użyciu zestawów międzyoperacyjnych](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)

 Opisuje, w jaki sposób pakietu VSPackage powiadamia IDE o tym, które polecenia obsługuje i czy są one obecnie włączone.

- [Kontrakty poleceń w zestawach międzyoperacyjnych](../../extensibility/internals/command-contracts-in-interop-assemblies.md)

 Zawiera definicję podstawowego kontraktu polecenia używanego przez wszystkie pakietów VSPackage implementację poleceń przy użyciu zestawów międzyoperacyjnych.

- [Implementacja polecenia](../../extensibility/internals/command-implementation.md)

 Zawiera omówienie sposobu, w jaki pakietu VSPackage implementuje polecenie.

- [Zarejestruj procedury obsługi poleceń zestawu międzyoperacyjnego](../../extensibility/internals/registering-interop-assembly-command-handlers.md)

 Opisuje wpisy rejestru wymagane do powiadomienia środowiska IDE, że pakietu VSPackage udostępnia procedurę obsługi poleceń.

## <a name="related-sections"></a>Sekcje pokrewne
- [Dostępność polecenia](../../extensibility/internals/command-availability.md)

 Opisuje kryteria, które są używane przez IDE w celu określenia, które polecenia pakietu VSPackage są dostępne i jakie obiekty je obsługuje.

- [Jak pakietów VSPackage Dodawanie elementów interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Zawiera szczegółowe informacje o sposobie tworzenia interfejsu użytkownika korzystającego z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obsługi poleceń.

- [Routing poleceń w pakietów VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)

 Przegląd procesu służącego do powiązania obiektu z prawidłowym żądaniem polecenia.
