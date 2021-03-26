---
description: Pobiera węzeł programu dla określonego programu.
title: 'IDebugProgramProvider2:: GetProviderProgramNode | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 07e7184c189d501b2fcb604590eeb121bae8ccdc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065284"
---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
Pobiera węzeł programu dla określonego programu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetProviderProgramNode(
   PROVIDER_FLAGS       Flags,
   IDebugDefaultPort2*  pPort,
   AD_PROCESS_ID        processId,
   REFGUID              guidEngine,
   UINT64               programId,
   IDebugProgramNode2** ppProgramNode
);
```

```csharp
int GetProviderProgramNode(
   enum_PROVIDER_FLAGS    Flags,
   IDebugDefaultPort2     pPort,
   AD_PROCESS_ID          ProcessId,
   ref Guid               guidEngine,
   ulong                  programId,
   out IDebugProgramNode2 ppProgramNode
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

`pPort`\
podczas Port, na którym jest uruchomiony proces wywołujący.

`processId`\
podczas Struktura [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) przechowująca identyfikator procesu zawierającego dany program.

`guidEngine`\
podczas Identyfikator GUID aparatu debugowania, do którego jest dołączony program (jeśli istnieje).

`programId`\
podczas Identyfikator programu, dla którego ma zostać pobrany węzeł programu.

`ppProgramNode`\
określoną Obiekt [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) reprezentujący żądany węzeł programu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
