---
title: Adres URL pomocy technicznej wstępnie wymaganych składników wdrożenia ClickOnce
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- ClickOnce deployment, URLs
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf115ad6ce8fb589e9b1c617f40053cf95af2b9c
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263220"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Instrukcje: Określ adres URL pomocy technicznej dla indywidualnych wstępnie wymaganych składników wdrożenia ClickOnce
A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pewne wymagania wstępne, które muszą być dostępne na komputerze klienckim, aby sprawdzić wdrożenia [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] do uruchomienia aplikacji. Te zależności obejmują wymaganą minimalną wersję [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], wersję systemu operacyjnego i dowolne zestawy, które muszą być wstępnie zainstalowane w globalnej pamięci podręcznej zestawów (GAC). [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], jednak nie zainstalują dowolną z tych wymagań wstępnych. Jeśli warunek wstępny nie zostanie znaleziony, po prostu zatrzymuje instalację i wyświetla okno dialogowe wyjaśniające, dlaczego instalacja nie powiodła się.

 Istnieją dwie metody instalacji wymagań wstępnych. Możesz zainstalować je przy użyciu aplikacji programu inicjującego. Alternatywnie można określić adres URL pomocy technicznej dla indywidualnych wstępnie wymaganych, który jest wyświetlany użytkownikom w oknie dialogowym, jeśli wymagań wstępnych nie zostanie znaleziony. Strony odwołuje się ten adres URL może zawierać łącza do instrukcji dotyczących instalacji wymagany warunek wstępny. Jeśli aplikacja nie określa adres URL pomocy technicznej dla indywidualnych wstępnie wymaganego składnika [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Wyświetla adres URL pomocy technicznej, określone w pliku manifestu wdrożenia dla aplikacji jako całości, jeśli jest zdefiniowana.

 Gdy [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], *Mage.exe*, i *MageUI.exe* wszystkie służy do generowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożeń, żadna z tych narzędzi bezpośrednio obsługuje określania adresu URL pomocy technicznej dla poszczególnych wymagania wstępne. W tym dokumencie opisano sposób modyfikowania wdrożenia manifest aplikacji i manifest wdrożenia, aby uwzględnić te obsługują adresów URL.

### <a name="specify-a-support-url-for-an-individual-prerequisite"></a>Określ adres URL pomocy technicznej dla indywidualnych wstępnie wymaganego składnika

1. Otwórz manifest aplikacji ( *.manifest* pliku) dla Twojego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji w edytorze tekstów.

2. Wstępnie wymaganego składnika systemu operacyjnego można dodać `supportUrl` atrybutu `dependentOS` elementu:

   ```xml
    <dependency>
       <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">
         <osVersionInfo>
           <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />
         </osVersionInfo>
       </dependentOS>
     </dependency>
   ```

3. Wymaganiem wstępnym dla określonej wersji środowiska uruchomieniowego języka wspólnego, Dodaj `supportUrl` atrybutu `dependentAssembly` wpis, który określa wspólne zależności środowiska uruchomieniowego języka:

   ```xml
     <dependency>
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">
         <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />
       </dependentAssembly>
     </dependency>
   ```

4. Wymaganiem wstępnym dla zestawu, który musi być wstępnie zainstalowane w globalnej pamięci podręcznej, można ustawić `supportUrl` dla `dependentAssembly` element, który określa wymagany zestaw:

   ```xml
     <dependency>
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">
         <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />
       </dependentAssembly>
     </dependency>
   ```

5. Opcjonalna. Dla aplikacji przeznaczonych dla środowiska .NET Framework 4, otwarcie manifestu wdrażania ( *.application* pliku) dla Twojego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji w edytorze tekstów.

6. Wymaganie wstępne platformy .NET Framework 4, można dodać `supportUrl` atrybutu `compatibleFrameworks` elementu:

   ```xml
   <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">
     <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />
     <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />
   </compatibleFrameworks>
   ```

7. Po ręcznie zmienione manifest aplikacji należy ponownie podpisać manifest aplikacji za pomocą certyfikatu cyfrowego, a następnie aktualizacji i ponowne podpisanie pliku manifestu wdrożenia. Użyj *Mage.exe* lub *MageUI.exe* narzędzi zestawu SDK, aby wykonać to zadanie, jak ponownie wygenerować te pliki przy użyciu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Usuwa ręczne zmiany. Aby uzyskać więcej informacji na temat korzystania z Mage.exe w celu ponownego podpisania manifestów, zobacz [jak: Ponowne podpisywanie aplikacji i manifestów wdrożenia](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="net-framework-security"></a>zabezpieczenia .NET Framework
 Adres URL pomocy technicznej nie jest wyświetlana w oknie dialogowym, jeśli aplikacja jest oznaczony do uruchamiania w trybie częściowego zaufania.

## <a name="see-also"></a>Zobacz także
- [Mage.exe (narzędzie generowania manifestu i edytowania)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [Przewodnik: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [\<compatibleFrameworks > element](../deployment/compatibleframeworks-element-clickonce-deployment.md)
- [ClickOnce i podpis Authenticode](../deployment/clickonce-and-authenticode.md)
- [Wstępnie wymagane składniki wdrażania aplikacji](../deployment/application-deployment-prerequisites.md)