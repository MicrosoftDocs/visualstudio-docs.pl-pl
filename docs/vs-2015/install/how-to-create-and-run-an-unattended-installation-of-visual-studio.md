---
title: 'Instrukcje: Tworzenie i uruchamianie instalacji nienadzorowanej | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- installing Visual Studio, unattended
- unattended installation, Visual Studio
ms.assetid: 3867b5dc-ed34-4ee2-be32-a42e7e320517
caps.latest.revision: 44
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 26e059d4fdc8eadd422924dd6bbda6f7c945ccfb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64833478"
---
# <a name="how-to-create-and-run-an-unattended-installation-of-visual-studio"></a>Porady: tworzenie i uruchamianie nienadzorowanej instalacji programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz uruchomić aplikację instalacji programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jako nienadzorowaną (czyli dostosowaną dyskretnie) instalację za pośrednictwem intranetu, a nie z nośników, takich jak dyski DVD. W tym temacie opisano, jak przygotować się [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] do tego typu instalacji z udziału sieciowego.

## <a name="creating-a-network-image"></a>Tworzenie obrazu sieciowego
 Najpierw Utwórz obraz sieciowy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nośnika.

#### <a name="to-create-a-network-image"></a>Aby utworzyć obraz sieciowy

1. Utwórz folder na serwerze (na przykład *dysk*: \IDEinstall \\ ).

2. Pobierz instalatora z programu [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015), a następnie uruchom plik *Product*. exe/layout *Drive*: \IDEinstall\

3. Udostępnij folder IDEinstall w sieci, a następnie ustaw odpowiednie ustawienia zabezpieczeń.

     Ścieżka sieciowa aplikacji instalacyjnej programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] przypomina \\ \\ \IDEinstall *servername*. \\ *Product*exe.

    > [!NOTE]
    > Instalacja może zakończyć się niepowodzeniem, jeśli ścieżka i nazwa pliku są dłuższe niż 260 znaków. Maksymalna długość ścieżki w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] to 221 znaków.  Nazwa ścieżki lokalnej nie powinna przekraczać 70 znaków, a nazwa ścieżki sieciowej nie powinna przekraczać 39 znaków.

     Instalacja może również zakończyć się niepowodzeniem, jeśli nazwy folderów w ścieżce obejmują spacje osadzone (na przykład " \\ \\ *servername*\IDE Install" lub \\ \\ *servername*\Visual Studio \\ ).

## <a name="deploying-visual-studio-in-unattended-mode"></a>Wdrażanie programu Visual Studio w trybie nienadzorowanym
 Aby wdrożyć [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] w trybie nienadzorowanym, należy zmodyfikować plik AdminDeployment.xml. W tym celu należy najpierw utworzyć plik AdminDeployment.xml przy użyciu `/CreateAdminFile` *\<file location>* parametru wiersza polecenia. Następnie możesz użyć tego pliku, aby wypchnąć wdrożenie programu Visual Studio do sieci lub ściągnąć je do instalacji, jeśli umieścisz ten plik na *dysku*: \IDEinstall\packages. Plik AdminDeployment.xml nie jest unikatowy dla systemu operacyjnego, architektury, wersji programu Visual Studio lub języka systemu operacyjnego.

> [!CAUTION]
> Czasami elementy wymienione w pliku AdminDeployment.xml nie są zainstalowane. Aby rozwiązać ten problem, umieść elementy oznaczone jako "selected =" yes "" na **końcu** pliku AdminDeployment.xml.
>
> Jeśli nie chcesz instalować opcjonalnych zależności elementu, należy najpierw zaznaczyć element nadrzędny, a następnie usunąć zaznaczenie opcjonalnych zależności po elemencie nadrzędnym, jak pokazano na poniższym zrzucie ekranu:
>
> ![Elementy instalacyjne na końcu pliku AdminDeployment.xml](../install/media/vs2015-install-endoffileadmindeploy.PNG "vs2015_Install_EndOfFileAdminDeploy")
>
> Innym sposobem, aby to zrobić, można po prostu pominąć opcjonalne elementy podrzędne elementu nadrzędnego — innymi słowy, nie uwzględniać żadnych elementów "selected =" No "", ale nadal trzeba umieścić wszystkie elementy "selected =" yes "na końcu pliku AdminDeployment.xml.

