---
title: Interfejs IDispatchEx | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDispatchEx interface, about IDispatchEx
- IDispatchEx interface
ms.assetid: 37a3303f-f78e-4b5b-aac8-b836c92819de
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a59f30c5b42301d29b73a4a079837423614da49
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087584"
---
# <a name="idispatchex-interface"></a>Interfejs IDispatchEx
`IDispatchEx`, rozszerzenie `IDispatch` interfejsu, obsługuje funkcje odpowiednie dla dynamicznych języków, takich jak językach skryptów. W tej sekcji opisano `IDispatchEx` interfejsu, różnice między `IDispatch` i `IDispatchEx`oraz uzasadnienie dla rozszerzenia. Oczekuje się, że czytelnicy zna `IDispatch` i mieć dostęp do `IDispatch` dokumentacji.  
  
## <a name="remarks"></a>Uwagi  
 `IDispatch` został opracowany, zasadniczo języka Visual Basic. Podstawowe ograniczenia `IDispatch` jest przyjęto założenie, że obiekty są statyczne. Innymi słowy ponieważ obiekty nie należy zmieniać w czasie wykonywania, informacje o typie można w pełni opisać je w czasie kompilacji. Dynamiczne modeli środowiska wykonawczego, które znajdują się w językach skryptów, takich jak Visual Basic Scripting Edition (VBScript) i [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] modele obiektów, takich jak DHTML wymagają bardziej elastyczny interfejs i.  
  
 `IDispatchEx` został opracowany, aby zapewnić wszystkich usług `IDispatch` oraz niektóre rozszerzenia, które są odpowiednie dla bardziej dynamiczne języków z późnym wiązaniem, takich jak językach skryptów. Dodatkowe funkcje `IDispatchEx` innych niż te dostarczone przez `IDispatch` są:  
  
- Dodawanie nowych członków do obiektu ("expando") — użyj `GetDispID` z `fdexNameEnsure` flagi.  
  
- Usuń elementy członkowskie obiektu — użyj `DeleteMemberByName` lub `DeleteMemberByDispID`.  
  
- Operacje wysyłania uwzględniana wielkość liter — użyj `fdexNameCaseSensitive` lub `fdexNameCaseInsensitive`.  
  
- Wyszukaj element członkowski o nazwie niejawne — użyj `fdexNameImplicit`.  
  
- Wyliczanie DISPID obiektu — użyj `GetNextDispID`.  
  
- Mapowanie nazwy elementu z DISPID — użyj `GetMemberName`.  
  
- Uzyskiwanie właściwości elementów członkowskich obiektu — użyj `GetMemberProperties`.  
  
- Wywołanie metody z `this` wskaźnik — użyj `InvokeEx` z DISPATCH_METHOD.  
  
- Zezwalaj na przeglądarek, które obsługują koncepcję przestrzenie nazw, można uzyskać nadrzędnego przestrzeni nazwy obiektu — użyj `GetNameSpaceParent`.  
  
  Obiekty, które obsługują `IDispatchEx` może również obsługiwać `IDispatch` zgodności z poprzednimi wersjami. Dynamiczny charakter obiektów, które obsługują `IDispatchEx` ma wpływ kilka na `IDispatch` interfejsu tych obiektów. Na przykład `IDispatch` sprawia, że następujące założenia:  
  
- Element członkowski i parametr DISPID musi pozostaje niezmienna przez okres istnienia obiektu. Dzięki temu klientowi uzyskać DISPID raz i zapisać je w pamięci podręcznej do późniejszego użycia.  
  
  Ponieważ `IDispatchEx` zezwala na dodawanie i usuwanie elementów członkowskich, zbiór prawidłowe dispid nie pozostaje niezmienna. Jednak `IDispatchEx` wymaga, że mapowanie między nazwę DISPID i elementów członkowskich pozostał bez zmian. Oznacza to, że usunięcie członka:  
  
- Nie można użyć ponownie DISPID, dopóki nie zostanie utworzony element członkowski o takiej samej nazwie.  
  
- Identyfikator DISPID musi być prawidłowy dla `GetNextDispID`.  
  
- Identyfikator DISPID musi być bezpiecznie zaakceptowana przez żaden z `IDispatch` lub `IDispatchEx` metody — musi rozpoznać elementu członkowskiego jako usunięty i zwracają kod odpowiedni komunikat o błędzie (zazwyczaj DISP_E_MEMBERNOTFOUND lub S_FALSE).  
  
## <a name="examples"></a>Przykłady  
 To [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] kodu w test() funkcja wykonuje następujące czynności:  
  
- Tworzy nowy obiekt przez wywołanie metody `Object` Konstruktor i przypisuje wskaźnik do nowego obiektu, aby zmienna obiektu  
  
