---
title: 'Instrukcje: Utworzyć i uruchomić nienadzorowaną instalację | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installing Visual Studio, unattended
- unattended installation, Visual Studio
ms.assetid: 3867b5dc-ed34-4ee2-be32-a42e7e320517
caps.latest.revision: 44
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 0045ff701947f834bd38dfff7c90b7388e9353b7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53951933"
---
# <a name="how-to-create-and-run-an-unattended-installation-of-visual-studio"></a>Instrukcje: Utworzyć i uruchomić nienadzorowaną instalację programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można uruchomić aplikację instalacji dla [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jako nienadzorowaną (dyskretna) instalacji za pośrednictwem intranetu, zamiast z nośnika, takiego jak DVD. W tym temacie opisano sposób przygotowania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dla tego typu instalacji z udziału sieciowego.

## <a name="creating-a-network-image"></a>Tworzenie obrazu sieciowego
 Najpierw należy utworzyć obraz sieciowy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nośnika.

#### <a name="to-create-a-network-image"></a>Aby utworzyć obraz sieciowy

1.  Utwórz folder na serwerze (na przykład *dysku*: \IDEinstall\\).

2.  Pobierz Instalatora z [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015), a następnie uruchom *produktu*.exe/Layout *dysku*: \IDEinstall\

3.  Udostępnij folder IDEinstall w sieci, a następnie ustaw odpowiednie ustawienia zabezpieczeń.

     Ścieżka sieciowa aplikacji instalacyjnej dla [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] przypomina \\ \\ *ServerName*\IDEinstall\\*produktu*.exe.

    > [!NOTE]
    >  Instalacja może zakończyć się niepowodzeniem, jeśli wszystkie ścieżce kombinacja nazwy pliku przekracza 260 znaków. Maksymalna długość ścieżki w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] to 221 znaków.  Nazwa ścieżki lokalnej nie powinna przekraczać 70 znaków, a nazwa ścieżki sieciowej nie powinna przekraczać 39 znaków.

     Instalację mogą zakończyć się niepowodzeniem, jeśli nazwy folderów w ścieżce zawierają spacje (na przykład "\\\\*ServerName*instalacji \IDE" lub \\ \\ *ServerName*\Visual studio\\).

## <a name="deploying-visual-studio-in-unattended-mode"></a>Wdrażanie programu Visual Studio w trybie instalacji nienadzorowanej
 Aby wdrożyć [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] w trybie nienadzorowanym, musisz zmodyfikować plik AdminDeployment.xml. Aby to zrobić, należy najpierw utworzyć plik AdminDeployment.xml przy użyciu `/CreateAdminFile`  *\<lokalizacja pliku >* parametru wiersza polecenia. Następnie można użyć tego pliku do wypychania wdrażanie programu Visual Studio z siecią lub wyciągniesz go do instalacji, jeśli umieścisz ten plik *dysku*: \IDEinstall\packages katalogu. Plik AdminDeployment.xml nie jest unikatowy dla systemu operacyjnego, architektury, wydanie programu Visual Studio lub języka systemu operacyjnego.

> [!CAUTION]
>  Czasami elementów jako wybranego na liście plik AdminDeployment.xml nie zainstalowane. Aby rozwiązać ten problem, umieść elementy oznaczone jako "wybrane ="yes"" w **zakończenia** z plik AdminDeployment.xml.
>
>  Jeśli nie chcesz zainstalować opcjonalne zależności elementu, musisz najpierw wybrać element nadrzędny i usuń zaznaczenie opcji opcjonalne zależności po nadrzędnego, jak pokazano na poniższym zrzucie ekranu:
>
>  ![Elementy wymagane do instalacji na końcu plik AdminDeployment.xml](../install/media/vs2015-install-endoffileadmindeploy.PNG "vs2015_Install_EndOfFileAdminDeploy")
>
>  Innym sposobem, w tym celu jest po prostu pominąć opcjonalny element podrzędny elementu nadrzędnego — innymi słowy, nie zawierają żadnego "wybrane ="no"" elementów —, ale nadal należy umieścić wszystkie "wybrane ="yes"" elementy na końcu plik AdminDeployment.xml.

