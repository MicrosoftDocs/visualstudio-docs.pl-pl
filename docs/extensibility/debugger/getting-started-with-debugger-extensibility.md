---
title: Wprowadzenie do rozszerzalności debugera | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 99e2dabf18d3d00034d65a94c41f2e435ad64114
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350009"
---
# <a name="get-started-with-debugger-extensibility"></a>Wprowadzenie do rozszerzalności debugera
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Zawiera informacje potrzebne do tworzenia i dostosowywania składniki debugera, używane do debugowania programów z poziomu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowiska.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowanie dodano ulepszenia pochodną użyteczność obszerne testy wykonywane na poprzednim [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugery. Możesz użyć [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania do kroku za pośrednictwem aplikacji wielojęzycznych, lub można zaimplementować na bieżąco edytowanie zmiennych podczas debugowania aplikacji i rozwiązań dla wielu języków.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowanie jest wykonywany poza procesem z debugowanego i dlatego ta opcja jest mniej pożądana w przestrzeni procesu aplikacji. W związku z tym łatwiej jest zapis składników współdziałających z debugerem bez wywierania wpływu na debugowania programu.

 Aby optymalnie wykorzystać [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], należy zapoznać się z następującymi elementami:

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Zintegrowanego środowiska programistycznego (IDE)

- Język programowania w języku C++

- ATL COM

## <a name="in-this-section"></a>W tej sekcji
 [Plan rozwoju rozszerzania debugera](../../extensibility/debugger/roadmap-for-extending-the-debugger.md) zawiera opis procesu wdrażania, debugowanie w programie, w zależności od kompilatora i jego dane wyjściowe.

 [Składniki debugera](../../extensibility/debugger/debugger-components.md) zawiera omówienie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowanie składników, które obejmują aparat debugowania (DE), Ewaluator wyrażeń (EE) i obsługi symboli (SH).

 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md) opisano główne pojęcia dotyczące architektury debugowania.

 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md) wyjaśnia, jak aparat debugowania (DE) działa jednocześnie w kontekstach oceny kodu, dokumentację i wyrażenia. W tym artykule opisano, dla każdego z trzech kontekstów, lokalizacji, pozycja lub oceny odpowiednie do niego.

 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md) zawiera łącza do różnych zadań debugowania, takich jak uruchamianie programu i wyrażeń.