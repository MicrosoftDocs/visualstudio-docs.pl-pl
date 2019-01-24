---
title: Rozszerzalność debugera programu Visual Studio | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 528716c4ea354ab63dc7fcab2b3f90fe2860b655
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54771935"
---
# <a name="visual-studio-debugger-extensibility"></a>Rozszerzalność debugera programu Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio zawiera debuger kodu źródłowego w pełni interaktywne, udostępnieniem zaawansowane i łatwe w użyciu narzędzia do śledzenia szczegółów błędów w programie. Debuger ma pełną obsługę języka Visual Basic, C#, C/C++ i JavaScript. Jednak w przypadku [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], która jest dostępna z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=214453),, innych języków programowania może być obsługiwany w debugerze przy użyciu tych samych funkcji zaawansowanych.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debuger jest wspólne frontonu (czyli interfejs użytkownika) do debugowania składników, które są kolei specyficznych dla języka debugowany. Dla nowych języków, wszystkie, które jest niezbędne do obsługi przez [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugera jest utworzenie niezbędnych składników zaplecza, takich jak aparat debugowania (DE). To tutaj [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] pochodzą.  
  
 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] Obejmuje pełną dokumentację wszystkich [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] elementy wymagane do utworzenia nowego DE. Istnieją ponadto, przykłady i samouczki ułatwiające rozpoczęcie pracy.  
  
 Przykład end-to-end systemu projektu języka, za pomocą obsługi debugowania można zobaczyć [przykładowe IronPython](http://msdn.microsoft.com/4c41695c-12c1-4670-b43b-d8d84c9e4089).  
  
 W poniższych sekcjach opisano, jak rozszerzyć debugera za pomocą [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)].  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wprowadzenie](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 Opisano, czego [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugowania oferty oraz instrukcje dotyczące instalowania zestawu SDK.  
  
 [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Dokumenty proces niestandardowej DE, od przygotowania programu do DE do odłączenia DE.  
  
 [Pisanie ewaluatora wyrażeń środowiska CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 W tym artykule wyjaśniono, czy trzeba napisać ewaluatora wyrażeń.  
  
 [Wybieranie strategii implementacji aparatu debugowania](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 W tym artykule omówiono sposób implementacji usługi DE.  
  
 [Dokumentacja](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 Dokumenty [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugowanie interfejsu API.  
  
 [Przykłady](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Zawiera łącza do typowych przykładowy ewaluatora wyrażeń środowiska uruchomieniowego języka i przykładowym aparatu debugowania.
