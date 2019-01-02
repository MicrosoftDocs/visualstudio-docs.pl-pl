---
title: Manifest aplikacji ClickOnce | Dokumentacja firmy Microsoft
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 550b4122775f8d38ed874227bb5b36066f411b9f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53929231"
---
# <a name="clickonce-application-manifest"></a>Manifest aplikacji ClickOnce
A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikacji jest plik XML, który opisuje aplikację, która jest wdrażany za pomocą [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Manifesty aplikacji ma następujące elementy i atrybuty.  


| Element | Opis | Atrybuty |
| - | - | - |
| [\<zestaw > Element](../deployment/assembly-element-clickonce-application.md) | Wymagana. Element najwyższego poziomu. | `manifestVersion` |
| [\<assemblyIdentity > Element](../deployment/assemblyidentity-element-clickonce-application.md) | Wymagana. Określa podstawowy zestaw z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. | `name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language` |
| [\<trustInfo > Element](../deployment/trustinfo-element-clickonce-application.md) | Określa wymagania dotyczące zabezpieczeń aplikacji. | Brak |
| [\<entryPoint > Element](../deployment/entrypoint-element-clickonce-application.md) | Wymagana. Określa punkt wejścia kodu aplikacji. | `name` |
| [\<zależność > Element](../deployment/dependency-element-clickonce-application.md) | Wymagana. Identyfikuje poszczególne zależności wymagane do uruchomienia aplikacji. Opcjonalnie określa zestawy, które muszą być wstępnie zainstalowane. | Brak |
| [\<Plik > Element](../deployment/file-element-clickonce-application.md) | Opcjonalna. Identyfikuje każdy plik nonassembly, który jest używany przez aplikację. Może zawierać dane izolacji Component Object Model (COM) skojarzone z plikiem. | `name`<br /><br /> `size`<br /><br /> `group`<br /><br /> `optional`<br /><br /> `writeableType` |
| [\<fileassociation — > Element](../deployment/fileassociation-element-clickonce-application.md) | Opcjonalna. Określa rozszerzenie pliku do skojarzenia z aplikacją. | `extension`<br /><br /> `description`<br /><br /> `progid`<br /><br /> `defaultIcon` |

## <a name="remarks"></a>Uwagi  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Pliku manifestu aplikacji identyfikuje aplikacje wdrożone za pomocą [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Aby uzyskać więcej informacji na temat [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], zobacz [wdrażania i zabezpieczeń ClickOnce](../deployment/clickonce-security-and-deployment.md).  

## <a name="file-location"></a>Lokalizacja pliku  
 A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikacji jest specyficzny dla jednej wersji wdrożenia. Z tego powodu powinny być przechowywane oddzielnie od manifesty wdrożenia. Typową Konwencją jest umieszczenie ich w podkatalogu nazwanym tak skojarzoną wersję.  

 Zawsze w manifeście aplikacji muszą być podpisane przed wdrożeniem. Jeśli ręcznie zmienisz manifest aplikacji, należy użyć *mage.exe* do ponownego podpisania manifestu aplikacji, zaktualizuj manifest wdrożenia, a następnie ponownie podpisać manifest wdrożenia. Aby uzyskać więcej informacji, zobacz [instruktażu: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  

## <a name="file-name-syntax"></a>Składnia nazwy pliku  
 Nazwa [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pliku manifestu aplikacji powinna być pełną nazwę i rozszerzenie aplikacji, jak wskazano w `assemblyIdentity` elementu, a następnie rozszerzenia *.manifest*. Na przykład manifest aplikacji, która odwołuje się do *Example.exe* aplikacja będzie używać następującej składni nazwy pliku.  

 `example.exe.manifest`  

## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje manifest aplikacji dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji.  

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

## <a name="see-also"></a>Zobacz także  
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)