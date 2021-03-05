---
description: Uruchamia plik wykonywalny.
title: 'IDebugPortEx2:: LaunchSuspended | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b5982ad665333aa4d11e2098d3b148db88e77c32
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142831"
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
podczas Nazwa pliku wykonywalnego, który ma zostać uruchomiony. Może to być pełna ścieżka lub względem katalogu roboczego określonego w `pszDir` parametrze.

`pszArgs`\
podczas Argumenty do przekazania do pliku wykonywalnego. Może mieć wartość null, jeśli nie ma żadnych argumentów.

`pszDir`\
podczas Nazwa katalogu roboczego używanego przez plik wykonywalny. Może mieć wartość null, jeśli nie jest wymagany żaden katalog roboczy.

`bstrEnv`\
podczas Blok środowiska ciągów zakończonych wartością null, a po nim dodatkowy terminator o wartości null.

`hStdInput`\
podczas Dojście do alternatywnego strumienia wejściowego. Może mieć wartość 0, jeśli przekierowanie nie jest wymagane.

`hStdOutput`\
podczas Dojście do alternatywnego strumienia wyjściowego. Może mieć wartość 0, jeśli przekierowanie nie jest wymagane.

`hStdError`\
podczas Dojście do alternatywnego strumienia wyjściowego błędu. Może mieć wartość 0, jeśli przekierowanie nie jest wymagane.

`ppPortProcess`\
określoną Zwraca obiekt [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) , który reprezentuje uruchomiony proces.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda powinna uruchamiać proces w taki sposób, aby był wstrzymany i nie był uruchomiony żaden kod. Metoda [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) jest wywoływana w celu wznowienia procesu.

 Program może być również uruchamiany z aparatu debugowania. Aby uzyskać szczegółowe informacje, zobacz [Uruchamianie programu](../../../extensibility/debugger/launching-a-program.md).

## <a name="see-also"></a>Zobacz też
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)
- [Uruchamianie programu](../../../extensibility/debugger/launching-a-program.md)
