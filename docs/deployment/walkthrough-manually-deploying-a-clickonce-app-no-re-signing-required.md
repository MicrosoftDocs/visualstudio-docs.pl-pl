---
title: 'Przewodnik: Ręczne wdrażanie aplikacji ClickOnce, które nie wymagają ponownego podpisywania i zachowują informacje o znakowaniu | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- branding
- preserved branding information
- ClickOnce deployment, manually
- multiple ClickOnce deployment and branding
- ClickOnce deployment, SDK tools
- customer deployments
- manual ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, deployed by others
ms.assetid: c21822fb-d4ee-42e4-b72d-41ee9786efe5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50febcb027ec51b62bdde7ea06a7112470cdc247
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63405832"
---
# <a name="walkthrough-manually-deploy-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information"></a>Przewodnik: Ręczne wdrażanie aplikacji ClickOnce, które nie wymagają ponownego podpisywania i zachowują informacje o znakowaniu
Po utworzeniu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji i nadaj mu klientowi do publikowania i wdrażania, tradycyjnie miał odbiorcy do manifestu wdrażania aktualizacji i ponownie zaloguj się. Która nadal jest preferowaną metodą w większości przypadków, .NET Framework 3.5 pozwala na tworzenie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożeń, które mogą być wdrażane przez klientów bez konieczności ponownie wygenerować nowy manifest wdrożenia. Aby uzyskać więcej informacji, zobacz [aplikacji wdrażania technologii ClickOnce do testowania i produkcji serwerów bez ponownego podpisywania](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md).

 Po utworzeniu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji i nadać mu klientowi do publikowania i wdrażania, można użyć znakowania przez klienta lub można zachować znakowanie aplikacji. Na przykład jeśli aplikacja jest pojedynczą aplikacją własności, warto zachować znakowanie. Jeśli aplikacja jest wysoce dostosowane dla każdego klienta, możesz chcieć użyć znakowania przez klienta. .NET Framework 3.5 umożliwia zachowanie znakowanie, informacje o wydawcy i sygnatury bezpieczeństwa po zapewnieniu umożliwia wdrażanie aplikacji dla organizacji. Aby uzyskać więcej informacji, zobacz [ClickOnce tworzenie aplikacji dla innych użytkowników wdrożyć](../deployment/creating-clickonce-applications-for-others-to-deploy.md).

> [!NOTE]
> W tym instruktażu utworzysz wdrożeń ręcznie za pomocą narzędzia wiersza polecenia *Mage.exe* lub graficznego narzędzia *MageUI.exe*. Aby uzyskać więcej informacji na temat ręcznego wdrożenia, zobacz [instruktażu: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Aby wykonać kroki opisane w tym przewodniku potrzebne są następujące elementy:

- Aplikacja Windows Forms, która wszystko będzie gotowe do wdrożenia. Ta aplikacja zostanie wcześniej określano *WindowsFormsApp1*.

- Visual Studio lub Windows SDK.

### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageexe"></a>Do wdrożenia z wieloma wdrożenia i obsługę znakowania przy użyciu Mage.exe aplikacji ClickOnce

1. Otwórz wiersz polecenia programu Visual Studio lub [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] wiersz polecenia i przejdź do katalogu, w którym będą przechowywane są Twoje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] plików.

2. Utwórz katalog o nazwie po bieżąca wersja wdrożenia. Jeśli po raz pierwszy, aplikacja jest wdrażana, prawdopodobnie wybierzesz opcję **1.0.0.0**.

   > [!NOTE]
   > Wersja wdrożenie może się różnić od wersji plików aplikacji.

3. Utwórz podkatalog o nazwie **bin** i skopiuj wszystkie pliki aplikacji w tym miejscu, w tym pliki wykonywalne, zestawy, zasobów i plików danych.

4. Generuj manifest aplikacji przy użyciu wywołania programu Mage.exe.

   ```cmd
   mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"
   ```

5. Zaloguj się w manifeście aplikacji za pomocą certyfikatu cyfrowego.

   ```cmd
   mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx
   ```

6. Generowanie manifestu wdrażania z wywołaniem *Mage.exe*. Domyślnie *Mage.exe* spowoduje oznaczenie Twojego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia jako zainstalowanych aplikacji, tak że można uruchomić zarówno online i offline. Aby udostępnić aplikację, tylko wtedy, gdy użytkownik jest w trybie online, należy użyć `-i` argumentu o wartości `f`. Ponieważ ta aplikacja będzie móc korzystać z funkcji wdrażania w wielu, Wyklucz `-providerUrl` argument *Mage.exe*. (W wersjach programu .NET Framework wcześniejszych niż wersja 3.5, z wyłączeniem `-providerUrl` dla aplikacji w trybie offline spowoduje wystąpienie błędu.)

   ```cmd
   mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest
   ```

7. Zrezygnujesz z podpisania manifestu wdrażania.

8. Podaj wszystkie pliki do klientów, którzy wdroży aplikację w jego sieci.

9. W tym momencie klienta muszą podpisać manifest wdrożenia przy użyciu własnej automatycznie wygenerowany certyfikat. Na przykład, jeśli klient działa w przypadku firma o nazwie Adventure Works, on wygenerować certyfikat z podpisem własnym za pomocą *MakeCert.exe* narzędzia. Następnie użyj *Pvk2pfx.exe* narzędzie do łączenia plików utworzonych przez *MakeCert.exe* do pliku PFX, który może być przekazywany do *Mage.exe*.

    ```cmd
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx
    ```

10. Klient używa następnie ten certyfikat do podpisania manifestu wdrażania.

    ```cmd
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx
    ```

11. Klient wdraża ją do użytkowników.

### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageuiexe"></a>Do wdrożenia z wieloma wdrożenia i obsługę znakowania przy użyciu MageUI.exe aplikacji ClickOnce

