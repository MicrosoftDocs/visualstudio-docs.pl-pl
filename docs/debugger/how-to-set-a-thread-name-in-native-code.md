---
title: 'Instrukcje: Ustawianie nazw wątków w kodzie natywnym | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 12/17/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [C++], threads
- SetThreadName function
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c85d0968-9f22-4d69-87f4-acca2ae777b8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 9226e009936d0a644a5a6fcfcaba57bc3af25d7d
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/27/2018
ms.locfileid: "53803101"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>Instrukcje: Ustawianie nazw wątków w kodzie natywnym
Nazwy wątków jest możliwe w dowolnej wersji programu Visual Studio. Nazewnictwo wątku jest przydatne do śledzenia wątków w **wątków** okna.

## <a name="set-a-thread-name"></a>Ustawianie nazw wątków

`SetThreadName` Funkcja jest przydatna do ustawiania i wyświetlania wątków, jeśli debuger jest dołączony do uruchomionej kodu. Począwszy od programu Visual Studio 2017 w wersji 15.6, możesz użyć [SetThreadDescription](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription) funkcję, aby ustawić i wyświetlić nazwy wątków.

```C++
#include <windows.h>
#include <processthreadsapi.h>

int main()
{
    HRESULT r;
    r = SetThreadDescription(
        GetCurrentThread(),
        L"ThisIsMyThreadName!"
    );

    return 0;
}
```

## <a name="set-a-thread-name-using-setthreadname"></a>Ustawianie nazw wątków przy użyciu setthreadname —

Aby Ustawianie nazw wątków w swoim programie, można także użyć `SetThreadName` funkcji, jak pokazano w poniższym przykładzie kodu. Należy pamiętać, że nazwa wątku jest kopiowany do wątku, aby pamięć `threadName` parametru może być zwolnione.  Ta metoda używa podejście oparte na wyjątek tylko wtedy, gdy debuger jest dołączony w czasie, stosuje się metodę opartą na wyjątkach. Nazwa wątku, który został ustawiony, za pomocą tej metody nie będą dostępne w zrzuty lub narzędzi do analizy wydajności.

Poniższy przykład kodu pokazuje sposób użycia `SetThreadName`:

```C++
//  
// Usage: SetThreadName ((DWORD)-1, "MainThread");  
//  
#include <windows.h>  
const DWORD MS_VC_EXCEPTION = 0x406D1388;  
#pragma pack(push,8)  
typedef struct tagTHREADNAME_INFO  
{  
    DWORD dwType; // Must be 0x1000.  
    LPCSTR szName; // Pointer to name (in user addr space).  
    DWORD dwThreadID; // Thread ID (-1=caller thread).  
    DWORD dwFlags; // Reserved for future use, must be zero.  
 } THREADNAME_INFO;  
#pragma pack(pop)  
void SetThreadName(DWORD dwThreadID, const char* threadName) {  
    THREADNAME_INFO info;  
    info.dwType = 0x1000;  
    info.szName = threadName;  
    info.dwThreadID = dwThreadID;  
    info.dwFlags = 0;  
#pragma warning(push)  
#pragma warning(disable: 6320 6322)  
    __try{  
        RaiseException(MS_VC_EXCEPTION, 0, sizeof(info) / sizeof(ULONG_PTR), (ULONG_PTR*)&info);  
    }  
    __except (EXCEPTION_EXECUTE_HANDLER){  
    }  
#pragma warning(pop)  
}  
```  

## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)   
 [Instrukcje: Ustawianie nazw wątków w kodzie zarządzanym](../debugger/how-to-set-a-thread-name-in-managed-code.md)