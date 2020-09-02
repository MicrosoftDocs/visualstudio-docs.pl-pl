---
title: Visual C++ Typedefs w Projektant klas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 980c49aafba55e29714d786e492f7bb37a8ca621
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646748"
---
# <a name="visual-c-typedefs-in-class-designer"></a>Definicje typów Visual C++ w Projektancie klas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Typedef — instrukcje Utwórz co najmniej jedną warstwę pośrednika między nazwą i jej typem podstawowym. Projektant klas obsługuje typy C++ typedef, które są zadeklarowane za pomocą słowa kluczowego `typedef` , na przykład:

```
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
} COORD;
```

 Następnie można użyć tego typu, aby zadeklarować wystąpienie:

 `COORD OriginPoint;`

 Chociaż można zadeklarować element typedef bez nazwy, Projektant klas nie będzie używać nazwy tagu określonej przez użytkownika; zostanie użyta nazwa generowana Widok klasy. Na przykład następująca deklaracja jest prawidłowa, ale występuje w Widok klasy i Projektant klas jako obiekt o nazwie **__unnamed**:

```
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
};
```

 Aby uzyskać więcej informacji na temat używania `typedef` typu, zobacz [(NOTINBUILD) specyfikator typedef](https://msdn.microsoft.com/cc96cf26-ba93-4179-951e-695d1f5fdcf1).

 Kształt języka C++ typedef ma kształt typu określonego w elemencie typedef. Na przykład, jeśli źródło deklaruje `typedef class` , kształt ma zaokrąglone rogi i **klasę**etykiet. Dla `typedef struct` , kształt ma narożniki kwadratowe i **strukturę**etykiet.

 Klasy i struktury mogą mieć zagnieżdżone definicje TypeDef zadeklarowane w nich; w związku z tym kształty klas i struktur mogą wyświetlać zagnieżdżone deklaracje typedef jako kształty zagnieżdżone.

 Kształty typedef obsługują polecenia **show as Association** i **show as Collection** w menu kontekstowym.

 Poniżej przedstawiono kilka przykładów typów typdef obsługiwanych przez Projektant klas:

 `typedef type name`

 *Nazwa* : *wpisz*

  — klasa typedef

 Rysuje linię skojarzenia łączącą się z *nazwą*typu, jeśli jest to możliwe.

 `typedef void (*func)(int)`

 `func: void (*)(int)`

  — klasa typedef

 Element typedef dla wskaźników funkcji. Nie jest rysowany żaden wiersz skojarzenia.

 Projektant klas nie wyświetla elementu typedef, jeśli jego typ źródłowy jest wskaźnikiem funkcji.

```
typedef int MyInt;
class A {
   MyInt I;
};
```

 `MyInt: int`

  — klasa typedef

 `A`

 Klasa

 Rysuje linię skojarzenia wskazującą kształt typu źródła do kształtu typu docelowego.

 `Class B {};`

 `typedef B MyB;`

 `B`

 Klasa

 `MyB : B`

  — klasa typedef

 Kliknięcie prawym przyciskiem myszy kształtu typedef i kliknięcie pozycji **Pokaż jako skojarzenie** powoduje wyświetlenie elementu typedef lub klasy oraz **aliasu** linii łączącej dwa kształty (podobnie jak w przypadku linii skojarzenia).

 `typedef B MyB;`

 `typedef MyB A;`

 `MyBar : Bar`

  — klasa typedef

 Tak samo jak powyżej.

```
Class B {};
typedef B MyB;

class A {
   MyB B;
};
```

 `B`

 Klasa

 `MyB : B`

  — klasa typedef

 `A`

 Klasa

 `MyB` jest zagnieżdżonym kształtem typedef.

 `#include <vector>`

 `...`

 `using namespace std;`

 `...`

 `typedef vector<int> MyIntVect;`

 `vector<T>`Klasa

 `MyIntVect : vector<int>`

  — klasa typedef

 `class B {};`

 `typedef B MyB;`

 `class A : MyB {};`

 `MyB : B`

  — klasa typedef

 -> B

 `B`

 `A`

 Klasa

 -> MyB

 Projektant klas nie obsługuje wyświetlania tego rodzaju relacji przy użyciu polecenia menu kontekstowego.

 `#include <vector>`

 `Typedef MyIntVect std::vector<int>;`

 `Class MyVect : MyIntVect {};`

 `std::vector<T>`

 Klasa

 `MyIntVect : std::vector<int>`

  — klasa typedef

 `MyVect`

 Klasa

 -> MyIntVect

## <a name="see-also"></a>Zobacz też
 [Praca z specyfikatorem "Visual C++ Code (Projektant klas)](../ide/working-with-visual-cpp-code-class-designer.md) [(NOTINBUILD) typedef](https://msdn.microsoft.com/cc96cf26-ba93-4179-951e-695d1f5fdcf1)
