---
title: Włącz & wyłącz pełną analizę rozwiązania dla kodu zarządzanego
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
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79428272"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Jak: Włącz i wyłącz pełną analizę rozwiązania dla kodu zarządzanego

*Pełna analiza rozwiązania* oznacza, że analiza kodu sprawdza wszystkie pliki języka C# lub Visual Basic w rozwiązaniu, niezależnie od tego, czy są one otwarte w edytorze, czy nie. Domyślnie pełna analiza rozwiązania jest *włączona* dla języka Visual Basic i *wyłączona* dla języka C#.

Może być przydatne, aby zobaczyć wszystkie problemy we wszystkich plikach, ale może być również rozpraszać. Spowalnia program Visual Studio w dół, jeśli rozwiązanie jest bardzo duży lub ma wiele plików. Aby ograniczyć liczbę wyświetlanych problemów i poprawić wydajność programu Visual Studio, można wyłączyć pełną analizę rozwiązania. W razie potrzeby można łatwo ponownie wywrzeć tę funkcję.

Na poniższej ilustracji jest włączona pełna analiza rozwiązania. Problemy z analizą kompilatora i kodu we wszystkich plikach w rozwiązaniu są wyświetlane, nawet jeśli nie są otwarte.

![Pełna analiza rozwiązań włączona.](../code-quality/media/fsa_enabled.png)

Na poniższej ilustracji przedstawiono wyniki z tego samego rozwiązania po wyłączeniu pełnej analizy rozwiązania. Na liście błędów pojawiają się tylko błędy kompilatora i analizy kodu w otwartych plikach rozwiązań.

![Pełna analiza rozwiązań wyłączona.](../code-quality/media/fsa_disabled.png)

## <a name="toggle-full-solution-analysis"></a>Przełączanie pełnej analizy rozwiązania

1. Aby otworzyć okno dialogowe **Opcje,** na pasku menu w programie Visual Studio wybierz pozycję**Opcje** **narzędzi** > .

1. W oknie dialogowym **Opcje** wybierz pozycję **Edytor** > tekstu**C#** lub **Basic** > **Advanced**.

1. Zaznacz pole wyboru **Włącz pełną analizę rozwiązania,** aby włączyć pełną analizę rozwiązania, lub wyczyść to pole, aby je wyłączyć. Po zakończeniu wybierz przycisk **OK.**

   ![Włącz pełną analizę rozwiązania pole wyboru.](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="automatically-disable-full-solution-analysis"></a>Automatyczne wyłączanie pełnej analizy rozwiązania

Jeśli program Visual Studio wykryje, że 200 MB lub mniej pamięci systemowej jest dostępna, automatycznie wyłącza pełną analizę rozwiązania (i niektóre inne funkcje), jeśli jest włączona. W takim przypadku pojawi się alert informujący, że program Visual Studio wyłączył niektóre funkcje. Przycisk umożliwia ponowne przynajemowanie pełnej analizy rozwiązania, jeśli chcesz.

![Tekst alertu zawieszający pełną analizę rozwiązania](../code-quality/media/fsa_alert.png)
