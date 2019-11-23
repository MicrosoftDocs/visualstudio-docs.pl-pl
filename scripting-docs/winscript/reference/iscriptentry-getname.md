---
title: 'IScriptEntry:: GetName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetName
ms.assetid: 56daa288-618f-497c-a360-7d443afd478b
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c99cda48a20efb41b2535645ccdb50be8bb6d6bc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575449"
---
# <a name="iscriptentrygetname"></a>IScriptEntry::GetName
W przypadku wpisów reprezentujących pojedynczy obiekt (na przykład funkcja) zwraca nazwę obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstr`  
 określoną Nazwa obiektu reprezentowanego przez blok skryptu `IScriptEntry`. Jeśli wpis nie reprezentuje pojedynczego obiektu, zwracana jest wartość NULL.  
  
 Wpisy podrzędne reprezentują pojedynczy obiekt funkcji.  
  
## <a name="return-value"></a>Wartość zwrócona  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz także  
 [IScriptEntry  interfejsu](../../winscript/reference/iscriptentry-interface.md)  
 [IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)