> [!IMPORTANT]
> Podczas instalacji komputer może zostać automatycznie ponownie uruchomiony jeden lub więcej razy. Po ponownym uruchomieniu programu należy zalogować się ponownie przy użyciu tego samego konta użytkownika, za pomocą którego zalogowano się w celu przeprowadzenia instalacji przed ponownym uruchomieniem komputera. Przed uruchomieniem instalacji nienadzorowanej można uniknąć automatycznego ponownego uruchamiania przez zainstalowanie składników wymaganych wstępnie. Aby uzyskać więcej informacji, zobacz sekcję zatytułowaną "unikanie ponownego uruchamiania podczas instalacji" w [podręczniku administratora programu Visual Studio](../install/visual-studio-administrator-guide.md).

 Schemat pliku AdminDeployment zawiera następujące elementy:

|Element|Atrybut|Wartości|Opis|
|-------------|---------------|------------|-----------------|
|BundleCustomizations|TargetDir|*Ścieżka*|Zachowuje się tak samo jak zastąpienie ścieżki w interfejsie użytkownika aplikacji instalacji. Ten element jest ignorowany, jeśli program Visual Studio jest już zainstalowany.|
|BundleCustomizations|NoWeb|tak&#124;domyślne|Jeśli wartość tego elementu to tak, aplikacja instalacyjna nigdy nie próbuje przejść do sieci Web podczas działania Instalatora.|
|SelectableItemCustomization|Ukryty|Tak&#124;nie|Jeśli wartość tego elementu to tak, ukrywa element, który można wybrać w drzewie dostosowywania.|
|SelectableItemCustomization|Wybrane|Tak&#124;nie|Zaznacza lub czyści element wybrany w drzewie dostosowywania.|
|BundleCustomizations|Źródło danych|Ścieżka|Lokalizacja źródła danych, którego użytkownik chce użyć.  To źródło danych jest używane do kolejnych operacji modyfikacji na maszynie (domyślnie "domyślnie").|
|BundleCustomizations|SuppressRefreshPrompt|tak&#124;domyślne|Uniemożliwi użytkownikowi monitowanie o odświeżenie Instalatora w przypadku, gdy jest dostępny nowszy.|
|BundleCustomizations|Norefresh|tak&#124;domyślne|Nie można odświeżyć Instalatora, jeśli jest dostępny nowszy.|
|BundleCustomizations|NoCacheOnlyMode|tak&#124;domyślne|Uniemożliwia wstępne wypełnianie pamięci podręcznej pakietu.|

> [!WARNING]
> Aplikacja instalacji będzie odnosił się do wybranego stanu SelectableItem, nawet jeśli jest ukryta. Na przykład, jeśli chcesz zawsze zainstalować element, który można wybrać, możesz oznaczyć go jako ukryty i wybrany.

#### <a name="to-create-an-unattended-installation-of-visual-studio"></a>Aby utworzyć nienadzorowaną instalację programu Visual Studio

1. W polu *dysk*:\IDEinstall\AdminDeployment.xml plik Zmień wartość atrybutu noweb elementu BundleCustomizations z "default" na "yes", jak pokazano na poniższym przykładzie:

     Zmień `<BundleCustomizations TargetDir="default" NoWeb="default"/>` na `<BundleCustomizations TargetDir="default" NoWeb="yes"/>`

2. Zmień atrybut SelectableItemCustomization w zależności od potrzeb składników opcjonalnych, a następnie Zapisz plik.

## <a name="running-unattended-setup"></a>Uruchamianie instalacji nienadzorowanej
 Instalację nienadzorowaną można uruchomić przez automatyczne uruchomienie aplikacji instalacyjnej programu Visual Studio na komputerach klienckich lub umożliwienie użytkownikom uruchamiania aplikacji przy użyciu zdefiniowanych ustawień.

