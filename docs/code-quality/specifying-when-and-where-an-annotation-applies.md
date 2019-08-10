---
title: Określanie warunków pojawiania się adnotacji
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Group_
- _At_
- _When_
- _At_buffer_
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 6c7adb310db9eece1d8d4a2881057cc1acde1062
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923814"
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>Określanie warunków pojawiania się adnotacji
Gdy adnotacja jest warunkowa, może wymagać innych adnotacji, aby określić, że do analizatora.  Na przykład, jeśli funkcja ma zmienną, która może być synchroniczna lub asynchroniczna, funkcja zachowuje się w następujący sposób: W przypadku synchronicznego, zawsze ostatecznie kończy się powodzeniem, ale w przypadku asynchronicznym zgłasza błąd, jeśli nie może natychmiast zakończyć się pomyślnie. Gdy funkcja jest wywoływana synchronicznie, sprawdzenie wartości wyniku nie zapewnia żadnej wartości dla analizatora kodu, ponieważ nie została zwrócona.  Jeśli jednak funkcja jest wywoływana asynchronicznie, a wynik funkcji nie jest zaznaczony, może wystąpić poważny błąd. Ten przykład ilustruje sytuację, w której można użyć `_When_` adnotacji — opisanej w dalszej części tego artykułu — aby włączyć sprawdzanie.

## <a name="structural-annotations"></a>Adnotacje strukturalne
Aby określić, kiedy i gdzie mają być stosowane adnotacje, użyj następujących adnotacji strukturalnej.

|Adnotacja|Opis|
|----------------|-----------------|
|`_At_(expr, anno-list)`|`expr`jest wyrażeniem, które zwraca lvalue. Adnotacje w `anno-list` są stosowane do obiektu, który jest nazwany przez `expr`. Dla każdej adnotacji `anno-list`w `expr` , jest interpretowany jako warunek wstępny, jeśli adnotacja jest interpretowana jako warunek wstępny, a w warunku post, jeśli adnotacja jest interpretowana w warunku post.|
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr`jest wyrażeniem, które zwraca lvalue. Adnotacje w `anno-list` są stosowane do obiektu, który jest nazwany przez `expr`. Dla każdej adnotacji `anno-list`w `expr` , jest interpretowany jako warunek wstępny, jeśli adnotacja jest interpretowana w warunku wstępnego i w warunku post, jeśli adnotacja jest interpretowana w warunku post.<br /><br /> `iter`jest nazwą zmiennej, która jest objęta zakresem adnotacji (włącznie z `anno-list`). `iter`ma typ `long`niejawny. Zmienne o identycznej nazwie w dowolnym zakresie otaczającym są ukryte przed oszacowaniem.<br /><br /> `elem-count`jest wyrażeniem, którego wynikiem jest liczba całkowita.|
|`_Group_(anno-list)`|Adnotacje w `anno-list` programie są uważane za posiadające dowolny kwalifikator dotyczący adnotacji grupy, która jest stosowana do każdej adnotacji.|
|`_When_(expr, anno-list)`|`expr`jest wyrażeniem, które można przekonwertować na `bool`. Jeśli wartość jest różna od zera (`true`), adnotacje określone w `anno-list` są uważane za odpowiednie.<br /><br /> Domyślnie dla każdej adnotacji w `anno-list`, `expr` jest interpretowana jako użycie wartości wejściowych, jeśli adnotacja jest warunkiem wstępnym, i jako wartość wyjściowa, jeśli adnotacja jest warunkiem post. Aby zastąpić wartość domyślną, można użyć `_Old_` wartości wewnętrznej podczas obliczania warunku końcowego, aby wskazać, że powinny być używane dane wejściowe. **Uwaga:**  Różne adnotacje mogą być włączane jako zgodne z użyciem `_When_` , jeśli wartość modyfikowalna — na przykład `*pLength`— jest uwzględniana, `expr` ponieważ wynikiem obliczania warunku wstępnego może być różnica w porównaniu z wynikami jego oceny warunkowej.|

## <a name="see-also"></a>Zobacz też

- [Korzystanie z adnotacji SAL w celu zmniejszenia liczby defektów kodu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Informacje o języku SAL](../code-quality/understanding-sal.md)
- [Dodawanie adnotacji do parametrów funkcji i zwracanych wartości](../code-quality/annotating-function-parameters-and-return-values.md)
- [Zachowanie funkcji dodawania adnotacji](../code-quality/annotating-function-behavior.md)
- [Dodawanie adnotacji do struktur i klas](../code-quality/annotating-structs-and-classes.md)
- [Dodawanie adnotacji do zachowania blokującego](../code-quality/annotating-locking-behavior.md)
- [Funkcje wewnętrzne](../code-quality/intrinsic-functions.md)
- [Najlepsze rozwiązania i przykłady](../code-quality/best-practices-and-examples-sal.md)