---
title: IDebugGenericParamField::GetFlags | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetFlags
- IDebugGenericParamField::GetFlags
ms.assetid: adcbbca1-8960-4c88-86b0-8b9467056c97
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8bed8af80312f5dc5d3f60c7093ac510ab8ac7b8
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66211849"
---
# <a name="idebuggenericparamfieldgetflags"></a>IDebugGenericParamField::GetFlags
Pobranie flagi dla tego parametru ogólnego.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetFlags(
    DWORD* pdwFlags
);
```

```csharp
int GetFlags(
    ref uint pdwFlags
);
```

## <a name="parameters"></a>Parametry
`pdwFlags`\
[out] Zwraca wartość flagi dla tego parametru ogólnego.

## <a name="return-value"></a>Wartość zwracana
Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
Te flagi, zawierają informacje dotyczące różnych ograniczeń specjalnych.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje, jak zaimplementować tę metodę, aby uzyskać **CDebugGenericParamFieldType** obiekt ujawniający [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) interfejsu.

```cpp
HRESULT CDebugGenericParamFieldType::GetFlags(DWORD *pdwFlags)
{
    HRESULT hr = S_OK;

    METHOD_ENTRY( CDebugGenericParamFieldType::GetFlags );

    IfFalseGo( pdwFlags, E_INVALIDARG );
    IfFailGo( this->LoadProps() );
    *pdwFlags = m_dwFlags;

Error:

    METHOD_EXIT( CDebugGenericParamFieldType::GetFlags, hr );
    return hr;
}
```

## <a name="see-also"></a>Zobacz także
- [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)
