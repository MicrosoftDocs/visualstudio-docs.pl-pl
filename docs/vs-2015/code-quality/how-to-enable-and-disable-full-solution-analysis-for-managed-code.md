---
title: 'Instrukcje: Włączanie i wyłączanie pełnej analizy rozwiązania dla kodu zarządzanego | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
ms.assetid: 04315147-5792-47f0-8b5f-9ac8413c6a57
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fddc41d264f30f6de5a2f69b098865cf3d997147
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60044827"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Instrukcje: Włączanie i wyłączanie pełnej analizy rozwiązania dla kodu zarządzanego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UWAGA]
>  Ten temat dotyczy tylko programu Visual Studio 2015 Update 3 RC lub nowszego.  
  
 *Pełnej analizy rozwiązania* jest funkcją programu Visual Studio, która umożliwia wybranie, czy wyświetlać tylko w otwartych plików języka Visual C# lub Visual Basic w rozwiązaniu lub w otwartych i zamkniętych plikach języka Visual C# lub Visual Basic w rozwiązaniu, problemów z analizą kodu.  
  
 Możliwości zobaczyć wszystkie problemy we wszystkich plikach jest przydatne, może być rozprasza uwagę i nawet spowolnić działanie programu Visual Studio, jeśli rozwiązanie jest bardzo duży lub ma wiele plików.  Ogranicz liczbę problemów wyświetlane i poprawa wydajności programu Visual Studio, można wyłączyć pełnej analizy rozwiązania. Jeśli chcesz, można łatwo ponownie włączyć tę funkcję.  
  
#### <a name="to-toggle-full-solution-analysis"></a>Aby przełączyć pełnej analizy rozwiązania  
  
1. W menu głównym w programie Visual Studio wybierz **narzędzia** &#124; **opcje** do wyświetlania **opcje** okno dialogowe.  
  
2. W **opcje** okna dialogowego wybierz **edytora tekstów** &#124; **C#** lub **podstawowe** &#124; **zaawansowane**.  
  
3. Wybierz **Włączanie pełnej analizy rozwiązania** pole wyboru, aby włączyć pełnej analizy rozwiązania, lub wyczyść pole, aby je wyłączyć. Wybierz **OK** przycisk po wykonaniu tych czynności.  
  
     ![Zaznacz pole wyboru analizy pełne rozwiązanie. ](../code-quality/media/fsa-toolsoptions.png "FSA_ToolsOptions")  
  
## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Wyniki Włączanie i wyłączanie pełnej analizy rozwiązania  
 Na poniższym zrzucie ekranu widać wyników po włączeniu pełnej analizy rozwiązania. Wszystkie błędy i problemy dotyczące analizy kodu w *wszystkich* plików w rozwiązaniu pojawia się, niezależnie od tego, czy pliki są otwarte, czy nie.  
  
 ![Po włączeniu analizy pełne rozwiązanie. ](../code-quality/media/fsa-enabled.png "FSA_Enabled")  
  
 Poniższy zrzut ekranu przedstawia wyniki z tego samego rozwiązania po wyłączeniu pełnej analizy rozwiązania. Tylko błędy i problemy dotyczące analizy kodu w Otwórz rozwiązanie, które pliki są wyświetlane na liście błędów.  
  
 ![Pełnej analizy rozwiązania wyłączone. ](../code-quality/media/fsa-disabled.png "FSA_Disabled")  
  
## <a name="automatically-disabling-full-solution-analysis"></a>Automatycznie wyłączanie pełnej analizy rozwiązania  
 Jeśli program Visual Studio wykryje, że 200MB lub mniej pamięci systemowej, jest dostępnych, automatycznie wyłącza pełnej analizy rozwiązania (a także niektórych innych funkcji) Jeśli jest włączone. Jeśli ten problem wystąpi, zostanie wyświetlony alert informujący o tym. Przycisk umożliwia ponowne włączanie pełnej analizy rozwiązania, jeśli chcesz to zrobić.  
  
 ![Tekst alertu zawieszanie pełnej analizy rozwiązania](../code-quality/media/fsa-alert.png "FSA_Alert")  
  
## <a name="additional-details"></a>Dodatkowe szczegóły  
 Domyślnie pełnej analizy rozwiązania jest włączona dla języka Visual Basic i wyłączone dla języka Visual C#.  
  
 Visual Studio Update 3 RC zawiera aparat diagnostycznych v2 analizatora rozszerzonego kodu, który znacznie zmniejsza użycie pamięci i zmniejsza czas procesora CPU do bezczynności (%), nawet jeśli jest włączona pełnej analizy rozwiązania.
