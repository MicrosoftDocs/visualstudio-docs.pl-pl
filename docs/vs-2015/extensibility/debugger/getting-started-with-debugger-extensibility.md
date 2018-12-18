---
title: Wprowadzenie do rozszerzalności debugera | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bafdd45b57a9fe660e97127c2c99c333ead0e60a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721166"
---
# <a name="getting-started-with-debugger-extensibility"></a>Wprowadzenie do rozszerzalności debugera
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] Udostępnia informacje niezbędne do tworzenia i dostosowywania składniki debugera, używane do debugowania programów z poziomu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] środowiska.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugowanie dodano ulepszenia pochodną użyteczność obszerne testy wykonywane na poprzednim [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugery. Możesz użyć [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugowania do kroku za pośrednictwem aplikacji wielojęzycznych, lub można zaimplementować na bieżąco edytowanie zmiennych podczas debugowania aplikacji i rozwiązań dla wielu języków.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugowanie jest wykonywany poza procesem z debugowanego i dlatego ta opcja jest mniej pożądana w przestrzeni procesu aplikacji. W związku z tym łatwiej jest zapis składników współdziałających z debugerem bez wywierania wpływu na debugowania programu.  
  
 Aby optymalnie wykorzystać [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], należy zapoznać się z następujących czynności:  
  
-   [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Zintegrowanego środowiska programistycznego (IDE)  
  
-   Język programowania w języku C++  
  
-   ATL COM  
  
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

