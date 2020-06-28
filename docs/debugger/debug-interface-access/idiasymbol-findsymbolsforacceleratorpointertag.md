---
title: 'IDiaSymbol:: findSymbolsForAcceleratorPointerTag | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: fb66852c-c5f7-4140-b9fe-20cb4e51a9fe
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3219312a96e5ad23c0eef519d077faedacb2b824
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464423"
---
# <a name="idiasymbolfindsymbolsforacceleratorpointertag"></a>IDiaSymbol::findSymbolsForAcceleratorPointerTag
Zwraca liczbę tagów wskaźnika akceleratora w funkcji zastępczej C++ AMP.

## <a name="syntax"></a>Składnia

```C++
HRESULT findSymbolsForAccleratorPointerTag (
   DWORD             tagValue,
   IDiaEnumSymbols** ppResult);
```

#### <a name="parameters"></a>Parametry
 `tagValue`

podczas Wartość znacznika wskaźnika, dla którego znaleziono rekordy symboli pointee.

 `ppResult`

określoną Wskaźnik do `IDiaEnumSymbols` wskaźnika interfejsu, który jest inicjowany z wynikiem.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)