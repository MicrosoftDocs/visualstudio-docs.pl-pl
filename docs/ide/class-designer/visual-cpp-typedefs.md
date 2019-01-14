---
title: Definicje typów Visual C++ w Projektancie klas
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: bca0dacf2fd649db91fb37756c1670af403b4e95
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2019
ms.locfileid: "54269414"
---
# <a name="visual-c-typedefs-in-class-designer"></a>Definicje typów Visual C++ w Projektancie klas

[Element TypeDef](/cpp/cpp/aliases-and-typedefs-cpp#typedefs) instrukcji utworzyć jedną lub więcej warstw pośredników między nazwą jej typ podstawowy. **Projektant klasy** obsługuje typy typedef C++, które są zadeklarowane za pomocą słowa kluczowego `typedef`, na przykład:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
} COORD;
```

Tego typu można następnie użyć do deklarowania wystąpienie:

`COORD OriginPoint;`

## <a name="class-and-struct-shapes"></a>Kształty klasy i struktury

W **projektanta klas**, C++ typedef ma kształt z typem określonym w definicji typu. Jeśli źródło deklaruje `typedef class`, kształt ma zaokrąglone rogi i etykiety **klasy**. Aby uzyskać `typedef struct`, kształt ma ostre rogi i etykieta **struktury**.

Klasy i struktury może mieć definicje typów zagnieżdżonych, zadeklarowany wewnątrz nich. W **projektanta klas**, kształty klasy i struktury można wyświetlić deklaracje typedef zagnieżdżonych kształtów jako zagnieżdżonych.

Element TypeDef kształty pomocy technicznej **wyświetlić jako skojarzenie** i **pokazać jako skojarzenia kolekcji** poleceń w menu kliknij prawym przyciskiem myszy (menu kontekstowe).

### <a name="class-typedef-example"></a>Przykład element typedef dla klasy

```cpp
class B {};
typedef B MyB;
```

![Typedef klasy języka C++ w Projektancie klas](media/cpp-class-typedef.png)

### <a name="struct-typedef-example"></a>Przykład — typedef — struktura

```cpp
typedef struct mystructtag
{
    int   i;
    double f;
} mystruct;
```

![Typedef — struktura języka C++ w Projektancie klas](media/cpp-struct-typedef.png)

## <a name="unnamed-typedefs"></a>Nienazwane elementy TypeDef

Mimo że można zadeklarować element typedef bez nazwy **projektanta klas** nie używa nazwa tagu, który określisz. **Projektant klasy** używa nazwy, **Widok klas** generuje. Na przykład następująca deklaracja jest prawidłowy, ale zostanie on wyświetlony na **Widok klas** i **projektanta klas** jako obiekt o nazwie **__unnamed**:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
};
```

> [!NOTE]
> **Projektant klasy** definicje typów, których typ źródłowy jest wskaźnik funkcji nie są wyświetlane.

## <a name="see-also"></a>Zobacz także

- [Praca z kodem Visual C++](working-with-visual-cpp-code.md)
- [Typedefs](/cpp/cpp/aliases-and-typedefs-cpp#typedefs)