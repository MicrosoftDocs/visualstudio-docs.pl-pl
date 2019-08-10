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
ms.openlocfilehash: c7ff2551f3a99bf13909f9db3b1659482246e957
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919633"
---
# <a name="annotating-function-behavior"></a>Zachowanie funkcji dodawania adnotacji
Oprócz dodawania adnotacji do [parametrów funkcji i zwracanych wartości](../code-quality/annotating-function-parameters-and-return-values.md)można dodawać adnotacje do właściwości całej funkcji.

## <a name="function-annotations"></a>Adnotacje funkcji
Poniższe adnotacje odnoszą się do funkcji jako całości i opisują sposób jej działania lub przewidywane znaczenie.

|Adnotacja|Opis|
|----------------|-----------------|
|`_Called_from_function_class_(name)`|Nie przeznaczony do autonomicznego; Zamiast tego jest predykatem, który ma być używany z `_When_` adnotacją. Aby uzyskać więcej informacji, zobacz [Określanie, kiedy i gdzie ma zastosowanie adnotacja](../code-quality/specifying-when-and-where-an-annotation-applies.md).<br /><br /> Parametr jest dowolnym ciągiem, który pojawia się również `_Function_class_` w adnotacji w deklaracji niektórych funkcji. `name`  `_Called_from_function_class_`Zwraca wartość różną od zera, jeśli funkcja, która jest obecnie analizowana, ma adnotację `_Function_class_` przy użyciu, która ma taką `name`samą wartość; w przeciwnym razie zwraca wartość zero.|
|`_Check_return_`|Adnotuj wartość zwracaną i stwierdza, że obiekt wywołujący powinien go sprawdzić. Kontroler raportuje błąd, jeśli funkcja jest wywoływana w kontekście void.|
|`_Function_class_(name)`|`name` Parametr jest dowolnym ciągiem, który jest wyznaczany przez użytkownika.  Istnieje w przestrzeni nazw, która różni się od innych przestrzeni nazw. Funkcja, wskaźnik funkcji, lub — najbardziej użyteczny — typ wskaźnika funkcji może być wyznaczono jako należące do jednej lub kilku klas funkcji.|
|`_Raises_SEH_exception_`|Adnotuj funkcję, która zawsze zgłasza wyjątek strukturalny programu obsługi wyjątków (SEH), który podlega `_When_` warunkom i `_On_failure_` . Aby uzyskać więcej informacji, zobacz [Określanie, kiedy i gdzie ma zastosowanie adnotacja](../code-quality/specifying-when-and-where-an-annotation-applies.md).|
|`_Maybe_raises_SEH_exception_`|Adnotuj funkcję, która może opcjonalnie podnieść wyjątek SEH, `_When_` co podlega warunkom i. `_On_failure_`|
|`_Must_inspect_result_`|Adnotuj dowolną wartość wyjściową, w tym wartość zwracaną, parametry i Globals.  Analizator raportuje błąd, jeśli wartość w obiekcie z adnotacjami nie jest następnie sprawdzana. "Inspekcja" polega na tym, czy jest używana w wyrażeniu warunkowym, jest przypisywana do parametru wyjściowego lub globalne lub jest przekazywane jako parametr.  Dla zwracanych wartości `_Must_inspect_result_` , `_Check_return_`oznacza.|
|`_Use_decl_annotations_`|Może być używany w definicji funkcji (znanej również jako treść funkcji) zamiast listy adnotacji w nagłówku.  Gdy `_Use_decl_annotations_` jest używany, adnotacje, które pojawiają się w nagłówku w zakresie dla tej samej funkcji, są używane tak, jakby znajdowały się również w definicji zawierającej `_Use_decl_annotations_` adnotację.|

## <a name="successfailure-annotations"></a>Adnotacje sukcesu/niepowodzeń
Funkcja może zakończyć się niepowodzeniem, a gdy tak się stanie, jego wyniki mogą być niekompletne lub inne niż wyniki, gdy funkcja się powiedzie.  Adnotacje na poniższej liście zawierają sposoby wyznaczania zachowania awarii.  Aby użyć tych adnotacji, należy je włączyć, aby określić sukces; w związku z `_Success_` tym wymagana jest adnotacja.  Zwróć uwagę `NTSTATUS` , `HRESULT` że i masz `_Success_` już wbudowaną adnotację, ale jeśli określisz własną `_Success_` adnotację `NTSTATUS` lub `HRESULT`zastąpisz adnotację wbudowaną.

|Adnotacja|Opis|
|----------------|-----------------|
|`_Always_(anno_list)`|Równoważne; oznacza to, że adnotacje w `anno_list` zastosowaniu, czy funkcja się powiedzie. `anno_list _On_failure_(anno_list)`|
|`_On_failure_(anno_list)`|Do użycia tylko wtedy, `_Success_` gdy jest również używany do dodawania adnotacji do funkcji — jawnie lub niejawnie `_Return_type_success_` za pomocą elementu typedef. `_Success_` `expr` `_When_(!expr, anno)` `anno_list` Gdy adnotacja jest obecna w parametrze funkcji lub zwracanej wartości, Każda adnotacja w (Anno) zachowuje się tak, jakby była zakodowana jako parametr, gdzie jest parametru do wymaganej adnotacji. `_On_failure_` Oznacza to, że implikowana aplikacja `_Success_` do wszystkich warunków post nie `_On_failure_`dotyczy.|
|`_Return_type_success_(expr)`|Mogą być stosowane do elementu typedef. Wskazuje, że wszystkie funkcje, które zwracają ten typ i nie są `_Success_` jawnie mają adnotacji, tak `_Success_(expr)`jakby znajdowały się. `_Return_type_success_`nie można użyć dla funkcji ani elementu typedef wskaźnika funkcji.|
|`_Success_(expr)`|`expr`jest wyrażeniem, które zwraca rvalue. Gdy adnotacja jest obecna w deklaracji lub definicji funkcji, Każda adnotacja`anno`() w funkcji i w warunku post zachowuje się tak, jakby była zakodowana `_When_(expr, anno)`jako. `_Success_` `_Success_` Adnotacja może być używana tylko w funkcji, nie na jej parametrach lub zwracanym typie. Może istnieć co najwyżej jedna `_Success_` adnotacja dla funkcji i nie może być `_At_`w żadnej `_When_`z nich,, `_Group_`ani. Aby uzyskać więcej informacji, zobacz [Określanie, kiedy i gdzie ma zastosowanie adnotacja](../code-quality/specifying-when-and-where-an-annotation-applies.md).|

## <a name="see-also"></a>Zobacz także

- [Korzystanie z adnotacji SAL w celu zmniejszenia liczby defektów kodu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Informacje o języku SAL](../code-quality/understanding-sal.md)
- [Dodawanie adnotacji do parametrów funkcji i zwracanych wartości](../code-quality/annotating-function-parameters-and-return-values.md)
- [Dodawanie adnotacji do struktur i klas](../code-quality/annotating-structs-and-classes.md)
- [Dodawanie adnotacji do zachowania blokującego](../code-quality/annotating-locking-behavior.md)
- [Określanie miejsca i warunków stosowania adnotacji](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Funkcje wewnętrzne](../code-quality/intrinsic-functions.md)
- [Najlepsze rozwiązania i przykłady](../code-quality/best-practices-and-examples-sal.md)