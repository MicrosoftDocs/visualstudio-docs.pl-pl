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
ms.openlocfilehash: afcf85fff188853890b86cf7deb13b2457f5e0b8
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58157701"
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
