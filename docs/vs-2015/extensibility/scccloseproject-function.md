---
title: Funkcja SccCloseProject | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7d2364215f528f16d05ecf0c53b152f7334f4b4a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54797756"
---
# <a name="scccloseproject-function"></a>SccCloseProject, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja powoduje zamknięcie projektu oznaczenia końca określonej sesji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 Struktura kontekście wtyczki kontroli źródła.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Projekt został pomyślnie zamknięty.|  
|SCC_E_PROJNOTOPEN|Projekt nie jest obecnie otwarty.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|  
|SCC_E_NONSPECIFICERROR|Wystąpił nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 [SccOpenProject](../extensibility/sccopenproject-function.md) zawsze jest wywoływany przed tej funkcji. Wywołanie tej funkcji po niej wywołania `SccOpenProject` funkcji lub [SccUninitialize](../extensibility/sccuninitialize-function.md), która całkowicie zakończy połączenie do systemu kontroli źródła.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)
