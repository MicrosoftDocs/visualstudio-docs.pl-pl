---
title: IActiveScriptAuthor::AddScriptlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 62499afe87a3d7dae31e609c9ce88f41e9d993a9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089215"
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
Dodaje skryptletu kodu jako element podrzędny elementu poziomu głównego `IScriptNode` obiektu. Na hoście w pełni kwalifikowana nazwa scriptlet może mieć tylko dwa poziomy.  
  
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
 [in] Adres nazwy domyślnej, aby skojarzyć ze scriptlet.  
  
 `pszCode`  
 [in] Adres tekstu scriptlet.  
  
 `pszItemName`  
 [in] Adres buforu identyfikator najwyższego poziomu o nazwie FQDN scriptlet na hoście.  
  
 `pszSubItemName`  
 [in] Adres buforu identyfikator drugiego poziomu, nazwy FQDN scriptlet na hoście. Ustaw na wartość NULL, jeśli nazwa zawiera tylko jeden poziom.  
  
 `pszEventName`  
 [in] Adres buforu, który zawiera nazwę zdarzenia, dla którego scriptlet ma program obsługi zdarzeń.  
  
 `pszDelimiter`  
 [in] Adres ogranicznika końcowego elementu skrypt bloku. Gdy `pszCode` jest analizowany ze strumienia tekstu, host zazwyczaj używa rozdzielnika (takie jak dwa pojedyncze cudzysłowy), na końcu bloku skryptu do wykrywania. Ustaw ten parametr na wartość NULL, jeśli ogranicznika nie są oznaczane koniec bloku skryptu.  
  
 `dwCookie`  
 [in] Wartość zdefiniowanych przez aplikację, która jest używana do kojarzenia scriptlet z obiektu hosta.  
  
 `dwFlags`  
 [in] Nie jest używany.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptAuthor, interfejs](../../winscript/reference/iactivescriptauthor-interface.md)