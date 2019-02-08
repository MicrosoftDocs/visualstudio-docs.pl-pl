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
ms.openlocfilehash: 1b94bd5dc40102bce073e42302e92b737b4e8b0d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55942027"
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>Określanie warunków pojawiania się adnotacji
W przypadku warunkowego adnotacji może wymagać innych adnotacji, aby określić, że do analizatora.  Na przykład jeśli funkcja zawiera zmienną, która może być synchroniczna lub asynchroniczna, funkcja zachowuje się w następujący sposób: W przypadku synchroniczne go zawsze ostatecznie zakończy się pomyślnie, ale w przypadku asynchronicznej go zgłasza błąd, jeśli nie powiedzie się natychmiast. Gdy funkcja jest wywoływana synchronicznie, wartość wyniku sprawdzania zapewnia żadnej wartości, aby analizator kodu, ponieważ nie będzie mieć zwracane.  Jednak gdy funkcja jest wywoływana asynchronicznie, a wynik funkcji nie jest zaznaczone, może wystąpić po poważnym błędzie. W tym przykładzie pokazano sytuację, w której można użyć `_When_` adnotacji — opisane w dalszej części tego artykułu — Aby włączyć sprawdzanie.

## <a name="structural-annotations"></a>Adnotacje strukturalnych
 Do kontrolowania, kiedy i gdzie Zastosuj adnotacje, użyj następujących adnotacji strukturalnych.

|Adnotacja|Opis|
|----------------|-----------------|
|`_At_(expr, anno-list)`|`expr` to wyrażenie zwracające l-wartością. Adnotacje w `anno-list` są stosowane do obiektu, który jest nazwany przez `expr`. Dla każdego wpisu `anno-list`, `expr` jest interpretowany w warunku wstępnego, jeśli adnotacja jest interpretowany w warunku wstępnego i jeśli warunek po adnotacja jest interpretowany w stanie po.|
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` to wyrażenie zwracające l-wartością. Adnotacje w `anno-list` są stosowane do obiektu, który jest nazwany przez `expr`. Dla każdego wpisu `anno-list`, `expr` jest interpretowany w warunku wstępnego, jeśli adnotacja jest interpretowany w warunku wstępnym, jeśli warunek po adnotacja jest interpretowany w stanie po.<br /><br /> `iter` to nazwa zmiennej, które są ograniczone do adnotacji (inclusive z `anno-list`). `iter` ma niejawnego typu `long`. Zmienne o identycznej nazwie w dowolnym otaczającego zakresu są ukryte przed oceny.<br /><br /> `elem-count` to wyrażenie obliczane do wartości całkowitej.|
|`_Group_(anno-list)`|Adnotacje w `anno-list` wszystkie uznaje się za mieć żadnych kwalifikatorów, dotyczy adnotacji grupy, która jest stosowana do każdego adnotacji.|
|`_When_(expr, anno-list)`|`expr` to wyrażenie, które mogą być konwertowane na `bool`. Gdy jest różna od zera (`true`), adnotacje, które są określone w `anno-list` są uważane za odpowiednie.<br /><br /> Domyślnie dla każdego wpisu `anno-list`, `expr` jest interpretowany jako przy użyciu wartości wejściowych, jeśli adnotacja jest warunkiem wstępnym, a jako przy użyciu wartości danych wyjściowych, jeśli adnotacja jest po warunku. Aby zastąpić domyślne, można użyć `_Old_` wewnętrzne podczas oceny po warunku, aby wskazać, że wartości wejściowe powinny być używane. **Uwaga:**  Adnotacje różnych może zostać włączona w wyniku za pomocą `_When_` Jeśli wartość modyfikowalną — na przykład `*pLength`— jest używana, ponieważ obliczony wynik `expr` w warunku wstępnym może różnić się od jego obliczony wynik w warunku po.|

## <a name="see-also"></a>Zobacz też

- [Korzystanie z adnotacji SAL w celu zmniejszenia liczby defektów kodu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Informacje o języku SAL](../code-quality/understanding-sal.md)
- [Dodawanie adnotacji do parametrów funkcji i zwracanych wartości](../code-quality/annotating-function-parameters-and-return-values.md)
- [Zachowanie funkcji dodawania adnotacji](../code-quality/annotating-function-behavior.md)
- [Dodawanie adnotacji do struktur i klas](../code-quality/annotating-structs-and-classes.md)
- [Dodawanie adnotacji do zachowania blokującego](../code-quality/annotating-locking-behavior.md)
- [Funkcje wewnętrzne](../code-quality/intrinsic-functions.md)
- [Najlepsze rozwiązania i przykłady](../code-quality/best-practices-and-examples-sal.md)