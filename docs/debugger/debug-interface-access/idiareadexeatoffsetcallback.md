---
title: Idiareadexeatoffsetcallback — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback interface
ms.assetid: 3c961641-3ce3-4bc3-bd6e-a802fa3bec49
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a52f34987ac938f09ecbb350d280deb1235589c0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53823532"
---
# <a name="idiareadexeatoffsetcallback"></a>IDiaReadExeAtOffsetCallback
Umożliwia aplikacji klienta podać plik wykonywalny określony przez położenie pliku w bajtach.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDiaReadExeAtOffsetCallback : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDiaReadExeAtOffsetCallback`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDiaReadExeAtOffsetCallback::ReadExecutableAt](../../debugger/debug-interface-access/idiareadexeatoffsetcallback-readexecutableat.md)|Odczytuje określoną liczbę bajtów, rozpoczynając od określonego przesunięcia przy użyciu pliku wykonywalnego.|  
  
## <a name="remarks"></a>Uwagi  
 Aplikacja kliencka implementuje ten interfejs zapewnić bajtów wykonywalny wykorzystujący przesunięcie bezwzględna do pliku wykonywalnego. Aby użyć względny adres wirtualny, należy zaimplementować [idiareadexeatrvacallback —](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ta metoda jest implementowana przez aplikację klienta i przekazywane do [idiadatasource::loaddataforexe —](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodę jako alternatywną metodą dla odczytu pliku.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: dia2.h  
  
 Biblioteka: diaguids.lib  
  
 Biblioteki DLL: msdia80.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy (debugowanie zestaw SDK dostępu do interfejsu)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiadatasource::loaddataforexe —](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)