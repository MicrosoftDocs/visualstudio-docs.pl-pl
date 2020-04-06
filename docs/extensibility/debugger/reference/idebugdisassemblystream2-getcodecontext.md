---
title: IDebugDisassemblyStream2::GetCodeContext | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeContext
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeContext
ms.assetid: a6d0ae82-7617-4915-9713-369abe3e2e53
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6b3864528ee90c22a1e7122eeaf1969f613cc8e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732284"
---
# <a name="idebugdisassemblystream2getcodecontext"></a>IDebugDisassemblyStream2::GetCodeContext
Zwraca obiekt kontekstu kodu odpowiadający określonemu identyfikatorowi lokalizacji kodu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetCodeContext( 
   UINT64               uCodeLocationId,
   IDebugCodeContext2** ppCodeContext
);
```

```csharp
int GetCodeContext( 
   ulong                  uCodeLocationId,
   out IDebugCodeContext2 ppCodeContext
);
```

## <a name="parameters"></a>Parametry
`uCodeLocationId`\
[w] Określa identyfikator lokalizacji kodu. Zobacz uwagi sekcji [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) metody opis identyfikatora lokalizacji kodu.

`ppCodeContext`\
[na zewnątrz] Zwraca obiekt [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) reprezentujący skojarzony kontekst kodu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Identyfikator lokalizacji kodu mogą być zwracane z wywołania [getCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md) metody i może pojawić się w [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) struktury.

 Aby przekonwertować kontekst kodu na identyfikator lokalizacji kodu, należy wywołać [metodę GetCodeLocationId.](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)

## <a name="see-also"></a>Zobacz też
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
- [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
