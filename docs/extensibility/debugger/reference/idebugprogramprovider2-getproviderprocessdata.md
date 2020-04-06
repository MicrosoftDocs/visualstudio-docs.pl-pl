---
title: IDebugProgramProvider2::GetProviderProcessData | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
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
[w] Kombinacja flag z wyliczenia [PROVIDER_FLAGS.](../../../extensibility/debugger/reference/provider-flags.md) Następujące flagi są typowe dla tego wywołania:

|Flaga|Opis|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|Rozmówca jest uruchomiony na komputerze zdalnym.|
|`PFLAG_DEBUGGEE`|Wywołujący jest obecnie debugowane (dodatkowe informacje na temat marshalling zostaną zwrócone dla każdego węzła).|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Wywołujący został dołączony do, ale nie został uruchomiony przez debugera.|
|`PFLAG_GET_PROGRAM_NODES`|Wywołujący prosi o listę węzłów programu do zwrócenia.|

`pPort`\
[w] Port, na który jest uruchomiony proces wywoływania.

`processId`\
[w] Struktura [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) zawierająca identyfikator procesu, który zawiera dany program.

`EngineFilter`\
[w] Tablica identyfikatorów GUID dla aparatów debugowania przypisanych do debugowania tego procesu (będą one używane do filtrowania programów, które są faktycznie zwracane na podstawie tego, co obsługują dostarczone aparaty; jeśli nie zostaną określone żadne aparaty, zostaną zwrócone wszystkie programy).

`pProcess`\
[na zewnątrz] Struktura [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) wypełniona żądanymi informacjami.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest zwykle wywoływana przez proces, aby uzyskać listę programów uruchomionych w tym procesie. Zwrócone informacje to lista obiektów [IDebugProgramNode2.](../../../extensibility/debugger/reference/idebugprogramnode2.md)

## <a name="see-also"></a>Zobacz też
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
