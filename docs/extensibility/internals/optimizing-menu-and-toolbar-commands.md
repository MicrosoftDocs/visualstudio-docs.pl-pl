---
title: Optymalizowanie poleceń menu i paska narzędzi | Microsoft Docs
description: Dowiedz się, jak program Visual Studio może zminimalizować liczbę poleceń spowodowanych przez dodanie pakietów VSPackage i odpowiadających im poleceń.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], menus
- commands [Visual Studio], toolbars
- menus [Visual Studio SDK], commands
- menu commands, implementing
- toolbars [Visual Studio], commands
ms.assetid: 8385f1a6-1e98-4dca-83d2-fcbed7177242
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b35f3a87f819885685b54888031883f4c2776d04
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877601"
---
# <a name="optimizing-menu-and-toolbar-commands"></a>Optymalizacja poleceń menu i paska narzędzi
Dodanie pakietów VSPackage i odpowiadające im poleceń, które [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mogą spowodować zaatakowany interfejs użytkownika. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zapewnia sposoby, aby pomóc zminimalizować pomylenie poleceń interfejsu użytkownika.

## <a name="in-this-section"></a>W tej sekcji
- [Udostępnianie poleceń](../../extensibility/internals/making-commands-available.md)

 Zawiera ogólne wskazówki dotyczące minimalizowania natłoku [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika podczas dodawania pakietów VSPackage.

- [Wskazówki dotyczące umieszczania](../../extensibility/internals/command-placement-guidelines.md)

 Zawiera szczegółowe wskazówki dotyczące implementowania pakietu VSPackage zgodnie z rozmiarem zestawu poleceń.

## <a name="related-sections"></a>Sekcje pokrewne
- [Polecenia, menu i paski narzędzi](../../extensibility/internals/commands-menus-and-toolbars.md)

 Wyjaśnia, jak utworzyć interfejs użytkownika, który obejmuje menu, paski narzędzi i pola kombi poleceń.
