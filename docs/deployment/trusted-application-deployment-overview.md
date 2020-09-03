---
title: Omówienie wdrażania zaufanych aplikacji | Microsoft Docs
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b3fca6db978eefc5af751d793ad299d89688cba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72806827"
---
# <a name="trusted-application-deployment-overview"></a>Omówienie wdrażania zaufanych aplikacji
Ten temat zawiera omówienie sposobu wdrażania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, które mają podwyższony poziom uprawnień przy użyciu technologii wdrażania zaufanych aplikacji.

 Wdrożenie zaufanej aplikacji, część [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] technologii wdrażania, ułatwia organizacjom dowolnego rozmiaru przyznawanie dodatkowych uprawnień do zarządzanej aplikacji w bezpieczny, bezpieczniejszy sposób bez monitowania użytkownika. W przypadku wdrażania zaufanych aplikacji organizacja może po prostu skonfigurować komputer kliencki w taki sposób, aby miał listę zaufanych wydawców, którzy zostali określeni przy użyciu certyfikatów Authenticode. Następnie każda [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja podpisana przez jednego z tych zaufanych wydawców otrzymuje wyższy poziom zaufania.

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

- Wydawca jest grupą, która tworzy [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikację.

- Wdrożenie to grupa, zazwyczaj dział IT, który dystrybuuje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikację na komputery stacjonarne korporacyjne przedsiębiorstwa.

Aby skorzystać z zaufanego wdrożenia aplikacji, należy wykonać następujące czynności:

1. Uzyskaj certyfikat dla wydawcy.

2. Dodaj wydawcę do magazynu zaufanych wydawców na wszystkich klientach.

3. Utwórz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikację.

4. Podpisz manifest wdrożenia za pomocą certyfikatu wydawcy.

5. Opublikuj wdrożenie aplikacji na komputerach klienckich.

### <a name="obtain-a-certificate-for-the-publisher"></a>Uzyskaj certyfikat dla wydawcy
 Certyfikaty cyfrowe są głównym składnikiem systemu zabezpieczeń i uwierzytelniania Authenticode firmy Microsoft. Authenticode jest standardową częścią systemu operacyjnego Windows. Wszystkie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje muszą być podpisane przy użyciu certyfikatu cyfrowego, niezależnie od tego, czy uczestniczą w wdrożeniu zaufanej aplikacji. Aby zapoznać się z pełnym wyjaśnieniem działania technologii Authenticode z programem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , zobacz [ClickOnce i Authenticode](../deployment/clickonce-and-authenticode.md).

### <a name="add-the-publisher-to-the-trusted-publishers-store"></a>Dodawanie wydawcy do magazynu zaufanych wydawców
 Aby [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja mogła uzyskać wyższy poziom zaufania, należy dodać certyfikat jako zaufany wydawca do każdego komputera klienckiego, na którym będzie uruchamiana aplikacja. Wykonanie tego zadania jest konfiguracją jednorazową. Po zakończeniu można wdrożyć dowolną liczbę [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji podpisanych za pomocą certyfikatu wydawcy zgodnie z potrzebami, a wszystkie będą uruchamiane z wysokim zaufaniem.

 Jeśli aplikacja jest wdrażana w środowisku pulpitu zarządzanego; na przykład firmowy intranet działający w systemie operacyjnym Windows; zaufanych wydawców można dodać do magazynu klienta, tworząc nową listę zaufania certyfikatów (CTL) za pomocą zasady grupy. Aby uzyskać więcej informacji, zobacz [Tworzenie listy zaufania certyfikatów dla obiektu zasady grupy](/previous-versions/windows/it-pro/windows-server-2003/cc728449(v=ws.10)).

 Jeśli aplikacja nie jest wdrażana w środowisku zarządzanym, dostępne są następujące opcje dodawania certyfikatu do magazynu zaufanych wydawców:

- <xref:System.Security.Cryptography?displayProperty=fullName>Przestrzeń nazw.

- *CertMgr.exe*, który jest składnikiem programu Internet Explorer i w związku z tym istnieje w systemie Windows 98 i wszystkich nowszych wersjach. Aby uzyskać więcej informacji, zobacz [Certmgr.exe (narzędzie Menedżer certyfikatów)](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool).

### <a name="create-a-clickonce-application"></a>Tworzenie aplikacji ClickOnce
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Aplikacja jest aplikacją kliencką .NET Framework, która jest połączona z plikami manifestu opisującymi aplikację i parametry instalacji. Program można przekształcić w [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikację przy użyciu polecenia **Publikuj** w programie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Alternatywnie można wygenerować wszystkie pliki wymagane do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia przy użyciu narzędzi, które są dołączone do programu [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] . Aby uzyskać szczegółowe instrukcje dotyczące [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrażania, zobacz [Przewodnik: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

 Wdrożenie zaufanej aplikacji jest specyficzne dla programu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] i może być używane tylko z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacjami.

### <a name="sign-the-deployment"></a>Podpisz wdrożenie
 Po uzyskaniu certyfikatu należy go użyć do podpisania wdrożenia. Jeśli aplikacja jest wdrażana za pomocą [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Kreatora publikacji, Kreator automatycznie wygeneruje certyfikat testowy, jeśli certyfikat nie został określony samodzielnie. Można również użyć [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] okna projektanta projektu, aby dostarczyć certyfikat dostarczony przez urząd certyfikacji.  Zobacz również [instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

> [!CAUTION]
> Nie zalecamy, aby aplikacja była wdrażana z certyfikatem testowym.

 Możesz również podpisać aplikację przy użyciu narzędzi *Mage.exe* lub *MageUI.exe* SDK. Aby uzyskać więcej informacji, zobacz [Przewodnik: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Aby uzyskać pełną listę opcji wiersza polecenia związanych z podpisywaniem wdrożenia, zobacz [Mage.exe (narzędzie tworzenia i edycji manifestów)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

### <a name="publish-the-application"></a>Publikowanie aplikacji
 Po podpisaniu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestów aplikacja jest gotowa do opublikowania w lokalizacji instalacji. Lokalizacją instalacji może być serwer sieci Web, udział plików lub dysk lokalny. Gdy klient uzyskuje dostęp do manifestu wdrożenia po raz pierwszy, Menedżer zaufania musi określić, czy [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja ma uprawnienia, czy nie do uruchamiania na wyższym poziomie zaufania przez zainstalowanego zaufanego wydawcę. Menedżer zaufania dokonuje tego wyboru, porównując certyfikat używany do podpisywania wdrożenia z certyfikatami przechowywanymi w zaufanym magazynie wydawcy klienta. Jeśli Menedżer zaufania odnajdzie dopasowanie, aplikacja działa z wysokim zaufaniem.

## <a name="trusted-application-deployment-and-permission-elevation"></a>Wdrażanie zaufanej aplikacji i podniesienie uprawnień
 Jeśli bieżący Wydawca nie jest zaufanym wydawcą, Menedżer zaufania będzie używać podniesienia uprawnień, aby wysłać zapytanie do użytkownika o tym, czy chce udzielić aplikacji podniesionych uprawnień. Jeśli jednak podniesienie uprawnień zostanie wyłączone przez administratora, aplikacja nie będzie mogła uzyskać uprawnień do uruchomienia. Aplikacja nie zostanie uruchomiona, a użytkownik nie będzie mógł wyświetlać żadnych powiadomień. Aby uzyskać więcej informacji na temat podniesienia uprawnień, zobacz [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md).

## <a name="limitations-of-trusted-application-deployment"></a>Ograniczenia wdrożenia zaufanej aplikacji
 Możesz użyć wdrożenia zaufanej aplikacji, aby udzielić podwyższonego zaufania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacjom wdrożonym za pośrednictwem sieci Web lub za pośrednictwem udziału plików przedsiębiorstwa. Nie jest konieczne używanie wdrożenia zaufanej aplikacji dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji rozproszonych na dysku CD, ponieważ domyślnie te aplikacje mają przyznane pełne zaufanie.

## <a name="see-also"></a>Zobacz też
- [Mage.exe (Narzędzie tworzenia i edycji manifestów)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [Przewodnik: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
