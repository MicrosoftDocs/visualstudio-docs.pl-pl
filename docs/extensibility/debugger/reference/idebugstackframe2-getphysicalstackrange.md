---
title: IDebugStackFrame2::GetPhysicalStackRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ac507c2eac00d025a36bed3e4c3461a6b3fab2f0
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212862"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
Pobiera reprezentację zależnych od maszyny, zakresu adresów fizycznych skojarzonych z ramki stosu.

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
[out] Zwraca najniższy adres fizyczny skojarzone z tą ramką stosu.

`paddrMax`\
[out] Zwraca najwyższy adres fizyczny skojarzone z tą ramką stosu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Informacje zwracane przez tę metodę jest używany przez Menedżer debugowania sesji (SDM) do sortowania ramki stosu.

 Zakłada się, że stos wywołań rośnie, oznacza to, dodania nowej ramki stosu w coraz większym stopniu niższe adresów pamięci. Architektura środowiska wykonawczego, musisz podać zakresy adresów fizycznych stosu, które odpowiadają tym założeń.

## <a name="see-also"></a>Zobacz także
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)