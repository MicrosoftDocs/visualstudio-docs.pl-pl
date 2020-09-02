---
title: '&lt;File — &gt; element (Aplikacja ClickOnce) | Microsoft Docs'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9345f3f094e1c48204892cd40cca71a7e28eba7c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62900282"
---
# <a name="ltfilegt-element-clickonce-application"></a>&lt;File — &gt; element (Aplikacja ClickOnce)
Identyfikuje wszystkie pliki niezestawowe pobrane i używane przez aplikację.

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

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 `file`Element jest opcjonalny. Element ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`name`|Wymagany. Określa nazwę pliku.|
|`size`|Wymagany. Określa rozmiar pliku w bajtach.|
|`group`|Opcjonalne, jeśli `optional` atrybut nie jest określony lub ma wartość `false` ; wymagane, jeśli `optional` jest `true` . Nazwa grupy, do której należy ten plik. Nazwa może być dowolną wartością ciągu Unicode wybraną przez dewelopera i służy do pobierania plików na żądanie z <xref:System.Deployment.Application.ApplicationDeployment> klasą.|
|`optional`|Opcjonalny. Określa, czy ten plik musi zostać pobrany podczas pierwszego uruchomienia aplikacji, czy plik powinien znajdować się tylko na serwerze, dopóki aplikacja nie zażąda tej aplikacji na żądanie. Jeśli `false` lub niezdefiniowany, plik zostanie pobrany podczas pierwszego uruchomienia lub zainstalowania aplikacji. Jeśli `true` `group` musi być określony, aby manifest aplikacji był prawidłowy. `optional` nie można wykonać wartości true, jeśli `writeableType` określono wartość `applicationData` .|
|`writeableType`|Opcjonalny. Określa, że ten plik jest plikiem danych. Obecnie jedyna prawidłowa wartość to `applicationData` .|

## <a name="typelib"></a>Eksport
 `typelib`Element jest opcjonalnym elementem podrzędnym elementu pliku. Element opisuje bibliotekę typów, która należy do składnika COM. Element ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`tlbid`|Wymagany. Identyfikator GUID przypisany do biblioteki typów.|
|`version`|Wymagany. Numer wersji biblioteki typów.|
|`helpdir`|Wymagany. Katalog zawierający pliki pomocy dla składnika. Może mieć długość 0.|
|`resourceid`|Opcjonalny. Szesnastkowa reprezentacja identyfikatora ustawień regionalnych (LCID). Jest to jeden do czterech cyfr szesnastkowych bez prefiksu 0x i bez zer wiodących. Identyfikator LCID może mieć neutralne identyfikatory języka.|
|`flags`|Opcjonalny. Ciąg reprezentujący flagi biblioteki typów dla tej biblioteki typów. W przypadku powinna być to jeden z wartości "z OGRANICZENIAmi", "CONTROL", "HIDDEN" i "HASDISKIMAGE".|

