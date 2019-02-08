---
title: Wyliczenia Visual C++ w Projektancie klas
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: f31f153183d0cdd809bd9dde9187ade32b20ddd2
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55939856"
---
# <a name="visual-c-enumerations-in-class-designer"></a>Wyliczenia Visual C++ w w Projektancie klas

**Projektant klasy** obsługuje C++ `enum` i zakresami `enum class` typów. Poniżej znajduje się przykład:

```cpp
enum CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};

// or...
enum class CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};
```

Kształt wyliczenia C++ na diagramie klasy wygląda i działa jak kształt struktury, chyba że czyta etykietę **wyliczenia** lub **Enum class**, jest różowy, a nie niebieski i ma kolorowe obramowanie na lewym i górnym marginesy. Zarówno wyliczenia kształtów, jak i struktury mają ostre rogi.

Aby uzyskać więcej informacji o korzystaniu z `enum` typu, zobacz [wyliczenia](/cpp/cpp/enumerations-cpp).

## <a name="see-also"></a>Zobacz także

- [Praca z kodem Visual C++](working-with-visual-cpp-code.md)
- [Wyliczenia](/cpp/cpp/enumerations-cpp)