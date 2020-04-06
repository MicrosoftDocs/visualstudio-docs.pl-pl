---
title: IDebugEngineLaunch2::UruchomienieSpplaned | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e802c17d0a93aabbe5c6c0a8573abc6a551944ae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730545"
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
Ta metoda uruchamia proces za pomocą aparatu debugowania (DE).

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
[w] Nazwa urządzenia, w którym ma zostać uruchomiony proces. Użyj wartości null, aby określić komputer lokalny.

`pPort`\
[w] Interfejs [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) reprezentujący port, w który program będzie uruchamiany.

`pszExe`\
[w] Nazwa pliku wykonywalnego, który ma zostać uruchomiony.

`pszArgs`\
[w] Argumenty, aby przejść do pliku wykonywalnego. Może być wartością null, jeśli nie ma żadnych argumentów.

`pszDir`\
[w] Nazwa katalogu roboczego używanego przez plik wykonywalny. Może to być wartość null, jeśli nie jest wymagany żaden katalog roboczy.

`bstrEnv`\
[w] Blok środowiska ciągów zakończonych wartością NULL, po którym następuje dodatkowy terminator NULL.

`pszOptions`\
[w] Opcje dla pliku wykonywalnego.

`dwLaunchFlags`\
[w] Określa [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) sesji.

`hStdInput`\
[w] Dojście do alternatywnego strumienia wejściowego. Może być 0, jeśli przekierowanie nie jest wymagane.

`hStdOutput`\
[w] Dojście do alternatywnego strumienia wyjściowego. Może być 0, jeśli przekierowanie nie jest wymagane.

`hStdError`\
[w] Obsługa strumienia wyjściowego błędu alternatywnego. Może być 0, jeśli przekierowanie nie jest wymagane.

`pCallback`\
[w] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) obiekt, który odbiera zdarzenia debugera.

`ppDebugProcess`\
[na zewnątrz] Zwraca wynikowy obiekt [IDebugProcess2,](../../../extensibility/debugger/reference/idebugprocess2.md) który reprezentuje uruchomiony proces.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zwykle uruchamia [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] program przy użyciu [launchsuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) metody, a następnie dołącza debuger do zawieszonego programu. Istnieją jednak okoliczności, w których aparat debugowania może być konieczne uruchomienie programu (na przykład, jeśli aparat debugowania jest częścią interpretera i [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] program debugowany jest interpretowany język), w którym to przypadku używa `IDebugEngineLaunch2::LaunchSuspended` metody.

 [Metoda ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) jest wywoływana, aby rozpocząć proces po pomyślnym uruchomieniu procesu w stanie wstrzymania.

## <a name="see-also"></a>Zobacz też
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)
