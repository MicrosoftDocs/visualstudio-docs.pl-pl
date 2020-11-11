---
title: 'Projektant przepływu pracy — instrukcje: ustawianie punktów przerwania w przepływach pracy'
description: Dowiedz się, jak za pomocą Projektant przepływu pracy ustawić punkty przerwania w graficznych przepływach pracy, tak jak w przypadku kodu Visual Basic lub C#.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2a8900d9df2679c6eb353336d8e7d96dd5ce365
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437882"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Instrukcje: ustawianie punktów przerwania w przepływach pracy

Korzystając z Projektant przepływu pracy, można ustawić punkty przerwania w graficznym przepływie pracy, tak jak w przypadku kodu Visual Basic lub C#. Zgodnie z oczekiwaniami wykonywanie przepływu pracy zostaje zatrzymane w każdym ustawionym punkcie przerwania.

Punkt przerwania ma trzy stany: *oczekujący* , *powiązany* i *błąd*. Gdy ustawisz punkt przerwania, jest on w stanie oczekiwania i jest reprezentowany przez pełną czerwoną ikonę. Po załadowaniu typu przepływu pracy środowisko uruchomieniowe zostanie powiązane. W przypadku określenia niepoprawnego formatu punktu przerwania, takiego jak Nieprawidłowa nazwa działania, pojawi się okno błędu. Punkt przerwania jest nadal dodawany do okna punktu przerwania, ale jest oznaczony małą "x".

> [!NOTE]
> Ustawianie punktów przerwania dla wywołanych przepływów pracy nie jest obsługiwane.

> [!NOTE]
> Upewnij się, że wybrano opcję **Włącz tylko mój kod (tylko zarządzane)** z **Tools**  >  menu **Opcje** narzędzi  >  **debugowanie** przed rozpoczęciem debugowania. Jeśli opcja nie jest zaznaczona i masz dwie sekwencje zagnieżdżone w innej sekwencji i ustawisz punkt przerwania w pierwszej sekwencji wewnętrznej, naciśnięcie klawisza **F11** nie debuguje do drugiej sekwencji wewnętrznej.

> [!NOTE]
> Punkty przerwania w przepływie pracy nie są trafień, jeśli pełna ścieżka do właściwości pliku XAML jest niedokładna. Pełna ścieżka do pliku XAML jest niedokładna po przeniesieniu projektu lub rozwiązania do innego folderu lub do innej maszyny. Wybierz **Ctrl** + **S** , aby zapisać i zaktualizować Właściwość pełna ścieżka.

## <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>Aby ustawić punkt przerwania dla działania w widoku projektu

1. Wybierz działanie, które ma zostać przerwane przez debuger.

2. W menu **Debuguj** wybierz polecenie **Przełącz punkt przerwania**. Czerwona ikona pojawi się w lewej górnej krawędzi działania.

   Alternatywnie można nacisnąć klawisz **F9** po zaznaczeniu działania lub można kliknąć prawym przyciskiem myszy działanie i wybrać **punkt przerwania**  >  **Wstaw punkt przerwania** w menu po kliknięciu prawym przyciskiem myszy.

## <a name="see-also"></a>Zobacz też

- [Debugowanie przepływów pracy za pomocą Projektanta przepływu pracy](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
- [Instrukcje: Debugowanie kodu XAML za pomocą Projektanta przepływu pracy](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)
