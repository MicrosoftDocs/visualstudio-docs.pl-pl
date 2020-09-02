---
title: Zabezpieczanie aplikacji ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce security
- ClickOnce deployment, security
- deploying applications, ClickOnce security
ms.assetid: a05b5f2f-d1f2-471a-8096-8b11f7554265
caps.latest.revision: 47
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2a2610c1fef92bb77d150dad7972bb991b6ef4a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686010"
---
# <a name="securing-clickonce-applications"></a>Zabezpieczanie aplikacji ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacje podlegają ograniczeniom zabezpieczeń dostępu kodu w .NET Framework, aby pomóc w ograniczeniu dostępu do tego kodu do chronionych zasobów i operacji. Z tego powodu ważne jest, aby zrozumieć skutki zabezpieczenia dostępu kodu w celu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] odpowiedniego zapisania aplikacji. W celu ograniczenia dostępu aplikacje mogą używać pełnego zaufania lub stref częściowych, takich jak strefy Internet i Intranet.  
  
 Ponadto technologia ClickOnce używa certyfikatów w celu weryfikowania autentyczności wydawcy aplikacji oraz podpisywania aplikacji i manifestów wdrożenia, co ma na celu zagwarantowanie, że pliki nie zostały w nieuprawniony sposób zmodyfikowane. Podpisywanie to opcjonalny krok, który ułatwia zmienianie plików aplikacji po wygenerowaniu manifestów. Jednak bez podpisanych manifestów trudno jest zagwarantować, że instalator aplikacji nie zostanie zmodyfikowany w wyniku ataku przeprowadzonego przez osobę z wewnątrz organizacji. Z tego powodu zaleca się podpisywanie aplikacji i manifestów wdrożenia, ponieważ pomaga to w zabezpieczaniu aplikacji.  
  
## <a name="zones"></a>Strefy  
 Aplikacje wdrożone za pomocą [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] technologii są ograniczone do zestawu uprawnień i akcji zdefiniowanych przez strefę zabezpieczeń. Strefy zabezpieczeń są zdefiniowane w programie Internet Explorer i są oparte na lokalizacji aplikacji. W poniższej tabeli wymieniono uprawnienia domyślne określone na podstawie lokalizacji wdrożenia:  
  
|Lokalizacja wdrożenia|Strefa zabezpieczeń|  
|-------------------------|-------------------|  
|Uruchamianie z sieci Web|Strefa Internet|  
|Instalacja z sieci Web|Strefa Internet|  
|Instalacja z sieciowego udziału plików|Strefa Lokalny intranet|  
|Instalacja z dysku CD-ROM|Pełne zaufanie|  
  
 Uprawnienia domyślne są określane na podstawie lokalizacji, z której została wdrożona oryginalna wersja aplikacji; aktualizacje aplikacji będą dziedziczyć te uprawnienia. Jeśli aplikacja jest skonfigurowana do sprawdzania, czy w sieci Web lub lokalizacji sieciowej są dostępne aktualizacje, oryginalna instalacja może otrzymać uprawienia dla strefy Internet lub Intranet, a nie uprawnienia pełnego zaufania. Aby zapobiec monitowaniu użytkowników, administrator systemu może określić zasady wdrażania technologii ClickOnce definiujące określonego wydawcę aplikacji jako zaufane źródło. Na komputerach, na których zostaną wdrożone te zasady, uprawnienia będą udzielane automatycznie i użytkownicy nie będą monitowani. Aby uzyskać więcej informacji, zobacz [Omówienie wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md). Aby skonfigurować zaufane wdrożenie aplikacji, certyfikat można zainstalować na poziomie komputera lub przedsiębiorstwa. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).  
  
