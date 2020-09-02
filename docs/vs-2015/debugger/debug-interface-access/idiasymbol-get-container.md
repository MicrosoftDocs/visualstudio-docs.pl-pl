---
title: 'IDiaSymbol:: get_container | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_container method
ms.assetid: 24e832eb-80b3-484c-a41b-11477ec9de99
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b759c8fc65130c37f24e8ec03bbcebf3a52241d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64810670"
---
# <a name="idiasymbolget_container"></a>IDiaSymbol::get_container
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ta funkcja Pobiera wskaźnik do symbolu reprezentującego element nadrzędny/kontener tego symbolu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_container(  
   IDiaSymbol **pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 określoną Zwraca wskaźnik do `IDiaSymbol` zawierającego je informacji o kontenerze tego symbolu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca S_FALSE lub kod błędu.  
  
> [!NOTE]
> Wartość zwracana przez S_FALSE oznacza, że właściwość nie jest dostępna dla symbolu.  
  
## <a name="requirements"></a>Wymagania  
  
|Wymaganie|Opis|  
|-----------------|-----------------|  
|Nagłówki|dia2. h|  
|Wersja:|DIA SDK v 8.0|  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
