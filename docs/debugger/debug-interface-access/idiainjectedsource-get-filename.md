---
title: Idiainjectedsource::get_filename — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_filename method
ms.assetid: 20f4fc68-335a-4971-b3a6-76501f0e8b19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99a96f1aac998c95f467fb644d67a49535749df4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54955989"
---
# <a name="idiainjectedsourcegetfilename"></a>IDiaInjectedSource::get_filename
Pobiera nazwę pliku źródłowego.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_filename (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pRetVal  
 [out] Zwraca nazwę pliku źródłowego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)