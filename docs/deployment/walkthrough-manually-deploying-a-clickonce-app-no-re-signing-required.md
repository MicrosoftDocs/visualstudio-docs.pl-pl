---
title: Ręcznie Wdróż aplikację ClickOnce & zachować znakowanie
description: Dowiedz się, jak tworzyć aplikacje ClickOnce, które mają zostać wdrożone przez klientów bez generowania nowego manifestu wdrożenia i które mogą korzystać z znakowania klienta.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 29bdd080e87e8fad44c7b8943d0d017749b8c30b
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350312"
---
# <a name="walkthrough-manually-deploy-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information"></a>Przewodnik: ręczne wdrażanie aplikacji ClickOnce, która nie wymaga ponownego podpisywania i zachowuje informacje o znakowaniu
Podczas tworzenia aplikacji, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] a następnie przekazania jej klientowi do opublikowania i wdrożenia, klient tradycyjnie musiał zaktualizować manifest wdrożenia i ponownie go podpisać. Mimo że jest to metoda preferowana w większości przypadków, .NET Framework 3,5 umożliwia tworzenie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożeń, które mogą zostać wdrożone przez klientów bez konieczności ponownego generowania nowego manifestu wdrożenia. Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji ClickOnce do testowania i serwerów produkcyjnych bez ponownego podpisywania](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md).

 Gdy tworzysz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikację, a następnie przekażesz ją do klienta w celu opublikowania i wdrożenia, aplikacja może korzystać z marki klienta lub można zachować znakowanie. Jeśli na przykład aplikacja jest aplikacją jednostronną, możesz chcieć zachować znakowanie. Jeśli aplikacja jest wysoce dostosowana dla każdego klienta, warto użyć znaku marki klienta. .NET Framework 3,5 pozwala zachować oznakowanie, informacje o wydawcy i podpisie zabezpieczeń w przypadku udzielenia aplikacji do wdrożenia w organizacji. Aby uzyskać więcej informacji, zobacz [Tworzenie aplikacji ClickOnce dla innych do wdrożenia](../deployment/creating-clickonce-applications-for-others-to-deploy.md).

