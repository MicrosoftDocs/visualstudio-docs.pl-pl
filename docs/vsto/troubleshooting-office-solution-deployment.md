---
title: Rozwiązywanie problemów z wdrażaniem rozwiązania pakietu Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- Office development in Visual Studio, troubleshooting
- deploying applications [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: de036ce9b0b566a6028b0ccfe45cfe5f2ac49da9
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444937"
---
# <a name="troubleshoot-office-solution-deployment"></a>Rozwiązywanie problemów z wdrażaniem rozwiązania pakietu Office
  Ten temat zawiera informacje dotyczące rozwiązywania typowych problemów, które mogą wystąpić podczas wdrażania rozwiązań pakietu Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="troubleshoot-office-solutions-by-using-the-event-viewer"></a>Rozwiązywanie problemów z rozwiązaniami pakietu Office przy użyciu podglądu zdarzeń
 Za pomocą przeglądarki zdarzeń w systemie Windows można wyświetlać komunikaty o błędach przechwycone przez rozwiązania pakietu Office [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] podczas instalowania lub odinstalowywania rozwiązań pakietu Office. Te komunikaty z rejestratora zdarzeń można użyć do rozwiązania problemów z instalacją i wdrażaniem. Aby uzyskać więcej informacji, zobacz [Rejestrowanie zdarzeń dla rozwiązań pakietu Office](../vsto/event-logging-for-office-solutions.md).

## <a name="change-the-assembly-name-causes-conflicts"></a>Zmiana nazwy zestawu powoduje konflikty
 Jeśli zmienisz wartość **Nazwa zestawu** na stronie **Aplikacji** **projektanta projektu** po już wdrożonym rozwiązaniu, narzędzia do publikowania zmodyfikują pakiet Instalatora, aby mieć jeden plik *Setup.exe* i dwa manifesty wdrażania. Jeśli wdrożysz dwa pliki manifestu, mogą wystąpić następujące warunki:

- Jeśli użytkownik końcowy zainstaluje obie wersje, aplikacja załaduje oba dodatki VSTO.

- Jeśli dodatek VSTO został zainstalowany przed zmianą nazwy zestawu, użytkownik końcowy nigdy nie otrzyma aktualizacji.

  Aby uniknąć tych warunków, nie należy zmieniać wartości **nazwa zestawu** rozwiązania po wdrożeniu rozwiązania.

## <a name="check-for-updates-takes-a-long-time"></a>Sprawdzanie dostępności aktualizacji zajmuje dużo czasu
 Visual Studio 2010 Narzędzia dla środowiska wykonawczego pakietu Office udostępnia wpis rejestru, który administratorzy mogą używać do ustawiania wartości limit czasu do pobierania manifestów i rozwiązania.

#### <a name="to-set-the-time-out-value"></a>Aby ustawić wartość przesuwu

1. W rejestrze przejdź do następującego klucza:

     **HKEY_CURRENT_USER\Oprogramowanie\Microsoft\VSTA**

2. W podkluczu **AddInTimeout** ustaw wartość limitu czasu w milisekundach.

     Jeśli **subklucz AddInTimeout** nie istnieje, utwórz go jako DWORD.

## <a name="cant-update-or-publish-to-a-network-file-share"></a>Nie można zaktualizować ani opublikować w sieciowym udziale plików
 Rozwiązania pakietu Office, które znajdują się w sieciowym udziale plików, mogą wyświetlać mylący komunikat podczas aktualizacji, jeśli plik *Setup.exe* rozwiązania jest zablokowany w procesie podczas publikowania aktualizacji. Komunikat może brzmieć następująco: "Nie można dodać 'setup.exe' do sieci Web. Plik 'setup.exe' już istnieje w tej sieci Web."

 Aby zapobiec blokowaniu plików, można udostępnić tylko do odczytu użytkownikom końcowym. Jeśli jednak dokumenty znajdują się w udziale, staną się one również tylko do odczytu dla użytkowników końcowych.

## <a name="prerequisites-for-microsoft-office-arent-installed"></a>Wymagania wstępne pakietu Microsoft Office nie są zainstalowane
 Można dodać .NET Framework, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], i pakietu Office podstawowych zestawów interop do pakietu instalatora jako wymagania wstępne, które są wdrażane z rozwiązaniem pakietu Office. Aby uzyskać informacje dotyczące instalowania podstawowych zestawów międzyoperacyjnych, zobacz [Konfigurowanie komputera do tworzenia rozwiązań pakietu Office](../vsto/configuring-a-computer-to-develop-office-solutions.md) i [Jak: Instalowanie podstawowych zestawów interop pakietu Office](../vsto/how-to-install-office-primary-interop-assemblies.md).

