---
title: IDebugProperty3::DestroyObjectID | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f465bc06712c5032c6e90288ebd02406de4f2330
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721200"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
Niszczy unikatowy identyfikator skojarzony z tą właściwością, wskazując, że obiekt wywołujący nie dba już o identyfikowanie tej właściwości w unikatowy sposób ze wszystkich innych właściwości.

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
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Jeśli aparat debugowania nie musi obsługiwać unikatowych identyfikatorów dla właściwości (ponieważ już śledzi je `E_NOTIMPL` wyjątkowo wewnętrznie), następnie można po prostu powrócić do tej metody.

 Unikatowe identyfikatory są tworzone za pomocą wywołania [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) metody, gdy obiekt wywołujący chce upewnić się, że ta właściwość jest jednoznacznie identyfikowane wśród wszystkich innych właściwości.

## <a name="see-also"></a>Zobacz też
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)
