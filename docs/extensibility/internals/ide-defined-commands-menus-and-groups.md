---
title: Polecenia definiowane w IDE, menu i grupy | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 727c999e275830260ce83eac3d2d72024e89882b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909867"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Polecenia, menu i grupy definiowane w środowisku IDE
Wiele menu, poleceń i polecenia grupy są już zdefiniowane na potrzeby używania przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Te polecenia są również dostępne do użycia podczas rozszerzania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="finding-environment-defined-commands"></a>Znajdowanie polecenia definiowane w środowisku
 Polecenia środowiska są zdefiniowane w zestawie cztery pliki vsct:

- SharedCmdDef.vsct

- SharedCmdPlace.vsct

- ShellCmdDef.vsct

- ShellCmdPlace.vsct

  Te pliki znajdują się w  *\<ścieżka instalacji programu Visual Studio SDK >* \VisualStudioIntegration\Common\Inc\\. Te pliki zawierają definicje i identyfikatory GUID, menu i grupy, które można używać w pliku konfiguracji (vsct) tabeli poleceń Twoje pakietu VSPackage jak kontenery dla własnego menu, grupy i polecenia.

## <a name="in-this-section"></a>W tej sekcji
- [Identyfikatory GUID i identyfikatory menu programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 Podano identyfikator GUID i identyfikator wartości menu na pasku menu programu Visual Studio i grup, które zawierają.

- [Identyfikatory GUID i identyfikatory pasków narzędzi programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 Podano identyfikator GUID i identyfikator wartości pasków narzędzi w programie Visual Studio IDE i grup, które zawierają.

- [Identyfikatory GUID i identyfikatory poleceń programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 Udostępnia wartości Identyfikator GUID i identyfikator polecenia zdefiniowane przez program Visual Studio IDE.

## <a name="see-also"></a>Zobacz też
- [Tabela poleceń programu Visual Studio (pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Polecenia definiowane w środowisku IDE do rozszerzania systemów projektu](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)