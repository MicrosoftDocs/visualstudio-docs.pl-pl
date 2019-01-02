---
title: Funkcja SccGetExtendedCapabilities | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c46a81190fb1c1c9b15627b7fb9620e01faa2f53
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53819611"
---
# <a name="sccgetextendedcapabilities-function"></a>Funkcja SccGetExtendedCapabilities
Ta funkcja zwraca dodatkowe funkcje obsługiwane przez wtyczka do kontroli źródła.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccGetExtendedCapabilities(  
   LPVOID pContext,  
   LONG lSccExCaps,  
   LPBOOL pbSupported  
);  
```  
  
### <a name="parameters"></a>Parametry  
 pContext  
 [in] Wskaźnik kontekście wtyczki kontroli źródła.  
  
 lSccExCaps  
 [in] Flaga określająca, rozszerzone możliwości, do których chcesz przetestować (znajdują się w tabeli rozszerzonego kodu możliwości [flagi możliwości](../extensibility/capability-flags.md) dla flag możliwe).  
  
 pbSupported  
 [out] Zwraca wartość różna od zera (`TRUE`), jeśli określona funkcja jest obsługiwana; w przeciwnym razie zwraca wartość zero (`FALSE`).  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Operacja możliwości pobrania została ukończona pomyślnie.|  
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Wystąpił nieznany lub nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana na żądanie; oznacza to, gdy możliwości musi zostać przetestowana, ta metoda jest wywoływana w celu określenia, czy, funkcja jest obsługiwana. Określono tylko jedną flagę w danym momencie.  
  
## <a name="see-also"></a>Zobacz także  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [Kody błędów](../extensibility/error-codes.md)   
 [Flagi możliwości](../extensibility/capability-flags.md)