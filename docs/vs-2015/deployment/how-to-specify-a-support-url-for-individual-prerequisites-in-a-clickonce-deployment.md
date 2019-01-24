---
title: 'Instrukcje: Określ adres URL pomocy technicznej dla indywidualnych wstępnie wymaganych składników wdrożenia ClickOnce | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- ClickOnce deployment, URLs
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 12d85a05e8210e292369f4c3a97fbb85dc48d821
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54772741"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Instrukcje: Określ adres URL pomocy technicznej dla indywidualnych wstępnie wymaganych składników wdrożenia ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] pewne wymagania wstępne, które muszą być dostępne na komputerze klienckim, aby sprawdzić wdrożenia [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] do uruchomienia aplikacji. Obejmują one wymaganą minimalną wersję [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], wersję systemu operacyjnego i dowolne zestawy, które muszą być wstępnie zainstalowane w globalnej pamięci podręcznej zestawów (GAC). [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], jednak nie zainstalują dowolną z tych wymagań wstępnych. Jeśli warunek wstępny nie zostanie znaleziony, po prostu zatrzymuje instalację i wyświetla okno dialogowe wyjaśniające, dlaczego instalacja nie powiodła się.  
  
 Istnieją dwie metody instalacji wymagań wstępnych. Możesz zainstalować je przy użyciu aplikacji programu inicjującego. Alternatywnie można określić adres URL pomocy technicznej dla indywidualnych wstępnie wymaganych, który jest wyświetlany użytkownikom w oknie dialogowym, jeśli wymagań wstępnych nie zostanie znaleziony. Strony odwołuje się ten adres URL może zawierać łącza do instrukcji dotyczących instalacji wymagany warunek wstępny. Jeśli aplikacja nie określa adres URL pomocy technicznej dla indywidualnych wstępnie wymaganego składnika [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Wyświetla adres URL pomocy technicznej, określone w pliku manifestu wdrożenia dla aplikacji jako całości, jeśli jest zdefiniowana.  
  
 Gdy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], Mage.exe i MageUI.exe wszystkie można wygenerować [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożeń, żadna z tych narzędzi bezpośrednio obsługuje określania adresu URL pomocy technicznej dla indywidualnych wstępnie wymaganych. W tym dokumencie opisano sposób modyfikowania wdrożenia manifest aplikacji i manifest wdrożenia, aby uwzględnić te obsługują adresów URL.  
  
### <a name="specifying-a-support-url-for-an-individual-prerequisite"></a>Określanie adresu URL pomocy technicznej dla indywidualnych wstępnie wymaganego składnika  
  
1.  Otwórz manifest aplikacji (plik .manifest) dla Twojego [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji w edytorze tekstów.  
  
2.  Wstępnie wymaganego składnika systemu operacyjnego można dodać `supportUrl` atrybutu `dependentOS` elementu:  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3.  Wymaganiem wstępnym dla określonej wersji środowiska uruchomieniowego języka wspólnego, Dodaj `supportUrl` atrybutu `dependentAssembly` wpis, który określa wspólne zależności środowiska uruchomieniowego języka:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4.  Wymaganiem wstępnym dla zestawu, który musi być wstępnie zainstalowane w globalnej pamięci podręcznej, można ustawić `supportUrl` dla `dependentAssembly` element, który określa wymagany zestaw:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5.  Opcjonalna. Dla aplikacji przeznaczonych dla środowiska .NET Framework 4, otwarcie manifestu wdrażania (pliku .application) dla Twojego [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji w edytorze tekstów.  
  
6.  Wymaganie wstępne platformy .NET Framework 4, można dodać `supportUrl` atrybutu `compatibleFrameworks` elementu:  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7.  Po ręcznie zmienione manifest aplikacji należy ponownie podpisać manifest aplikacji za pomocą certyfikatu cyfrowego, a następnie aktualizacji i ponowne podpisanie pliku manifestu wdrożenia. Należy użyć Mage.exe lub MageUI.exe SDK narzędzi do wykonywania tego zadania, jak ponownie wygenerować te pliki przy użyciu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Usuwa ręczne zmiany. Aby uzyskać więcej informacji na temat korzystania z Mage.exe w celu ponownego podpisania manifestów, zobacz [jak: Ponowne podpisywanie aplikacji i manifestów wdrożenia](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Adres URL pomocy technicznej nie jest wyświetlana w oknie dialogowym, jeśli aplikacja jest oznaczony do uruchamiania w trybie częściowego zaufania.  
  
## <a name="see-also"></a>Zobacz też  
 [Mage.exe (manifestu narzędzie generowania i edytowania)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [Przewodnik: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks> Element](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [ClickOnce i podpis Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Wstępnie wymagane składniki wdrażania aplikacji](../deployment/application-deployment-prerequisites.md)
