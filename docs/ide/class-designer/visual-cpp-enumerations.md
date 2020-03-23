---
title: Wyliczenia języka C++ w projektancie klas
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114195"
---
# <a name="c-enumerations-in-class-designer"></a>Wyliczenia języka C++ w projektancie klas

**Projektant klas** obsługuje `enum` typy `enum class` języka C++ i o określonym zakresie. Oto przykład:

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

Kształt wyliczenia języka C++ na diagramie klasy wygląda i działa jak kształt struktury, z tą różnicą, że etykieta odczytuje klasę **Wyliczenia** lub **Wyliczenia**, jest różowa zamiast niebieska i ma kolorowe obramowanie po lewej i górnych marginesach. Zarówno kształty wyliczenia, jak i kształty konstrukcji mają kwadratowe narożniki.

Aby uzyskać więcej `enum` informacji na temat używania tego typu, zobacz [Wyliczenia](/cpp/cpp/enumerations-cpp).

## <a name="see-also"></a>Zobacz też

- [Praca z kodem C++](working-with-visual-cpp-code.md)
- [Wyliczenia](/cpp/cpp/enumerations-cpp)