## <a name="publish-using-localhost-can-cause-installation-problems"></a>Publikowanie przy użyciu localhost może powodować problemy z instalacją
 W przypadku `http://localhost` użycia jako lokalizacji publikowania lub instalacji rozwiązań na poziomie dokumentu **Kreator publikowania** nie konwertuje ciągu na rzeczywistą nazwę komputera. W takim przypadku rozwiązanie musi być zainstalowane na komputerze deweloperskim. Aby wdrożone rozwiązania używały usług IIS na komputerze deweloperskim, należy użyć w pełni kwalifikowanej nazwy dla wszystkich lokalizacji HTTP/HTTPS/FTP zamiast hosta lokalnego.

## <a name="cached-assemblies-are-loaded-instead-of-updated-assemblies"></a>Buforowane zestawy są ładowane zamiast zaktualizowanych zestawów
 Fusion, moduł ładujący zestawu .NET Framework, ładuje buforowaną kopię zestawów, gdy ścieżka wyjściowa projektu znajduje się w udziale plików sieciowych, zestaw jest podpisany o silnej nazwie, a wersja zestawu dostosowywania nie ulegnie zmianie. Jeśli zaktualizujesz zestaw, który spełnia te warunki, aktualizacja nie pojawi się przy następnym uruchomieniu projektu, ponieważ kopia w pamięci podręcznej jest ładowany.

 Program Visual Studio można skonfigurować tak, aby Fusion pobierał zestawy za każdym razem, gdy projekt jest uruchamiany.

### <a name="to-download-assemblies-instead-of-loading-cached-copies"></a>Aby pobrać zestawy zamiast ładować buforowane kopie

1. Na pasku menu wybierz polecenie **Project**, _ProjectName_**Properties**.

2. Na stronie **Aplikacja** wybierz pozycję **Informacje o zestawie**.

3. Ustaw numer poprawki, trzecie pole wersji **zestawu**, na\*symbol wieloznaczny ( ). Na przykład "1.0.*".  Następnie wybierz przycisk **OK.**

   Po zmianie wersji zestawu, można kontynuować podpisywanie zestawu z silną nazwą i Fusion załaduje najnowszą wersję dostosowywania.

 [!NOTE]
> Począwszy od programu Visual Studio 2017, jeśli spróbujesz przy użyciu dzikich kart w wersji zestawu wystąpi błąd kompilacji.  Dzieje się tak, ponieważ dzikie karty w wersji zestawu spowoduje przerwanie funkcji deterministycznej MSBuild. Zostaniesz poinstruowany, aby usunąć symbole wieloznaczne z wersji zestawu lub wyłączyć determinizm.  Aby dowiedzieć się więcej o funkcji deterministycznej, zobacz: [Typowe właściwości projektu MSBuild](../msbuild/common-msbuild-project-properties.md) i [dostosowywanie kompilacji](../msbuild/customize-your-build.md)

## <a name="installation-fails-when-the-uri-has-characters-that-arent-us-ascii"></a>Instalacja kończy się niepowodzeniem, gdy identyfikator URI ma znaki, które nie są US-ASCII
 Podczas publikowania rozwiązania pakietu Office w lokalizacji HTTP/HTTPS/FTP ścieżka nie może mieć żadnych znaków Unicode, które nie są w usłudze US-ASCII. Takie znaki mogą powodować niespójne zachowanie w programie instalacyjnym. Użyj znaków US-ASCII dla ścieżki instalacji.

## <a name="prompt-to-manually-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Monit o ręczne odinstalowanie pojawia się po opublikowaniu i zainstalowaniu rozwiązania na komputerze deweloperskim
 Podczas tworzenia rozwiązania pakietu Office, wersja zbudowana jest automatycznie rejestrowana. Jeśli wcześniej opublikowano i zainstalowano to samo rozwiązanie [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] na komputerze deweloperskim, wykryje, że ścieżka instalacji dla opublikowanej wersji i wersji wbudowanej są różne po następnym skompilowanym, przebudowanym lub opublikowanym rozwiązaniu. Komunikat o błędzie mówi "nie można zainstalować dostosowania, ponieważ inna wersja jest aktualnie zainstalowana i nie można jej uaktualnić z tej lokalizacji". Klucze rejestru są aktualizowane za każdym razem, gdy rozwiązanie jest przebudowywane. W związku z tym należy odinstalować poprzednią wersję przed opublikowaniem, debugowanie lub uruchomienie nowej wersji.

 Aby zapobiec pojawianiu się komunikatu, utwórz inne konto użytkownika na komputerze deweloperskim, aby przetestować wdrożenie. Alternatywnie można odinstalować wersję z listy zainstalowanych programów na komputerze przed następnym opublikowaniem, debugowaniem lub odbudowaniem rozwiązania.

