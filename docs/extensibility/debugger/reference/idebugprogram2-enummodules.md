---
title: IDebugProgram2::EnumModules | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumModules
helpviewer_keywords:
- IDebugProgram2::EnumModules
ms.assetid: 876ac9da-3b7c-4156-b79a-8f340e9fcea6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 68ccc490476fcb8ccf3cc135493f5d95253f1018
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66200306"
---
# <a name="idebugprogram2enummodules"></a>IDebugProgram2::EnumModules
Pobiera listę modułów, w których ten program został załadowany i jest wykonywany.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumModules( 
   IEnumDebugModules2** ppEnum
);
```

```csharp
int EnumModules( 
   out IEnumDebugModules2 ppEnum
);
```

## <a name="parameters"></a>Parametry
`ppEnum`\
[out] Zwraca [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) obiektu, który zawiera listę modułów.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Moduł biblioteki DLL lub zestawu i zazwyczaj znajduje się w **modułów** okna debugowania.

## <a name="see-also"></a>Zobacz także
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)