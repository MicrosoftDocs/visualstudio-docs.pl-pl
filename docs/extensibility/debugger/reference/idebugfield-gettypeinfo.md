---
description: Ta metoda pobiera niezależne od typu informacje o symbolu lub typie.
title: 'IDebugField:: | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetTypeInfo
helpviewer_keywords:
- IDebugField::GetTypeInfo method
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9ea120cb58faa28bbb8168800ef6e35f707d879f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073706"
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
