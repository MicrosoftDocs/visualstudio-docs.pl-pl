---
title: 'IScriptEntry:: SetName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetName
ms.assetid: dfa33450-87d7-4c8e-bfd8-0cc2d6542a0e
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9dfa27c6c8c58c0ee1599e17e1da5b5f424e416
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575351"
---
# <a name="iscriptentrysetname"></a>IScriptEntry::SetName
Dla wpisów reprezentujących pojedynczy obiekt (na przykład funkcja) ustawia nazwę obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT SetName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `psz`  
 podczas Nowa nazwa obiektu `IScriptEntry`.  
  
## <a name="return-value"></a>Wartość zwrócona  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz także  
 [IScriptEntry  interfejsu](../../winscript/reference/iscriptentry-interface.md)  
 [IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)