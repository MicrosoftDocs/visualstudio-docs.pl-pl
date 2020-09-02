---
title: Nieużywane wartości i parametry
ms.date: 02/15/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ce2b0f1e0c0db45c478c3917306683b314da0564
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65531874"
---
# <a name="unused-value-assignments-variables-and-parameters"></a>Nieużywane przypisania wartości, zmienne i parametry

To Refaktoryzacja dotyczy:

- C#
- Visual Basic

**Co:** Stopniowo rozjaśnia nieużywane parametry i generuje ostrzeżenie dla nieużywanych wartości wyrażeń. Kompilator wykonuje również analizę przepływu, aby znaleźć wszystkie nieużywane przypisania wartości. Nieużywane przypisania wartości zmniejszają się, a żarówka jest wyświetlana z [szybką akcją](../quick-actions.md) usuwania nadmiarowego przypisania. Nieużywane zmienne z nieznanymi wartościami pokazują [szybką](../quick-actions.md) sugestię akcji umożliwiającą korzystanie z [odrzutów](/dotnet/csharp/discards) . (Odrzuty są tymczasowymi, fikcyjnymi, które są celowo nieużywane w kodzie aplikacji. Mogą zmniejszyć alokację pamięci i ułatwić odczytywanie kodu.

**Kiedy:** Masz przydziały wartości, parametry lub wartości wyrażeń, które nigdy nie są używane.

**Dlaczego:** Czasami trudno jest stwierdzić, czy nie jest już używane przypisanie wartości, zmienna lub parametr. W wyniku zanikania tych wartości lub wygenerowania ostrzeżenia można uzyskać wizualny wskaźnik kodu, który można usunąć.

## <a name="unused-expression-values-and-parameters-diagnostic"></a>Diagnostyka nieużywanych wartości i parametrów wyrażeń

1. Mieć dowolne przypisanie wartości, zmienną lub parametr, który nie jest używany.
2. Nieużywane przypisanie wartości lub parametr pojawia się. Nieużywana wartość wyrażenia generuje ostrzeżenie.

  ![Nieużywana wartość nieużywanej wartości ](media/unused-parameter.png)
   ![ ](media/unused-value.png)
   ![ przypisywania wartości ](media/unused-value-assignment.png)
   ![ niewykorzystanej wartości](media/unused-value-discard.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Porady dla deweloperów platformy .NET](../csharp-developer-productivity.md)
