---
title: IDiaLoadCallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback interface
ms.assetid: 2f18c64c-2cf0-43fc-a447-21e82702ca2a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ca58a206fec15bb8a9ae7f68a278a4530be47d8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743036"
---
# <a name="idialoadcallback"></a>IDiaLoadCallback
Odbiera wywołania zwrotne z DIA symbol lokalizowania procedury, dzięki czemu interfejs użytkownika może raportować postęp próby lokalizacji.

## <a name="syntax"></a>Składnia

```
IDiaLoadCallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 Ten interfejs udostępnia następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)|Wywoływana, gdy w pliku exe znaleziono katalog debugowania.|
|[IDiaLoadCallback::NotifyOpenDBG](../../debugger/debug-interface-access/idialoadcallback-notifyopendbg.md)|Wywoływana, gdy plik kandydata. dbg został otwarty.|
|[IDiaLoadCallback::NotifyOpenPDB](../../debugger/debug-interface-access/idialoadcallback-notifyopenpdb.md)|Wywołuje się, gdy plik kandydata. pdb został otwarty.|
|[IDiaLoadCallback::RestrictRegistryAccess](../../debugger/debug-interface-access/idialoadcallback-restrictregistryaccess.md)|Określa, czy zapytania rejestru mogą służyć do lokalizowania ścieżek wyszukiwania symboli.|
|[IDiaLoadCallback::RestrictSymbolServerAccess](../../debugger/debug-interface-access/idialoadcallback-restrictsymbolserveraccess.md)|Określa, czy dostęp jest dozwolony do serwera symboli, aby rozpoznać symbole.|

## <a name="remarks"></a>Uwagi
 Aplikacja kliencka implementuje ten interfejs i dostarcza odwołanie do niego w wywołaniu metody [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .

 Aby uzyskać dodatkowe ograniczenia, które mogą zostać nałożone na proces ładowania, zobacz Interfejs [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md) .

## <a name="requirements"></a>Wymagania
 Nagłówek: dia2. h

 Biblioteka: diaguids. lib

 DLL: msdia80. dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)