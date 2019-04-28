---
title: IActiveScriptError::GetSourcePosition | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 4446235a9584bc45fad84b6f92ecc02592e554f3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009627"
---
# <a name="iactivescripterrorgetsourceposition"></a>IActiveScriptError::GetSourcePosition
Pobiera lokalizację w kodzie źródłowym, w której wystąpił błąd, gdy aparat skryptów był uruchomiony skrypt.  
  
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
 [out] Adres zmiennej, która odbiera plik cookie, który identyfikuje kontekst. Interpretacja tego parametru, zależy od aplikacji hosta.  
  
 `pulLineNumber`  
 [out] Adres zmiennej, która odbiera numer wiersza w pliku źródłowym, w którym wystąpił błąd.  
  
 `pichCharPosition`  
 [out] Adres zmiennej, która odbiera pozycja znaku w wierszu, w którym wystąpił błąd.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` w przypadku powodzenia lub `E_FAIL` Jeśli lokalizacji nie została pobrana.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)