---
title: 'IDiaEnumSymbolsByAddr:: Next | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Next method
ms.assetid: a1320587-7ce7-401f-9548-2f8bcece5cc3
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fc58c8da54380b8a835d64fcc5dc079bb8d8023e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189649"
---
# <a name="idiaenumsymbolsbyaddrnext"></a>IDiaEnumSymbolsByAddr::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera następne symbole w kolejności według adresu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Next (   
   ULONG        celt,   
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 celt  
 podczas Liczba symboli w module wyliczającym do pobrania.  
  
 rgelt  
 określoną Tablica, która ma zostać wypełniona obiektem [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , który reprezentuje żądane symbole.  
  
 pceltFetched  
 określoną Zwraca liczbę symboli w ramach pobranego modułu wyliczającego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca `S_FALSE` czy nie ma więcej symboli. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda aktualizuje pozycję modułu wyliczającego o liczbę pobranych elementów.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
