---
title: 'Instrukcje: Ustawianie nazwy wątku w kodzie natywnym | Microsoft Docs'
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
ms.openlocfilehash: 1f9df52bee88722006c21c28e88a2e32113942e4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72732756"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>Porady: ustawianie nazw wątków w kodzie natywnym
Nazewnictwo wątków jest możliwe w dowolnej wersji programu Visual Studio. Nazewnictwo wątków jest przydatne do identyfikowania wątków interesujących w oknie **wątków** podczas debugowania uruchomionego procesu. Mając rozpoznawalne i nazwane wątki mogą być również pomocne podczas przeprowadzania debugowania po awarii przez inspekcję zrzutów awaryjnych i podczas analizowania przechwytywania wydajności przy użyciu różnych narzędzi.

## <a name="ways-to-set-a-thread-name"></a>Sposoby ustawiania nazwy wątku

Istnieją dwa sposoby ustawiania nazwy wątku. Pierwszy jest za pośrednictwem funkcji [SetThreadDescription](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription) . Drugi polega na wyrzucaniu określonego wyjątku podczas dołączania debugera programu Visual Studio do procesu. Każde podejście ma zalety i zastrzeżenia. Korzystanie z `SetThreadDescription` jest obsługiwane począwszy od systemu Windows 10, w wersji 1607 lub Windows Server 2016.

Należy zauważyć, że _oba_ podejścia mogą być używane razem, w razie potrzeby, ponieważ mechanizmy, za pomocą których działają, są niezależne od siebie.

### <a name="set-a-thread-name-by-using-setthreaddescription"></a>Ustaw nazwę wątku za pomocą `SetThreadDescription`

Korzysta
* Nazwy wątków są widoczne podczas debugowania w programie Visual Studio, niezależnie od tego, czy debuger został dołączony do procesu w momencie wywołania SetThreadDescription.
* Nazwy wątków są widoczne podczas przeprowadzania debugowania po załadowaniu zrzutu awaryjnego w programie Visual Studio.
* Nazwy wątków są również widoczne w przypadku korzystania z innych narzędzi, takich jak program [WinDbg](https://docs.microsoft.com/windows-hardware/drivers/debugger/debugger-download-tools) Debugger i Analizator wydajności [Analizator wydajności systemu Windows](https://docs.microsoft.com/windows-hardware/test/wpt/windows-performance-analyzer) .

Zastrzeżenia
* Nazwy wątków są widoczne tylko w programie Visual Studio 2017 w wersji 15,6 i nowszych.
* Po zakończeniu debugowania pliku zrzutu awaryjnego nazwy wątków są widoczne tylko wtedy, gdy awaria została utworzona w systemie Windows 10 w wersji 1607, Windows Server 2016 lub nowszych wersjach systemu Windows.

*Przyklad*

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

### <a name="set-a-thread-name-by-throwing-an-exception"></a>Ustaw nazwę wątku, zgłaszając wyjątek

Innym sposobem ustawienia nazwy wątku w programie jest komunikowanie się żądanej nazwy wątku z debugerem programu Visual Studio przez wygenerowanie specjalnie skonfigurowanego wyjątku.

Korzysta
* Działa we wszystkich wersjach programu Visual Studio.

Zastrzeżenia
* Działa tylko wtedy, gdy debuger jest dołączony w momencie użycia metody opartej na wyjątku.
* Nazwy wątków ustawiane za pomocą tej metody nie będą dostępne w narzędziach zrzutów lub analizy wydajności.

*Przyklad*

Funkcja `SetThreadName` pokazana poniżej demonstruje takie podejście oparte na wyjątkach. Należy zauważyć, że nazwa wątku zostanie automatycznie skopiowana do wątku, dzięki czemu pamięć dla parametru `threadName` może zostać wydana po zakończeniu wywołania `SetThreadName`.

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

## <a name="see-also"></a>Zobacz także
- [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)
- [Instrukcje: ustawianie nazw wątków w kodzie zarządzanym](../debugger/how-to-set-a-thread-name-in-managed-code.md)
