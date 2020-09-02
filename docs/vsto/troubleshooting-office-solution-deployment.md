---
title: Rozwiązywanie problemów z wdrażaniem rozwiązań pakietu Office
ms.date: 02/02/2017
ms.topic: troubleshooting
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
ms.openlocfilehash: fc8f336c3d43fb1f896d9e5e6b4d4d12c13d4064
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "87234981"
---
# <a name="troubleshoot-office-solution-deployment"></a>Rozwiązywanie problemów z wdrażaniem rozwiązań pakietu Office
  Ten temat zawiera informacje o sposobach rozwiązywania typowych problemów, które mogą wystąpić podczas wdrażania rozwiązań pakietu Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="troubleshoot-office-solutions-by-using-the-event-viewer"></a>Rozwiązywanie problemów z rozwiązaniami pakietu Office przy użyciu podglądu zdarzeń
 Możesz użyć podglądu zdarzeń w systemie Windows, aby wyświetlić komunikaty o błędach przechwycone przez [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] program podczas instalowania lub odinstalowywania rozwiązań pakietu Office. Możesz użyć tych komunikatów z rejestratora zdarzeń, aby rozwiązać problemy dotyczące instalacji i wdrażania. Aby uzyskać więcej informacji, zobacz [Rejestrowanie zdarzeń dla rozwiązań pakietu Office](../vsto/event-logging-for-office-solutions.md).

## <a name="change-the-assembly-name-causes-conflicts"></a>Zmiana nazwy zestawu powoduje konflikty
 Jeśli zmienisz wartość **nazwy zestawu** na stronie **aplikacji** **projektanta projektu** po wdrożeniu rozwiązania, narzędzia do publikowania zmodyfikują pakiet instalacyjny tak, aby zawierał jeden plik *Setup.exe* i dwa manifesty wdrożenia. W przypadku wdrażania dwóch plików manifestu mogą wystąpić następujące warunki:

- Jeśli użytkownik końcowy instaluje obie wersje, aplikacja załaduje oba dodatki narzędzi VSTO.

- Jeśli dodatek VSTO został zainstalowany przed zmianą nazwy zestawu, użytkownik końcowy nigdy nie będzie otrzymywać aktualizacji.

  Aby uniknąć tych warunków, nie zmieniaj wartości **nazwy zestawu** rozwiązania po wdrożeniu rozwiązania.

## <a name="check-for-updates-takes-a-long-time"></a>Sprawdzanie dostępności aktualizacji zajmuje dużo czasu
 Program Visual Studio 2010 Tools for Office Runtime zawiera wpis rejestru, za pomocą którego Administratorzy mogą ustawić wartość limitu czasu na potrzeby pobierania manifestów i rozwiązania.

#### <a name="to-set-the-time-out-value"></a>Aby ustawić wartość limitu czasu

1. W rejestrze przejdź do następującego klucza:

     **HKEY_CURRENT_USER \Software\Microsoft\VSTA**

2. W podkluczu **AddInTimeout** ustaw wartość limitu czasu (w milisekundach).

     Jeśli podklucz **AddInTimeout** nie istnieje, utwórz go jako wartość typu DWORD.

## <a name="cant-update-or-publish-to-a-network-file-share"></a>Nie można zaktualizować lub opublikować w sieciowym udziale plików
 W rozwiązaniach pakietu Office, które znajdują się w sieciowym udziale plików, może być wyświetlany komunikat o błędnej realizacji podczas aktualizacji, jeśli plik *Setup.exe* rozwiązania jest zablokowany w procesie podczas publikowania aktualizacji. Komunikat może być następujący: "nie można dodać" setup.exe "do sieci Web. Plik "setup.exe" już istnieje w tej sieci Web ".

 Aby zapobiec zablokowaniu plików, możesz udostępnić udział użytkownikom końcowym tylko do odczytu. Jednak jeśli dokumenty znajdują się w udziale, również będą tylko do odczytu dla użytkowników końcowych.

## <a name="prerequisites-for-microsoft-office-arent-installed"></a>Wymagania wstępne dotyczące Microsoft Office nie są zainstalowane
 Możesz dodać .NET Framework, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] i podstawowe zestawy międzyoperacyjności pakietu Office do pakietu instalacyjnego jako wymagania wstępne, które są wdrażane przy użyciu rozwiązania z pakietem Office. Aby uzyskać informacje na temat sposobu instalowania podstawowych zestawów międzyoperacyjnych, zobacz [Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/configuring-a-computer-to-develop-office-solutions.md) i [instrukcje: Instalowanie podstawowych zestawów międzyoperacyjnych pakietu Office](../vsto/how-to-install-office-primary-interop-assemblies.md).

