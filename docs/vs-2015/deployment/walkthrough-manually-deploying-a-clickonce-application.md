---
title: 'Przewodnik: ręczne wdrażanie aplikacji ClickOnce | Microsoft Docs'
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
ms.openlocfilehash: 1e1099eaf8d766088612abbb399bdf004e6378e4
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74294675"
---
# <a name="walkthrough-manually-deploying-a-clickonce-application"></a>Wskazówki: ręczne wdrażanie aplikacji ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli nie możesz użyć programu Visual Studio do wdrożenia aplikacji [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] lub musisz użyć zaawansowanych funkcji wdrażania, takich jak wdrażanie aplikacji zaufanej, użyj narzędzia wiersza polecenia programu Mage. exe, aby utworzyć manifesty [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]. W tym przewodniku opisano sposób tworzenia wdrożenia [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] przy użyciu wersji wiersza polecenia (Mage. exe) lub wersji graficznej (MageUI. exe) Narzędzie tworzenia i edycji manifestów.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym instruktażu zawarto pewne wymagania wstępne i opcje, które należy wybrać przed skompilowaniem wdrożenia.  
  
- Zainstaluj program Mage. exe i MageUI. exe.  
  
     Program Mage. exe i MageUI. exe jest częścią [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]. Musisz mieć zainstalowany [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] lub wersję [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] dołączonej do programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=158044) w witrynie MSDN.  
  
- Podaj aplikację do wdrożenia.  
  
     W tym przewodniku przyjęto założenie, że masz aplikację systemu Windows, która jest gotowa do wdrożenia. Ta aplikacja będzie określana jako AppToDeploy.  
  
- Określ sposób dystrybuowania wdrożenia.  
  
     Opcje dystrybucji obejmują: sieć Web, udział plików lub dysk CD. Aby uzyskać więcej informacji, zobacz [zabezpieczenia i wdrażanie technologii ClickOnce](../deployment/clickonce-security-and-deployment.md).  
  
- Ustal, czy aplikacja wymaga podwyższonego poziomu zaufania.  
  
     Jeśli aplikacja wymaga pełnego zaufania — na przykład pełny dostęp do systemu użytkownika — możesz użyć opcji `-TrustLevel` programu Mage. exe, aby to zrobić. Jeśli chcesz zdefiniować niestandardowy zestaw uprawnień dla aplikacji, możesz skopiować sekcję uprawnienia internetowe lub intranetowe z innego manifestu, zmodyfikować ją zgodnie z potrzebami, a następnie dodać do manifestu aplikacji przy użyciu edytora tekstu lub MageUI. exe. Aby uzyskać więcej informacji, zobacz [Omówienie wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md).  
  
- Uzyskaj certyfikat Authenticode.  
  
     Należy podpisać wdrożenie przy użyciu certyfikatu Authenticode. Certyfikat testowy można wygenerować za pomocą programu Visual Studio, MageUI. exe lub MakeCert. exe i Pvk2Pfx. exe. można też uzyskać certyfikat z urzędu certyfikacji. Jeśli zdecydujesz się użyć wdrożenia zaufanej aplikacji, musisz także wykonać jednorazową instalację certyfikatu na wszystkich komputerach klienckich. Aby uzyskać więcej informacji, zobacz [Omówienie wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md).  
  
    > [!NOTE]
    > Możesz również podpisać wdrożenie z certyfikatem CNG, który można uzyskać od urzędu certyfikacji.  
  
