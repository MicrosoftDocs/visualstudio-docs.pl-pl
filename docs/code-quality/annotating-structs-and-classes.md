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
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 35be465064c9524eb0e1339794b6a19b7a595da1
ms.sourcegitcommit: d2b234e0a4a875c3cba09321cdf246842670d872
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2019
ms.locfileid: "67493633"
---
# <a name="annotating-structs-and-classes"></a>Dodawanie adnotacji struktur i klas

Elementy członkowskie struktury i klasy może dodawać adnotacje, za pomocą funkcji adnotacje, przypominają invariants — jest uznawana za tę prawdziwe dowolnego wywołania funkcji i funkcji wejścia/wyjścia, która obejmuje otaczającej strukturze jako parametr lub wartość wyniku.

## <a name="struct-and-class-annotations"></a>Struktury i klasy adnotacji

- `_Field_range_(low, high)`

     To pole jest z zakresu (włącznie) z `low` do `high`.  Odpowiednikiem `_Satisfies_(_Curr_ >= low && _Curr_ <= high)` zastosowany do obiektu adnotacjami przy użyciu odpowiednich warunków pre lub post.

- `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`

     Pola, które ma rozmiar obszaru do zapisu w elementy (lub w bajtach) jako określony przez `size`.

- `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`

     Pola, które ma rozmiar obszaru do zapisu w elementy (lub w bajtach) jako określony przez `size`i `count` tych elementów (w bajtach), które są do odczytu.

- `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`

     Pola, które ma elementy readable i writable rozmiar elementów (lub w bajtach) jako określony przez `size`.

- `_Field_z_`

     Pole, które zawiera ciąg zakończony znakiem null.

- `_Struct_size_bytes_(size)`

     Ma zastosowanie do deklaracji struktury lub klasy.  Wskazuje, że prawidłowy obiekt tego typu mogą być większe niż zadeklarowanym typem z liczbą bajtów jest określona przez `size`.  Na przykład:

    ```cpp

    typedef _Struct_size_bytes_(nSize)
    struct MyStruct {
        size_t nSize;
        ...
    };

    ```

     Rozmiar buforu w bajtach parametr `pM` typu `MyStruct *` zostaje następnie przeniesiony za:

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

Informacje w tym przykładzie:

- `_Field_z_` jest odpowiednikiem `_Null_terminated_`.  `_Field_z_` dla nazwy pola określa, że pole nazwy jest ciąg zakończony znakiem null.
- `_Field_range_` Aby uzyskać `bufferSize` Określa, że wartość `bufferSize` powinny być w ciągu 1 i `MaxBufferSize` (oba włącznie).
- Wyniki zakończenia `_Struct_size_bytes_` i `_Field_size_` adnotacje są równoważne. Struktury lub klasy, które mają podobny układ `_Field_size_` jest łatwiej odczytywać i utrzymywania, ponieważ ma ona mniejszą liczbę odwołań i obliczeń niż równowartość `_Struct_size_bytes_` adnotacji. `_Field_size_` nie wymaga konwersji na rozmiar w bajtach. Jeśli rozmiar w bajtach jest jedyną opcją, na przykład dla pola wskaźnika void `_Field_size_bytes_` mogą być używane. Jeśli oba `_Struct_size_bytes_` i `_Field_size_` istnieje, oba będą dostępne dla narzędzia. Jest to narzędzie co należy zrobić, jeśli dwa adnotacji nie zgadzają się.

## <a name="see-also"></a>Zobacz też

- [Korzystanie z adnotacji SAL w celu zmniejszenia liczby defektów kodu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Informacje o języku SAL](../code-quality/understanding-sal.md)
- [Dodawanie adnotacji do parametrów funkcji i zwracanych wartości](../code-quality/annotating-function-parameters-and-return-values.md)
- [Zachowanie funkcji dodawania adnotacji](../code-quality/annotating-function-behavior.md)
- [Dodawanie adnotacji do zachowania blokującego](../code-quality/annotating-locking-behavior.md)
- [Określanie miejsca i warunków stosowania adnotacji](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Funkcje wewnętrzne](../code-quality/intrinsic-functions.md)
- [Najlepsze rozwiązania i przykłady](../code-quality/best-practices-and-examples-sal.md)