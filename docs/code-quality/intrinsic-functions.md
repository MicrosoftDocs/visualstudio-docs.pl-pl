---
title: Funkcje wewnętrzne
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- _String_length_
- _Param_
- _Curr_
- _Old_
- _Nullterm_length_
- _Inexpressible_
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 7781a1ac48945b2c272d5234ac7f4dcbd923b309
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53944525"
---
# <a name="intrinsic-functions"></a>Funkcje wewnętrzne
Wyrażenia w SAL może być wyrażeniem języka C/C++, pod warunkiem, że to wyrażenie ma efekty uboczne — na przykład ++,--i wywołania funkcji, wszystkie mają skutki uboczne w tym kontekście.  SAL zapewnia jednak niektóre obiekty funkcyjne i niektóre zastrzeżone symboli, które mogą być używane w wyrażeniach SAL. Są one określane jako *funkcje wewnętrzne*.

## <a name="general-purpose"></a>Ogólne zastosowanie
 Następujących adnotacji funkcja instrinsic zapewniają ogólne narzędzie SAL.

|Adnotacja|Opis|
|----------------|-----------------|
|`_Curr_`|Synonim dla obiektu, który jest obecnie oznaczony.  Gdy `_At_` adnotacja jest w użyciu, `_Curr_` jest taki sam jak pierwszy parametr `_At_`.  W przeciwnym razie jest parametr lub całej funkcji/zwracana wartość, z którą skojarzono się leksykalnie adnotacji.|
|`_Inexpressible_(expr)`|Wyraża sytuacji, w których rozmiar buforu jest zbyt złożona, aby reprezentować za pomocą wyrażenia adnotacji — na przykład, gdy jest ona obliczana przez skanowanie wejściowego zestawu danych, a następnie wciąż dochodzą nowe wybrane elementy członkowskie.|
|`_Nullterm_length_(param)`|`param` jest to liczba elementów w buforze do, ale nie łącznie z terminatorem null. Można stosować do dowolnej buforu typ agregacji, innym niż void.|
|`_Old_(expr)`|Gdy zostanie on oceniony w warunku wstępnym, `_Old_` zwraca wartości wejściowej `expr`.  Gdy zostanie ono ocenione po warunek, zwracana jest wartość `expr` jako może być ocenione w warunku wstępnym.|
|`_Param_(n)`|`n`Parametru do funkcji, licząc od 1 do `n`, i `n` jest literałem stałej. Jeśli ten parametr nosi, ta adnotacja jest taka sama jak uzyskiwanie dostępu do parametru o nazwie. **Uwaga:** `n` mogą odwoływać się do parametry pozycyjne, które są definiowane przez wielokropek lub mogą być używane w prototypy funkcji gdzie nazwy nie są używane.|
|`return`|C/C++ zastrzeżone słowa kluczowego `return` może służyć w wyrażeniu SAL do wskazania wartość zwracaną przez funkcję.  Wartość jest dostępna tylko w stanie post; jest z niego korzystać w stanie sprzed błąd składni.|

## <a name="string-specific"></a>Określonego ciągu
 Następujących adnotacji Wewnętrzna funkcja umożliwiają manipulowanie ciągami. Wszystkie cztery funkcje te służą do celów tego samego: Aby zwrócić liczbę elementów typu, który znajduje się przed terminatorem null. Różnice są typy danych w elementach, które są określone. Należy zauważyć, że jeśli chcesz określić długość zakończony znakiem null buforu, który nie składa się ze znaków, należy użyć `_Nullterm_length_(param)` adnotacji w poprzedniej sekcji.

|Adnotacja|Opis|
|----------------|-----------------|
|`_String_length_(param)`|`param` jest to liczba elementów w ciągu maksymalnie, ale nie łącznie z terminatorem null. Ta adnotacja jest zarezerwowana dla typów znaku ciągu.|
|`strlen(param)`|`param` jest to liczba elementów w ciągu maksymalnie, ale nie łącznie z terminatorem null. Ta adnotacja jest zarezerwowany do użycia na znak tablice i przypomina funkcji środowiska uruchomieniowego C [funkcje strlen()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|
|`wcslen(param)`|`param` jest to liczba elementów w ciągu maksymalnie (z wyjątkiem) terminator o wartości null. Ta adnotacja jest zarezerwowany do użycia na znak dwubajtowy tablice i przypomina funkcji środowiska uruchomieniowego C [wcslen()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|

## <a name="see-also"></a>Zobacz też

- [Korzystanie z adnotacji SAL w celu zmniejszenia liczby defektów kodu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Informacje o języku SAL](../code-quality/understanding-sal.md)
- [Dodawanie adnotacji do parametrów funkcji i zwracanych wartości](../code-quality/annotating-function-parameters-and-return-values.md)
- [Zachowanie funkcji dodawania adnotacji](../code-quality/annotating-function-behavior.md)
- [Dodawanie adnotacji do struktur i klas](../code-quality/annotating-structs-and-classes.md)
- [Dodawanie adnotacji do zachowania blokującego](../code-quality/annotating-locking-behavior.md)
- [Określanie miejsca i warunków stosowania adnotacji](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Najlepsze rozwiązania i przykłady](../code-quality/best-practices-and-examples-sal.md)