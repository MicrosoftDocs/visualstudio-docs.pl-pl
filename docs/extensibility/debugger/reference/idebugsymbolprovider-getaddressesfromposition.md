---
description: Ta metoda mapuje pozycję dokumentu na tablicę adresów debugowania.
title: 'IDebugSymbolProvider:: GetAddressesFromPosition | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4dd3b8fbe65a72ccf937007d19117359859ff29f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087109"
---
# <a name="idebugsymbolprovidergetaddressesfromposition"></a>IDebugSymbolProvider::GetAddressesFromPosition
Ta metoda mapuje pozycję dokumentu na tablicę adresów debugowania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetAddressesFromPosition( 
   IDebugDocumentPosition2* pDocPos,
   BOOL                     fStatmentOnly,
   IEnumDebugAddresses**    ppEnumBegAddresses,
   IEnumDebugAddresses**    ppEnumEndAddresses
);
```

```csharp
int GetAddressesFromPosition( 
   IDebugDocumentPosition2  pDocPos,
   bool                     fStatmentOnly,
   out IEnumDebugAddresses  ppEnumBegAddresses,
   out IEnumDebugAddresses  ppEnumEndAddresses
);
```

## <a name="parameters"></a>Parametry
`pDocPos`\
podczas Pozycja dokumentu.

`fStatmentOnly`\
podczas W przypadku wartości TRUE program ogranicza adresy debugowania do pojedynczej instrukcji.

`ppEnumBegAddresses`\
określoną Zwraca moduł wyliczający dla początkowych adresów debugowania skojarzonych z tą instrukcją lub wierszem.

`ppEnumEndAddresses`\
określoną Zwraca moduł wyliczający [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) dla końcowych adresów debugowania skojarzonych z tą instrukcją lub wierszem.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Pozycja dokumentu zwykle wskazuje zakres wierszy źródłowych. Ta metoda zapewnia początkową i końcową adresy debugowania skojarzone z tymi wierszami. Niektóre języki umożliwiają stosowanie instrukcji obejmujących wiele wierszy lub wierszy zawierających więcej niż jedną instrukcję. Ta metoda zapewnia flagę, aby ograniczyć adresy debugowania do pojedynczej instrukcji.

 Istnieje możliwość, że pojedyncza instrukcja ma wiele adresów debugowania, tak jak w przypadku szablonów.

## <a name="see-also"></a>Zobacz też
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
