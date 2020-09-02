---
title: Raportowanie funkcji punktu zaczepienia | Microsoft Docs
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
ms.openlocfilehash: 0a492a1db8b65cad74d02cec0f43bf0c81461730
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687509"
---
# <a name="report-hook-functions"></a>Raportowanie funkcji punktów zaczepienia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Funkcja podłączania raportów zainstalowana przy użyciu [_CrtSetReportHook](https://msdn.microsoft.com/library/1ae7c64f-8c84-4797-9574-b59f00f7a509)jest wywoływana za każdym razem, gdy [_CrtDbgReport](https://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc) generuje raport debugowania. Można jej używać między innymi w przypadku filtrowania raportów, aby skoncentrować się na określonych typach alokacji. Funkcja punktu zaczepienia raportu powinna mieć prototyp podobny do następującego:  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 Wskaźnik przekazany do **_CrtSetReportHook** jest typu **_CRT_REPORT_HOOK**, zgodnie z definicją w CRTDBG. C  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Gdy Biblioteka wykonawcza wywołuje funkcję Hook, argument *nRptType* zawiera kategorię raportu (**_CRT_WARN**, **_CRT_ERROR**lub **_CRT_ASSERT**), *szMsg* zawiera wskaźnik do w pełni zmontowany ciąg komunikatu raportu, a *retval* określa, czy `_CrtDbgReport` należy kontynuować normalne wykonywanie po wygenerowaniu raportu lub uruchomieniu debugera. (Wartość *retval* zero kontynuuje wykonywanie, A wartość 1 powoduje uruchomienie debugera).  
  
 Jeśli hak przechwytuje komunikat w całości, więc nie jest wymagane żadne dalsze raportowanie, należy zwrócić **wartość true**. Jeśli zwraca **wartość false**, `_CrtDbgReport` będzie zgłaszać komunikat w normalny sposób.  
  
## <a name="see-also"></a>Zobacz też  
 [Zapisywanie funkcji punktu zaczepienia debugowania](../debugger/debug-hook-function-writing.md)   
 [Przykład crt_dbg2](https://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)
