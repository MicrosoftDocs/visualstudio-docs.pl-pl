---
title: IScriptEntry::GetBody | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetBody
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetBody
ms.assetid: 419c8c11-a1f8-4b97-ab00-e8af2b2f9bfc
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7f8f1ad24660401d575af2724b788387fd546af8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60064921"
---
# <a name="iscriptentrygetbody"></a>IScriptEntry::GetBody
Zwraca tekst, który odnosi się do treści `IScriptEntry` blok skryptu, bloku funkcji lub scriptlet.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetBody(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstr`  
 [out] Tekst, który znajduje się w treści w jednej z następujących czynności:  
  
- `IScriptEntry` Blok skryptu  
  
- `IScriptEntry` Funkcji w bloku funkcji  
  
- `IScriptEntry` Scriptlet obsługi zdarzeń  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [IScriptEntry, interfejs](../../winscript/reference/iscriptentry-interface.md)