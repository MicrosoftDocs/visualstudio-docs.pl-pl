---
title: 'IActiveScriptError:: GetSourcePosition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptError.GetSourcePosition
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptError_GetSourcePosition
ms.assetid: ae9b26b1-82a7-4645-9686-3261d8248664
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76ed307f988a3e5bf77ff978c466eda6e5dfee18
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576886"
---
# <a name="iactivescripterrorgetsourceposition"></a>IActiveScriptError::GetSourcePosition
Pobiera lokalizację w kodzie źródłowym, w której wystąpił błąd podczas wykonywania skryptu przez aparat skryptów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetSourcePosition(  
    DWORD *pdwSourceContext,  // context cookie  
    ULONG *pulLineNumber,     // line number of error  
    LONG *pichCharPosition    // character position of error  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwSourceContext`  
 określoną Adres zmiennej, która odbiera plik cookie identyfikujący kontekst. Interpretacja tego parametru zależy od aplikacji hosta.  
  
 `pulLineNumber`  
 określoną Adres zmiennej, która otrzymuje numer wiersza w pliku źródłowym, w którym wystąpił błąd.  
  
 `pichCharPosition`  
 określoną Adres zmiennej, która otrzymuje pozycję znaku w wierszu, w którym wystąpił błąd.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`, jeśli się powiedzie, lub `E_FAIL`, jeśli lokalizacja nie została pobrana.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)