- Tworzy nowy element w obiekcie o nazwie Elem i przypisuje do tego elementu wskaźnik do cat funkcji.  
  
- Wywołuje tę funkcję. Ponieważ jest wywoływana jako metoda `this` wskaźnika, który odwołuje się do obiektu obiektu Funkcja dodaje nowy element paska do obiektu.  
  
  Pełny kod HTML jest:  
  
```html
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
  
function test()  
{  
   // Construct new object  
   Obj = new Object();  
  
   // Create new element and assign function pointer  
   Obj.Elem = cat;  
  
   // Call Elem method ("this" == Obj)  
   Obj.Elem();  
  
   // Obj.Bar now exists  
}  
test();  
</script>  
</body>  
</html>  
```  
  
 Kontrolki umieszczone na tej samej stronie sieci Web można uzyskać wskaźnik wysyłania do aparatów skryptów w przeglądarce. Formant może następnie zaimplementować test() funkcji:  
  
```html
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
</script>  
<object id="test" <CLASSID="CLSID:9417DB5D-FA2A-11D0-8CB3-00C04FC2B085">>  
</object>  
</body>  
</html>  
```  
  
 Kod z kontrolki, testowanie, działa tak samo jak [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] funkcja `test()`. Należy pamiętać, że te wysyłanie wywołań do uruchamiania [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] aparatu i zmiany stanu aparatu:  
  
- Uzyskuje wskaźnik wysyłania za pomocą funkcji cat `GetDispID()`.  
  
- Uzyskuje wskaźnik wysyłania za pomocą funkcji obiektu `GetDispID()`.  
  
- Konstruuje obiekt, wywołując funkcję obiektu za pomocą `InvokeEx()` i uzyskuje wskaźnik wysyłania do nowo utworzonym obiekcie.  
  
- Tworzy nowy element Elem, za pomocą obiektu `GetDispID()` z `fdexNameEnsure` flagi.  
  
- Umieszcza wskaźnik wysyłania do cat przy użyciu elementu `InvokeEx()`.  
  
- Wywołuje wskaźnik wysyłania do cat jako metoda, przez wywołanie metody `InvokeEx()` i przekazując we wskaźniku wysyłania do skonstruowanego obiektu jako `this` wskaźnika.  
  
- Metoda cat tworzy nowy element pasek na bieżącym `this` obiektu.  
  
- Sprawdza, czy nowy element paska, został utworzony w utworzonym obiekcie przez wyliczanie elementów za pomocą `GetNextDispID()`.  
  
  Kod dla formantu testu:  
  
```cpp
   BOOL test(IDispatchEx *pdexScript)  
   {  
      HRESULT hr;  
      VARIANT var;  
      DISPID dispid, putid;  
      BOOL retval = FALSE;  
      BSTR bstrName = NULL;  
      IDispatch   *pdispObj = NULL, *pdispCat = NULL;  
      IDispatchEx *pdexObj = NULL;  
      DISPPARAMS dispparams, dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
      // Get dispatch pointer for "cat"  
      bstrName = SysAllocString(OLESTR("cat"));  
         if (bstrName == NULL) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispCat = var.pdispVal;  
  
      // Create object by calling "Object" constructor  
      bstrName = SysAllocString(OLESTR("Object"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_CONSTRUCT, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispObj = var.pdispVal;  
      hr = pdispObj->QueryInterface(IID_IDispatchEx, (void **)&pdexObj);  
         if (FAILED(hr)) goto LDone;  
  
      // Create new element in object  
      bstrName = SysAllocString(OLESTR("Elem"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexObj->GetDispID(bstrName, fdexNameEnsure, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
  
      // Assign "cat" dispatch pointer to element  
      putid = DISPID_PROPERTYPUT;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispCat;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYPUTREF, &dispparams,  
         NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Invoke method with "this" pointer  
      putid = DISPID_THIS;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispObj;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_METHOD, &dispparams,  
            NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Confirm that new element "Bar" is in object  
      hr = pdexObj->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
      while (hr == NOERROR)  
      {  
            hr = pdexObj->GetMemberName(dispid, &bstrName);  
            if (FAILED(hr)) goto LDone;  
            retval = !wcscmp(bstrName, OLESTR("Bar"));  
            SysFreeString(bstrName);  
            bstrName = NULL;  
            if (retval) goto LDone;  
         hr = pdexObj->GetNextDispID(fdexEnumAll, dispid, &dispid);  
      }  
LDone:  
   SysFreeString(bstrName);  
   if (pdispCat != NULL)  
      pdispCat->Release();  
   if (pdispObj != NULL)  
      pdispObj->Release();  
   if (pdexObj != NULL)  
      pdexObj->Release();  
  
   return retval;  
   }  
```  
  
## <a name="methods"></a>Metody  
 [Metody IDispatchEx](../../winscript/reference/idispatchex-methods.md)