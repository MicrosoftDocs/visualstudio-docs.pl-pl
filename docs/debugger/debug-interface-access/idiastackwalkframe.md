---
title: IDiaStackWalkFrame | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 343c56e3d3175c26900b0cfb4cdc3d816a324404
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56630590"
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
Utrzymuje kontekst stosu między wywołań [idiaframedata::EXECUTE —](../../debugger/debug-interface-access/idiaframedata-execute.md) metody.

## <a name="syntax"></a>Składnia

```
IDiaStackWalkFrame : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDiaStackWalkFrame`.

|Metoda|Opis|
|------------|-----------------|
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|Pobiera wartość rejestru.|
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|Ustawia wartość rejestru.|
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|Odczytuje pamięć z obrazu.|
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|Wyszukuje ramki określonego stosu, dla najbliższej adres zwrotny funkcji.|
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|Wyszukuje ramki określonego stosu, dla adres zwrotny po lub w pobliżu podanym adresem.|

## <a name="remarks"></a>Uwagi
 Ten interfejs jest używany podczas wykonywania programu odczytu i zapisu rejestrów, a także uzyskiwania dostępu do pamięci oraz znaleźć adres zwrotny.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Aplikacja kliencka implementuje ten interfejs i przekazanie wystąpienia interfejsu do [idiaframedata::EXECUTE —](../../debugger/debug-interface-access/idiaframedata-execute.md) metody. To samo wystąpienie elementu ten interfejs jest używany wielokrotnie w celu zachowania stanu rejestrów podczas każdego wywołania elementu `execute` metody. `execute` Metoda również używa tego interfejsu do określenia adres zwrotny.

## <a name="requirements"></a>Wymagania
 Nagłówek: Dia2.h

 Biblioteka: diaguids.lib

 DLL: msdia80.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)