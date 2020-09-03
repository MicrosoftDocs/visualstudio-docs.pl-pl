---
title: 'IDebugProcess2:: Attach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fb6ea896285c784021402400597ba168f6ccf716
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724195"
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
Dołącza Menedżera debugowania sesji (SDM) do procesu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   GUID*                 rgguidSpecificEngines,
   DWORD                 celtSpecificEngines,
   HRESULT*              rghrEngineAttach
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   Guid[]               rgguidSpecificEngines,
   uint                 celtSpecificEngines,
   int[]                rghrEngineAttach
);
```

## <a name="parameters"></a>Parametry
`pCallback`\
podczas Obiekt [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , który jest używany do powiadamiania o zdarzeniach debugowania.

`rgguidSpecificEngines`\
podczas Tablica identyfikatorów GUID aparatów debugowania, która ma być używana do debugowania programów uruchomionych w procesie. Ten parametr może być wartością null. Aby uzyskać szczegółowe informacje, zobacz uwagi.

`celtSpecificEngines`\
podczas Liczba aparatów debugowania w `rgguidSpecificEngines` tablicy i rozmiar `rghrEngineAttach` tablicy.

`rghrEngineAttach`\
[in. out] Tablica kodów HRESULT zwracanych przez aparaty debugowania. Rozmiar tej tablicy jest określony w `celtSpecificEngines` parametrze. Każdy kod jest zwykle albo `S_OK` lub `S_ATTACH_DEFERRED` . Ten ostatni wskazuje, że DE jest obecnie dołączony do żadnego z programów.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. W poniższej tabeli przedstawiono inne możliwe wartości.

|Wartość|Opis|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Określony proces jest już dołączony do debugera.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Podczas procedury Attach wystąpiło naruszenie zabezpieczeń.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Nie można dołączyć procesu pulpitu do debugera.|

## <a name="remarks"></a>Uwagi
 Dołączenie do procesu dołącza model SDM do wszystkich programów uruchomionych w tym procesie, które mogą być debugowane przez aparaty debugowania (DE) określone w `rgguidSpecificEngines` tablicy. Ustaw `rgguidSpecificEngines` parametr na wartość null lub Dołącz do `GUID_NULL` tablicy, aby dołączyć do wszystkich programów w procesie.

 Wszystkie zdarzenia debugowania występujące w procesie są wysyłane do danego obiektu [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) . Ten `IDebugEventCallback2` obiekt jest dostarczany, gdy model SDM wywołuje tę metodę.

## <a name="see-also"></a>Zobacz też
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
