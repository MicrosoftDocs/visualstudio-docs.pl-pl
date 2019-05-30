---
title: IDebugPointerObject::Dereference | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 381c6f392cccb398497204cc5772c5f9a00fd5b0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331658"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
Pobiera obiekt wskazywany.

## <a name="syntax"></a>Składnia

```cpp
HRESULT DeReference( 
   DWORD          dwIndex,
   IDebugObject** ppObject
);
```

```csharp
int Dereference(
   uint             dwIndex,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametry
`dwIndex`\
[in] Przesunięcie bajtu proste, od początku obiektu wskazywanego.

`ppObject`\
[out] Zwraca [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) obiekt reprezentujący obiekt wskazywany, a także przesunięcie, jeśli istnieje.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu. Zwraca E_FAIL, jeśli ten obiekt nie wskazuje innego obiektu.

## <a name="remarks"></a>Uwagi
 Jaki wskazał obiekt może być podstawowy lub bardziej złożonych typów, takich jak klasy lub struktury.

## <a name="see-also"></a>Zobacz także
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)