---
title: Zabezpieczanie aplikacji ClickOnce | Microsoft Docs
description: Dowiedz się więcej na temat skutków ograniczeń zabezpieczeń dostępu kodu w .NET Framework, które mogą ograniczyć dostęp do kodu dla aplikacji ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 02/17/2017
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: aa698fc0ac0e46fa645ede54d6608b79dd031655
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949665"
---
# <a name="secure-clickonce-applications"></a>Zabezpieczanie aplikacji ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje podlegają ograniczeniom zabezpieczeń dostępu kodu w .NET Framework, aby pomóc w ograniczeniu dostępu do tego kodu do chronionych zasobów i operacji. Z tego powodu ważne jest, aby zrozumieć skutki zabezpieczenia dostępu kodu w celu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] odpowiedniego zapisania aplikacji. W celu ograniczenia dostępu aplikacje mogą używać pełnego zaufania lub stref częściowych, takich jak strefy Internet i Intranet.

 Ponadto technologia ClickOnce używa certyfikatów w celu weryfikowania autentyczności wydawcy aplikacji oraz podpisywania aplikacji i manifestów wdrożenia, co ma na celu zagwarantowanie, że pliki nie zostały w nieuprawniony sposób zmodyfikowane. Podpisywanie to opcjonalny krok, który ułatwia zmienianie plików aplikacji po wygenerowaniu manifestów. Jednak bez podpisanych manifestów trudno jest zagwarantować, że instalator aplikacji nie zostanie zmodyfikowany w wyniku ataku przeprowadzonego przez osobę z wewnątrz organizacji. Z tego powodu zaleca się podpisywanie aplikacji i manifestów wdrożenia, ponieważ pomaga to w zabezpieczaniu aplikacji.

## <a name="zones"></a>Strefy
 Aplikacje wdrożone za pomocą [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] technologii są ograniczone do zestawu uprawnień i akcji zdefiniowanych przez strefę zabezpieczeń. Strefy zabezpieczeń są zdefiniowane w programie Internet Explorer i są oparte na lokalizacji aplikacji. W poniższej tabeli wymieniono uprawnienia domyślne określone na podstawie lokalizacji wdrożenia:

|Lokalizacja wdrożenia|Strefa zabezpieczeń|
|-------------------------|-------------------|
|Uruchamianie z sieci Web|Strefa Internet|
|Instalacja z sieci Web|Strefa Internet|
|Instalacja z sieciowego udziału plików|Strefa Lokalny intranet|
|Instalacja z dysku CD-ROM|Pełne zaufanie|

 Uprawnienia domyślne są określane na podstawie lokalizacji, z której została wdrożona oryginalna wersja aplikacji; aktualizacje aplikacji będą dziedziczyć te uprawnienia. Jeśli aplikacja jest skonfigurowana do sprawdzania, czy w sieci Web lub lokalizacji sieciowej są dostępne aktualizacje, oryginalna instalacja może otrzymać uprawienia dla strefy Internet lub Intranet, a nie uprawnienia pełnego zaufania. Aby zapobiec monitowaniu użytkowników, administrator systemu może określić zasady wdrażania technologii ClickOnce definiujące określonego wydawcę aplikacji jako zaufane źródło. Na komputerach, na których zostaną wdrożone te zasady, uprawnienia będą udzielane automatycznie i użytkownicy nie będą monitowani. Aby uzyskać więcej informacji, zobacz [Omówienie wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md). Aby skonfigurować zaufane wdrożenie aplikacji, certyfikat można zainstalować na poziomie komputera lub przedsiębiorstwa. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).

## <a name="code-access-security-policies"></a>Zasady zabezpieczeń dostępu kodu
 Uprawnienia dla aplikacji są określane przez ustawienia [ \<trustInfo> w elemencie elementu](../deployment/trustinfo-element-clickonce-application.md) manifestu aplikacji. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] te informacje są generowane automatycznie na podstawie ustawień na stronie właściwości **zabezpieczenia** projektu. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Aplikacja otrzymuje tylko określone uprawnienia, które żąda. Na przykład w sytuacji, gdy dostęp do plików wymaga uprawnień pełnego zaufania, a aplikacja żąda uprawnienia dostępu do pliku, zostanie jej udzielone tylko uprawnienie dostępu do plików, a nie uprawnienia pełnego zaufania. Podczas tworzenia [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji należy upewnić się, że zażądasz tylko określonych uprawnień wymaganych przez aplikację. W większości przypadków można użyć stref Internet lub Lokalny intranet, aby ograniczyć aplikację do częściowego zaufania. Aby uzyskać więcej informacji, zobacz [jak to zrobić: Ustawianie strefy zabezpieczeń dla aplikacji ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md). Jeśli aplikacja wymaga uprawnień niestandardowych, można utworzyć strefę niestandardową. Aby uzyskać więcej informacji, zobacz [jak: Ustawianie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).

 Dołączenie uprawnienia, które nie wchodzi w skład domyślnego zestawu uprawnień dla strefy, z której została wdrożona aplikacja, spowoduje, że użytkownik końcowy będzie w czasie instalacji lub aktualizacji monitowany o udzielenie uprawnienia. Aby zapobiec monitowaniu użytkowników, administrator systemu może określić zasady wdrażania technologii ClickOnce definiujące określonego wydawcę aplikacji jako zaufane źródło. Na komputerach, na których zostaną wdrożone te zasady, uprawnienia będą udzielane automatycznie i użytkownicy nie będą monitowani.

 Deweloper jest odpowiedzialny za zagwarantowanie, że jego aplikacja będzie działać z odpowiednimi uprawnieniami. Jeśli aplikacja w czasie wykonywania zażąda uprawnień spoza strefy, może wystąpić wyjątek zabezpieczeń. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] umożliwia debugowanie aplikacji w docelowej strefie zabezpieczeń i zapewnia pomoc w projektowaniu bezpiecznych aplikacji. Aby uzyskać więcej informacji, zobacz [debugowanie aplikacji ClickOnce używających System. Deployment. Application](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md).

 Aby uzyskać więcej informacji o zabezpieczeniach dostępu kodu i technologii ClickOnce, zobacz [zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).

