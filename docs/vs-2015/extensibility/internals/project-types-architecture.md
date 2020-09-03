---
title: Architektura typów projektów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 775656d2190a36f62c2b047c1ff7f1e02575c1ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154145"
---
# <a name="project-types-architecture"></a>Architektura typów projektów
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ta sekcja zawiera szczegółowe informacje o architekturze typów projektów w programie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Elementy modelu projektu](../../extensibility/internals/elements-of-a-project-model.md)  
 Wyświetla listę usług, które mogą być używane przez typ projektu i interfejsy, które musi zaimplementować.  
  
 [Podstawowe składniki modelu projektu](../../extensibility/internals/project-model-core-components.md)  
 Opisuje typy projektów interfejsów, które muszą implementować i opcjonalnie można zaimplementować w celu zapewnienia dodatkowych funkcji.  
  
 [Kiedy należy tworzyć typy projektów](../../extensibility/internals/when-to-create-project-types.md)  
 Pomaga określić, kiedy należy utworzyć typ projektu i kiedy można użyć innej [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] funkcji rozszerzalności, takiej jak pakietów VSPackage i Editors, aby osiągnąć ten sam cel.  
  
 [Hierarchie i wybór](../../extensibility/internals/hierarchies-and-selection.md)  
 Opisuje, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] w jaki sposób używa hierarchii i kontekstu wyboru w celu zapewnienia spójnego i uproszczonego środowiska użytkownika.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Podtypy projektów](../../extensibility/internals/project-subtypes.md)  
 Wyjaśnia, w jaki sposób podtypy projektów pozwalają dostosować zachowanie systemów projektowych [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] i [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] .  
  
 [Typy projektów](../../extensibility/internals/project-types.md)  
 Zawiera omówienie projektów jako podstawowych bloków konstrukcyjnych [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zintegrowanego środowiska programistycznego (IDE). Linki są dostarczane do dodatkowych tematów, które wyjaśniają, jak projekty kontrolują Kompilowanie i kompilowanie kodu.
