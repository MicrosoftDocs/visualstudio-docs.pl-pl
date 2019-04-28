---
title: '&lt;zależność&gt; — Element (aplikacja ClickOnce) | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 7c9172749dc00acf0fd43725f6754373a0ade16e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62900361"
---
# <a name="ltdependencygt-element-clickonce-application"></a>&lt;zależność&gt; — element (aplikacja ClickOnce)
Określa zależność platformy lub zestawu, który jest wymagany dla aplikacji.

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

## <a name="elements-and-attributes"></a>Atrybuty i elementy
 `dependency` Element jest wymagany. Może istnieć wiele wystąpień `dependency` w tym samym manifestu aplikacji.

 `dependency` Element nie ma żadnych atrybutów i zawiera następujące elementy podrzędne.

### <a name="dependentos"></a>dependentOS
 Opcjonalna. Zawiera `osVersionInfo` elementu. `dependentOS` i `dependentAssembly` elementy wykluczają się wzajemnie: jednej z nich, musi istnieć przez `dependency` elementu, ale nie oba.

 `dependentOS` obsługuje następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`supportUrl`|Opcjonalna. Określa adres URL pomocy technicznej dla platformy zależnych. Ten adres URL jest wyświetlany użytkownikowi, jeśli znajduje się wymagane platformy.|
|`description`|Opcjonalna. W tym artykule opisano, w postaci czytelnej dla człowieka, systemu operacyjnego opisana przez `dependentOS` elementu.|

### <a name="osversioninfo"></a>osVersionInfo
 Wymagana. Ten element jest elementem podrzędnym `dependentOS` elementu i zawiera `os` elementu. Ten element nie ma żadnych atrybutów.

### <a name="os"></a>os
 Wymagana. Ten element jest elementem podrzędnym `osVersionInfo` elementu. Ten element ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`majorVersion`|Wymagana. Określa główny numer wersji systemu operacyjnego.|
|`minorVersion`|Wymagana. Określa pomocniczy numer wersji systemu operacyjnego.|
|`buildNumber`|Wymagana. Określa numer kompilacji systemu operacyjnego.|
|`servicePackMajor`|Wymagana. Określa usługę pakiet główny numer systemu operacyjnego.|
|`servicePackMinor`|Opcjonalna. Określa numer pomocnicza usługa pakietu systemu operacyjnego.|
|`productType`|Opcjonalna. Umożliwia określenie wartości typu produktu. Prawidłowe wartości to `server`, `workstation`, i `domainController`. Na przykład Windows 2000 Professional, ta wartość atrybutu jest `workstation`.|
|`suiteType`|Opcjonalna. Identyfikuje pakiet produktów systemu lub typ konfiguracji systemu. Prawidłowe wartości to `backoffice`, `blade`, `datacenter`, `enterprise`, `home`, `professional`, `smallbusiness`, `smallbusinessRestricted`, i `terminal`. Na przykład Windows 2000 Professional, ta wartość atrybutu jest `professional`.|

### <a name="dependentassembly"></a>dependentAssembly
 Opcjonalna. Zawiera `assemblyIdentity` elementu. `dependentOS` i `dependentAssembly` elementy wykluczają się wzajemnie: jednej z nich, musi istnieć przez `dependency` elementu, ale nie oba.

 `dependentAssembly` ma następujące atrybuty.

