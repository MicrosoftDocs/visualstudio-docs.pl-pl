---
title: IDebugSymbolProvider::GetAddressesFromContext | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromContext
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromContext method
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7cf7599cf0fc37c16467c29c2b432f1f58b172fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719433"
---
# <a name="idebugsymbolprovidergetaddressesfromcontext"></a>IDebugSymbolProvider::GetAddressesFromContext
Ta metoda mapuje kontekst dokumentu na tablicę adresów debugowania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetAddressesFromContext( 
   IDebugDocumentContext2* pDocContext,
   BOOL                    fStatmentOnly,
   IEnumDebugAddresses**   ppEnumBegAddresses,
   IEnumDebugAddresses**   ppEnumEndAddresses
);
```

```csharp
int GetAddressesFromContext(
   IDebugDocumentContext2  pDocContext,
   bool                    fStatmentOnly,
   out IEnumDebugAddresses ppEnumBegAddresses,
   out IEnumDebugAddresses ppEnumEndAddresses
);
```

## <a name="parameters"></a>Parametry
`pDocContext`\
[w] Kontekst dokumentu.

`fStatmentOnly`\
[w] Jeśli true, ogranicza adresy debugowania do pojedynczej instrukcji.

`ppEnumBegAddresses`\
[na zewnątrz] Zwraca wyliczenia dla początkowych adresów debugowania skojarzonych z tą instrukcją lub wierszem.

`ppEnumEndAddresses`\
[na zewnątrz] Zwraca [wyliczenia IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) dla końcowego adresów debugowania skojarzonych z tą instrukcją lub wierszem.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Kontekst dokumentu zazwyczaj wskazuje zakres wierszy źródłowych. Ta metoda zawiera początkowe i końcowe adresy debugowania skojarzone z tymi wierszami. Niektóre języki zezwalają na instrukcje, które obejmują wiele wierszy lub wierszy, które zawierają więcej niż jedną instrukcję. Ta metoda zapewnia flagę, aby ograniczyć adresy debugowania do pojedynczej instrukcji.

 Jest możliwe dla pojedynczej instrukcji mieć wiele adresów debugowania, jak w przypadku szablonów.

## <a name="see-also"></a>Zobacz też
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
