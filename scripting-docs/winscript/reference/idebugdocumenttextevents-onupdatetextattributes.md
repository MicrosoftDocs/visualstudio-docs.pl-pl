---
title: IDebugDocumentTextEvents::onUpdateTextAttributes | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextEvents.onUpdateTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextEvents::onUpdateTextAttributes
ms.assetid: 24a6d409-3137-4a7a-ac24-0955c109902f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 746339cb281d4d039759f350bb5516456ce142cf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62989801"
---
# <a name="idebugdocumenttexteventsonupdatetextattributes"></a>IDebugDocumentTextEvents::onUpdateTextAttributes
Wskazuje, że atrybuty tekstu skojarzonych z zakresem pozycji podstawowego znak zostały zmienione.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT onUpdateTextAttributes(  
   ULONG  cCharacterPosition,  
   ULONG  cNumToUpdate  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cCharacterPosition`  
 [in] Pozycja znaku pierwszy znak, który zmieniono atrybuty.  
  
 `cNumToUpdate`  
 [in] Liczba znaków w zakresie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda wskazuje, czy zmieniono atrybuty tekstu skojarzonych z zakresem pozycji podstawowego znak.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDocumentTextEvents, interfejs](../../winscript/reference/idebugdocumenttextevents-interface.md)