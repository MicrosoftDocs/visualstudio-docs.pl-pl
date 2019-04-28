---
title: 'Przewodnik: Ręczne wdrażanie aplikacji ClickOnce | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Mage.exe, manual ClickOnce deployments
- MageUI.exe, manual ClickOnce deployments
- deploying applications [ClickOnce], manual ClickOnce deployments
- ClickOnce deployment, manually
- ClickOnce deployment, SDK tools
- manual ClickOnce deployments
- manifests [ClickOnce]
ms.assetid: ccee6551-a1b9-4ca2-8845-9c1cf4ac2560
caps.latest.revision: 51
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: baa62dc48b329cd3639c0623fccfdbe2325cf9e3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63429123"
---
# <a name="walkthrough-manually-deploying-a-clickonce-application"></a>Przewodnik: Ręczne wdrażanie aplikacji ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli nie możesz użyć programu Visual Studio, aby wdrożyć swoje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji lub jeśli trzeba korzystać z zaawansowanego wdrożenia funkcji, takich jak wdrażanie zaufanych aplikacji należy używać narzędzia wiersza polecenia Mage.exe, aby utworzyć swoje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestów. W tym przewodniku opisano sposób tworzenia [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia przy użyciu (Mage.exe) w wersji wiersza polecenia lub graficznego wersji (MageUI.exe) Manifest Generation i narzędzia do edytowania.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Ten przewodnik zawiera niektórych wymaganiach wstępnych oraz opcjach, które musisz wybrać przed kompilacją wdrożenia.  
  
