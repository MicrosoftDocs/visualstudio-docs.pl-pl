---
title: Rozwiązywanie problemów z wdrażaniem rozwiązań Office
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
ms.openlocfilehash: 418a1a22979b701ec1d1d32521f7f89e2c5274eb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60088096"
---
# <a name="troubleshoot-office-solution-deployment"></a>Rozwiązywanie problemów z wdrażaniem rozwiązań Office
  Ten temat zawiera informacje o tym, jak rozwiązać typowe problemy, które mogą wystąpić podczas wdrażania rozwiązań pakietu Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="troubleshoot-office-solutions-by-using-the-event-viewer"></a>Rozwiązywanie problemów z rozwiązań pakietu Office za pomocą Podglądu zdarzeń
 Aby wyświetlić komunikaty o błędach, które są przechwytywane przez służy Podgląd zdarzeń w Windows [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] po zainstalowaniu lub odinstalowaniu rozwiązań pakietu Office. Te komunikaty z Rejestratora zdarzeń służy do instalacji i problemy z wdrażaniem. Aby uzyskać więcej informacji, zobacz [rejestrowanie zdarzeń dla rozwiązań pakietu Office](../vsto/event-logging-for-office-solutions.md).

## <a name="change-the-assembly-name-causes-conflicts"></a>Zmień nazwę zestawu powoduje, że konflikty
 Jeśli zmienisz **nazwy zestawu** wartość w **aplikacji** strony **projektanta projektu** po zostało już wdrożone to rozwiązanie, zmodyfikuje narzędzia publikowania Pakiet instalacyjny, aby istniało jedno *Setup.exe* plików i dwa manifesty wdrożenia. Jeśli wdrożono dwa pliki manifestu, mogą wystąpić następujące warunki:

- Jeśli użytkownik końcowy instaluje obie wersje, aplikacja zostanie załadowany obu dodatków narzędzi VSTO dla programów.

- Jeśli dodatku narzędzi VSTO została zainstalowana przed zmianą nazwy zestawu, użytkownik końcowy nigdy nie będzie otrzymywać aktualizacje.

  Aby uniknąć tych warunków, nie należy zmieniać tego rozwiązania **nazwy zestawu** wartość po wdrożeniu rozwiązania.

## <a name="check-for-updates-takes-a-long-time"></a>Sprawdź, czy aktualizacje zajmuje dużo czasu
 Visual Studio 2010 Tools dla pakietu Office runtime zawiera wpis rejestru, które umożliwiają administratorom można ustawić wartość limitu czasu pobierania manifestów, jak i rozwiązania.

#### <a name="to-set-the-time-out-value"></a>Aby ustawić wartość limitu czasu

1. W rejestrze przejdź do następującego klucza:

     **HKEY_CURRENT_USER\Software\Microsoft\VSTA**

2. W **AddInTimeout** podklucza, należy ustawić wartość limitu czasu w milisekundach.

     Jeśli **AddInTimeout** podklucz nie istnieje, utwórz ją jako wartość typu DWORD.

## <a name="cant-update-or-publish-to-a-network-file-share"></a>Nie można zaktualizować ani publikować w sieciowym udziale plików
 Rozwiązań pakietu Office, które są w sieciowym udziale plików może wyświetlić mylący komunikat podczas aktualizacji, jeśli rozwiązanie *Setup.exe* plik jest zablokowany w procesie, gdy jest on publikowany aktualizacji. Komunikat powiedzieć następujące czynności: "Nie można dodać"setup.exe"w sieci Web. Plik setup.exe już istnieje w tej sieci Web".

 Aby uniknąć blokowania plików, należy wybrać udziału tylko do odczytu do użytkowników końcowych. Jednak jeśli dokumenty znajdują się w udziale, również staną się tylko do odczytu do użytkowników końcowych.

## <a name="prerequisites-for-microsoft-office-arent-installed"></a>Wymagania wstępne dotyczące programu Microsoft Office nie są zainstalowane.
 .NET Framework, można dodać [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]i podstawowe zestawy międzyoperacyjne pakietu Office do pakiet Instalatora jako warunki wstępne, które zostały wdrożone za pomocą rozwiązania pakietu Office. Aby uzyskać informacje o sposobie instalowania podstawowych zestawów międzyoperacyjnych, zobacz [Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/configuring-a-computer-to-develop-office-solutions.md) i [jak: Instalowanie podstawowych zestawów międzyoperacyjnych pakietu Office](../vsto/how-to-install-office-primary-interop-assemblies.md).

