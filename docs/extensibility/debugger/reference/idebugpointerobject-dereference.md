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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe87d5db40ce663d84c9561e89a84e6fcb1684ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725567"
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