## <a name="comclass"></a>comClass
 `comClass`Element jest opcjonalnym elementem podrzędnym `file` elementu, ale jest wymagany, jeśli [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja zawiera składnik com, który zamierza wdrożyć przy użyciu modelu COM bez rejestracji. Element ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`clsid`|Wymagany. Identyfikator klasy składnika COM wyrażony jako identyfikator GUID.|
|`description`|Opcjonalny. Nazwa klasy.|
|`threadingModel`|Opcjonalny. Model wątkowości używany przez klasy modelu COM w procesie. Jeśli ta właściwość ma wartość null, nie jest używany żaden model wątkowy. Składnik jest tworzony w głównym wątku klienta i wywołania z innych wątków są organizowane w tym wątku. Poniższa lista zawiera prawidłowe wartości:<br /><br /> `Apartment`, `Free` , `Both` i `Neutral` .|
|`tlbid`|Opcjonalny. Identyfikator GUID dla biblioteki typów dla tego składnika COM.|
|`progid`|Opcjonalny. Identyfikator programistyczny zależny od wersji skojarzony ze składnikiem COM. Format `ProgID` jest `<vendor>.<component>.<version>` .|
|`miscStatus`|Opcjonalny. Duplikaty w manifeście zestawu informacje dostarczone przez `MiscStatus` klucz rejestru. Jeśli `miscStatusIcon` `miscStatusContent` nie można odnaleźć wartości dla atrybutów,, lub, `miscStatusDocprint` `miscStatusThumbnail` odpowiednia wartość domyślna wymieniona w `miscStatus` jest używana dla brakujących atrybutów. Wartość może być rozdzielaną przecinkami listą wartości atrybutów z poniższej tabeli. Tego atrybutu można użyć, jeśli Klasa COM jest klasą OCX wymagającą `MiscStatus` wartości klucza rejestru.|
|`miscStatusIcon`|Opcjonalny. Duplikaty w manifeście zestawu informacje dostarczone przez DVASPECT_ICON. Może zapewnić ikonę obiektu. Wartość może być rozdzielaną przecinkami listą wartości atrybutów z poniższej tabeli. Tego atrybutu można użyć, jeśli Klasa COM jest klasą OCX wymagającą `Miscstatus` wartości klucza rejestru.|
|`miscStatusContent`|Opcjonalny. Duplikaty w manifeście zestawu informacje dostarczone przez DVASPECT_CONTENT. Może zapewnić możliwość wyświetlania dokumentu złożonego dla ekranu lub drukarki. Wartość może być rozdzielaną przecinkami listą wartości atrybutów z poniższej tabeli. Tego atrybutu można użyć, jeśli Klasa COM jest klasą OCX wymagającą `MiscStatus` wartości klucza rejestru.|
|`miscStatusDocPrint`|Opcjonalny. Duplikaty w manifeście zestawu informacje dostarczone przez DVASPECT_DOCPRINT. Może zapewnić, że na ekranie ma być wyświetlana reprezentacja obiektu, tak jakby była drukowana na drukarce. Wartość może być rozdzielaną przecinkami listą wartości atrybutów z poniższej tabeli. Tego atrybutu można użyć, jeśli Klasa COM jest klasą OCX wymagającą `MiscStatus` wartości klucza rejestru.|
|`miscStatusThumbnail`|Opcjonalny. Duplikaty w manifeście zestawu informacje dostarczone przez DVASPECT_THUMBNAIL. Może zapewnić miniaturę obiektu, który można wyświetlić w narzędziu do przeglądania. Wartość może być rozdzielaną przecinkami listą wartości atrybutów z poniższej tabeli. Tego atrybutu można użyć, jeśli Klasa COM jest klasą OCX wymagającą `MiscStatus` wartości klucza rejestru.|

## <a name="cominterfaceexternalproxystub"></a>comInterfaceExternalProxyStub
 `comInterfaceExternalProxyStub`Element jest opcjonalnym elementem podrzędnym `file` elementu, ale może być wymagana, jeśli [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja zawiera składnik com, który zamierza wdrożyć przy użyciu modelu COM bez rejestracji. Element zawiera następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`iid`|Wymagany. Identyfikator interfejsu (IID) obsługiwany przez ten serwer proxy. Identyfikator IID musi zawierać nawiasy klamrowe.|
|`baseInterface`|Opcjonalny. Identyfikator IID interfejsu, z którego pochodzi interfejs wywoływany przez program `iid` .|
|`numMethods`|Opcjonalny. Liczba metod implementowanych przez interfejs.|
|`name`|Opcjonalny. Nazwa interfejsu w postaci, w jakiej będzie wyświetlana w kodzie.|
|`tlbid`|Opcjonalny. Biblioteka typów, która zawiera opis interfejsu określonego przez `iid` atrybut.|
|`proxyStubClass32`|Opcjonalny. Mapuje identyfikator IID na identyfikator CLSID w 32-bitowych bibliotekach DLL serwera proxy.|

## <a name="cominterfaceproxystub"></a>comInterfaceProxyStub
 `comInterfaceProxyStub`Element jest opcjonalnym elementem podrzędnym `file` elementu, ale może być wymagana, jeśli [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja zawiera składnik com, który zamierza wdrożyć przy użyciu modelu COM bez rejestracji. Element zawiera następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`iid`|Wymagany. Identyfikator interfejsu (IID) obsługiwany przez ten serwer proxy. Identyfikator IID musi zawierać nawiasy klamrowe.|
|`baseInterface`|Opcjonalny. Identyfikator IID interfejsu, z którego pochodzi interfejs wywoływany przez program `iid` .|
|`numMethods`|Opcjonalny. Liczba metod implementowanych przez interfejs.|
|`Name`|Opcjonalny. Nazwa interfejsu w postaci, w jakiej będzie wyświetlana w kodzie.|
|`Tlbid`|Opcjonalny. Biblioteka typów, która zawiera opis interfejsu określonego przez `iid` atrybut.|
|`proxyStubClass32`|Opcjonalny. Mapuje identyfikator IID na identyfikator CLSID w 32-bitowych bibliotekach DLL serwera proxy.|
|`threadingModel`|Opcjonalny. Opcjonalny. Model wątkowości używany przez klasy modelu COM w procesie. Jeśli ta właściwość ma wartość null, nie jest używany żaden model wątkowy. Składnik jest tworzony w głównym wątku klienta i wywołania z innych wątków są organizowane w tym wątku. Poniższa lista zawiera prawidłowe wartości:<br /><br /> `Apartment`, `Free` , `Both` i `Neutral` .|

## <a name="windowclass"></a>windowClass
 `windowClass`Element jest opcjonalnym elementem podrzędnym `file` elementu, ale może być wymagana, jeśli [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja zawiera składnik com, który zamierza wdrożyć przy użyciu modelu COM bez rejestracji. Element odwołuje się do klasy okna zdefiniowanej przez składnik COM, do której należy zastosować wersję. Element zawiera następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`versioned`|Opcjonalny. Określa, czy nazwa wewnętrznej klasy okna używana w rejestracji zawiera wersję zestawu, który zawiera klasę okna. Wartość tego atrybutu może być `yes` lub `no` . Wartość domyślna to `yes`. Wartość `no` powinna być używana tylko wtedy, gdy ta sama klasa okna jest definiowana przez składnik side-by-Side i równoważny składnik nienależący do siebie i chcesz traktować je jako tę samą klasę okna. Należy pamiętać, że reguły dotyczące rejestracji klas okien są stosowane — tylko pierwszy składnik, który rejestruje klasę okna, będzie mógł go zarejestrować, ponieważ nie ma zastosowanej wersji.|

## <a name="hash"></a>hash
 `hash`Element jest opcjonalnym elementem podrzędnym `file` elementu. `hash`Element nie ma żadnych atrybutów.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] używa skrótu algorytmu dla wszystkich plików w aplikacji jako sprawdzenie zabezpieczeń, aby upewnić się, że żaden z plików nie został zmieniony po wdrożeniu. Jeśli `hash` element nie jest uwzględniony, to sprawdzenie nie zostanie wykonane. W związku z tym pominięcie `hash` elementu nie jest zalecane.

 Jeśli manifest zawiera plik, który nie jest poddany mieszania, ten manifest nie może być podpisany cyfrowo, ponieważ użytkownicy nie mogą zweryfikować zawartości niezmieszanego pliku.

## <a name="dsigtransforms"></a>dsig: przekształcenia
 `dsig:Transforms`Element jest wymaganym elementem podrzędnym `hash` elementu. `dsig:Transforms`Element nie ma żadnych atrybutów.

## <a name="dsigtransform"></a>dsig: Przekształć
 `dsig:Transform`Element jest wymaganym elementem podrzędnym `dsig:Transforms` elementu. `dsig:Transform`Element ma następujące atrybuty.

| Atrybut | Opis |
|-------------| - |
| `Algorithm` | Algorytm używany do obliczania skrótu dla tego pliku. Obecnie jedyną wartością używaną przez [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] is jest `urn:schemas-microsoft-com:HashTransforms.Identity` . |

## <a name="dsigdigestmethod"></a>dsig: DigestMethod
 `dsig:DigestMethod`Element jest wymaganym elementem podrzędnym `hash` elementu. `dsig:DigestMethod`Element ma następujące atrybuty.

| Atrybut | Opis |
|-------------| - |
| `Algorithm` | Algorytm używany do obliczania skrótu dla tego pliku. Obecnie jedyną wartością używaną przez [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] is jest `http://www.w3.org/2000/09/xmldsig#sha1` . |

## <a name="dsigdigestvalue"></a>dsig: DigestValue
 `dsig:DigestValue`Element jest wymaganym elementem podrzędnym `hash` elementu. `dsig:DigestValue`Element nie ma żadnych atrybutów. Wartość tekstowa jest obliczanym skrótem dla określonego pliku.

## <a name="remarks"></a>Uwagi
 Ten element identyfikuje wszystkie pliki niebędące zestawami, które składają się na aplikację, a w szczególności wartości skrótu dla weryfikacji pliku. Ten element może również zawierać dane izolacji Component Object Model (COM) skojarzone z plikiem. Jeśli plik zostanie zmieniony, plik manifestu aplikacji również musi zostać zaktualizowany w celu odzwierciedlenia zmiany.

## <a name="example"></a>Przykład
 Poniższy przykład kodu ilustruje `file` elementy w manifeście aplikacji dla aplikacji wdrożonej przy użyciu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

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

## <a name="see-also"></a>Zobacz też
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)