---
title: 'Instrukcje: Włączanie i wyłączanie pełnej analizy rozwiązania dla kodu zarządzanego | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
ms.assetid: 04315147-5792-47f0-8b5f-9ac8413c6a57
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 72b27bf9dcc1f0ee8a222ac701f2ffae4fc68614
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646279"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Instrukcje: Włączanie i wyłączanie pełnej analizy rozwiązania dla kodu zarządzanego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

KORYGUJĄC
> Ten temat dotyczy tylko programu Visual Studio 2015 Update 3 RC lub nowszego.

 *Pełna analiza rozwiązań* to funkcja programu Visual Studio, która umożliwia wybranie, czy problemy z analizą kodu są widoczne tylko w otwartych plikach Visual c# lub Visual Basic w rozwiązaniu, czy zarówno w otwartym, jak i zamkniętym pliku Visual c# lub Visual Basic w rozwiązaniu.

 Chociaż jest możliwe, że wszystkie problemy występujące we wszystkich plikach są przydatne, można rozpraszać uwagę i nawet spowalniać program Visual Studio, jeśli rozwiązanie jest bardzo duże lub ma wiele plików.  Aby ograniczyć liczbę wyświetlanych problemów i zwiększyć wydajność programu Visual Studio, można wyłączyć pełną analizę rozwiązania. Jeśli chcesz, możesz łatwo włączyć tę funkcję.

#### <a name="to-toggle-full-solution-analysis"></a>Aby przełączać pełną analizę rozwiązania

1. W menu głównym programu Visual Studio wybierz pozycję **narzędzia** &#124; **Opcje** , aby wyświetlić okno dialogowe **Opcje** .

2. W oknie dialogowym **Opcje** wybierz **Edytor tekstu** &#124; **C#** lub **Basic** &#124; **Advanced**.

3. Zaznacz pole wyboru **Włącz pełną analizę rozwiązań** , aby włączyć pełną analizę rozwiązania, lub wyczyść to pole, aby je wyłączyć. Po zakończeniu wybierz przycisk **OK** .

     ![Pole wyboru Włącz pełną analizę rozwiązań.](../code-quality/media/fsa-toolsoptions.png "FSA_ToolsOptions")

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Wyniki włączania i wyłączania pełnej analizy rozwiązania
 Na poniższym zrzucie ekranu można zobaczyć wyniki, gdy jest włączona Pełna analiza rozwiązania. Wszystkie błędy i problemy związane z analizą kodu we *wszystkich* plikach w rozwiązaniu są wyświetlane niezależnie od tego, czy pliki są otwarte, czy nie.

 ![Włączono pełną analizę rozwiązań.](../code-quality/media/fsa-enabled.png "FSA_Enabled")

 Poniższy zrzut ekranu przedstawia wyniki z tego samego rozwiązania po wyłączeniu pełnej analizy rozwiązania. W Lista błędów są wyświetlane tylko błędy i problemy z analizą kodu w otwartych plikach rozwiązania.

 ![Pełna analiza rozwiązania została wyłączona.](../code-quality/media/fsa-disabled.png "FSA_Disabled")

## <a name="automatically-disabling-full-solution-analysis"></a>Automatyczne wyłączanie pełnej analizy rozwiązania
 Jeśli program Visual Studio wykryje, że dostępna jest 200 MB lub mniejsza ilość pamięci systemowej, program automatycznie wyłącza pełną analizę rozwiązania (a także inne funkcje), jeśli jest włączona. W takim przypadku zostanie wyświetlony alert informujący o tym. Przycisk umożliwia ponowne włączenie pełnej analizy rozwiązania, jeśli chcesz to zrobić.

 ![Tekst alertu wstrzymywanie pełnej analizy rozwiązania](../code-quality/media/fsa-alert.png "FSA_Alert")

## <a name="additional-details"></a>Dodatkowe szczegóły
 Domyślnie Pełna analiza rozwiązań jest włączona dla Visual Basic i wyłączone dla języka Visual C#.

 Program Visual Studio Update 3 RC zawiera udoskonalony aparat diagnostyki analizatora kodu w wersji 2, który znacznie zmniejsza użycie pamięci i zmniejsza czas procesora CPU do bezczynności, nawet jeśli jest włączona Pełna analiza rozwiązania.
