---
title: IDebugEngineLaunch2::LaunchSuspended | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d7a3de4a6de71ed1cc291ebec46ca8aac992e4e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55038672"
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
Ta metoda uruchamia proces, za pomocą aparatu debugowania (DE).  
  
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
  
#### <a name="parameters"></a>Parametry  
 `pszMachine`  
 [in] Nazwa maszyny, w którym można uruchomić procesu. Użyj wartości null, aby określić komputer lokalny.  
  
 `pPort`  
 [in] [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfejs reprezentujący portu, który będzie uruchamiany program.  
  
 `pszExe`  
 [in] Nazwa pliku wykonywalnego do uruchomienia.  
  
 `pszArgs`  
 [in] Argumenty do przekazania do pliku wykonywalnego. Może być wartością null, jeśli nie wymaga argumentów.  
  
 `pszDir`  
 [in] Nazwa katalogu roboczego używane przez plik wykonywalny. Może być wartością null, jeśli katalog roboczy nie jest wymagana.  
  
 `bstrEnv`  
 [in] Blok środowiska ciągów zakończony znakiem NULL, następuje dodatkowe terminator o wartości NULL.  
  
 `pszOptions`  
 [in] Opcje dla pliku wykonywalnego.  
  
 `dwLaunchFlags`  
 [in] Określa [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) opłata za sesję.  
  
 `hStdInput`  
 [in] Dojście do alternatywnego strumienia wejściowego. Może być równa 0, jeśli przekierowanie nie jest wymagana.  
  
 `hStdOutput`  
 [in] Dojście do strumienia wyjściowego alternatywne. Może być równa 0, jeśli przekierowanie nie jest wymagana.  
  
 `hStdError`  
 [in] Dojście do błędu alternatywnego strumienia wyjściowego. Może być równa 0, jeśli przekierowanie nie jest wymagana.  
  
 `pCallback`  
 [in] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) obiekt, który odbiera zdarzenia debuger.  
  
 `ppDebugProcess`  
 [out] Zwraca wartość wynikowa [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) obiekt, który reprezentuje uruchomienie procesu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Zwykle [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] uruchamia program korzysta [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) metody, a następnie dołącza debuger do wstrzymania programu. Istnieją jednak okoliczności, w których aparat debugowania może być konieczne, uruchom program (na przykład, jeśli aparat debugowania jest częścią tłumacza i debugowanego jest językiem interpretowanych), w którym to przypadku [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] używa `IDebugEngineLaunch2::LaunchSuspended` — metoda .  
  
 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) metoda jest wywoływana, aby rozpocząć proces po procesie została pomyślnie uruchomiona w stanie wstrzymania.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)