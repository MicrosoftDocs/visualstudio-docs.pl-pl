---
title: 'Projektant przepływu pracy — instrukcje: ustawianie punktów przerwania w przepływach pracy'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b6d2806a8757f00924d51c76aea82cfc8c6a5673
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650328"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Instrukcje: ustawianie punktów przerwania w przepływach pracy

Korzystając z Projektant przepływu pracy, można ustawić punkty przerwania w graficznych przepływach pracy, jak w Visual Basic lub C# kodzie. Zgodnie z oczekiwaniami wykonywanie przepływu pracy zostaje zatrzymane w każdym ustawionym punkcie przerwania.

Punkt przerwania ma trzy stany: *oczekujący*, *powiązany*i *błąd*. Gdy ustawisz punkt przerwania, jest on w stanie oczekiwania i jest reprezentowany przez pełną czerwoną ikonę. Po załadowaniu typu przepływu pracy środowisko uruchomieniowe zostanie powiązane. W przypadku określenia niepoprawnego formatu punktu przerwania, takiego jak Nieprawidłowa nazwa działania, pojawi się okno błędu. Punkt przerwania jest nadal dodawany do okna punktu przerwania, ale jest oznaczony małą "x".

> [!NOTE]
> Ustawianie punktów przerwania dla wywołanych przepływów pracy nie jest obsługiwane.

> [!NOTE]
> Upewnij się, że wybrano **opcję włącz tylko mój kod (tylko zarządzane)** z poziomu**opcji** **Narzędzia**  >   > **debugowanie** przed rozpoczęciem debugowania. Jeśli opcja nie jest zaznaczona i masz dwie sekwencje zagnieżdżone w innej sekwencji i ustawisz punkt przerwania w pierwszej sekwencji wewnętrznej, naciśnięcie klawisza **F11** nie debuguje do drugiej sekwencji wewnętrznej.

> [!NOTE]
> Punkty przerwania w przepływie pracy nie są trafień, jeśli pełna ścieżka do właściwości pliku XAML jest niedokładna. Pełna ścieżka do pliku XAML jest niedokładna po przeniesieniu projektu lub rozwiązania do innego folderu lub do innej maszyny. Wybierz pozycję **Ctrl** +**S** , aby zapisać i zaktualizować Właściwość pełna ścieżka.

## <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>Aby ustawić punkt przerwania dla działania w widoku projektu

1. Wybierz działanie, które ma zostać przerwane przez debuger.

2. W menu **Debuguj** wybierz polecenie **Przełącz punkt przerwania**. Czerwona ikona pojawi się w lewej górnej krawędzi działania.

   Alternatywnie można nacisnąć klawisz **F9** po zaznaczeniu działania lub można kliknąć prawym przyciskiem myszy działanie i wybrać pozycję **punkt przerwania**  > **Wstaw punkt przerwania** w menu po kliknięciu prawym przyciskiem myszy.

## <a name="see-also"></a>Zobacz także

- [Debugowanie przepływów pracy za pomocą Projektanta przepływu pracy](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
- [Instrukcje: Debugowanie kodu XAML za pomocą Projektanta przepływu pracy](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)