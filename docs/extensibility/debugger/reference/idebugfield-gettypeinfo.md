---
title: 'IDebugField:: | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetTypeInfo
helpviewer_keywords:
- IDebugField::GetTypeInfo method
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0f74cc24d7698c3d83991c7f338bd2ef155ee1ce
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869794"
---
# <a name="idebugfieldgettypeinfo"></a>IDebugField::GetTypeInfo
Ta metoda pobiera niezależne od typu informacje o symbolu lub typie.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetTypeInfo( 
   TYPE_INFO* pTypeInfo
);
```

```csharp
int GetTypeInfo(
   TYPE_INFO[] pTypeInfo
);
```

## <a name="parameters"></a>Parametry
`pTypeInfo`\
określoną Zwraca informacje o typie w podanej strukturze [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Informacje niezależne od typu obejmują na przykład obiekt AppDomain, moduł i klasę, która zawiera symbol.

## <a name="see-also"></a>Zobacz też
- [GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
