---
title: Funkcja SccGetVersion | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 16a21ab75c8390f0bb5ff5f016f2bf5b8d04c3a3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779089"
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

