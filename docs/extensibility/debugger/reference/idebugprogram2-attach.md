---
title: IDebugProgram2::Dołącz | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Attach
helpviewer_keywords:
- IDebugProgram2::Attach
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7d0b182ba7a873816e3a7aa32d39beb2c63cc5ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723139"
---
# <a name="idebugprogram2attach"></a>IDebugProgram2::Attach
Dołącza się do programu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback
);
```

## <a name="parameters"></a>Parametry
`pCallback`\
[w] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) obiekt do użycia do powiadamiania o zdarzeniach debugowania.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu. W poniższej tabeli przedstawiono niektóre możliwe kody błędów.

|Wartość|Opis|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Określony program jest już dołączony do debugera.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Podczas procedury dołączania wystąpiło naruszenie zabezpieczeń.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Do debugera nie można dołączyć programu klasycznego.|

## <a name="remarks"></a>Uwagi
 Aparat debugowania (DE) nigdy nie wywołuje tej metody, aby dołączyć do programu. Jeśli DE działa w przestrzeni adresowej programu, [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metoda jest wywoływana. Jeśli DE działa w przestrzeni adresowej menedżera debugowania sesji (SDM), [dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md) metodę jest wywoływana.

## <a name="see-also"></a>Zobacz też
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md)
