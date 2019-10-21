---
title: Struktury Visual C++ w Projektancie klas
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: da786e6f598b4b28aeb7758df41f54ea23c4185d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647595"
---
# <a name="visual-c-structures-in-class-designer"></a>Struktury C++ wizualizacji w Projektant klas

**Projektant klas** obsługuje C++ struktury, które są zadeklarowane za pomocą słowa kluczowego `struct`. Oto przykład:

```cpp
struct MyStructure
{
   char a;
   int i;
   long j;
};
```

Aby uzyskać więcej informacji o używaniu typu `struct`, zobacz [struct](/cpp/cpp/struct-cpp).

Kształt C++ struktury na diagramie klas wygląda i działa jak kształt klasy, z tą różnicą, że etykieta odczytuje **strukturę** i ma kwadratowe rogi zamiast zaokrąglonych rogów.

|Element Code|Widok Projektant klas|
|------------------| - |
|`struct StructureName {};`|**StructureName**<br /><br /> Struct|

## <a name="see-also"></a>Zobacz także

- [Praca z kodem Visual C++](working-with-visual-cpp-code.md)
- [Klasy i struktury](/cpp/cpp/classes-and-structs-cpp)
- [struct](/cpp/cpp/struct-cpp)