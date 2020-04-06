---
title: Architektura typów projektów | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e53929b1ec2ed9c73191bf16f1cedc84a53b58f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706321"
---
# <a name="project-types-architecture"></a>Architektura typów projektów
Ta sekcja zawiera szczegółowe informacje na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]temat architektury typów projektów w programie .

## <a name="in-this-section"></a>W tej sekcji
- [Elementy modelu projektu](../../extensibility/internals/elements-of-a-project-model.md)

 Wyświetla listę usług, z które może korzystać typ projektu i interfejsów, które musi implementować.

- [Podstawowe składniki modelu projektu](../../extensibility/internals/project-model-core-components.md)

 W tym artykule opisano interfejsy typy projektu zarówno należy zaimplementować i opcjonalnie można zaimplementować w celu zapewnienia dodatkowych funkcji.

- [Kiedy należy tworzyć typy projektów](../../extensibility/internals/when-to-create-project-types.md)

 Pomaga zdecydować, kiedy należy utworzyć typ projektu i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kiedy można użyć innej funkcji rozszerzalności, takich jak VSPackages i edytorów, aby osiągnąć ten sam cel.

- [Hierarchie i wybór](../../extensibility/internals/hierarchies-and-selection.md)

 W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tym artykule opisano, jak używa hierarchii i kontekstu wyboru, aby zapewnić spójne i uproszczone środowisko użytkownika.

## <a name="related-sections"></a>Sekcje pokrewne
- [Podtypy projektów](../../extensibility/internals/project-subtypes.md)

 W tym artykule wyjaśniono, w jaki sposób [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] podtypy projektu umożliwiają dostosowanie zachowania systemów projektu i [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].

- [Project Types (Typy projektów)](../../extensibility/internals/project-types.md)

 Zawiera omówienie projektów jako podstawowych [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] elementów składowych zintegrowanego środowiska programistycznego (IDE). Łącza są dostarczane do dodatkowych tematów, które wyjaśniają, jak projekty kontroli tworzenia i kompilacji kodu.