- Zainstaluj Mage.exe i MageUI.exe.  
  
     Mage.exe i MageUI.exe są częścią [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]. Musisz mieć [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] zainstalowane lub wersję [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] dołączone do programu Visual Studio. Aby uzyskać więcej informacji, zobacz [zestawu Windows SDK](http://go.microsoft.com/fwlink/?LinkId=158044) w witrynie MSDN.  
  
- Podaj umożliwia wdrażanie aplikacji.  
  
     W tym przewodniku przyjęto założenie, iż aplikacji Windows, który można przystąpić do wdrażania. Ta aplikacja zostanie określone jako AppToDeploy.  
  
- Określ sposób dystrybucji wdrożenia.  
  
     Dostępne są następujące opcje dystrybucji: W sieci Web, udziału plików lub dysku CD. Aby uzyskać więcej informacji, zobacz [wdrażania i zabezpieczeń ClickOnce](../deployment/clickonce-security-and-deployment.md).  
  
- Ustal, czy aplikacja wymaga podwyższonego poziomu zaufania.  
  
     Jeśli aplikacja wymaga pełnego zaufania — na przykład pełny dostęp do systemu użytkownika — możesz użyć `-TrustLevel` Ustaw tę opcję programu Mage.exe. Jeśli użytkownik chce zdefiniować niestandardowe uprawnienia ustawione dla aplikacji, skopiuj sekcji uprawnień w Internecie lub intranecie z innego manifestu, zmodyfikuj go do własnych potrzeb, a dodać go do manifestu aplikacji za pomocą edytora tekstu lub MageUI.exe. Aby uzyskać więcej informacji, zobacz [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
- Uzyskiwanie certyfikatu Authenticode.  
  
     Utwórz wdrożenie za pomocą certyfikatu Authenticode. Można wygenerować certyfikatu testowego przy użyciu narzędzi programu Visual Studio i MageUI.exe, lub MakeCert.exe Pvk2Pfx.exe lub certyfikat można uzyskać z urząd certyfikacji (CA). Wybranie opcji użycia zaufanego wdrożenia aplikacji, należy również wykonać jednorazowe Instalacja certyfikatu na wszystkich komputerach klienckich. Aby uzyskać więcej informacji, zobacz [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
    > [!NOTE]
    > Możesz też zarejestrować wdrożenia przy użyciu certyfikatów CNG, który można uzyskać od urzędu certyfikacji.  
  
- Upewnij się, czy aplikacja nie ma manifestu za pomocą informacji o funkcji Kontrola konta użytkownika.  
  
     Należy określić, czy aplikacja zawiera manifestu kontroli konta użytkownika (UAC) informacje, takie jak `<dependentAssembly>` elementu. Aby zbadać manifest aplikacji, należy użyć narzędzi Windows Sysinternals [Sigcheck](http://go.microsoft.com/fwlink/?LinkId=158035) narzędzia.  
  
     Jeśli aplikacja zawiera manifest ze szczegółowymi informacjami kontroli konta użytkownika, należy go utworzyć ponownie bez informacji o funkcji Kontrola konta użytkownika. Projekt C# w programie Visual Studio Otwórz właściwości projektu, a następnie wybierz kartę aplikacji. W **manifestu** listy rozwijanej wybierz **tworzenie aplikacji bez manifestu**. Dla projektów języka Visual Basic w programie Visual Studio, otwórz właściwości projektu, wybierz kartę aplikacji, a następnie kliknij przycisk **ustawienia funkcji Kontrola konta użytkownika widoku**. W otwarty plik manifestu, należy usunąć wszystkie elementy w ramach pojedynczej precyzji `<asmv1:assembly>` elementu.  
  
- Ustal, czy aplikacja wymaga wymagań wstępnych na komputerze klienckim.  
  
     [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacje wdrożone za pomocą programu Visual Studio mogą obejmować instalacja warunku wstępnego program inicjujący (setup.exe) z wdrożeniem. Ten poradnik tworzy dwa manifesty wymagane dla [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia. Program inicjujący wymagań wstępnych można utworzyć za pomocą [generatebootstrapper — zadanie](../msbuild/generatebootstrapper-task.md).  
  
### <a name="to-deploy-an-application-with-the-mageexe-command-line-tool"></a>Aby wdrożyć aplikację za pomocą narzędzia wiersza polecenia Mage.exe  
  
1. Utwórz katalog, w którym będą przechowywane Twoje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] pliki wdrożenia.  
  
2. W katalogu wdrażania, który został utworzony Utwórz podkatalog wersji. Jeśli po raz pierwszy, aplikacja jest wdrażana, nazwę podkatalogu wersji **1.0.0.0**.  
  
    > [!NOTE]
    > Wersja wdrożenie może się różnić od wersji aplikacji.  
  
3. Skopiuj wszystkie pliki aplikacji do podkatalogu wersji, w tym pliki wykonywalne, zestawy, zasobów i plików danych. Jeśli to konieczne, możesz utworzyć dodatkowe podkatalogów, które zawierają dodatkowe pliki.  
  
4. Otwórz [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] lub polecenia programu Visual Studio Monituj i zmienić podkatalog wersji.  
  
5. Utwórz manifest aplikacji przy użyciu wywołania programu Mage.exe. Poniższa instrukcja umożliwia utworzenie manifest aplikacji dla kodu skompilowane do uruchamiania na procesorze Intel x86.  
  
    ```  
    mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .   
    ```  
  
    > [!NOTE]
    > Pamiętaj uwzględnić znaku kropki (.) po `-FromDirectory` opcja, która wskazuje bieżący katalog. Jeśli nie zostanie uwzględniony kropki (.), należy określić ścieżkę do plików aplikacji.  
  
6. Zaloguj się w manifeście aplikacji za pomocą certyfikatu Authenticode. Zastąp *mycert.pfx* ze ścieżką do pliku certyfikatu. Zastąp *haseł* przy użyciu hasła dla pliku certyfikatu.  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd  
    ```  
  
     Aby utworzyć manifest aplikacji przy użyciu certyfikatów CNG, należy użyć następującego polecenia. Zastąp *cngCert.pfx* ze ścieżką do pliku certyfikatu.  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
7. Przejdź do katalogu głównego katalogu wdrażania.  
  
8. Generowanie manifestu wdrażania za pomocą wywołania programu Mage.exe. Domyślnie program Mage.exe spowoduje oznaczenie Twojego [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia jako zainstalowanych aplikacji, tak że można uruchomić zarówno online i offline. Aby udostępnić aplikację, tylko wtedy, gdy użytkownik jest w trybie online, należy użyć `-Install` opcji z wartością `false`. Jeśli użytkownik korzysta z domyślnych, a użytkownicy będą instalować aplikację z witryny sieci Web lub udziału plików, upewnij się, że wartość `-ProviderUrl` opcja wskazuje lokalizację aplikacji manifestu na serwerze sieci Web lub udziału.  
  
    ```  
    mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application  
    ```  
  
9. Podpisać manifest wdrażania za pomocą certyfikatu Authenticode lub CNG.  
  
    ```  
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd  
    ```  
  
     lub  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
10. Skopiuj wszystkie pliki w katalogu wdrożenia do wdrożenia docelowego lub nośnika. Może to być folderem na witryny sieci Web lub witryny FTP, udziału plików lub dysku CD.  
  
11. Zapewnić użytkownikom za pomocą adresu URL, UNC lub nośnik fizyczny wymagane do zainstalowania aplikacji. Jeśli podasz adres URL lub UNC, należy zapewnić użytkownikom pełną ścieżkę do pliku manifestu wdrożenia. Na przykład, jeśli jest wdrażana AppToDeploy http://webserver01/ w katalogu AppToDeploy Pełna ścieżka adresu URL byłaby http://webserver01/AppToDeploy/AppToDeploy.application.  
  
### <a name="to-deploy-an-application-with-the-mageuiexe-graphical-tool"></a>Aby wdrożyć aplikację za pomocą graficznego narzędzia MageUI.exe  
  
1. Utwórz katalog, w którym będą przechowywane Twoje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] pliki wdrożenia.  
  
2. W katalogu wdrażania, który został utworzony Utwórz podkatalog wersji. Jeśli po raz pierwszy, aplikacja jest wdrażana, nazwę podkatalogu wersji **1.0.0.0**.  
  
    > [!NOTE]
    > Wersja wdrożenia prawdopodobnie różni się od wersji aplikacji.  
  
3. Skopiuj wszystkie pliki aplikacji do podkatalogu wersji, w tym pliki wykonywalne, zestawy, zasobów i plików danych. Jeśli to konieczne, możesz utworzyć dodatkowe podkatalogów, które zawierają dodatkowe pliki.  
  
4. Rozpocznij graficznego narzędzia MageUI.exe.  
  
    ```  
    MageUI.exe  
    ```  
  
5. Utwórz nowy manifest aplikacji przez wybranie **pliku**, **New**, **Manifest aplikacji** z menu.  
  
6. Domyślny **nazwa** karty, wpisz nazwę oraz numer wersji tego wdrożenia. Również określić **procesora** stworzonemu aplikacji, takich jak x86.  
  
7. Wybierz **pliki** kartę, a następnie kliknij przycisk wielokropka (**...** ) znajdujący się obok **katalogu aplikacji** pola tekstowego. Zostanie wyświetlone okno dialogowe Przeglądanie w poszukiwaniu folderu.  
  
8. Wybierz podkatalogu wersji zawierającym pliki aplikacji, a następnie kliknij przycisk **OK**.  
  
9. Jeśli zostanie wdrożony z Internet Information Services (IIS), wybierz **podczas wypełniania Dodaj rozszerzenie .deploy do każdego pliku, który nie ma** pole wyboru.  
  
10. Kliknij przycisk **wypełniania** przycisk, aby dodać pliki aplikacji do listy plików. Jeśli aplikacja zawiera więcej niż jeden plik wykonywalny, oznacz głównego pliku wykonywalnego dla tego wdrożenia, co aplikacja uruchamiania, wybierając **punktu wejścia** z **typ pliku** listy rozwijanej. (Jeśli aplikacja zawiera tylko jeden plik wykonywalny, MageUI.exe oznaczy go dla Ciebie.)  
  
11. Wybierz **wymagane są uprawnienia** kartę, a następnie wybierz poziom zaufania, należy dodać aplikację do potwierdzenia. Wartość domyślna to **FullTrust**, który będzie odpowiedni dla większości aplikacji.  
  
12. Wybierz **pliku**, **Zapisz jako** z menu. Pojawi się okno dialogowe Opcje podpisywania, prośbą do podpisania manifestu aplikacji.  
  
13. Jeśli masz certyfikat przechowywany jako plik w systemie plików, użyj **logowania przy użyciu pliku certyfikatu** opcji, a następnie wybierz certyfikat z systemu plików przy użyciu wielokropka (**...** ) przycisku. Następnie wpisz hasło do certyfikatu.  
  
     —lub—  
  
     Jeżeli certyfikat znajduje się w magazynie certyfikatów dostępny z komputera, wybierz **logowania przechowywanym certyfikatem** opcji, a następnie wybierz certyfikat z podanej listy.  
  
14. Kliknij przycisk **OK** Aby podpisać manifest aplikacji. Zostanie wyświetlone okno dialogowe Zapisz jako.  
  
15. W oknie dialogowym Zapisz jako, należy określić katalog wersji, a następnie kliknij **Zapisz**.  
  
16. Wybierz **pliku**, **New**, **manifestu wdrażania** z menu, aby utworzyć manifest wdrożenia.  
  
17. Na **nazwa** karcie, określ nazwę oraz numer wersji dla tego wdrożenia (**1.0.0.0** w tym przykładzie). Również określić **procesora** stworzonemu aplikacji, takich jak x86.  
  
18. Wybierz **opis** kartę, a następnie określ wartości dla **wydawcy** i **produktu**. (**Produktu** jest nazwa nadana do aplikacji w menu Windows Start, gdy Twoja aplikacja jest instalowana na komputerze klienckim w trybie offline.)  
  
19. Wybierz **opcje wdrażania** kartę, a następnie w **lokalizacja początkowa** tekstu określ lokalizację w manifeście aplikacji na serwerze sieci Web lub udziału. Na przykład \\\myServer\myShare\AppToDeploy.application.  
  
20. Jeśli rozszerzenie jest automatycznie usuwane dodane w poprzednim kroku, również wybrać **rozszerzenie nazwy pliku .deploy** tutaj.  
  
21. Wybierz **opcje aktualizacji** kartę, a następnie określ, jak często chcesz tej aplikacji do zaktualizowania. Jeśli aplikacja używa <xref:System.Deployment.Application.UpdateCheckInfo> pod kątem aktualizacji samego, wyczyść **ta aplikacja ma sprawdzać dostępność aktualizacji** pole wyboru.  
  
22. Wybierz **odwołania aplikacji** kartę, a następnie kliknij przycisk **wybierz manifestu** przycisku. Pojawi się okno dialogowe Otwieranie.  
  
23. Wybierz manifest aplikacji, która została utworzona wcześniej, a następnie kliknij przycisk **Otwórz**.  
  
24. Wybierz **pliku**, **Zapisz jako** z menu. Pojawi się okno dialogowe Opcje podpisywania, prośbą do podpisania manifestu wdrażania.  
  
25. Jeśli masz certyfikat przechowywany jako plik w systemie plików, użyj **logowania przy użyciu pliku certyfikatu** opcji, a następnie wybierz certyfikat z systemu plików przy użyciu wielokropka (**...** ) przycisku. Następnie wpisz hasło do certyfikatu.  
  
     —lub—  
  
     Jeżeli certyfikat znajduje się w magazynie certyfikatów dostępny z komputera, wybierz **logowania przechowywanym certyfikatem** opcji, a następnie wybierz certyfikat z podanej listy.  
  
26. Kliknij przycisk **OK** Aby podpisać manifest wdrożenia. Zostanie wyświetlone okno dialogowe Zapisz jako.  
  
27. W **Zapisz jako** okno dialogowe, Przenieś w górę jednego katalogu głównym Twojego wdrożenia, a następnie kliknij przycisk **Zapisz**.  
  
28. Skopiuj wszystkie pliki w katalogu wdrożenia do wdrożenia docelowego lub nośnika. Może to być folderem na witryny sieci Web lub witryny FTP, udziału plików lub dysku CD.  
  
29. Zapewnić użytkownikom za pomocą adresu URL, UNC lub nośnik fizyczny wymagane do zainstalowania aplikacji. Jeśli podasz adres URL lub UNC, należy zapewnić użytkownikom pełną ścieżkę manifestu wdrażania. Na przykład, jeśli jest wdrażana AppToDeploy http://webserver01/ w katalogu AppToDeploy Pełna ścieżka adresu URL byłaby http://webserver01/AppToDeploy/AppToDeploy.application.  
  
## <a name="next-steps"></a>Następne kroki  
 Gdy zajdzie potrzeba wdrożenia nowej wersji aplikacji, Utwórz nowy katalog o nazwie po nowej wersji — na przykład 1.0.0.1—and Skopiuj nowe pliki aplikacji do nowego katalogu. Następnie należy wykonać poprzednie kroki, aby utworzyć i zarejestrować nowy manifest aplikacji i aktualizacji i podpisać manifest wdrożenia. Uważaj określić tę samą wersję wyższe w obu Mage.exe `-New` i `–Update` wywołań, jako [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aktualizuje tylko nowsze wersje z najbardziej znaczących całkowitą najdalej po lewej stronie. Jeśli używasz MageUI.exe, możesz zaktualizować manifest wdrożenia, otwierając go, wybierając **odwołania aplikacji** kartę, klikając **wybierz manifestu** przycisk, a następnie wybierając aktualizację manifest aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Mage.exe (manifestu narzędzie generowania i edytowania)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (Manifest narzędzie generowania i edytowania, graficzny klient)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)   
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Manifest wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
