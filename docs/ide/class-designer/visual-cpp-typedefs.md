---
title: Definicje c++ w projektancie klas
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
ms.openlocfilehash: 4c57382809b7730df2d7c674c24902d70ccab647
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590699"
---
# <a name="c-typedefs-in-class-designer"></a>Definicje c++ w projektancie klas

[Instrukcje typedef](/cpp/cpp/aliases-and-typedefs-cpp#typedefs) tworzą jedną lub więcej warstw pośrednich między nazwą a jej typem bazowym. **Projektant klas** obsługuje typy typedef języka C++, które są zadeklarowane za pomocą słowa kluczowego `typedef`, na przykład:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
} COORD;
```

Następnie można użyć tego typu do zadeklarowania wystąpienia:

`COORD OriginPoint;`

## <a name="class-and-struct-shapes"></a>Kształty klas i struktur

W **projektancie klas**, C++ typedef ma kształt typu określonego w typedef. Jeśli źródło `typedef class`deklaruje, kształt ma zaokrąglone narożniki i etykietę **Class**. Dla `typedef struct`, kształt ma kwadratowe narożniki i etykietę **Struct**.

Klasy i struktury mogą mieć zagnieżdżone typedefs zadeklarowane w nich. W **Projektancie klas**kształty klas i struktur mogą wyświetlać zagnieżdżone deklaracje typedef jako kształty zagnieżdżone.

Kształty Typedef obsługują polecenia **Pokaż jako skojarzenie** i **Pokaż jako skojarzenie kolekcji** w menu po kliknięciu prawym przyciskiem myszy (menu kontekstowe).

### <a name="class-typedef-example"></a>Przykład class typedef

```cpp
class B {};
typedef B MyB;
```

![Typdef klasy C++ w projektancie klas](media/cpp-class-typedef.png)

### <a name="struct-typedef-example"></a>Przykład strumyk typu def

```cpp
typedef struct mystructtag
{
    int   i;
    double f;
} mystruct;
```

![C++ struct typedef w projektancie klas](media/cpp-struct-typedef.png)

## <a name="unnamed-typedefs"></a>Nienazwane definicje typów

Chociaż można zadeklarować typedef bez nazwy, **Projektant klas** nie używa nazwy znacznika, który określisz. **Projektant klas** używa nazwy generowanej przez **widok klasy.** Na przykład następująca deklaracja jest prawidłowa, ale pojawia się w **widoku klasy** i **projektancie klas** jako obiekt o nazwie **__unnamed:**

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
};
```

> [!NOTE]
> **Projektant klasy** nie wyświetla typedefs, którego typem źródłem jest wskaźnik funkcji.

## <a name="see-also"></a>Zobacz też

- [Praca z kodem języka C++](working-with-visual-cpp-code.md)
- [Typedefs ( typedefs )](/cpp/cpp/aliases-and-typedefs-cpp#typedefs)
