---
title: IActiveScriptStats::GetStatEx | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.GetStatEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStatEx
ms.assetid: f526f51d-8ab5-49ef-a8f7-ae0ac1cb46e4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f1585e335fac0072eba48494bf8c27736a47f41
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58149172"
---
# <a name="iactivescriptstatsgetstatex"></a>IActiveScriptStats::GetStatEx
Zwraca statystyki skryptu niestandardowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetStatEx(  
   REFGUID  guid,  
   ULONG*   pluHi,  
   ULONG*   pluLo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `guid`  
 [in] Określa statystykę do zwrócenia. Semantyka statystykę odnosi się do określonego identyfikatora GUID jest całkowicie zdefiniowane aparatu.  
  
 `pluHi`  
 [out] Wysoka 32 bity 64-bitowa liczba całkowita bez znaku reprezentujący dane statystyczne.  
  
 `pluLo`  
 [out] Niski 32 bity 64-bitowa liczba całkowita bez znaku reprezentujący dane statystyczne.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_NOTIMPL`|Metoda nie jest zaimplementowana.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia aparatu niestandardowego skryptu przywrócić statystyki istotnych niestandardowego hosta.  
  
> [!NOTE]
>  Ta metoda nie jest obecnie zaimplementowana.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)   
 [IActiveScriptStats, interfejs](../../winscript/reference/iactivescriptstats-interface.md)