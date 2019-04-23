---
title: Wprowadzenie do rozszerzalności debugera | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d1c616c7cf8ed90ec3d76046892167b9b742a1b0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60085678"
---
# <a name="getting-started-with-debugger-extensibility"></a>Wprowadzenie do rozszerzalności debugera
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] Udostępnia informacje niezbędne do tworzenia i dostosowywania składniki debugera, używane do debugowania programów z poziomu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] środowiska.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugowanie dodano ulepszenia pochodną użyteczność obszerne testy wykonywane na poprzednim [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugery. Możesz użyć [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugowania do kroku za pośrednictwem aplikacji wielojęzycznych, lub można zaimplementować na bieżąco edytowanie zmiennych podczas debugowania aplikacji i rozwiązań dla wielu języków.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugowanie jest wykonywany poza procesem z debugowanego i dlatego ta opcja jest mniej pożądana w przestrzeni procesu aplikacji. W związku z tym łatwiej jest zapis składników współdziałających z debugerem bez wywierania wpływu na debugowania programu.  
  
 Aby optymalnie wykorzystać [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], należy zapoznać się z następujących czynności:  
  
- [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Zintegrowanego środowiska programistycznego (IDE)  
  
- Język programowania w języku C++  
  
- ATL COM  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Plan rozwoju rozszerzania debugera](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Zawiera opis procesu wdrażania, debugowanie w programie, w zależności od kompilatora i jego dane wyjściowe.  
  
 [Składniki debugera](../../extensibility/debugger/debugger-components.md)  
 Zawiera omówienie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugowanie składników, które obejmują aparat debugowania (DE), Ewaluator wyrażeń (EE) i obsługi symboli (SH).  
  
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)  
 W tym artykule opisano główne pojęcia dotyczące architektury debugowania.  
  
 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)  
 W tym artykule wyjaśniono, jak aparat debugowania (DE) działa jednocześnie w ramach kodu, dokumentację i konteksty oceny wyrażenia. W tym artykule opisano, dla każdego z trzech kontekstów, lokalizacji, pozycja lub oceny odpowiednie do niego.  
  
 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)  
 Zawiera łącza do różnych zadań debugowania, takie jak uruchamianie programu i wyrażeń.