## <a name="code-signing-certificates"></a>Certyfikaty podpisywania kodu
 Aby opublikować aplikację przy użyciu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia, można podpisać aplikacje i manifesty wdrożenia dla aplikacji za pomocą pary kluczy publicznych/prywatnych. Narzędzia do podpisywania manifestu są dostępne na stronie **podpisywanie** w **projektancie projektu**. Aby uzyskać więcej informacji, zobacz [Strona podpisywania, Projektant projektu](../ide/reference/signing-page-project-designer.md).

 Po podpisaniu manifestów informacje o wydawcy określone na podstawie podpisu Authenticode będą wyświetlane użytkownikowi w oknie dialogowym uprawnień podczas instalacji, aby pokazać mu, że aplikacja pochodzi z zaufanego źródła.

 Aby uzyskać więcej informacji na temat technologii ClickOnce i certyfikatów, zobacz [ClickOnce i Authenticode](../deployment/clickonce-and-authenticode.md).

## <a name="aspnet-form-based-authentication"></a>ASP.NET uwierzytelniania opartego na formularzach
 Jeśli chcesz kontrolować, które wdrożenia mogą uzyskać dostęp dla poszczególnych użytkowników, nie należy włączać anonimowego dostępu do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji wdrożonych na serwerze sieci Web. Zamiast tego należy umożliwić użytkownikom dostęp do zainstalowanych wdrożeń na podstawie tożsamości użytkownika, używając uwierzytelniania systemu Windows.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Program nie obsługuje uwierzytelniania opartego na formularzach ASP.NET, ponieważ używa trwałych plików cookie; stanowią one zagrożenie bezpieczeństwa, ponieważ znajdują się w pamięci podręcznej programu Internet Explorer i mogą być zaatakowana. W związku z tym, Jeśli wdrażasz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje, żaden scenariusz uwierzytelniania, poza uwierzytelnianiem systemu Windows, nie jest obsługiwany.

## <a name="pass-arguments"></a>Przekazywanie argumentów
 Dodatkowe zagadnienia dotyczące zabezpieczeń występuje, jeśli trzeba przekazywać argumenty do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] umożliwia deweloperom dostarczanie ciągu zapytania do aplikacji wdrożonych za pośrednictwem sieci Web. Ciąg zapytania ma formę serii par nazwa-wartość umieszczonych na końcu adresu URL używanego do uruchamiania aplikacji:

 `http://servername.adatum.com/WindowsApp1.application?username=joeuser`

 Domyślnie argumenty ciągu zapytania są wyłączone. Aby je włączyć, atrybut `trustUrlParameters` musi być ustawiony w manifeście wdrożenia aplikacji. Tę wartość można ustawić z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i z MageUI.exe. Aby uzyskać szczegółowe instrukcje dotyczące włączania przekazywania ciągów zapytania, zobacz [How to: pobieranie informacji o ciągu zapytania w aplikacji ClickOnce w trybie online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).

 Nigdy nie należy przekazywać argumentów odebranych za pośrednictwem ciągu zapytania do bazy danych lub wiersza polecenia bez sprawdzenia, czy argumenty są bezpieczne. Argumentami niebezpiecznymi są argumenty zawierające znaki ucieczki bazy danych lub wiersza polecenia, które mogłyby umożliwić złośliwemu użytkownikowi „zmuszenie” aplikacji do wykonywania dowolnie wybranych przez niego poleceń.

> [!NOTE]
> Argumenty ciągu zapytania są jedynym sposobem przekazywania argumentów do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji podczas uruchamiania. Nie można przekazać argumentów do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji z wiersza polecenia.

## <a name="deploying-obfuscated-assemblies"></a>Wdrażanie zestawów zasłoniętych
 Program Visual Studio obejmuje bezpłatną [społeczność Dotfuscator Protection](../ide/dotfuscator/index.md), która umożliwia ochronę aplikacji ClickOnce za pomocą zaciemniania kodu i aktywnych miar ochrony.  Aby uzyskać szczegółowe informacje, zobacz [sekcję ClickOnce podręcznika użytkownika społeczności Dotfuscator](https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/advanced_clickonce.html).

## <a name="see-also"></a>Zobacz też
- [Zabezpieczenia i wdrażanie technologii ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Wybieranie strategii wdrażania technologii ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
