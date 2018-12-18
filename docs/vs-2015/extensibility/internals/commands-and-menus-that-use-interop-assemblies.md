---
title: Polecenia i menu, które używają zestawów międzyoperacyjnych | Dokumentacja firmy Microsoft
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
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1a1c7d0e3acde1ca412d7bfaba0cfa3606ee54a4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753687"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Polecenia i menu, w których używane są zestawy międzyoperacyjne
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pakietu VSPackage, który implementuje poleceń menu i paska narzędzi przy użyciu zestawów międzyoperacyjnych musi:  
  
- Poinformuj [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zintegrowanego środowiska programistycznego (IDE) dotyczące poleceń obsługuje i tego, czy są obecnie włączone.  
  
- Zgodne z regułami (Umowa) do obsługi poleceń.  
  
- Jawne Implementowanie obsługi poleceń przy użyciu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfejsu.  
  
  Poniżej opisano sposób wykonywania tych zadań.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Określanie stanu polecenia przy użyciu zestawów międzyoperacyjnych](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 W tym artykule opisano, jak pakietu VSPackage powiadamia IDE dotyczących poleceń, które obsługuje i tego, czy są obecnie włączone.  
  
 [Kontrakty poleceń w zestawach międzyoperacyjnych](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 Zawiera definicję kontraktu podstawowe polecenia używane przez wszystkich pakietów VSPackage wykonania polecenia przy użyciu zestawów międzyoperacyjnych  
  
 [Implementacja](../../extensibility/internals/command-implementation.md)  
 Omówienie Implementowanie polecenia pakietu VSPackage.  
  
 [Rejestrowanie programów obsługi zestawu międzyoperacyjnego](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 W tym artykule opisano wpisy rejestru wymagane do powiadamiania środowiska IDE, że pakietu VSPackage udostępnia procedurę obsługi poleceń.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Dostępność](../../extensibility/internals/command-availability.md)  
 W tym artykule opisano kryteria, które są używane przez środowisko IDE do określenia polecenia pakietu VSPackage, które są dostępne i jak obiekt je obsługuje.  
  
 [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Zawiera szczegółowe informacje o sposobie tworzenia interfejsu użytkownika, który używa [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] polecenia pomocy technicznej.  
  
 [Routing poleceń w pakietach VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)  
 Przegląd procesu umożliwiającego odnoszą się obiektu z żądaniem odpowiednie polecenie.

