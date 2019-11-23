---
title: 'IActiveScriptAuthor:: RemoveNamedItem | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.RemoveNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::RemoveNamedItem
ms.assetid: 1173ef46-39a5-4bc1-8e0c-89259a16be16
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cade532d2ca276237981855cafe12804307d0bb6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572841"
---
# <a name="iactivescriptauthorremovenameditem"></a>IActiveScriptAuthor::RemoveNamedItem
Usuwa obiekt `NamedItem` z przestrzeni nazw aparatu tworzenia skryptów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT RemoveNamedItem(  
   LPCOLESTR          pszName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszName`  
 podczas Adres buforu identyfikujący obiekt `NamedItem`, który ma zostać usunięty.  
  
## <a name="return-value"></a>Wartość zwrócona  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`S_FALSE`|Obiekt `NamedItem` nie występuje w przestrzeni nazw aparatu tworzenia skryptów.|  
  
## <a name="remarks"></a>Uwagi  
 [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) służy do iniekcji obiektu `NamedItem` do przestrzeni nazw aparatu tworzenia skryptów.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptAuthor  interfejsu](../../winscript/reference/iactivescriptauthor-interface.md)  
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)