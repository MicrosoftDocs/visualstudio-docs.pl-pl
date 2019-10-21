---
title: Definicje typów Visual C++ w Projektancie klas
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 7bf886aedc27b6e702637b84bbe919971baec9e3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647584"
---
# <a name="visual-c-typedefs-in-class-designer"></a>Visual C++ Typedefs w Projektant klas

[Typedef](/cpp/cpp/aliases-and-typedefs-cpp#typedefs) — instrukcje Utwórz co najmniej jedną warstwę pośrednika między nazwą i jej typem podstawowym. **Projektant klas** obsługuje C++ typy typedef, które są zadeklarowane za pomocą słowa kluczowego `typedef`, na przykład:

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

W **Projektant klas** C++ element typedef ma kształt typu określonego w elemencie typedef. Jeśli źródło deklaruje `typedef class`, kształt ma zaokrąglone rogi i **klasę**etykiet. W przypadku `typedef struct` kształt ma prostokąty kwadratowe i **strukturę**etykiet.

Klasy i struktury mogą mieć zagnieżdżone elementy typedef zadeklarowane w obrębie tych elementów. W **Projektant klas**kształty klas i struktur mogą wyświetlać zagnieżdżone deklaracje typedef jako zagnieżdżone kształty.

W elementach typedef są obsługiwane polecenia **Pokaż jako skojarzenie** i **Pokaż jako kolekcje kolekcji** w menu rozwijanym prawym przyciskiem myszy (menu kontekstowe).

### <a name="class-typedef-example"></a>Przykład klasy typedef

```cpp
class B {};
typedef B MyB;
```

![C++Klasa typedef w Projektant klas](media/cpp-class-typedef.png)

### <a name="struct-typedef-example"></a>Przykład struktury typedef

```cpp
typedef struct mystructtag
{
    int   i;
    double f;
} mystruct;
```

![C++Struktura typedef w Projektant klas](media/cpp-struct-typedef.png)

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

- [Pracuj z kodem C++ wizualizacji](working-with-visual-cpp-code.md)
- [Definicje typów](/cpp/cpp/aliases-and-typedefs-cpp#typedefs)