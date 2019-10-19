---
title: 'IRemoteDebugApplication:: QueryAlive | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.QueryAlive
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::QueryAlive
ms.assetid: 08e49d3b-6fb3-4438-960e-f05395ba9b17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3edc4fc007a2372c429b0bbece394cb1c30a2770
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577474"
---
# <a name="iremotedebugapplicationqueryalive"></a>IRemoteDebugApplication::QueryAlive
Wskazuje, czy aplikacja jest odpowiedzią.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT QueryAlive();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda wskazuje, czy aplikacja odpowiada. Implementacje tej metody powinny zawsze zwracać `S_OK`.  
  
 Jeśli proces aplikacji nieoczekiwanie zakończy działanie, COM zwróci błąd z organizatora serwera proxy dla wywołań tej metody.  
  
## <a name="see-also"></a>Zobacz także  
 [IRemoteDebugApplication, interfejs](../../winscript/reference/iremotedebugapplication-interface.md)