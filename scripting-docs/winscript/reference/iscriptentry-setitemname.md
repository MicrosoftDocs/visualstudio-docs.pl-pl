---
title: IScriptEntry::SetItemName | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: d25ac4977f1fca44d63767c372db169f8cb61ea6
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58160553"
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