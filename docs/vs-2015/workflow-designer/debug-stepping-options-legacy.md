---
title: Opcje debugowania wykonywania krokowego (starsza wersja) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- branch stepping
- stepping, options in workflow debugging
- debugging, stepping options
- debugging workflows, stepping options
- instance stepping
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b1f0761ba750146ce7f8cc52e6992dae689f7779
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54754854"
---
# <a name="debug-stepping-options-legacy"></a>Opcje debugowania wykonywania krokowego (starsza wersja)
W tym temacie opisano sposób debugowania [!INCLUDE[wf](../includes/wf-md.md)] aplikacji, które mają działań w starszej wersji [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Użyj starszego [!INCLUDE[wfd2](../includes/wfd2-md.md)] konieczność docelowy: [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Kiedy debugujesz starsze działania, które mają wykonania, takie jak **działaniu równoległym** lub **grupy ConditionedActivityGroup**, używasz jednego z poniższych dwóch opcji krokowo kodu .  
  
- **Rozgałęzienie, przechodzenie krok po kroku.** Ten tryb przechodzenie krok po kroku umożliwia krok po kroku i debugować gałąź działania złożonego, takich jak **działaniu równoległym** lub **ConditionalActivityGroup** działania. Gdy ta opcja umożliwia debugowanie nie zauważysz, że zmiana w formancie występuje ze względu na równoczesne wykonywanie innych działań w przepływie pracy. Debuger kroki tylko do działania w obecnie zaznaczonej gałęzi, podczas gdy inne działania w przepływie pracy, które mogą być wykonywane jednocześnie. Na przykład domyślnie skrajnie po lewej stronie gałęzi w **działaniu równoległym** działanie i pierwszego działania podrzędne **grupy ConditionedActivityGroup** działania są używane do przechodzenia. Jeśli użytkownik jest zainteresowany debugowania dowolne inne działanie gałęzi lub podrzędnej, jawnych punktów przerwania muszą znajdować się w gałęzi lub podrzędnej działania. Przechodzenie krok po kroku będzie kontynuowana w tej gałęzi, gdy punkt przerwania zostanie wyzwolony.  
  
- **Wystąpienia, przechodzenie krok po kroku.** Przechodzenie krok po kroku ten tryb pozwala na krok po kroku i debugowania równocześnie wykonywanych działań w przepływie pracy. Po wybraniu tej opcji można zauważyć, że zmiana w formancie występuje, gdy jednocześnie wykonywania działań uruchamianych w ramach przepływu pracy.  
  
  Domyślnie opcja przechodzenia krok po kroku gałęzi jest zaznaczone, a użytkownicy mogą przełączać się pomiędzy dwiema opcjami podczas debugowania przepływem pracy starszego.  
  
  Należy wybrać wystąpienie przechodzenie krok po kroku opcji podczas debugowania przepływów pracy automatu stanów starszej wersji.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie starszych wersji przepływów pracy](../workflow-designer/debugging-legacy-workflows.md)   
 [Instrukcje: Zmień debugowania opcję krokowego (starsza wersja)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)