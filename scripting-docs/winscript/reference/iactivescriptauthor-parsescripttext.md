---
title: IActiveScriptAuthor::P arseScriptText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.ParseScriptText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::ParseScriptText
ms.assetid: ebe212e8-6789-423d-ad22-92be984dc7ad
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 90d5ab0fa700ed29b5fb37b1c48617cedec871b9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576149"
---
# <a name="iactivescriptauthorparsescripttext"></a>IActiveScriptAuthor::ParseScriptText
Analizuje tekst skryptu, dodaje tekst do aparatu tworzenia skryptów i tworzy obiekt `IScriptEntry`, który odpowiada blokowi skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT ParseScriptText(  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszCode`  
 podczas Tekst skryptu do analizy.  
  
 `pszItemName`  
 podczas Adres buforu, który zawiera nazwę elementu skojarzoną z blokiem skryptu.  
  
 `pszDelimiter`  
 podczas Adres ogranicznika bloku End-of-Script. Gdy `pszCode` jest analizowany ze strumienia tekstu, Host zwykle używa ogranicznika (takiego jak dwa znaki pojedynczego cudzysłowu) w celu wykrycia końca bloku skryptu. Ustaw ten parametr na wartość NULL, jeśli nie ma ogranicznika identyfikującego koniec bloku skryptu.  
  
 `dwCookie`  
 podczas Zdefiniowana przez aplikację wartość, która jest skojarzona z nowym obiektem `IScriptEntry`.  
  
 `dwFlags`  
 podczas Nieużywane.  
  
## <a name="return-value"></a>Wartość zwracana  
 @No__t_0. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptAuthor, interfejs](../../winscript/reference/iactivescriptauthor-interface.md)