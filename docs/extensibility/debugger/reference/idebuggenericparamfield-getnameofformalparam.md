---
title: IDebugGenericParamField::GetNameOfFormalParam | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField::GetNameOfFormalParam
- GetNameOfFormalParam
ms.assetid: 05032a83-49ce-4007-b5d6-7b56945b956c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e927c6fb85a4e654224f95564f6575141783137
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56682872"
---
# <a name="idebuggenericparamfieldgetnameofformalparam"></a>IDebugGenericParamField::GetNameOfFormalParam
Pobiera nazwę tego parametru ogólnego.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetNameOfFormalParam (
    BSTR* pbstrName
);
```

```csharp
int GetNameOfFormalParam (
    string pbstrName
);
```

#### <a name="parameters"></a>Parametry
`pbstrName`

 [out] Nazwa tego parametru ogólnego.

## <a name="return-value"></a>Wartość zwracana
Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje, jak zaimplementować tę metodę, aby uzyskać **CDebugGenericParamFieldType** obiekt ujawniający [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) interfejsu.

```cpp
HRESULT CDebugGenericParamFieldType::GetNameOfFormalParam(BSTR *pbstrName)
{
    HRESULT hr = S_OK;
    CComBSTR bstrName;

    METHOD_ENTRY( CDebugGenericParamFieldType::GetNameOfFormalParam );

    IfFalseGo( pbstrName, E_INVALIDARG );
    IfFailGo( this->LoadProps() );
    IfNullGo( *pbstrName = SysAllocString(m_bstrName), E_OUTOFMEMORY );

Error:

    METHOD_EXIT( CDebugGenericParamFieldType::GetNameOfFormalParam, hr );
    return hr;
}
```

## <a name="see-also"></a>Zobacz też
- [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)
