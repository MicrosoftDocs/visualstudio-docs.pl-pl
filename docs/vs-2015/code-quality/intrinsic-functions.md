---
title: Funkcje wewnętrzne | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _String_length_
- _Param_
- _Curr_
- _Old_
- _Nullterm_length_
- _Inexpressible_
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: a0a6cd31cbc8cf73cfa2c7e9ee7c096fa56799b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77277961"
---
# <a name="intrinsic-functions"></a>Funkcje wewnętrzne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wyrażenie w SAL może być wyrażeniem C/C++, pod warunkiem, że jest wyrażeniem, które nie ma efektów ubocznych — na przykład + +,--, i wywołania funkcji wszystkie mają efekty uboczne w tym kontekście.  Funkcja SAL udostępnia jednak niektóre obiekty podobne do funkcji i niektóre zastrzeżone symbole, które mogą być używane w wyrażeniach SAL. Są one nazywane *funkcjami wewnętrznymi*.  
  
## <a name="general-purpose"></a>Ogólnego przeznaczenia  
 Poniższe adnotacje funkcji instrinsic zapewniają ogólne narzędzie dla SAL.  
  
|Adnotacja|Opis|  
|----------------|-----------------|  
|`_Curr_`|Synonim dla obiektu, który jest aktualnie dodawany do adnotacji.  Gdy `_At_` adnotacja jest używana, `_Curr_` jest taka sama jak pierwszy parametr do `_At_` .  W przeciwnym razie jest to parametr lub cała funkcja/wartość zwracana, z którą adnotacja jest w sposób leksykalny.|  
|`_Inexpressible_(expr)`|Wyraża sytuację, w której rozmiar buforu jest zbyt złożony do reprezentowania przy użyciu wyrażenia adnotacji — na przykład, kiedy jest obliczany przez skanowanie zestawu danych wejściowych, a następnie liczenie wybranych elementów członkowskich.|  
|`_Nullterm_length_(param)`|`param` to liczba elementów w buforze, do których nie dołączany jest terminator o wartości null. Może być zastosowany do dowolnego buforu typu innego niż "void".|  
|`_Old_(expr)`|Gdy jest oceniana w warunku wstępnym, `_Old_` zwraca wartość wejściową `expr` .  Gdy jest oceniane w warunku post, zwraca wartość, `expr` ponieważ zostałaby oceniona w warunku wstępnym.|  
|`_Param_(n)`|`n`Parametr do funkcji, zliczanie od 1 do `n` , i `n` jest stałą całkowitą literału. Jeśli parametr ma nazwę, ta adnotacja jest taka sama, aby uzyskać dostęp do parametru według nazwy. **Uwaga:** `n` może odwoływać się do parametrów pozycyjnych, które są zdefiniowane przez wielokropek lub mogą być używane w prototypach funkcji, gdzie nazwy nie są używane.  |  
|`return`|Zastrzeżone słowo kluczowe języka C/C++ `return` może być używane w wyrażeniu sal do wskazywania wartości zwracanej funkcji.  Wartość jest dostępna tylko w stanie post; jest to błąd składniowy, aby używać go w stanie sprzed.|  
  
## <a name="string-specific"></a>Określony ciąg  
 Poniższe adnotacje funkcji wewnętrznych umożliwiają manipulowanie ciągami. Wszystkie cztery z tych funkcji służą tego samego celu: aby zwrócić liczbę elementów typu znalezionych przed terminatorem o wartości null. Różnice to rodzaje danych w elementach, do których odwołują się. Należy pamiętać, że jeśli chcesz określić długość bufora zakończono znakiem null, który nie zawiera znaków, użyj `_Nullterm_length_(param)` adnotacji z poprzedniej sekcji.  
  
|Adnotacja|Opis|  
|----------------|-----------------|  
|`_String_length_(param)`|`param` to liczba elementów w ciągu, które nie obejmują terminatora null. Ta adnotacja jest zarezerwowana dla typów ciągów znaków.|  
|`strlen(param)`|`param` to liczba elementów w ciągu, które nie obejmują terminatora null. Ta adnotacja jest zarezerwowana do użycia w tablicach znaków i przypomina funkcję środowiska uruchomieniowego C [strlen ()](https://msdn.microsoft.com/library/16462f2a-1e0f-4eb3-be55-bf1c83f374c2).|  
|`wcslen(param)`|`param` jest liczbą elementów w ciągu do (ale nie obejmuje) terminatora o wartości null. Ta adnotacja jest zarezerwowana do użycia w tablicach o szerokim znaku i przypomina funkcję środowiska uruchomieniowego C [wcslen ()](https://msdn.microsoft.com/library/16462f2a-1e0f-4eb3-be55-bf1c83f374c2).|  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z adnotacji SAL w celu zmniejszenia wad kodu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Zrozumienie SAL](../code-quality/understanding-sal.md)   
 [Dodawanie adnotacji do parametrów funkcji i zwracanych wartości](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Zachowanie funkcji dodawania adnotacji](../code-quality/annotating-function-behavior.md)   
 [Dodawanie adnotacji do struktur i klas](../code-quality/annotating-structs-and-classes.md)   
 [Dodawanie adnotacji do zachowania blokowania](../code-quality/annotating-locking-behavior.md)   
 [Określanie momentu i miejsca zastosowania adnotacji](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Najlepsze rozwiązania i przykłady](../code-quality/best-practices-and-examples-sal.md)
