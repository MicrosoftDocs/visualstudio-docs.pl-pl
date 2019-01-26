---
title: Funkcja SccGetVersion | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1fe071cb0c0de62f4e59785f829adfaacc992336
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55023541"
---
# <a name="sccgetversion-function"></a>SccGetVersion, funkcja
Ta funkcja pobiera numer wersji interfejsu API wtyczki kontroli źródła obsługiwane przez wtyczka do kontroli źródła.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
LONG SccGetVersion(void);  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak.  
  
## <a name="return-value"></a>Wartość zwracana  
 A `LONG` typu danych, który zawiera numer wersji obsługiwanych API wtyczki kontroli źródła:  
  
|WORD|Opis|  
|----------|-----------------|  
|HIWORD|Wersja główna|  
|LOWORD|Wersja pomocnicza|  
  
## <a name="remarks"></a>Uwagi  
 Na przykład jeśli wtyczka do kontroli źródła obsługuje interfejs API wtyczki kontroli źródła w wersji 1.3, ta funkcja zwróci 0x0103.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)