## <a name="publish-using-localhost-can-cause-installation-problems"></a>Publikowanie przy użyciu hosta lokalnego może spowodować problemy z instalacją
 W przypadku korzystania `http://localhost` z programu jako lokalizacji publikowania lub instalacji dla rozwiązań na poziomie dokumentu **Kreator publikacji** nie konwertuje ciągu na rzeczywistą nazwę komputera. W takim przypadku rozwiązanie musi być zainstalowane na komputerze deweloperskim. Aby wdrożone rozwiązania korzystały z usług IIS na komputerze deweloperskim, należy użyć w pełni kwalifikowanej nazwy dla wszystkich lokalizacji HTTP/HTTPS/FTP zamiast localhost.

## <a name="cached-assemblies-are-loaded-instead-of-updated-assemblies"></a>Zestawy w pamięci podręcznej są ładowane zamiast zaktualizowanych zestawów
 Łączenie, moduł ładujący zestawy .NET Framework, ładuje buforowaną kopię zestawów, gdy ścieżka wyjściowa projektu znajduje się w sieciowym udziale plików, zestaw jest podpisany przy użyciu silnej nazwy, a wersja zestawu nie zmienia się. W przypadku zaktualizowania zestawu, który spełnia te warunki, aktualizacja nie zostanie wyświetlona podczas następnego uruchomienia projektu, ponieważ załadowana jest buforowana kopia.

 Program Visual Studio można skonfigurować tak, aby Fusion pobierał zestawy za każdym razem, gdy projekt zostanie uruchomiony.

### <a name="to-download-assemblies-instead-of-loading-cached-copies"></a>Aby pobrać zestawy zamiast ładować kopie buforowane

1. Na pasku menu wybierz **projekt**,**Właściwości** _ProjectName_.

2. Na stronie **aplikacja** wybierz pozycję **Informacje o zestawie**.

3. Ustaw numer poprawki, trzecie pole **wersji zestawu**, na symbol wieloznaczny ( \* ). Na przykład "1,0. *".  Następnie wybierz przycisk **OK** .

   Po zmianie wersji zestawu można nadal podpisać zestaw za pomocą silnej nazwy, a Fusion będzie ładować najnowszą wersję dostosowania.

 [!NOTE]
> Począwszy od programu Visual Studio 2017, jeśli spróbujesz użyć symboli wieloznacznych w wersji zestawu, wystąpi błąd kompilacji.  Dzieje się tak dlatego, że symbole wieloznaczne w wersji zestawu spowodują uszkodzenie funkcji deterministycznej programu MSBuild. Spowoduje to usunięcie symboli wieloznacznych z wersji zestawu lub wyłączenie.  Aby dowiedzieć się więcej o funkcji deterministycznej, zobacz: [typowe właściwości projektu MSBuild](../msbuild/common-msbuild-project-properties.md) i [Dostosowywanie kompilacji](../msbuild/customize-your-build.md)

## <a name="installation-fails-when-the-uri-has-characters-that-arent-us-ascii"></a>Instalacja nie powiedzie się, jeśli identyfikator URI zawiera znaki, które nie są US-ASCII
 W przypadku publikowania rozwiązania pakietu Office w lokalizacji HTTP/HTTPS/FTP ścieżka nie może zawierać żadnych znaków Unicode, które nie znajdują się w kodzie ASCII. Takie znaki mogą spowodować niespójne zachowanie w programie instalacyjnym. Użyj znaków US-ASCII dla ścieżki instalacji.

## <a name="prompt-to-manually-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Monit o ręczne odinstalowanie jest wyświetlany podczas publikowania i instalowania rozwiązania na komputerze deweloperskim
 Podczas kompilowania rozwiązania pakietu Office utworzona wersja jest automatycznie rejestrowana. Jeśli wcześniej opublikowano i zainstalowano to samo rozwiązanie na komputerze deweloperskim, program [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] wykryje, że ścieżka instalacji dla opublikowanej wersji i skompilowanej wersji różni się od kolejnego skompilowanego, skompilowanego lub opublikowanego rozwiązania. Zostanie wyświetlony komunikat o błędzie "nie można zainstalować dostosowania, ponieważ inna wersja jest obecnie zainstalowana i nie można jej uaktualnić z tej lokalizacji". Klucze rejestru są aktualizowane po każdym odbudowaniu rozwiązania. W związku z tym należy odinstalować poprzednią wersję przed opublikowaniem, debugowaniem lub uruchomieniem nowej wersji.

 Aby zapobiec wyświetlaniu komunikatu, Utwórz inne konto użytkownika na komputerze deweloperskim w celu przetestowania wdrożenia. Alternatywnie można odinstalować wersję z listy zainstalowanych programów na komputerze przed następną publikacją, debugowaniem lub kompilacją rozwiązania.

