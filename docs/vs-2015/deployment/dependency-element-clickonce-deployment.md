---
title: '&lt;Dependency — &gt; element (wdrożenie ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
- <dependency> element [ClickOnce deployment manifest]
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f191b11dfce5b3877d0a31e260e092000a556a5a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187783"
---
# <a name="ltdependencygt-element-clickonce-deployment"></a>&lt;Dependency — &gt; element (wdrażanie ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identyfikuje wersję aplikacji do zainstalowania i lokalizację manifestu aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      <dependency>   
   <dependentAssembly  
      preRequisite  
      visible  
      dependencyType  
      codeBase  
      size  
   >   
      <assemblyIdentity   
         name   
         version   
         publicKeyToken   
         processorArchitecture   
         language  
         type  
      />   
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
  
   </dependentAssembly>   
</dependency>  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `dependency`Element jest wymagany. Nie ma atrybutów. Manifest wdrożenia może zawierać wiele `dependency` elementów.  
  
 `dependency`Element zwykle wyraża zależności dla głównej aplikacji w zestawach zawartych w [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji. Jeśli aplikacja Main.exe zużywa zestaw o nazwie DotNetAssembly.dll, ten zestaw musi znajdować się w sekcji zależności. Zależność, jednak może również wyznaczać inne typy zależności, takie jak zależności w określonej wersji środowiska uruchomieniowego języka wspólnego, w zestawie w globalnej pamięci podręcznej zestawów (GAC) lub w obiekcie COM. Ponieważ nie jest to technologia wdrażania bez dotyku, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nie można zainicjować pobierania i instalacji tych typów zależności, ale uniemożliwia uruchomienie aplikacji, jeśli co najmniej jedno z określonych zależności nie istnieje.  
  
## <a name="dependentassembly"></a>dependentAssembly  
 Wymagany. Ten element zawiera `assemblyIdentity` element. W poniższej tabeli przedstawiono atrybuty obsługiwane przez program `dependentAssembly` .  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`preRequisite`|Opcjonalny. Określa, że ten zestaw powinien już istnieć w pamięci podręcznej GAC. Prawidłowe wartości to `true` i `false` . Jeśli `true` określony zestaw nie istnieje w pamięci PODręcznej GAC, uruchomienie aplikacji nie powiedzie się.|  
|`visible`|Opcjonalny. Identyfikuje tożsamość aplikacji najwyższego poziomu, łącznie z jej zależnościami. Używane wewnętrznie przez program [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] do zarządzania magazynem i aktywacją aplikacji.|  
|`dependencyType`|Wymagany. Relacja między tą zależnością a aplikacją. Prawidłowe wartości:<br /><br /> -   `install`. Składnik reprezentuje oddzielną instalację od bieżącej aplikacji.<br />-   `preRequisite`. Składnik jest wymagany przez bieżącą aplikację.|  
|`codebase`|Opcjonalny. Pełna ścieżka do manifestu aplikacji.|  
|`size`|Opcjonalny. Rozmiar manifestu aplikacji w bajtach.|  
  
## <a name="assemblyidentity"></a>assemblyIdentity  
 Wymagany. Ten element jest elementem podrzędnym `dependentAssembly` elementu. Zawartość `assemblyIdentity` musi być taka sama jak opisana w [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifeście aplikacji. W poniższej tabeli przedstawiono atrybuty `assemblyIdentity` elementu.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Wymagany. Identyfikuje nazwę aplikacji.|  
|`Version`|Wymagany. Określa numer wersji aplikacji w następującym formacie: `major.minor.build.revision`|  
|`publicKeyToken`|Wymagany. Określa 16-znakowy ciąg szesnastkowy, który reprezentuje ostatnie 8 bajtów skrótu SHA-1 klucza publicznego, w którym aplikacja lub zestaw są podpisane. Klucz publiczny używany do podpisywania musi mieć wartość 2048 bitów lub większą.|  
|`processorArchitecture`|Wymagany. Określa mikroprocesor. Prawidłowe wartości to `x86` 32-bitowy system Windows i `IA64` dla systemu Windows 64-bit.|  
|`Language`|Opcjonalny. Identyfikuje dwa kody języka części zestawu. Na przykład EN-US, która oznacza angielski (Stany Zjednoczone). Wartość domyślna to `neutral`. Ten element znajduje się w `asmv2` przestrzeni nazw.|  
|`type`|Opcjonalny. W celu zapewnienia zgodności z poprzednimi wersjami z technologią instalacji równoległej systemu Windows. Jedyna dozwolona wartość to `win32` .|  
  
## <a name="hash"></a>hash  
 `hash`Element jest opcjonalnym elementem podrzędnym `file` elementu. `hash`Element nie ma żadnych atrybutów.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] używa skrótu algorytmu dla wszystkich plików w aplikacji jako kontroli zabezpieczeń, aby upewnić się, że żaden z plików nie został zmieniony po wdrożeniu. Jeśli `hash` element nie jest uwzględniony, to sprawdzenie nie zostanie wykonane. W związku z tym pominięcie `hash` elementu nie jest zalecane.  
  
## <a name="dsigtransforms"></a>dsig: przekształcenia  
 `dsig:Transforms`Element jest wymaganym elementem podrzędnym `hash` elementu. `dsig:Transforms`Element nie ma żadnych atrybutów.  
  
## <a name="dsigtransform"></a>dsig: Przekształć  
 `dsig:Transform`Element jest wymaganym elementem podrzędnym `dsig:Transforms` elementu. W poniższej tabeli przedstawiono atrybuty `dsig:Transform` elementu.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Algorithm`|Algorytm używany do obliczania skrótu dla tego pliku. Obecnie jedyną wartością używaną przez [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] is jest `urn:schemas-microsoft-com:HashTransforms.Identity` .|  
  
## <a name="dsigdigestmethod"></a>dsig: DigestMethod  
 `dsig:DigestMethod`Element jest wymaganym elementem podrzędnym `hash` elementu. W poniższej tabeli przedstawiono atrybuty `dsig:DigestMethod` elementu.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Algorithm`|Algorytm używany do obliczania skrótu dla tego pliku. Obecnie jedyną wartością używaną przez [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] is jest `http://www.w3.org/2000/09/xmldsig#sha1` .|  
  
## <a name="dsigdigestvalue"></a>dsig: DigestValue  
 `dsig:DigestValue`Element jest wymaganym elementem podrzędnym `hash` elementu. `dsig:DigestValue`Element nie ma żadnych atrybutów. Wartość tekstowa jest obliczanym skrótem dla określonego pliku.  
  
## <a name="remarks"></a>Uwagi  
 Manifesty wdrożenia zazwyczaj mają jeden `assemblyIdentity` element, który identyfikuje nazwę i wersję manifestu aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu przedstawia `dependency` element w [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifeście wdrożenia.  
  
```  
<!-- Identify the assembly dependencies -->  
<dependency>  
  <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="16384">  
    <assemblyIdentity name="MyApplication" version="0.0.0.0" cultural="neutral" processorArchitecture="msil" />  
    <hash>  
      <dsig:Transforms>  
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
      </dsig:Transforms>  
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
       <dsig:DigestValue>YzXYZJAvj9pgAG3y8jXUjC7AtHg=</dsig:DigestValue>  
    </hash>  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu określa zależność od zestawu już zainstalowanego w pamięci podręcznej GAC.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu określa zależność od określonej wersji środowiska uruchomieniowego języka wspólnego.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu określa zależność systemu operacyjnego.  
  
```  
<dependency>  
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">  
      <osVersionInfo>  
         <os majorVersion="4" minorVersion="10" />  
      </osVersionInfo>  
   </dependentOS>  
</dependency>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifest wdrożenia ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [\<dependency> Postaci](../deployment/dependency-element-clickonce-application.md)
