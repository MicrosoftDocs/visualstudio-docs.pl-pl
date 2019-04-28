---
title: Zachowanie funkcji dodawania adnotacji
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _On_failure_
- _Return_type_success_
- _Always_
- _Maybe_raises_SEH_exception_
- _Raises_SEH_exception_
- _Called_from_function_class_
- _Function_class_
- _Must_inspect_result_
- _Success_
- _Check_return_
- _Use_decl_annotations_
ms.assetid: c0aa268d-6fa3-4ced-a8c6-f7652b152e61
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 78a8bf94323391d031aaf718f6e3132eb89e1df3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62560379"
---
# <a name="annotating-function-behavior"></a>Zachowanie funkcji dodawania adnotacji
Oprócz dodawania adnotacji [funkcji parametry i zwracane wartości](../code-quality/annotating-function-parameters-and-return-values.md), może dodawać adnotacje właściwości całej funkcji.

## <a name="function-annotations"></a>Adnotacje — funkcja
 Następujących adnotacji dotyczą funkcji jako całość i opisują sposób działania lub oczekuje to true.

|Adnotacja|Opis|
|----------------|-----------------|
|`_Called_from_function_class_(name)`|Nie ma na celu autonomicznie; Zamiast tego jest predykatem, po którym ma być używany z `_When_` adnotacji. Aby uzyskać więcej informacji, zobacz [określanie podczas i gdzie warunków stosowania adnotacji](../code-quality/specifying-when-and-where-an-annotation-applies.md).<br /><br /> `name` Parametr jest dowolny ciąg, który pojawia się również w `_Function_class_` adnotacji w deklaracji z niektórych funkcji.  `_Called_from_function_class_` Zwraca wartość różną od zera, jeśli funkcja, która jest aktualnie analizowana jest oznaczona za pomocą `_Function_class_` który ma taką samą wartość `name`; w przeciwnym razie zwraca wartość zero.|
|`_Check_return_`|Oznacza stosowanym zwracana wartość i Stany, obiekt wywołujący powinien sprawdzić go. Moduł sprawdzania zgłasza błąd, jeśli funkcja jest wywoływana w kontekście typu void.|
|`_Function_class_(name)`|`name` Parametr jest dowolny ciąg, który jest wyznaczone przez użytkownika.  Istnieje w przestrzeni nazw, która różni się od innych przestrzeniach nazw. Funkcja, wskaźnika funkcji lub — najbardziej korzyścią — typ wskaźnika funkcji mogą być oznaczone jako należące do co najmniej jedną klasę funkcji.|
|`_Raises_SEH_exception_`|Oznacza stosowanym funkcja, która zawsze zgłasza wyjątek strukturalnej obsługi wyjątków strukturalnych, podlegają `_When_` i `_On_failure_` warunków. Aby uzyskać więcej informacji, zobacz [określanie podczas i gdzie warunków stosowania adnotacji](../code-quality/specifying-when-and-where-an-annotation-applies.md).|
|`_Maybe_raises_SEH_exception_`|Oznacza stosowanym funkcja, która opcjonalnie może zgłosić wyjątek SEH, podlegają `_When_` i `_On_failure_` warunków.|
|`_Must_inspect_result_`|Oznacza stosowanym dowolne wartości danych wyjściowych, w tym zwracanej wartości, parametry i zmienne globalne.  Analizator zgłasza błąd, jeśli wartość w obiekcie adnotacjami nie później sprawdzana jest. "Inspekcja" obejmuje, czy jest używana w wyrażeniu warunkowym, jest przypisany do parametru wyjściowego lub globalnego, jest przekazywany jako parametr.  Dla wartości zwracanych `_Must_inspect_result_` oznacza `_Check_return_`.|
|`_Use_decl_annotations_`|Mogą być używane w definicji funkcji (nazywanego także treści funkcji) zamiast listy adnotacje w nagłówku.  Gdy `_Use_decl_annotations_` jest używany, adnotacje, które pojawiają się w nagłówku w zakresie dla tej samej funkcji są używane tak, jakby są również obecne w definicji, który ma `_Use_decl_annotations_` adnotacji.|

