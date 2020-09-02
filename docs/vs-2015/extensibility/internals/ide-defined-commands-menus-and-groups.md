---
title: Polecenia, menu i grupy zdefiniowane w środowisku IDE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 32e8135328c11fd74311371d07645a525426371e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192730"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Polecenia, menu i grupy definiowane w środowisku IDE
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wiele menu, poleceń i grup poleceń jest już zdefiniowanych do użycia przez [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE. Te polecenia są również dostępne do użycia podczas jego rozszerania [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="finding-environment-defined-commands"></a>Znajdowanie poleceń zdefiniowanych w środowisku  
 Polecenia środowiska są zdefiniowane w zbiorze czterech plików vsct:  
  
- SharedCmdDef. vsct  
  
- SharedCmdPlace. vsct  
  
- ShellCmdDef. vsct  
  
- ShellCmdPlace. vsct  
  
  Te pliki znajdują się w *\<Visual Studio SDK installation path>* \VisualStudioIntegration\Common\Inc \\ . Pliki te zawierają definicje i identyfikatory GUID menu i grup, których można użyć w pliku konfiguracji tabeli poleceń (. vsct) pakietu VSPackage jako kontenery dla własnych menu, grup i poleceń.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Identyfikatory GUID i identyfikatory menu programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 Zawiera wartości identyfikatora GUID i identyfikatora menu na pasku menu programu Visual Studio i zawartych w nich grup.  
  
 [Identyfikatory GUID i identyfikatory pasków narzędzi programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 Zawiera identyfikatory GUID i identyfikator pasków narzędzi w środowisku IDE programu Visual Studio oraz zawartych w nich grup.  
  
 [Identyfikatory GUID i identyfikatory poleceń programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 Zawiera identyfikatory GUID i identyfikator poleceń zdefiniowanych przez środowisko IDE programu Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (. Vsct) — pliki](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Polecenia zdefiniowane w środowisku IDE służące do rozszerzania systemów projektów](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
