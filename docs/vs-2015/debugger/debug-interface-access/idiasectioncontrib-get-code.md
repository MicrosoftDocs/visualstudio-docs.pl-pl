---
title: 'IDiaSectionContrib:: get_code | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_code method
ms.assetid: f9ccf7a6-46e7-4a1d-9d5c-97272e17bbbb
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6a11e8ee423f096e4b069a085652d9211ee17693
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187254"
---
# <a name="idiasectioncontribget_code"></a>IDiaSectionContrib::get_code
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera flagę wskazującą, czy sekcja zawiera kod wykonywalny.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_code (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 określoną Zwraca `TRUE` czy sekcja zawiera kod wykonywalny; w przeciwnym razie zwraca `FALSE` .  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
