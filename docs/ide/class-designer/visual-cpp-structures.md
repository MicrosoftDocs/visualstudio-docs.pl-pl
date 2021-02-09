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
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 3ca35f9e1c3c1340330ddbbe36ede540fe1e547d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879959"
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

## <a name="see-also"></a>Zobacz też

- [Praca z kodem C++](working-with-visual-cpp-code.md)
- [Klasy i struktury](/cpp/cpp/classes-and-structs-cpp)
- [konstrukcja](/cpp/cpp/struct-cpp)
