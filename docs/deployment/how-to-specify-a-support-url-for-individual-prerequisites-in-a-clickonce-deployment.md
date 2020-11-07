---
title: Adres URL pomocy technicznej dla wymagań wstępnych wdrożenia technologii ClickOnce
description: Dowiedz się, w jaki sposób można testować wdrożenie technologii ClickOnce pod kątem wymagań wstępnych dla aplikacji ClickOnce oraz jak działa wdrożenie z brakującymi wymaganiami wstępnymi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: af912503ddc1e87f14756a1041e9fa4d8aac505b
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350949"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Instrukcje: Określanie adresu URL pomocy technicznej dla indywidualnych wymagań wstępnych w ramach wdrożenia ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Wdrożenie może przetestować różne wymagania wstępne, które muszą być dostępne na komputerze klienckim w celu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uruchomienia aplikacji. Te zależności obejmują wymaganą minimalną wersję .NET Framework, wersję systemu operacyjnego oraz wszystkie zestawy, które muszą być wstępnie zainstalowane w globalnej pamięci podręcznej zestawów (GAC). [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]nie można jednak zainstalować żadnego z tych wymagań wstępnych; Jeśli wymaganie wstępne nie zostanie znalezione, po prostu zatrzymuje instalację i wyświetla okno dialogowe z wyjaśnieniem dlaczego instalacja nie powiodła się.

 Istnieją dwie metody instalacji wstępnie wymaganego oprogramowania. Można je zainstalować przy użyciu aplikacji programu inicjującego. Alternatywnie można określić adres URL pomocy technicznej dla indywidualnych wymagań wstępnych, który jest wyświetlany użytkownikom w oknie dialogowym, jeśli nie zostanie znaleziony warunek wstępny. Strona, do której odwołuje się ten adres URL, może zawierać linki do instrukcji dotyczących instalowania wymaganego wymagania wstępnego. Jeśli aplikacja nie określa adresu URL pomocy technicznej dla danego wymagania wstępnego, program [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wyświetla adres URL pomocy technicznej określony w manifeście wdrożenia dla aplikacji jako całości, jeśli jest zdefiniowany.

 Chociaż [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , *Mage.exe* i *MageUI.exe* mogą być używane do generowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożeń, żadne z tych narzędzi nie obsługują bezpośredniego określania adresu URL pomocy technicznej dla indywidualnych wymagań wstępnych. W tym dokumencie opisano sposób modyfikowania manifestu aplikacji i manifestu wdrażania wdrożenia w celu uwzględnienia tych adresów URL pomocy technicznej.

### <a name="specify-a-support-url-for-an-individual-prerequisite"></a>Określ adres URL pomocy technicznej dla pojedynczego wymagania wstępnego

1. Otwórz manifest aplikacji (plik *. manifest* ) dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji w edytorze tekstu.

2. W przypadku wymagań wstępnych systemu operacyjnego Dodaj `supportUrl` atrybut do `dependentOS` elementu:

   ```xml
    <dependency>
       <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">
         <osVersionInfo>
           <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />
         </osVersionInfo>
       </dependentOS>
     </dependency>
   ```

3. W przypadku wymagania wstępnego dla określonej wersji środowiska uruchomieniowego języka wspólnego Dodaj `supportUrl` atrybut do `dependentAssembly` wpisu określającego zależność aparatu plików wykonywalnych języka wspólnego:

   ```xml
     <dependency>
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">
         <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />
       </dependentAssembly>
     </dependency>
   ```

4. W przypadku wstępnie wymaganego zestawu, który musi być preinstalowany w globalnej pamięci podręcznej zestawów, należy ustawić `supportUrl` dla `dependentAssembly` elementu, który określa wymagany zestaw:

   ```xml
     <dependency>
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">
         <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />
       </dependentAssembly>
     </dependency>
   ```

5. Opcjonalny. W przypadku aplikacji przeznaczonych dla .NET Framework 4 Otwórz manifest wdrożenia (plik *aplikacji* ) dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji w edytorze tekstów.

6. W przypadku wymagania wstępnego .NET Framework 4 Dodaj `supportUrl` atrybut do `compatibleFrameworks` elementu:

   ```xml
   <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">
     <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />
     <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />
   </compatibleFrameworks>
   ```

7. Po ręcznym zmodyfikowaniu manifestu aplikacji należy ponownie podpisać manifest aplikacji przy użyciu certyfikatu cyfrowego, a następnie zaktualizować i ponownie podpisać manifest wdrożenia. Użyj narzędzi zestawu SDK *Mage.exe* lub *MageUI.exe* do wykonania tego zadania, ponieważ spowoduje to ponowne wygenerowanie tych plików przy użyciu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wymazania zmian ręcznych. Aby uzyskać więcej informacji na temat używania Mage.exe do ponownego podpisywania manifestów, zobacz [How to: ponowne podpisywanie aplikacji i manifestów wdrożenia](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="net-framework-security"></a>zabezpieczenia .NET Framework
 Adres URL pomocy technicznej nie jest wyświetlany w oknie dialogowym, jeśli aplikacja jest oznaczona do uruchamiania w częściowej relacji zaufania.

## <a name="see-also"></a>Zobacz też
- [Mage.exe (Narzędzie tworzenia i edycji manifestów)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [Przewodnik: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [\<compatibleFrameworks> postaci](../deployment/compatibleframeworks-element-clickonce-deployment.md)
- [ClickOnce i podpis Authenticode](../deployment/clickonce-and-authenticode.md)
- [Wstępnie wymagane składniki wdrażania aplikacji](../deployment/application-deployment-prerequisites.md)