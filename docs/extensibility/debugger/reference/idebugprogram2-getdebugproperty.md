---
description: Pobiera właściwości programu.
title: 'IDebugProgram2:: GetDebugProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0114d0cf51769d6162563f6c60d51a3f031e19e2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159955"
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
Pobiera właściwości programu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetDebugProperty( 
   IDebugProperty2** ppProperty
);
```

```csharp
int GetDebugProperty( 
   out IDebugProperty2 ppProperty
);
```

## <a name="parameters"></a>Parametry
`ppProperty`\
określoną Zwraca obiekt [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , który reprezentuje właściwości programu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Właściwości zwrócone przez tę metodę są specyficzne dla programu. Jeśli program musi zwrócić więcej niż jedną właściwość, wówczas obiekt [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) zwracany przez tę metodę jest kontenerem dodatkowych właściwości i wywołanie metody [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) zwraca listę wszystkich właściwości.

 Program może uwidaczniać dowolną liczbę i typ dodatkowych właściwości, które można opisać za pomocą `IDebugProperty2` interfejsu. IDE może wyświetlić dodatkowe właściwości programu za pomocą ogólnego interfejsu użytkownika przeglądarki właściwości.

## <a name="see-also"></a>Zobacz też
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
