---
title: 'IApplicationDebugger:: QueryAlive | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 867d00a4ef42aa8759496540edc1937fc6f2a0a6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577825"
---
# <a name="iapplicationdebuggerqueryalive"></a>IApplicationDebugger::QueryAlive
Wskazuje, czy debuger jest odpowiedzią.  
  
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
 Ta metoda wskazuje, czy debuger jest odpowiedzią. Implementacje tej metody powinny zawsze zwracać `S_OK`.  
  
 Jeśli proces debugera nieoczekiwanie zakończy działanie, COM zwróci błąd z kierujący serwer proxy dla wywołań tej metody.  
  
## <a name="see-also"></a>Zobacz także  
 [IApplicationDebugger, interfejs](../../winscript/reference/iapplicationdebugger-interface.md)