1. Otwórz wiersz polecenia programu Visual Studio lub [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] wiersz polecenia i przejdź do katalogu, w którym będą przechowywane są Twoje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] plików.

2. Utwórz podkatalog o nazwie **bin** i skopiuj wszystkie pliki aplikacji w tym miejscu, w tym pliki wykonywalne, zestawy, zasobów i plików danych.

3. Tworzenie podkatalogu nazwanym tak bieżąca wersja wdrożenia. Jeśli po raz pierwszy, aplikacja jest wdrażana, prawdopodobnie wybierzesz opcję **1.0.0.0**.

   > [!NOTE]
   > Wersja wdrożenie może się różnić od wersji plików aplikacji.

4. Przenieś \\ **bin** katalog do katalogu, który został utworzony w kroku 2.

5. Uruchom narzędzie graficzne *MageUI.exe*.

   ```cmd
   MageUI.exe
   ```

6. Utwórz nowy manifest aplikacji przez wybranie **pliku**, **New**, **Manifest aplikacji** z menu.

7. Domyślny **nazwa** wprowadź nazwę i numer wersji tego wdrożenia. Ponadto należy podać wartość **wydawcy**, która będzie służyć jako nazwa folderu dla łącza skrót aplikacji w Start menu po jego wdrożeniu.

8. Wybierz **Opcje aplikacji** kartę, a następnie kliknij przycisk **Manifest aplikacji użyj uzyskać zaufania**. Spowoduje to włączenie znakowania innych firm, w tym [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji.

9. Wybierz **pliki** kartę, a następnie kliknij przycisk **Przeglądaj** znajdujący się obok **katalogu aplikacji** pola tekstowego.

10. Wybierz katalog, który zawiera pliki aplikacji, które zostały utworzone w kroku 2, a następnie kliknij przycisk **OK** okno dialogowe wyboru folderu.

11. Kliknij przycisk **wypełniania** przycisk, aby dodać pliki aplikacji do listy plików. Jeśli aplikacja zawiera więcej niż jeden plik wykonywalny, oznacz głównego pliku wykonywalnego dla tego wdrożenia, co aplikacja uruchamiania, wybierając **punktu wejścia** z **typ pliku** listy rozwijanej. (Jeśli aplikacja zawiera tylko jeden plik wykonywalny, *MageUI.exe* oznaczy go dla Ciebie.)

12. Wybierz **wymagane są uprawnienia** kartę, a następnie wybierz poziom zaufania, potrzebujesz aplikacji do potwierdzenia. Wartość domyślna to **pełne zaufanie**, który będzie odpowiedni dla większości aplikacji.

13. Wybierz **pliku**, **Zapisz** z menu i Zapisz w manifeście aplikacji. Zostanie wyświetlony monit podpisać manifest aplikacji, podczas zapisywania.

14. Jeśli masz certyfikat przechowywany jako plik w systemie plików, użyj **logowania jako plik certyfikatu** opcji, a następnie wybierz certyfikat z systemu plików, przy użyciu wielokropka (**...** ) przycisku.

     —lub—

     Jeśli certyfikat jest przechowywany w magazynie certyfikatów, które są dostępne z komputera, wybierz opcję **logowania przy użyciu opcji przechowywanego certyfikatu**, a następnie wybierz certyfikat z podanej listy.

15. Wybierz **pliku**, **New**, **manifestu wdrażania** z menu, aby utworzyć manifest wdrożenia, a następnie **nazwa** kartę, podaj Nazwa i numer wersji (**1.0.0.0** w tym przykładzie).

16. Przełącz się do **aktualizacji** kartę, a następnie określ, jak często ma tę aplikację, aby zaktualizować. Jeśli aplikacja używa [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrażania interfejsu API, aby sprawdzał dostępność aktualizacji, wyczyść pole wyboru przy opcji **ta aplikacja ma sprawdzać dostępność aktualizacji**.

17. Przełącz się do **odwołania aplikacji** kartę. Można wstępnie wypełnić wszystkie wartości na tej karcie, klikając **wybierz manifestu** przycisk i wybierając polecenie manifest aplikacji utworzony w poprzednich krokach.

18. Wybierz **Zapisz** i zapisanie pliku manifestu wdrożenia na dysku. Zostanie wyświetlony monit podpisać manifest aplikacji, podczas zapisywania. Kliknij przycisk **anulować** zapisanie manifestu bez rejestrowania jej.

19. Podaj wszystkie pliki aplikacji do klienta.

20. W tym momencie klienta muszą podpisać manifest wdrożenia przy użyciu własnej automatycznie wygenerowany certyfikat. Na przykład, jeśli klient działa w przypadku firma o nazwie Adventure Works, on wygenerować certyfikat z podpisem własnym za pomocą *MakeCert.exe* narzędzia. Następnie użyj *Pvk2pfx.exe* narzędzie do łączenia plików utworzonych przez *MakeCert.exe* do pliku PFX, który może być przekazywany do *MageUI.exe*.

    ```cmd
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx
    ```

21. Wygenerowany certyfikatem klienta teraz podpisuje manifest wdrożenia na przez otwarcie manifestu wdrażania w *MageUI.exe*, a następnie zapisz go. Gdy pojawi się okno dialogowe podpisywania, klient wybiera **logowania jako plik certyfikatu** opcji, a następnie wybierze plik PFX, został on zapisany na dysku.

22. Klient wdraża ją do użytkowników.

## <a name="see-also"></a>Zobacz także
- [Mage.exe (narzędzie generowania manifestu i edytowania)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [MageUI.exe (narzędzie generowania i edytowania manifestu, klient z interfejsem graficznym)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
- [MakeCert](/windows/desktop/SecCrypto/makecert)