- Upewnij się, że aplikacja nie ma manifestu z informacjami o funkcji Kontrola konta użytkownika.  
  
     Należy określić, czy aplikacja zawiera manifest z informacjami o kontroli konta użytkownika (UAC), takimi jak `<dependentAssembly>` elementu. Aby przejrzeć manifest aplikacji, można użyć narzędzia Windows Sysinternals [sigcheck](https://go.microsoft.com/fwlink/?LinkId=158035) .  
  
     Jeśli aplikacja zawiera manifest ze szczegółami funkcji Kontrola konta użytkownika, należy ją ponownie skompilować bez informacji o kontroli konta użytkownika. W przypadku C# projektu w programie Visual Studio Otwórz właściwości projektu i wybierz kartę aplikacja. Z listy rozwijanej **manifest** wybierz pozycję **Utwórz aplikację bez manifestu**. W przypadku projektu Visual Basic w programie Visual Studio Otwórz właściwości projektu, wybierz kartę aplikacja, a następnie kliknij pozycję **Wyświetl ustawienia kontroli konta użytkownika**. W otwartym pliku manifestu Usuń wszystkie elementy w ramach jednego `<asmv1:assembly>` elementu.  
  
- Ustal, czy aplikacja wymaga wymagań wstępnych na komputerze klienckim.  
  
     [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacje wdrożone z programu Visual Studio mogą obejmować program inicjujący instalacji wymagań wstępnych (Setup. exe) wraz z wdrożeniem. W tym instruktażu są tworzone dwa manifesty wymagane do wdrożenia [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]. Program inicjujący wymaganie wstępne można utworzyć przy użyciu [zadania GenerateBootstrapper —](../msbuild/generatebootstrapper-task.md).  
  
### <a name="to-deploy-an-application-with-the-mageexe-command-line-tool"></a>Aby wdrożyć aplikację za pomocą narzędzia wiersza polecenia programu Mage. exe  
  
1. Utwórz katalog, w którym będą przechowywane pliki wdrożenia [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
2. W utworzonym katalogu wdrożenia Utwórz podkatalog wersji. Jeśli aplikacja jest wdrażana po raz pierwszy, nadaj jej nazwę podkatalogu **1.0.0.0**.  
  
    > [!NOTE]
    > Wersja wdrożenia może być odrębna od wersji aplikacji.  
  
3. Skopiuj wszystkie pliki aplikacji do podkatalogu wersji, w tym plików wykonywalnych, zestawów, zasobów i plików danych. W razie potrzeby można utworzyć dodatkowe podkatalogi zawierające dodatkowe pliki.  
  
4. Otwórz wiersz polecenia [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] lub Visual Studio i przejdź do podkatalogu wersji.  
  
5. Utwórz manifest aplikacji z wywołaniem programu Mage. exe. Poniższa instrukcja tworzy manifest aplikacji dla kodu skompilowanego do uruchamiania na procesorze Intel x86.  
  
    ```  
    mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .   
    ```  
  
    > [!NOTE]
    > Upewnij się, że po opcji `-FromDirectory` zostanie uwzględniona kropka (.), która wskazuje bieżący katalog. Jeśli kropka nie zostanie uwzględniona, należy określić ścieżkę do plików aplikacji.  
  
6. Podpisz manifest aplikacji przy użyciu certyfikatu Authenticode. Zastąp plik *webcert. pfx* ścieżką do pliku certyfikatu. Zastąp ciąg *passwd* hasłem dla pliku certyfikatu.  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd  
    ```  
  
     Aby podpisać manifest aplikacji z certyfikatem CNG, należy użyć poniższego. Zastąp plik *cngCert. pfx* ścieżką do pliku certyfikatu.  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
7. Zmień na katalog główny katalogu wdrożenia.  
  
8. Wygeneruj manifest wdrożenia z wywołaniem programu Mage. exe. Domyślnie program Mage. exe oznaczy wdrożenie [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] jako zainstalowaną aplikację, aby można było uruchomić je zarówno w trybie online, jak i offline. Aby aplikacja była dostępna tylko wtedy, gdy użytkownik jest w trybie online, użyj opcji `-Install` z wartością `false`. Jeśli używasz wartości domyślnej, a użytkownicy zainstalują aplikację z witryny sieci Web lub udziału plików, upewnij się, że wartość `-ProviderUrl` wskazuje lokalizację manifestu aplikacji na serwerze sieci Web lub udziale.  
  
    ```  
    mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application  
    ```  
  
9. Podpisz manifest wdrożenia przy użyciu certyfikatu Authenticode lub CNG.  
  
    ```  
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd  
    ```  
  
     lub  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
10. Skopiuj wszystkie pliki z katalogu wdrożenia do lokalizacji docelowej lub nośnika wdrożenia. Może to być folder w witrynie sieci Web lub w witrynie FTP, udziale plików lub dysku CD-ROM.  
  
11. Zapewnij użytkownikom adresy URL, UNC lub nośniki fizyczne wymagane do zainstalowania aplikacji. Jeśli podano adres URL lub UNC, należy nadać użytkownikom pełną ścieżkę do manifestu wdrożenia. Na przykład jeśli AppToDeploy został wdrożony w http://webserver01/ w katalogu AppToDeploy, pełna ścieżka adresu URL zostanie http://webserver01/AppToDeploy/AppToDeploy.applicationa.  
  
### <a name="to-deploy-an-application-with-the-mageuiexe-graphical-tool"></a>Aby wdrożyć aplikację za pomocą narzędzia graficznego MageUI. exe  
  
1. Utwórz katalog, w którym będą przechowywane pliki wdrożenia [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
2. W utworzonym katalogu wdrożenia Utwórz podkatalog wersji. Jeśli aplikacja jest wdrażana po raz pierwszy, nadaj jej nazwę podkatalogu **1.0.0.0**.  
  
    > [!NOTE]
    > Wersja wdrożenia prawdopodobnie różni się od wersji aplikacji.  
  
3. Skopiuj wszystkie pliki aplikacji do podkatalogu wersji, w tym plików wykonywalnych, zestawów, zasobów i plików danych. W razie potrzeby można utworzyć dodatkowe podkatalogi zawierające dodatkowe pliki.  
  
4. Uruchom narzędzie graficzne MageUI. exe.  
  
    ```  
    MageUI.exe  
    ```  
  
5. Utwórz nowy manifest aplikacji, wybierając kolejno opcje **plik**, **Nowy**, **manifest aplikacji** .  
  
6. Na karcie **Nazwa** domyślna wpisz nazwę i numer wersji tego wdrożenia. Określ również **procesor** , dla którego aplikacja została skompilowana, taka jak x86.  
  
7. Wybierz kartę **pliki** , a następnie kliknij przycisk wielokropka ( **...** ) obok pola tekstowego **katalog aplikacji** . Zostanie wyświetlone okno dialogowe Przeglądanie w poszukiwaniu folderu.  
  
8. Wybierz podkatalog wersji zawierający pliki aplikacji, a następnie kliknij przycisk **OK**.  
  
9. W przypadku wdrażania z programu Internet Information Services (IIS) zaznacz pole wyboru **podczas wypełniania Dodaj rozszerzenie. deploy do dowolnego pliku, który go nie ma** .  
  
10. Kliknij przycisk **Wypełnij** , aby dodać do listy plików wszystkie pliki aplikacji. Jeśli aplikacja zawiera więcej niż jeden plik wykonywalny, Oznacz główny plik wykonywalny dla tego wdrożenia jako aplikację startową, wybierając pozycję **punkt wejścia** z listy rozwijanej **Typ pliku** . (Jeśli aplikacja zawiera tylko jeden plik wykonywalny, program MageUI. exe oznaczy go jako ty).  
  
11. Wybierz kartę **wymagane uprawnienia** i wybierz poziom zaufania, który ma być używany przez aplikację. Wartość domyślna to **FullTrust**, która będzie odpowiednia dla większości aplikacji.  
  
12. Wybierz pozycję **plik**, **Zapisz jako** z menu. Zostanie wyświetlone okno dialogowe Opcje podpisywania z monitem o podpisanie manifestu aplikacji.  
  
13. Jeśli masz certyfikat przechowywany jako plik w systemie plików, użyj opcji **Podpisz przy użyciu pliku certyfikatu** , a następnie wybierz certyfikat z systemu plików przy użyciu przycisku wielokropka ( **...** ). Następnie wpisz hasło certyfikatu.  
  
     —lub—  
  
     Jeśli certyfikat jest przechowywany w magazynie certyfikatów dostępnym z komputera, wybierz opcję **Podpisz z przechowywanym certyfikatem** i wybierz certyfikat z podanej listy.  
  
14. Kliknij przycisk **OK** , aby podpisać manifest aplikacji. Zostanie wyświetlone okno dialogowe Zapisywanie jako.  
  
15. W oknie dialogowym Zapisz jako określ katalog wersji, a następnie kliknij przycisk **Zapisz**.  
  
16. Wybierz pozycję **plik**, **Nowy**, **manifest wdrożenia** z menu, aby utworzyć manifest wdrożenia.  
  
17. Na karcie **Nazwa** Określ nazwę i numer wersji dla tego wdrożenia (**1.0.0.0** w tym przykładzie). Określ również **procesor** , dla którego aplikacja została skompilowana, taka jak x86.  
  
18. Wybierz kartę **Opis** i określ wartości dla **wydawcy** i **produktu**. (**Produkt** to nazwa nadana aplikacji w menu Start systemu Windows, gdy aplikacja jest instalowana na komputerze klienckim w celu użycia w trybie offline).  
  
19. Wybierz kartę **Opcje wdrażania** , a następnie w polu tekstowym **Lokalizacja początkowa** Określ lokalizację manifestu aplikacji na serwerze sieci Web lub udziale. Na przykład \\\myServer\myShare\AppToDeploy.application.  
  
20. Jeśli dodano rozszerzenie. deploy w poprzednim kroku, w tym miejscu należy również wybrać opcję **Użyj. Wdróż rozszerzenie nazwy pliku** .  
  
21. Wybierz kartę **Opcje aktualizacji** i określ, jak często chcesz aktualizować tę aplikację. Jeśli aplikacja używa <xref:System.Deployment.Application.UpdateCheckInfo>, aby sprawdzać dostępność aktualizacji, wyczyść pole wyboru **Ta aplikacja powinna sprawdzać dostępność aktualizacji** .  
  
22. Wybierz kartę **odwołanie do aplikacji** , a następnie kliknij przycisk **Wybierz manifest** . Zostanie wyświetlone okno dialogowe Otwórz.  
  
23. Wybierz utworzony wcześniej manifest aplikacji, a następnie kliknij przycisk **Otwórz**.  
  
24. Wybierz pozycję **plik**, **Zapisz jako** z menu. Zostanie wyświetlone okno dialogowe Opcje podpisywania z monitem o podpisanie manifestu wdrożenia.  
  
25. Jeśli masz certyfikat przechowywany jako plik w systemie plików, użyj opcji **Podpisz przy użyciu pliku certyfikatu** , a następnie wybierz certyfikat z systemu plików przy użyciu przycisku wielokropka ( **...** ). Następnie wpisz hasło certyfikatu.  
  
     —lub—  
  
     Jeśli certyfikat jest przechowywany w magazynie certyfikatów dostępnym z komputera, wybierz opcję **Podpisz z przechowywanym certyfikatem** i wybierz certyfikat z podanej listy.  
  
26. Kliknij przycisk **OK** , aby podpisać manifest wdrożenia. Zostanie wyświetlone okno dialogowe Zapisywanie jako.  
  
27. W oknie dialogowym **Zapisywanie jako** Przenieś jeden katalog do katalogu głównego wdrożenia, a następnie kliknij przycisk **Zapisz**.  
  
28. Skopiuj wszystkie pliki z katalogu wdrożenia do lokalizacji docelowej lub nośnika wdrożenia. Może to być folder w witrynie sieci Web lub w witrynie FTP, udziale plików lub dysku CD-ROM.  
  
29. Zapewnij użytkownikom adresy URL, UNC lub nośniki fizyczne wymagane do zainstalowania aplikacji. W przypadku podania adresu URL lub UNC należy nadać użytkownikom pełną ścieżkę manifestu wdrożenia. Na przykład jeśli AppToDeploy został wdrożony w http://webserver01/ w katalogu AppToDeploy, pełna ścieżka adresu URL zostanie http://webserver01/AppToDeploy/AppToDeploy.applicationa.  
  
## <a name="next-steps"></a>Następne kroki  
 Jeśli musisz wdrożyć nową wersję aplikacji, Utwórz nowy katalog o nazwie po nowej wersji — na przykład 1.0.0.1 — i skopiuj nowe pliki aplikacji do nowego katalogu. Następnie należy wykonać kroki opisane w poprzednich krokach, aby utworzyć i podpisać nowy manifest aplikacji oraz zaktualizować i podpisać manifest wdrożenia. Należy zachować ostrożność, aby określić tę samą nowszą wersję w ramach wywołań programu Mage. exe `-New` i `–Update`, ponieważ [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] tylko aktualizacje wyższej wersji z największą liczbą całkowitą z lewej strony. Jeśli użyto MageUI. exe, możesz zaktualizować manifest wdrożenia, otwierając go, wybierając kartę **odwołanie do aplikacji** , klikając przycisk **Wybierz manifest** , a następnie wybierając zaktualizowany manifest aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 Program [Mage. exe (narzędzie tworzenia i edycji manifestów)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI. exe (narzędzie tworzenia i edycji manifestów, klient graficzny)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)   
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
   [manifestu wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md)  
 [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
