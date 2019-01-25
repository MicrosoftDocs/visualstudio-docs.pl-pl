---
title: Raport funkcji punktów zaczepienia | Dokumentacja firmy Microsoft
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
- hooks, report
- _CrtDbgReport function
- debugger, report hook functions
- memory allocation, debug heap
- debugging [C++], hook functions
- _CrtSetReportHook function
- report hook functions
ms.assetid: 1854bca7-d7eb-4502-89bf-b1ee64cb50ef
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 38d553abd50d1b5870adc31e08d349f9f84c0579
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54786320"
---
# <a name="report-hook-functions"></a>Raportowanie funkcji punktów zaczepienia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Raport funkcji podłączania zainstalowane za pomocą [_CrtSetReportHook](http://msdn.microsoft.com/library/1ae7c64f-8c84-4797-9574-b59f00f7a509), jest wywoływana za każdym razem [_CrtDbgReport](http://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc) generuje raport debugowania. Używając go, między innymi do filtrowania raportów skoncentrować się na określonych typów alokacji. Funkcja podłączania raport powinien mieć prototypu, jak pokazano poniżej:  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 Wskaźnik, który jest przekazywany do **_CrtSetReportHook** typu **_crt_report_hook —**, zgodnie z definicją w CRTDBG. GODZ.:  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Gdy biblioteka środowiska uruchomieniowego wywołuje funkcję podłączania, *nRptType* argument zawiera kategorii raportu (**_CRT_WARN**, **_CRT_ERROR**, lub **_CRT _ASSERT**), *szMsg* zawiera wskaźnik do ciągu komunikatu zmontowanych raportu, a *retVal* Określa, czy `_CrtDbgReport` powinno być kontynuowane normalnego wykonywania Po wygenerowaniu raportu lub uruchamiania debugera. (A *retVal* o wartości zero kontynuuje wykonywanie, wartość 1 Uruchamia debuger.)  
  
 Jeśli punkt zaczepienia obsługi wiadomości w danym całkowicie, dzięki czemu nie dalsze raportowania są wymagane, powinna zwrócić **TRUE**. Jeśli zostanie zwrócona **FALSE**, `_CrtDbgReport` będzie raportu, komunikat normalnie.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie pisanie funkcji punktów zaczepienia](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 Sample](http://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)
