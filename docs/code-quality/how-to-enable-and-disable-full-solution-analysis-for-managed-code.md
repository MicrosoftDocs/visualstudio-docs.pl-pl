---
title: 'Instrukcje: Włączanie i wyłączanie pełnej analizy rozwiązania dla kodu zarządzanego'
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: dbd4cf06a5d51a668acc5c980e7e93a94f2992f2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816469"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Instrukcje: Włączanie i wyłączanie pełnej analizy rozwiązania dla kodu zarządzanego

*Pełnej analizy rozwiązania* jest funkcją programu Visual Studio, która umożliwia wyświetlenie tylko w elemencie wizualnym otwarte, problemów z analizą kodu C# lub plikach języka Visual Basic w rozwiązaniu lub w plikach kodu, które są zamknięte. Domyślnie jest pełnej analizy rozwiązania *włączone* dla języka Visual Basic i *wyłączone* wizualizacji C#.

Może być przydatne zobaczyć wszystkie problemy we wszystkich plikach, ale może też być rozprasza uwagę. Go spowalnia programu Visual Studio, jeśli rozwiązanie jest bardzo długa lub zawiera wiele plików. Ogranicz liczbę problemów wyświetlane i poprawa wydajności programu Visual Studio, można wyłączyć pełnej analizy rozwiązania. W razie potrzeby można łatwo ponownie włączyć tę funkcję.

## <a name="to-toggle-full-solution-analysis"></a>Aby przełączyć pełnej analizy rozwiązania

1. Aby otworzyć **opcje** okno dialogowe, na pasku menu w programie Visual Studio wybierz **narzędzia** > **opcje**.

1. W **opcje** okna dialogowego wybierz **edytora tekstów**  >  **C#** lub **podstawowe**  >  **Zaawansowane**.

1. Wybierz **Włączanie pełnej analizy rozwiązania** pole wyboru, aby włączyć pełnej analizy rozwiązania, lub wyczyść pole, aby je wyłączyć. Wybierz **OK** po zakończeniu.

    ![Zaznacz pole wyboru analizy pełne rozwiązanie.](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Wyniki Włączanie i wyłączanie pełnej analizy rozwiązania

Na poniższym zrzucie ekranu widać wyników po włączeniu pełnej analizy rozwiązania. Wszystkie błędy i problemy dotyczące analizy kodu w *wszystkich* plików w rozwiązaniu pojawia się, niezależnie od tego, czy pliki są otwarte, czy nie.

![Po włączeniu analizy pełne rozwiązanie.](../code-quality/media/fsa_enabled.png)

Poniższy zrzut ekranu przedstawia wyniki z tego samego rozwiązania po wyłączeniu pełnej analizy rozwiązania. Tylko błędy i problemy dotyczące analizy kodu w plikach otwartego rozwiązania są wyświetlane w **lista błędów**.

![Pełnej analizy rozwiązania wyłączone.](../code-quality/media/fsa_disabled.png)

## <a name="automatically-disable-full-solution-analysis"></a>Automatycznie wyłączanie pełnej analizy rozwiązania

Jeśli program Visual Studio wykryje, że 200 MB lub mniej pamięci systemowej, jest dostępnych, automatycznie wyłączany pełnej analizy rozwiązania (i niektórych innych funkcji) Jeśli jest włączone. Jeśli ten problem wystąpi, zostanie wyświetlony alert informujący o tym, że Visual Studio ma wyłączone niektóre funkcje. Przycisk służy do ponownego włączenia pełnej analizy rozwiązania, jeśli chcesz.

![Tekst alertu zawieszanie pełnej analizy rozwiązania](../code-quality/media/fsa_alert.png)