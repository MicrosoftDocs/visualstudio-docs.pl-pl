---
title: 'IActiveScriptAuthor:: GetEventHandler | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetEventHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetEventHandler
ms.assetid: 87c7a71d-46b9-448c-b34d-394105e20982
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c69b32f0040ea6d52e0712b8e1813cc5a0b40c58
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576229"
---
# <a name="iactivescriptauthorgeteventhandler"></a>IActiveScriptAuthor::GetEventHandler
Zwraca Scriptlet, który ma określone atrybuty.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetEventHandler(  
   IDispatch          *pdisp,  
   LPCOLESTR          pszItem,  
   LPCOLESTR          pszSubItem,  
   LPCOLESTR          pszEvent,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdisp`  
 podczas Obiekt `IDispatch`, który odnosi się do `NamedItem`, do którego jest dołączona Scriptlet.  
  
 `pszItem`  
 podczas Adres buforu identyfikatora najwyższego poziomu w pełni kwalifikowanej nazwy Scriptlet na hoście.  
  
 `pszSubItem`  
 podczas Adres buforu identyfikatora drugiego poziomu w pełni kwalifikowanej nazwy Scriptlet na hoście. Ustaw wartość NULL, jeśli nazwa ma tylko jeden poziom.  
  
 `pszEvent`  
 podczas Adres buforu, który zawiera nazwę zdarzenia. Scriptlet jest obsługą zdarzeń dla tego zdarzenia.  
  
 `ppse`  
 określoną Adres zmiennej, która otrzymuje wskaźnik do interfejsu `IScriptEntry` Scriptlet, który ma określone atrybuty.  
  
## <a name="return-value"></a>Wartość zwracana  
 @No__t_0. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptAuthor   interfejsu](../../winscript/reference/iactivescriptauthor-interface.md)  
 [IScriptEntry, interfejs](../../winscript/reference/iscriptentry-interface.md)