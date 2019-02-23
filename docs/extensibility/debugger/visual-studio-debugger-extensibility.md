---
title: Rozszerzalność debugera programu Visual Studio | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df9d1bccb2147d8416555099f3493ceac8c21b4b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56704803"
---
# <a name="visual-studio-debugger-extensibility"></a>Rozszerzeń debugera programu Visual Studio
Visual Studio zawiera debuger kodu źródłowego w pełni interaktywne, udostępnieniem zaawansowane i łatwe w użyciu narzędzia do śledzenia szczegółów błędów w programie. Debuger ma pełną obsługę języka Visual Basic, C#, C/C++ i JavaScript. Jednak w przypadku [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], która jest dostępna z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=214453), innych języków programowania może być obsługiwany w debugerze przy użyciu tych samych funkcji zaawansowanych.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuger jest wspólne frontonu (czyli interfejs użytkownika) do debugowania składników, które są kolei specyficznych dla języka debugowany. Dla nowych języków, wszystkie, które jest niezbędne do obsługi przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugera jest utworzenie niezbędnych składników zaplecza, takich jak aparat debugowania (DE). Ten punkt jest gdzie [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] pochodzą.

 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Obejmuje pełną dokumentację wszystkich [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] elementy wymagane do utworzenia nowego DE. Istnieją ponadto, przykłady i samouczki ułatwiające rozpoczęcie pracy.

 Pełny przykład języka systemu projektu za pomocą obsługi debugowania, zobacz [przykładowe IronPython](https://www.microsoft.com/download/details.aspx?id=55984).

 W poniższych sekcjach opisano, jak rozszerzyć debugera za pomocą [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].

## <a name="in-this-section"></a>W tej sekcji
 [Rozpoczynanie pracy](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) opisano, czego [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania oferty oraz instrukcje dotyczące instalowania zestawu SDK.

 [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md) dokumenty proces niestandardowej DE, od przygotowania programu do DE do odłączenia DE.

 [Pisanie ewaluatora wyrażeń CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) wyjaśnia, czy trzeba napisać ewaluatora wyrażeń.

 [Wybieranie strategii implementacji aparatu debugowania](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) w tym artykule omówiono sposób implementacji usługi DE.

 [Odwołanie](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) dokumenty [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowanie interfejsu API.

 [Przykłady](../../extensibility/debugger/visual-studio-debugging-samples.md) zawiera łącza do typowych przykładowy ewaluatora wyrażeń środowiska uruchomieniowego języka i przykładowe aparatu debugowania.
