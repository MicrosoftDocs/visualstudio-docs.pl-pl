---
title: IDebugField::GetTypeInfo | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetTypeInfo
helpviewer_keywords:
- IDebugField::GetTypeInfo method
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 781c9a0e4365a454d45af957207099d6d5ae7d92
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212655"
---
# <a name="idebugfieldgettypeinfo"></a>IDebugField::GetTypeInfo
Ta metoda pobiera niezależnie od typu informacji na temat symboli lub typu.

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
[out] Zwraca informację o typie w podanym [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) struktury.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Niezależnie od typu informacji obejmuje, na przykład, element AppDomain, moduł i klasę, która zawiera symbol.

## <a name="see-also"></a>Zobacz także
- [GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)