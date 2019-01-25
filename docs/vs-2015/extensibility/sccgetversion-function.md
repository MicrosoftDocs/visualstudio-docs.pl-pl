---
title: Funkcja SccGetVersion | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a4e548f1f2b82a97206cdf41174a8c1c7d61e885
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54763787"
---
# <a name="sccgetversion-function"></a>SccGetVersion, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja pobiera numer wersji interfejsu API wtyczki kontroli źródła obsługiwane przez wtyczka do kontroli źródła.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
