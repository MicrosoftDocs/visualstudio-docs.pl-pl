---
title: Punkty zaczepienia alokacji i alokacje pamięci w czasie wykonywania C | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8487972c237b9c2ba6bf2594ffc1df43fa0c63cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702433"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Punkty zaczepienia alokacji i alokacja pamięci środowiska wykonawczego języka C
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bardzo ważne ograniczenie dotyczące funkcji punktu zaczepienia alokacji polega na tym, że muszą jawnie ignorować `_CRT_BLOCK` bloki (alokacje pamięci wykonane wewnętrznie przez funkcje biblioteki wykonawczej c), jeśli wykonają jakiekolwiek wywołania funkcji biblioteki wykonawczej języka c, które przydzielą pamięć wewnętrzną. `_CRT_BLOCK`Bloki można zignorować przez dołączenie kodu, takiego jak poniższy na początku funkcji punktu zaczepienia alokacji:  
  
```  
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 Jeśli punkt zaczepienia alokacji nie ignoruje `_CRT_BLOCK` bloków, wówczas każda funkcja biblioteki wykonawczej języka C wywołana w urządzeniu Hook może Zalewka programu w pętli nieskończonej. Na przykład program `printf` tworzy wewnętrzną alokację. Jeśli kod punktu zaczepienia wywołuje `printf` , wówczas przydzielone przypisanie spowoduje ponowne wywołanie punktu zaczepienia, który będzie ponownie wywoływał **printf** i tak dalej, aż stos przepływa. Jeśli trzeba zgłosić `_CRT_BLOCK` operacje alokacji, jednym ze sposobów obejścia tego ograniczenia jest użycie funkcji interfejsu API systemu Windows, a nie funkcji w czasie wykonywania w języku C do formatowania i wyjścia. Ponieważ interfejsy API systemu Windows nie używają sterty biblioteki wykonawczej C, nie będą zalewkować punktu zaczepienia alokacji w pętli nieskończonej.  
  
 Jeśli sprawdzisz pliki źródłowe biblioteki wykonawczej, zobaczysz, że domyślna funkcja punktu zaczepienia alokacji, **CrtDefaultAllocHook** (która po prostu zwraca **wartość true**), znajduje się w osobnym pliku, DBGHOOK. C. Jeśli chcesz, aby punkt zaczepienia alokacji był wywoływany nawet w przypadku alokacji dokonanych przez kod uruchomienia w czasie wykonywania, który jest wykonywany przed **główną** funkcją aplikacji, możesz zastąpić tę funkcję domyślną, zamiast korzystać z [_CrtSetAllocHook](https://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d).  
  
## <a name="see-also"></a>Zobacz też  
 [Zapisywanie funkcji punktu zaczepienia debugowania](../debugger/debug-hook-function-writing.md)   
 [Przykład crt_dbg2](https://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)
