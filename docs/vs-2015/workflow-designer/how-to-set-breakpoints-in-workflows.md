---
title: 'Instrukcje: Ustawianie punktów przerwania w przepływach pracy | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dc428d70e036da311d2cf3050cec9e94a13782e3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60089981"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Instrukcje: Ustawianie punktów przerwania w przepływach pracy
Kiedy używasz [!INCLUDE[wfd1](../includes/wfd1-md.md)], możesz ustawić punkty przerwania na graficzny przepływów pracy, tak jak w kodzie języka Visual Basic lub C#. Zgodnie z oczekiwaniami, zatrzyma wykonywanie przepływu pracy, w każdym punkcie przerwania, który został ustawiony.  
  
 Punkt przerwania ma trzy stany: *Oczekujące*, *powiązany*, i *błąd*. Po ustawieniu punktu przerwania jest oczekujące i jest reprezentowana przez stałe czerwoną ikonę. Po załadowaniu szablonu przepływu pracy środowiska uruchomieniowego staje się powiązany. Jeśli określisz ma niewłaściwy format dla punktu przerwania, takich jak nazwa działania, który nie jest prawidłowy, pojawi się okno błędu. Punkt przerwania nadal jest dodawany do okna punkt przerwania, ale jest oznaczony za pomocą małych "x".  
  
> [!NOTE]
>  Ustawianie punktów przerwania w przepływach pracy, wywoływane jest nieobsługiwana.  
> 
> [!WARNING]
>  Upewnij się, że wybrano opcję **Włącz tylko mój kod (tylko zarządzany)** z **narzędzia**, **opcje**, **debugowanie** menu przed debugowanie. Jeśli masz dwie sekwencje zagnieżdżone w obrębie innej sekwencji, a następnie ustaw punkt przerwania w pierwszej sekwencji wewnętrzny, naciskając klawisz **F11** nie będzie debugowania do drugiej sekwencji wewnętrzny, jeśli <strong>Włącz tylko mój kod (tylko zarządzany)</strong>nie wybrano opcji.  
> 
> [!WARNING]
>  Punkty przerwania w przepływie pracy nie zostanie pobieranie odwołań, jeśli Pełna ścieżka do właściwości pliku XAML nie jest dokładne. Pełna ścieżka do pliku XAML nie jest dokładne po przeniesieniu projektu/rozwiązania do innego folderu lub innego komputera. Wybierz klawisze Ctrl + S, aby zapisać i zaktualizować właściwość pełną ścieżkę.  
  
### <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>Aby ustawić punkt przerwania w działaniu w widoku projektu  
  
1. Wybierz czynność chcesz, aby debuger przerywał działanie w przypadku.  
  
2. Na **debugowania** menu, wybierz opcję **Przełącz punkt przerwania**. Czerwona ikona pojawi się do górnej krawędzi lewej działania.  
  
     Alternatywnie można również nacisnąć skrót **F9** klucza po wybraniu działania lub można kliknij prawym przyciskiem myszy działanie i wybierz opcję **punktu przerwania** następnie **Wstaw punkt przerwania**z menu kontekstowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Wywoływanie debugera przepływu pracy](../workflow-designer/how-to-invoke-the-workflow-debugger.md)   
 [Debugowanie przepływów pracy za pomocą projektanta przepływu pracy](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)   
 [Instrukcje: Debugowanie kodu XAML za pomocą Projektanta przepływu pracy](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)