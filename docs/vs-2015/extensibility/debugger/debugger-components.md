---
title: Składniki debugera | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
caps.latest.revision: 31
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 12f865e7d4c44cfa4002b330ed85ec95f95a8ef9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200670"
---
# <a name="debugger-components"></a>Składniki debugera
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Debuger jest zaimplementowany jako pakietu VSPackage i zarządza całą sesją debugowania. Sesja debugowania obejmuje następujące elementy:  
  
- **Pakiet debugowania:** [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debuger zapewnia ten sam interfejs użytkownika niezależnie od tego, co jest debugowane.  
  
- **Menedżer debugowania sesji (SDM):** Zapewnia spójny interfejs programistyczny [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugera służący do zarządzania różnymi aparatami debugowania. Jest zaimplementowany przez [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- **Menedżer debugowania procesów (PDM):** Zarządza, dla wszystkich uruchomionych wystąpień programu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , listę wszystkich programów, które mogą być lub są debugowane. Jest zaimplementowany przez [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- **Aparat debugowania (de):** Jest odpowiedzialny za monitorowanie debugowanego programu, komunikowanie się stanu uruchomionego programu z modelem SDM i PDM oraz współdziałanie z programem Expression ewaluatora i dostawcą symboli w celu zapewnienia analiz w czasie rzeczywistym stanu pamięci i zmiennych programu. Jest ona implementowana przez [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] program (dla obsługiwanych języków) i dostawców innych firm, którzy chcą obsługiwać własny czas wykonywania.  
  
- **Ewaluatora wyrażeń (EE):** Zapewnia obsługę dynamicznego oceniania zmiennych i wyrażeń dostarczonych przez użytkownika, gdy program został zatrzymany w określonym punkcie. Jest ona implementowana przez [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] program (dla obsługiwanych języków) i dostawców innych firm, którzy chcą obsługiwać własne języki.  
  
- **Dostawca symboli (SP):** Nazywana również obsługą symboli, mapuje symbole debugowania programu do uruchomionego wystąpienia programu, aby można było uzyskać zrozumiałe informacje (takie jak debugowanie na poziomie kodu i obliczanie wyrażeń). Jest implementowana przez [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] program (dla symboli środowiska uruchomieniowego języka wspólnego [CLR] i format pliku symboli programu [PDB]) oraz dostawców innych firm, którzy posiadają zastrzeżoną metodę przechowywania informacji o debugowaniu.  
  
  Na poniższym diagramie przedstawiono relację między tymi elementami debugera programu Visual Studio.  
  
  ![Debugowanie składników — przegląd](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Pakiet debugowania](../../extensibility/debugger/debug-package.md)  
 Omawia pakiet debugowania, który działa w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] powłoce i obsługuje cały interfejs użytkownika.  
  
 [Menedżer debugowania procesów](../../extensibility/debugger/process-debug-manager.md)  
 Zawiera omówienie funkcji PDM, które jest menedżerem procesów, które mogą być debugowane.  
  
 [Menedżer debugowania sesji](../../extensibility/debugger/session-debug-manager.md)  
 Definiuje model SDM, który zapewnia ujednolicony widok sesji debugowania do IDE. Model SDM zarządza DE.  
  
 [Aparat debugowania](../../extensibility/debugger/debug-engine.md)  
 Dokumentuje usługi debugowania, które zawiera.  
  
 [Tryby operacyjne](../../extensibility/debugger/operational-modes.md)  
 Zawiera omówienie trzech trybów, w których środowisko IDE może działać: tryb projektowania, tryb uruchamiania i tryb przerwania. Omówiono również mechanizmy przejściowe.  
  
 [Ewaluator wyrażeń](../../extensibility/debugger/expression-evaluator.md)  
 Wyjaśnia przeznaczenie EE w czasie wykonywania.  
  
 [Dostawca symboli](../../extensibility/debugger/symbol-provider.md)  
 W tym artykule omówiono, w jaki sposób, w trakcie implementacji, dostawca symboli oblicza zmienne i wyrażenia.  
  
 [Wizualizator typów i przeglądarka niestandardowa](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)  
 W tym artykule omówiono wizualizację typu i Podgląd niestandardową, a także rolę, jaką ewaluatora wyrażeń odgrywa w obsłudze obu tych elementów.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)  
 Opisuje główne koncepcje dotyczące architektury debugowania.  
  
 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)  
 Wyjaśnia, jak działa w ramach kodu, dokumentacji i kontekstów oceny wyrażenia. Opisuje dla każdego z trzech kontekstów, lokalizację, pozycję lub ocenę, która jest dla niego odpowiednia.  
  
 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)  
 Zawiera linki do różnych zadań debugowania, takich jak uruchamianie programu i ocenianie wyrażeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
