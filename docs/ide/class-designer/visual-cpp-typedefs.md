---
title: Definicje typów C++ w Projektant klas
description: Dowiedz się, jak Projektant klas obsługuje typy języka C++ typedef zadeklarowane za pomocą słowa kluczowego typedef.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: f95b948d4ffc70d225dd4a8b2bb2debe111c967e
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903445"
---
# <a name="c-typedefs-in-class-designer"></a>Definicje typów C++ w Projektant klas

[Typedef](/cpp/cpp/aliases-and-typedefs-cpp#typedefs) — instrukcje Utwórz co najmniej jedną warstwę pośrednika między nazwą i jej typem podstawowym. **Projektant klas** obsługuje typy C++ typedef, które są zadeklarowane za pomocą słowa kluczowego `typedef` , na przykład:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
} COORD;
```

Następnie można użyć tego typu, aby zadeklarować wystąpienie:

`COORD OriginPoint;`

## <a name="class-and-struct-shapes"></a>Kształty klas i struktur

W **Projektant klas**, element typedef języka C++ ma kształt typu określonego w elemencie typedef. Jeśli źródło deklaruje `typedef class` , kształt ma zaokrąglone rogi i **klasę** etykiet. Dla `typedef struct` , kształt ma narożniki kwadratowe i **strukturę** etykiet.

Klasy i struktury mogą mieć zagnieżdżone elementy typedef zadeklarowane w obrębie tych elementów. W **Projektant klas** kształty klas i struktur mogą wyświetlać zagnieżdżone deklaracje typedef jako zagnieżdżone kształty.

W elementach typedef są obsługiwane polecenia **Pokaż jako skojarzenie** i **Pokaż jako kolekcje kolekcji** w menu rozwijanym prawym przyciskiem myszy (menu kontekstowe).

### <a name="class-typedef-example"></a>Przykład klasy typedef

```cpp
class B {};
typedef B MyB;
```

![C++ Class typedef w Projektant klas](media/cpp-class-typedef.png)

### <a name="struct-typedef-example"></a>Przykład struktury typedef

```cpp
typedef struct mystructtag
{
    int   i;
    double f;
} mystruct;
```

![C++ struct typedef w Projektant klas](media/cpp-struct-typedef.png)

## <a name="unnamed-typedefs"></a>Nienazwane definicje typów

Chociaż można zadeklarować element typedef bez nazwy, **Projektant klas** nie używa nazwy tagu, którą określisz. **Projektant klas** używa nazwy wygenerowanej **Widok klasy** . Na przykład następująca deklaracja jest prawidłowa, ale występuje w **Widok klasy** i **Projektant klas** jako obiekt o nazwie **__unnamed**:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
};
```

> [!NOTE]
> W **Projektant klas** nie są wyświetlane definicje typów, których typ źródłowy jest wskaźnikiem funkcji.

## <a name="see-also"></a>Zobacz także

- [Współpraca z kodem C++](working-with-visual-cpp-code.md)
- [Definicje typów](/cpp/cpp/aliases-and-typedefs-cpp#typedefs)
