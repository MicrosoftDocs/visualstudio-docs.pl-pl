---
title: 'IDebugEngine2:: RemoveAllSetExceptions | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveAllSetExceptions
helpviewer_keywords:
- IDebugEngine2::RemoveAllSetExceptions
ms.assetid: 165fbe89-802d-4d99-85ca-c10fd6cccc09
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca4fbf706fb9172aea2ac7a1304f1643a0061dc4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878958"
---
# <a name="idebugengine2removeallsetexceptions"></a>IDebugEngine2::RemoveAllSetExceptions
Usuwa listę wyjątków ustawionych przez środowisko IDE dla określonej architektury lub języka w czasie wykonywania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT RemoveAllSetExceptions( 
   REFGUID guidType
);
```

```csharp
int RemoveAllSetExceptions( 
   ref Guid guidType
);
```

## <a name="parameters"></a>Parametry
`guidType`\
podczas Identyfikator GUID dla języka lub identyfikator GUID dla aparatu debugowania, który jest specyficzny dla architektury czasu wykonywania.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wyjątki usunięte przez tę metodę zostały ustawione przez wcześniejsze wywołania metody [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) .

 Aby usunąć konkretny wyjątek, wywołaj metodę [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) .

## <a name="see-also"></a>Zobacz też
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)
