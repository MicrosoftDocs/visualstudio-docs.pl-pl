---
title: Rozszerzalność debugera programu Visual Studio | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff4222b555fab73914776725fc79581f29fa5e53
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712500"
---
# <a name="visual-studio-debugger-extensibility"></a>Rozszerzalność debugera programu Visual Studio
Visual Studio zawiera w pełni interaktywny debuger kodu źródłowego, zapewniając zaawansowane i łatwe w użyciu narzędzie do śledzenia błędów w programie. Debuger ma pełną obsługę języka Visual Basic, C#, C/C++i JavaScript. Jednak z [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], który jest dostępny w [Centrum pobierania Microsoft](https://www.microsoft.com/download/details.aspx?id=21835), inne języki programowania mogą być obsługiwane w debuger z tych samych funkcji rozszerzonych.

 Debuger [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest wspólnym frontonu (czyli interfejsu użytkownika) do debugowania składników, które są z kolei specyficzne dla języka debugowane. W przypadku nowych języków wszystko, co [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest niezbędne do obsługi przez debugera jest utworzenie niezbędnych składników zaplecza, takich jak aparat debugowania (DE). W tym miejscu [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] pojawia się ten punkt.

 Zawiera [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] pełne odwołanie do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wszystkich elementów wymaganych do utworzenia nowego DE. Ponadto istnieją przykłady i samouczki, które pomogą Ci zacząć.

 Aby uzyskać pełną próbkę systemu projektu języka z obsługą debugowania, zobacz [przykład IronPython](https://www.microsoft.com/download/details.aspx?id=55984).

 W poniższych sekcjach opisano sposób rozszerzenia debugera przy użyciu pliku [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].

## <a name="in-this-section"></a>W tej sekcji
 [Rozpocznij pracę](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tym artykule opisano, co oferuje debugowanie i jak zainstalować sdk.

 [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md) Dokumenty niestandardowy proces DE, od przygotowania programu do DE do odłączenia DE.

 [Napisz ewaluatora wyrażenia CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) Wyjaśnia, czy należy napisać oceniającego wyrażenie.

 [Wybieranie strategii wdrażania aparatu debugowania](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) W tym artykule omówiono sposób implementacji DE.

 [Dokumentacja](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) Dokumenty [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfejsu API debugowania.

 [Próbki](../../extensibility/debugger/visual-studio-debugging-samples.md) Zawiera łącza do próbki ewaluatora wyrażeń środowiska wykonawczego języka wspólnego i przykładu aparatu debugowania.
