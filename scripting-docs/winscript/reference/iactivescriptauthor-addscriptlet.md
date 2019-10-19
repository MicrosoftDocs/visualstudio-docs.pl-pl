---
title: 'IActiveScriptAuthor:: AddScriptlet | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddScriptlet
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddScriptlet
ms.assetid: 879a6651-f187-4934-b130-c1247549900b
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a349a848f282e6b3a228c7b17009e0261801be5
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577984"
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
Dodaje kod Scriptlet jako element podrzędny obiektu głównego poziomu `IScriptNode`. W pełni kwalifikowana nazwa Scriptlet może mieć tylko dwa poziomy na hoście.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT AddScriptlet(  
   LPCOLESTR pszDefaultName,  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszSubItemName,  
   LPCOLESTR pszEventName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszDefaultName`  
 podczas Adres nazwy domyślnej, która ma zostać skojarzona z Scriptlet.  
  
 `pszCode`  
 podczas Adres tekstu Scriptlet.  
  
 `pszItemName`  
 podczas Adres buforu identyfikatora najwyższego poziomu w pełni kwalifikowanej nazwy Scriptlet na hoście.  
  
 `pszSubItemName`  
 podczas Adres buforu identyfikatora drugiego poziomu w pełni kwalifikowanej nazwy Scriptlet na hoście. Ustaw wartość NULL, jeśli nazwa ma tylko jeden poziom.  
  
 `pszEventName`  
 podczas Adres buforu, który zawiera nazwę zdarzenia, dla którego Scriptlet jest procedura obsługi zdarzeń.  
  
 `pszDelimiter`  
 podczas Adres ogranicznika bloku End-of-Script. Gdy `pszCode` jest analizowany ze strumienia tekstu, Host zwykle używa ogranicznika (takiego jak dwa znaki pojedynczego cudzysłowu) w celu wykrycia końca bloku skryptu. Ustaw ten parametr na wartość NULL, jeśli ogranicznik nie oznacza końca bloku skryptu.  
  
 `dwCookie`  
 podczas Zdefiniowana przez aplikację wartość, która jest używana do kojarzenia Scriptlet z obiektem hosta.  
  
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