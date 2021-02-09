---
title: 'IDebugProperty2:: GetParent | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetParent
helpviewer_keywords:
- IDebugProperty2::GetParent
ms.assetid: 58780469-fe25-4d84-9187-67940ca0767f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9855ff168152ed68117569aab939e62da990f81b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850974"
---
# <a name="idebugproperty2getparent"></a>IDebugProperty2::GetParent
Pobiera Właściwość Parent właściwości.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetParent ( 
   IDebugProperty2** ppParent
);
```

```csharp
int GetParent ( 
   out IDebugProperty2 ppParent
);
```

## <a name="parameters"></a>Parametry
`ppParent`\
określoną Zwraca obiekt [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , który reprezentuje element nadrzędny właściwości.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. Zwraca `S_GETPARENT_NO_PARENT` czy nie ma elementu nadrzędnego.

## <a name="see-also"></a>Zobacz też
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
