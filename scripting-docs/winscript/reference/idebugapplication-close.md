---
title: 'IDebugApplication:: Close | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.Close
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::Close
ms.assetid: d19baa07-3f3b-47de-8185-5eb3e7ac8b46
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0445e9aed990da684efac6675e05183fd939973f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575577"
---
# <a name="idebugapplicationclose"></a>IDebugApplication::Close
Powoduje, że ta aplikacja zwolni wszystkie odwołania i wprowadzi nieaktywny stan.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Close();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Zazwyczaj właściciel aplikacji wywołuje tę metodę, gdy aplikacja zostanie zakończona.  
  
 Ta metoda powoduje wywoływanie `IApplicationDebugger::onClose`.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugApplication  interfejsu](../../winscript/reference/idebugapplication-interface.md)  
 [IApplicationDebugger::onClose](../../winscript/reference/iapplicationdebugger-onclose.md)