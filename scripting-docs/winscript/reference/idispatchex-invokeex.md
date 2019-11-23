---
title: 'IDispatchEx:: InvokeEx | Microsoft Docs'
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
ms.openlocfilehash: 8a15acb3211c0d3dd19c0d262efb6cbd3327ab9a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575321"
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
Zapewnia dostęp do właściwości i metod udostępnianych przez obiekt `IDispatchEx`.  
  
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
 Określa element członkowski. Używa `GetDispID` lub `GetNextDispID` do uzyskania identyfikatora wysyłania.  
  
 `lcid`  
 Ustawienia regionalne kontekstu, w którym można interpretować argumenty. `lcid` jest przenoszona do `InvokeEx`, aby umożliwić obiektowi interpretowanie argumentów specyficznych dla ustawień regionalnych.  
  
 `wFlags`  
 Wartości prawne dla `wFlags` są następujące:  
  
 DISPATCH_PROPERTYGET &#124; DISPATCH_METHOD &#124; DISPATCH_PROPERTYPUT &#124; DISPATCH_PROPERTYPUTREF &#124; DISPATCH_CONSTRUCT  
  
 Flagi opisujące kontekst wywołania `InvokeEx`:  
  
|Value|Znaczenie|  
|-----------|-------------|  
|DISPATCH_METHOD|Element członkowski jest wywoływany jako metoda. Jeśli właściwość ma taką samą nazwę, można ustawić zarówno tę, jak i flagę DISPATCH_PROPERTYGET (zdefiniowaną przez `IDispatch`).|  
|DISPATCH_PROPERTYGET|Element członkowski zostanie pobrany jako właściwość lub element członkowski danych (zdefiniowany przez `IDispatch`).|  
|DISPATCH_PROPERTYPUT|Element członkowski zostanie zmieniony jako właściwość lub element członkowski danych (zdefiniowany przez `IDispatch`).|  
|DISPATCH_PROPERTYPUTREF|Element członkowski zostanie zmieniony przez przypisanie odwołania, a nie przypisanie wartości. Ta flaga jest prawidłowa tylko wtedy, gdy Właściwość akceptuje odwołanie do obiektu (zdefiniowanego przez `IDispatch`).|  
|DISPATCH_CONSTRUCT|Element członkowski jest używany jako Konstruktor. (Jest to nowa wartość zdefiniowana przez `IDispatchEx`). Wartości prawne dla `wFlags` są następujące:<br /><br /> DISPATCH_PROPERTYGET DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 Wskaźnik do struktury zawiera tablicę argumentów, tablicę identyfikatorów DISPID argumentu dla nazwanych argumentów i zlicza liczbę elementów w tablicach. Pełny opis struktury DISPPARAMS można znaleźć w dokumentacji `IDispatch`.  
  
 `pVarRes`  
 Wskaźnik do lokalizacji, w której ma być przechowywany wynik, lub wartość null, jeśli obiekt wywołujący oczekuje braku wyniku. Ten argument jest ignorowany, jeśli określono DISPATCH_PROPERTYPUT lub DISPATCH_PROPERTYPUTREF.  
  
 `pei`  
 Wskaźnik do struktury, która zawiera informacje o wyjątku. Ta struktura powinna zostać wprowadzona, jeśli `DISP_E_EXCEPTION` jest zwracana. Może mieć wartość null. Pełny opis struktury `EXCEPINFO` można znaleźć w dokumentacji `IDispatch`.  
  
 `pspCaller`  
 Wskaźnik do obiektu dostawcy usług dostarczonego przez obiekt wywołujący, który umożliwia obiektowi uzyskanie usług z elementu wywołującego. Może mieć wartość null.  
  
 `IDispatchEx::InvokeEx` udostępnia wszystkie te same funkcje co `IDispatch::Invoke` i dodaje kilka rozszerzeń:  
  
|||  
|-|-|  
|DISPATCH_CONSTRUCT|Wskazuje, że element jest używany jako Konstruktor.|  
|`pspCaller`|`pspCaller` umożliwia dostęp obiektu do usług udostępnianych przez obiekt wywołujący. Określone usługi mogą być obsługiwane przez samego wywołującego lub delegowane do wywoływania w celu dalszej realizacji łańcucha wywołań. Na przykład jeśli aparat skryptu wewnątrz przeglądarki tworzy `InvokeEx` wywołanie do obiektu zewnętrznego, obiekt może następować przy użyciu łańcucha `pspCaller` w celu uzyskania usług z aparatu skryptu lub przeglądarki. (Należy zauważyć, że łańcuch wywołań nie jest taki sam jak łańcuch tworzenia — znany również jako łańcuch kontenerów lub łańcuch witryn. Łańcuch tworzenia może być dostępny za pomocą innego mechanizmu, takiego jak `IObjectWithSite`.)|  
|`this` wskaźnik|Gdy DISPATCH_METHOD jest ustawiony w `wFlags`, może istnieć "nazwany parametr" dla wartości "This". Identyfikator DISPID zostanie DISPID_THIS i musi być pierwszym nazwanym parametrem.|  
  
 Nieużywany parametr `riid` w `IDispatch::Invoke` został usunięty.  
  
 Parametr `puArgArr` w `IDispatch::Invoke` został usunięty.  
  
 Zapoznaj się z dokumentacją `IDispatch::Invoke` w następujących przykładach:  
  
 "Wywoływanie metody bez argumentów"  
  
 "Pobieranie i Ustawianie właściwości"  
  
 "Przekazywanie parametrów"  
  
 "Właściwości indeksowane"  
  
 "Wywoływanie wyjątków"  
  
 "Zwracanie błędów"  
  
## <a name="return-value"></a>Wartość zwrócona  
 Zwraca jedną z następujących wartości:  
  
|||  
|-|-|  
|`S_OK`|Prawnego.|  
|DISP_E_BADPARAMCOUNT|Liczba elementów dostarczonych do DISPPARAMS różni się od liczby argumentów zaakceptowanych przez metodę lub właściwość.|  
|DISP_E_BADVARTYPE|Jeden z argumentów w `rgvarg` nie jest prawidłowym typem VARIANT.|  
|DISP_E_EXCEPTION|Aplikacja musi zgłosić wyjątek. W takim przypadku struktura przeniesiona `pei` powinna zostać wypełniona.|  
|DISP_E_MEMBERNOTFOUND|Żądany element członkowski nie istnieje lub wywołanie `InvokeEx` próbowało ustawić wartość właściwości tylko do odczytu.|  
|DISP_E_NONAMEDARGS|Ta implementacja `IDispatch` nie obsługuje argumentów nazwanych.|  
|DISP_E_OVERFLOW|Nie można przekształcić jednego z argumentów w `rgvarg` określonego typu.|  
|DISP_E_PARAMNOTFOUND|Jeden z identyfikatorów SPID parametru nie odpowiada parametrowi metody.|  
|DISP_E_TYPEMISMATCH|Nie można przekształcić co najmniej jednego z argumentów.|  
|DISP_E_UNKNOWNLCID|Wywoływany element członkowski interpretuje argumenty ciągu zgodnie z identyfikatorem LCID i nie rozpoznano identyfikatora LCID. Jeśli identyfikator LCID nie jest wymagany do interpretacji argumentów, ten błąd nie powinien być zwracany.|  
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
  
## <a name="see-also"></a>Zobacz także  
 [IDispatchEx  interfejsu](../../winscript/reference/idispatchex-interface.md)  
 [IDispatchEx:: getdispid](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)