## <a name="uncaught-exception-or-method-not-found-error-when-you-install-a-solution"></a>Nieprzechowywudowy wyjątek lub nie znaleziono błędu metody podczas instalowania rozwiązania
 Podczas instalowania rozwiązań pakietu Office przez otwarcie manifestu wdrożenia (pliku *vsto),* aplikacji pakietu Office, dokumentu lub skoroszytu mogą pojawić się komunikaty o błędach dotyczące następujących warunków:

- Nie znaleziono metody.

- Missingmethodexception.

- Nieprzechodny wyjątek.

  Aby zapobiec tym komunikatom o błędach, zainstaluj rozwiązanie, uruchamiając program instalacyjny.

  Po zainstalowaniu rozwiązania bez uruchamiania programu instalacyjnego instalator nie sprawdza ani nie instaluje wymagań wstępnych. Program instalacyjny sprawdza poprawną wersję wymagań wstępnych i instaluje je w razie potrzeby.

## <a name="manifest-registry-keys-for-add-ins-change-after-an-installshield-limited-edition-project-is-built"></a>Manifest klucze rejestru dla dodatków zmienić po InstallShield Limited Edition projekt jest zbudowany
 Klucz rejestru manifestu, który jest częścią programu instalacyjnego dodatku VSTO, czasami zmienia się z *vsto* na *.dll.manifest* podczas tworzenia projektu InstallShield Limited Edition.

 Aby obejść ten problem, utwórz projekt InstallShield Limited Edition w innym rozwiązaniu lub użyj CompanyName.AddinName jako wartości klucza rejestru zawierającego nazwę dodatku VSTO.

## <a name="the-clickonce-installer-for-your-office-solution-doesnt-install-the-primary-interop-assemblies"></a>Instalator ClickOnce dla rozwiązania pakietu Office nie instaluje podstawowych zestawów międzyoperacyjnych
 Po uruchomieniu programu instalacyjnego, który ClickOnce tworzy dla rozwiązania pakietu Office, instalator podstawowych zestawów międzyoperacyjnych pakietu Office (PIA) działa tylko wtedy, gdy nie są już zainstalowane żadne pia.

 Jeśli instalator nie instaluje pias poprawnie, zainstaluj je ręcznie, uruchamiając plik instalatora o nazwie *o2007pia.msi* z katalogu instalacji.

## <a name="reinstall-office-solutions-causes-an-argument-out-of-range-exception"></a>Ponowne instalowanie rozwiązań pakietu Office powoduje wyjątek argumentu poza zakresem
 Podczas ponownej instalacji rozwiązania <xref:System.ArgumentOutOfRangeException> pakietu Office może pojawić się wyjątek z następującym komunikatem o błędzie: Określony argument był poza zakresem prawidłowych wartości.

 Taka sytuacja występuje, jeśli wielkość liter dla adresu URL dla lokalizacji instalacji jest inna. Na przykład ten błąd pojawi się, jeśli `http://fabrikam.com/ExcelSolution.vsto` zainstalowano rozwiązanie `http://fabrikam.com/excelsolution.vsto` pakietu Office od pierwszego razu, a następnie użyto po raz drugi.

 Aby zapobiec pojawianiu się wiadomości, użyj tej samej wielkości liter podczas instalowania rozwiązań pakietu Office.

## <a name="cant-install-a-clickonce-solution-by-opening-the-deployment-manifest-from-the-web"></a>Nie można zainstalować rozwiązania ClickOnce, otwierając manifest wdrożenia z sieci Web
 Użytkownicy mogą instalować rozwiązania pakietu Office, otwierając manifest wdrożenia z sieci Web. Jednak niektóre instalacje internetowych usług informacyjnych (IIS) blokują rozszerzenie nazwy pliku *vsto.* Należy zdefiniować typ MIME w serwisach IIS przed użyciem go do wdrożenia rozwiązania pakietu Office.

 Aby uzyskać informacje dotyczące definiowania typu MIME w iis 7, zobacz [Dodawanie typu MIME (IIS7)](https://technet.microsoft.com/library/cc725608(WS.10).aspx).

 Ustaw rozszerzenie na **.vsto** i typ MIME na **application/x-ms-vsto**.

## <a name="see-also"></a>Zobacz też

- [Rozwiązywanie problemów z wdrożeniami technologii ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
- [Wdrażanie rozwiązania pakietu Office](../vsto/deploying-an-office-solution.md)
