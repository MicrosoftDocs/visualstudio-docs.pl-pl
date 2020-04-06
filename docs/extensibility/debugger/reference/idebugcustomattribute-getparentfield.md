---
title: IDebugCustomAttribute::GetParentField | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetParentField
helpviewer_keywords:
- IDebugCustomAttribute::GetParentField
ms.assetid: bcdfdf37-bfcf-4988-a7b8-4c731d0af1b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fae84a4d02438335aea00c50dd9b89520d08bae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732689"
---
# <a name="idebugcustomattributegetparentfield"></a>IDebugCustomAttribute::GetParentField
Pobiera pole, do którego dołączony jest atrybut niestandardowy.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetParentField( 
   IDebugField** ppField
);
```

```csharp
int GetParentField(
   out IDebugField ppField
);
```

## <a name="parameters"></a>Parametry
`ppField`\
[na zewnątrz] Zwraca obiekt [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) reprezentujący pole, do którego jest dołączony atrybut niestandardowy.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się powiedzie, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wywołanie [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) metody na zwrócony [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiektu, aby określić, jakiego rodzaju pola nadrzędnego jest.

## <a name="see-also"></a>Zobacz też
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