> [!IMPORTANT]
>  Podczas instalacji komputer może automatycznie uruchomiony ponownie jeden lub więcej razy. Po ponownym uruchomieniu, należy zalogować się ponownie przy użyciu tego samego konta użytkownika, z którym użytkownik był zalogowany do przeprowadzenia instalacji przed ponownym uruchomieniem komputera. Możesz uniknąć automatycznego ponownego uruchamiania, instalując wstępnie wymagane składniki przed uruchomieniem instalacji nienadzorowanej. Aby uzyskać więcej informacji, zobacz sekcję zatytułowaną "Uniknąć ponownego uruchomienia podczas instalacji" w [Podręcznik administratora programu Visual Studio](../install/visual-studio-administrator-guide.md).

 Schemat pliku AdminDeployment zawiera następujące elementy:

|Element|Atrybut|Wartości|Opis|
|-------------|---------------|------------|-----------------|
|BundleCustomizations|TargetDir|*Path*|Działa tak samo jak zastępowanie ścieżki w interfejsie użytkownika aplikacji instalacji. Ten element jest ignorowany, jeśli program Visual Studio jest już zainstalowany.|
|BundleCustomizations|NoWeb|tak&#124;domyślne|Jeśli wartość tego elementu jest twierdząca, aplikacja instalacji nigdy nie próbuje go w sieci Web podczas działania Instalatora.|
|Selectableitemcustomization, zależnie od|Hidden|Tak&#124;nr|Jeśli wartość tego elementu jest twierdząca, ukrywa element podlegający wyborowi w drzewie dostosowywania.|
|Selectableitemcustomization, zależnie od|Wybrane|Tak&#124;nr|Zaznacza lub czyści elementy wybieralne w drzewie dostosowywania.|
|BundleCustomizations|źródło danych|Ścieżka|Lokalizacja źródła danych, które użytkownik chce używać.  To źródło danych jest używany dla kolejnych modyfikować operacji na komputerze ("domyślna" domyślnie).|
|BundleCustomizations|SuppressRefreshPrompt|tak&#124;domyślne|Będzie zapobiec monitowaniu odświeżyć instalacji, jeśli jest dostępna nowsza jeden użytkownik.|
|BundleCustomizations|NoRefresh|tak&#124;domyślne|Nie będzie Odśwież instalacji, jeśli jest dostępny nowszej.|
|BundleCustomizations|NoCacheOnlyMode|tak&#124;domyślne|Zapobiega wstępnemu zapełnianiu pamięci podręcznej pakietu.|

> [!WARNING]
>  Aplikacja instalacyjna będzie uwzględniać stan wybrany w SelectableItem, nawet jeśli jest on ukryty. Na przykład jeśli chcesz zawsze instalować element podlegający wyborowi, możesz oznaczyć go jako ukryty i wybrany.

#### <a name="to-create-an-unattended-installation-of-visual-studio"></a>Aby utworzyć instalację nienadzorowaną programu Visual Studio

1.  W *dysku*: \IDEinstall\AdminDeployment.xml plik, zmień wartość atrybutu NoWeb na element dostosowania pakietu z "domyślne" na "tak", co ilustruje poniższy przykład:

     Zmiana `<BundleCustomizations TargetDir="default" NoWeb="default"/>` do `<BundleCustomizations TargetDir="default" NoWeb="yes"/>`

2.  Zmień atrybut selectableitemcustomization, zależnie od potrzeb dla składników opcjonalnych, a następnie zapisz plik.

## <a name="running-unattended-setup"></a>Uruchamianie instalacji nienadzorowanej
 Instalacja nienadzorowana można uruchomić albo przez automatyczne uruchomienie aplikacji instalacyjnej dla programu Visual Studio na komputerach klienckich, pozwalając użytkownikom na uruchamianie aplikacji samodzielnie przy użyciu ustawień zdefiniowanych przez użytkownika.

