---
title: 'IScriptEntry:: GetBody | Microsoft Docs'
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
ms.openlocfilehash: aba6019f4729f1b4a31933a4ca93c0eddf6159a2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575486"
---
# <a name="iscriptentrygetbody"></a>IScriptEntry::GetBody
Zwraca tekst, który odpowiada treści bloku skryptu `IScriptEntry`, bloku funkcji lub Scriptlet.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetBody(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstr`  
 określoną Tekst, który znajduje się w treści jednego z następujących elementów:  
  
- Blok skryptu `IScriptEntry`  
  
- Funkcja `IScriptEntry` w bloku funkcji  
  
- Procedura obsługi zdarzeń `IScriptEntry` Scriptlet  
  
## <a name="return-value"></a>Wartość zwracana  
 @No__t_0. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz także  
 [IScriptEntry, interfejs](../../winscript/reference/iscriptentry-interface.md)