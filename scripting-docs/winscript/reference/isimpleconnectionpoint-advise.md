---
title: 'ISimpleConnectionPoint:: Advise | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Advise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Advise
ms.assetid: 59ded60d-b938-4110-aca3-e69ba234ca9a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7d08d4774dffbfd840c674b15abe82bedb37e5f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571826"
---
# <a name="isimpleconnectionpointadvise"></a>ISimpleConnectionPoint::Advise
Ustanawia połączenie między obiektem prostego punktu połączenia i ujściam klienta.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdisp`  
 podczas Wskaźnik do interfejsu `IDispatch`owego w odniesieniu do ujścia klienta. Ujścia klienta odbiera wychodzące wywołania z prostego punktu połączenia.  
  
 `pdwCookie`  
 określoną Wskaźnik do zwróconego tokenu, który jednoznacznie identyfikuje to połączenie. Obiekt wywołujący używa tego tokenu później do usunięcia połączenia przez przekazanie go do metody `ISimpleConnectionPoint::Unadvise`. Jeśli połączenie nie zostało pomyślnie ustanowione, ta wartość jest równa zero.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda ustanawia połączenie między obiektem prostego punktu połączenia i ujściam klienta.  
  
## <a name="see-also"></a>Zobacz także  
 [ISimpleConnectionPoint   interfejsu](../../winscript/reference/isimpleconnectionpoint-interface.md)  
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)