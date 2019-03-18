---
title: IActiveScript::GetScriptDispatch | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptDispatch
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptDispatch
ms.assetid: 2092ccd4-1f4c-493a-b5b7-077a70ce95ca
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c329a4dbf42461369441b86f6d9ba18992916366
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58144748"
---
# <a name="iactivescriptgetscriptdispatch"></a>IActiveScript::GetScriptDispatch
Pobiera `IDispatch` interfejs służący do metod i właściwości skojarzone z aktualnie działającego skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrItemName`  
 [in] Adres buforu, który zawiera nazwę elementu, dla którego wywołujący musi mieć obiekt wysyłki skojarzone. Jeśli ten parametr jest `NULL`, obiekt wysyłania zawiera jako członków globalnych metod i właściwości definiowane przez skrypt. Za pomocą `IDispatch` interfejs oraz skojarzonych z nimi `ITypeInfo` interfejsu hosta można wywołać metody skryptów lub w widoku i modyfikować zmiennych skryptu.  
  
 `ppdisp`  
 [out] Adres zmiennej, która otrzymuje wskaźnik do obiektu skojarzone z właściwości i metody globalne skryptu. Jeśli silnik wykonywania skryptów nie obsługuje taki obiekt `NULL` jest zwracana.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_INVALIDARG`|Argument ten był nieprawidłowy.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_UNEXPECTED`|Nie oczekiwano wywołania (na przykład aparat skryptów jeszcze nie został załadowany lub zainicjowany).|  
|`S_FALSE`|Aparat skryptów nie obsługuje obiektu dispatch; `ppdisp` parametr ma wartość NULL.|  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ metody i właściwości mogą być dodawany przez wywołanie [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md) interfejsu `IDispatch` zwracanego przez tę metodę interfejsu dynamicznie może obsługiwać nowe metody i właściwości. Podobnie `IDispatch::GetTypeInfo` metoda powinna zwrócić nowych, unikatowych `ITypeInfo` interfejsu dodanie metody i właściwości. Należy jednak pamiętać, nie może zmienić język aparatów `IDispatch` interfejsu w sposób niezgodny z dowolnego poprzedniego `ITypeInfo` zawracany interfejs. Oznacza to, na przykład, że DISPID nigdy nie zostanie ponownie.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScript](../../winscript/reference/iactivescript.md)