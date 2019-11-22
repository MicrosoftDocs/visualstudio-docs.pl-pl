---
title: Omówienie wdrażania zaufanych aplikacji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- ClickOnce deployment, security
- trusted application deployment
ms.assetid: b24a1702-8fbe-45b1-87a0-9618a0708f1d
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a95392525826fcfb2595e1bac7d45ebea20317fc
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74294698"
---
# <a name="trusted-application-deployment-overview"></a>Przegląd wdrażania zaufanych aplikacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten temat zawiera omówienie sposobu wdrażania aplikacji [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], które mają podwyższony poziom uprawnień przy użyciu technologii wdrażania zaufanych aplikacji.  
  
 Wdrożenie zaufanej aplikacji, część technologii wdrażania [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], ułatwia organizacjom dowolnego rozmiaru przyznawanie dodatkowych uprawnień do zarządzanej aplikacji w bezpieczny, bezpieczniejszy sposób bez monitowania użytkownika. W przypadku wdrażania zaufanych aplikacji organizacja może po prostu skonfigurować komputer kliencki w taki sposób, aby miał listę zaufanych wydawców, którzy zostali określeni przy użyciu certyfikatów Authenticode. Następnie każda aplikacja [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] podpisana przez jednego z tych zaufanych wydawców otrzymuje wyższy poziom zaufania.  
  
> [!NOTE]
> Wdrożenie zaufanej aplikacji wymaga jednorazowej konfiguracji komputera użytkownika. W zarządzanych środowiskach klasycznych tę konfigurację można wykonać przy użyciu zasad globalnych. Jeśli nie ma tego, czego potrzebujesz w aplikacji, użyj podniesienia uprawnień. Aby uzyskać więcej informacji, zobacz [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md).  
  
## <a name="trusted-application-deployment-basics"></a>Podstawowe informacje dotyczące wdrażania aplikacji zaufanych  
 W poniższej tabeli przedstawiono obiekty i role, które są objęte wdrożeniem zaufanej aplikacji.  
  
|Obiekt lub rola|Opis|  
|--------------------|-----------------|  
|administrator|Jednostka organizacyjna odpowiedzialna za aktualizowanie i obsługiwanie komputerów klienckich|  
|Menedżer zaufania|Podsystem w środowisku uruchomieniowym języka wspólnego (CLR) odpowiedzialny za Wymuszanie zabezpieczeń aplikacji klienta.|  
|publisher|Jednostka, która zapisuje i utrzymuje aplikację.|  
|narzędzia wdrażania|Jednostka, która pakuje i dystrybuuje aplikację dla użytkowników.|  
|certyfikat|Sygnatura kryptograficzna, która składa się z klucza publicznego i prywatnego; Ogólnie wystawiony przez urząd certyfikacji (CA), który może zaręczyć za jego autentyczność.|  
|Certyfikat Authenticode|Certyfikat z osadzonymi metadanymi opisującymi, między innymi, zastosowania, dla których można zastosować certyfikat.|  
|Urząd certyfikacji|Organizacja, która weryfikuje tożsamość wydawców i wystawia certyfikaty z certyfikatem osadzonym w metadanych wydawcy.|  
|urząd główny|Urząd certyfikacji, który autoryzuje inne urzędy certyfikacji do wystawiania certyfikatów.|  
|kontener kluczy|Logiczna przestrzeń magazynowa w systemie Microsoft Windows do przechowywania certyfikatów.|  
|zaufany wydawca|Wydawca, którego certyfikat Authenticode został dodany do listy zaufania certyfikatów (CTL) na komputerze klienckim.|  
  
 W dużych organizacjach Wydawca i program wdrażania często są dwoma osobnymi jednostkami:  
  
