---
title: IEnumJsStackFrames Interface | Microsoft Docs
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
ms.openlocfilehash: 2e8302737fb4abf96c55d3ae70424cc03579b270
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963328"
---
# <a name="ienumjsstackframes-interface"></a>IEnumJsStackFrames — Interfejs
Implementowany przez debugera, aby zapewnić stosu Odwiń do biblioteki jscript9diag.dll dla języka JavaScript.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
IEnumJsStackFrames : public IUnknown;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IEnumJsStackFrames::Next, metoda](../../winscript/reference/ienumjsstackframes-next-method.md)|Pobiera określoną liczbę klatek.|  
|[IEnumJsStackFrames::Reset, metoda](../../winscript/reference/ienumjsstackframes-reset-method.md)|Resetuje ramkę stosu do pozycji przed pierwszym elementem.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja interfejsów skryptów systemu Windows](../../winscript/reference/windows-script-interfaces-reference.md)