## <a name="publish-using-localhost-can-cause-installation-problems"></a>Publikowanie za pomocą nazwy "Host_lokalny" może spowodować problemy z instalacją
 Kiedy używać "<http://localhost>" jako lokalizacji publikowania lub instalacji w przypadku rozwiązań na poziomie dokumentu, **Kreatora publikacji** nie konwertuje ciąg na nazwę komputera rzeczywistych. W takim przypadku można zainstalować rozwiązania na komputerze deweloperskim. Aby wdrożonymi rozwiązaniami, które używają usług IIS na komputerze deweloperskim, należy użyć w pełni kwalifikowanej nazwy dla wszystkich lokalizacji HTTP/HTTPS/FTP zamiast nazwy localhost.

## <a name="cached-assemblies-are-loaded-instead-of-updated-assemblies"></a>Buforowane zestawy są ładowane zamiast zaktualizowane zestawy
 Fusion, moduł ładujący zestawu .NET Framework, ładuje pamięci podręcznej kopię zestawy ścieżki wyjściowej projektu jest w sieciowym udziale plików, zestaw zostanie podpisany silną nazwą i nie zmienia wersji zestawu dostosowywania. Jeśli aktualizujesz zestaw, który spełnia te warunki, aktualizacja nie będzie wyświetlane przy następnym uruchomieniu projektu, ponieważ kopia pamięci podręcznej jest ładowana.

 Visual Studio można skonfigurować tak, aby Fusion pobierze zestawy każdorazowym uruchomieniu projektu.

### <a name="to-download-assemblies-instead-of-loading-cached-copies"></a>Aby pobrać zestawy zamiast ładowania zbuforowane kopie

1. Na pasku menu wybierz **projektu**, _ProjectName_**właściwości**.

2. Na **aplikacji** wybierz **informacje o zestawie**.

3. W pierwszym **wersji zestawu** Wprowadź znak gwiazdki (\*), a następnie wybierz **OK** przycisku.

   Po zmianie wersji zestawu, można kontynuować podpisać zestaw silną nazwą, a Fusion załaduje najbardziej aktualną wersję dostosowania.

## <a name="installation-fails-when-the-uri-has-characters-that-arent-us-ascii"></a>Instalacja kończy się niepowodzeniem, jeśli identyfikator URI zawiera znaki, które nie są US-ASCII
 Podczas publikowania rozwiązania do pakietu Office do lokalizacji HTTP/HTTPS/FTP, ścieżka nie może zawierać dowolne znaki Unicode, których nie ma w US-ASCII. Znaki te mogą spowodować niespójne działanie Instalatora. Znaki US-ASCII ścieżki instalacji.

## <a name="prompt-to-manually-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Zostanie wyświetlony monit o ręczne odinstalowanie, podczas publikowania i zainstalowanie rozwiązania na komputerze deweloperskim
 W przypadku tworzenia rozwiązań pakietu Office, skompilowanych wersji jest automatycznie rejestrowane. Jeśli masz wcześniej opublikowana i zainstalowana na tym samym rozwiązaniu na komputerze dewelopera, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] wykryje, że ścieżka instalacji dla opublikowanej wersji i skompilowanych wersji różnią się po rozwiązaniu obok został opracowany, odbudować lub opublikowane. Komunikat o błędzie jest wyświetlany komunikat "nie można zainstalować dostosowania, ponieważ inna wersja jest obecnie zainstalowany i nie można uaktualnić z tej lokalizacji." Klucze rejestru są aktualizowane, zawsze wtedy, gdy rozwiązanie zostanie ponownie skompilowany. W związku z tym należy odinstalować poprzednią wersję, przed opublikowaniem, debugować lub uruchomić nową wersję.

 Aby zapobiec wyświetlaniu wiadomości, Utwórz kolejne konto użytkownika na komputerze dewelopera, aby przetestować wdrożenie. Jako alternatywę można odinstalować wersję z listy zainstalowanych programów na komputerze przed obok publikowania, debugowanie lub ponownie skompiluj rozwiązanie.