## <a name="code-access-security-policies"></a>Zasady zabezpieczeń dostępu kodu  
 Uprawnienia dla aplikacji są określane przez ustawienia [ \<trustInfo> w elemencie elementu](../deployment/trustinfo-element-clickonce-application.md) manifestu aplikacji. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] te informacje są generowane automatycznie na podstawie ustawień na stronie właściwości **zabezpieczenia** projektu. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Aplikacja otrzymuje tylko określone uprawnienia, które żąda. Na przykład w sytuacji, gdy dostęp do plików wymaga uprawnień pełnego zaufania, a aplikacja żąda uprawnienia dostępu do pliku, zostanie jej udzielone tylko uprawnienie dostępu do plików, a nie uprawnienia pełnego zaufania. Podczas tworzenia [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji należy upewnić się, że zażądasz tylko określonych uprawnień wymaganych przez aplikację. W większości przypadków można użyć stref Internet lub Lokalny intranet, aby ograniczyć aplikację do częściowego zaufania. Aby uzyskać więcej informacji, zobacz [jak to zrobić: Ustawianie strefy zabezpieczeń dla aplikacji ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md). Jeśli aplikacja wymaga uprawnień niestandardowych, można utworzyć strefę niestandardową. Aby uzyskać więcej informacji, zobacz [jak: Ustawianie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
 Dołączenie uprawnienia, które nie wchodzi w skład domyślnego zestawu uprawnień dla strefy, z której została wdrożona aplikacja, spowoduje, że użytkownik końcowy będzie w czasie instalacji lub aktualizacji monitowany o udzielenie uprawnienia. Aby zapobiec monitowaniu użytkowników, administrator systemu może określić zasady wdrażania technologii ClickOnce definiujące określonego wydawcę aplikacji jako zaufane źródło. Na komputerach, na których zostaną wdrożone te zasady, uprawnienia będą udzielane automatycznie i użytkownicy nie będą monitowani.  
  
 Deweloper jest odpowiedzialny za zagwarantowanie, że jego aplikacja będzie działać z odpowiednimi uprawnieniami. Jeśli aplikacja w czasie wykonywania zażąda uprawnień spoza strefy, może wystąpić wyjątek zabezpieczeń. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] umożliwia debugowanie aplikacji w docelowej strefie zabezpieczeń. i oferuje pomoc w projektowaniu bezpiecznych aplikacji. Aby uzyskać więcej informacji, zobacz [How to: Debug The ClickOnce Application z ograniczonymi uprawnieniami](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md).  
  
 Aby uzyskać więcej informacji o zabezpieczeniach dostępu kodu i technologii ClickOnce, zobacz [zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).  
  
## <a name="code-signing-certificates"></a>Certyfikaty podpisywania kodu  
 Aby opublikować aplikację przy użyciu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia, można podpisać aplikacje i manifesty wdrożenia dla aplikacji za pomocą pary kluczy publicznych/prywatnych. Narzędzia do podpisywania manifestu są dostępne na stronie **podpisywanie** w **projektancie projektu**. Aby uzyskać więcej informacji, zobacz [Strona podpisywania, Projektant projektu](../ide/reference/signing-page-project-designer.md). Alternatywnie można podpisać manifesty za pomocą pliku klucza podczas procesu publikowania przy użyciu Kreatora publikacji.  
  
 Po podpisaniu manifestów informacje o wydawcy określone na podstawie podpisu Authenticode będą wyświetlane użytkownikowi w oknie dialogowym uprawnień podczas instalacji, aby pokazać mu, że aplikacja pochodzi z zaufanego źródła.  
  
 Aby uzyskać więcej informacji na temat technologii ClickOnce i certyfikatów, zobacz [ClickOnce i Authenticode](../deployment/clickonce-and-authenticode.md).  
  
## <a name="aspnet-form-based-authentication"></a>Uwierzytelnianie oparte na formularzach ASP.NET  
 Jeśli chcesz kontrolować, które wdrożenia mogą uzyskać dostęp dla poszczególnych użytkowników, nie należy włączać anonimowego dostępu do [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji wdrożonych na serwerze sieci Web. Zamiast tego należy umożliwić użytkownikom dostęp do zainstalowanych wdrożeń na podstawie tożsamości użytkownika, używając uwierzytelniania systemu Windows.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Program nie obsługuje uwierzytelniania opartego na formularzach ASP.NET, ponieważ używa trwałych plików cookie; stanowią one zagrożenie bezpieczeństwa, ponieważ znajdują się w pamięci podręcznej programu Internet Explorer i mogą być zaatakowana. W związku z tym, Jeśli wdrażasz [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacje, żaden scenariusz uwierzytelniania, poza uwierzytelnianiem systemu Windows, nie jest obsługiwany.  
  
## <a name="passing-arguments"></a>Przekazywanie argumentów  
 Dodatkowe zagadnienia dotyczące zabezpieczeń występuje, jeśli trzeba przekazywać argumenty do [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] umożliwia deweloperom dostarczanie ciągu zapytania do aplikacji wdrożonych za pośrednictwem sieci Web. Ciąg zapytania ma formę serii par nazwa-wartość umieszczonych na końcu adresu URL używanego do uruchamiania aplikacji:  
  
 `http://servername.adatum.com/WindowsApp1.application?username=joeuser`  
  
 Domyślnie argumenty ciągu zapytania są wyłączone. Aby je włączyć, atrybut `trustUrlParameters` musi być ustawiony w manifeście wdrożenia aplikacji. Tę wartość można ustawić z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i z MageUI.exe. Aby uzyskać szczegółowe instrukcje dotyczące włączania przekazywania ciągów zapytania, zobacz [How to: pobieranie informacji o ciągu zapytania w aplikacji ClickOnce w trybie online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).  
  
 Nigdy nie należy przekazywać argumentów odebranych za pośrednictwem ciągu zapytania do bazy danych lub wiersza polecenia bez sprawdzenia, czy argumenty są bezpieczne. Argumentami niebezpiecznymi są argumenty zawierające znaki ucieczki bazy danych lub wiersza polecenia, które mogłyby umożliwić złośliwemu użytkownikowi „zmuszenie” aplikacji do wykonywania dowolnie wybranych przez niego poleceń.  
  
> [!NOTE]
> Argumenty ciągu zapytania są jedynym sposobem przekazywania argumentów do [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji podczas uruchamiania. Nie można przekazać argumentów do [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji z wiersza polecenia.  
  
## <a name="deploying-obfuscated-assemblies"></a>Wdrażanie zestawów zasłoniętych  
 Można zasłonić swoją aplikację, używając narzędzia Dotfuscator, aby uniemożliwić innym osobom odtworzenie kodu. Jednak funkcja zasłaniania zestawu nie jest zintegrowana ze środowiskiem IDE programu Visual Studio i procesem wdrażania technologii ClickOnce. Dlatego zasłanianie trzeba będzie wykonać poza procesem wdrażania, być może w ramach kroków wykonywanych po kompilacji. Po skompilowaniu projektu można wykonać następujące kroki ręcznie poza programem Visual Studio:  
  
1. Wykonaj zasłanianie przy użyciu narzędzia Dotfuscator.  
  
2. Użyj programu Mage.exe lub MageUI.exe, aby wygenerować manifesty technologii ClickOnce i je podpisać. Aby uzyskać więcej informacji, zobacz [Mage.exe (narzędzie tworzenia i edycji manifestów)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1) i [MageUI.exe (narzędzie tworzenia i edycji manifestów, klient graficzny)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14).  
  
3. Ręcznie opublikuj (skopiuj) pliki do lokalizacji źródła wdrożenia (serwer sieci Web, udział UNC lub dysk CD-ROM).  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo i wdrażanie technologii ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Wybieranie strategii wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
