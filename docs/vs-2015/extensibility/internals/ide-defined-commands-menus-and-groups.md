---
title: Polecenia definiowane w IDE, menu i grupy | Dokumentacja firmy Microsoft
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
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 20fc9e69224f45a5e50462d38b4b2001e3122b49
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776762"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Polecenia, menu i grupy definiowane w środowisku IDE
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wiele menu, poleceń i polecenia grupy są już zdefiniowane na potrzeby używania przez [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE. Te polecenia są również dostępne do użycia podczas rozszerzania [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="finding-environment-defined-commands"></a>Znajdowanie polecenia definiowane w środowisku  
 Polecenia środowiska są zdefiniowane w zestawie cztery pliki vsct:  
  
- SharedCmdDef.vsct  
  
- SharedCmdPlace.vsct  
  
- ShellCmdDef.vsct  
  
- ShellCmdPlace.vsct  
  
  Te pliki znajdują się w  *\<ścieżka instalacji programu Visual Studio SDK >* \VisualStudioIntegration\Common\Inc\\. Te pliki zawierają definicje i identyfikatory GUID, menu i grupy, które można używać w pliku konfiguracji (vsct) tabeli poleceń Twoje pakietu VSPackage jak kontenery dla własnego menu, grupy i polecenia.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Identyfikatory GUID i identyfikatory menu programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 Podano identyfikator GUID i identyfikator wartości menu na pasku menu programu Visual Studio i grup, które zawierają.  
  
 [Identyfikatory GUID i identyfikatory pasków narzędzi programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 Podano identyfikator GUID i identyfikator wartości pasków narzędzi w programie Visual Studio IDE i grup, które zawierają.  
  
 [Identyfikatory GUID i identyfikatory poleceń programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 Udostępnia wartości Identyfikator GUID i identyfikator polecenia zdefiniowane przez program Visual Studio IDE.  
  
## <a name="see-also"></a>Zobacz też  
 [Tabeli poleceń programu Visual Studio (. Pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Polecenia definiowane w środowisku IDE do rozszerzania systemów projektu](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

