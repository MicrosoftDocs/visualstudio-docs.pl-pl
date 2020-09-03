---
title: 'IDebugProgramProvider2:: GetProviderProcessData | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4e958900307f5f7915f58679709c88f80c2abfc9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721853"
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
Pobiera listę uruchomionych programów z określonego procesu.

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
podczas Kombinacja flag z wyliczenia [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) . Następujące flagi są typowe dla tego wywołania:

|Flaga|Opis|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|Obiekt wywołujący jest uruchomiony na komputerze zdalnym.|
|`PFLAG_DEBUGGEE`|Obiekt wywołujący jest obecnie debugowany (dodatkowe informacje o kierowaniu zostaną zwrócone dla każdego węzła).|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Obiekt wywołujący został dołączony do, ale nie został uruchomiony przez debuger.|
|`PFLAG_GET_PROGRAM_NODES`|Obiekt wywołujący prosi o listę węzłów programów do zwrócenia.|

`pPort`\
podczas Port, na którym jest uruchomiony proces wywołujący.

`processId`\
podczas Struktura [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) przechowująca identyfikator procesu zawierającego dany program.

`EngineFilter`\
podczas Tablica identyfikatorów GUID dla aparatów debugowania przypisanych do debugowania tego procesu (zostaną one użyte do filtrowania programów, które faktycznie są zwracane na podstawie obsługiwanych aparatów). Jeśli nie zostaną określone żadne aparaty, zostaną zwrócone wszystkie programy.

`pProcess`\
określoną Struktura [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) , która jest wypełniana przy użyciu żądanych informacji.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest zwykle wywoływana przez proces w celu uzyskania listy programów uruchomionych w ramach tego procesu. Zwrócone informacje to lista obiektów [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) .

## <a name="see-also"></a>Zobacz też
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
