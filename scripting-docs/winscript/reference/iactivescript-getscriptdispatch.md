---
title: IActiveScript::GetScriptDispatch | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 2a18d6781ca2b7820686b317ad0be5da425ade1f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097685"
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