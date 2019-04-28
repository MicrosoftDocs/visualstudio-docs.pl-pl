---
title: IDiaLoadCallback::NotifyOpenPDB | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyOpenPDB method
ms.assetid: c0547f99-8468-4e57-82ca-9ef7d6707c8a
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e5945ba54f1c09f4f13d2a982e90a3bb58cfb5f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839761"
---
# <a name="idialoadcallbacknotifyopenpdb"></a>IDiaLoadCallback::NotifyOpenPDB
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wywołuje się, gdy jest otwarty plik .pdb Release candidate.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT NotifyOpenPDB (   
   LPCOLESTR pdbPath,  
   HRESULT   resultCode  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdbPath`  
 [in] Pełna ścieżka pliku .pdb.  
  
 `resultCode`  
 [in] Kod, który pokazuje Powodzenie (`S_OK`) lub niepowodzenie obciążenia, jakie mają zastosowanie do tego pliku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Kod powrotny zwykle jest ignorowany.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
