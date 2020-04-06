---
title: IDebugPortEx2::UruchomienieSpuspended | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 28ff6065bbe83852b5acc3ffe253a0bdabcc67ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725099"
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
Uruchamia plik wykonywalny.

## <a name="syntax"></a>Składnia

```cpp
HRESULT LaunchSuspended( 
   LPCOLESTR        pszExe,
   LPCOLESTR        pszArgs,
   LPCOLESTR        pszDir,
   BSTR             bstrEnv,
   DWORD            hStdInput,
   DWORD            hStdOutput,
   DWORD            hStdError,
   IDebugProcess2** ppPortProcess
);
```

```csharp
int LaunchSuspended( 
   string             pszExe,
   string             pszArgs,
   string             pszDir,
   string             bstrEnv,
   uint               hStdInput,
   uint               hStdOutput,
   uint               hStdError,
   out IDebugProcess2 ppPortProcess
);
```

## <a name="parameters"></a>Parametry
`pszExe`\
[w] Nazwa pliku wykonywalnego, który ma zostać uruchomiony. Może to być pełna ścieżka lub względem katalogu `pszDir` roboczego określonego w parametrze.

`pszArgs`\
[w] Argumenty, aby przejść do pliku wykonywalnego. Może być wartością null, jeśli nie ma żadnych argumentów.

`pszDir`\
[w] Nazwa katalogu roboczego używanego przez plik wykonywalny. Może to być wartość null, jeśli nie jest wymagany żaden katalog roboczy.

`bstrEnv`\
[w] Blok środowiska ciągów zakończonych wartościami null, po którym następuje dodatkowy terminator NULL.

`hStdInput`\
[w] Dojście do alternatywnego strumienia wejściowego. Może być 0, jeśli przekierowanie nie jest wymagane.

`hStdOutput`\
[w] Dojście do alternatywnego strumienia wyjściowego. Może być 0, jeśli przekierowanie nie jest wymagane.

`hStdError`\
[w] Obsługa strumienia wyjściowego błędu alternatywnego. Może być 0, jeśli przekierowanie nie jest wymagane.

`ppPortProcess`\
[na zewnątrz] Zwraca obiekt [IDebugPendingBreakpoint2,](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) który reprezentuje uruchomiony proces.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda powinna uruchomić proces, tak aby został zawieszony i nie uruchamiał żadnego kodu. Metoda [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) jest wywoływana, aby wznowić proces.

 Program można również uruchamiać z aparatu debugowania. Aby uzyskać szczegółowe informacje, zobacz [Uruchamianie programu](../../../extensibility/debugger/launching-a-program.md).

## <a name="see-also"></a>Zobacz też
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)
- [Uruchamianie programu](../../../extensibility/debugger/launching-a-program.md)