## <a name="uncaught-exception-or-method-not-found-error-when-you-install-a-solution"></a>Nieprzechwycony wyjątek lub metoda nie znaleziono błąd podczas instalowania rozwiązania
 Po zainstalowaniu rozwiązania dla pakietu Office poprzez otwarcie manifestu wdrażania ( *.vsto* pliku), mogą być wyświetlane Office aplikacji, dokument lub skoroszyt, komunikaty o błędach dla następujących warunków:

- Nie można odnaleźć metody.

- MissingMethodException.

- Nieprzechwycony wyjątek.

  Aby uniknąć tych komunikatów o błędach, należy zainstalować rozwiązanie przez uruchomienie programu instalacyjnego.

  Po zainstalowaniu rozwiązania bez konieczności uruchamiania programu instalacyjnego Instalatora nie sprawdzaj lub instalowanie wymagań wstępnych. Program instalacyjny sprawdza, czy poprawną wersję wymagań wstępnych i instaluje je w razie potrzeby.

## <a name="manifest-registry-keys-for-add-ins-change-after-an-installshield-limited-edition-project-is-built"></a>Manifest kluczy rejestru dla dodatków zmian, po utworzeniu projektu programu InstallShield Limited Edition
 Klucz rejestru manifestu, który jest częścią konfiguracji dodatku narzędzi VSTO dla programów czasami zmian z *.vsto* do *. dll.manifest* podczas kompilowania projektu programu InstallShield Limited Edition.

 Aby obejść ten problem, Utwórz projekt InstallShield Limited Edition w różne rozwiązania, lub użyj CompanyName.AddinName jako wartość klucza rejestru, który zawiera nazwę dodatku narzędzi VSTO.

## <a name="the-clickonce-installer-for-your-office-solution-doesnt-install-the-primary-interop-assemblies"></a>Instalatora ClickOnce dla rozwiązania pakietu Office nie instaluje podstawowe zestawy międzyoperacyjne
 Po uruchomieniu programu instalacyjnego, który tworzy ClickOnce dla rozwiązania pakietu Office, Instalator podstawowe zestawy międzyoperacyjne pakietu Office (PIA) działa tylko wtedy, gdy nie zestawy PIA są już zainstalowane.

 Jeśli program instalacyjny nie poprawnie zainstalować PIA, zainstaluj je ręcznie, uruchamiając plik Instalatora, który nosi nazwę *o2007pia.msi* z katalogu instalacyjnego.

## <a name="reinstall-office-solutions-causes-an-argument-out-of-range-exception"></a>Zainstaluj ponownie Office solutions powoduje, że argument wyjątek poza zakresem
 Podczas ponownej instalacji rozwiązania do pakietu Office, <xref:System.ArgumentOutOfRangeException> wyjątek może pojawić się następujący komunikat o błędzie: Określony argument jest poza zakresem prawidłowych wartości.

 Taka sytuacja ma miejsce, jeśli różni się wielkość liter w wyrazie adresu URL dla lokalizacji instalacji. Na przykład ten błąd zostanie wyświetlony po zainstalowaniu rozwiązania do pakietu Office z [ http://fabrikam.com/ExcelSolution.vsto ](http://fabrikam.com/ExcelSolution.vsto) po raz pierwszy, a następnie wykorzystania [ http://fabrikam.com/excelsolution.vsto ](http://fabrikam.com/excelsolution.vsto) po raz drugi.

 Aby uniknąć komunikat, należy użyć tą samą wielkością liter podczas instalowania rozwiązania dla pakietu Office.

## <a name="cant-install-a-clickonce-solution-by-opening-the-deployment-manifest-from-the-web"></a>Nie można zainstalować rozwiązania ClickOnce przez otwarcie manifestu wdrażania z sieci web
 Użytkownicy mogą zainstalować rozwiązań pakietu Office poprzez otwarcie manifestu wdrażania z sieci web. Jednak niektóre instalacje programu Internetowe usługi informacyjne (IIS) block *.vsto* rozszerzenie nazwy pliku. Przed użyciem wdrożyć rozwiązanie Office, w usługach IIS należy zdefiniować typ MIME.

 Aby uzyskać informacje o tym, jak zdefiniować typ MIME w usługach IIS 7, zobacz [dodać typ MIME (IIS7)](http://technet.microsoft.com/library/cc725608(WS.10).aspx).

 Ustaw rozszerzenie **.vsto** i typ MIME do **application/x-ms-vsto**.

## <a name="see-also"></a>Zobacz także

- [Rozwiązywanie problemów z wdrożeniami ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
- [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)