- Wydawca jest grupą, która tworzy aplikację [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
- Wdrożenie to grupa, zazwyczaj dział IT, który dystrybuuje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji na komputery stacjonarne korporacyjne przedsiębiorstwa.  
  
  Aby skorzystać z zaufanego wdrożenia aplikacji, należy wykonać następujące czynności:  
  
1. Uzyskaj certyfikat dla wydawcy.  
  
2. Dodaj wydawcę do magazynu zaufanych wydawców na wszystkich klientach.  
  
3. Utwórz aplikację [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
4. Podpisz manifest wdrożenia za pomocą certyfikatu wydawcy.  
  
5. Opublikuj wdrożenie aplikacji na komputerach klienckich.  
  
### <a name="obtain-a-certificate-for-the-publisher"></a>Uzyskaj certyfikat dla wydawcy  
 Certyfikaty cyfrowe są głównym składnikiem systemu zabezpieczeń i uwierzytelniania Authenticode firmy Microsoft. Authenticode jest standardową częścią systemu operacyjnego Windows. Wszystkie aplikacje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] muszą być podpisane przy użyciu certyfikatu cyfrowego, niezależnie od tego, czy uczestniczą w wdrożeniu zaufanej aplikacji. Aby uzyskać pełne wyjaśnienie działania technologii Authenticode z [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], zobacz [ClickOnce i Authenticode](../deployment/clickonce-and-authenticode.md).  
  
### <a name="add-the-publisher-to-the-trusted-publishers-store"></a>Dodawanie wydawcy do magazynu zaufanych wydawców  
 Aby aplikacja [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] mogła uzyskać wyższy poziom zaufania, należy dodać certyfikat jako zaufany wydawca do każdego komputera klienckiego, na którym będzie uruchamiana aplikacja. Wykonanie tego zadania jest konfiguracją jednorazową. Po zakończeniu można wdrożyć dowolną liczbę [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji podpisanych za pomocą certyfikatu wydawcy zgodnie z potrzebami, a wszystkie będą uruchamiane z wysokim zaufaniem.  
  
 Jeśli aplikacja jest wdrażana w środowisku pulpitu zarządzanego; na przykład firmowy intranet działający w systemie operacyjnym Windows; zaufanych wydawców można dodać do magazynu klienta, tworząc nową listę zaufania certyfikatów (CTL) za pomocą zasady grupy. Aby uzyskać więcej informacji, zobacz [Tworzenie listy zaufania certyfikatów dla obiektu zasady grupy](https://go.microsoft.com/fwlink/?LinkId=102576).  
  
 Jeśli aplikacja nie jest wdrażana w środowisku zarządzanym, dostępne są następujące opcje dodawania certyfikatu do magazynu zaufanych wydawców:  
  
- Przestrzeń nazw <xref:System.Security.Cryptography?displayProperty=fullName>.  
  
- CertMgr. exe, który jest składnikiem programu Internet Explorer i w związku z tym istnieje w systemie Windows 98 i wszystkich nowszych wersjach. Aby uzyskać więcej informacji, zobacz [certmgr. exe (narzędzie Menedżer certyfikatów)](https://msdn.microsoft.com/library/7e953b43-1374-4bbc-814f-53ca1b6b52bb).  
  
### <a name="create-a-clickonce-application"></a>Tworzenie aplikacji ClickOnce  
 Aplikacja [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] to [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]a aplikacja kliencka w połączeniu z plikami manifestu opisującymi aplikację i parametry instalacji. Program można przekształcić w aplikację [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] przy użyciu polecenia **Publikuj** w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Alternatywnie można generować wszystkie pliki wymagane do wdrożenia [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] przy użyciu narzędzi, które są dołączone do [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]. Aby uzyskać szczegółowe instrukcje dotyczące wdrażania [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], zobacz [Przewodnik: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
 Wdrożenie zaufanej aplikacji jest specyficzne dla [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]i może być używane tylko z aplikacjami [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
### <a name="sign-the-deployment"></a>Podpisz wdrożenie  
 Po uzyskaniu certyfikatu należy go użyć do podpisania wdrożenia. Jeśli aplikacja jest wdrażana za pomocą Kreatora publikowania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], Kreator automatycznie wygeneruje certyfikat testowy, jeśli certyfikat nie został określony samodzielnie. Jednak można również użyć okna projektanta projektu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], aby dostarczyć certyfikat dostarczony przez urząd certyfikacji.  Zobacz również [instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](https://msdn.microsoft.com/library/31kztyey\(v=vs.110\)) lub [instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](https://msdn.microsoft.com/library/31kztyey\(v=vs.110\)).  
  
> [!CAUTION]
> Nie zalecamy, aby aplikacja była wdrażana z certyfikatem testowym.  
  
 Możesz również podpisać aplikację przy użyciu narzędzi programu Mage. exe lub MageUI. exe SDK. Aby uzyskać więcej informacji, zobacz [Przewodnik: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Aby uzyskać pełną listę opcji wiersza polecenia związanych z podpisywaniem wdrożenia, zobacz [plik Mage. exe (narzędzie tworzenia i edycji manifestów)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
### <a name="publish-the-application"></a>Publikowanie aplikacji  
 Po podpisaniu manifestów [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacja jest gotowa do opublikowania w lokalizacji instalacji. Lokalizacją instalacji może być serwer sieci Web, udział plików lub dysk lokalny. Gdy klient uzyskuje dostęp do manifestu wdrożenia po raz pierwszy, Menedżer zaufania musi określić, czy aplikacja [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ma przyznane uprawnienia, czy nie do uruchamiania na wyższym poziomie zaufania przez zainstalowanego zaufanego wydawcę. Menedżer zaufania dokonuje tego wyboru, porównując certyfikat używany do podpisywania wdrożenia z certyfikatami przechowywanymi w zaufanym magazynie wydawcy klienta. Jeśli Menedżer zaufania odnajdzie dopasowanie, aplikacja działa z wysokim zaufaniem.  
  
## <a name="trusted-application-deployment-and-permission-elevation"></a>Wdrażanie zaufanej aplikacji i podniesienie uprawnień  
 Jeśli bieżący Wydawca nie jest zaufanym wydawcą, Menedżer zaufania będzie używać podniesienia uprawnień, aby wysłać zapytanie do użytkownika o tym, czy chce udzielić aplikacji podniesionych uprawnień. Jeśli jednak podniesienie uprawnień zostanie wyłączone przez administratora, aplikacja nie będzie mogła uzyskać uprawnień do uruchomienia. Aplikacja nie zostanie uruchomiona, a użytkownik nie będzie mógł wyświetlać żadnych powiadomień. Aby uzyskać więcej informacji na temat podniesienia uprawnień, zobacz [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md).  
  
## <a name="limitations-of-trusted-application-deployment"></a>Ograniczenia wdrożenia zaufanej aplikacji  
 Możesz użyć wdrożenia zaufanej aplikacji, aby udzielić podwyższonego zaufania do [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji wdrożonych za pośrednictwem sieci Web lub udziału plików przedsiębiorstwa. Nie jest konieczne używanie wdrożenia zaufanej aplikacji na potrzeby aplikacji [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dystrybuowanych na dysku CD, ponieważ domyślnie te aplikacje mają przyznane pełne zaufanie.  
  
## <a name="see-also"></a>Zobacz też  
 Program [Mage. exe (narzędzie tworzenia i edycji manifestów)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [Przewodnik: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
