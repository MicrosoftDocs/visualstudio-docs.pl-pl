---
title: '&lt;Dependency&gt; — element (Aplikacja ClickOnce) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#osVersionInfo
- urn:schemas-microsoft-com:asm.v2#os
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#dependency
- http://www.w3.org/2000/09/xmldsig#DigestValue
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
- urn:schemas-microsoft-com:asm.v2#dependentAssembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- manifests [ClickOnce], dependency element
- <dependency> element [ClickOnce application manifest]
ms.assetid: 09d6a1e0-60f8-4fbd-843b-8e49ee3115a3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3aa949aa2f8e718ab0209c54a0ea2160c042a4eb
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252495"
---
# <a name="ltdependencygt-element-clickonce-application"></a>&lt;Dependency&gt; — element (Aplikacja ClickOnce)
Identyfikuje platformę lub zależność zestawu, która jest wymagana dla aplikacji.

## <a name="syntax"></a>Składnia

```xml

      <dependency>
   <dependentOS
      supportURL
      description
   >
      <osVersionInfo>
         <os
            majorVersion
            minorVersion
            buildNumber
            servicePackMajor
            servicePackMinor
            productType
            suiteType
         />
      </osVersionInfo>
   </dependentOS>
   <dependentAssembly
      dependencyType
      allowDelayedBinding
      group
      codeBase
      size
   >
      <assemblyIdentity
         name
         version
         processorArchitecture
         language
      >
         <hash>
            <dsig:Transforms>
               <dsig:Transform
                  Algorithm
            />
            </dsig:Transforms>
            <dsig:DigestMethod />
            <dsig:DigestValue>
            </dsig:DigestValue>
    </hash>

      </assemblyIdentity>
   </dependentAssembly>
</dependency>
```

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 `dependency` Element jest wymagany. Może istnieć wiele wystąpień `dependency` tego samego manifestu aplikacji.

 `dependency` Element nie ma żadnych atrybutów i zawiera następujące elementy podrzędne.

### <a name="dependentos"></a>dependentOS
 Opcjonalny. `osVersionInfo` Zawiera element. Elementy `dependentOS` `dependency` i `dependentAssembly` wzajemnie się wykluczają: jeden lub drugi musi istnieć dla elementu, ale nie oba.

 `dependentOS`obsługuje następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`supportUrl`|Opcjonalny. Określa adres URL pomocy technicznej dla platformy zależnej. Ten adres URL jest pokazywany użytkownikowi, gdy zostanie znaleziona wymagana platforma.|
|`description`|Opcjonalny. Opisuje w formularzu czytelnym dla człowieka system operacyjny opisany przez `dependentOS` element.|

### <a name="osversioninfo"></a>osVersionInfo
 Wymagany. Ten element jest elementem podrzędnym `dependentOS` elementu i `os` zawiera element. Ten element nie ma atrybutów.

### <a name="os"></a>Macintosh
 Wymagany. Ten element jest elementem podrzędnym `osVersionInfo` elementu. Ten element ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`majorVersion`|Wymagany. Określa numer wersji głównej systemu operacyjnego.|
|`minorVersion`|Wymagany. Określa numer wersji pomocniczej systemu operacyjnego.|
|`buildNumber`|Wymagany. Określa numer kompilacji systemu operacyjnego.|
|`servicePackMajor`|Wymagany. Określa numer wersji głównej dodatku Service Pack dla systemu operacyjnego.|
|`servicePackMinor`|Opcjonalny. Określa numer pomocniczy dodatku Service Pack dla systemu operacyjnego.|
|`productType`|Opcjonalny. Identyfikuje wartość typu produktu. Prawidłowe wartości to `server`, `workstation`, i `domainController`. Na przykład w przypadku systemu Windows 2000 Professional wartość tego atrybutu to `workstation`.|
|`suiteType`|Opcjonalny. Identyfikuje pakiet produktów dostępny w systemie lub typ konfiguracji systemu. Prawidłowe wartości to `backoffice`, `blade` `datacenter` ,,`home` ,,`smallbusinessRestricted`,,, i`terminal`. `enterprise` `professional` `smallbusiness` Na przykład w przypadku systemu Windows 2000 Professional wartość tego atrybutu to `professional`.|

### <a name="dependentassembly"></a>dependentAssembly
 Opcjonalny. `assemblyIdentity` Zawiera element. Elementy `dependentOS` `dependency` i `dependentAssembly` wzajemnie się wykluczają: jeden lub drugi musi istnieć dla elementu, ale nie oba.

 `dependentAssembly`ma następujące atrybuty.

