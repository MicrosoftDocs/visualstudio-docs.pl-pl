---
title: IDebugProperty3::DestroyObjectID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3375ce22a9b66077d635acd9a5a98f2640662467
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457678"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
Niszczy Unikatowy identyfikator skojarzony z tą właściwością wskazujący, że obiekt wywołujący nie jest już dba do identyfikowania tej właściwości, które jednoznacznie ze wszystkich innych właściwości.

## <a name="syntax"></a>Składnia

```cpp
HRESULT DestroyObjectID(
   void
);
```

```csharp
int DestroyObjectID();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Jeśli aparat debugowania nie ma konieczności obsługi unikatowych identyfikatorów dla właściwości (ponieważ jest on już śledzi je jednoznacznie wewnętrznie), a następnie można po prostu zwrócenia `E_NOTIMPL` dla tej metody.

 Unikatowe identyfikatory są tworzone za pomocą wywołania [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) metody, gdy obiekt wywołujący chce upewnić się, ta właściwość jest unikatowo identyfikowana przez inne właściwości.

## <a name="see-also"></a>Zobacz także
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)