#### <a name="to-run-an-unattended-installation-on-a-client-computer"></a>Aby uruchomić nienadzorowaną instalację na komputerze klienckim

- Otwórz **Start** menu, wybierz **Uruchom**, a następnie wprowadź \\ \\ *ServerName*\IDEinstall\vs_*produktu*.exe parametrem/adminfile *PathOfTheAdmindeployment.xmlFile*<em>AdditionalParametersAsNeeded</em>

   Na przykład można określić następujące polecenie w wierszu: `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\ IDEinstall\AdminDeployment.xml /quiet /norestart`

#### <a name="to-enable-clients-to-manually-install-visual-studio-with-pre-defined-settings"></a>Aby umożliwić klientom ręczną instalację programu Visual Studio ze wstępnie zdefiniowanymi ustawieniami

1.  Skopiuj dostosowany plik AdminDeployment.xml do udziału sieciowego, który jest tylko do odczytu (na przykład \\ \\ *ServerName*\IDEinstall\packages\AdminDeployment.xml).

2.  Pozwalają użytkownikom na instalowanie z tego folderu wspólnego.

## <a name="maintaining-an-installation"></a>Obsługiwanie instalacji
 Jeśli otworzysz **Panelu sterowania** i ponownie uruchom instalację aplikacji, można zmodyfikować funkcje programu Visual Studio, odinstalować języki programowania, a także naprawić lub odinstalować program Visual Studio.

> [!NOTE]
>  Musi mieć poświadczenia administracyjne na komputerze lokalnym, aby używać trybu konserwacji.

#### <a name="to-maintain-an-installation-on-a-client-computer"></a>Aby prowadzić instalację na komputerze klienckim

-   Otwórz **Panelu sterowania**, a następnie wybierz **programy i funkcje**.

-   Wybierz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], a następnie wybierz **zmiany**.

#### <a name="to-change-admindeployment-settings-on-a-client-computer-after-visual-studio-has-been-installed"></a>Aby zmienić ustawienia AdminDeployment na komputerze klienckim po zainstalowaniu programu Visual Studio

1. Zaktualizuj plik AdminDeployment.xml.

2. Otwórz **Start** menu, a następnie wybierz **Uruchom**.

3. Wprowadź następujący tekst: \\\\*ServerName*\IDEinstall\vs_*produktu*pliku PathToAdmindeployment.xml parametrem/adminfile .exe

    AdditionalParametersAsNeeded

    Na przykład można określić następujące polecenie w wierszu: `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\IDEinstall\AdminDeployment.xml /quiet /norestart`

   Naprawa jest parametrem domyślnym po zainstalowaniu programu Visual Studio. Jeśli naprawisz Visual Studio za pomocą aktualizacji/pliku, spowoduje zastąpienie bieżącego ustawienia wdrażania administratora z tymi, które wywołuje zaktualizowany plik AdminDeployment.xml.

## <a name="updating-an-installation"></a>Aktualizowanie instalacji
 Firma Microsoft wydała kilka aktualizacji do programu Visual Studio 2015. W tej sekcji wyjaśniono, jak można zaktualizować obrazu instalacji nienadzorowanej programu Visual Studio 2015, aby obejmowała aktualizacji.

#### <a name="to-update-an-unattended-installation-of-visual-studio"></a>Aby zaktualizować instalacji nienadzorowanej programu Visual Studio

1. Zlokalizuj plik Product.exe w istniejący obraz sieci, kliknij go prawym przyciskiem myszy, a następnie kliknij **właściwości**.

2. Kliknij przycisk **szczegóły** kartę, a następnie zanotuj **wersji produktu** właściwości.

    ![Przykład okno dialogowe właściwości w przypadku instalacji nienadzorowanej programu Visual Studio](../install/media/unattended-install-properties-dialog-box.PNG "instalacji nienadzorowanej — okno dialogowe właściwości")

