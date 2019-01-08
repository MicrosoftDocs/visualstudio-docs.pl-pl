---
title: IActiveScriptProperty::GetProperty | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 0e68cb73b1b94b84d5133e1c7489bc8bf6309aea
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091302"
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
 Wartość właściwości, które można pobrać.  
  
 `pvarIndex`  
 Nie używany.  
  
 `pvarValue`  
 Wartość właściwości.  
  
 Dozwolone wartości dla `dwProperty` są opisane w poniższej tabeli.  
  
|Stała|Wartość|Znaczenie|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Wymusza silnik wykonywania skryptów do dzielenia w trybie całkowitą zamiast tryb punktu zmiennoprzecinkowego.|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|Umożliwia korzystanie z funkcji porównania ciągu aparatu obsługi skryptów, które ma zostać zastąpione.|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|Informuje o aparatów skryptów, który ma przyczyniają się do obiektów globalnych innych aparatów obsługi skryptów.|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|Wymusza [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] silnik wykonywania skryptów, aby wybrać zestaw funkcji języka, które są obsługiwane. Domyślny zestaw funkcji językowych obsługiwanych przez [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] silnik wykonywania skryptów jest odpowiednikiem zestawu funkcji języka, które pojawiło się w wersji 5.7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] silnik wykonywania skryptów.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_INVALIDARG`|Argument jest nieprawidłowy.|  
|`E_UNEXPECTED`|Nie oczekiwano wywołania (na przykład aparat skryptów jeszcze nie został załadowany lub zainicjowany).|  
  
## <a name="remarks"></a>Uwagi  
 Hosta można użyć właściwości SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION poinformować aparatów skryptów, który ma przyczyniają się do obiektów globalnych innych aparatów obsługi skryptów. Na przykład, program Internet Explorer mogą informować [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] renderowanej strony zawiera jedynie aparat [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] skryptów. W związku z tym tylko [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] aparatu można dodać nowe właściwości do okna obiekt globalny, a istnieje żaden aparat Visual Basic Scripting Edition (VBScript), aby zrobić to samo. Silnik może ignorują tę flagę lub można go używać do zarządzania nowych elementów członkowskich, które są dodawane do obiektów globalnych optymalizacji.  
  
 Hosta można użyć właściwości SCRIPTPROP_INVOKEVERSIONING wybrać zestaw funkcji języka, aby być obsługiwane w przypadku [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] silnik wykonywania skryptów jest uruchomiona. Jeśli ta właściwość jest ustawiona na 1 (SCRIPTLANGUAGEVERSION_5_7), funkcje językowe dostępne są takie same, jak te, które znajdowały się w wersji 5.7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] silnik wykonywania skryptów. Jeśli jest ustawiona na 2 (SCRIPTLANGUAGEVERSION_5_8), funkcje językowe dostępne są te, które znajdowały się w wersji 5.7 Oprócz funkcji, które zostały dodane w wersji 5.8. Domyślnie właściwość ta jest równa 0 (SCRIPTLANGUAGEVERSION_DEFAULT), który jest odpowiednikiem zestawu funkcji języka, które pojawiło się w wersji 5.7, chyba że host obsługuje różne domyślne zachowanie. Na przykład programu Internet Explorer 8 zdecyduje się na [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] funkcji językowych obsługiwanych przez wersję 5.8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] silnik wykonywania skryptów domyślnie, gdy tryb dokumentu dla programu Internet Explorer 8 jest tryb "Standardów programu Internet Explorer 8".  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie zgodności dokumentów](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Informacje o wersji](../../javascript/reference/javascript-version-information.md)