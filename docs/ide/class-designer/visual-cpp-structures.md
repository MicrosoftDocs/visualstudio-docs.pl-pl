---
title: Struktury C++ w Projektant klas
description: Dowiedz się, w jaki sposób Projektant klas obsługuje struktury C++ zadeklarowane za pomocą struktury słowa kluczowego.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: d22ff6be694de69f105897821aba1b587955f748
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903432"
---
# <a name="c-structures-in-class-designer"></a>Struktury C++ w Projektant klas

**Projektant klas** obsługuje struktury języka C++, które są zadeklarowane za pomocą słowa kluczowego `struct` . Oto przykład:

```cpp
struct MyStructure
{
   char a;
   int i;
   long j;
};
```

Aby uzyskać więcej informacji na temat korzystania z `struct` typu, zobacz [Struktura](/cpp/cpp/struct-cpp).

Kształt struktury C++ na diagramie klas wygląda i działa jak kształt klasy, z tą różnicą, że etykieta odczytuje **strukturę** i ma kwadratowe rogi zamiast zaokrąglonych rogów.

|Element Code|Widok Projektant klas|
|------------------| - |
|`struct StructureName {};`|**StructureName**<br /><br /> Struktura|

## <a name="see-also"></a>Zobacz także

- [Praca z kodem C++](working-with-visual-cpp-code.md)
- [Klasy i struktury](/cpp/cpp/classes-and-structs-cpp)
- [konstrukcja](/cpp/cpp/struct-cpp)
