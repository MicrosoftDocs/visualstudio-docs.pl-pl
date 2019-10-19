---
title: 'IActiveScript:: GetScriptDispatch | Microsoft Docs'
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
ms.openlocfilehash: ba53f2eccde18bd5b2d9c609ea680b50cb7261c9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575760"
---
# <a name="iactivescriptgetscriptdispatch"></a>IActiveScript::GetScriptDispatch
Pobiera interfejs `IDispatch` dla metod i właściwości skojarzonych z aktualnie uruchomionym skryptem.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrItemName`  
 podczas Adres buforu, który zawiera nazwę elementu, dla którego obiekt wywołujący wymaga skojarzonego obiektu wysyłki. Jeśli ten parametr jest `NULL`, obiekt wysyłki zawiera jako członków wszystkie globalne metody i właściwości zdefiniowane przez skrypt. Za pomocą interfejsu `IDispatch` i skojarzonego interfejsu `ITypeInfo`, host może wywoływać metody skryptów lub wyświetlać i modyfikować zmienne skryptu.  
  
 `ppdisp`  
 określoną Adres zmiennej, która otrzymuje wskaźnik do obiektu skojarzonego z globalnymi metodami i właściwościami skryptu. Jeśli aparat skryptów nie obsługuje takiego obiektu, `NULL` jest zwracana.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Prawnego.|  
|`E_INVALIDARG`|Nieprawidłowy argument.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_UNEXPECTED`|Wywołanie nie było oczekiwane (na przykład aparat skryptów nie został jeszcze załadowany lub zainicjowany).|  
|`S_FALSE`|Aparat skryptów nie obsługuje obiektu wysyłania; parametr `ppdisp` ma wartość NULL.|  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ metody i właściwości można dodać przez wywołanie interfejsu [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md) , interfejs `IDispatch` zwracany przez tę metodę może dynamicznie obsługiwać nowe metody i właściwości. Podobnie Metoda `IDispatch::GetTypeInfo` powinna zwracać nowy, unikatowy interfejs `ITypeInfo`, gdy są dodawane metody i właściwości. Należy jednak pamiętać, że aparaty języka nie mogą zmieniać interfejsu `IDispatch` w taki sposób, który jest niezgodny z żadnym z poprzednich `ITypeInfo` zwróconym interfejsem. Oznacza to, na przykład, że identyfikatory SPID nigdy nie będą ponownie używane.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScript](../../winscript/reference/iactivescript.md)