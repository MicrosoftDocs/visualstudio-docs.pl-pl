---
title: Funkcja SccUninitialize | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8dba45116c956c1edc1a8ffb691397375345c661
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54967209"
---
# <a name="sccuninitialize-function"></a>SccUninitialize, funkcja
Ta funkcja czyści wszystkie alokacje lub otwartych połączeń utworzonych przez poprzednie wywołanie [SccInitialize](../extensibility/sccinitialize-function.md) w ramach przygotowania do zamykania wtyczka do kontroli źródła.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccUninitialize (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Wskaźnik do struktury kontekście wtyczki kontroli źródła, utworzone w [SccInitialize](../extensibility/sccinitialize-function.md).  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Oczyszczania została ukończona pomyślnie.|  
  
## <a name="remarks"></a>Uwagi  
 Wtyczka do kontroli źródła jest odpowiedzialny za przygotowywanie zamknięcie i zwalnianie pamięci, że wtyczka została przydzielona w strukturze kontekstu. Funkcja jest wywoływana raz dla każdego wystąpienia danego dodatku typu plug-in. Wywołanie [SccInitialize](../extensibility/sccinitialize-function.md) poprzedza tego wywołania. Brak projektów nadal może być otwarty w momencie wywołania `SccUninitialize`.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)