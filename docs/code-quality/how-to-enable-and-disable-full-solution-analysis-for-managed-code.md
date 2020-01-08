---
title: Włącz & Wyłącz pełną analizę rozwiązania dla kodu zarządzanego
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d699dd74315cfc36820c1cdb4120543e0290b1a1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587514"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Instrukcje: Włączanie i wyłączanie pełnej analizy rozwiązania dla kodu zarządzanego

*Pełna analiza rozwiązań* oznacza, że analiza kodu analizuje wszystkie pliki C# lub Visual Basic w rozwiązaniu, niezależnie od tego, czy są otwarte w edytorze, czy nie. Domyślnie Pełna analiza rozwiązań jest *włączona* dla Visual Basic i *wyłączone* dla programu C#.

Może być przydatne, aby zobaczyć wszystkie problemy we wszystkich plikach, ale może również rozpraszać uwagę. Spowalnia program Visual Studio, jeśli rozwiązanie jest bardzo duże lub ma wiele plików. Aby ograniczyć liczbę wyświetlanych problemów i zwiększyć wydajność programu Visual Studio, można wyłączyć pełną analizę rozwiązania. W razie potrzeby można łatwo włączyć tę funkcję.

Na poniższej ilustracji jest włączona Pełna analiza rozwiązania. Problemy kompilatora i analizy kodu we wszystkich plikach w rozwiązaniu są wyświetlane, nawet jeśli nie są otwarte.

![Włączono pełną analizę rozwiązań.](../code-quality/media/fsa_enabled.png)

Na poniższej ilustracji przedstawiono wyniki z tego samego rozwiązania po wyłączeniu pełnej analizy rozwiązania. W Lista błędów są wyświetlane tylko błędy kompilatora i problemy z analizą kodu w otwartych plikach rozwiązania.

![Pełna analiza rozwiązania została wyłączona.](../code-quality/media/fsa_disabled.png)

## <a name="toggle-full-solution-analysis"></a>Przełącz pełną analizę rozwiązania

1. Aby otworzyć okno dialogowe **Opcje** , na pasku menu w programie Visual Studio wybierz pozycję **Narzędzia** > **Opcje**.

1. W oknie dialogowym **Opcje** wybierz **Edytor tekstu** > **C#** lub **Basic** > **Advanced**.

1. Zaznacz pole wyboru **Włącz pełną analizę rozwiązań** , aby włączyć pełną analizę rozwiązania, lub wyczyść to pole, aby je wyłączyć. Po zakończeniu wybierz **przycisk OK** .

   ![Pole wyboru Włącz pełną analizę rozwiązań.](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="automatically-disable-full-solution-analysis"></a>Automatycznie Wyłącz pełną analizę rozwiązania

Jeśli program Visual Studio wykryje, że dostępna jest 200 MB lub mniej pamięci systemowej, program automatycznie wyłączy pełną analizę rozwiązań (i inne funkcje), jeśli jest włączona. W takim przypadku zostanie wyświetlony alert informujący o tym, że program Visual Studio wyłączył niektóre funkcje. Przycisk umożliwia ponownie włączyć pełną analizę rozwiązania, jeśli chcesz.

![Tekst alertu zawieszanie pełnej analizy rozwiązania](../code-quality/media/fsa_alert.png)
