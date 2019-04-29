---
title: Struktury Visual C++ w Projektancie klas
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: e9b8e81ee25e081a324a8520317fa57a1314ccd0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62975037"
---
# <a name="visual-c-structures-in-class-designer"></a>Struktury Visual C++ w w Projektancie klas

**Projektant klasy** obsługuje struktury, C++, które są zadeklarowane za pomocą słowa kluczowego `struct`. Poniżej znajduje się przykład:

```cpp
struct MyStructure
{
   char a;
   int i;
   long j;
};
```

Aby uzyskać więcej informacji o korzystaniu z `struct` typu, zobacz [struktury](/cpp/cpp/struct-cpp).

Kształt struktury języka C++ na diagramie klasy wygląda i działa jak kształt klasy, z tą różnicą, że czyta etykietę **struktury** i ma ostre rogi zamiast zaokrąglone rogi.

|Element Code|Widok projektanta klas|
|------------------| - |
|`struct StructureName {};`|**StructureName**<br /><br /> Struct|

## <a name="see-also"></a>Zobacz także

- [Praca z kodem Visual C++](working-with-visual-cpp-code.md)
- [Klasy i struktury](/cpp/cpp/classes-and-structs-cpp)
- [struct](/cpp/cpp/struct-cpp)