#### <a name="to-run-an-unattended-installation-on-a-client-computer"></a>Aby uruchomić instalację nienadzorowaną na komputerze klienckim

- Otwórz menu **Start** , wybierz polecenie **Uruchom**, a następnie wprowadź \\ \\ *nazwa_serwera*\IDEinstall\ vs_*Product*. exe parametrem/adminfile. *PathOfTheAdmindeployment.xml*<em>AdditionalParametersAsNeeded</em> plików

   Na przykład można określić następujący wiersz polecenia: `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\ IDEinstall\AdminDeployment.xml /quiet /norestart`

#### <a name="to-enable-clients-to-manually-install-visual-studio-with-pre-defined-settings"></a>Aby umożliwić klientom ręczne instalowanie programu Visual Studio ze wstępnie zdefiniowanymi ustawieniami

1. Skopiuj dostosowany plik AdminDeployment.xml do udziału sieciowego, który jest tylko do odczytu (na przykład \\ \\ *nazwa_serwera*\IDEinstall\packages\AdminDeployment.xml).

2. Zezwól użytkownikom na instalowanie z tego udziału.

## <a name="maintaining-an-installation"></a>Utrzymywanie instalacji
 Jeśli otworzysz **Panel sterowania** i ponownie uruchomisz aplikację instalacji, możesz zmodyfikować funkcje programu Visual Studio, odinstalować Języki programowania i naprawić lub odinstalować program Visual Studio.

> [!NOTE]
> Musisz mieć poświadczenia administracyjne na komputerze lokalnym, aby można było korzystać z trybu konserwacji.

#### <a name="to-maintain-an-installation-on-a-client-computer"></a>Aby zachować instalację na komputerze klienckim

- Otwórz **Panel sterowania**, a następnie wybierz **aplet Programy i funkcje**.

- Wybierz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pozycję, a następnie wybierz pozycję **Zmień**.

#### <a name="to-change-admindeployment-settings-on-a-client-computer-after-visual-studio-has-been-installed"></a>Aby zmienić ustawienia AdminDeployment na komputerze klienckim po zainstalowaniu programu Visual Studio

1. Zaktualizuj AdminDeployment.xml zgodnie z wymaganiami.

2. Otwórz menu **Start** , a następnie wybierz polecenie **Uruchom**.

3. Wprowadź następujący tekst: \\ \\ *servername*\IDEinstall\ vs_*Product*. exe parametrem/adminfile. PathToAdmindeployment.xml File

    AdditionalParametersAsNeeded

    Na przykład można określić następujący wiersz polecenia: `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\IDEinstall\AdminDeployment.xml /quiet /norestart`

   Naprawa jest domyślnym parametrem po zainstalowaniu programu Visual Studio. W przypadku naprawy programu Visual Studio ze zaktualizowanym parametrem/adminfile. zastąpią bieżące ustawienia wdrożenia administratora tymi, które są używane przez zaktualizowany plik AdminDeployment.xml.

## <a name="updating-an-installation"></a>Aktualizowanie instalacji
 Firma Microsoft udostępniła kilka aktualizacji programu Visual Studio 2015. W tej sekcji wyjaśniono, jak zaktualizować obraz instalacji nienadzorowanej programu Visual Studio 2015 w taki sposób, aby zawierał aktualizacje.

#### <a name="to-update-an-unattended-installation-of-visual-studio"></a>Aby zaktualizować instalację nienadzorowaną programu Visual Studio

1. Znajdź plik Product.exe w istniejącym obrazie sieci, kliknij go prawym przyciskiem myszy, a następnie kliknij polecenie **Właściwości**.

2. Kliknij kartę **szczegóły** , a następnie zanotuj Właściwość **Wersja produktu** .

    ![Przykład okna dialogowego właściwości w instalacji nienadzorowanej programu Visual Studio](../install/media/unattended-install-properties-dialog-box.PNG "Instalacja nienadzorowana — okno dialogowe właściwości")

