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
ms.openlocfilehash: 5b2657127726e387e81a5b28c639abbaa5399019
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741441"
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
Utrzymuje kontekst stosu między wywołaniami metody [IDiaFrameData:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) .

## <a name="syntax"></a>Składnia

```
IDiaStackWalkFrame : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDiaStackWalkFrame`.

|Metoda|Opis|
|------------|-----------------|
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|Pobiera wartość rejestru.|
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|Ustawia wartość rejestru.|
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|Odczytuje pamięć z obrazu.|
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|Przeszukuje określoną ramkę stosu dla najbliższego adresu zwrotnego funkcji.|
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|Przeszukuje określoną ramkę stosu dla adresu zwrotnego pod określonym adresem lub w jego prawie.|

## <a name="remarks"></a>Uwagi
 Ten interfejs jest używany podczas wykonywania programu w celu odczytu i zapisu rejestrów, a także uzyskiwania dostępu do pamięci i znajdowania zwrotnych adresów.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Aplikacja kliencka implementuje ten interfejs i przekazuje wystąpienie interfejsu do metody [IDiaFrameData:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) . To samo wystąpienie tego interfejsu jest używane ponownie i ponownie w celu utrzymania stanu rejestrów podczas każdego wywołania metody `execute`. Metoda `execute` używa również tego interfejsu do określenia adresu zwrotnego.

## <a name="requirements"></a>Wymagania
 Nagłówek: dia2. h

 Biblioteka: diaguids. lib

 DLL: msdia80. dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)