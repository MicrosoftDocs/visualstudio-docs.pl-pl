---
title: IDebugComPlusSymbolProvider::GetSymAttribute | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetSymAttribute
- GetSymAttribute
ms.assetid: 6cbaac92-a60b-4165-a7f5-c34407770f3c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cb405bd0cf6f3ec846e3b146e4fd02399d583fb7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733770"
---
# <a name="idebugcomplussymbolprovidergetsymattribute"></a>IDebugComPlusSymbolProvider::GetSymAttribute
Pobiera symbole debugowania z atrybutem nadrzędnym dla określonego modułu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetSymAttribute (
    ULONG32  ulAppDomainID,
    GUID     guidModule,
    _mdToken tokParent,
    LPOLESTR pstrName,
    ULONG32  cBuffer,
    ULONG32* pcBuffer,
    BYTE*    buffer
);
```

```csharp
int GetSymAttribute (
    uint      ulAppDomainID,
    Guid      guidModule,
    int       tokParent,
    string    pstrName,
    uint      cBuffer,
    out uint  pcBuffer,
    out int[] buffer
);
```

## <a name="parameters"></a>Parametry
`ulAppDomainID`\
[w] Identyfikator domeny aplikacji.

`guidModule`\
[w] Unikatowy identyfikator modułu.

`tokParent`\
[w] Token dla atrybutu nadrzędnego.

`pstrName`\
[w] Nazwa modułu.

`cBuffer`\
[w] Liczba bajtów wymaganych `buffer`dla danych wyjściowych .

`pcBuffer`\
[na zewnątrz] Długość wyjścia `buffer`.

`buffer`\
[na zewnątrz] Tablica zawierająca symbole.

## <a name="return-value"></a>Wartość zwracana
Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="example"></a>Przykład
W poniższym przykładzie pokazano, jak zaimplementować tę metodę dla **obiektu CDebugSymbolProvider,** który udostępnia interfejs [IDebugComPlusSymbolProvider.](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)

```cpp
HRESULT CDebugSymbolProvider::GetSymAttribute(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    _mdToken tokParent,
    __in_z LPOLESTR pstrName,
    ULONG32 cBuffer,
    ULONG32 *pcBuffer,
    BYTE buffer[])
{
    HRESULT hr = S_OK;
    CComPtr<CModule> pModule;
    Module_ID idModule(ulAppDomainID, guidModule);

    METHOD_ENTRY( CDebugSymbolProvider::GetSymAttribute );

    IfFailGo( GetModule( idModule, &pModule) );

    IfFailGo( pModule->GetSymAttribute( tokParent, pstrName, cBuffer, pcBuffer, buffer ) );

Error:

    METHOD_EXIT(CDebugSymbolProvider::GetSymAttribute, hr);

    return hr;
}
```

## <a name="see-also"></a>Zobacz też
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
