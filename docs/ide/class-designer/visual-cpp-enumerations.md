---
title: Wyliczenia Visual C++ w Projektancie klas
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: b5df17176839dccf0fbe0c42f164bde6b3e39f56
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72631126"
---
# <a name="visual-c-enumerations-in-class-designer"></a>Wyliczenia C++ wizualne w Projektant klas

**Projektant klas** obsługuje C++ typy `enum` i `enum class` z zakresem. Oto przykład:

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

Kształt C++ wyliczenia na diagramie klas wygląda i działa jak kształt struktury, z tą różnicą, że etykieta odczytuje klasę **enum** lub **enum**, jest kolorem różowym, a nie niebieską i ma kolorowe obramowanie na lewym i górnym marginesie. Zarówno kształty wyliczenia, jak i kształty struktury mają narożniki kwadratowe.

Aby uzyskać więcej informacji o używaniu typu `enum`, zobacz [wyliczenia](/cpp/cpp/enumerations-cpp).

## <a name="see-also"></a>Zobacz także

- [Praca z kodem Visual C++](working-with-visual-cpp-code.md)
- [Wyliczenia](/cpp/cpp/enumerations-cpp)