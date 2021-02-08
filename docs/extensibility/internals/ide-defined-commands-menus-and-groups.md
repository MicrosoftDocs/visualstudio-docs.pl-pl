---
title: IDE-Defined polecenia, menu i grupy | Microsoft Docs
description: Dowiedz się więcej na temat menu, poleceń i grup poleceń, które są zdefiniowane w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e46832803008ea65d0f7ec4f2723a615ba496b94
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840083"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Polecenia, menu i grupy definiowane w środowisku IDE
Wiele menu, poleceń i grup poleceń jest już zdefiniowanych do użycia przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Te polecenia są również dostępne do użycia podczas jego rozszerania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="finding-environment-defined-commands"></a>Znajdowanie Environment-Defined poleceń
 Polecenia środowiska są zdefiniowane w zbiorze czterech plików vsct:

- SharedCmdDef. vsct

- SharedCmdPlace. vsct

- ShellCmdDef. vsct

- ShellCmdPlace. vsct

  Te pliki znajdują się w *\<Visual Studio SDK installation path>* \VisualStudioIntegration\Common\Inc \\ . Pliki te zawierają definicje i identyfikatory GUID menu i grup, których można użyć w pliku konfiguracji tabeli poleceń (. vsct) pakietu VSPackage jako kontenery dla własnych menu, grup i poleceń.

## <a name="in-this-section"></a>W tej sekcji
- [Identyfikatory GUID i identyfikatory menu programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 Zawiera wartości identyfikatora GUID i identyfikatora menu na pasku menu programu Visual Studio i zawartych w nich grup.

- [Identyfikatory GUID i identyfikatory pasków narzędzi programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 Zawiera identyfikatory GUID i identyfikator pasków narzędzi w środowisku IDE programu Visual Studio oraz zawartych w nich grup.

- [Identyfikatory GUID i identyfikatory poleceń programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 Zawiera identyfikatory GUID i identyfikator poleceń zdefiniowanych przez środowisko IDE programu Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Tabela poleceń programu Visual Studio (pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Polecenia definiowane w środowisku IDE do rozszerzania systemów projektu](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
