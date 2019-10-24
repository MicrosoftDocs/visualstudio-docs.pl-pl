---
title: Dodawanie adnotacji struktur i klas
ms.date: 06/28/2019
ms.topic: conceptual
f1_keywords:
- _Field_size_bytes_part_
- _Field_size_bytes_full_opt_
- _Field_size_bytes_
- _Field_size_opt_
- _Field_size_part_
- _Field_size_bytes_part_opt_
- _Field_range_
- _Field_size_part_opt_
- _Field_size_
- _Field_size_bytes_opt_
- _Struct_size_bytes_
- _Field_size_bytes_full_
- _Field_size_full_
- _Field_size_full_opt_
- _Field_z_
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 93c6826f2903f30fbbdcb9c40ec5f695df32ac05
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747052"
---
# <a name="annotating-structs-and-classes"></a>Dodawanie adnotacji struktur i klas

Możesz dodawać adnotacje do struktury i składowych klas przy użyciu adnotacji, które działają jak niewarianty — są one uznawane za prawdziwe w przypadku dowolnego wywołania funkcji lub wejścia/wyjścia funkcji, która obejmuje otaczającą strukturę jako parametr lub wartość wynikową.

## <a name="struct-and-class-annotations"></a>Adnotacje struktury i klasy

- `_Field_range_(low, high)`

     Pole znajduje się w zakresie (włącznie) od `low` do `high`.  Odpowiednik do `_Satisfies_(_Curr_ >= low && _Curr_ <= high)` stosowany do obiektu z adnotacją przy użyciu odpowiednich warunków poprzedzających lub post.

- `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)` `_Field_size_bytes_opt_(size)`

     Pole, które ma rozmiar zapisywalny w elementach (lub bajtach) określony przez `size`.

- `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`, `_Field_size_bytes_part_(size, count)` `_Field_size_bytes_part_opt_(size, count)`

     Pole, które ma zapisywalny rozmiar w elementach (lub bajtach) określony przez `size` i `count` tych elementów (bajtów), które są odczytywane.

- `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)` `_Field_size_bytes_full_opt_(size)`

     Pole, które ma zarówno czytelny, jak i zapisywalny rozmiar w elementach (lub bajtach) określony przez `size`.

- `_Field_z_`

     Pole, które ma ciąg zakończony znakiem null.

- `_Struct_size_bytes_(size)`

     Dotyczy deklaracji struktury lub klasy.  Wskazuje, że prawidłowy obiekt tego typu może być większy niż zadeklarowany typ, z liczbą bajtów określoną przez `size`.  Na przykład:

    ```cpp

    typedef _Struct_size_bytes_(nSize)
    struct MyStruct {
        size_t nSize;
        ...
    };

    ```

     Rozmiar buforu w bajtach `pM` typu `MyStruct *` jest następnie traktowany jako:

    ```cpp
    min(pM->nSize, sizeof(MyStruct))
    ```

## <a name="example"></a>Przykład

```cpp
#include <sal.h>
// For FIELD_OFFSET macro
#include <windows.h>

// This _Struct_size_bytes_ is equivalent to what below _Field_size_ means.
_Struct_size_bytes_(FIELD_OFFSET(MyBuffer, buffer) + bufferSize * sizeof(int))
struct MyBuffer
{
    static int MaxBufferSize;
    
    _Field_z_
    const char* name;
    
    int firstField;

    // ... other fields

    _Field_range_(1, MaxBufferSize)
    int bufferSize;
    _Field_size_(bufferSize)        // Prefered way - easier to read and maintain.
    int buffer[0];
};
```

Uwagi dotyczące tego przykładu:

- `_Field_z_` jest równoznaczna z `_Null_terminated_`.  `_Field_z_` pola Nazwa Określa, że pole Nazwa jest ciągiem zakończonym wartością null.
- `_Field_range_` dla `bufferSize` określa, że wartość `bufferSize` powinna należeć do zakresu od 1 do `MaxBufferSize` (włącznie).
- Końcowe wyniki `_Struct_size_bytes_` i `_Field_size_` adnotacji są równoważne. W przypadku struktur lub klas, które mają podobny układ, `_Field_size_` jest łatwiejsze do odczytania i konserwowania, ponieważ ma mniejszą liczbę odwołań i obliczeń niż odpowiednik `_Struct_size_bytes_`j adnotacji. `_Field_size_` nie wymaga konwersji do rozmiaru bajtowego. Jeśli rozmiar bajtu jest jedyną opcją, na przykład dla pola wskaźnika void, można użyć `_Field_size_bytes_`. Jeśli zarówno `_Struct_size_bytes_`, jak i `_Field_size_` istnieją, oba będą dostępne dla narzędzi. Jest to narzędzie, co należy zrobić, jeśli dwa adnotacje nie zgadzają się.

## <a name="see-also"></a>Zobacz także

- [Korzystanie z adnotacji SAL w celu zmniejszenia liczby defektów kodu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Informacje o języku SAL](../code-quality/understanding-sal.md)
- [Dodawanie adnotacji do parametrów funkcji i zwracanych wartości](../code-quality/annotating-function-parameters-and-return-values.md)
- [Zachowanie funkcji dodawania adnotacji](../code-quality/annotating-function-behavior.md)
- [Dodawanie adnotacji do zachowania blokującego](../code-quality/annotating-locking-behavior.md)
- [Określanie miejsca i warunków stosowania adnotacji](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Funkcje wewnętrzne](../code-quality/intrinsic-functions.md)
- [Najlepsze rozwiązania i przykłady](../code-quality/best-practices-and-examples-sal.md)
