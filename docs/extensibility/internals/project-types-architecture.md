---
title: Architektura typów projektów | Microsoft Docs
description: Ten artykuł zawiera linki do artykułów zawierających szczegółowe informacje o architekturze typów projektów w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6c9463604cda8c26a53cb02802252dfe40d309b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970130"
---
# <a name="project-types-architecture"></a>Architektura typów projektów
Ta sekcja zawiera szczegółowe informacje o architekturze typów projektów w programie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="in-this-section"></a>W tej sekcji
- [Elementy modelu projektu](../../extensibility/internals/elements-of-a-project-model.md)

 Wyświetla listę usług, które mogą być używane przez typ projektu i interfejsy, które musi zaimplementować.

- [Podstawowe składniki modelu projektu](../../extensibility/internals/project-model-core-components.md)

 Opisuje typy projektów interfejsów, które muszą implementować i opcjonalnie można zaimplementować w celu zapewnienia dodatkowych funkcji.

- [Kiedy należy tworzyć typy projektów](../../extensibility/internals/when-to-create-project-types.md)

 Pomaga określić, kiedy należy utworzyć typ projektu i kiedy można użyć innej [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] funkcji rozszerzalności, takiej jak pakietów VSPackage i Editors, aby osiągnąć ten sam cel.

- [Hierarchie i wybór](../../extensibility/internals/hierarchies-and-selection.md)

 Opisuje, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] w jaki sposób używa hierarchii i kontekstu wyboru w celu zapewnienia spójnego i uproszczonego środowiska użytkownika.

## <a name="related-sections"></a>Sekcje pokrewne
- [Podtypy projektów](../../extensibility/internals/project-subtypes.md)

 Wyjaśnia, w jaki sposób podtypy projektów pozwalają dostosować zachowanie systemów projektowych [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] i [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] .

- [Typy projektów](../../extensibility/internals/project-types.md)

 Zawiera omówienie projektów jako podstawowych bloków konstrukcyjnych [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowanego środowiska programistycznego (IDE). Linki są dostarczane do dodatkowych tematów, które wyjaśniają, jak projekty kontrolują Kompilowanie i kompilowanie kodu.
