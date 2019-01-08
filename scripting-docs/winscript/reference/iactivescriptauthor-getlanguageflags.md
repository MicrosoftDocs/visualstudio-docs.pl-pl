---
title: IActiveScriptAuthor::GetLanguageFlags | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetLanguageFlags
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetLanguageFlags
ms.assetid: eb244452-62f7-4a73-b48f-1aa05cbcc32d
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dca878d6d4fd15db4b516e37932fbfebd30607a2
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093200"
---
# <a name="iactivescriptauthorgetlanguageflags"></a>IActiveScriptAuthor::GetLanguageFlags
Zwraca informacje o języku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pgrfasa`  
 [out] Flagi, które zawierają informacje o języku. Może być kombinacją następujących wartości:  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|fasaPreferInternalHandler|0x0001|Język preferowany Tworzenie procedury obsługi zdarzeń skryptu za pomocą skryptu tworzenia aparatu zamiast aplikacji.|  
|fasaSupportInternalHandler|0x0002|Język obsługuje programy obsługi zdarzeń skryptu utworzone przez skrypt tworzenia aparatu.|  
|fasaCaseSensitive|0x0004|Język skryptu jest uwzględniana wielkość liter.|  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli skrypt tworzenia aparatu zarządza procedury obsługi zdarzeń, Twoja aplikacja powinna wywołać `CreateChildHandler` z `IScriptEntry` obiektu. Spowoduje to utworzenie `IScriptScriptlet` obiekt, który odnosi się do programu obsługi zdarzeń. Aparat dodaje także procedury obsługi zdarzeń do wejścia skryptu. Procedura obsługi zdarzeń jest pusta funkcja, który zawiera informacje o określonej sygnaturze.  
  
 Jeśli aplikacja zarządza procedury obsługi zdarzeń, powinny wywoływać `CreateChildHandler` z `IScriptNode` obiekt, który reprezentuje scriptlet procedury obsługi zdarzeń. Spowoduje to utworzenie `IScriptScriptlet` obiekt, który jest skojarzony z scriptlet procedury obsługi zdarzeń. Aplikacja ma również dodać pusty funkcji jako zdarzenie obsługi na nową lub istniejącą `IScriptEntry` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptAuthor, interfejs](../../winscript/reference/iactivescriptauthor-interface.md)