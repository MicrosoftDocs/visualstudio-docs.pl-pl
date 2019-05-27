---
title: IDebugProgramProvider2::GetProviderProcessData | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dc0884597454cf50cb5540d61b865dfe7686c25f
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66203781"
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
Pobiera listę uruchomionymi programami od określonego procesu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetProviderProcessData(
   PROVIDER_FLAGS         Flags,
   IDebugDefaultPort2*    pPort,
   AD_PROCESS_ID          processId,
   CONST_GUID_ARRAY       EngineFilter,
   PROVIDER_PROCESS_DATA* pProcess
);
```

```csharp
int GetProviderProcessData(
   enum_PROVIDER_FLAGS     Flags,
   IDebugDefaultPort2      pPort,
   AD_PROCESS_ID           ProcessId,
   CONST_GUID_ARRAY        EngineFilter,
   PROVIDER_PROCESS_DATA[] pProcess
);
```

## <a name="parameters"></a>Parametry
`Flags`\
[in] Kombinacja flag z [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) wyliczenia. Następujące flagi są typowe dla tego wywołania:

|Flaga|Opis|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|Obiekt wywołujący jest uruchomiona na komputerze zdalnym.|
|`PFLAG_DEBUGGEE`|Obiekt wywołujący jest teraz debugowana (dodatkowe informacje na temat kierowania zostanie zwrócony dla każdego węzła).|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Dołączony do obiektu wywołującego, ale nie jest uruchomiona przez debuger.|
|`PFLAG_GET_PROGRAM_NODES`|Obiekt wywołujący pyta o listę węzłów program mają zostać zwrócone.|

`pPort`\
[in] Port procesu wywołującego jest uruchomiona na.

`processId`\
[in] [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struktury zawierający identyfikator procesu, który zawiera program zagrożona.

`EngineFilter`\
[in] Tablica identyfikatorów GUID dla aparaty debugowania przypisane do debugowania tego procesu (zostaną one użyte do filtrowania programy, które faktycznie są zwracane na podstawie co podane aparaty obsługują; Jeśli żadne aparaty nie są określone, a następnie zostaną zwrócone wszystkie programy).

`pProcess`\
[out] A [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) strukturę, która jest wypełniane wymagane informacje.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest zazwyczaj wywoływana przez proces, aby uzyskać listę programów uruchomionych w tym procesie. Zwracane informacje znajduje się lista [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) obiektów.

## <a name="see-also"></a>Zobacz także
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)