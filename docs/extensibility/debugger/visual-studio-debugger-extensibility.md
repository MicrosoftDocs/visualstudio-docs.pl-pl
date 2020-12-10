---
title: Rozszerzalność debugera programu Visual Studio | Microsoft Docs
description: W tym artykule opisano rozszerzalność debugera programu Visual Studio i przedstawiono linki do artykułów na temat debugowania programu Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: a072373ce0cf7633c595eb549455e6ecd62df887
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995996"
---
# <a name="visual-studio-debugger-extensibility"></a>Rozszerzalność debugera programu Visual Studio
Program Visual Studio zawiera w pełni interaktywny debuger kodu źródłowego, który zapewnia zaawansowane i łatwe w użyciu narzędzie do śledzenia błędów w programie. Debuger ma pełną obsługę Visual Basic, C#, C/C++ i JavaScript. Jednak w przypadku programu [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , który jest dostępny w [Centrum pobierania Microsoft](https://www.microsoft.com/download/details.aspx?id=21835), inne języki programowania mogą być obsługiwane w debugerze z tymi samymi, bogatymi funkcjami.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Debuger jest wspólnym frontonem (czyli interfejsem użytkownika) do składników debugowania, które są z kolei charakterystyczne dla debugowanego języka. W przypadku nowych języków wszystkie te, które są niezbędne do obsługi przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debuger, to tworzenie niezbędnych składników zaplecza, takich jak aparat debugowania (de). Ten punkt to miejsce, w którym się znajduje [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]Obejmuje kompletne odwołanie do wszystkich [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] elementów wymaganych do utworzenia nowego elementu de. Ponadto istnieją przykłady i samouczki, które pomogą Ci rozpocząć pracę.

 Aby uzyskać pełny przykład systemu projektu języka z obsługą debugowania, zobacz [przykład IronPython](https://www.microsoft.com/download/details.aspx?id=55984).

 W poniższych sekcjach opisano, jak zwiększyć debuger za pomocą [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

## <a name="in-this-section"></a>W tej sekcji
 [Wprowadzenie](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) Opisuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , jakie oferty debugowania oraz jak zainstalować zestaw SDK.

 [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md) Dokumentuje niestandardowy proces usuwania od przygotowania programu do odłączenia.

 [Napisz ewaluatora wyrażeń CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) Wyjaśnia, czy należy napisać ewaluatora wyrażeń.

 [Wybierz strategię implementacji aparatu debugowania](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) W tym artykule omówiono sposób implementacji programu DE.

 [Dokumentacja](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) Dokumentuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfejs API debugowania.

 [Przykłady](../../extensibility/debugger/visual-studio-debugging-samples.md) Zawiera linki do przykładowej ewaluatora wyrażeń środowiska uruchomieniowego języka wspólnego i próbki aparatu debugowania.
