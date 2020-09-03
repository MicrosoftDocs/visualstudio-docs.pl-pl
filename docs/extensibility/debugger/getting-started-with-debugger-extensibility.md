---
title: Wprowadzenie z rozszerzalnością debugera | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738595"
---
# <a name="get-started-with-debugger-extensibility"></a>Wprowadzenie do rozszerzalności debugera
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]Zawiera informacje potrzebne do tworzenia i dostosowywania składników debugera używanych do debugowania programów z poziomu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowiska.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugowanie dodaliśmy ulepszenia wynikające z rozbudowanych testów użyteczności wykonanych na wcześniejszych [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugerach. Debugowania można użyć [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] do przechodzenia przez aplikację z obsługą wielu języków lub podczas debugowania aplikacji i rozwiązań wielojęzycznych.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugowanie jest wykonywane poza procesem z debugowanym programem i w związku z tym jest mniej niepożądane w przestrzeni procesu aplikacji. W związku z tym łatwiej jest pisać składniki, które współdziałają z debugerem bez wpływu na program do debugowania.

 Aby najlepiej korzystać z programu [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , należy zapoznać się z następującymi elementami:

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Zintegrowane środowisko programistyczne (IDE)

- Język programowania C++

- ATL COM

## <a name="in-this-section"></a>W tej sekcji
 [Plan rozszerzający debuger](../../extensibility/debugger/roadmap-for-extending-the-debugger.md) Przedstawia proces implementowania debugowania w produkcie, w zależności od kompilatora i jego danych wyjściowych.

 [Składniki debugera](../../extensibility/debugger/debugger-components.md) Zawiera omówienie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] składników debugowania, takich jak aparat debugowania (de), ewaluatora wyrażeń (EE) i procedura obsługi symboli (SH).

 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md) Opisuje główne koncepcje dotyczące architektury debugowania.

 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md) Wyjaśnia, w jaki sposób aparat debugowania (DE) działa jednocześnie w kontekście kodu, dokumentacji oraz kontekstów oceny wyrażenia. Opisuje dla każdego z trzech kontekstów, lokalizację, pozycję lub ocenę, która jest dla niego odpowiednia.

 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md) Zawiera linki do różnych zadań debugowania, takich jak uruchamianie programu i ocenianie wyrażeń.
