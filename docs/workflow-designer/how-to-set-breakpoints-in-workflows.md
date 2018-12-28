---
title: 'Projektant przepływu pracy — jak: Ustawianie punktów przerwania w przepływach pracy'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 96db38e8a69d0b8b9ee042420647851aa1fbf0c0
ms.sourcegitcommit: 935e341a02dba1c2aa3b6e89469388aa6e626f7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53684252"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Instrukcje: Ustawianie punktów przerwania w przepływach pracy

Korzystając z projektanta przepływów pracy, można ustawić punktów przerwania na graficzny przepływy pracy tak jak w języku Visual Basic lub C# kodu. Zgodnie z oczekiwaniami, zatrzyma wykonywanie przepływu pracy, w każdym punkcie przerwania, który został ustawiony.

Punkt przerwania ma trzy stany: *Oczekujące*, *powiązany*, i *błąd*. Po ustawieniu punktu przerwania jest oczekujące i jest reprezentowana przez stałe czerwoną ikonę. Po załadowaniu szablonu przepływu pracy środowiska uruchomieniowego staje się powiązany. Jeśli określisz ma niewłaściwy format dla punktu przerwania, takich jak nazwa działania, który nie jest prawidłowy, pojawi się okno błędu. Punkt przerwania nadal jest dodawany do okna punkt przerwania, ale jest oznaczony za pomocą małych "x".

> [!NOTE]
> Ustawianie punktów przerwania w przepływach pracy, wywoływane jest nieobsługiwana.

> [!NOTE]
> Upewnij się, że wybrano opcję **Włącz tylko mój kod (tylko zarządzany)** z **narzędzia** > **opcje** > **debugowania**  menu przed debugowania. Jeśli nie została wybrana opcja i masz dwie sekwencje zagnieżdżone w obrębie innej sekwencji, a następnie ustaw punkt przerwania w pierwszej sekwencji wewnętrzny, naciskając klawisz **F11** nie zdebugować drugiej sekwencji wewnętrznego.

> [!NOTE]
> Punkty przerwania w przepływie pracy nie są osiągane, jeśli Pełna ścieżka do właściwości pliku XAML nie jest dokładne. Pełna ścieżka do pliku XAML nie jest dokładne po przeniesieniu projektu lub rozwiązania do innego folderu lub innego komputera. Wybierz **Ctrl**+**S** Aby zapisać i zaktualizować właściwość pełną ścieżkę.

## <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>Aby ustawić punkt przerwania w działaniu w widoku projektu

1. Wybierz czynność chcesz, aby debuger przerywał działanie w przypadku.

2. Na **debugowania** menu, wybierz opcję **Przełącz punkt przerwania**. Czerwona ikona pojawi się do górnej krawędzi lewej działania.

   Alternatywnie, możesz nacisnąć przycisk **F9** po wybranie działania lub możesz można kliknij działanie prawym przyciskiem myszy i wybrać **punktu przerwania** > **Wstaw punkt przerwania** z menu kontekstowego.

## <a name="see-also"></a>Zobacz także

- [Debugowanie przepływów pracy za pomocą Projektanta przepływu pracy](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
- [Instrukcje: Debugowanie XAML za pomocą projektanta przepływu pracy](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)