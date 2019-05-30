---
title: IDebugComPlusSymbolProvider::GetLocalVariablelayout | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetLocalVariablelayout
- IDebugComPlusSymbolProvider::GetLocalVariablelayout
ms.assetid: b7328d85-e5e9-4d9f-bcd1-e7711fd33878
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c92bdab6c3bbe7196e5f1df68758bcce4a9f2063
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66336760"
---
# <a name="idebugcomplussymbolprovidergetlocalvariablelayout"></a>IDebugComPlusSymbolProvider::GetLocalVariablelayout
Pobiera układ zmienne lokalne, aby uzyskać zestaw metod.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetLocalVariablelayout(
    ULONG32   ulAppDomainID,
    GUID      guidModule,
    ULONG32   cMethods,
    _mdToken  rgMethodTokens[],
    IStream** pStreamLayout
);
```

```csharp
int GetLocalVariablelayout(
    uint        ulAppDomainID,
    Guid        guidModule,
    uint        cMethods,
    int[]       rgMethodTokens,
    out IStream pStreamLayout
);
```

## <a name="parameters"></a>Parametry
`ulAppDomainID`\
[in] Identyfikator domeny aplikacji.

`guidModule`\
[in] Unikatowy identyfikator modułu.

`cMethods`\
[in] Liczba metoda tokenów w `rgMethodTokens` tablicy.

`rgMethodTokens`\
[in] Tablica metody.

`pStreamLayout`\
[out] Strumień tekst, który zawiera zmienną układu.

## <a name="return-value"></a>Wartość zwracana
Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje, jak zaimplementować tę metodę, aby uzyskać **CDebugSymbolProvider** obiekt ujawniający [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfejsu.

```cpp
HRESULT CDebugSymbolProvider::GetLocalVariablelayout(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    ULONG32 cMethods,
    _mdToken rgMethodTokens[],
    IStream** ppStreamLayout)
{
    HRESULT hr = S_OK;

    METHOD_ENTRY(CDebugSymbolProvider::GetLocalVariablelayout);

    CComPtr<ISymUnmanagedReader> symReader;
    IfFailRet(GetSymUnmanagedReader(ulAppDomainID, guidModule, (IUnknown **) &symReader));
    CComPtr<IStream> stream;
    IfFailRet(CreateStreamOnHGlobal(NULL, true, &stream));

    for (ULONG32 iMethod = 0; iMethod < cMethods; iMethod += 1)
    {
        CComPtr<ISymUnmanagedMethod> method;
        IfFailRet(symReader->GetMethod(rgMethodTokens[iMethod], &method));
        CComPtr<ISymUnmanagedScope> rootScope;
        IfFailRet(method->GetRootScope(&rootScope));

        //
        // Add the method's variables to the stream
        //
        IfFailRet(AddScopeToStream(rootScope, 0, stream));

        // do end of method marker
        ULONG32 depth = 0xFFFFFFFF;
        ULONG cb = 0;
        IfFailRet(stream->Write(&depth, sizeof(depth), &cb));
    }

    LARGE_INTEGER pos;
    pos.QuadPart = 0;
    IfFailRet(stream->Seek(pos, STREAM_SEEK_SET, 0));
    *ppStreamLayout = stream.Detach();

    METHOD_EXIT(CDebugSymbolProvider::GetLocalVariablelayout, hr);
    return hr;
}
```

## <a name="see-also"></a>Zobacz także
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
