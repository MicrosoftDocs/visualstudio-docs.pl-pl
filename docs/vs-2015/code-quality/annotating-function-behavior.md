---
title: Zachowanie funkcji dodawania adnotacji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
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
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 7ebda5933f73e2511932f8968104327a56ee7606
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2020
ms.locfileid: "77277870"
---
# <a name="annotating-function-behavior"></a>Zachowanie funkcji dodawania adnotacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Oprócz dodawania adnotacji do [parametrów funkcji i zwracanych wartości](../code-quality/annotating-function-parameters-and-return-values.md)można dodawać adnotacje do właściwości całej funkcji.  
  
## <a name="function-annotations"></a>Adnotacje funkcji  
 Poniższe adnotacje odnoszą się do funkcji jako całości i opisują sposób jej działania lub przewidywane znaczenie.  
  
|Adnotacja|Opis|  
|----------------|-----------------|  
|`_Called_from_function_class_(name)`|Nie przeznaczony do autonomicznego; Zamiast tego jest predykatem, który ma być używany z adnotacją `_When_`. Aby uzyskać więcej informacji, zobacz [Określanie, kiedy i gdzie ma zastosowanie adnotacja](../code-quality/specifying-when-and-where-an-annotation-applies.md).<br /><br /> `name` parametr to dowolny ciąg, który pojawia się również w adnotacji `_Function_class_` w deklaracji niektórych funkcji.  `_Called_from_function_class_` zwraca wartość różną od zera, jeśli funkcja, która jest obecnie analizowana, ma adnotację przy użyciu `_Function_class_` o tej samej wartości `name`; w przeciwnym razie zwraca wartość zero.|  
|`_Check_return_`|Adnotuj wartość zwracaną i stwierdza, że obiekt wywołujący powinien go sprawdzić. Kontroler raportuje błąd, jeśli funkcja jest wywoływana w kontekście void.|  
|`_Function_class_(name)`|`name` parametr to dowolny ciąg, który jest wyznaczyny przez użytkownika.  Istnieje w przestrzeni nazw, która różni się od innych przestrzeni nazw. Funkcja, wskaźnik funkcji, lub — najbardziej użyteczny — typ wskaźnika funkcji może być wyznaczono jako należące do jednej lub kilku klas funkcji.|  
|`_Raises_SEH_exception_`|Adnotuj funkcję, która zawsze zgłasza wyjątek strukturalny programu obsługi wyjątków (SEH), z zastrzeżeniem `_When_` i `_On_failure_` warunków. Aby uzyskać więcej informacji, zobacz [Określanie, kiedy i gdzie ma zastosowanie adnotacja](../code-quality/specifying-when-and-where-an-annotation-applies.md).|  
|`_Maybe_raises_SEH_exception_`|Adnotuj funkcję, która może opcjonalnie podnieść wyjątek SEH, z zastrzeżeniem `_When_` i `_On_failure_` warunków.|  
|`_Must_inspect_result_`|Adnotuj dowolną wartość wyjściową, w tym wartość zwracaną, parametry i Globals.  Analizator raportuje błąd, jeśli wartość w obiekcie z adnotacjami nie jest następnie sprawdzana. "Inspekcja" polega na tym, czy jest używana w wyrażeniu warunkowym, jest przypisywana do parametru wyjściowego lub globalne lub jest przekazywane jako parametr.  Dla wartości zwracanych `_Must_inspect_result_` oznacza `_Check_return_`.|  
|`_Use_decl_annotations_`|Może być używany w definicji funkcji (znanej również jako treść funkcji) zamiast listy adnotacji w nagłówku.  Gdy `_Use_decl_annotations_` jest używany, adnotacje, które pojawiają się w nagłówku w zakresie dla tej samej funkcji, są używane tak, jakby znajdowały się również w definicji zawierającej adnotację `_Use_decl_annotations_`.|  
  
## <a name="successfailure-annotations"></a>Adnotacje sukcesu/niepowodzeń  
 Funkcja może zakończyć się niepowodzeniem, a gdy tak się stanie, jego wyniki mogą być niekompletne lub inne niż wyniki, gdy funkcja się powiedzie.  Adnotacje na poniższej liście zawierają sposoby wyznaczania zachowania awarii.  Aby użyć tych adnotacji, należy je włączyć, aby określić sukces; w związku z tym wymagana jest adnotacja `_Success_`.  Zwróć uwagę, że `NTSTATUS` i `HRESULT` mają już wbudowaną adnotację `_Success_`. Jeśli jednak określisz własną adnotację `_Success_` na `NTSTATUS` lub `HRESULT`, zastępuje ona wbudowaną adnotację.  
  
|Adnotacja|Opis|  
|----------------|-----------------|  
|`_Always_(anno_list)`|Równoważne `anno_list _On_failure_(anno_list)`; oznacza to, że adnotacje w `anno_list` mają zastosowanie, czy funkcja się powiedzie.|  
|`_On_failure_(anno_list)`|Ma być używany tylko wtedy, gdy `_Success_` jest również używany do dodawania adnotacji do funkcji — jawnie lub niejawnie za pomocą `_Return_type_success_` na podstawie elementu typedef. Gdy adnotacja `_On_failure_` jest obecna w parametrze funkcji lub wartości zwracanej, Każda adnotacja w `anno_list` (Anno) zachowuje się tak, jakby była zakodowana jako `_When_(!expr, anno)`, gdzie `expr` jest parametrem wymaganej adnotacji `_Success_`. Oznacza to, że implikowane zastosowanie `_Success_` do wszystkich warunków post nie ma zastosowania do `_On_failure_`.|  
|`_Return_type_success_(expr)`|Mogą być stosowane do elementu typedef. Wskazuje, że wszystkie funkcje, które zwracają ten typ i nie mają jawnie `_Success_` są adnotacje, tak jakby były `_Success_(expr)`. nie można użyć `_Return_type_success_` dla funkcji lub elementu typedef wskaźnika funkcji.|  
|`_Success_(expr)`|`expr` jest wyrażeniem, które zwraca rvalue. Gdy adnotacja `_Success_` jest obecna w deklaracji lub definicji funkcji, Każda adnotacja (`anno`) w funkcji i w warunku post zachowuje się tak, jakby była zakodowana jako `_When_(expr, anno)`. Adnotacja `_Success_` może być używana tylko w funkcji, nie na jej parametrach lub zwracanym typie. Może istnieć co najwyżej jedna `_Success_` adnotacji w funkcji i nie może ona być w żadnym `_When_`, `_At_`lub `_Group_`. Aby uzyskać więcej informacji, zobacz [Określanie, kiedy i gdzie ma zastosowanie adnotacja](../code-quality/specifying-when-and-where-an-annotation-applies.md).|  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z adnotacji sal w celuC++ zmniejszenia wad kodu C/Code](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Zrozumienie  sal](../code-quality/understanding-sal.md)  
 [Dodawanie adnotacji do parametrów funkcji i zwracanych wartości](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Dodawanie adnotacji do struktur i klas](../code-quality/annotating-structs-and-classes.md)   
 [Dodawanie adnotacji do zachowania blokowania](../code-quality/annotating-locking-behavior.md)   
 [Określanie, kiedy i gdzie ma być stosowana adnotacja](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Funkcje wewnętrzne](../code-quality/intrinsic-functions.md)   
 [Najlepsze rozwiązania i przykłady](../code-quality/best-practices-and-examples-sal.md)