## <a name="successfailure-annotations"></a>Adnotacje Powodzenie/niepowodzenie
 Funkcja może zakończyć się niepowodzeniem, a jeśli tak się stanie, wyniki mogą być niekompletne lub różnią się od wyników, jeśli funkcja się powiedzie.  Adnotacje na poniższej liście umożliwiają określenie zachowania awarii.  Aby użyć tych adnotacji, należy włączyć je do określenia sukcesu; w związku z tym `_Success_` wymagana jest adnotacja.  Należy zauważyć, że `NTSTATUS` i `HRESULT` jeszcze `_Success_` adnotacji wbudowane; jednak w przypadku określenia własnego `_Success_` adnotacja `NTSTATUS` lub `HRESULT`, zastępuje ona wbudowanych adnotacji.

|Adnotacja|Opis|
|----------------|-----------------|
|`_Always_(anno_list)`|Odpowiednikiem `anno_list _On_failure_(anno_list)`; oznacza to, adnotacje w `anno_list` zastosować informację określającą, czy funkcja się powiedzie.|
|`_On_failure_(anno_list)`|Ma być używany tylko wtedy, gdy `_Success_` służy również dodawać adnotacje do funkcji — jawnie lub niejawnie za pośrednictwem `_Return_type_success_` na element typedef. Gdy `_On_failure_` adnotacji znajduje się na funkcji parametrze lub wartości zwracanej, każdej adnotacji w `anno_list` (anno) zachowuje się tak, jakby było kodowane jako `_When_(!expr, anno)`, gdzie `expr` jest parametrem wymaganym `_Success_` adnotacji. Oznacza to, że stosowanie dorozumianych `_Success_` do wszystkich warunków nie ma zastosowania do `_On_failure_`.|
|`_Return_type_success_(expr)`|Można stosować do typedef. Wskazuje, że wszystkie funkcje zwracające, wpisz i nie mają jawnie `_Success_` adnotację tak, jakby mieli oni `_Success_(expr)`. `_Return_type_success_` Nie można użyć funkcji lub typedef wskaźnika funkcji.|
|`_Success_(expr)`|`expr` to wyrażenie zwracające rvalue. Gdy `_Success_` adnotacji jest obecny w deklaracji funkcji lub definicja, każda adnotacja (`anno`) dla funkcji, jak i w stanie po zachowuje się tak, jakby było kodowane jako `_When_(expr, anno)`. `_Success_` Adnotację może być używana tylko dla funkcji, nie na jego parametrów lub typ zwracany. Może być co najwyżej jeden `_Success_` adnotacja dla funkcji, a nie może być w dowolnym `_When_`, `_At_`, lub `_Group_`. Aby uzyskać więcej informacji, zobacz [określanie podczas i gdzie warunków stosowania adnotacji](../code-quality/specifying-when-and-where-an-annotation-applies.md).|

## <a name="see-also"></a>Zobacz także

- [Korzystanie z adnotacji SAL w celu zmniejszenia liczby defektów kodu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Informacje o języku SAL](../code-quality/understanding-sal.md)
- [Dodawanie adnotacji do parametrów funkcji i zwracanych wartości](../code-quality/annotating-function-parameters-and-return-values.md)
- [Dodawanie adnotacji do struktur i klas](../code-quality/annotating-structs-and-classes.md)
- [Dodawanie adnotacji do zachowania blokującego](../code-quality/annotating-locking-behavior.md)
- [Określanie miejsca i warunków stosowania adnotacji](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Funkcje wewnętrzne](../code-quality/intrinsic-functions.md)
- [Najlepsze rozwiązania i przykłady](../code-quality/best-practices-and-examples-sal.md)