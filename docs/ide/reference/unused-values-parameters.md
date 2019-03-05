---
title: Nieużywanych wartości i parametry
ms.date: 02/15/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 1ea80887fff6dcb1afba80feb782b23d1e790579
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57325346"
---
# <a name="unused-expression-values-and-parameters"></a>Wyrażenie nieużywanych wartości i parametry

Ta Refaktoryzacja mają zastosowanie do:

- C#
- Visual Basic

**Co:** Powoduje zanikanie nieużywanych parametrów out i generuje ostrzeżenie dla wyrażenia nieużywanych wartości.

**Kiedy:** Masz parametrów lub wartości wyrażenia, które nigdy nie są używane.

**Dlaczego:** Czasami trudno stwierdzić, jeśli wartość lub parametr jest już używany. Wygaszanie te wartości lub ostrzegający, możesz uzyskać wizualną jaki kod, możesz usunąć.

## <a name="unused-expression-values-and-parameters-diagnostic"></a>Wyrażenie nieużywanych wartości i parametry diagnostyczne

1. Istnieją jakieś wartości wyrażenia parametr, który nie jest używany.
2. Nieużywany parametr pojawia się rozmytą się. Wartość wyrażenia nieużywane otrzyma ostrzeżenie.

  ![Nieużywany parametr](media/unused-parameter.png)
  ![nieużywanej wartości](media/unused-value.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Wskazówki dla deweloperów platformy .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
