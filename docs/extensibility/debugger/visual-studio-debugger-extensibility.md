---
title: Rozszerzalność debugera programu Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 58bfec6fa09f6450afb8170d60acad39edacd590
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72982456"
---
# <a name="visual-studio-debugger-extensibility"></a>Rozszerzalność debugera programu Visual Studio
Program Visual Studio zawiera w pełni interaktywny debuger kodu źródłowego, który zapewnia zaawansowane i łatwe w użyciu narzędzie do śledzenia błędów w programie. Debuger ma pełną obsługę Visual Basic, C#, C/C++i JavaScript. Jednak w przypadku [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], który jest dostępny w [Centrum pobierania Microsoft](https://www.microsoft.com/download/details.aspx?id=21835), inne języki programowania mogą być obsługiwane w debugerze przy użyciu tych samych bogatych funkcji.

 Debuger [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest typowym frontonem (czyli interfejsem użytkownika) do składników debugowania, które są z kolei charakterystyczne dla debugowanego języka. W przypadku nowych języków wszystkie te, które są niezbędne do obsługi przez debuger [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], to utworzenie niezbędnych składników zaplecza, takich jak aparat debugowania (Niemcy). Jest to miejsce, w którym znajduje się [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].

 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] zawiera pełne odwołanie do wszystkich elementów [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wymaganych do utworzenia nowego elementu DE. Ponadto istnieją przykłady i samouczki, które pomogą Ci rozpocząć pracę.

 Aby uzyskać pełny przykład systemu projektu języka z obsługą debugowania, zobacz [przykład IronPython](https://www.microsoft.com/download/details.aspx?id=55984).

 W poniższych sekcjach opisano sposób rozszerzający debuger przy użyciu [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].

## <a name="in-this-section"></a>W tej sekcji
 [Wprowadzenie](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) Zawiera opis [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i sposobu instalowania zestawu SDK.

 [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md) Dokumentuje niestandardowy proces usuwania od przygotowania programu do odłączenia.

 [Napisz ewaluatora wyrażeń CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) Wyjaśnia, czy należy napisać ewaluatora wyrażeń.

 [Wybierz strategię implementacji aparatu debugowania](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) W tym artykule omówiono sposób implementacji programu DE.

 [Dokumentacja](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) Dokumentuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowanie interfejsu API.

 [Przykłady](../../extensibility/debugger/visual-studio-debugging-samples.md) Zawiera linki do przykładowej ewaluatora wyrażeń środowiska uruchomieniowego języka wspólnego i próbki aparatu debugowania.
