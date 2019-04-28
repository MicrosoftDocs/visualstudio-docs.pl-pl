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
ms.openlocfilehash: 2d0875f9a298af24575cc05008713cbb6c3e2ead
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62789754"
---
# <a name="unused-value-assignments-variables-and-parameters"></a>Nieużywane przypisania wartości, zmienne i parametry

Ta Refaktoryzacja mają zastosowanie do:

- C#
- Visual Basic

**Co:** Powoduje zanikanie nieużywanych parametrów out i generuje ostrzeżenie dla wyrażenia nieużywanych wartości. Kompilator wykonuje też analizę przepływu, aby znaleźć wszystkich przypisań nieużywanej wartości. Nieużywane zanikanie wartości przypisania i żarówka pojawia się za pomocą [szybka akcja](../quick-actions.md) można usunąć nadmiarowe przypisania. Nieużywane zmienne przy użyciu wartości nieznany Pokaż [szybka akcja](../quick-actions.md) sugestiami użycia [odrzuca](/dotnet/csharp/discards) zamiast tego. (Odrzucenia są tymczasowego, fikcyjnego zmiennych, które są celowo nieużywane w kodzie aplikacji. Mogą zmniejszyć alokacji pamięci i sprawić, że kod jest łatwiejsza do odczytania.)

**Kiedy:** Masz przypisań wartości, parametry i wartości wyrażenia, które nigdy nie są używane.

**Dlaczego:** Czasami trudno stwierdzić, jeśli przypisanie wartości, zmienna lub parametr jest już używany. Wygaszanie te wartości lub zostanie wygenerowane ostrzeżenie, możesz uzyskać wizualną jaki kod, możesz usunąć.

## <a name="unused-expression-values-and-parameters-diagnostic"></a>Wyrażenie nieużywanych wartości i parametry diagnostyczne

1. Mieć żadnych przypisanie wartości, zmienna lub parametr, który nie jest używany.
2. Przypisanie nieużywanej wartości lub parametr pojawia się rozmytą się. Wartość wyrażenia nieużywane generuje ostrzeżenie.

  ![Nieużywany parametr](media/unused-parameter.png)
  ![nieużywanej wartości](media/unused-value.png)
  ![przypisania nieużywanej wartości](media/unused-value-assignment.png)
  ![odrzucenia nieużywanej wartości](media/unused-value-discard.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Wskazówki dla deweloperów platformy .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
