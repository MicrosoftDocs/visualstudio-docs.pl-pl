---
title: IDebugProgram2::GetDebugProperty | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 33bc10aadf25eb95414cc5fd334c572b2f270429
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722896"
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
[na zewnątrz] Zwraca obiekt [IDebugProperty2,](../../../extensibility/debugger/reference/idebugproperty2.md) który reprezentuje właściwości programu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Właściwości zwracane przez tę metodę są specyficzne dla programu. Jeśli program musi zwrócić więcej niż jedną właściwość, a następnie [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) obiekt zwrócony przez tę metodę jest kontenerem dodatkowych właściwości i wywołanie [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) metoda zwraca listę wszystkich właściwości.

 Program może udostępnić dowolną liczbę i typ dodatkowych właściwości, `IDebugProperty2` które można opisać za pośrednictwem interfejsu. IDE może wyświetlać dodatkowe właściwości programu za pośrednictwem interfejsu użytkownika przeglądarki właściwości ogólne.

## <a name="see-also"></a>Zobacz też
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