3. ###### <a name="if-the-product-version-is-140247200-or-140247201-follow-these-steps"></a>W przypadku 14.0.24720.0 lub 14.0.24720.1 wersję produktu, wykonaj następujące kroki:
4. 1.  Uruchom *Product.exe* /Layout *dysków:* \IDEinstall na komputerze, który ma dostęp do Internetu. (Na przykład uruchomić: `vs_enterprise.exe /Layout d:\IDEinstall`.)

   2.  Po zakończeniu / Layout, skopiuj nowy obraz do nowej lokalizacji.

   3.  Utworzyć i zmodyfikować plik AdminDeployment.xml. Aby to zrobić, należy użyć `/CreateAdminFile`  *\<lokalizacja pliku >* parametru wiersza polecenia. (Aby uzyskać więcej informacji, zobacz sekcję "Wdrażanie Visual Studio w trybie nienadzorowanym" tego artykułu).

   4.  Na komputerze klienckim, uruchom następujące polecenie, aby zaktualizować kopię programu Visual Studio, który został wcześniej zainstalowany: "\\\\*serwer1*\IDEinstall_Updated_1\\*Product.exe*  parametrem/adminfile \\\server1\ IDEinstall_Updated_1\AdminDeployment.xml/quiet/norestart ".

        Na przykład uruchomić: `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`
5. ###### <a name="for-other-product-version-values-follow-these-steps"></a>Dla innych wartości wersji produktu wykonaj następujące kroki:
6. 1.  Uruchom *Product.exe* /Layout *dysków:* \IDEinstall na komputerze, który ma dostęp do Internetu. (Na przykład uruchomić `vs-enterprise.exe /Layout d:\IDEinstall`.)

   2.  Po zakończeniu / Layout, skopiuj nowy obraz do nowej lokalizacji. (Lub, możesz zamiast tego zastąpić istniejący obraz sieci.)

   3.  Utwórz, a następnie zmodyfikować plik AdminDeployment.xml. Aby to zrobić, należy użyć `/CreateAdminFile`  *\<lokalizacja pliku >* parametru wiersza polecenia. (Aby uzyskać więcej informacji, zobacz sekcję "Wdrażanie Visual Studio w trybie nienadzorowanym" tego artykułu).

   4.  Jeśli kopiujesz obrazu do nowej lokalizacji na komputerze klienckim, aby zaktualizować kopię programu Visual Studio, który został wcześniej zainstalowany, musi uruchom następujące polecenie: "\\\\*serwer1*\IDEinstall_Updated_1\\ *Product.exe* parametrem/adminfile \\\server1\ IDEinstall_Updated_1\AdminDeployment.xml/quiet/norestart ".

        Na przykład uruchomić: `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`

   5.  Możesz zastąpić istniejący obraz sieci, można uruchomić polecenie, zgodnie z opisem w poprzednim kroku, czy można wykonać następujące czynności:

   6.  1.  Otwórz **Panelu sterowania**, a następnie wybierz **programy i funkcje**.

       2.  Wybierz **programu Visual Studio**, a następnie wybierz **zmiany**.

       3.  Po uruchomieniu programu Visual Studio w trybie konserwacji, kliknij przycisk **Modyfikuj**.

       4.  Najnowsza aktualizacja powinna zostać wyświetlona na stronie funkcji. Wybierz funkcje, które chcesz zainstalować, kliknij przycisk **dalej**, a następnie kliknij przycisk **aktualizacji** do zainstalowania aktualizacji i nowych funkcji.

## <a name="registering-the-product"></a>Rejestrowanie produktu
 Po zakończeniu instalacji możesz zarejestrować swoją kopię [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] z poziomu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

#### <a name="to-register"></a>Aby zarejestrować

1.  Otwórz **pomocy** menu, a następnie wybierz **Zarejestruj produkt**.

2.  Wprowadź klucz produktu.

     (Aby uzyskać więcej informacji, zobacz [jak: Znajdź klucz produktu programu Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md) i [jak: Automatyczne stosowanie kluczy produktów podczas wdrażania programu Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md) tematy.)

## <a name="see-also"></a>Zobacz też
 [Instalowanie programu Visual Studio](../install/install-visual-studio-2015.md)