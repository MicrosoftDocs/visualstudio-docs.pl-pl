---
title: 'IActiveScript:: GetScriptThreadID | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadID
ms.assetid: 2595d76e-30b5-429f-88b4-1d026645dd9b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a0fb1eebfcb6ed100056289fab6bce662f86a7b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575702"
---
# <a name="iactivescriptgetscriptthreadid"></a>IActiveScript::GetScriptThreadID
Pobiera identyfikator zdefiniowany przez aparat skryptu dla wątku skojarzonego z danym wątkiem Win32.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwWin32ThreadID`,  
 podczas Identyfikator wątku działającego wątku Win32 w bieżącym procesie. Użyj funkcji [IActiveScript:: GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md) , aby pobrać identyfikator wątku aktualnie wykonywanego wątku.  
  
 `pstidThread`,  
 określoną Adres zmiennej, która odbiera identyfikator wątku skryptu skojarzonego z danym wątkiem Win32. Interpretacja tego identyfikatora pozostała do aparatu skryptów, ale może to być tylko kopia identyfikatora wątku systemu Windows. Należy pamiętać, że jeśli wątek Win32 zostanie zakończony, ten identyfikator zostanie cofnięty i może zostać przypisany do innego wątku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Prawnego.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_UNEXPECTED`|Wywołanie nie było oczekiwane (na przykład aparat skryptów nie został jeszcze załadowany lub zainicjowany) i w związku z tym nie powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Pobranego identyfikatora można użyć w kolejnych wywołaniach metod sterowania wykonywaniem wątków skryptu, takich jak Metoda [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) .  
  
 Ta metoda może być wywoływana z wątków niebazowych bez wypełniania niepodstawowego wywołania do obiektów hosta lub interfejsu [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) .  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScript](../../winscript/reference/iactivescript.md)