---
title: Interfejs IEnumJsStackFrames | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 49e7b425-df17-4d7f-87ff-0bc82715c911
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4a635a802ae84b8e839159f5e2f1c4c461e05ae
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572029"
---
# <a name="ienumjsstackframes-interface"></a>IEnumJsStackFrames — Interfejs
Zaimplementowane przez debuger w celu zapewnienia operacji unwindy stosu do Jscript9diag. dll dla języka JavaScript.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
IEnumJsStackFrames : public IUnknown;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IEnumJsStackFrames::Next, metoda](../../winscript/reference/ienumjsstackframes-next-method.md)|Pobiera określoną liczbę ramek.|  
|[IEnumJsStackFrames::Reset, metoda](../../winscript/reference/ienumjsstackframes-reset-method.md)|Resetuje ramkę stosu do pozycji przed pierwszym elementem.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** Jscript9diag. h  
  
## <a name="see-also"></a>Zobacz także  
 [Dokumentacja interfejsów skryptów systemu Windows](../../winscript/reference/windows-script-interfaces-reference.md)