---
title: Trusted Application Deployment Overview | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 34d643d3a5966ac287773b2d01d88596d51239f9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54804967"
---
# <a name="trusted-application-deployment-overview"></a>Przegląd wdrażania zaufanych aplikacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten temat zawiera omówienie sposobu wdrażania [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji, które mają podwyższony poziom uprawnień przy użyciu technologii zaufanego wdrożenia aplikacji.  
  
 Zaufane wdrożenie aplikacji, część [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] technologii wdrażania ułatwia organizacjom o dowolnym rozmiarze, aby udzielić dodatkowych uprawnień do zarządzanej aplikacji w sposób, bezpieczeństwo, bardziej bezpiecznymi bez monitowania użytkownika. Za pomocą zaufanego wdrożenia aplikacji organizacji można skonfigurować tylko na kliencie, aby wyświetlić listę zaufanych wydawców, którzy są identyfikowane za pomocą certyfikatów Authenticode. Następnie dowolne [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji podpisanej przez jedną z tych zaufanych wydawców odbiera wyższego poziomu zaufania.  
  
> [!NOTE]
>  Zaufane wdrożenie aplikacji wymaga jednorazowej konfiguracji komputera użytkownika. W zarządzanych środowiskach pulpitu tej konfiguracji można wykonać przy użyciu zasad globalnych. Jeśli to nie chcemy dla aplikacji, należy użyć podnoszenia poziomu uprawnień. Aby uzyskać więcej informacji, zobacz [zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md).  
  
## <a name="trusted-application-deployment-basics"></a>Podstawy wdrażania zaufanych aplikacji  
 W poniższej tabeli przedstawiono obiekty i role, które są zaangażowane w zaufanego wdrożenia aplikacji.  
  
|Obiekt lub roli|Opis|  
|--------------------|-----------------|  
|administrator|Jednostki organizacyjne odpowiedzialny za aktualizowanie i utrzymywanie komputerów klienckich|  
|Menedżer zaufania|Podsystem we wspólnym środowisku uruchomieniowym (języka wspólnego CLR) odpowiedzialnych za wymuszania zabezpieczeń aplikacji klienta.|  
|Wydawcy|Jednostka, która zapisuje i przechowuje ją.|  
|Narzędzia wdrażania|Jednostka, która pakietów i rozpowszechnianie aplikacji dla użytkowników.|  
|certificate|Podpisu kryptograficznego, który zawiera klucz publiczny i prywatny; ogólnie wystawiony przez urząd certyfikacji (CA), który można ciesząca jego autentyczności.|  
|Certyfikatu Authenticode|Certyfikat z osadzone metadane opisujące między innymi do zastosowań, w których można zastosować certyfikat.|  
|Urząd certyfikacji|Organizacja, która weryfikuje tożsamość wydawcy i wystawia ich certyfikaty osadzone metadane wydawcy.|  
|główny urząd certyfikacji|Urząd certyfikacji, które autoryzują innych urzędów certyfikacji do wystawiania certyfikatów.|  
|kontener klucza|Logiczne miejsce do magazynowania w programie Microsoft Windows do przechowywania certyfikatów.|  
|zaufanego wydawcy|Wydawca, którego certyfikat Authenticode został dodany do listy zaufania certyfikatów (CTL) na komputerze klienckim.|  
  
 W większych organizacji wydawcy i wdrażania są często dwa osobne jednostki:  
  
- Wydawca jest grupa, która tworzy [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji.  
  
- Wdrażania jest to grupa, zazwyczaj dział technologii informatycznych (IT) informacji, która będzie dystrybuować [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji na komputerach stacjonarnych korporacyjnym.  
  
  Należy wykonać następujące kroki, aby móc korzystać z zaufanego wdrożenia aplikacji:  
  
1.  Uzyskaj certyfikat dla wydawcy.  
  
2.  Dodaj wydawcy do magazynu zaufanych wydawców na wszystkich klientach.  
  
3.  Utwórz swoje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji.  
  
4.  Podpisać manifest wdrożenia przy użyciu certyfikatu wydawcy.  
  
5.  Publikowanie wdrażania aplikacji na komputerach klienckich.  
  
### <a name="obtain-a-certificate-for-the-publisher"></a>Uzyskaj certyfikat dla wydawcy  
 Certyfikaty cyfrowe są podstawowym składnikiem systemu zabezpieczeń i uwierzytelniania Microsoft Authenticode. Jest standardowa częścią systemu operacyjnego Windows. Wszystkie [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacje muszą być podpisane za pomocą certyfikatu cyfrowego, niezależnie od tego, czy uczestniczą w zaufanego wdrożenia aplikacji. Aby uzyskać pełne wyjaśnienie sposobu działania kodu Authenticode z [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], zobacz [ClickOnce i podpis Authenticode](../deployment/clickonce-and-authenticode.md).  
  
### <a name="add-the-publisher-to-the-trusted-publishers-store"></a>Dodać wydawcę do zaufanych Store wydawcy  
 Dla Twojej [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji w celu otrzymywania wyższego poziomu zaufania, konieczne jest dodanie certyfikatu jako zaufanego wydawcę na każdym komputerze klienckim, na którym aplikacja zostanie uruchomiona. Wykonanie tego zadania jest jednorazowej konfiguracji. Po zakończeniu, można wdrożyć jako wiele [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacje podpisane przy użyciu certyfikatu wydawcy, jak chcesz, a zostaną wszystkie działają z wysokim poziomem zaufania.  
  
 Jeżeli wdrażasz aplikację w środowisku zarządzanym pulpitu; na przykład firmowego intranetu uruchomiony system operacyjny Windows; Tworząc nową listę zaufania certyfikatów (CTL) za pomocą zasad grupy może dodawać zaufanych wydawców do magazynu klienta. Aby uzyskać więcej informacji, zobacz [utworzyć listę zaufania certyfikatów dla obiektu zasad grupy](http://go.microsoft.com/fwlink/?LinkId=102576).  
  
 Nie wymaga wdrażania aplikacji w środowisku zarządzanym pulpitu, masz następujące opcje umożliwiające dodawanie certyfikatu do magazynu zaufanego wydawcy:  
  
-   <xref:System.Security.Cryptography?displayProperty=fullName> Przestrzeni nazw.  
  
-   CertMgr.exe, który jest składnikiem programu Internet Explorer i w związku z tym istnieje w systemach Windows 98 i wszystkich nowszych wersji. Aby uzyskać więcej informacji, zobacz [Certmgr.exe (Menedżer certyfikatów narzędzie)](http://msdn.microsoft.com/library/7e953b43-1374-4bbc-814f-53ca1b6b52bb).  
  
### <a name="create-a-clickonce-application"></a>Tworzenie aplikacji ClickOnce  
 A [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacja jest [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] aplikacja kliencka w połączeniu z plików manifestu, które opisują aplikacji, a następnie podaj parametry instalacji. Można włączyć program do [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikację za pomocą **Publikuj** polecenia w pliku [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Alternatywnie można wygenerować wszystkie pliki, które są wymagane do [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia za pomocą narzędzi, które są dołączone [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]. Aby uzyskać szczegółowe instrukcje dotyczące [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrażania, zobacz [instruktażu: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
 Wdrażanie zaufanej aplikacji zależy od [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]i mogą być używane tylko z [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji.  
  
### <a name="sign-the-deployment"></a>Utwórz wdrożenie  
 Po uzyskaniu certyfikatu, musisz podać go do podpisania wdrożenia. Jeśli aplikacja jest wdrażana przy użyciu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Kreator publikacji, Kreator automatycznie wygeneruje certyfikat testowy dla Ciebie, jeśli nie podano certyfikatu samodzielnie. Można również użyć [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okno projektanta projektu, jednak podać certyfikat podany przez urząd certyfikacji.  Zobacz też [jak: Publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](http://msdn.microsoft.com/library/31kztyey\(v=vs.110\)) lub [jak: Publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](http://msdn.microsoft.com/library/31kztyey\(v=vs.110\)).  
  
> [!CAUTION]
>  Zaleca się, że aplikacja jest wdrożona za pomocą certyfikatu testu.  
  
 Możesz też zarejestrować aplikację za pomocą narzędzi Mage.exe lub MageUI.exe SDK. Aby uzyskać więcej informacji, zobacz [instruktażu: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Aby uzyskać pełną listę opcji wiersza polecenia, które dotyczą wdrażania podpisywania, zobacz [Mage.exe (Manifest Generation i narzędzia do edytowania)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
### <a name="publish-the-application"></a>Publikowanie aplikacji  
 Zaraz po zarejestrowaniu Twojego [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestów, aplikacja jest gotowa do opublikowania w lokalizacji instalacji. Lokalizacja instalacji może być serwerem sieci Web, udziału plików lub dysk lokalny. Gdy klient uzyskuje dostęp do pliku manifestu wdrożenia po raz pierwszy, musisz wybrać Menedżer zaufania czy [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji udzielono uprawnienia lub nie było uruchamiane na wyższym poziomie zaufania przez zainstalowany zaufany wydawcy. Menedżer zaufania sprawia, że ten wybór porównując certyfikat użyty do podpisania wdrożenia przy użyciu certyfikatów przechowywanych w klienta zaufanego wydawcę, przechowywania. Jeśli Menedżer zaufania znajdzie dopasowanie, aplikacja będzie działać z wysokim poziomem zaufania.  
  
## <a name="trusted-application-deployment-and-permission-elevation"></a>Wdrażanie zaufanej aplikacji i podniesienie uprawnień  
 Bieżący wydawcy nie jest zaufanym wydawcą, Menedżer zaufania użyje podnoszenia poziomu uprawnień do wykonywania zapytań użytkownika dotyczące tego, czy użytkownik chce, aby przyznać aplikacji podwyższony poziom uprawnień. Jeśli podniesienie uprawnień jest wyłączona przez administratora, jednak aplikacja nie może uzyskać uprawnienia do uruchomienia. Aplikacja nie zostanie uruchomiona, i bez powiadomienia będzie widoczny dla użytkownika. Aby uzyskać więcej informacji o podniesienie uprawnień, zobacz [zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md).  
  
## <a name="limitations-of-trusted-application-deployment"></a>Ograniczenia dotyczące wdrażania zaufanych aplikacji  
 Wdrażanie zaufanych aplikacji służy do udzielania podwyższonego zaufania do [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacje wdrożone za pośrednictwem sieci Web lub przez udział plików przedsiębiorstwa. Nie masz do użycia zaufanego wdrożenia aplikacji dla [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji rozproszonych na dysku CD, ponieważ domyślnie, te aplikacje są udzielane pełne zaufanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Mage.exe (manifestu narzędzie generowania i edytowania)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [Przewodnik: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
