---
title: 'IDebugDynamicFieldCOMPlus:: GetTypeFromPrimitive | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDynamicFieldCOMPlus::GetTypeFromPrimitive
- GetTypeFromPrimitive
ms.assetid: d7f51e2a-1b72-489c-b7b6-4af7b7e4d663
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d1f0a93c14c99c885a9ea8af0f1d650b508efb76
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899025"
---
# <a name="idebugdynamicfieldcomplusgettypefromprimitive"></a>IDebugDynamicFieldCOMPlus::GetTypeFromPrimitive
Pobiera typ z danym typem pierwotnym.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetTypeFromPrimitive(
   DWORD         dwCorElementType,
   IDebugField** ppType
);
```

```csharp
int GetTypeFromPrimitive(
   uint            dwCorElementType,
   out IDebugField ppType
);
```

## <a name="parameters"></a>Parametry
`dwCorElementType`\
podczas Wartość z [wyliczenia CorElementType —](/dotnet/framework/unmanaged-api/metadata/corelementtype-enumeration) , która reprezentuje typ pierwotny.

`ppType`\
określoną Zwraca [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , który reprezentuje typ.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)
