---
title: Struktury języka C++ w projektancie klas
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
ms.openlocfilehash: 2aa8014835df2b5b2bd3dc68e2aaf0b079e001e8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590687"
---
# <a name="c-structures-in-class-designer"></a>Struktury języka C++ w projektancie klas

**Projektant klas** obsługuje struktury języka C++, `struct`które są zadeklarowane za pomocą słowa kluczowego . Oto przykład:

```cpp
struct MyStructure
{
   char a;
   int i;
   long j;
};
```

Aby uzyskać więcej `struct` informacji na temat używania tego typu, zobacz [struct](/cpp/cpp/struct-cpp).

Kształt struktury C++ na diagramie klasy wygląda i działa jak kształt klasy, z tą różnicą, że etykieta odczytuje **Struct** i ma kwadratowe narożniki zamiast zaokrąglonych narożników.

|Element Code|Widok projektanta klas|
|------------------| - |
|`struct StructureName {};`|**Nazwa struktury**<br /><br /> Struct|

## <a name="see-also"></a>Zobacz też

- [Praca z kodem C++](working-with-visual-cpp-code.md)
- [Klasy i struktury](/cpp/cpp/classes-and-structs-cpp)
- [Struct](/cpp/cpp/struct-cpp)
