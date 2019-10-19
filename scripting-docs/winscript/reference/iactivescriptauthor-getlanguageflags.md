---
title: 'IActiveScriptAuthor:: GetLanguageFlags | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetLanguageFlags
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetLanguageFlags
ms.assetid: eb244452-62f7-4a73-b48f-1aa05cbcc32d
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68da16513050bd87642be2c96212a330a0916608
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576204"
---
# <a name="iactivescriptauthorgetlanguageflags"></a>IActiveScriptAuthor::GetLanguageFlags
Zwraca informacje o języku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pgrfasa`  
 określoną Flagi zawierające informacje o języku. Może być kombinacją następujących wartości:  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|fasaPreferInternalHandler|0x0001|Język preferuje Tworzenie obsługi zdarzeń skryptów przez aparat tworzenia skryptów zamiast aplikacji.|  
|fasaSupportInternalHandler|0x0002|Język obsługuje procedury obsługi zdarzeń skryptów utworzone przez aparat tworzenia skryptów.|  
|fasaCaseSensitive|0x0004|W języku skryptu jest rozróżniana wielkość liter.|  
  
## <a name="return-value"></a>Wartość zwracana  
 @No__t_0. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli aparat tworzenia skryptów zarządza obsługą zdarzeń, aplikacja powinna wywołać `CreateChildHandler` z `IScriptEntry` obiektu. Spowoduje to utworzenie obiektu `IScriptScriptlet`, który odnosi się do programu obsługi zdarzeń. Aparat dodaje również procedurę obsługi zdarzeń do wpisu skryptu. Program obsługi zdarzeń jest pustą funkcją, która zawiera określone informacje o podpisie.  
  
 Jeśli aplikacja zarządza procedurami obsługi zdarzeń, powinna wywołać `CreateChildHandler` z `IScriptNode` obiektu, który reprezentuje procedurę obsługi zdarzeń Scriptlet. Spowoduje to utworzenie obiektu `IScriptScriptlet` skojarzonego z programem obsługi zdarzeń Scriptlet. Aplikacja musi również dodać pustą funkcję jako procedurę obsługi zdarzeń do nowego lub istniejącego obiektu `IScriptEntry`.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptAuthor, interfejs](../../winscript/reference/iactivescriptauthor-interface.md)