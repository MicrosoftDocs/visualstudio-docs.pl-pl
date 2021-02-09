---
title: Wyliczenia C++ w Projektant klas
description: Dowiedz się, jak Projektant klas obsługuje typy wyliczeniowe C++ i klasy wyliczeniowe w zakresie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 88675bb7593a901805cc156bbb36a2f49d69ec29
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852560"
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
