---
title: IDebugProgram2::GetName | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetName
helpviewer_keywords:
- IDebugProgram2::GetName
ms.assetid: a54cbf13-b3e3-4c9f-8b8d-13573232dfb0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2f7faa4b864824a46e30f05f6465eee30f4a3e16
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66210189"
---
# <a name="idebugprogram2getname"></a>IDebugProgram2::GetName
Pobiera nazwę programu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetName( 
   BSTR* pbstrName
);
```

```csharp
int GetName( 
   out string pbstrName
);
```

## <a name="parameters"></a>Parametry
`pbstrName`\
[out] Zwraca nazwę programu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Nazwa zwracanego przez tę metodę jest zawsze przyjaznej nazwy zawiera użytkownika, która opisuje program.

## <a name="see-also"></a>Zobacz także
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)