---
title: Funkcja SccGetUserOption | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0f73eff3f1be51045381c0eaa76d5d3914d8e9ec
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53869271"
---
# <a name="sccgetuseroption-function"></a>SccGetUserOption, funkcja
Ta funkcja pobiera różnorodne opcje specyficzne dla użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccGetUserOption(  
   LPVOID pContext,  
   LONG nOption,  
   LPLONG lpVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pContext  
 [in] Wskaźnik kontekście wtyczki kontroli źródła.  
  
 nOption  
 [in] Opcja do pobrania (zobacz uwagi dla możliwych opcji).  
  
 lpVal  
 [out] Wartość skojarzona z opcją.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Opcja został pomyślnie pobrany.|  
|SCC_E_OPNOTSUPPORTED|opcja nie jest obsługiwana.|  
|SCC_E_NONSPECIFICERROR|Wystąpił nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Poniższe opcje są obsługiwane przez to polecenie:  
  
|Opcja użytkownika|Opis|  
|-----------------|-----------------|  
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Określa, czy użytkownik chce zapoznaj się z lokalną wersję plików. `lpVal` przypisano `SCC_USEROPT_COLV_YES` (użytkownik chce zapoznaj się z lokalnymi plikami) lub `SCC_USEROPT_COLV_NO`.|  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [Kody błędów](../extensibility/error-codes.md)