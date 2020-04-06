---
title: IDebugProcess2::Dołącz | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724195"
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
Dołącza menedżera debugowania sesji (SDM) do procesu.

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
[w] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) obiekt, który jest używany do debugowania zdarzenia powiadomienia.

`rgguidSpecificEngines`\
[w] Tablica identyfikatorów GUID aparatów debugowania, które mają być używane do debugowania programów uruchomionych w procesie. Ten parametr może być wartością null. Zobacz Uwagi, aby uzyskać szczegółowe informacje.

`celtSpecificEngines`\
[w] Liczba aparatów debugowania `rgguidSpecificEngines` w tablicy `rghrEngineAttach` i rozmiar tablicy.

`rghrEngineAttach`\
[w, na zewnątrz] Tablica kodów HRESULT zwracana przez aparaty debugowania. Rozmiar tej tablicy jest `celtSpecificEngines` określony w parametrze. Każdy kod jest zazwyczaj `S_OK` `S_ATTACH_DEFERRED`albo albo . Ten ostatni wskazuje, że DE jest obecnie dołączony do żadnych programów.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu. W poniższej tabeli przedstawiono inne możliwe wartości.

|Wartość|Opis|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Określony proces jest już dołączony do debugera.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Podczas procedury dołączania wystąpiło naruszenie zabezpieczeń.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Nie można dołączyć procesu pulpitu do debugera.|

## <a name="remarks"></a>Uwagi
 Dołączanie do procesu dołącza SDM do wszystkich programów uruchomionych w tym procesie, które mogą być debugowane przez aparaty debugowania (DE) określone w `rgguidSpecificEngines` tablicy. Ustaw `rgguidSpecificEngines` parametr na wartość null `GUID_NULL` lub uwzględnij w tablicy, aby dołączyć go do wszystkich programów w procesie.

 Wszystkie zdarzenia debugowania, które występują w procesie są wysyłane do danego [obiektu IDebugEventCallback2.](../../../extensibility/debugger/reference/idebugeventcallback2.md) Ten `IDebugEventCallback2` obiekt jest dostarczany, gdy SDM wywołuje tę metodę.

## <a name="see-also"></a>Zobacz też
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
