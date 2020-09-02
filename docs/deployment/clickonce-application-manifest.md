---
title: Manifest aplikacji ClickOnce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- application manifests [ClickOnce]
- ClickOnce, application manifests
ms.assetid: 29570cec-4e53-4660-a850-abc4fa150243
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be9bfe19b92740d6be6c91802d193bf2fc401847
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62928960"
---
# <a name="clickonce-application-manifest"></a>Manifest aplikacji ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Manifest aplikacji to plik XML, który opisuje aplikację wdrożoną za pomocą programu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesty aplikacji mają następujące elementy i atrybuty.

| Element | Opis | Atrybuty |
| - | - | - |
| [\<assembly> Postaci](../deployment/assembly-element-clickonce-application.md) | Wymagany. Element najwyższego poziomu. | `manifestVersion` |
| [\<assemblyIdentity> Postaci](../deployment/assemblyidentity-element-clickonce-application.md) | Wymagany. Identyfikuje podstawowy zestaw [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. | `name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language` |
| [\<trustInfo> Postaci](../deployment/trustinfo-element-clickonce-application.md) | Identyfikuje wymagania dotyczące zabezpieczeń aplikacji. | Brak |
| [\<entryPoint> Postaci](../deployment/entrypoint-element-clickonce-application.md) | Wymagany. Identyfikuje punkt wejścia kodu aplikacji. | `name` |
| [\<dependency> Postaci](../deployment/dependency-element-clickonce-application.md) | Wymagany. Identyfikuje każdą zależność wymaganą do uruchomienia aplikacji. Opcjonalnie identyfikuje zestawy, które muszą być preinstalowane. | Brak |
| [\<file> Postaci](../deployment/file-element-clickonce-application.md) | Opcjonalny. Identyfikuje każdy plik niezestawowy, który jest używany przez aplikację. Może zawierać dane izolacji Component Object Model (COM) skojarzone z plikiem. | `name`<br /><br /> `size`<br /><br /> `group`<br /><br /> `optional`<br /><br /> `writeableType` |
| [\<fileAssociation> Postaci](../deployment/fileassociation-element-clickonce-application.md) | Opcjonalny. Identyfikuje rozszerzenie pliku, które ma być skojarzone z aplikacją. | `extension`<br /><br /> `description`<br /><br /> `progid`<br /><br /> `defaultIcon` |

## <a name="remarks"></a>Uwagi
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Plik manifestu aplikacji identyfikuje aplikację wdrożoną przy użyciu programu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Aby uzyskać więcej informacji na temat [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , zobacz [zabezpieczenia i wdrażanie technologii ClickOnce](../deployment/clickonce-security-and-deployment.md).

## <a name="file-location"></a>Lokalizacja pliku
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Manifest aplikacji jest specyficzny dla jednej wersji wdrożenia. Z tego powodu powinny one być przechowywane oddzielnie od manifestów wdrożenia. Wspólną Konwencją jest umieszczenie ich w podkatalogu o nazwie po skojarzonej wersji.

 Manifest aplikacji zawsze musi być podpisany przed wdrożeniem. W przypadku ręcznego zmiany manifestu aplikacji należy użyć *mage.exe* , aby ponownie podpisać manifest aplikacji, zaktualizować manifest wdrożenia, a następnie ponownie podpisać manifest wdrożenia. Aby uzyskać więcej informacji, zobacz [Przewodnik: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="file-name-syntax"></a>Składnia nazwy pliku
 Nazwa [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pliku manifestu aplikacji powinna być pełną nazwą i rozszerzeniem aplikacji identyfikowanej w `assemblyIdentity` elemencie, po której następuje rozszerzenie *. manifest*. Na przykład manifest aplikacji, który odwołuje się do aplikacji *Example.exe* , użyje następującej składni nazw plików.

 `example.exe.manifest`

## <a name="example"></a>Przykład
 Poniższy przykład kodu przedstawia manifest aplikacji dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji.

```xml
<?xml version="1.0" encoding="utf-8"?>
<asmv1:assembly xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd" manifestVersion="1.0" xmlns:asmv3="urn:schemas-microsoft-com:asm.v3" xmlns:dsig="http://www.w3.org/2000/09/xmldsig#" xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2" xmlns="urn:schemas-microsoft-com:asm.v2" xmlns:asmv1="urn:schemas-microsoft-com:asm.v1" xmlns:asmv2="urn:schemas-microsoft-com:asm.v2" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">
  <asmv1:assemblyIdentity name="My Application Deployment.exe" version="1.0.0.0" publicKeyToken="43cb1e8e7a352766" language="neutral" processorArchitecture="x86" type="win32" />
  <application />
  <entryPoint>
    <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />
    <commandLine file="MyApplication.exe" parameters="" />
  </entryPoint>
  <trustInfo>
    <security>
      <applicationRequestMinimum>
        <PermissionSet Unrestricted="true" ID="Custom" SameSite="site" />
        <defaultAssemblyRequest permissionSetReference="Custom" />
      </applicationRequestMinimum>
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">
        <!--
          UAC Manifest Options
          If you want to change the Windows User Account Control level replace the
          requestedExecutionLevel node with one of the following.

        <requestedExecutionLevel  level="asInvoker" uiAccess="false" />
        <requestedExecutionLevel  level="requireAdministrator" uiAccess="false" />
        <requestedExecutionLevel  level="highestAvailable" uiAccess="false" />

         If you want to utilize File and Registry Virtualization for backward
         compatibility then delete the requestedExecutionLevel node.
    -->
        <requestedExecutionLevel level="asInvoker" uiAccess="false" />
      </requestedPrivileges>
    </security>
  </trustInfo>
  <dependency>
    <dependentOS>
      <osVersionInfo>
        <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
      </osVersionInfo>
    </dependentOS>
  </dependency>
  <dependency>
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
      <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.20506.0" />
    </dependentAssembly>
  </dependency>
  <dependency>
    <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="4096">
      <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />
      <hash>
        <dsig:Transforms>
          <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
        </dsig:Transforms>
        <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
        <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>
      </hash>
    </dependentAssembly>
  </dependency>
<publisherIdentity name="CN=DOMAINCONTROLLER\UserMe" issuerKeyHash="18312a18a21b215ecf4cdb20f5a0e0b0dd263c08" /><Signature Id="StrongNameSignature" xmlns="http://www.w3.org/2000/09/xmldsig#">
...
</Signature></r:issuer></r:license></msrel:RelData></KeyInfo></Signature></asmv1:assembly>
```

## <a name="see-also"></a>Zobacz też
- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)