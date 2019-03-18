---
title: ISimpleConnectionPoint::Advise | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 98db9c92f682808ce8ecc9f6aa382a2eb2bd8495
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58153113"
---
# <a name="isimpleconnectionpointadvise"></a>ISimpleConnectionPoint::Advise
Ustanawia połączenie między obiektu punktu połączenia proste a zbiornikiem klienta.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdisp`  
 [in] Wskaźnik do `IDispatch` interfejsu na komputerze klienckim przez poinstruuj ujścia. Zbiornikiem klienta odbiera połączenia wychodzące z punktu połączenia proste.  
  
 `pdwCookie`  
 [out] Wskaźnik do zwrócony token, który unikatowo identyfikuje tego połączenia. Obiekt wywołujący używa tego tokenu później można usunąć połączenia przez przekazanie jej do `ISimpleConnectionPoint::Unadvise` metody. Jeśli połączenie nie zostało pomyślnie nawiązane, ta wartość wynosi zero.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda ustanawia połączenie między obiektu punktu połączenia proste a zbiornikiem klienta.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)   
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)