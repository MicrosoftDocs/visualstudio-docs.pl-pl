---
title: IDiaStackWalkHelper | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2 interface
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 357d4b9482fb8a5ba7f287ed305ff71083f97590
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51770054"
---
# <a name="idiastackwalkhelper"></a>IDiaStackWalkHelper
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ułatwia zalet stosu przy użyciu pliku bazy danych (PDB) programu debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
IDiaStackWalkHelper: IUnknown  
  
```  
  
## <a name="methods-in-vtable-order"></a>Metody w VTable kolejności  
 W poniższej tabeli przedstawiono metody `IDiaStackWalkHelper`:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDiaStackWalkHelper::get_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|Pobiera wartość rejestru.|  
|[IDiaStackWalkHelper::put_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|Ustawia wartość rejestru.|  
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|Odczytuje blok danych z pliku wykonywalnego obrazu w pamięci.|  
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|Wyszukuje ramki określonego stosu, dla najbliższej adres zwrotny funkcji.|  
|[IDiaStackWalkHelper::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddressstart.md)|Wyszukuje ramki określonego stosu, dla adres zwrotny po lub w pobliżu adresu określonego stosu.|  
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|Pobiera ramki stosu, który zawiera określony wirtualny adres.|  
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|Pobiera symbol, który zawiera określony adres wirtualny. **Uwaga:** Symbol musi mieć typ `SymTagFunctionType` (wartość z zakresu od [symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md) wyliczenia).|  
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|Zwraca skojarzonego z określonym wirtualnym adresem bloku danych PDATA.|  
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|Pobiera początkowy adres wirtualny plik wykonywalny podany wirtualny adres gdzieś w obszarze pamięci pliku wykonywalnego.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest wywoływany przez kod DIA, aby uzyskać informacje o pliku wykonywalnego, aby utworzyć listę ramek stosu podczas wykonywania programu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Aplikacja kliencka implementuje ten interfejs do obsługi zalet stosu podczas wykonywania programu. Wystąpienie tego interfejsu jest przekazywany do [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) lub [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Dia2.h  
  
 Biblioteka: diaguids.lib  
  
 Biblioteki DLL: msdia80.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy (debugowanie zestaw SDK dostępu do interfejsu)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiaframedata —](../../debugger/debug-interface-access/idiaframedata.md)   
 [Symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)