| Atrybut | Opis |
|-----------------------| - |
| `dependencyType` | Wymagana. Określa typ zależności. Prawidłowe wartości to `preprequisite` i `install`. `install` Zestawów jest instalowany jako część [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. A `prerequisite` zestawu musi znajdować się w globalnej pamięci podręcznej zestawów (GAC) przed [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] można zainstalować aplikacji. |
| `allowDelayedBinding` | Wymagana. Określa, czy zestaw można załadować programowo w czasie wykonywania. |
| `group` | Opcjonalna. Jeśli `dependencyType` ma ustawioną wartość atrybutu `install`, Określa nazwaną grupę zestawów tę instalację tylko na żądanie. Aby uzyskać więcej informacji, zobacz [instruktażu: Pobieranie zestawów na żądanie z wdrożeniem ClickOnce interfejsu API przy użyciu narzędzia Projektant](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md).<br /><br /> Jeśli ustawiono `framework` i `dependencyType` ma ustawioną wartość atrybutu `prerequisite`, określa zestaw jako część programu .NET Framework. Dla tego zestawu nie zaznaczono assemby globalnej pamięci podręcznej (GAC), podczas instalowania na [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] i nowszych wersjach. |
| `codeBase` | Wymagany, gdy `dependencyType` ma ustawioną wartość atrybutu `install`. Ścieżka do zestawu zależnego. Może być ścieżką bezwzględną lub ścieżką względną wobec manifestu kod podstawowy. Ta ścieżka musi być prawidłowym identyfikatorem URI w kolejności do manifestu zestawu był prawidłowy. |
| `size` | Wymagany, gdy `dependencyType` ma ustawioną wartość atrybutu `install`. Rozmiar zależnego zestawu, w bajtach. |

### <a name="assemblyidentity"></a>assemblyIdentity
 Wymagana. Ten element jest elementem podrzędnym `dependentAssembly` elementu i ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`name`|Wymagana. Określa nazwę aplikacji.|
|`version`|Wymagana. Określa numer wersji aplikacji w następującym formacie: `major.minor.build.revision`|
|`publicKeyToken`|Opcjonalna. Określa ciąg szesnastkowy 16-znakowy, który reprezentuje ostatnie 8 bajtów `SHA-1` wyznaczania wartości skrótu wartość klucza publicznego, w ramach której aplikacja lub zestaw jest podpisany. Klucz publiczny używany do podpisywania katalogu musi być 2048 bitów lub więcej.|
|`processorArchitecture`|Opcjonalna. Określa procesor. Prawidłowe wartości to `x86` dla Windows 32-bitowe i `I64` dla Windows 64-bitowych.|
|`language`|Opcjonalna. Identyfikuje części dwóch kodów języków, takim jak pl-pl. zestawu.|

### <a name="hash"></a>hash
 `hash` Element jest opcjonalny element podrzędny elementu `assemblyIdentity` elementu. `hash` Element nie ma żadnych atrybutów.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] używa konsolidatorze skrótów wszystkich plików w aplikacji w celu sprawdzenia zabezpieczeń, aby upewnić się, że żaden z plików zostały zmienione po wdrożeniu. Jeśli `hash` element nie jest uwzględniony, ten test nie zostanie wykonane. W związku z pominięciem `hash` element nie jest zalecane.

### <a name="dsigtransforms"></a>DSIG:TRANSFORMS
 `dsig:Transforms` Element jest wymagany element podrzędny elementu `hash` elementu. `dsig:Transforms` Element nie ma żadnych atrybutów.

### <a name="dsigtransform"></a>DSIG:Transform
 `dsig:Transform` Element jest wymagany element podrzędny elementu `dsig:Transforms` elementu. `dsig:Transform` Element ma następujące atrybuty.

| Atrybut | Opis |
|-------------| - |
| `Algorithm` | Algorytm używany do obliczania skrótu dla tego pliku. Obecnie tylko wartość używana przez [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] jest `urn:schemas-microsoft-com:HashTransforms.Identity`. |

### <a name="dsigdigestmethod"></a>DSIG:DigestMethod
 `dsig:DigestMethod` Element jest wymagany element podrzędny elementu `hash` elementu. `dsig:DigestMethod` Element ma następujące atrybuty.

| Atrybut | Opis |
|-------------| - |
| `Algorithm` | Algorytm używany do obliczania skrótu dla tego pliku. Obecnie tylko wartość używana przez [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] jest `http://www.w3.org/2000/09/xmldsig#sha1`. |

### <a name="dsigdigestvalue"></a>dsig:DigestValue
 `dsig:DigestValue` Element jest wymagany element podrzędny elementu `hash` elementu. `dsig:DigestValue` Element nie ma żadnych atrybutów. Jego wartość tekstowa jest obliczana wartość skrótu dla określonego pliku.

## <a name="remarks"></a>Uwagi
 Wszystkie zestawy używanych przez aplikację muszą mieć odpowiedni `dependency` elementu. Zależnych zestawów zawiera zestawy, które musi być wstępnie zainstalowane w globalnej pamięci podręcznej jako zestawy dla platform.

## <a name="example"></a>Przykład
 W poniższym przykładzie kodu pokazano `dependency` elementów w [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestu aplikacji. Ten przykład kodu jest częścią większego przykładu przewidzianego dla [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md) tematu.

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
- [\<zależność > element](../deployment/dependency-element-clickonce-deployment.md)