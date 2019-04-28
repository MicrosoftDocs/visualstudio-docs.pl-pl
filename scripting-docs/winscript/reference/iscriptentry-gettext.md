---
title: IScriptEntry::GetText | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetText
ms.assetid: 105b8244-1972-4b39-ac18-965f1f345ef2
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 24b314443644558b9900fc7d702dcd1b96a7cea4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787714"
---
# <a name="iscriptentrygettext"></a>IScriptEntry::GetText
Zwraca tekst, który odpowiada `IScriptEntry` blok skryptu lub kodu źródłowego, który jest zawarty w `IScriptScriptlet` programu obsługi zdarzeń.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetText(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstr`  
 [out] Tekst w `IScriptEntry` blok skryptu lub kodu źródłowego, który jest zawarty w `IScriptScriptlet` programu obsługi zdarzeń.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [IScriptEntry, interfejs](../../winscript/reference/iscriptentry-interface.md)