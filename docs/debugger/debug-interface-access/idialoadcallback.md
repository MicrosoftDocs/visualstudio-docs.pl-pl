---
description: Odbiera wywołania zwrotne z DIA symbol lokalizowania procedury, dzięki czemu interfejs użytkownika może raportować postęp próby lokalizacji.
title: IDiaLoadCallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback interface
ms.assetid: 2f18c64c-2cf0-43fc-a447-21e82702ca2a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9a283a40ae39c53a4a96f80adb633b92ba68f637
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157470"
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

 DLL: msdia80.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
