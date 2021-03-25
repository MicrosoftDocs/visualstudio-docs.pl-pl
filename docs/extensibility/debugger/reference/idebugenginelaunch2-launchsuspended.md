---
description: Ta metoda uruchamia proces za pomocą aparatu debugowania (Niemcy).
title: 'IDebugEngineLaunch2:: LaunchSuspended | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2db2ce2a35cd8be6599fca3e01bc69a6680012b2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066025"
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
Ta metoda uruchamia proces za pomocą aparatu debugowania (Niemcy).

## <a name="syntax"></a>Składnia

```cpp
HRESULT LaunchSuspended ( 
   LPCOLESTR             pszMachine,
   IDebugPort2*          pPort,
   LPCOLESTR             pszExe,
   LPCOLESTR             pszArgs,
   LPCOLESTR             pszDir,
   BSTR                  bstrEnv,
   LPCOLESTR             pszOptions,
   LAUNCH_FLAGS          dwLaunchFlags,
   DWORD                 hStdInput,
   DWORD                 hStdOutput,
   DWORD                 hStdError,
   IDebugEventCallback2* pCallback,
   IDebugProcess2**      ppDebugProcess
);
```

```csharp
int LaunchSuspended(
   string               pszServer,
   IDebugPort2          pPort,
   string               pszExe,
   string               pszArgs,
   string               pszDir,
   string               bstrEnv,
   string               pszOptions,
   enum_LAUNCH_FLAGS    dwLaunchFlags,
   uint                 hStdInput,
   uint                 hStdOutput,
   uint                 hStdError,
   IDebugEventCallback2 pCallback,
   out IDebugProcess2   ppProcess
);
```

## <a name="parameters"></a>Parametry
`pszMachine`\
podczas Nazwa komputera, na którym ma zostać uruchomiony proces. Użyj wartości null, aby określić komputer lokalny.

`pPort`\
podczas Interfejs [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) reprezentujący port, w którym program będzie uruchamiany.

`pszExe`\
podczas Nazwa pliku wykonywalnego, który ma zostać uruchomiony.

`pszArgs`\
podczas Argumenty do przekazania do pliku wykonywalnego. Może mieć wartość null, jeśli nie ma żadnych argumentów.

`pszDir`\
podczas Nazwa katalogu roboczego używanego przez plik wykonywalny. Może mieć wartość null, jeśli nie jest wymagany żaden katalog roboczy.

`bstrEnv`\
podczas Blok środowiska ciągów zakończonych wartością NULL, a po nim dodatkowy terminator o wartości null.

`pszOptions`\
podczas Opcje dla pliku wykonywalnego.

`dwLaunchFlags`\
podczas Określa [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) sesji.

`hStdInput`\
podczas Dojście do alternatywnego strumienia wejściowego. Może mieć wartość 0, jeśli przekierowanie nie jest wymagane.

`hStdOutput`\
podczas Dojście do alternatywnego strumienia wyjściowego. Może mieć wartość 0, jeśli przekierowanie nie jest wymagane.

`hStdError`\
podczas Dojście do alternatywnego strumienia wyjściowego błędu. Może mieć wartość 0, jeśli przekierowanie nie jest wymagane.

`pCallback`\
podczas Obiekt [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , który odbiera zdarzenia debugera.

`ppDebugProcess`\
określoną Zwraca wynikowy obiekt [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , który reprezentuje uruchomiony proces.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zwykle [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] uruchamia program przy użyciu metody [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) , a następnie dołącza debuger do wstrzymanego programu. Jednak istnieją sytuacje, w których aparat debugowania może potrzebować uruchomienia programu (na przykład jeśli aparat debugowania jest częścią interpretera, a debugowany program jest językiem interpretowanym), w tym przypadku [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] używa `IDebugEngineLaunch2::LaunchSuspended` metody.

 Metoda [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) jest wywoływana w celu uruchomienia procesu po pomyślnym uruchomieniu procesu w stanie wstrzymania.

## <a name="see-also"></a>Zobacz też
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)
