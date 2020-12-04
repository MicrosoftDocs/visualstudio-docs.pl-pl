---
title: Nieużywane wartości i parametry
description: Dowiedz się więcej o nieużywanych przypisaniach wartości, zmiennych i parametrach oraz sposobie ich wyświetlania w edytorze kodu w programie Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 8768992ce3ef9f40ab0adba1724d43b32e5bde5c
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560710"
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

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Porady dla deweloperów platformy .NET](../csharp-developer-productivity.md)
