---
title: 'IDiaSession:: findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf05d60499da0317461d03d05579dce6124385f7
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465532"
---
# <a name="idiasessionfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
Mając odpowiednią wartość tagu, ta metoda zwraca Wyliczenie symboli, które znajdują się w określonej funkcji zastępczej akceleratora nadrzędnego w określonym względnym adresie wirtualnym.

## <a name="syntax"></a>Składnia

```C++
HRESULT findSymbolsByRVAForAcceleratorPointerTag ( 
   IDiaSymbol*           parent,
   DWORD                 tagValue,
   DWORD                 rva,
   IDiaEnumSymbols**     ppResult
);
```

#### <a name="parameters"></a>Parametry
 `parent`

podczas `IDiaSymbol`Odpowiada funkcji zastępczej akceleratora do przeszukania.

 `tagValue`

podczas Wartość znacznika wskaźnika.

 `rva`

podczas Względny adres wirtualny.

 `ppResult`

określoną Wskaźnik do `IDiaEnumSymbols` wskaźnika interfejsu, który jest inicjowany z wynikiem.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wywołaj tę metodę tylko w `IDiaSymbol` interfejsie, który odpowiada funkcji zastępczej akceleratora.

## <a name="see-also"></a>Zobacz też
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)