| Atrybut | Opis |
|-----------------------| - |
| `dependencyType` | Wymagany. Określa typ zależności. Prawidłowe wartości to `preprequisite` i `install`. Zestaw jest instalowany jako część [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. `install` Aby można było zainstalować `prerequisite` aplikację,zestawmusiznajdowaćsięwglobalnejpamięcipodręcznejzestawów[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] (GAC). |
| `allowDelayedBinding` | Wymagany. Określa, czy zestaw może być ładowany programowo w czasie wykonywania. |
| `group` | Opcjonalny. Jeśli atrybut jest ustawiony na `install`, wyznacza nazwaną grupę zestawów, które są instalowane tylko na żądanie. `dependencyType` Aby uzyskać więcej informacji, [zobacz Przewodnik: Pobieranie zestawów na żądanie za pomocą interfejsu API wdrażania ClickOnce przy użyciu](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md)narzędzia Projektant.<br /><br /> Jeśli jest ustawiona `framework` na, `dependencyType` a atrybut jest ustawiony `prerequisite`na, wyznacza zestaw jako część .NET Framework. Globalna pamięć podręczna Assemby (GAC) nie jest sprawdzana dla tego zestawu podczas instalacji programu w wersji .NET Framework 4 i nowszych. |
| `codeBase` | Wymagane, `dependencyType` gdy atrybut jest ustawiony na `install`. Ścieżka do zestawu zależnego. Może być ścieżką bezwzględną lub ścieżką względem bazy kodu manifestu. Ta ścieżka musi być prawidłowym identyfikatorem URI, aby manifest zestawu był prawidłowy. |
| `size` | Wymagane, `dependencyType` gdy atrybut jest ustawiony na `install`. Rozmiar zestawu zależnego, w bajtach. |

### <a name="assemblyidentity"></a>assemblyIdentity
 Wymagany. Ten element jest elementem podrzędnym `dependentAssembly` elementu i ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`name`|Wymagany. Identyfikuje nazwę aplikacji.|
|`version`|Wymagany. Określa numer wersji aplikacji w następującym formacie:`major.minor.build.revision`|
|`publicKeyToken`|Opcjonalny. Określa 16-znakowy ciąg szesnastkowy, który reprezentuje ostatnie 8 bajtów `SHA-1` wartości skrótu klucza publicznego, w którym aplikacja lub zestaw są podpisane. Klucz publiczny używany do podpisywania wykazu musi mieć 2048 bitów lub więcej.|
|`processorArchitecture`|Opcjonalny. Określa procesor. Prawidłowe wartości to `x86` 32-bitowy system Windows i `I64` dla systemu Windows 64-bit.|
|`language`|Opcjonalny. Identyfikuje dwa kody języka części, takie jak EN-US, zestawu.|

### <a name="hash"></a>hash
 Element jest opcjonalnym elementem podrzędnym `assemblyIdentity` elementu. `hash` `hash` Element nie ma żadnych atrybutów.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]używa skrótu algorytmu dla wszystkich plików w aplikacji jako sprawdzenie zabezpieczeń, aby upewnić się, że żaden z plików nie został zmieniony po wdrożeniu. `hash` Jeśli element nie jest uwzględniony, to sprawdzenie nie zostanie wykonane. W związku z `hash` tym pominięcie elementu nie jest zalecane.

### <a name="dsigtransforms"></a>dsig: przekształcenia
 Element jest wymaganym elementem podrzędnym `hash` elementu. `dsig:Transforms` `dsig:Transforms` Element nie ma żadnych atrybutów.

### <a name="dsigtransform"></a>dsig: Przekształć
 Element jest wymaganym elementem podrzędnym `dsig:Transforms` elementu. `dsig:Transform` `dsig:Transform` Element ma następujące atrybuty.

| Atrybut | Opis |
|-------------| - |
| `Algorithm` | Algorytm używany do obliczania skrótu dla tego pliku. Obecnie jedyną wartością używaną przez [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] is `urn:schemas-microsoft-com:HashTransforms.Identity`jest. |

### <a name="dsigdigestmethod"></a>dsig: DigestMethod
 Element jest wymaganym elementem podrzędnym `hash` elementu. `dsig:DigestMethod` `dsig:DigestMethod` Element ma następujące atrybuty.

| Atrybut | Opis |
|-------------| - |
| `Algorithm` | Algorytm używany do obliczania skrótu dla tego pliku. Obecnie jedyną wartością używaną przez [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] is `http://www.w3.org/2000/09/xmldsig#sha1`jest. |

### <a name="dsigdigestvalue"></a>dsig: DigestValue
 Element jest wymaganym elementem podrzędnym `hash` elementu. `dsig:DigestValue` `dsig:DigestValue` Element nie ma żadnych atrybutów. Wartość tekstowa jest obliczanym skrótem dla określonego pliku.

## <a name="remarks"></a>Uwagi
 Wszystkie zestawy używane przez aplikację muszą mieć odpowiadający `dependency` element. Zestawy zależne nie obejmują zestawów, które muszą być wstępnie zainstalowane w globalnej pamięci podręcznej zestawów jako zestawy platform.

## <a name="example"></a>Przykład
 Poniższy przykład kodu ilustruje `dependency` elementy [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] w manifeście aplikacji. Ten przykład kodu jest częścią większego przykładu dostarczonego w temacie [manifestu aplikacji ClickOnce](../deployment/clickonce-application-manifest.md) .

```xml
<dependency>
  <dependentOS>
    <osVersionInfo>
      <os
        majorVersion="4"
        minorVersion="10"
        buildNumber="0"
        servicePackMajor="0" />
    </osVersionInfo>
  </dependentOS>
</dependency>
<dependency>
  <dependentAssembly
    dependencyType="preRequisite"
    allowDelayedBinding="true">
    <assemblyIdentity
      name="Microsoft.Windows.CommonLanguageRuntime"
      version="4.0.20506.0" />
  </dependentAssembly>
</dependency>

<dependency>
  <dependentAssembly
    dependencyType="install"
    allowDelayedBinding="true"
    codebase="MyApplication.exe"
    size="4096">
    <assemblyIdentity
      name="MyApplication"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="x86" />
    <hash>
      <dsig:Transforms>
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
      </dsig:Transforms>
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
      <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>
    </hash>
  </dependentAssembly>
</dependency>
```

## <a name="see-also"></a>Zobacz także
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
- [\<Element > zależności](../deployment/dependency-element-clickonce-deployment.md)