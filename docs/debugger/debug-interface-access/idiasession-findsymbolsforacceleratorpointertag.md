---
title: 'IDiaSession:: findSymbolsForAcceleratorPointerTag | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 95fd5e7a-c637-437e-b369-c864eef733c2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da795770ad0f6f57697bc17a4ee8cf936cfc1183
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741977"
---
# <a name="idiasessionfindsymbolsforacceleratorpointertag"></a>IDiaSession::findSymbolsForAcceleratorPointerTag
Zwraca Wyliczenie symboli dla zmiennej, do której odnosi się określona wartość tagu w funkcji zastępczej akceleratora nadrzędnego.

## <a name="syntax"></a>Składnia

```C++
HRESULT findSymbolsForAcceleratorPointerTag ( 
   IDiaSymbol*           parent,
   DWORD                 tagValue,
   IDiaEnumSymbols**     ppResult
);
```

#### <a name="parameters"></a>Parametry
 `parent`

podczas Element IDiaSymbol, który odpowiada funkcji zastępczej akceleratora do przeszukania.

 `tagValue`

podczas Wartość znacznika wskaźnika.

 `ppResult`

określoną Wskaźnik do `IDiaEnumSymbols` wskaźnika interfejsu, który jest inicjowany z wynikiem.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)