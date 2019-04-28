---
title: Architektura typów projektów | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3aee42e266e1082228c30ce56ac128e19ef6c576
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909463"
---
# <a name="project-types-architecture"></a>Architektura typów projektów
Ta sekcja zawiera szczegółowe informacje o architekturze typów projektów w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="in-this-section"></a>W tej sekcji
- [Elementy modelu projektu](../../extensibility/internals/elements-of-a-project-model.md)

 Wyświetla listę usług, których może używać typu projektu i musi on implementować interfejs.

- [Podstawowe składniki modelu projektu](../../extensibility/internals/project-model-core-components.md)

 W tym artykule opisano interfejsy typów projektów należy zaimplementować i opcjonalnie można zaimplementować w celu zapewnienia dodatkowych funkcji.

- [Kiedy należy tworzyć typy projektów](../../extensibility/internals/when-to-create-project-types.md)

 Wpisz ułatwia podjęcie decyzji, kiedy należy utworzyć projekt, a kiedy można użyć innej [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] funkcji rozszerzeń, takich jak pakietów VSPackage i edytorów, aby osiągnąć ten sam cel.

- [Hierarchie i wybór](../../extensibility/internals/hierarchies-and-selection.md)

 W tym artykule opisano sposób [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] używa hierarchii i kontekst zaznaczenia, aby zapewnić spójne i uproszczone środowisko.

## <a name="related-sections"></a>Sekcje pokrewne
- [Podtypy projektów](../../extensibility/internals/project-subtypes.md)

 Wyjaśnia, jak podtypy projektów pozwalają dostosować zachowanie systemów projektu [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] i [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].

- [Typy projektów](../../extensibility/internals/project-types.md)

 Zawiera omówienie projektów jako podstawowe bloki konstrukcyjne [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowanego środowiska programistycznego (IDE). Podano linki do dodatkowych tematów, które wyjaśniają, jak kontrolować projektów, tworzenie i kompilowanie kodu.