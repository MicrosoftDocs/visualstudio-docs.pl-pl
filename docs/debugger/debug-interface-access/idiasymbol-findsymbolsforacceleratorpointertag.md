---
title: IDiaSymbol::findSymbolsForAcceleratorPointerTag | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: fb66852c-c5f7-4140-b9fe-20cb4e51a9fe
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7bf55f372b9beb0a4cb0feda0dc5869ee9eb7c5f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62827733"
---
# <a name="idiasymbolfindsymbolsforacceleratorpointertag"></a>IDiaSymbol::findSymbolsForAcceleratorPointerTag
Zwraca liczbę znaczników wskaźnika akceleratora w funkcji skrótową, C++ AMP.

## <a name="syntax"></a>Składnia

```C++
HRESULT findSymbolsForAccleratorPointerTag (
   DWORD             tagValue,
   IDiaEnumSymbols** ppResult);
```

#### <a name="parameters"></a>Parametry
 `tagValue`

[in] Wartość tagu wskaźnika, dla której rekordy symbol pointee zostaną znalezione.

 `ppResult`

[out] Wskaźnik do `IDiaEnumSymbols` wskaźnika interfejsu, który jest inicjowany z wynikiem.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)