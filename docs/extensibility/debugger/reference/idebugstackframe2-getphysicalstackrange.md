---
title: IDebugStackFrame2::GetPhysicalStackRange | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3df924c6c8a4373082d61575e4ad8a7ec3f161d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719672"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
Pobiera zależną od komputera reprezentację zakresu adresów fizycznych skojarzonych z ramką stosu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetPhysicalStackRange ( 
   UINT64* paddrMin,
   UINT64* paddrMax
);
```

```csharp
int GetPhysicalStackRange ( 
   out ulong paddrMin,
   out ulong paddrMax
);
```

## <a name="parameters"></a>Parametry
`paddrMin`\
[na zewnątrz] Zwraca najniższy adres fizyczny skojarzony z tą ramką stosu.

`paddrMax`\
[na zewnątrz] Zwraca najwyższy adres fizyczny skojarzony z tą ramką stosu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Informacje zwracane przez tę metodę są używane przez menedżera debugowania sesji (SDM) do sortowania ramek stosu.

 Zakłada się, że stos wywołań rośnie w dół, oznacza to, że nowe ramki stosu są dodawane przy coraz niższych adresach pamięci. Architektura czasu wykonywania musi zapewniać zakresy stosu fizycznego, które odpowiadają temu założeniu.

## <a name="see-also"></a>Zobacz też
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
