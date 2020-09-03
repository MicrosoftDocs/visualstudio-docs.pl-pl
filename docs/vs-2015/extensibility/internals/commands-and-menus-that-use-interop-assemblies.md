---
title: Polecenia i menu używające zestawów międzyoperacyjnych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ad6b324953914df7103d0dec7371199e3cbbd937
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195049"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Polecenia i menu, w których używane są zestawy międzyoperacyjne
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pakietu VSPackage implementujący polecenia menu i paska narzędzi przy użyciu zestawów międzyoperacyjnych musi:  
  
- Informowanie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zintegrowanego środowiska programistycznego (IDE) o obsługiwanych przez niego poleceniach oraz o tym, czy są one obecnie włączone.  
  
- Przestrzegaj reguł (kontraktu) na potrzeby obsługi poleceń.  
  
- Jawnie Implementuj obsługę poleceń za pomocą <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfejsu lub.  
  
  Poniżej opisano, jak wykonać te zadania.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Określanie stanu polecenia przy użyciu zestawów międzyoperacyjnych](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 Opisuje, w jaki sposób pakietu VSPackage powiadamia IDE o tym, które polecenia obsługuje i czy są one obecnie włączone.  
  
 [Kontrakty poleceń w zestawach międzyoperacyjnych](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 Zawiera definicję podstawowego kontraktu polecenia używanego przez wszystkie pakietów VSPackage implementujące polecenia przy użyciu zestawów międzyoperacyjnych  
  
 [Implementacja](../../extensibility/internals/command-implementation.md)  
 Zawiera omówienie sposobu, w jaki pakietu VSPackage implementuje polecenie.  
  
 [Rejestrowanie programów obsługi zestawu międzyoperacyjnego](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 Opisuje wpisy rejestru wymagane do powiadomienia środowiska IDE, że pakietu VSPackage udostępnia procedurę obsługi poleceń.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Dostępność](../../extensibility/internals/command-availability.md)  
 Opisuje kryteria, które są używane przez IDE w celu określenia, które polecenia pakietu VSPackage są dostępne i jakie obiekty je obsługuje.  
  
 [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Zawiera szczegółowe informacje o sposobie tworzenia interfejsu użytkownika korzystającego z [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] obsługi poleceń.  
  
 [Routing poleceń w pakietach VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)  
 Przegląd procesu służącego do powiązania obiektu z prawidłowym żądaniem polecenia.
