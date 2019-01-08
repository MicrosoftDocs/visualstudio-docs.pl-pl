---
title: ISimpleConnectionPoint::Advise | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: b3c0ea37e6fabb051458a11c4838061126bd98bf
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091744"
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