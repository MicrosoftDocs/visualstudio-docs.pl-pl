---
title: IDebugPointerObject::D ereference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9b3646df80dc93d3248c698efb172bb12a09925e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869638"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
Pobiera obiekt wskazywany przez.

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
podczas Proste przesunięcie bajtów od początku obiektu wskazywanego przez.

`ppObject`\
określoną Zwraca obiekt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) reprezentujący obiekt wskazywany, a także przesunięcie, jeśli istnieje.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu. Zwraca E_FAIL, jeśli ten obiekt nie wskazuje innego obiektu.

## <a name="remarks"></a>Uwagi
 Obiekt wskazywany może być typem pierwotnym lub bardziej złożonym, takim jak Klasa lub struktura.

## <a name="see-also"></a>Zobacz też
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
