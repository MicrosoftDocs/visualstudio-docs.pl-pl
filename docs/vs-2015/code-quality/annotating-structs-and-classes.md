---
title: Dodawanie adnotacji do struktur i klas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
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
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 6db2202971facb0419db68c04835c8d5c848f528
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2020
ms.locfileid: "77271585"
---
# <a name="annotating-structs-and-classes"></a>Dodawanie adnotacji struktur i klas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz dodawać adnotacje do struktury i składowych klas przy użyciu adnotacji, które działają jak niewarianty — są one uznawane za prawdziwe w przypadku dowolnego wywołania funkcji lub wejścia/wyjścia funkcji, która obejmuje otaczającą strukturę jako parametr lub wartość wynikową.  
  
## <a name="struct-and-class-annotations"></a>Adnotacje struktury i klasy  
  
- `_Field_range_(low, high)`  
  
     Pole znajduje się w zakresie (włącznie) od `low` do `high`.  Odpowiednik do `_Satisfies_(_Curr_ >= low && _Curr_ <= high)` stosowany do obiektu z adnotacją przy użyciu odpowiednich warunków poprzedzających lub post.  
  
- `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`  
  
     Pole, które ma rozmiar możliwy do zapisu w elementach (lub bajtach) określonych przez `size`.  
  
- `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`, `_Field_size_bytes_part_(size, count)``_Field_size_bytes_part_opt_(size, count)`  
  
     Pole, które ma zapisywalny rozmiar w elementach (lub bajtach) określony przez `size`i `count` tych elementów (bajtów), które można odczytać.  
  
- `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`  
  
     Pole, które ma zarówno czytelny, jak i zapisywalny rozmiar w elementach (lub bajtach) określony przez `size`.  
  
- `_Struct_size_bytes_(size)`  
  
     Pole, które ma zarówno czytelny, jak i zapisywalny rozmiar w elementach (lub bajtach) określony przez `size`.  
  
     Dotyczy deklaracji struktury lub klasy.  Wskazuje, że prawidłowy obiekt tego typu może być większy niż zadeklarowany typ, z liczbą bajtów określoną przez `size`.  Na przykład:  
  
    ```cpp  
  
    typedef _Struct_size_bytes_(nSize)  
    struct MyStruct {  
        size_t nSize;  
        …  
    };  
  
    ```  
  
     Rozmiar buforu w bajtach `pM` parametru typu `MyStruct *` jest następnie traktowany jako:  
  
    ```cpp  
    min(pM->nSize, sizeof(MyStruct))  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z adnotacji sal w celuC++ zmniejszenia wad kodu C/Code](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Zrozumienie  sal](../code-quality/understanding-sal.md)  
 [Dodawanie adnotacji do parametrów funkcji i zwracanych wartości](../code-quality/annotating-function-parameters-and-return-values.md)   
   [zachowanie funkcji dodawania adnotacji](../code-quality/annotating-function-behavior.md)  
 [Dodawanie adnotacji do zachowania blokowania](../code-quality/annotating-locking-behavior.md)   
 [Określanie, kiedy i gdzie ma być stosowana adnotacja](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Funkcje wewnętrzne](../code-quality/intrinsic-functions.md)   
 [Najlepsze rozwiązania i przykłady](../code-quality/best-practices-and-examples-sal.md)
