---
title: Funkcje wewnętrzne
ms.date: 11/04/2016
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
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: b9236a5135d1339f46aeb6f2dd1a11658adf01c2
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72445708"
---
# <a name="intrinsic-functions"></a>Funkcje wewnętrzne
Wyrażenie w porażeniu SAL może być C/C++ wyrażeniem, pod warunkiem, że jest wyrażeniem, które nie ma efektów ubocznych — na przykład + +,--, i wywołania funkcji wszystkie mają efekty uboczne w tym kontekście.  Funkcja SAL udostępnia jednak niektóre obiekty podobne do funkcji i niektóre zastrzeżone symbole, które mogą być używane w wyrażeniach SAL. Są one nazywane *funkcjami wewnętrznymi*.

## <a name="general-purpose"></a>Ogólnego przeznaczenia
Poniższe adnotacje funkcji instrinsic zapewniają ogólne narzędzie dla SAL.

|Adnotacja|Opis|
|----------------|-----------------|
|`_Curr_`|Synonim dla obiektu, który jest aktualnie dodawany do adnotacji.  Gdy adnotacja `_At_` jest używana, `_Curr_` jest taka sama jak pierwszy parametr `_At_`.  W przeciwnym razie jest to parametr lub cała funkcja/wartość zwracana, z którą adnotacja jest w sposób leksykalny.|
|`_Inexpressible_(expr)`|Wyraża sytuację, w której rozmiar buforu jest zbyt złożony do reprezentowania przy użyciu wyrażenia adnotacji — na przykład, kiedy jest obliczany przez skanowanie zestawu danych wejściowych, a następnie liczenie wybranych elementów członkowskich.|
|`_Nullterm_length_(param)`|`param` to liczba elementów w buforze, do których nie dołączany jest terminator o wartości null. Może być zastosowany do dowolnego buforu typu innego niż "void".|
|`_Old_(expr)`|Gdy jest oceniana w warunku wstępnym, `_Old_` zwraca wartość wejściową `expr`.  Gdy jest on oceniany w warunku post, zwraca wartość `expr`, ponieważ zostałaby oceniona w warunku wstępnym.|
|`_Param_(n)`|@No__t-0th parametr do funkcji, licząc od 1 do `n` i `n` jest stałą całkowitą. Jeśli parametr ma nazwę, ta adnotacja jest taka sama, aby uzyskać dostęp do parametru według nazwy. **Uwaga:**  `n` może odwoływać się do parametrów pozycyjnych, które są zdefiniowane przez wielokropek lub które mogą być używane w prototypach funkcji, gdzie nazwy nie są używane.|
|`return`|Słowo kluczowe CC++ /zastrzeżone `return` może być używane w wyrażeniu sal w celu wskazania wartości zwracanej funkcji.  Wartość jest dostępna tylko w stanie post; jest to błąd składniowy, aby używać go w stanie sprzed.|

## <a name="string-specific"></a>Określony ciąg
Poniższe adnotacje funkcji wewnętrznych umożliwiają manipulowanie ciągami. Wszystkie cztery z tych funkcji służą tego samego celu: aby zwrócić liczbę elementów typu znalezionych przed terminatorem o wartości null. Różnice to rodzaje danych w elementach, do których odwołują się. Należy pamiętać, że jeśli chcesz określić długość bufora zakończono znakiem null, który nie zawiera znaków, użyj adnotacji `_Nullterm_length_(param)` z poprzedniej sekcji.

|Adnotacja|Opis|
|----------------|-----------------|
|`_String_length_(param)`|`param` to liczba elementów w ciągu, które nie obejmują terminatora null. Ta adnotacja jest zarezerwowana dla typów ciągów znaków.|
|`strlen(param)`|`param` to liczba elementów w ciągu, które nie obejmują terminatora null. Ta adnotacja jest zarezerwowana do użycia w tablicach znaków i przypomina funkcję środowiska uruchomieniowego C [strlen ()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|
|`wcslen(param)`|`param` to liczba elementów w ciągu, do których nie ma terminatora null. Ta adnotacja jest zarezerwowana do użycia w tablicach o szerokim znaku i przypomina funkcję środowiska uruchomieniowego C [wcslen ()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|

## <a name="see-also"></a>Zobacz też

- [Korzystanie z adnotacji SAL w celu zmniejszenia liczby defektów kodu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Informacje o języku SAL](../code-quality/understanding-sal.md)
- [Dodawanie adnotacji do parametrów funkcji i zwracanych wartości](../code-quality/annotating-function-parameters-and-return-values.md)
- [Zachowanie funkcji dodawania adnotacji](../code-quality/annotating-function-behavior.md)
- [Dodawanie adnotacji do struktur i klas](../code-quality/annotating-structs-and-classes.md)
- [Dodawanie adnotacji do zachowania blokującego](../code-quality/annotating-locking-behavior.md)
- [Określanie miejsca i warunków stosowania adnotacji](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Najlepsze rozwiązania i przykłady](../code-quality/best-practices-and-examples-sal.md)
