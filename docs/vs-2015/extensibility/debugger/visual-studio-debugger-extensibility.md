---
title: Rozszerzalność debugera programu Visual Studio | Microsoft Docs
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
ms.openlocfilehash: 0b8d37954bf238b2ed1323bf021fded94ec0c584
ms.sourcegitcommit: 3a19319e2599bd193fb2ca32020ca53942974bfd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2019
ms.locfileid: "73983665"
---
# <a name="visual-studio-debugger-extensibility"></a>Rozszerzalność debugera programu Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Program Visual Studio zawiera w pełni interaktywny debuger kodu źródłowego, który zapewnia zaawansowane i łatwe w użyciu narzędzie do śledzenia błędów w programie. Debuger ma pełną pomoc techniczną Visual Basic C#,, CC++/i JavaScript. Jednak w przypadku [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], który jest dostępny w [Centrum pobierania Microsoft](https://www.microsoft.com/download/details.aspx?id=21835), inne języki programowania mogą być obsługiwane w debugerze przy użyciu tych samych bogatych funkcji.  
  
 Debuger [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] jest typowym frontonem (czyli interfejsem użytkownika) do składników debugowania, które są z kolei charakterystyczne dla debugowanego języka. W przypadku nowych języków wszystkie te, które są niezbędne do obsługi przez debuger [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], to utworzenie niezbędnych składników zaplecza, takich jak aparat debugowania (Niemcy). Jest to miejsce, w którym znajduje się [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)].  
  
 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] zawiera pełne odwołanie do wszystkich elementów [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] wymaganych do utworzenia nowego elementu DE. Ponadto istnieją przykłady i samouczki, które pomogą Ci rozpocząć pracę.  
  
 Aby uzyskać kompleksowy przykład systemu projektu języka z obsługą debugowania, zobacz [przykład IronPython](https://msdn.microsoft.com/4c41695c-12c1-4670-b43b-d8d84c9e4089).  
  
 W poniższych sekcjach opisano sposób rozszerzający debuger przy użyciu [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)].  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wprowadzenie](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 Zawiera opis [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] i sposobu instalowania zestawu SDK.  
  
 [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Dokumentuje niestandardowy proces usuwania od przygotowania programu do odłączenia.  
  
 [Pisanie ewaluatora wyrażeń środowiska CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 Wyjaśnia, czy należy napisać ewaluatora wyrażeń.  
  
 [Wybieranie strategii implementacji aparatu debugowania](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 W tym artykule omówiono sposób implementacji programu DE.  
  
 [Tematy pomocy](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 Dokumentuje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugowanie interfejsu API.  
  
 [Przykłady](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Zawiera linki do przykładowej ewaluatora wyrażeń środowiska uruchomieniowego języka wspólnego i próbki aparatu debugowania.
