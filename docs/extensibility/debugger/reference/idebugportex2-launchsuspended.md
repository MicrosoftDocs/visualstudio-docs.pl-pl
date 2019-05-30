---
title: IDebugPortEx2::LaunchSuspended | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 94810761e546b0cae9eca32fc76bc0bfd396c7e7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311118"
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
[in] Nazwa pliku wykonywalnego do uruchomienia. Może to być pełna ścieżka lub względna do katalogu roboczego, określone w `pszDir` parametru.

`pszArgs`\
[in] Argumenty do przekazania do pliku wykonywalnego. Może być wartością null, jeśli nie wymaga argumentów.

`pszDir`\
[in] Nazwa katalogu roboczego używane przez plik wykonywalny. Może być wartością null, jeśli katalog roboczy nie jest wymagana.

`bstrEnv`\
[in] Blok środowiska ciągów zakończony znakiem null, następuje dodatkowe terminator o wartości NULL.

`hStdInput`\
[in] Dojście do alternatywnego strumienia wejściowego. Może być równa 0, jeśli przekierowanie nie jest wymagana.

`hStdOutput`\
[in] Dojście do strumienia wyjściowego alternatywne. Może być równa 0, jeśli przekierowanie nie jest wymagana.

`hStdError`\
[in] Dojście do błędu alternatywnego strumienia wyjściowego. Może być równa 0, jeśli przekierowanie nie jest wymagana.

`ppPortProcess`\
[out] Zwraca [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) obiekt, który reprezentuje uruchomienie procesu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda powinna Uruchom proces, że jest zawieszony, a nie działa każdy kod. [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) metoda jest wywoływana, aby wznowić proces.

 Program można także uruchomić z aparatu debugowania. Aby uzyskać więcej informacji, zobacz [uruchamianie programu](../../../extensibility/debugger/launching-a-program.md).

## <a name="see-also"></a>Zobacz także
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)
- [Uruchamianie programu](../../../extensibility/debugger/launching-a-program.md)