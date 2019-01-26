---
title: Idiaenumframedata::clone — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Clone Method
ms.assetid: 28a17300-1626-422f-a17a-3a4d3872c37c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3de325e78869abd4298d2d4ad45ef0643a96ece7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54967764"
---
# <a name="idiaenumframedataclone"></a>IDiaEnumFrameData::Clone
Tworzy moduł wyliczający, który zawiera ten sam stan wyliczenia jako bieżącego modułu wyliczającego.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT Clone(   
   IDiaEnumFrameData** ppenum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 ppenum  
 [out] Zwraca [idiaenumframedata —](../../debugger/debug-interface-access/idiaenumframedata.md) obiekt, który zawiera zduplikowane modułu wyliczającego. Ramki, w których dane są duplikowane tylko moduł wyliczający.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)