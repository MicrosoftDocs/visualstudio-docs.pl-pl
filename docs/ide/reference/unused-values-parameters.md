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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531874"
---
# <a name="unused-value-assignments-variables-and-parameters"></a>Nieużywane przypisania wartości, zmienne i parametry

Ten refaktoryzator ma zastosowanie do:

- C#
- Visual Basic

**Co:** Zanika nieużywane parametry i generuje ostrzeżenie dla nieużywanych wartości wyrażeń. Kompilator wykonuje również analizę przepływu, aby znaleźć wszystkie nieużywane przypisania wartości. Nieużywane przypisania wartości zanikają, a żarówka pojawi się z [szybką akcją,](../quick-actions.md) aby usunąć nadmiarowe przypisanie. Nieużywane zmienne o nieznanych wartościach pokazują sugestię [szybkiej akcji,](../quick-actions.md) aby zamiast tego użyć [odrzutów.](/dotnet/csharp/discards) (Odrzuty są tymczasowe, fikcyjne zmienne, które są celowo nieużywane w kodzie aplikacji. Mogą one zmniejszyć alokację pamięci i ułatwić odczytanie kodu.)

**Kiedy:** Masz przypisania wartości, parametry lub wartości wyrażeń, które nigdy nie są używane.

**Dlaczego?** Czasami trudno jest stwierdzić, czy przypisanie wartości, zmienna lub parametr nie jest już używany. Zanikanie tych wartości lub generowanie ostrzeżenia, otrzymasz wizualną wskazówkę, jaki kod można usunąć.

## <a name="unused-expression-values-and-parameters-diagnostic"></a>Nieużywane wartości i parametry diagnostyczne

1. Mieć dowolne przypisanie wartości, zmienną lub parametr, który nie jest używany.
2. Nieużywane przypisanie wartości lub parametr wydaje się wyblakłe. Nieużywane wyrażenie wartość generuje ostrzeżenie.

  ![Nieużywane](media/unused-parameter.png)
  ![parametry Nieużywane](media/unused-value.png)
  ![wartości](media/unused-value-assignment.png)
  ![Nieużywane przypisanie wartości Nieużywane odrzucić wartość](media/unused-value-discard.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Wskazówki dla deweloperów platformy .NET](../csharp-developer-productivity.md)