> [!NOTE]
> W tym instruktażu utworzysz wdrożenia ręcznie przy użyciu narzędzia wiersza polecenia *Mage.exe* lub *MageUI.exe* narzędzia graficznego. Aby uzyskać więcej informacji na temat wdrożeń ręcznych, zobacz [Przewodnik: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Aby wykonać kroki opisane w tym instruktażu, potrzebne są następujące elementy:

- Aplikacja Windows Forms, która jest gotowa do wdrożenia. Ta aplikacja będzie określana jako *WindowsFormsApp1*.

- Visual Studio lub Windows SDK.

### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageexe"></a>Aby wdrożyć aplikację ClickOnce z obsługą wielu oznakowań przy użyciu Mage.exe

1. Otwórz wiersz polecenia programu Visual Studio lub [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] wiersz polecenia i przejdź do katalogu, w którym będą przechowywane [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pliki.

2. Utwórz katalog o nazwie po bieżącej wersji wdrożenia. Jeśli aplikacja jest wdrażana po raz pierwszy, prawdopodobnie wybierz pozycję **1.0.0.0**.

   > [!NOTE]
   > Wersja wdrożenia może różnić się od wersji plików aplikacji.

3. Utwórz podkatalog o nazwie **bin** i skopiuj do niego wszystkie pliki aplikacji, w tym pliki wykonywalne, zestawy, zasoby i pliki danych.

4. Wygeneruj manifest aplikacji z wywołaniem do Mage.exe.

   ```cmd
   mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"
   ```

5. Podpisz manifest aplikacji z certyfikatem cyfrowym.

   ```cmd
   mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx
   ```

6. Wygeneruj manifest wdrożenia z wywołaniem do *Mage.exe*. Domyślnie *Mage.exe* oznacza [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenie jako zainstalowaną aplikację, aby można było uruchomić je w trybie online i offline. Aby aplikacja była dostępna tylko wtedy, gdy użytkownik jest w trybie online, użyj `-i` argumentu z wartością `f` . Ponieważ ta aplikacja będzie korzystać z funkcji wielu wdrożeń, należy wykluczyć `-providerUrl` argument do *Mage.exe*. (W wersjach .NET Framework wcześniejszych niż wersja 3,5, wykluczanie `-providerUrl` dla aplikacji w trybie offline spowoduje wystąpienie błędu).

   ```cmd
   mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest
   ```

7. Nie Podpisz manifestu wdrożenia.

8. Podaj wszystkie pliki dla klienta, które będą wdrażać aplikację w sieci.

9. W tym momencie klient musi podpisać manifest wdrożenia własnym własnym certyfikatem wygenerowanym przez siebie. Na przykład jeśli klient współpracuje z firmą o nazwie Adventure Works, może wygenerować certyfikat z podpisem własnym za pomocą narzędzia *MakeCert.exe* . Następnie użyj *Pvk2pfx.exe* narzędzia do łączenia plików utworzonych przez *MakeCert.exe* do pliku PFX, który może zostać przesłany do *Mage.exe*.

    ```cmd
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx
    ```

10. Klient następnym używa tego certyfikatu do podpisania manifestu wdrożenia.

    ```cmd
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx
    ```

11. Klient wdraża aplikację dla swoich użytkowników.

### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageuiexe"></a>Aby wdrożyć aplikację ClickOnce z obsługą wielu oznakowań przy użyciu MageUI.exe

1. Otwórz wiersz polecenia programu Visual Studio lub [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] wiersz polecenia i przejdź do katalogu, w którym będą przechowywane [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pliki.

2. Utwórz podkatalog o nazwie **bin** i skopiuj do niego wszystkie pliki aplikacji, w tym pliki wykonywalne, zestawy, zasoby i pliki danych.

3. Utwórz podkatalog o nazwie z bieżącą wersją wdrożenia. Jeśli aplikacja jest wdrażana po raz pierwszy, prawdopodobnie wybierz pozycję **1.0.0.0**.

   > [!NOTE]
   > Wersja wdrożenia może różnić się od wersji plików aplikacji.

4. Przenieś katalog \\ **bin** do katalogu utworzonego w kroku 2.

5. Uruchom narzędzie graficzne *MageUI.exe*.

   ```cmd
   MageUI.exe
   ```

6. Utwórz nowy manifest aplikacji, wybierając kolejno opcje **plik** , **Nowy** , **manifest aplikacji** .

7. Na karcie **Nazwa** domyślna wprowadź nazwę i numer wersji tego wdrożenia. Należy również podać wartość **wydawcy** , która będzie używana jako nazwa folderu dla linku skrótu aplikacji w menu Start podczas jego wdrażania.

8. Wybierz kartę **Opcje aplikacji** , a następnie kliknij pozycję **Użyj manifestu aplikacji, aby uzyskać informacje o zaufaniu**. Spowoduje to włączenie znakowania innej firmy dla tej [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji.

9. Wybierz kartę **pliki** , a następnie kliknij przycisk **Przeglądaj** obok pola tekstowego **katalog aplikacji** .

10. Wybierz katalog zawierający pliki aplikacji, które zostały utworzone w kroku 2, a następnie kliknij przycisk **OK** w oknie dialogowym Wybieranie folderu.

11. Kliknij przycisk **Wypełnij** , aby dodać do listy plików wszystkie pliki aplikacji. Jeśli aplikacja zawiera więcej niż jeden plik wykonywalny, Oznacz główny plik wykonywalny dla tego wdrożenia jako aplikację startową, wybierając pozycję **punkt wejścia** z listy rozwijanej **Typ pliku** . (Jeśli aplikacja zawiera tylko jeden plik wykonywalny, *MageUI.exe* oznaczyć ją jako użytkownika).

12. Wybierz kartę **wymagane uprawnienia** i wybierz poziom zaufania, który ma być używany przez aplikację. Wartość domyślna to **Pełna relacja zaufania** , która będzie odpowiednia dla większości aplikacji.

13. Wybierz pozycję **plik** , **Zapisz** z menu i Zapisz manifest aplikacji. Po jego zapisaniu zostanie wyświetlony monit o podpisanie manifestu aplikacji.

14. Jeśli masz certyfikat przechowywany jako plik w systemie plików, użyj opcji **Zaloguj jako certyfikat** , a następnie wybierz certyfikat z systemu plików przy użyciu przycisku wielokropka ( **...** ).

     -lub-

     Jeśli certyfikat jest przechowywany w magazynie certyfikatów, do którego można uzyskać dostęp z komputera, wybierz **opcję Podpisz z przechowywanym certyfikatem** i wybierz certyfikat z podanej listy.

15. Wybierz pozycję **plik** , **Nowy** , **manifest wdrożenia** z menu, aby utworzyć manifest wdrożenia, a następnie na karcie **Nazwa** Podaj nazwę i numer wersji ( **1.0.0.0** w tym przykładzie).

16. Przejdź do karty **Aktualizacja** i określ, jak często aplikacja ma być aktualizowana. Jeśli aplikacja używa [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] interfejsu API wdrażania do sprawdzenia, czy są aktualizacje, wyczyść pole wyboru etykieta **Ta aplikacja powinna sprawdzać dostępność aktualizacji**.

17. Przejdź do karty **odwołanie do aplikacji** . Możesz wstępnie wypełnić wszystkie wartości na tej karcie, klikając przycisk **Wybierz manifest** i wybierając manifest aplikacji utworzony w poprzednich krokach.

18. Wybierz pozycję **Zapisz** i Zapisz manifest wdrożenia na dysku. Po jego zapisaniu zostanie wyświetlony monit o podpisanie manifestu aplikacji. Kliknij przycisk **Anuluj** , aby zapisać manifest bez podpisywania.

19. Podaj do klienta wszystkie pliki aplikacji.

20. W tym momencie klient musi podpisać manifest wdrożenia własnym własnym certyfikatem wygenerowanym przez siebie. Na przykład jeśli klient współpracuje z firmą o nazwie Adventure Works, może wygenerować certyfikat z podpisem własnym za pomocą narzędzia *MakeCert.exe* . Następnie użyj *Pvk2pfx.exe* narzędzia do łączenia plików utworzonych przez *MakeCert.exe* do pliku PFX, który może zostać przesłany do *MageUI.exe*.

    ```cmd
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx
    ```

21. Po wygenerowaniu certyfikatu klient jest teraz podpisem manifestu wdrożenia, otwierając manifest wdrożenia w *MageUI.exe* , a następnie zapisując go. Gdy zostanie wyświetlone okno dialogowe podpisywania, klient wybierze opcję **Podpisz jako plik certyfikatu** i wybierze plik PFX zapisany na dysku.

22. Klient wdraża aplikację dla swoich użytkowników.

## <a name="see-also"></a>Zobacz też
- [Mage.exe (Narzędzie tworzenia i edycji manifestów)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [MageUI.exe (Narzędzie tworzenia i edycji manifestów, klient graficzny)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
- [MakeCert](/windows/desktop/SecCrypto/makecert)
