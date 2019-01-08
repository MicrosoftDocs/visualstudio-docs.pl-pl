---
title: IApplicationDebugger::QueryAlive | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.QueryAlive
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::QueryAlive
ms.assetid: 41181ebb-a3bf-4e41-82af-d6c7348dc706
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 00055eaaf79e24a9f59c380318b9c24fa476f1af
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096073"
---
# <a name="iapplicationdebuggerqueryalive"></a>IApplicationDebugger::QueryAlive
Wskazuje, czy debuger jest elastyczny.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT QueryAlive();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda wskazuje, czy debuger jest elastyczny. Implementacje tej metody zawsze powinna zwrócić `S_OK`.  
  
 Jeśli proces debugera zostaje nieoczekiwanie zamknięty, COM zwraca błąd z serwera proxy kierujące do wywołania tej metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IApplicationDebugger, interfejs](../../winscript/reference/iapplicationdebugger-interface.md)