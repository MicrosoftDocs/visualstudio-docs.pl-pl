---
title: Nieużywane wartości i parametry
description: Dowiedz się więcej o nieużywanych przypisaniach wartości, zmiennych i parametrach oraz sposobie ich wyświetlania w edytorze kodu w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/15/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: cd0b6e936f4478cb4b74a3f004e69d77dbad7fbc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960614"
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
