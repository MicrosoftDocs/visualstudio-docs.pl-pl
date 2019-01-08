---
title: IScriptEntry::SetItemName | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetItemName
ms.assetid: 9551a7ec-38f8-466a-9722-09367763f380
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20af0975a4175d10b110ac5e3cef9e0055f4ce1b
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097763"
---
# <a name="iscriptentrysetitemname"></a>IScriptEntry::SetItemName
Ustawia nazwę elementu, który identyfikuje `IScriptEntry` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT SetItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `psz`  
 [in] Adres buforu, który zawiera nazwę elementu. Nazwa elementu jest używany przez hosta do zidentyfikowania wpisu.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_FAIL`|Metoda nie powiodła się.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać `IScriptEntry` obiektów, Metoda ta zwraca `S_OK`.  
  
 Aby uzyskać `IScriptScriptlet` obiektów (wynikającymi z `IScriptEntry`), ta metoda zwraca `E_FAIL`. Aby uzyskać `IScriptScriptlet` obiektów, nazwa elementu jest ustawiony [IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md) i nie można zmienić.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IScriptEntry](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)