## <a name="uncaught-exception-or-method-not-found-error-when-you-install-a-solution"></a>Wystąpił błąd nieprzechwyconego wyjątku lub nieznalezienia metody podczas instalacji rozwiązania
 Po zainstalowaniu rozwiązań pakietu Office przez otwarcie manifestu wdrożenia (plik *. VSTO* ), aplikacji pakietu Office, dokumentu lub skoroszytu mogą pojawić się komunikaty o błędach dotyczące następujących warunków:

- Nie znaleziono metody.

- MissingMethodException.

- Nieprzechwycony wyjątek.

  Aby zapobiec wyświetlaniu tych komunikatów o błędach, Zainstaluj rozwiązanie, uruchamiając program instalacyjny.

  Po zainstalowaniu rozwiązania bez uruchamiania programu instalacyjnego Instalator nie sprawdza lub nie zainstaluje wymagań wstępnych. Program instalacyjny sprawdza poprawność wersji wstępnej i instaluje je w razie potrzeby.

## <a name="manifest-registry-keys-for-add-ins-change-after-an-installshield-limited-edition-project-is-built"></a>Klucze rejestru manifestu dla dodatków zmieniają się po skompilowaniu projektu InstallShield Limited Edition
 Klucz rejestru manifestu, który jest częścią Instalatora dodatku VSTO czasami zmienia się z *. VSTO* na *. dll. manifest* podczas kompilowania projektu InstallShield Limited Edition.

 Aby obejść ten problem, należy utworzyć projekt InstallShield Limited Edition w innym rozwiązaniu lub użyć elementu NazwaFirmy. AddinName jako wartości klucza rejestru zawierającego nazwę dodatku VSTO.

## <a name="the-clickonce-installer-for-your-office-solution-doesnt-install-the-primary-interop-assemblies"></a>Instalator ClickOnce dla Twojego rozwiązania pakietu Office nie instaluje podstawowych zestawów międzyoperacyjnych
 Po uruchomieniu programu instalacyjnego, który jest tworzony przez ClickOnce dla rozwiązania pakietu Office, Instalator dla podstawowych zestawów międzyoperacyjnych (zestawów PIA) pakietu Office działa tylko wtedy, gdy żaden zestawów PIA nie jest już zainstalowany.

 Jeśli program instalacyjny nie zainstaluje prawidłowo zestawów Pia, należy zainstalować je ręcznie, uruchamiając plik Instalatora o nazwie *o2007pia.msi* z katalogu instalacyjnego.

## <a name="reinstall-office-solutions-causes-an-argument-out-of-range-exception"></a>Ponowne zainstalowanie rozwiązań pakietu Office powoduje wyjątek poza zakresem
 Po ponownym zainstalowaniu rozwiązania pakietu Office <xref:System.ArgumentOutOfRangeException> może wystąpić wyjątek z następującym komunikatem o błędzie: określony argument jest poza zakresem prawidłowych wartości.

 Taka sytuacja występuje, jeśli wielkość liter w adresie URL lokalizacji instalacji jest inna. Na przykład ten błąd pojawia się, jeśli po raz pierwszy zainstalowano rozwiązanie pakietu Office `http://fabrikam.com/ExcelSolution.vsto` , a następnie użyto `http://fabrikam.com/excelsolution.vsto` drugiego czasu.

 Aby zapobiec wyświetlaniu komunikatu, Użyj tej samej wielkości liter podczas instalacji rozwiązań pakietu Office.

## <a name="cant-install-a-clickonce-solution-by-opening-the-deployment-manifest-from-the-web"></a>Nie można zainstalować rozwiązania ClickOnce, otwierając manifest wdrożenia z sieci Web
 Użytkownicy mogą instalować rozwiązania pakietu Office, otwierając manifest wdrożenia z sieci Web. Jednak niektóre instalacje programu Internet Information Services (IIS) blokują rozszerzenie nazwy pliku *. VSTO* . Należy zdefiniować typ MIME w usługach IIS przed użyciem go do wdrożenia rozwiązania biurowego.

 Informacje o sposobie definiowania typu MIME w usługach IIS 7 można znaleźć w temacie [Add a MIME Type (IIS7)](https://technet.microsoft.com/library/cc725608(WS.10).aspx).

 Dla rozszerzenia **VSTO** i typu MIME ustaw wartość **Application/x-MS-VSTO**.

## <a name="see-also"></a>Zobacz też

- [Rozwiązywanie problemów z wdrożeniami technologii ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
- [Wdróż rozwiązanie pakietu Office](../vsto/deploying-an-office-solution.md)
- [Rozwiązywanie problemów z programem Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
