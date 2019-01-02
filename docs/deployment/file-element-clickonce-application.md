---
title: '&lt;plik&gt; — Element (aplikacja ClickOnce) | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#file
- http://www.w3.org/2000/09/xmldsig#DigestValue
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <file> element [ClickOnce application manifest]
- manifests [ClickOnce], file element
ms.assetid: 56e3490c-eed5-4841-b1bf-eefe778b6ac9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c16c2cb00bf91d3fc0d991be71ba9b387d5a09cb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53828306"
---
# <a name="ltfilegt-element-clickonce-application"></a>&lt;plik&gt; — element (aplikacja ClickOnce)
Identyfikuje wszystkie pliki nonassembly pobierane i używane przez aplikację.  

## <a name="syntax"></a>Składnia  

```xml  
<file  
    name  
    size  
    group  
    optional  
    writeableType  
>  
    <typelib  
        tlbid  
        version  
        helpdir  
        resourceid  
        flags  
    />  
    <comClass  
        clsid  
        description  
        threadingModel  
        tlbid  
        progid  
        miscStatus  
        miscStatusIcon  
        miscStatusContent  
        miscStatusDocPrint  
        miscStatusThumbnail  
    />  
    <comInterfaceExternalProxyStub  
        iid  
        baseInterface  
        numMethods  
        name  
        tlbid  
        proxyStubClass32  
    />  
    <comInterfaceProxyStub  
        iid  
        baseInterface  
        numMethods  
        name  
        tlbid  
        proxyStubClass32  
    />  
    <windowClass  
        versioned  
    />  
</file>  
```  

## <a name="elements-and-attributes"></a>Atrybuty i elementy  
 `file` Element jest opcjonalne. Element ma następujące atrybuty.  

|Atrybut|Opis|  
|---------------|-----------------|  
|`name`|Wymagana. Określa nazwę pliku.|  
|`size`|Wymagana. Określa rozmiar w bajtach, pliku.|  
|`group`|Opcjonalny, jeśli `optional` atrybut jest określony lub nie ustawiono `false`; wymagany, jeżeli `optional` jest `true`. Nazwa grupy, do której należy ten plik. Nazwa może być dowolną wartością ciągu Unicode, wybierany przez deweloperów i służy do pobierania plików na żądanie przy użyciu <xref:System.Deployment.Application.ApplicationDeployment> klasy.|  
|`optional`|Opcjonalna. Określa, czy ten plik musi uruchomić pobieranie, gdy aplikacja jest pierwszym, czy plik powinien znajdować się tylko na serwerze do momentu aplikacja żąda ją na żądanie. Jeśli `false` lub niezdefiniowany, plik jest pobierany podczas najpierw uruchomić lub zainstalować aplikacji. Jeśli `true`, `group` musi być określony dla manifestu aplikacji był prawidłowy. `optional` nie może mieć wartość true, jeśli `writeableType` jest określony z wartością `applicationData`.|  
|`writeableType`|Opcjonalna. Określa, że ten plik jest plikiem danych. Obecnie jedyna prawidłowa wartość to `applicationData`.|  

## <a name="typelib"></a>biblioteki typów  
 `typelib` Element jest opcjonalny element podrzędny elementu file. Element zawiera opis biblioteki typów, który należy do składnika COM. Element ma następujące atrybuty.  

|Atrybut|Opis|  
|---------------|-----------------|  
|`tlbid`|Wymagana. Identyfikator GUID jest przypisany do biblioteki typów.|  
|`version`|Wymagana. Numer wersji biblioteki typów.|  
|`helpdir`|Wymagana. Katalog, który zawiera pliki pomocy dla tego składnika. Może mieć długości zerowej.|  
|`resourceid`|Opcjonalna. Reprezentacja ciągu szesnastkowego identyfikator ustawień regionalnych (LCID). Jest jednej do czterech liczb szesnastkowych bez prefiksu 0 x i bez zer wiodących. Identyfikator LCID może mieć identyfikator podjęzyk neutralne.|  
|`flags`|Opcjonalna. Ciąg reprezentujący flagi biblioteki typów dla tego typu biblioteki. W szczególności powinien być jednym z "RESTRICTED", "CONTROL", "HIDDEN" i "HASDISKIMAGE".|  

