---
title: Manifest wdrażania ClickOnce | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce, deployment manifests
- deployment manifests [ClickOnce]
ms.assetid: 8457e615-e3b6-4990-8dcf-11bc590e4e9b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d2f3383731fcfa314c3b936cd42002186012439
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59648004"
---
# <a name="clickonce-deployment-manifest"></a>Manifest wdrażania ClickOnce
Manifest wdrożenia jest plikiem XML, który opisuje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia, w tym identyfikator bieżącego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wersję aplikacji do wdrożenia.

 Manifesty wdrożenia ma następujące elementy i atrybuty.

| Element | Opis | Atrybuty |
| - | - | - |
| [\<assembly>, element](../deployment/assembly-element-clickonce-deployment.md) | Wymagana. Element najwyższego poziomu. | `manifestVersion` |
| [\<assemblyIdentity>, element](../deployment/assemblyidentity-element-clickonce-deployment.md) | Wymagana. Identyfikuje manifest aplikacji dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. | `name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `culture` |
| [\<description>, element](../deployment/description-element-clickonce-deployment.md) | Wymagana. Określa informacje o aplikacji, które pozwala utworzyć obecności powłoki i **apletu Dodaj lub usuń programy** w Panelu sterowania. | `publisher`<br /><br /> `product`<br /><br /> `supportUrl` |
| [\<deployment>, element](../deployment/deployment-element-clickonce-deployment.md) | Opcjonalna. Określa atrybuty, używany do wdrażania aktualizacji i ograniczyć narażenie na system. | `install`<br /><br /> `minimumRequiredVersion`<br /><br /> `mapFileExtensions`<br /><br /> `disallowUrlActivation`<br /><br /> `trustUrlParameters` |
| [\<compatibleFrameworks>, element](../deployment/compatibleframeworks-element-clickonce-deployment.md) | Wymagana. Identyfikuje wersje programu .NET Framework, gdzie tę aplikację można instalować i uruchamiać. | `SupportUrl` |
| [\<dependency>, element](../deployment/dependency-element-clickonce-deployment.md) | Wymagana. Identyfikuje wersję aplikacji do zainstalowania dla wdrożenia i lokalizację w manifeście aplikacji. | `preRequisite`<br /><br /> `visible`<br /><br /> `dependencyType`<br /><br /> `codebase`<br /><br /> `size` |
| [\<publisherIdentity> Element](../deployment/publisheridentity-element-clickonce-deployment.md) | Wymagany dla podpisanych manifestów. Zawiera informacje o wydawcy, który podpisał tego manifestu wdrażania. | `Name`<br /><br /> `issuerKeyHash` |
| [\<Signature>, element](../deployment/signature-element-clickonce-deployment.md) | Opcjonalna. Zawiera informacje potrzebne do cyfrowego podpisywania to manifest wdrożenia. | Brak |
| [\<customErrorReporting>, element](../deployment/customerrorreporting-element-clickonce-deployment.md) | Opcjonalna. Określa identyfikator URI do wyświetlenia, gdy wystąpi błąd. | Identyfikator URI |

## <a name="remarks"></a>Uwagi
 Identyfikuje pliku manifestu wdrożenia [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia aplikacji, w tym bieżącej wersji i inne ustawienia wdrażania. Odwołuje się manifest aplikacji, który opisuje bieżącą wersję aplikacji i wszystkich plików znajdujących się we wdrożeniu.

 Aby uzyskać więcej informacji, zobacz [wdrażania i zabezpieczeń ClickOnce](../deployment/clickonce-security-and-deployment.md).

## <a name="file-location"></a>Lokalizacja pliku
 Pliku manifestu wdrożenia odwołuje się do właściwej aplikacji manifestu dla bieżącej wersji aplikacji. Po udostępnieniu nowej wersji wdrożenia aplikacji, należy zaktualizować manifest wdrożenia do odwoływania się do nowego manifestu aplikacji.

 Pliku manifestu wdrożenia silnej nazwy i może również zawierać certyfikaty na potrzeby weryfikacji wydawcy.

## <a name="file-name-syntax"></a>Składnia nazwy pliku
 Nazwa pliku manifestu wdrożenia musi kończyć się *.application* rozszerzenia.

## <a name="examples"></a>Przykłady
 Poniższy przykład kodu ilustruje manifest wdrożenia.

```xml
<?xml version="1.0" encoding="utf-8"?>
<asmv1:assembly xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"
  manifestVersion="1.0"
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"
  xmlns="urn:schemas-microsoft-com:asm.v2"
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <assemblyIdentity
    name="My Application Deployment.app"
    version="1.0.0.0"
    publicKeyToken="43cb1e8e7a352766"
    language="neutral"
    processorArchitecture="x86"
    xmlns="urn:schemas-microsoft-com:asm.v1" />
  <description
    asmv2:publisher="My Company Name"
    asmv2:product="My Application"
    xmlns="urn:schemas-microsoft-com:asm.v1" />
  <deployment install="true">
    <subscription>
      <update>
        <expiration maximumAge="0" unit="days" />
      </update>
    </subscription>
    <deploymentProvider codebase="\\myServer\sampleDeployment\MyApplicationDeployment.application" />
  </deployment>
  <compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">
    <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.20506" />
    <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.20506" />
  </compatibleFrameworks>
  <dependency>
    <dependentAssembly
      dependencyType="install"
      codebase="1.0.0.0\My Application Deployment.exe.manifest"
      size="6756">
      <assemblyIdentity
        name="My Application Deployment.exe"
        version="1.0.0.0"
        publicKeyToken="43cb1e8e7a352766"
        language="neutral"
        processorArchitecture="x86"
        type="win32" />
      <hash>
        <dsig:Transforms>
          <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
        </dsig:Transforms>
        <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
        <dsig:DigestValue>E506x9FwNauks7UjQywmzgtd3FE=</dsig:DigestValue>
      </hash>
    </dependentAssembly>
  </dependency>
<publisherIdentity name="CN=DOMAIN\MyUsername" issuerKeyHash="18312a18a21b215ecf4cdb20f5a0e0b0dd263c08" /><Signature Id="StrongNameSignature" xmlns="http://www.w3.org/2000/09/xmldsig#">
...
</Signature></asmv1:assembly>
```

## <a name="see-also"></a>Zobacz także
- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)