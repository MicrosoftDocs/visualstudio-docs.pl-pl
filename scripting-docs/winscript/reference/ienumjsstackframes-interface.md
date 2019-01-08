---
title: IEnumJsStackFrames, interfejs | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 49e7b425-df17-4d7f-87ff-0bc82715c911
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c26470e02f6c7e5d8911df7e743bce0cb0e560bb
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087883"
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