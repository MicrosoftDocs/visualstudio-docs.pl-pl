---
title: IActiveScript::GetCurrentScriptThreadID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetCurrentScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetCurrentScriptThreadID
ms.assetid: b09e8b48-4209-480e-8b71-e99ee9ae2e17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e1b6e7bae7d78c18e11cd1aac8d0844fb9e90a5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935659"
---
# <a name="iactivescriptgetcurrentscriptthreadid"></a>IActiveScript::GetCurrentScriptThreadID
Pobiera identyfikator aktualnie wykonywany wątek skryptów aparatu zdefiniowane. Identyfikator może być używany w kolejnych wywołaniach do metod Kontrola wykonywania wątków skryptu takich jak [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstidThread`  
 [out] Adres zmiennej, która odbiera identyfikator wątku skryptu, które są skojarzone z bieżącym wątkiem. Interpretacja tego identyfikatora pozostało do silnika wykonywania skryptów, ale może być po prostu kopię Windows identyfikator wątku. Jeśli wątek Win32 kończy działanie, ten identyfikator staje się nieprzypisane i następnie można przypisać do innego wątku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` w przypadku powodzenia lub `E_POINTER` Jeśli określono nieprawidłowy wskaźnik.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda może być wywołana z wątków-base bez skutkuje objaśnienia-base na obiektach hosta lub do [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScript](../../winscript/reference/iactivescript.md)