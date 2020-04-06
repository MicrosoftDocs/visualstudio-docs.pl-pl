---
title: Wprowadzenie do rozszerzalności debugera | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 153db8889c78890a31a2e8003e6aa95ed24a02eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738595"
---
# <a name="get-started-with-debugger-extensibility"></a>Wprowadzenie do rozszerzalności debugera
Zawiera [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] informacje, które należy utworzyć i dostosować składniki debugera używane do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania programów z poziomu środowiska.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]debugowanie dodał ulepszenia wynikające z szeroko zakrojonych testów [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] użyteczności przeprowadzonych na poprzednich debugerów. Debugowania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] można użyć do przechodzenia przez aplikację wielojęzyczną lub można zaimplementować edycję zmiennych w locie podczas debugowania aplikacji i rozwiązań wielojęzycznych.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]debugowanie jest wykonywane poza procesem z debugowanym programem i dlatego jest mniej inwazyjne w przestrzeni procesu aplikacji. W związku z tym łatwiej jest pisać składniki, które współdziałają z debugerem bez wpływu na program debugowania.

 Aby najlepiej [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]użyć , należy zapoznać się z następującymi elementami:

- Zintegrowane [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowisko programistyczne (IDE)

- Język programowania C++

- ATL COM

## <a name="in-this-section"></a>W tej sekcji
 [Plan rozszerzenia debugera](../../extensibility/debugger/roadmap-for-extending-the-debugger.md) Przedstawia proces implementowania debugowania w produkcie, w zależności od kompilatora i jego danych wyjściowych.

 [Składniki debugera](../../extensibility/debugger/debugger-components.md) Zawiera omówienie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] składników debugowania, które obejmują aparat debugowania (DE), oceniający wyrażenia (EE) i program obsługi symboli (SH).

 [Pojęcia debugera](../../extensibility/debugger/debugger-concepts.md) W tym artykule opisano główne debugowanie koncepcji architektury.

 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md) Wyjaśniono, jak aparat debugowania (DE) działa jednocześnie w kontekście oceny kodu, dokumentacji i wyrażenia. Opisuje, dla każdego z trzech kontekstów, lokalizacji, pozycji lub oceny istotne dla niego.

 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md) Zawiera łącza do różnych zadań debugowania, takich jak uruchamianie programu i oceny wyrażeń.
