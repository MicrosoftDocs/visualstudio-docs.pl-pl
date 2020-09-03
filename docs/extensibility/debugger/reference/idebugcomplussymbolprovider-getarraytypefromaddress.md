---
title: 'IDebugComPlusSymbolProvider:: GetArrayTypeFromAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetArrayTypeFromAddress
- IDebugComPlusSymbolProvider::GetArrayTypeFromAddress
ms.assetid: cc0c53f1-8c0f-49fa-8dbe-bc155e9ce0ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 048a086bae946b5ce730bdfe2c343b6cde1b29e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80733991"
---
# <a name="idebugcomplussymbolprovidergetarraytypefromaddress"></a>IDebugComPlusSymbolProvider::GetArrayTypeFromAddress
Pobiera informacje o typie dla określonej tablicy z uwzględnieniem jego adresu debugowania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetArrayTypeFromAddress(
    IDebugAddress* pAddress,
    BYTE*          pSig,
    DWORD          dwSigLength,
    IDebugField**  ppField
);
```

```csharp
int GetArrayTypeFromAddress(
    IDebugAddress   pAddress,
    int[]           pSig,
    uint            dwSigLength,
    out IDebugField ppField
);
```

## <a name="parameters"></a>Parametry
`pAddress`\
podczas Adres debugowania reprezentowany przez interfejs [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

`pSig`\
podczas Tablica do sprawdzenia.

`dwSigLength`\
podczas Długość w bajtach `pSig` tablicy.

`ppField`\
określoną Zwraca typ tablicy reprezentowanej przez interfejs [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) .

## <a name="return-value"></a>Wartość zwracana
Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje, jak zaimplementować tę metodę dla obiektu **CDebugSymbolProvider** , który uwidacznia Interfejs [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) .

```cpp
HRESULT CDebugSymbolProvider::GetArrayTypeFromAddress(
    IDebugAddress *pAddress,
    BYTE *pSig,
    DWORD dwSigLength,
    IDebugField **ppField)
{
    HRESULT hr = E_FAIL;
    CDEBUG_ADDRESS da;
    CDebugGenericParamScope* pGenScope = NULL;

    METHOD_ENTRY( CDebugDynamicFieldSymbol::GetArrayTypeFromAddress );

    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));
    ASSERT(IsValidWritePtr(ppField, IDebugField*));

    IfFailGo( pAddress->GetAddress(&da) );

    if ( S_OK == hr )
    {
        IfNullGo( pGenScope = new CDebugGenericParamScope(da.GetModule(), da.tokClass, da.GetMethod()), E_OUTOFMEMORY );

        IfFailGo( this->CreateType((const COR_SIGNATURE*)(pSig), dwSigLength, da.GetModule(), mdMethodDefNil, pGenScope, ppField) );
    }

Error:

    METHOD_EXIT( CDebugDynamicFieldSymbol::GetArrayTypeFromAddress, hr );
    RELEASE( pGenScope );
    return hr;
}
```

## <a name="see-also"></a>Zobacz też
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
