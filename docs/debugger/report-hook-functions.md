---
title: Raport funkcji punktów zaczepienia | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- hooks, report
- _CrtDbgReport function
- debugger, report hook functions
- memory allocation, debug heap
- debugging [C++], hook functions
- _CrtSetReportHook function
- report hook functions
ms.assetid: 1854bca7-d7eb-4502-89bf-b1ee64cb50ef
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ce84105fa1a3d7bf5c6f949421b306b5147368a5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53892358"
---
# <a name="report-hook-functions"></a>Raportowanie funkcji punktów zaczepienia
Raport funkcji podłączania zainstalowane za pomocą [_CrtSetReportHook](/cpp/c-runtime-library/reference/crtsetreporthook), jest wywoływana za każdym razem [_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) generuje raport debugowania. Używając go, między innymi do filtrowania raportów skoncentrować się na określonych typów alokacji. Funkcja podłączania raport powinien mieć prototypu, jak pokazano poniżej:  
  
```cpp
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 Wskaźnik, który jest przekazywany do **_CrtSetReportHook** typu **_crt_report_hook —**, zgodnie z definicją w CRTDBG. GODZ.:  
  
```cpp
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Gdy biblioteka środowiska uruchomieniowego wywołuje funkcję podłączania, *nRptType* argument zawiera kategorii raportu (**_CRT_WARN**, **_CRT_ERROR**, lub **_CRT _ASSERT**), *szMsg* zawiera wskaźnik do ciągu komunikatu zmontowanych raportu, a *retVal* Określa, czy `_CrtDbgReport` powinno być kontynuowane normalnego wykonywania Po wygenerowaniu raportu lub uruchamiania debugera. (A *retVal* o wartości zero kontynuuje wykonywanie, wartość 1 Uruchamia debuger.)  
  
 Jeśli punkt zaczepienia obsługi wiadomości w danym całkowicie, dzięki czemu nie dalsze raportowania są wymagane, powinna zwrócić **TRUE**. Jeśli zostanie zwrócona **FALSE**, `_CrtDbgReport` będzie raportu, komunikat normalnie.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie pisanie funkcji punktów zaczepienia](../debugger/debug-hook-function-writing.md)   
 [Przykładowe crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)
