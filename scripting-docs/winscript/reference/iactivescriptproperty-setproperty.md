---
title: IActiveScriptProperty::SetProperty | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProperty.SetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- SetProperty method, IActiveScriptProperty interface
ms.assetid: 0ba429c5-04a3-4505-bc5f-69c505dfca91
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f24f63612b5d4dcb1c6a5a65e0ad38f8056cf842
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58159390"
---
# <a name="iactivescriptpropertysetproperty"></a>IActiveScriptProperty::SetProperty
Ustawia właściwość, która jest określona przez parametr.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT SetProperty(  
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
 Wartość właściwości do ustawienia.  
  
 `pvarIndex`  
 Nie używany.  
  
 `pvarValue`  
 Wartość właściwości.  
  
 Dozwolone wartości dla `dwProperty` są opisane w poniższej tabeli.  
  
|Stała|Wartość|Znaczenie|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Wymusza silnik wykonywania skryptów do dzielenia w trybie całkowitą zamiast tryb punktu zmiennoprzecinkowego. Wartość domyślna to `False`.|  
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
 Aby włączyć lub wyłączyć dzielenie liczby całkowitej, wywołaj `SetProperty` i przekonwertować `Boolean` do `Object`. Domyślnie wartość właściwości jest `False`. Jeśli ustawisz na `True`, operacji dzielenia zwróci tylko liczby całkowite.  
  
 Aby włączyć lub wyłączyć niestandardowy ciąg porównania, wywołaj `SetProperty` i przekazać `Object` wartość. Obiekt, który można przekazać musi implementować interfejs [interfejs IActiveScriptStringCompare](../../winscript/reference/iactivescriptstringcompare-interface.md). [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md) metody [interfejs IActiveScriptStringCompare](../../winscript/reference/iactivescriptstringcompare-interface.md) interfejsu nosi nazwę każdym wykonaniu funkcji porównania ciągu.  
  
 Aby wybrać zestaw funkcji języka, które są obsługiwane podczas [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] silnik wykonywania skryptów jest inicjowany, wywołaj `SetProperty` i przekaż wartość, która odnosi się do języka zestaw funkcji, który można włączyć dla SCRIPTPROP_INVOKEVERSIONING. Jeśli ta właściwość jest ustawiona na 1 (SCRIPTLANGUAGEVERSION_5_7), funkcje językowe dostępne są takie same, jak te, które znajdowały się w wersji 5.7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] silnik wykonywania skryptów. Jeśli jest ustawiona na 2 (SCRIPTLANGUAGEVERSION_5_8), funkcje językowe dostępne są te, które znajdowały się w wersji 5.7 Oprócz nowych funkcji, które zostały dodane w wersji 5.8. Domyślnie właściwość ta jest równa 0 (SCRIPTLANGUAGEVERSION_DEFAULT), który jest odpowiednikiem zestawu funkcji języka, które pojawiło się w wersji 5.7, chyba że host obsługuje różne domyślne zachowanie. Na przykład programu Internet Explorer 8 zdecyduje się na [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] funkcje językowe, które są obsługiwane przez wersję 5.8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] silnik wykonywania skryptów domyślnie, gdy domyślny tryb dokumentu dla programu Internet Explorer 8 to tryb "Standardów programu Internet Explorer 8". Przełączanie trybu dokumentu programu Internet Explorer 8, aby standardów programu Internet Explorer 7 lub tryb Osobliwości resetuje [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] silnik wykonywania skryptów do obsługi tylko zestaw funkcji języka autonomiczności występujące w wersji 5.7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] silnik wykonywania skryptów.  
  
> [!NOTE]
>  SCRIPTPROP_INVOKEVERSIONING powinna być ustawiona tylko wtedy, gdy [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] silnik wykonywania skryptów jest inicjowany.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje sposób wymusić silnik wykonywania skryptów, aby użyć dzielenie liczby całkowitej i umożliwić przeciążanie funkcji porównania.  
  
```c#  
BMLScriptEngine bmlScriptEngine = new BMLScriptEngine();  
IActiveScriptProperty scriptProperties = bmlScriptEngine as   
    IActiveScriptProperty;  
  
// Force the scripting engine to use integer division.  
Boolean enableIntegerDivision = true;  
Object vtIntegerDivInstance = (Object)enableIntegerDivision;  
                scriptProperties.SetProperty(SCRIPTPROP_INTEGERDIVISION,   
    System.IntPtr.Zero, ref vtIntegerDivInstance);  
  
// Allow overloading of the compare function.  
BMLScriptStringCompare bmlScriptStringCompareInstance = new   
    BMLScriptStringCompare();  
Object vtStrCmpInstance = (Object)bmlScriptStringCompareInstance;  
scriptProperties.SetProperty(SCRIPTPROP_STRCOMPINST,   
    System.IntPtr.Zero, ref vtStrCmpInstance);  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie zgodności dokumentów](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Informacje o wersji](../../javascript/reference/javascript-version-information.md)