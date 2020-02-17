---
title: Określanie, kiedy i gdzie ma być stosowana adnotacja | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Group_
- _At_
- _When_
- _At_buffer_
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 1eb32aa7d87da75ebf37b27aa1d425adb85f8c9b
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2020
ms.locfileid: "77278456"
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>Określanie warunków pojawiania się adnotacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gdy adnotacja jest warunkowa, może wymagać innych adnotacji, aby określić, że do analizatora.  Na przykład, jeśli funkcja ma zmienną, która może być synchroniczna lub asynchroniczna, funkcja zachowuje się w następujący sposób: w przypadku synchronicznym zawsze kończy się powodzeniem, ale w przypadku asynchronicznym zgłasza błąd, jeśli nie powiedzie się natychmiast. Gdy funkcja jest wywoływana synchronicznie, sprawdzenie wartości wyniku nie zapewnia żadnej wartości dla analizatora kodu, ponieważ nie została zwrócona.  Jeśli jednak funkcja jest wywoływana asynchronicznie, a wynik funkcji nie jest zaznaczony, może wystąpić poważny błąd. Ten przykład ilustruje sytuację, w której można użyć adnotacji `_When_`ej — opisanej w dalszej części tego artykułu — aby włączyć sprawdzanie.  
  
## <a name="structural-annotations"></a>Adnotacje strukturalne  
 Aby określić, kiedy i gdzie mają być stosowane adnotacje, użyj następujących adnotacji strukturalnej.  
  
|Adnotacja|Opis|  
|----------------|-----------------|  
|`_At_(expr, anno-list)`|`expr` jest wyrażeniem, które zwraca lvalue. Adnotacje w `anno-list` są stosowane do obiektu, który jest nazwany przez `expr`. Dla każdej adnotacji w `anno-list`, `expr` jest interpretowany w warunku wstępnym, jeśli adnotacja jest interpretowana jako warunek wstępny, a w warunku post, jeśli adnotacja jest interpretowana w warunku post.|  
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` jest wyrażeniem, które zwraca lvalue. Adnotacje w `anno-list` są stosowane do obiektu, który jest nazwany przez `expr`. Dla każdej adnotacji w `anno-list`, `expr` jest interpretowany w warunku wstępnego, jeśli adnotacja jest interpretowana w warunku wstępnym i w warunku post, jeśli adnotacja jest interpretowana w warunku post.<br /><br /> `iter` to nazwa zmiennej, która jest objęta zakresem adnotacji (włącznie z `anno-list`). `iter` ma `long`typu niejawnego. Zmienne o identycznej nazwie w dowolnym zakresie otaczającym są ukryte przed oszacowaniem.<br /><br /> `elem-count` jest wyrażeniem, którego wynikiem jest liczba całkowita.|  
|`_Group_(anno-list)`|Adnotacje w `anno-list` są uważane za posiadające dowolny kwalifikator odnoszący się do adnotacji grupy stosowanej do każdej adnotacji.|  
|`_When_(expr, anno-list)`|`expr` jest wyrażeniem, które można przekonwertować na `bool`. Jeśli wartość jest różna od zera (`true`), adnotacje określone w `anno-list` są uważane za odpowiednie.<br /><br /> Domyślnie dla każdej adnotacji w `anno-list``expr` jest interpretowana jako użycie wartości wejściowych, jeśli adnotacja jest warunkiem wstępnym, i jako wartość wyjściowa, jeśli adnotacja jest warunkiem post. Aby zastąpić wartość domyślną, można użyć `_Old_` wewnętrznej podczas obliczania warunku końcowego, aby wskazać, że należy użyć wartości wejściowych. **Uwaga:**  Różne adnotacje mogą być włączane jako zgodne z używaniem `_When_`, jeśli modyfikowalna wartość, na przykład `*pLength`— jest uwzględniana, ponieważ wynikiem obliczenia `expr` w warunku wstępnym może być inna różnica od wyniku jego oceny w warunku.|  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z adnotacji sal w celuC++ zmniejszenia wad kodu C/Code](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Zrozumienie  sal](../code-quality/understanding-sal.md)  
 [Dodawanie adnotacji do parametrów funkcji i zwracanych wartości](../code-quality/annotating-function-parameters-and-return-values.md)   
   [zachowanie funkcji dodawania adnotacji](../code-quality/annotating-function-behavior.md)  
 [Dodawanie adnotacji do struktur i klas](../code-quality/annotating-structs-and-classes.md)   
 [Dodawanie adnotacji do zachowania blokowania](../code-quality/annotating-locking-behavior.md)   
 [Funkcje wewnętrzne](../code-quality/intrinsic-functions.md)   
 [Najlepsze rozwiązania i przykłady](../code-quality/best-practices-and-examples-sal.md)
