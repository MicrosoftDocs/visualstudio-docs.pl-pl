---
title: IActiveScript::GetScriptThreadID | Microsoft Docs
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
ms.openlocfilehash: d329e08e6a17d9edcdf26e14b468c3c56f036c00
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935695"
---
# <a name="iactivescriptgetscriptthreadid"></a>IActiveScript::GetScriptThreadID
Pobiera skryptów aparatu-zdefiniowany przez identyfikator wątku skojarzone z danym wątek Win32.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwWin32ThreadID` ,  
 [in] Identyfikator wątku uruchomiony wątek Win32 w bieżącym procesie. Użyj [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md) funkcję, aby pobrać identyfikator wątku aktualnie wykonywany wątek.  
  
 `pstidThread` ,  
 [out] Adres zmiennej, która odbiera identyfikator wątku skryptu, które są skojarzone z danym wątek Win32. Interpretacja tego identyfikatora pozostało do silnika wykonywania skryptów, ale może być po prostu kopię Windows identyfikator wątku. Pamiętaj, że jeśli kończy się wątek Win32, ten identyfikator staje się nieprzypisane i mogą być później przypisane do innego wątku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_UNEXPECTED`|Nie oczekiwano wywołania (na przykład aparat skryptów jeszcze nie został załadowany lub zainicjowany) i w związku z tym nie powiodła się.|  
  
## <a name="remarks"></a>Uwagi  
 Pobrano identyfikator może służyć w kolejnych wywołaniach metod kontroli wykonania skryptu w wątku takich jak [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) metody.  
  
 Ta metoda może być wywołana z wątków-base bez skutkuje objaśnienia-base na obiektach hosta lub do [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScript](../../winscript/reference/iactivescript.md)