## <a name="comclass"></a>comClass  
 `comClass` Element jest opcjonalny element podrzędny elementu `file` elementu, ale jest wymagany, jeśli [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja zawiera składnik COM zamierza wdrażanie przy użyciu rejestracji wolnego modelu COM. Element ma następujące atrybuty.  

|Atrybut|Opis|  
|---------------|-----------------|  
|`clsid`|Wymagana. Identyfikator klasy składnika modelu COM, wyrażony jako identyfikator GUID.|  
|`description`|Opcjonalna. Nazwa klasy.|  
|`threadingModel`|Opcjonalna. Model wątkowości, używane przez klasy modelu COM w procesie. Jeśli ta właściwość ma wartość null, jest używany bez modelu wątkowości. Składnik jest tworzony w głównym wątku klienta i wywołania z innych wątków są przekazywane do tego wątku. Poniższa lista przedstawia prawidłowe wartości:<br /><br /> `Apartment`, `Free`, `Both`, i `Neutral`.|  
|`tlbid`|Opcjonalna. Identyfikator GUID dla biblioteki typów dla tego składnika COM.|  
|`progid`|Opcjonalna. Identyfikator programowy zależne od wersji skojarzony z składnika COM. Format `ProgID` jest `<vendor>.<component>.<version>`.|  
|`miscStatus`|Opcjonalna. Duplikaty w zestawie manifestu informacji dostarczonych przez `MiscStatus` klucza rejestru. Jeśli wartości `miscStatusIcon`, `miscStatusContent`, `miscStatusDocprint`, lub `miscStatusThumbnail` atrybutów nie zostaną znalezione, odpowiadająca wartość w domyślnej liście `miscStatus` służy do brakujących atrybutów. Wartość może być rozdzielana przecinkami lista wartości atrybutu z poniższej tabeli. Można użyć tego atrybutu, jeśli klasa COM jest klasą OCX, która wymaga `MiscStatus` wartości kluczy rejestru.|  
|`miscStatusIcon`|Opcjonalna. Duplikaty w zestawie manifestu informacji dostarczonych przez DVASPECT_ICON. Umożliwia ona ikoną obiektu. Wartość może być rozdzielana przecinkami lista wartości atrybutu z poniższej tabeli. Można użyć tego atrybutu, jeśli klasa COM jest klasą OCX, która wymaga `Miscstatus` wartości kluczy rejestru.|  
|`miscStatusContent`|Opcjonalna. Duplikaty w zestawie manifestu informacji dostarczonych przez DVASPECT_CONTENT. Może ona dokumencie złożonym, którą można wyświetlić dla ekranu lub drukarki. Wartość może być rozdzielana przecinkami lista wartości atrybutu z poniższej tabeli. Można użyć tego atrybutu, jeśli klasa COM jest klasą OCX, która wymaga `MiscStatus` wartości kluczy rejestru.|  
|`miscStatusDocPrint`|Opcjonalna. Duplikaty w zestawie manifestu informacji dostarczonych przez DVASPECT_DOCPRINT. Umożliwia ona reprezentację obiektu w postaci wyświetlanej na ekranie tak, jakby drukowania na drukarce. Wartość może być rozdzielana przecinkami lista wartości atrybutu z poniższej tabeli. Można użyć tego atrybutu, jeśli klasa COM jest klasą OCX, która wymaga `MiscStatus` wartości kluczy rejestru.|  
|`miscStatusThumbnail`|Opcjonalna. Duplikaty w zestawie manifestu informacji dostarczonych przez DVASPECT_THUMBNAIL. Umożliwia ona miniaturę wyświetlanej w narzędziu do przeglądania obiektu. Wartość może być rozdzielana przecinkami lista wartości atrybutu z poniższej tabeli. Można użyć tego atrybutu, jeśli klasa COM jest klasą OCX, która wymaga `MiscStatus` wartości kluczy rejestru.|  

## <a name="cominterfaceexternalproxystub"></a>comInterfaceExternalProxyStub  
 `comInterfaceExternalProxyStub` Element jest opcjonalny element podrzędny elementu `file` elementu, ale może być wymagane, jeśli [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja zawiera składnik COM zamierza wdrażanie przy użyciu rejestracji wolnego modelu COM. Element zawiera następujące atrybuty.  

|Atrybut|Opis|  
|---------------|-----------------|  
|`iid`|Wymagana. Interfejs identyfikator (IID), który jest obsługiwany przez ten serwer proxy. Identyfikator IID musi mieć nawiasów klamrowych otaczających je.|  
|`baseInterface`|Opcjonalna. IID interfejsu, z którego odwołuje się interfejs `iid` pochodzi.|  
|`numMethods`|Opcjonalna. Liczba metod zaimplementowanych przez interfejs.|  
|`name`|Opcjonalna. Nazwa interfejsu, ponieważ pojawi się w kodzie.|  
|`tlbid`|Opcjonalna. Biblioteki typów, który zawiera opis interfejs określony przez `iid` atrybutu.|  
|`proxyStubClass32`|Opcjonalna. Mapuje IID CLSID serwera proxy 32-bitowych bibliotek DLL.|  

## <a name="cominterfaceproxystub"></a>comInterfaceProxyStub  
 `comInterfaceProxyStub` Element jest opcjonalny element podrzędny elementu `file` elementu, ale może być wymagane, jeśli [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja zawiera składnik COM zamierza wdrażanie przy użyciu rejestracji wolnego modelu COM. Element zawiera następujące atrybuty.  

|Atrybut|Opis|  
|---------------|-----------------|  
|`iid`|Wymagana. Interfejs identyfikator (IID), który jest obsługiwany przez ten serwer proxy. Identyfikator IID musi mieć nawiasów klamrowych otaczających je.|  
|`baseInterface`|Opcjonalna. IID interfejsu, z którego odwołuje się interfejs `iid` pochodzi.|  
|`numMethods`|Opcjonalna. Liczba metod zaimplementowanych przez interfejs.|  
|`Name`|Opcjonalna. Nazwa interfejsu, ponieważ pojawi się w kodzie.|  
|`Tlbid`|Opcjonalna. Biblioteki typów, który zawiera opis interfejs określony przez `iid` atrybutu.|  
|`proxyStubClass32`|Opcjonalna. Mapuje IID CLSID serwera proxy 32-bitowych bibliotek DLL.|  
|`threadingModel`|Opcjonalna. Opcjonalna. Model wątkowości, używane przez klasy modelu COM w procesie. Jeśli ta właściwość ma wartość null, jest używany bez modelu wątkowości. Składnik jest tworzony w głównym wątku klienta i wywołania z innych wątków są przekazywane do tego wątku. Poniższa lista przedstawia prawidłowe wartości:<br /><br /> `Apartment`, `Free`, `Both`, i `Neutral`.|  

## <a name="windowclass"></a>windowClass  
 `windowClass` Element jest opcjonalny element podrzędny elementu `file` elementu, ale może być wymagane, jeśli [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja zawiera składnik COM zamierza wdrażanie przy użyciu rejestracji wolnego modelu COM. Element odwołuje się do klasy okna, zdefiniowane przez składnik COM, który musi mieć wersję stosowane do niego. Element zawiera następujące atrybuty.  

|Atrybut|Opis|  
|---------------|-----------------|  
|`versioned`|Opcjonalna. Czy wewnętrzny okna klasy nazwa używana podczas rejestracji zawiera wersję zestawu, który zawiera klasę okna kontrolki. Wartość tego atrybutu może być `yes` lub `no`. Wartość domyślna to `yes`. Wartość `no` należy używać tylko jeśli w tej samej klasy okna jest definiowany przez side-by-side i równoważne składnik nie side-by-side i chcesz je traktować jako tej samej klasy okna. Należy zauważyć, że zwykle stosuje się zasady o rejestrowanie klasy okna — tylko pierwszy składnik, który rejestruje klasę okna będzie można zarejestrować go, ponieważ nie ma wersji stosowane do niego.|  

## <a name="hash"></a>hash  
 `hash` Element jest opcjonalny element podrzędny elementu `file` elementu. `hash` Element nie ma żadnych atrybutów.  

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] używa konsolidatorze skrótów wszystkich plików w aplikacji w celu sprawdzenia zabezpieczeń, aby upewnić się, że żaden z plików zostały zmienione po wdrożeniu. Jeśli `hash` element nie jest uwzględniony, ten test nie zostanie wykonane. W związku z pominięciem `hash` element nie jest zalecane.  

 Jeśli manifest zawiera plik, który nie jest mieszany, że manifest nie może być cyfrowo podpisany, ponieważ użytkownicy nie może sprawdzić zawartość pliku bez haszowania.  

## <a name="dsigtransforms"></a>DSIG:TRANSFORMS  
 `dsig:Transforms` Element jest wymagany element podrzędny elementu `hash` elementu. `dsig:Transforms` Element nie ma żadnych atrybutów.  

## <a name="dsigtransform"></a>DSIG:Transform  
 `dsig:Transform` Element jest wymagany element podrzędny elementu `dsig:Transforms` elementu. `dsig:Transform` Element ma następujące atrybuty.  


| Atrybut | Opis |
|-------------| - |
| `Algorithm` | Algorytm używany do obliczania skrótu dla tego pliku. Obecnie tylko wartość używana przez [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] jest `urn:schemas-microsoft-com:HashTransforms.Identity`. |

## <a name="dsigdigestmethod"></a>DSIG:DigestMethod  
 `dsig:DigestMethod` Element jest wymagany element podrzędny elementu `hash` elementu. `dsig:DigestMethod` Element ma następujące atrybuty.  


| Atrybut | Opis |
|-------------| - |
| `Algorithm` | Algorytm używany do obliczania skrótu dla tego pliku. Obecnie tylko wartość używana przez [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] jest `http://www.w3.org/2000/09/xmldsig#sha1`. |

## <a name="dsigdigestvalue"></a>DSIG:DigestValue  
 `dsig:DigestValue` Element jest wymagany element podrzędny elementu `hash` elementu. `dsig:DigestValue` Element nie ma żadnych atrybutów. Jego wartość tekstowa jest obliczana wartość skrótu dla określonego pliku.  

## <a name="remarks"></a>Uwagi  
 Ten element określa wszystkie pliki nonassembly, które tworzą aplikację, a w szczególności wartości skrótu dla pliku weryfikacji. Ten element może także zawierać dane izolacji Component Object Model (COM), skojarzone z plikiem. Jeśli zmieni się pliku, plik manifestu aplikacji musi można również zaktualizować do odzwierciedlenia zmiany.  

## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu pokazano `file` elementów w aplikacji manifestu dla aplikacji wdrożonych za pomocą [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  

```xml  
<file name="Icon.ico" size="9216">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>lVoj+Rh6RQ/HPNLOdayQah5McrI=</dsig:DigestValue>  
  </hash>  
</file>  
```  

## <a name="see-also"></a>Zobacz także  
 [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)