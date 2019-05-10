---
title: Idiaenumframedata::SKIP — | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Skip method
ms.assetid: 67140b4c-7125-4895-932d-42412326da29
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ff8b58f6d36e9ce9759e2672f7e438bc0019fc1e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54773460"
---
# <a name="idiaenumframedataskip"></a>IDiaEnumFrameData::Skip
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pomija określoną liczbę elementów danych ramki w kolejności wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 celt  
 [in] Liczba elementów danych ramki w kolejności wyliczenie, aby pominąć.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` Jeśli nie ma żadnych więcej rekordów do pominięcia.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
