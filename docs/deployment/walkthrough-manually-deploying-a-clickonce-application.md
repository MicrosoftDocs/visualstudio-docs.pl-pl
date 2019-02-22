---
title: 'Przewodnik: Ręczne wdrażanie aplikacji ClickOnce | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39d482b6e2b0e2cdd9fce553a1cb11b1b27e9467
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56628107"
---
# <a name="walkthrough-manually-deploy-a-clickonce-application"></a>Przewodnik: Ręczne wdrażanie aplikacji ClickOnce
Jeśli nie możesz użyć programu Visual Studio, aby wdrożyć swoje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji lub jeśli trzeba korzystać z zaawansowanego wdrożenia funkcji, takich jak wdrażanie zaufanych aplikacji, należy użyć *Mage.exe* narzędzie wiersza polecenia, aby utworzyć swoje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestów. W tym przewodniku opisano sposób tworzenia [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia przy użyciu wiersza polecenia wersji (*Mage.exe*) lub wersji graficznego (*MageUI.exe*) generowania manifestu i Narzędzia do edycji.

## <a name="prerequisites"></a>Wymagania wstępne
 Ten przewodnik zawiera niektórych wymaganiach wstępnych oraz opcjach, które musisz wybrać przed kompilacją wdrożenia.

- Zainstaluj *Mage.exe* i *MageUI.exe*.

   *Mage.exe* i *MageUI.exe* są częścią [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Musisz mieć [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] zainstalowane lub wersję [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] dołączone do programu Visual Studio. Aby uzyskać więcej informacji, zobacz [zestawu Windows SDK](http://go.microsoft.com/fwlink/?LinkId=158044) w witrynie MSDN.

- Podaj umożliwia wdrażanie aplikacji.

   W tym przewodniku przyjęto założenie, iż aplikacji Windows, który można przystąpić do wdrażania. Ta aplikacja zostanie określone jako AppToDeploy.

- Określ sposób dystrybucji wdrożenia.

   Dostępne są następujące opcje dystrybucji: W sieci Web, udziału plików lub dysku CD. Aby uzyskać więcej informacji, zobacz [wdrażania i zabezpieczeń ClickOnce](../deployment/clickonce-security-and-deployment.md).

- Ustal, czy aplikacja wymaga podwyższonego poziomu zaufania.

   Jeśli aplikacja wymaga pełnego zaufania — na przykład pełny dostęp do systemu użytkownika — możesz użyć `-TrustLevel` opcji *Mage.exe* ustawienie. Jeśli użytkownik chce zdefiniować niestandardowe uprawnienia ustawione dla aplikacji, można skopiować sekcji uprawnień w Internecie lub intranecie z innego manifestu, zmodyfikuj go do własnych potrzeb i dodać go do manifestu aplikacji za pomocą edytora tekstów lub  *MageUI.exe*. Aby uzyskać więcej informacji, zobacz [Przegląd wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md).

- Uzyskiwanie certyfikatu Authenticode.

   Utwórz wdrożenie za pomocą certyfikatu Authenticode. Za pomocą programu Visual Studio można wygenerować certyfikat testowy *MageUI.exe*, lub *MakeCert.exe* i *Pvk2Pfx.exe* narzędzia lub uzyskać certyfikat z certyfikatu Urzędu certyfikacji. Wybranie opcji użycia zaufanego wdrożenia aplikacji, należy również wykonać jednorazowe Instalacja certyfikatu na wszystkich komputerach klienckich. Aby uzyskać więcej informacji, zobacz [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).

  > [!NOTE]
  >  Możesz też zarejestrować wdrożenia przy użyciu certyfikatów CNG, który można uzyskać od urzędu certyfikacji.

- Upewnij się, czy aplikacja nie ma manifestu za pomocą informacji o funkcji Kontrola konta użytkownika.

   Należy określić, czy aplikacja zawiera manifestu kontroli konta użytkownika (UAC) informacje, takie jak `<dependentAssembly>` elementu. Aby zbadać manifest aplikacji, należy użyć narzędzi Windows Sysinternals [Sigcheck](http://go.microsoft.com/fwlink/?LinkId=158035) narzędzia.

   Jeśli aplikacja zawiera manifest ze szczegółowymi informacjami kontroli konta użytkownika, należy go utworzyć ponownie bez informacji o funkcji Kontrola konta użytkownika. Projekt C# w programie Visual Studio Otwórz właściwości projektu, a następnie wybierz kartę aplikacji. W **manifestu** listy rozwijanej wybierz **tworzenie aplikacji bez manifestu**. Dla projektów języka Visual Basic w programie Visual Studio, otwórz właściwości projektu, wybierz kartę aplikacji, a następnie kliknij przycisk **ustawienia funkcji Kontrola konta użytkownika widoku**. W otwarty plik manifestu, należy usunąć wszystkie elementy w ramach pojedynczej precyzji `<asmv1:assembly>` elementu.

- Ustal, czy aplikacja wymaga wymagań wstępnych na komputerze klienckim.

   [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje wdrożone za pomocą programu Visual Studio może obejmować programu inicjującego instalacja warunku wstępnego (*setup.exe*) z wdrożeniem. Ten poradnik tworzy dwa manifesty wymagane dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia. Program inicjujący wymagań wstępnych można utworzyć za pomocą [generatebootstrapper — zadanie](../msbuild/generatebootstrapper-task.md).

### <a name="to-deploy-an-application-with-the-mageexe-command-line-tool"></a>Aby wdrożyć aplikację za pomocą narzędzia wiersza polecenia Mage.exe

1. Utwórz katalog, w którym będą przechowywane Twoje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pliki wdrożenia.

2. W katalogu wdrażania, który został utworzony Utwórz podkatalog wersji. Jeśli po raz pierwszy, aplikacja jest wdrażana, nazwę podkatalogu wersji **1.0.0.0**.

   > [!NOTE]
   >  Wersja wdrożenie może się różnić od wersji aplikacji.

3. Skopiuj wszystkie pliki aplikacji do podkatalogu wersji, w tym pliki wykonywalne, zestawy, zasobów i plików danych. Jeśli to konieczne, możesz utworzyć dodatkowe podkatalogów, które zawierają dodatkowe pliki.

4. Otwórz [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] lub polecenia programu Visual Studio Monituj i zmienić podkatalog wersji.

5. Tworzenie manifestu aplikacji przy użyciu wywołania do *Mage.exe*. Poniższa instrukcja umożliwia utworzenie manifest aplikacji dla kodu skompilowane do uruchamiania na procesorze Intel x86.

   ```cmd
   mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .
   ```

   > [!NOTE]
   >  Pamiętaj uwzględnić znaku kropki (.) po `-FromDirectory` opcja, która wskazuje bieżący katalog. Jeśli nie zostanie uwzględniony kropki (.), należy określić ścieżkę do plików aplikacji.

6. Zaloguj się w manifeście aplikacji za pomocą certyfikatu Authenticode. Zastąp *mycert.pfx* ze ścieżką do pliku certyfikatu. Zastąp *haseł* przy użyciu hasła dla pliku certyfikatu.

   ```cmd
   mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd
   ```

   Począwszy od zestawu SDK platformy .NET Framework 4.6.2, który jest dostarczany z programem Visual Studio i za pomocą zestawu Windows SDK, *mage.exe* podpisuje manifesty za pomocą CNG, a także za pomocą certyfikatów Authenticode. Używanie tego samego parametrów wiersza polecenia, podobnie jak w przypadku certyfikatów kodu Authenticode.

7. Przejdź do katalogu głównego katalogu wdrażania.

8. Generowanie manifestu wdrażania z wywołaniem *Mage.exe*. Domyślnie *Mage.exe* spowoduje oznaczenie Twojego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia jako zainstalowanych aplikacji, tak że można uruchomić zarówno online i offline. Aby udostępnić aplikację, tylko wtedy, gdy użytkownik jest w trybie online, należy użyć `-Install` opcji z wartością `false`. Jeśli użytkownik korzysta z domyślnych, a użytkownicy będą instalować aplikację z witryny sieci Web lub udziału plików, upewnij się, że wartość `-ProviderUrl` opcja wskazuje lokalizację aplikacji manifestu na serwerze sieci Web lub udziału.

   ```cmd
   mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application
   ```

9. Podpisać manifest wdrażania za pomocą certyfikatu Authenticode lub CNG.

    ```cmd
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd
    ```

10. Skopiuj wszystkie pliki w katalogu wdrożenia do wdrożenia docelowego lub nośnika. Może to być folderem na witryny sieci Web lub witryny FTP, udziału plików lub dysku CD.

11. Zapewnić użytkownikom za pomocą adresu URL, UNC lub nośnik fizyczny wymagane do zainstalowania aplikacji. Jeśli podasz adres URL lub UNC, należy zapewnić użytkownikom pełną ścieżkę do pliku manifestu wdrożenia. Na przykład, jeśli jest wdrażana AppToDeploy http://webserver01/ w katalogu AppToDeploy Pełna ścieżka adresu URL byłaby http://webserver01/AppToDeploy/AppToDeploy.application.

### <a name="to-deploy-an-application-with-the-mageuiexe-graphical-tool"></a>Aby wdrożyć aplikację za pomocą graficznego narzędzia MageUI.exe

1. Utwórz katalog, w którym będą przechowywane Twoje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pliki wdrożenia.

2. W katalogu wdrażania, który został utworzony Utwórz podkatalog wersji. Jeśli po raz pierwszy, aplikacja jest wdrażana, nazwę podkatalogu wersji **1.0.0.0**.

   > [!NOTE]
   >  Wersja wdrożenia prawdopodobnie różni się od wersji aplikacji.

3. Skopiuj wszystkie pliki aplikacji do podkatalogu wersji, w tym pliki wykonywalne, zestawy, zasobów i plików danych. Jeśli to konieczne, możesz utworzyć dodatkowe podkatalogów, które zawierają dodatkowe pliki.

4. Rozpocznij *MageUI.exe* narzędzie graficzne.

   ```cmd
   MageUI.exe
   ```

5. Utwórz nowy manifest aplikacji przez wybranie **pliku**, **New**, **Manifest aplikacji** z menu.

6. Domyślny **nazwa** karty, wpisz nazwę oraz numer wersji tego wdrożenia. Również określić **procesora** stworzonemu aplikacji, takich jak x86.

7. Wybierz **pliki** kartę, a następnie kliknij przycisk wielokropka (**...** ) znajdujący się obok **katalogu aplikacji** pola tekstowego. A **przeglądanie w poszukiwaniu folderu** pojawi się okno dialogowe.

8. Wybierz podkatalogu wersji zawierającym pliki aplikacji, a następnie kliknij przycisk **OK**.

9. Jeśli zostanie wdrożony z Internet Information Services (IIS), wybierz **podczas wypełniania Dodaj rozszerzenie .deploy do każdego pliku, który nie ma** pole wyboru.

10. Kliknij przycisk **wypełniania** przycisk, aby dodać pliki aplikacji do listy plików. Jeśli aplikacja zawiera więcej niż jeden plik wykonywalny, oznacz głównego pliku wykonywalnego dla tego wdrożenia, co aplikacja uruchamiania, wybierając **punktu wejścia** z **typ pliku** listy rozwijanej. (Jeśli aplikacja zawiera tylko jeden plik wykonywalny, *MageUI.exe* oznaczy go dla Ciebie.)

11. Wybierz **wymagane są uprawnienia** kartę, a następnie wybierz poziom zaufania, należy dodać aplikację do potwierdzenia. Wartość domyślna to **FullTrust**, który będzie odpowiedni dla większości aplikacji.

12. Wybierz **pliku**, **Zapisz jako** z menu. Pojawi się okno dialogowe Opcje podpisywania, prośbą do podpisania manifestu aplikacji.

13. Jeśli masz certyfikat przechowywany jako plik w systemie plików, użyj **logowania przy użyciu pliku certyfikatu** opcji, a następnie wybierz certyfikat z systemu plików przy użyciu wielokropka (**...** ) przycisku. Następnie wpisz hasło do certyfikatu.

     —lub—

     Jeżeli certyfikat znajduje się w magazynie certyfikatów dostępny z komputera, wybierz **logowania przechowywanym certyfikatem** opcji, a następnie wybierz certyfikat z podanej listy.

14. Kliknij przycisk **OK** Aby podpisać manifest aplikacji. **Zapisz jako** pojawi się okno dialogowe.

15. W **Zapisz jako** okno dialogowe, określ katalog, w wersji, a następnie kliknij przycisk **Zapisz**.

16. Wybierz **pliku**, **New**, **manifestu wdrażania** z menu, aby utworzyć manifest wdrożenia.

17. Na **nazwa** karcie, określ nazwę oraz numer wersji dla tego wdrożenia (**1.0.0.0** w tym przykładzie). Również określić **procesora** stworzonemu aplikacji, takich jak x86.

18. Wybierz **opis** kartę, a następnie określ wartości dla **wydawcy** i **produktu**. (**Produktu** jest nazwa nadana do aplikacji w menu Windows Start, gdy Twoja aplikacja jest instalowana na komputerze klienckim w trybie offline.)

19. Wybierz **opcje wdrażania** kartę, a następnie w **lokalizacja początkowa** tekstu określ lokalizację w manifeście aplikacji na serwerze sieci Web lub udziału. Na przykład  *\\\myServer\myShare\AppToDeploy.application*.

20. Jeśli dodano *.deploy* rozszerzenia w poprzednim kroku, również wybrać **rozszerzenie nazwy pliku .deploy** tutaj.

21. Wybierz **opcje aktualizacji** kartę, a następnie określ, jak często chcesz tej aplikacji do zaktualizowania. Jeśli aplikacja używa <xref:System.Deployment.Application.UpdateCheckInfo> pod kątem aktualizacji samego, wyczyść **ta aplikacja ma sprawdzać dostępność aktualizacji** pole wyboru.

22. Wybierz **odwołania aplikacji** kartę, a następnie kliknij przycisk **wybierz manifestu** przycisku. Pojawi się okno dialogowe Otwieranie.

23. Wybierz manifest aplikacji, która została utworzona wcześniej, a następnie kliknij przycisk **Otwórz**.

24. Wybierz **pliku**, **Zapisz jako** z menu. A **opcje podpisywania** pojawi się okno dialogowe prośbą do podpisania manifestu wdrażania.

25. Jeśli masz certyfikat przechowywany jako plik w systemie plików, użyj **logowania przy użyciu pliku certyfikatu** opcji, a następnie wybierz certyfikat z systemu plików przy użyciu wielokropka (**...** ) przycisku. Następnie wpisz hasło do certyfikatu.

     —lub—

     Jeżeli certyfikat znajduje się w magazynie certyfikatów dostępny z komputera, wybierz **logowania przechowywanym certyfikatem** opcji, a następnie wybierz certyfikat z podanej listy.

26. Kliknij przycisk **OK** Aby podpisać manifest wdrożenia. **Zapisz jako** pojawi się okno dialogowe.

27. W **Zapisz jako** okno dialogowe, Przenieś w górę jednego katalogu głównym Twojego wdrożenia, a następnie kliknij przycisk **Zapisz**.

28. Skopiuj wszystkie pliki w katalogu wdrożenia do wdrożenia docelowego lub nośnika. Może to być folderem na witryny sieci Web lub witryny FTP, udziału plików lub dysku CD.

29. Zapewnić użytkownikom za pomocą adresu URL, UNC lub nośnik fizyczny wymagane do zainstalowania aplikacji. Jeśli podasz adres URL lub UNC, należy zapewnić użytkownikom pełną ścieżkę manifestu wdrażania. Na przykład, jeśli jest wdrażana AppToDeploy http://webserver01/ w katalogu AppToDeploy Pełna ścieżka adresu URL byłaby http://webserver01/AppToDeploy/AppToDeploy.application.

## <a name="next-steps"></a>Następne kroki
 Gdy zajdzie potrzeba wdrożenia nowej wersji aplikacji, Utwórz nowy katalog o nazwie po nowej wersji — na przykład 1.0.0.1—and Skopiuj nowe pliki aplikacji do nowego katalogu. Następnie należy wykonać poprzednie kroki, aby utworzyć i zarejestrować nowy manifest aplikacji i aktualizacji i podpisać manifest wdrożenia. Uważaj określić tę samą wersję wyższe w obu *Mage.exe* `-New` i `-Update` wywołań, jako [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aktualizuje tylko nowsze wersje z najbardziej znaczących całkowitą najdalej po lewej stronie. Jeśli użyto *MageUI.exe*, możesz zaktualizować manifest wdrożenia, otwierając go, wybierając **odwołania aplikacji** kartę, klikając **wybierz manifestu** przycisku i następnie wybierając manifest zaktualizowaną aplikację.

## <a name="see-also"></a>Zobacz także
- [Mage.exe (narzędzie generowania manifestu i edytowania)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [MageUI.exe (narzędzie generowania i edytowania manifestu, klient z interfejsem graficznym)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Manifest wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)