---
title: 'IActiveScriptProperty:: GetProperty | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProperty.GetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetProperty method, IActiveScriptProperty interface
ms.assetid: a43383db-b148-4d76-83bd-4f0e899b7cb1
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1eeec6472a067d18a8b8962cfac70c25c0ff971
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571417"
---
# <a name="iactivescriptpropertygetproperty"></a>IActiveScriptProperty::GetProperty
Pobiera właściwość, która jest określona przez parametr.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetProperty(  
// The property value:  
    uint dwProperty,    
// Not used:  
    IntPtr pvarIndex,    
// The value of the property:   
    out object pvarValue,    
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwProperty`  
 Wartość właściwości do pobrania.  
  
 `pvarIndex`  
 Nie używany.  
  
 `pvarValue`  
 Wartość właściwości.  
  
 Wartości dozwolone dla `dwProperty` są opisane w poniższej tabeli.  
  
|Stała|Wartość|Znaczenie|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Wymusza podział aparatu skryptów w tryb liczby całkowitej zamiast trybu zmiennoprzecinkowego.|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|Umożliwia zamianę funkcji porównywania ciągów aparatu skryptów.|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|Informuje aparat skryptów, że nie istnieją żadne inne aparaty skryptów do współtworzenia obiektu globalnego.|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|Wymusza, aby aparat skryptów [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] mógł wybrać zestaw funkcji języka, które mają być obsługiwane. Domyślny zestaw funkcji językowych obsługiwanych przez aparat skryptów [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] jest odpowiednikiem zestawu funkcji języka, który pojawił się w wersji 5,7 aparatu obsługi skryptów [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].|  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Prawnego.|  
|`E_INVALIDARG`|Argument jest nieprawidłowy.|  
|`E_UNEXPECTED`|Wywołanie nie było oczekiwane (na przykład aparat skryptów nie został jeszcze załadowany lub zainicjowany).|  
  
## <a name="remarks"></a>Uwagi  
 Host może użyć właściwości SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION, aby poinformować aparat skryptów, że nie istnieją żadne inne aparaty skryptów do współtworzenia obiektu globalnego. Na przykład program Internet Explorer może poinformować aparat [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], że renderowana Strona zawiera tylko skrypty [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. W ten sposób tylko aparat [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] może dodawać nowe właściwości do okna obiektu globalnego i nie ma żadnego aparatu Visual Basic Scripting Edition (VBScript) w taki sam sposób. Aparat może zignorować tę flagę lub użyć jej do optymalizacji zarządzania nowymi elementami członkowskimi, które są dodawane do obiektu globalnego.  
  
 Na hoście można użyć właściwości SCRIPTPROP_INVOKEVERSIONING, aby wybrać zestaw funkcji języka, które mają być obsługiwane po uruchomieniu aparatu skryptów [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Jeśli ta właściwość ma wartość 1 (SCRIPTLANGUAGEVERSION_5_7), dostępne funkcje języka są takie same jak te, które pojawiły się w wersji 5,7 aparatu skryptów [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Jeśli jest ustawiona na 2 (SCRIPTLANGUAGEVERSION_5_8), dostępne funkcje języka są te, które pojawiły się w wersji 5,7, oprócz funkcji, które zostały dodane w wersji 5,8. Domyślnie właściwość ta ma wartość 0 (SCRIPTLANGUAGEVERSION_DEFAULT), która jest równoważna z zestawem funkcji języka, który pojawił się w wersji 5,7, chyba że host obsługuje inne zachowanie domyślne. Na przykład program Internet Explorer 8 zażąda funkcji języka [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] obsługiwanych przez aparat obsługi skryptów w wersji 5,8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] domyślnie, gdy tryb dokumentu dla programu Internet Explorer 8 to tryb "Standardy programu Internet Explorer 8".  
  
## <a name="see-also"></a>Zobacz także  
 [Definiowanie   zgodności dokumentów](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))  
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)    
 [Informacje o wersji](../../javascript/reference/javascript-version-information.md)