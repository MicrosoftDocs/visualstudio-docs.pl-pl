---
title: 'IActiveScript:: GetCurrentScriptThreadID | Microsoft Docs'
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
ms.openlocfilehash: dedb16e0c007ed05370fb54835f84f00784c1ae4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575765"
---
# <a name="iactivescriptgetcurrentscriptthreadid"></a>IActiveScript::GetCurrentScriptThreadID
Pobiera identyfikator zdefiniowany przez aparat skryptów dla aktualnie wykonywanego wątku. Identyfikatora można użyć w kolejnych wywołaniach metod kontroli wykonywania wątku skryptu, takich jak Metoda [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstidThread`  
 określoną Adres zmiennej, która odbiera identyfikator wątku skryptu skojarzonego z bieżącym wątkiem. Interpretacja tego identyfikatora pozostała do aparatu skryptów, ale może to być tylko kopia identyfikatora wątku systemu Windows. Jeśli wątek Win32 zostanie przerwany, ten identyfikator stanie się nieprzypisany i następnie może zostać przypisany do innego wątku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`, jeśli się powiedzie, lub `E_POINTER`, jeśli określono nieprawidłowy wskaźnik.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda może być wywoływana z wątków niebazowych bez wypełniania niepodstawowego wywołania obiektów hosta lub interfejsu [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScript](../../winscript/reference/iactivescript.md)