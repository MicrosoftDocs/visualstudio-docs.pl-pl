---
title: IDebugDisassemblyStream2::GetCodeContext | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeContext
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeContext
ms.assetid: a6d0ae82-7617-4915-9713-369abe3e2e53
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 241a86e1c0fb5acc9ca0c0e92339ea45af514f61
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66205052"
---
# <a name="idebugdisassemblystream2getcodecontext"></a>IDebugDisassemblyStream2::GetCodeContext
Zwraca obiekt kontekstu kodu odpowiadającego identyfikatorowi lokalizacji określonego kodu.

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
[in] Określa identyfikator lokalizacji kodu. Zobacz sekcję Spostrzeżenia, aby [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) metoda opis identyfikator lokalizacji kodu.

`ppCodeContext`\
[out] Zwraca [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) obiekt, który reprezentuje kontekst skojarzonego kodu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Identyfikator lokalizacji kodu mogą być zwracane przez wywołanie [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md) metoda i może być wyświetlany w [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) struktury.

 Aby dokonać konwersji kontekst kodu na identyfikator lokalizacji kodu, należy wywołać [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) metody.

## <a name="see-also"></a>Zobacz także
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
- [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)