---
title: 'Instrukcje: Ustawianie nazw wątków w kodzie natywnym | Dokumentacja firmy Microsoft'
ms.date: 12/17/2018
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 264ac57a0d159b9cdd2627d7a62372fa070e31de
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56715183"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>Instrukcje: Ustawianie nazw wątków w kodzie natywnym
Nazwy wątków jest możliwe w dowolnej wersji programu Visual Studio. Wątek nazewnictwa jest przydatny do identyfikowania wątków zainteresowanie **wątków** okna podczas debugowania uruchomionego procesu. Posiadanie uznane o silnych nazwach wątków przydatne może być również podczas wykonywania po zakończeniu działania debugowania za pomocą inspekcji zrzutu awaryjnego i analizowania wydajności przechwytuje przy użyciu różnych narzędzi.

## <a name="ways-to-set-a-thread-name"></a>Sposoby Ustawianie nazw wątków

Istnieją dwa sposoby Ustawianie nazw wątków. Pierwsza to za pośrednictwem [SetThreadDescription](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription) funkcji. Druga polega na określony wyjątek zostanie zgłoszony, gdy debuger programu Visual Studio jest dołączony do procesu. Każde podejście ma zalety i ostrzeżenia.

Warto zauważyć, że _zarówno_ podejścia można ze sobą, jeśli to konieczne, ponieważ mechanizmy, według których pracują są niezależne od siebie nawzajem.

### <a name="set-a-thread-name-by-using-setthreaddescription"></a>Ustawianie nazw wątków przy użyciu `SetThreadDescription`

Korzyści:
* Nazwy wątków są widoczne podczas debugowania w programie Visual Studio, niezależnie od tego, czy debuger został dołączony do procesu w czasie, które jest wywoływane SetThreadDescription.
* Nazwy wątków są widoczne podczas przeprowadzania późniejszej debugowania, ładując zrzut awaryjny w programie Visual Studio.
* Nazwy wątków również są widoczne, gdy przy użyciu innych narzędzi, takich jak [WinDbg](https://docs.microsoft.com/windows-hardware/drivers/debugger/debugger-download-tools) debugera i [Analizator wydajności Windows](https://docs.microsoft.com/windows-hardware/test/wpt/windows-performance-analyzer) Analizator wydajności.

Ostrzeżenia:
* Nazwy wątków są tylko widoczne w programie Visual Studio 2017 w wersji 15.6 i nowsze.
* Gdy plik zrzutu po zakończeniu działania debugowania awarii, nazwy wątku są widoczne tylko w przypadku awarii został utworzony w systemie Windows 10 w wersji 1607, Windows Server 2016 lub nowszych wersjach systemu Windows.

*Przykład:*

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

### <a name="set-a-thread-name-by-throwing-an-exception"></a>Ustawianie nazw wątków, zostanie zgłoszony wyjątek

Innym sposobem na Ustawianie nazw wątków w programie służy do przekazywania nazwa żądanego wątku do debugera programu Visual Studio, zgłaszając wyjątek specjalnie skonfigurować.

Korzyści:
* Działa we wszystkich wersjach programu Visual Studio.

Ostrzeżenia:
* Tylko wtedy, gdy debuger jest dołączony w czasie, stosuje się metodę opartą na wyjątkach.
* Nazwy wątków ustawiane przez przy użyciu tej metody nie będą dostępne w zrzuty lub narzędzi do analizy wydajności.

*Przykład:*

`SetThreadName` Funkcja poniżej przedstawiono to podejście oparte na wyjątek. Należy pamiętać, że nazwa wątku będą automatycznie skopiowane do wątku, tak aby pamięci dla `threadName` parametru może być zwolnione po `SetThreadName` ukończenie wywołania.

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
- [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)
- [Instrukcje: Ustawianie nazwy wątku w kodzie zarządzanym](../debugger/how-to-set-a-thread-name-in-managed-code.md)
