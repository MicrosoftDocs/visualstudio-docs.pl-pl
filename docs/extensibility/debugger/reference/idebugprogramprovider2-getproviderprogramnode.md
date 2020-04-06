---
title: IDebugProgramProvider2::GetProviderProgramNode | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd8ca7d5120ba20695caef2e9021ee25869df72f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721794"
---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
Pobiera węzeł programu dla określonego programu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetProviderProgramNode(
   PROVIDER_FLAGS       Flags,
   IDebugDefaultPort2*  pPort,
   AD_PROCESS_ID        processId,
   REFGUID              guidEngine,
   UINT64               programId,
   IDebugProgramNode2** ppProgramNode
);
```

```csharp
int GetProviderProgramNode(
   enum_PROVIDER_FLAGS    Flags,
   IDebugDefaultPort2     pPort,
   AD_PROCESS_ID          ProcessId,
   ref Guid               guidEngine,
   ulong                  programId,
   out IDebugProgramNode2 ppProgramNode
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

`pPort`\
[w] Port, na który jest uruchomiony proces wywoływania.

`processId`\
[w] Struktura [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) zawierająca identyfikator procesu, który zawiera dany program.

`guidEngine`\
[w] Identyfikator GUID aparatu debugowania, do którego jest dołączony program (jeśli istnieje).

`programId`\
[w] Identyfikator programu, dla którego ma zostać wydzielona węźle programu.

`ppProgramNode`\
[na zewnątrz] [Obiekt IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) reprezentujący żądany węzeł programu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