3. ###### <a name="if-the-product-version-is-140247200-or-140247201-follow-these-steps"></a>Jeśli wersja produktu to 14.0.24720.0 lub 14.0.24720.1, wykonaj następujące kroki:
   1. Uruchom *Product.exe* *dysk/layout:* \IDEinstall na komputerze, który ma dostęp do Internetu. (Na przykład Uruchom: `vs_enterprise.exe /Layout d:\IDEinstall` .)

   2. Po zakończeniu/layout skopiuj nowy obraz do nowej lokalizacji.

   3. Utwórz i zmodyfikuj plik AdminDeployment.xml. W tym celu należy użyć `/CreateAdminFile` *\<file location>* parametru wiersza polecenia. (Aby uzyskać więcej informacji, zobacz sekcję "wdrażanie programu Visual Studio w trybie nienadzorowanym" w tym artykule).

   4. Na komputerze klienckim uruchom następujące polecenie, aby zaktualizować kopię programu Visual Studio, która została wcześniej zainstalowana: " \\ \\ *serwer1*\ IDEinstall_Updated_1 \\ *Product.exe* parametrem/adminfile. \\ \server1\ IDEinstall_Updated_1\AdminDeployment.xml/quiet/norestart".

        Na przykład uruchom polecenie: `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`
5. ###### <a name="for-other-product-version-values-follow-these-steps"></a>W przypadku innych wartości wersji produktu wykonaj następujące kroki:
   1. Uruchom *Product.exe* *dysk/layout:* \IDEinstall na komputerze, który ma dostęp do Internetu. (Na przykład uruchom `vs-enterprise.exe /Layout d:\IDEinstall` ).

   2. Po zakończeniu/layout skopiuj nowy obraz do nowej lokalizacji. (Możesz również zastąpić istniejący obraz sieciowy).

   3. Utwórz, a następnie zmodyfikuj plik AdminDeployment.xml. W tym celu należy użyć `/CreateAdminFile` *\<file location>* parametru wiersza polecenia. (Aby uzyskać więcej informacji, zobacz sekcję "wdrażanie programu Visual Studio w trybie nienadzorowanym" w tym artykule).

   4. W przypadku kopiowania obrazu do nowej lokalizacji należy uruchomić następujące polecenie na komputerze klienckim, aby zaktualizować kopię programu Visual Studio, która została wcześniej zainstalowana: " \\ \\ *serwer1*\ IDEinstall_Updated_1 \\ *Product.exe* parametrem/adminfile. \\ \server1\ IDEinstall_Updated_1\AdminDeployment.xml/quiet/norestart".

        Na przykład uruchom polecenie: `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`

   5. Jeśli zastąpisz istniejący obraz sieciowy, możesz uruchomić polecenie zgodnie z opisem w poprzednim kroku lub wykonać następujące czynności:
       1. Otwórz **Panel sterowania**, a następnie wybierz **aplet Programy i funkcje**.

       2. Wybierz **program Visual Studio**, a następnie wybierz pozycję **Zmień**.

       3. Po uruchomieniu programu Visual Studio w trybie konserwacji kliknij przycisk **Modyfikuj**.

       4. Na stronie funkcje powinna zostać wyświetlona Najnowsza aktualizacja. Wybierz inne funkcje, które chcesz zainstalować, kliknij przycisk **dalej**, a następnie kliknij przycisk **Aktualizuj** , aby zainstalować aktualizację i nowe funkcje.

## <a name="registering-the-product"></a>Rejestrowanie produktu
 Po zakończeniu instalacji możesz zarejestrować swoją kopię z poziomu programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

#### <a name="to-register"></a>Aby zarejestrować

1. Otwórz menu **Pomoc** , a następnie wybierz polecenie **zarejestruj produkt**.

2. Wprowadź klucz produktu.

     (Aby uzyskać więcej informacji, zobacz [instrukcje: Lokalizowanie klucza produktu Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md) i [instrukcje: automatyczne stosowanie kluczy produktów podczas wdrażania programu Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md) .)

## <a name="see-also"></a>Zobacz też
 [Instalowanie programu Visual Studio](../install/install-visual-studio-2015.md)