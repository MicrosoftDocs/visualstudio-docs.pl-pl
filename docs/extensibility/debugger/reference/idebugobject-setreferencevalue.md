---
title: 'IDebugObject:: SetReferenceValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cc0db8ee7f0581a4c336111d3876c24f0e5c12d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726381"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
Ustawia wartość referencyjną tego obiektu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetReferenceValue( 
   IDebugObject* pObject
);
```

```csharp
int SetReferenceValue(
   [In] IDebugObject pObject
);
```

## <a name="parameters"></a>Parametry
`pObject`\
podczas Obiekt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) reprezentujący nową wartość referencyjną.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda sprawia, że obiekt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) odwołuje się do wartości obiektu podaną w `pObject` parametrze, zwracając wszystkie poprzednie odwołanie. Należy pamiętać, że ten `IDebugObject` obiekt musi już być typem referencyjnym.

## <a name="see-also"></a>Zobacz też
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
