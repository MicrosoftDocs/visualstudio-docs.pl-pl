---
title: C++Wyliczenia w Projektant klas
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
ms.openlocfilehash: a514d5eb4b7f79e2fd193c79de670b6dd9c14cb5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747993"
---
# <a name="c-enumerations-in-class-designer"></a>C++wyliczenia w Projektant klas

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

- [Praca z C++ kodem](working-with-visual-cpp-code.md)
- [Wyliczenia](/cpp/cpp/enumerations-cpp)