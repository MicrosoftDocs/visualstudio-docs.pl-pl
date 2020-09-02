---
title: 'IDiaEnumTables:: Next | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Next method
ms.assetid: 8d7bd359-d33e-4317-9674-d89283efd7de
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 69e96ad3c19a488546ad8f2a95c94c9c521fa914
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197564"
---
# <a name="idiaenumtablesnext"></a>IDiaEnumTables::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera określoną liczbę tabel w sekwencji wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Next (   
   ULONG       celt,  
   IDiaTable** rgelt,  
   ULONG*      pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 podczas Liczba tabel w module wyliczającym do pobrania.  
  
 `rgelt`  
 określoną Tablica, która ma zostać wypełniona obiektami [IDiaTable](../../debugger/debug-interface-access/idiatable.md) , które reprezentują żądane tabele.  
  
 `pceltFetched`  
 określoną Zwraca liczbę tabel w ramach pobranego modułu wyliczającego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca `S_FALSE` czy nie ma więcej tabel. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
