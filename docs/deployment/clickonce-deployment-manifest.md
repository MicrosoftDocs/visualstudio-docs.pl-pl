---
title: Manifest wdrożenia ClickOnce | Microsoft Docs
description: Dowiedz się więcej o manifeście wdrożenia, pliku XML, który opisuje wdrożenie ClickOnce, włącznie z bieżącą wersją aplikacji ClickOnce do wdrożenia.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 47589b909ee2b7ee367c81684ac53e2b5e4e7d70
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383095"
---
# <a name="clickonce-deployment-manifest"></a>Manifest wdrożenia ClickOnce
Manifest wdrożenia to plik XML, który opisuje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenie, włącznie z identyfikacją bieżącej [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wersji aplikacji do wdrożenia.

 Manifesty wdrożenia mają następujące elementy i atrybuty.

| Element | Opis | Atrybuty |
| - | - | - |
| [\<assembly> Postaci](../deployment/assembly-element-clickonce-deployment.md) | Wymagane. Element najwyższego poziomu. | `manifestVersion` |
| [\<assemblyIdentity> Postaci](../deployment/assemblyidentity-element-clickonce-deployment.md) | Wymagane. Identyfikuje manifest aplikacji dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. | `name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `culture` |
| [\<description> Postaci](../deployment/description-element-clickonce-deployment.md) | Wymagane. Identyfikuje informacje o aplikacji używane do tworzenia obecności powłoki i apletu **Dodaj lub usuń programy** w panelu sterowania. | `publisher`<br /><br /> `product`<br /><br /> `supportUrl` |
| [\<deployment> Postaci](../deployment/deployment-element-clickonce-deployment.md) | Opcjonalny. Identyfikuje atrybuty używane do wdrożenia aktualizacji i ekspozycji na system. | `install`<br /><br /> `minimumRequiredVersion`<br /><br /> `mapFileExtensions`<br /><br /> `disallowUrlActivation`<br /><br /> `trustUrlParameters` |
| [\<compatibleFrameworks> Postaci](../deployment/compatibleframeworks-element-clickonce-deployment.md) | Wymagane. Identyfikuje wersje .NET Framework, w których ta aplikacja może zostać zainstalowana i uruchomiona. | `SupportUrl` |
| [\<dependency> Postaci](../deployment/dependency-element-clickonce-deployment.md) | Wymagane. Identyfikuje wersję aplikacji do zainstalowania na potrzeby wdrożenia i lokalizację manifestu aplikacji. | `preRequisite`<br /><br /> `visible`<br /><br /> `dependencyType`<br /><br /> `codebase`<br /><br /> `size` |
| [\<publisherIdentity> Postaci](../deployment/publisheridentity-element-clickonce-deployment.md) | Wymagane w przypadku podpisanych manifestów. Zawiera informacje o wydawcy, który podpisał ten manifest wdrożenia. | `Name`<br /><br /> `issuerKeyHash` |
| [\<Signature> Postaci](../deployment/signature-element-clickonce-deployment.md) | Opcjonalny. Zawiera informacje niezbędne do podpisania cyfrowo tego manifestu wdrożenia. | Brak |
| [\<customErrorReporting> Postaci](../deployment/customerrorreporting-element-clickonce-deployment.md) | Opcjonalny. Określa identyfikator URI, który ma być wyświetlany w przypadku wystąpienia błędu. | Adresu |

## <a name="remarks"></a>Uwagi
 Plik manifestu wdrożenia identyfikuje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenie aplikacji, w tym bieżącą wersję i inne ustawienia wdrożenia. Odwołuje się do manifestu aplikacji, który opisuje bieżącą wersję aplikacji i wszystkie pliki zawarte we wdrożeniu.

 Aby uzyskać więcej informacji, zobacz [zabezpieczenia i wdrażanie technologii ClickOnce](../deployment/clickonce-security-and-deployment.md).

## <a name="file-location"></a>Lokalizacja pliku
 Plik manifestu wdrożenia odwołuje się do prawidłowego manifestu aplikacji dla bieżącej wersji aplikacji. Po udostępnieniu nowej wersji wdrożenia aplikacji należy zaktualizować manifest wdrożenia, aby odwołać się do nowego manifestu aplikacji.

 Plik manifestu wdrożenia musi mieć silną nazwę i może również zawierać certyfikaty do walidacji wydawcy.

## <a name="file-name-syntax"></a>Składnia nazwy pliku
 Nazwa pliku manifestu wdrożenia musi kończyć się rozszerzeniem *. Application* .

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

## <a name="see-also"></a>Zobacz też
- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)