---
title: 'IActiveScriptProperty:: SetProperty | Microsoft Docs'
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
ms.openlocfilehash: 0f8307a82f181be20205c7bfcc47e881b0fa1e90
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571307"
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
 Nie jest używany.  
  
 `pvarValue`  
 Wartość właściwości.  
  
 Wartości dozwolone dla `dwProperty` są opisane w poniższej tabeli.  
  
|Stała|Value|Znaczenie|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Wymusza podział aparatu skryptów w tryb liczby całkowitej zamiast trybu zmiennoprzecinkowego. Wartość domyślna to `False`.|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|Umożliwia zamianę funkcji porównywania ciągów aparatu skryptów.|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|Informuje aparat skryptów, że nie istnieją żadne inne aparaty skryptów do współtworzenia obiektu globalnego.|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|Wymusza, aby aparat skryptów [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] mógł wybrać zestaw funkcji języka, które mają być obsługiwane. Domyślny zestaw funkcji językowych obsługiwanych przez aparat skryptów [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] jest odpowiednikiem zestawu funkcji języka, który pojawił się w wersji 5,7 aparatu obsługi skryptów [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].|  
  
## <a name="return-value"></a>Wartość zwrócona  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwrócona|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Prawnego.|  
|`E_INVALIDARG`|Argument jest nieprawidłowy.|  
|`E_UNEXPECTED`|Wywołanie nie było oczekiwane (na przykład aparat skryptów nie został jeszcze załadowany lub zainicjowany).|  
  
## <a name="remarks"></a>Uwagi  
 Aby włączyć lub wyłączyć dzielenie liczby całkowitej, wywołaj `SetProperty` i Przekształć `Boolean` na `Object`. Domyślnie wartość właściwości jest `False`. Jeśli ustawisz ją na `True`, operacje dzielenia będą zwracać tylko liczby całkowite.  
  
 Aby włączyć lub wyłączyć Porównywanie ciągów niestandardowych, wywołaj `SetProperty` i przekaż wartość `Object`. Obiekt, który przekazujesz, musi implementować interfejs [IActiveScriptStringCompare](../../winscript/reference/iactivescriptstringcompare-interface.md)interfejsu. Metoda [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md) interfejsu [interfejsu IActiveScriptStringCompare](../../winscript/reference/iactivescriptstringcompare-interface.md) jest wywoływana za każdym razem, gdy jest wykonywana funkcja porównywania ciągów.  
  
 Aby wybrać zestaw funkcji języka, które mają być obsługiwane po zainicjowaniu aparatu skryptów [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], wywołaj `SetProperty` i przekaż wartość odpowiadającą zestawowi funkcji języka, który ma być włączony dla SCRIPTPROP_INVOKEVERSIONING. Jeśli ta właściwość ma wartość 1 (SCRIPTLANGUAGEVERSION_5_7), dostępne funkcje języka są takie same jak te, które pojawiły się w wersji 5,7 aparatu skryptów [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Jeśli jest ustawiona na 2 (SCRIPTLANGUAGEVERSION_5_8), dostępne funkcje języka to te, które pojawiły się w wersji 5,7, a także nowe funkcje, które zostały dodane w wersji 5,8. Domyślnie właściwość ta ma wartość 0 (SCRIPTLANGUAGEVERSION_DEFAULT), która jest równoważna z zestawem funkcji języka, który pojawił się w wersji 5,7, chyba że host obsługuje inne zachowanie domyślne. Na przykład program Internet Explorer 8 zażąda funkcji języka [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], które są obsługiwane przez aparat obsługi skryptów w wersji 5,8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] domyślnie, gdy domyślny tryb dokumentu programu Internet Explorer 8 jest trybem "Standardy programu Internet Explorer 8". Przełączenie trybu dokumentu programu Internet Explorer 8 do standardów programu Internet Explorer 7 lub tryb osobliwości resetuje aparat skryptów [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], aby obsługiwał tylko zestaw funkcji języka, który istniał w wersji 5,7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] aparatu obsługi skryptów.  
  
> [!NOTE]
> SCRIPTPROP_INVOKEVERSIONING powinna być ustawiona tylko wtedy, gdy jest inicjowany aparat skryptów [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wymusić użycie przez aparat skryptów dzielenia liczb całkowitych i sposobu zezwalania na Przeciążenie funkcji porównywania.  
  
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
  
## <a name="see-also"></a>Zobacz także  
 [Definiowanie  zgodności dokumentów](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))  
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Informacje o wersji](../../javascript/reference/javascript-version-information.md)