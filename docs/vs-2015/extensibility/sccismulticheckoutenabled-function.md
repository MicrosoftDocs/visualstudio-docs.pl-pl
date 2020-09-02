---
title: Funkcja SccIsMultiCheckoutEnabled | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 65641803c1fdcb4645bbc20f6cbc845e5d326689
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200064"
---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja sprawdza, czy wtyczka do kontroli źródła zezwala na wiele wyewidencjonowania pliku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
SCCRTN SccIsMultiCheckoutEnabled(  
   LPVOID pContext,  
   LPBOOL pbMultiCheckout  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pContext  
 podczas Struktura kontekstu wtyczki kontroli źródła.  
  
 pbMultiCheckout  
 określoną Określa, czy dla tego projektu włączono wiele wyewidencjonowania (wartość nierówna oznacza, że obsługiwane są wiele wyewidencjonowania).  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Sprawdzenie zakończyło się pomyślnie.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 IDE wykonuje dwie testy, aby określić, czy pliki mogą być wyewidencjonowane jednocześnie przez więcej niż jednego użytkownika. Po pierwsze system kontroli źródła musi obsługiwać wiele wyewidencjonowania. Wtyczka do kontroli źródła może określić tę możliwość podczas inicjowania, określając `SCC_CAP_MULTICHECKOUT` . Następnie jako drugie sprawdzenie, IDE wywołuje tę funkcję, aby określić, czy bieżący projekt obsługuje wiele wyewidencjonowania. Jeśli dla wybranego projektu są obsługiwane wiele wyewidencjonowania, Wtyczka zwraca kod sukcesu i ustawia `pbMultiCheckout` wartość różną od zera ( `TRUE` ) lub `FALSE` .  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
