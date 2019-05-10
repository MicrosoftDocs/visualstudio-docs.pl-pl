---
title: IDebugSymbolProvider::GetAddressesFromPosition | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1276a1c1a076c624ffcfd78c3b7f9d09df2a6e01
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65224012"
---
# <a name="idebugsymbolprovidergetaddressesfromposition"></a>IDebugSymbolProvider::GetAddressesFromPosition
Ta metoda mapuje położenie dokumentu na tablicę adresów debugowania.

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

 [in] Położenie dokumentu.

 `fStatmentOnly`\

 [in] W przypadku opcji TRUE ogranicza adresy debugowania do pojedynczej instrukcji.

 `ppEnumBegAddresses`\

 [out] Zwraca moduł wyliczający dla wyjścia adresów debugowania skojarzone z tym instrukcja lub wiersza.

 `ppEnumEndAddresses`\

 [out] Zwraca [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) modułu wyliczającego dla końcowy adresów debugowania skojarzone z tym instrukcja lub wiersza.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Położenie dokumentu zazwyczaj wskazuje zakres wierszy źródłowych. Ta metoda zapewnia początkowy i końcowy adres debugowania powiązanych z tymi wierszami. W niektórych językach umożliwiają instrukcji, które rozciągają się wiele wierszy lub wiersze, które zawiera więcej niż jedną instrukcję. Ta metoda zapewnia flagi, aby ograniczyć adresy debugowania do pojedynczej instrukcji.

 Istnieje możliwość dla pojedynczej instrukcji wielu adresów debugowania, tak jak w przypadku szablonów.

## <a name="see-also"></a>Zobacz także
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)