---
title: Polecenia, menu i grupy zdefiniowane przez IDE | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6557f49b019a6793698dabe852919ec2e9f28cfd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707716"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Polecenia, menu i grupy definiowane w środowisku IDE
Wiele menu, poleceń i grup poleceń są [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] już zdefiniowane do użytku przez IDE. Te polecenia są również dostępne do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]użycia podczas rozszerzania .

## <a name="finding-environment-defined-commands"></a>Znajdowanie poleceń zdefiniowanych przez środowisko
 Polecenia środowiska są zdefiniowane w zestawie czterech plików vsct:

- SharedCmdDef.vsct

- SharedCmdPlace.vsct

- Polecenie ShellCmdDef.vsct

- ShellCmdPlace.vsct

  Te pliki znajdują się w\\ * \<ścieżce instalacji zestawów SDK programu Visual Studio>* \VisualStudioIntegration\Common\Inc . Pliki te zawierają definicje i identyfikatory GUID z menu i grup, które można użyć w konfiguracji tabeli poleceń (.vsct) pliku VSPackage jako kontenery dla własnych menu, grup i poleceń.

## <a name="in-this-section"></a>W tej sekcji
- [Identyfikatory GUID i identyfikatory menu programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 Podaje wartości identyfikatora GUID i identyfikatora menu na pasku menu programu Visual Studio oraz w grupach, które zawierają.

- [Identyfikatory GUID i identyfikatory pasków narzędzi programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 Nadaje wartości identyfikatora GUID i identyfikatora pasków narzędzi w programie Visual Studio IDE i grup, które zawierają.

- [Identyfikatory GUID i identyfikatory poleceń programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 Nadaje wartości identyfikatora GUID i identyfikatora poleceń zdefiniowanych przez ide programu Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Tabela poleceń programu Visual Studio (pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Polecenia definiowane w środowisku IDE do rozszerzania systemów projektu](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
