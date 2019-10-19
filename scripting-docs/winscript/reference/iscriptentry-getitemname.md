---
title: 'IScriptEntry:: getitemname | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetItemName
ms.assetid: 8f2562f1-8231-4a39-ad79-074f9ec3d403
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dcd1b83fa6d22fafc2123645f1f252fa1325f7f1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575461"
---
# <a name="iscriptentrygetitemname"></a>IScriptEntry::GetItemName
Zwraca nazwę elementu, który identyfikuje obiekt `IScriptEntry`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetItemName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstr`  
 określoną Adres buforu, który zawiera nazwę elementu. Nazwa elementu jest używana przez hosta do identyfikowania wpisu.  
  
## <a name="return-value"></a>Wartość zwracana  
 @No__t_0. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Dla `IScriptScriptlet` obiektów należy ustawić nazwę elementu przy użyciu [IActiveScriptAuthor:: AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md). W przypadku innych interfejsów należy ustawić nazwę elementu przy użyciu [IScriptEntry:: Setitemname](../../winscript/reference/iscriptentry-setitemname.md).  
  
## <a name="see-also"></a>Zobacz także  
 [IScriptEntry, interfejs](../../winscript/reference/iscriptentry-interface.md)