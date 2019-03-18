---
title: IDispatchEx::InvokeEx | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.InvokeEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- InvokeEx method
ms.assetid: d90783e6-4b89-4423-8a56-a9c8b4b2c813
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33494836e463c9c2fd74acf7835d7e4630747b0e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58157350"
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
Zapewnia dostęp do właściwości i metod udostępnianych przez `IDispatchEx` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT InvokeEx(  
   DISPID id,  
   LCID lcid,  
   WORD wFlags,  
   DISPARAMS *pdp,  
   VARIANT *pVarRes,   
   EXCEPINFO *pei,   
   IServiceProvider *pspCaller   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 Określa element członkowski. Używa `GetDispID` lub `GetNextDispID` można uzyskać identyfikatora wysyłania.  
  
 `lcid`  
 Ustawienia regionalne kontekstu, w którym można interpretować argumenty. `lcid` Jest przekazywany do `InvokeEx` umożliwiające obiektu do interpretacji jej argumenty, które są specyficzne dla ustawień regionalnych.  
  
 `wFlags`  
 Wartości prawne `wFlags` są:  
  
 DISPATCH_PROPERTYGET &AMP;#124; DISPATCH_METHOD &AMP;#124; DISPATCH_PROPERTYPUT &AMP;#124; DISPATCH_PROPERTYPUTREF &AMP;#124; DISPATCH_CONSTRUCT  
  
 Flagi opisujące kontekst `InvokeEx` wywołania:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|DISPATCH_METHOD|Element członkowski jest wywoływana jako metoda. Jeśli właściwość ma taką samą nazwę, to i Flaga DISPATCH_PROPERTYGET może być ustawiona (zdefiniowany przez `IDispatch`).|  
|DISPATCH_PROPERTYGET|Element członkowski jest pobierana jako element członkowski danych lub właściwości (zdefiniowany przez `IDispatch`).|  
|DISPATCH_PROPERTYPUT|Element członkowski zostanie zmieniony jako element członkowski danych lub właściwości (zdefiniowany przez `IDispatch`).|  
|DISPATCH_PROPERTYPUTREF|Element członkowski zostanie zmieniony przez przypisywanie odwołania, a nie przypisanie wartości. Ta flaga jest prawidłowy tylko wtedy, gdy właściwość akceptuje odwołanie do obiektu (zdefiniowany przez `IDispatch`).|  
|DISPATCH_CONSTRUCT|Element członkowski jest używana jako Konstruktor. (Jest to nowa wartość zdefiniowana przez `IDispatchEx`). Wartości prawne `wFlags` są:<br /><br /> DISPATCH_PROPERTYGET DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 Wskaźnik do struktury zawiera tablicę argumentów, tablicę identyfikatorów DISPID argumentu dla nazwanych argumentów i zlicza liczbę elementów w tablicach. Zobacz `IDispatch` dokumentację dotyczącą pełen opis struktury DISPPARAMS.  
  
 `pVarRes`  
 Wskaźnik do lokalizacji, gdzie wynik jest przechowywanych lub wartość Null, jeśli obiekt wywołujący nie oczekuje żadnego wyniku. Ten argument jest ignorowana, jeśli określono DISPATCH_PROPERTYPUT lub DISPATCH_PROPERTYPUTREF.  
  
 `pei`  
 Wskaźnik do struktury, która zawiera informacje o wyjątku. Ta struktura powinno być wypełnione if `DISP_E_EXCEPTION` jest zwracana. Może mieć wartości Null. Zobacz `IDispatch` dokumentację dotyczącą pełen opis `EXCEPINFO` struktury.  
  
 `pspCaller`  
 Wskaźnik do obiektu dostawcy usługi dostarczane przez obiekt wywołujący, który sprawia, że obiekt uzyskać usług od elementu wywołującego. Może mieć wartości Null.  
  
 `IDispatchEx::InvokeEx` udostępnia wszystkie te same funkcje co `IDispatch::Invoke` i dodaje kilka rozszerzeń:  
  
|||  
|-|-|  
|DISPATCH_CONSTRUCT|Wskazuje, że element jest używana jako Konstruktor.|  
|`pspCaller`|`pspCaller` Umożliwia uzyskanie obiektu dostępu do usług udostępnianych przez obiekt wywołujący. Określonych usług mogą być obsługiwane przez obiekt wywołujący, samego lub przekazać obiekty wywołujące dodatkowo łańcuch wywołań. Na przykład, jeśli aparat skryptów w przeglądarce sprawia, że `InvokeEx` wykonać wywołanie do obiektu zewnętrznego obiektu `pspCaller` łańcucha uzyskania usług z aparatu skryptów lub przeglądarki. (Należy pamiętać, że łańcuch wywołań nie jest taka sama jak w łańcuchu tworzenia — znana także jako łańcuch kontenera lub łańcucha lokacji. Tworzenie łańcucha mogą być dostępne w innym mechanizmem takich jak `IObjectWithSite`.)|  
|`this` Wskaźnik|Gdy DISPATCH_METHOD jest ustawiona `wFlags`, może to być "parametr o nazwie" wartość "to". Identyfikator DISPID będzie DISPID_THIS i musi być pierwszy parametr o danej nazwie.|  
  
 Nieużywane `riid` parametru w `IDispatch::Invoke` został usunięty.  
  
 `puArgArr` Parametru w `IDispatch::Invoke` został usunięty.  
  
 Zobacz `IDispatch::Invoke` dokumentacji w poniższych przykładach:  
  
 "Wywołanie metody bez argumentów"  
  
 "Pobieranie i ustawianie właściwości"  
  
 "Przekazywanie parametrów"  
  
 "Właściwości indeksowanej"  
  
 "Występowanie wyjątków podczas Invoke"  
  
 "Zwraca błędy"  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|||  
|-|-|  
|`S_OK`|Powodzenie.|  
|DISP_E_BADPARAMCOUNT|Liczba elementów udostępnionych DISPPARAMS różni się od liczby argumentów akceptowanych przez metodę lub właściwość.|  
|DISP_E_BADVARTYPE|Jeden z argumentów `rgvarg` nie jest prawidłowym typem variant.|  
|DISP_E_EXCEPTION|Aplikacja musi zgłosić wyjątek. W tym przypadku struktury przekazanej `pei` powinno być wypełnione.|  
|DISP_E_MEMBERNOTFOUND|Żądany element nie istnieje, lub wywołanie `InvokeEx` próbowano ustawić wartość właściwości tylko do odczytu.|  
|DISP_E_NONAMEDARGS|Ta implementacja `IDispatch` nie obsługuje argumenty nazwane.|  
|DISP_E_OVERFLOW|Jeden z argumentów `rgvarg` nie można przekształcić do określonego typu.|  
|DISP_E_PARAMNOTFOUND|Jeden z parametrów DISPID jest niezgodny z parametrem w metodzie.|  
|DISP_E_TYPEMISMATCH|Nie można przekształcić co najmniej jeden z argumentów.|  
|DISP_E_UNKNOWNLCID|Zinterpretował argumenty typu string według identyfikatora LCID, i nie został rozpoznany identyfikator LCID. Jeśli identyfikator LCID nie jest potrzebna można interpretować argumenty, ten błąd nie powinien być zwracany.|  
|DISP_E_PARAMNOTOPTIONAL|Wymagany parametr został pominięty.|  
  
## <a name="example"></a>Przykład  
  
```cpp
VARIANT var;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
   DISPPARAMS dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
   {  
      pdex->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
   }  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)