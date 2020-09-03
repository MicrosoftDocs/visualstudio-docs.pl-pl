---
title: Wyliczenia C++ w Projektant klas
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: ee56850c05e4b06ea4325ec238e56e99b38978d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "76114195"
---
# <a name="c-enumerations-in-class-designer"></a>Wyliczenia C++ w Projektant klas

**Projektant klas** obsługuje C++ `enum` i typy z zakresem `enum class` . Oto przykład:

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

Kształt wyliczenia języka C++ na diagramie klas wygląda i działa jak kształt struktury, z tą różnicą, że etykieta odczytuje klasę **enum** lub **enum**, jest kolorem różowym zamiast niebieskim i ma kolorowe obramowanie na lewym i górnym marginesie. Zarówno kształty wyliczenia, jak i kształty struktury mają narożniki kwadratowe.

Aby uzyskać więcej informacji na temat korzystania z `enum` typu, zobacz [wyliczenia](/cpp/cpp/enumerations-cpp).

## <a name="see-also"></a>Zobacz też

- [Praca z kodem C++](working-with-visual-cpp-code.md)
- [Wyliczenia](/cpp/cpp/enumerations-cpp)
