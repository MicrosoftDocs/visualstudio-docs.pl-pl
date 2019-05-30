---
title: Architektura typów projektów | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d77524097509c45c23d6a3d9cc147e5aba6691d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318900"
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