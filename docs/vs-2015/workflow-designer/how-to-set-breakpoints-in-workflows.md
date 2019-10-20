---
title: 'Instrukcje: ustawianie punktów przerwania w przepływach pracy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2d1bbb18a9015b52b3d65cb8f8fd02674693abc0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659140"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Instrukcje: ustawianie punktów przerwania w przepływach pracy
Korzystając z [!INCLUDE[wfd1](../includes/wfd1-md.md)], można ustawić punkty przerwania w graficznych przepływach pracy, jak w Visual Basic lub C# kodzie. Zgodnie z oczekiwaniami wykonywanie przepływu pracy zostaje zatrzymane w każdym ustawionym punkcie przerwania.

 Punkt przerwania ma trzy stany: *oczekujący*, *powiązany*i *błąd*. Gdy ustawisz punkt przerwania, jest on w stanie oczekiwania i jest reprezentowany przez pełną czerwoną ikonę. Po załadowaniu typu przepływu pracy środowisko uruchomieniowe zostanie powiązane. W przypadku określenia niepoprawnego formatu punktu przerwania, takiego jak Nieprawidłowa nazwa działania, pojawi się okno błędu. Punkt przerwania jest nadal dodawany do okna punktu przerwania, ale jest oznaczony małą "x".

> [!NOTE]
> Ustawianie punktów przerwania dla wywołanych przepływów pracy nie jest obsługiwane.
>
> [!WARNING]
> Upewnij się, że wybrano opcję **włącz tylko mój kod (tylko zarządzane)** z menu **Narzędzia**, **Opcje**, **debugowanie** , przed rozpoczęciem debugowania. Jeśli masz dwie sekwencje zagnieżdżone w innej sekwencji i ustawisz punkt przerwania w pierwszej sekwencji wewnętrznej, naciśnięcie klawisza **F11** nie spowoduje debugowania do drugiej sekwencji wewnętrznej, jeśli opcja <strong>Włącz tylko mój kod (tylko zarządzany)</strong>nie jest zaznaczona.
>
> [!WARNING]
> Punkty przerwania w przepływie pracy nie będą trafiać, jeśli pełna ścieżka do właściwości pliku XAML jest niedokładna. Pełna ścieżka do pliku XAML jest niedokładna po przeniesieniu projektu/rozwiązania do innego folderu lub do innej maszyny. Wybierz kombinację klawiszy Ctrl + S, aby zapisać i zaktualizować Właściwość pełnej ścieżki.

### <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>Aby ustawić punkt przerwania dla działania w widoku projektu

1. Wybierz działanie, które ma zostać przerwane przez debuger.

2. W menu **Debuguj** wybierz polecenie **Przełącz punkt przerwania**. Czerwona ikona pojawi się w lewej górnej krawędzi działania.

     Alternatywnie można również nacisnąć skrót **F9** po zaznaczeniu działania lub można kliknąć prawym przyciskiem myszy działanie i wybrać **punkt przerwania** , a następnie **wstawić punkt przerwania** z menu kontekstowego.

## <a name="see-also"></a>Zobacz też
 [Instrukcje: wywoływanie](../workflow-designer/how-to-invoke-the-workflow-debugger.md) [przepływów pracy debugowania debugera przepływu pracy z Projektant przepływu pracy](../workflow-designer/debugging-workflows-with-the-workflow-designer.md) [How to: Debug XAML with the Projektant przepływu pracy](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)