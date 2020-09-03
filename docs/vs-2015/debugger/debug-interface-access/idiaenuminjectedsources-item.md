---
title: 'IDiaEnumInjectedSources:: Item | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Item method
ms.assetid: 14846955-7270-451d-91d2-9cb34bb65187
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fec8369e07c563891d476ccbdee5ae11ec6bbdbd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202611"
---
# <a name="idiaenuminjectedsourcesitem"></a>IDiaEnumInjectedSources::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera wstrzykiwane Źródło przy użyciu indeksu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Item (   
   DWORD                index,  
   IDiaInjectedSource** injectedSource  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 index  
 podczas Indeks obiektu [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) do pobrania. Indeks jest zakresem od 0 do `count` -1, gdzie `count` jest zwracany przez metodę [IDiaEnumInjectedSources:: get_Count](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md) .  
  
 injectedSource  
 określoną Zwraca obiekt [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) reprezentujący wstrzyknięte źródło.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
