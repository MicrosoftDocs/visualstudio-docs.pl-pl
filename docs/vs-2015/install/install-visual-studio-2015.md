---
title: Instalowanie programu Visual Studio 2015 | Dokumenty firmy Microsoft
titleSuffix: ''
ms.date: 04/15/2020
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- Visual Studio, installing
- installing Visual Studio
- server installations [Visual Studio]
- Setup [Visual Studio]
- install Visual Studio
- visual studio installer
ms.assetid: da049020-cfda-40d7-8ff4-7492772b620f
caps.latest.revision: 183
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 1bfc573c30281e5bc976ee25ea3a80a2f874ab25
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81445080"
---
# <a name="install-visual-studio-2015"></a>Instalowanie programu Visual Studio 2015

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta strona zawiera szczegółowe informacje ułatwiające instalowanie **programu Visual Studio 2015**, naszego zintegrowanego pakietu narzędzi zwiększających produktywność dla deweloperów. Zamieściliśmy również linki, aby szybko uzyskać informacje o [funkcjach,](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-version-history) [wymaganiach systemowych,](https://docs.microsoft.com/visualstudio/productinfo/vs2015-sysrequirements-vs) [plikach do pobrania](https://visualstudio.microsoft.com/vs/older-downloads/)i innych.

## <a name="quick-links"></a>Szybkie linki

Zanim zagłębimy się w szczegóły, oto lista naszych najczęściej wymaganych linków.

|||
|------------------|----------------|
|![Pobierz program Visual Studio](../install/media/downloads.png "Pliki do pobrania") |**Pliki do pobrania**: Aby zainstalować program Visual Studio 2015, można pobrać plik wykonywalny produktu ze strony [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) (wymagana subskrypcja) lub użyć nośnika instalacyjnego z produktu w pudełku. [Dowiedz się więcej o pobieraniu bieżących lub poprzednich wersji programu Visual Studio.](https://www.visualstudio.com/vs/older-downloads/)|
|![Dowiedz się więcej o funkcjach](../install/media/features.png "Funkcje") |**Funkcje**: Aby dowiedzieć się więcej o funkcjach programu Visual Studio 2015, zobacz informacje o wersji [rtm](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-rtm-vs), [aktualizacja 1,](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update1-vs) [aktualizacja 2](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update2-vs)i [aktualizacja 3](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update3-vs).|
|![Wyświetlanie wymagań systemowych](../install/media/system-requirements.png "Wymagania systemu") |**Wymagania systemowe:** Aby wyświetlić wymagania systemowe dla każdej wersji programu Visual Studio 2015, zobacz stronę [Kierowania i zgodności platformy programu Visual Studio 2015.](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs)|
|![Znajdź klucz produktu](../install/media/product-keys.png "Klucze produktu") |**Klucze produktu:** Aby zlokalizować klucz produktu, zobacz [jak: Znajdź klucz produktu programu Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md) tematu.|
|![Dowiedz się więcej o licencjonowaniu](../install/media/licensing.png "Licencjonowanie") |**Licencjonowanie:** Aby dowiedzieć się więcej o opcjach licencjonowania zarówno dla klientów indywidualnych, jak i korporacyjnych, zobacz [oficjalny dokument dotyczący licencjonowania programu Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=13350).|

## <a name="default-vs-custom-setup"></a><a name="custom"></a>Ustawienia domyślne a niestandardowe
 Podczas instalowania programu Visual Studio 2015 można uwzględnić lub wykluczyć składniki, które będą używane codziennie. Oznacza to, że instalacja domyślna będzie często mniejsza i instaluje się szybciej niż instalacja niestandardowa. Oznacza to również, że wiele składników, które zostały zainstalowane domyślnie w poprzednich wersjach są teraz uważane za składniki niestandardowe, które należy jawnie wybrać w tej wersji.

 ![Okno dialogowe ustawień programu Visual Studio 2015](../ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

 Składniki niestandardowe obejmują visual c++, Visual F#, SQL Server Data Tools, wieloplatformowe narzędzia mobilne i zestawy SDK oraz zestawy SDK innych firm i rozszerzenia. Możesz zainstalować dowolny z niestandardowych składników w późniejszym czasie, jeśli nie wybierzesz ich podczas początkowej konfiguracji.

> [!NOTE]
> Instalacja niestandardowa automatycznie zawiera składniki, które znajdują się w instalacji domyślnej.

 Pełna lista składników niestandardowych jest następująca:

|Zestawy funkcji|Składniki|
|------------------|----------------|
|**Aktualizacje**|Visual Studio 2015 Update 3|
|**Języki programowania**|Visual C++<br />Visual F#<br />Python Tools for Visual Studio|
|**Tworzenie systemu Windows i sieci Web**|Narzędzia do publikowania w witrynie Kliknij przycisku<br />LightSwitch<br />Narzędzia deweloperskie pakietu Microsoft Office<br />Narzędzia danych programu Microsoft SQL Server<br /> Narzędzia microsoft web developer<br />Narzędzia programu PowerShell dla programu Visual Studio (3rd Party)<br />Zestaw deweloperski Silverlight<br />Uniwersalne narzędzia do tworzenia aplikacji systemu Windows<br />Narzędzia i zestaw SDK systemu Windows 10<br />Narzędzia dla systemów Windows 8.1 i Windows Phone 8.0/8.1<br />Narzędzia i zestaw SDK systemu Windows 8.1|
|**Rozwój mobilny między platformami**|C#/.NET (Xamarin)<br />HTML/JavaScript (Apache Cordova)<br />Visual C++ Mobile Development dla iOS / Android<br />Clang with Microsoft CodeGen|
|**Typowe narzędzia i zestawy programistyczne**|Natywny zestaw rozwoju Androida (3rd Party)<br /> Android SDK [3rd Party]<br />Interfejsy API instalatora sdk systemu Android (3rd Party)<br />Apache Ant (trzecia strona)<br /> Zestaw deweloperski Java SE (strona trzecia)<br /> Joyent Node.js (trzecia strona)|
|**Typowe narzędzia**|Git dla Windows (3rd Party)<br />Rozszerzenie GitHub dla programu Visual Studio (3rd Party)<br /> Narzędzia rozszerzalności programu Visual Studio|

## <a name="install-visual-studio"></a><a name="installing"></a>Instalowanie programu Visual Studio
 Program Visual Studio można zainstalować przy użyciu nośnika instalacyjnego (DVD), korzystając z usługi subskrypcji programu Visual Studio z [witryny sieci](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) Web My.VisualStudio.com, pobierając instalatora sieci Web z [witryny usługi Visual Studio Downloads](https://visualstudio.microsoft.com/vs/older-downloads/) lub tworząc układ instalacji w trybie offline (więcej informacji można znaleźć na stronie [Tworzenie instalacji w trybie offline programu Visual Studio).](../install/create-an-offline-installation-of-visual-studio.md)

> [!IMPORTANT]
> Do zainstalowania potrzebne [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]są poświadczenia administratora . Jednak nie są one potrzebne [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] do użycia po zainstalowaniu go.

 Konto administratora lokalnego musi mieć włączone następujące uprawnienia, aby zainstalować wszystko w programie Visual Studio.

|Nazwa wyświetlana obiektu zasad lokalnych|Prawo użytkownika|
|--------------------------------------|----------------|
|Pliki kopii zapasowych i katalogi|SeBackupPrivilege|
|Debugowanie programów|SeDebugPrivilege|
|Zarządzanie dziennikiem inspekcji i zabezpieczeń|SeSecurityPrivilege|

 Aby uzyskać więcej informacji na temat tego wymagania konta administratora lokalnego, zobacz artykuł z bazy wiedzy Knowledge Base, [instalacja programu SQL Server kończy się niepowodzeniem, jeśli konto Instalatora nie ma określonych praw użytkownika](https://support.microsoft.com/kb/2000257).

### <a name="use-installation-media"></a><a name="BKMK_Media"></a>Korzystanie z nośnika instalacyjnego
 Aby [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]zainstalować program , w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] katalogu głównym na nośniku instalacyjnym, uruchom plik instalacyjny dla żądanej wersji:

|Wersja|Plik instalacyjny|
|-------------|-----------------------|
|Visual Studio Enterprise|vs_enterprise.exe|
|Visual Studio Professional|vs_professional.exe|
|Visual Studio Community|vs_community.exe|

### <a name="download-from-the-product-website"></a><a name="BKMK_Website"></a>Pobierz ze strony produktu
 Odwiedź stronę [Pobieranie programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) i wybierz odpowiednią wersję programu Visual Studio.

### <a name="download-from-your-subscription-service"></a>Pobieranie z usługi subskrypcji
 Odwiedź [stronę My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) i wybierz odpowiednią wersję programu Visual Studio.

### <a name="create-an-offline-installation-layout"></a><a name="BKMK_Offline"></a>Tworzenie układu instalacji w trybie offline
 Jeśli nie masz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nośnika instalacyjnego lub nie masz subskrypcji programu Visual [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Studio lub nie chcesz instalować za pomocą instalatora sieci web, możesz przeprowadzić instalację "rozłączony", tworząc tak zwany układ instalacji w trybie offline. Aby uzyskać więcej informacji, zobacz [tworzenie instalacji w trybie offline programu Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) strony.

## <a name="deploy-visual-studio-in-an-enterprise"></a><a name="enterprise"></a>Wdrażanie programu Visual Studio w przedsiębiorstwie
 Aby uzyskać informacje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dotyczące wdrażania za pośrednictwem sieci, zobacz [Przewodnik dla administratorów programu Visual Studio](../install/visual-studio-administrator-guide.md).

### <a name="install-visual-studio-in-a-virtualized-environment"></a><a name="BKMK_Virtualized"></a>Instalowanie programu Visual Studio w środowisku zwirtualizowanym
 **Problemy z obrazem z funkcji Hyper-V**

 Jeśli uruchamiasz system Windows Server 2008 R2 z włączoną funkcją Hyper-V oraz akcelerowaną kartą grafiki, może wystąpić spowolnienie systemu.

 Aby uzyskać więcej informacji, zobacz [Wydajność wideo może się zmniejszyć, gdy na komputerze z systemem Windows Server 2008 lub Windows Server 2008 R2 jest włączona rola funkcji Hyper-V i zainstalowano przyspieszoną kartę graficzną](https://support.microsoft.com/kb/961661).

 **Emulowanie urządzeń z funkcji Hyper-V**

 Po zainstalowaniu programu Visual Studio 2015 na rzeczywistym sprzęcie bez wirtualizacji można wybrać funkcje umożliwiające emulację urządzeń z systemem Windows i Android przy użyciu funkcji Hyper-V. Po zainstalowaniu w funkcji Hyper-V nie będzie można emulować urządzeń z systemem Windows lub Android. Dzieje się tak, ponieważ emulatory są same maszyny wirtualne i obecnie nie można hostować maszyny wirtualnej wewnątrz innej maszyny wirtualnej. Obejście polega na tym, aby mieć prawdziwe urządzenia z systemem Windows lub Android, na których można bezpośrednio wdrożyć i debugować aplikację.

## <a name="install-optional-components"></a><a name="optionalComponents"></a>Zainstaluj komponenty opcjonalne
 Jeśli chcesz zainstalować składniki, które mogą nie zostać wybrane podczas oryginalnej instalacji, należy skorzystać z poniższej procedury.

#### <a name="to-install-optional-components"></a>Aby zainstalować składniki opcjonalne

1. W **Panelu sterowania**na stronie Programy i **funkcje** wybierz wersję produktu, do której chcesz dodać jeden lub więcej składników, a następnie wybierz pozycję **Zmień**.

2. W Kreatorze instalacji wybierz pozycję **Modyfikuj**, a następnie wybierz składniki, które chcesz zainstalować.

3. Wybierz **pozycję Dalej**, a następnie postępuj zgodnie z pozostałymi instrukcjami.

## <a name="install-offline-help-content"></a><a name="helpContent"></a>Instalowanie zawartości Pomocy w trybie offline
 Po zainstalowaniu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]można pobrać dodatkową zawartość Pomocy, aby była dostępna w trybie offline.

#### <a name="to-install-or-uninstall-help-content"></a>Aby zainstalować lub odinstalować zawartość pomocy

1. Na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pasku menu wybierz pozycję **Pomoc**, **Dodaj i usuń zawartość Pomocy**.

2. Na karcie **Zarządzanie zawartością** **w przeglądarce Pomocy firmy Microsoft**wybierz źródło instalacji zawartości Pomocy.

3. Jeśli szukasz określonej kolekcji Pomocy, wprowadź nazwę lub słowo kluczowe w polu tekstowym **Wyszukaj,** a następnie naciśnij **klawisz Enter**.

4. Obok nazwy kolekcji Pomoc wybierz łącze **Dodaj** lub **Usuń.**

5. Kliknij przycisk **Aktualizuj.**

   Aby uzyskać więcej informacji na temat instalowania lub wdrażania Pomocy w trybie offline, zobacz [Przewodnik administratora Podglądu pomocy](../ide/help-viewer-administrator-guide.md).

## <a name="check-for-service-releases-and-product-updates"></a><a name="serviceReleases"></a>Sprawdź dostępność wersji usług i aktualizacji produktów
 Ponieważ nie wszystkie rozszerzenia są zgodne, program Visual Studio nie uaktualnia automatycznie rozszerzeń podczas uaktualniania z poprzednich wersji. Należy ponownie zainstalować rozszerzenia z [programu Visual Studio Marketplace](https://marketplace.visualstudio.com/) lub od wydawcy oprogramowania.

#### <a name="to-automatically-check-for-service-releases"></a>Aby automatycznie sprawdzić, czy są dostępne poprawki

1. Na pasku menu wybierz pozycję **Narzędzia**, **Opcje**.

2. W oknie dialogowym **Opcje** rozwiń węzeł **Środowisko**, a następnie wybierz pozycję **Rozszerzenia i aktualizacje**. Upewnij się, że pole wyboru **Automatycznie sprawdzaj aktualizacje** jest zaznaczone, a następnie wybierz przycisk **OK**.

## <a name="register-visual-studio"></a>Zarejestruj program Visual Studio

1. Na pasku menu wybierz pozycję **Pomoc**, **Informacje**.

     Okno dialogowe **Informacje** zawiera numer identyfikacyjny produktu (PID). Do zarejestrowania produktu potrzebne są poświadczenia pid i konta systemu Windows (takie jak hotmail lub Outlook.com adres e-mail i hasło).

2. Na pasku menu wybierz pozycję **Pomoc**, **Zarejestruj produkt**.

## <a name="repair-visual-studio"></a><a name="repair"></a>Napraw program Visual Studio

#### <a name="to-repair-visual-studio"></a>Aby naprawić program Visual Studio

1. W **Panelu sterowania**na stronie Programy i **funkcje** wybierz wersję produktu, którą chcesz naprawić, a następnie wybierz pozycję **Zmień**.

2. W kreatorze instalacji wybierz pozycję **Napraw,** wybierz pozycję **Dalej**, a następnie postępuj zgodnie z pozostałymi instrukcjami.

#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>Aby naprawić program Visual Studio w trybie cichym lub pasywnym (czyli do naprawy ze źródła)

1. Na komputerze, na którym jest zainstalowany program Visual Studio, otwórz wiersz polecenia systemu Windows.

2. Wprowadź następujące parametry:

     *Plik instalacyjny* \> \< `/quiet|/passive` *DVDRoot* \\ <`norestart`> [/ ]/`Repair`

## <a name="troubleshoot-an-installation"></a><a name="troubleshooting"></a>Rozwiązywanie problemów z instalacją
 Skorzystaj z tych zasobów, aby uzyskać pomoc dotyczącą problemów z instalacją i instalacją:

- [Forum instalacji i instalacji programu Visual Studio.](https://social.msdn.microsoft.com/Forums/en-US/vssetup/threads) Przejrzyj pytania i odpowiedzi od innych użytkowników w społeczności programu Visual Studio. Jeśli nie możesz znaleźć potrzebnych informacji, zadaj własne pytania.

- [Uzyskaj pomoc dotyczącą programu Visual Studio](https://visualstudio.microsoft.com/vs/support/vs2015/). Znajdź artykuły bazy wiedzy (KB) i dowiedz się, jak skontaktować się z pomocą techniczną firmy Microsoft, aby uzyskać informacje na temat problemów z instalacją programu Visual Studio.

## <a name="related-topics"></a><a name="relatedTopics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Tworzenie instalacji programu Visual Studio w trybie offline](../install/create-an-offline-installation-of-visual-studio.md)|W tym artykule opisano sposób instalowania programu Visual Studio, gdy nie masz połączenia z Internetem.
|[Instalowanie wersji programu Visual Studio obok siebie](../install/install-visual-studio-versions-side-by-side.md)|Zawiera informacje dotyczące sposobu instalowania wielu wersji programu Visual Studio na tym samym komputerze.|
|[Instalowanie programu Visual Studio za pomocą parametrów wiersza polecenia](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)|Wyświetla listę parametrów wiersza polecenia, których można użyć podczas instalowania programu Visual Studio z wiersza polecenia.|
|[Odinstalowywanie programu Visual Studio](../install/uninstall-visual-studio.md)|W tym artykule opisano sposób odinstalowywania programu Visual Studio.|
|[Przewodnik po administratorze programu Visual Studio](../install/visual-studio-administrator-guide.md)|Zawiera informacje dotyczące opcji wdrażania programu Visual Studio.|
|[Biblioteka obrazów programu Visual Studio](../designers/the-visual-studio-image-library.md)|Zawiera informacje dotyczące sposobu instalowania grafiki, która może być używana w aplikacjach Visual Studio.|
|[Wprowadzenie do programowania w programie Visual Studio](../ide/get-started-developing-with-visual-studio.md)|Zawiera informacje i łącza, które mogą pomóc w bardziej efektywnym korzystaniu z programu Visual Studio.|

## <a name="see-also"></a>Zobacz też

- [Visual Studio — logowanie](../ide/signing-in-to-visual-studio.md)
