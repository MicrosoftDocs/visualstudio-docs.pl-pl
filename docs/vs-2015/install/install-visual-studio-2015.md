---
title: Instalowanie programu Visual Studio 2015 | Dokumentacja firmy Microsoft
titleSuffix: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: a31bc328c20aada21b05edeef61886d57e914165
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298053"
---
# <a name="install-visual-studio-2015"></a>Instalowanie programu Visual Studio 2015

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta strona zawiera szczegółowe informacje ułatwiające zainstalowanie **programu Visual Studio 2015**, naszego zintegrowanego pakietu narzędzi zwiększających produktywność dla deweloperów. Dołączono także linki umożliwiające szybkie uzyskanie informacji na temat [funkcji](https://www.visualstudio.com/news/vs2015-vs.aspx), [wersji](https://go.microsoft.com/fwlink/?LinkID=242142), [wymagań systemowych](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs), [plików do pobrania](https://go.microsoft.com/fwlink/?LinkId=517106)itp.

## <a name="quick-links"></a>Szybkie linki

Przed rozpoczęciem omawiania szczegółach poniżej przedstawiono listę nasze najczęściej żądanych łączy.

|||
|------------------|----------------|
|![Pobierz program Visual Studio](../install/media/downloads.png "Pliki do pobrania") |**Pobieranie**: Aby zainstalować program Visual Studio 2015, można pobrać plik wykonywalny produktu ze strony [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) (wymagana jest subskrypcja) lub użyć nośnika instalacyjnego z produktu opakowanego. [Dowiedz się więcej na temat pobierania bieżących lub wcześniejszych wersji programu Visual Studio](https://www.visualstudio.com/vs/older-downloads/).|
|![Dowiedz się więcej o funkcjach](../install/media/features.png "Funkcje") |**Funkcje**: Aby dowiedzieć się więcej o funkcjach w programie Visual Studio 2015, zapoznaj się z informacjami o wersji [RTM](https://www.visualstudio.com/news/vs2015-vs), [Update 1](https://www.visualstudio.com/news/vs2015-update1-vs), [Update 2](https://www.visualstudio.com/news/vs2015-update2-vs)i [Update 3](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs).|
|![Dowiedz się, co znajduje się w każdej jednostce SKU](../install/media/sku.png "SKU") |**Jednostki SKU**: Aby dowiedzieć się, co jest dostępne w poszczególnych wersjach programu visual Studio 2015, zobacz stronę [porównanie ofert programu Visual Studio](https://go.microsoft.com/fwlink/?LinkID=242142) .|
|![Wyświetl wymagania systemowe](../install/media/system-requirements.png "Wymagania systemowe") |**Wymagania systemowe**: Aby wyświetlić wymagania systemowe dla każdej wersji programu Visual Studio 2015, zobacz stronę [zgodności programu Visual Studio 2015](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs) .|
|![Lokalizowanie klucza produktu](../install/media/product-keys.png "Klucze produktów") |**Klucze produktu**: aby znaleźć klucz produktu, zobacz temat [jak znaleźć klucz produktu Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md) .|
|![Dowiedz się więcej o licencjonowaniu](../install/media/licensing.png "Licencjonowanie") |**Licencjonowanie**: Aby dowiedzieć się więcej o opcjach licencjonowania dla klientów indywidualnych lub dla przedsiębiorstw, zobacz oficjalny dokument dotyczący [licencjonowania programu Visual Studio i MSDN](https://www.microsoft.com/download/details.aspx?id=13350) .|

## <a name="custom"></a>Domyślne a Konfiguracja niestandardowa
 Podczas instalowania programu Visual Studio 2015 można uwzględnić lub wykluczyć składniki, które są używane codziennie. Oznacza to, czy domyślnej instalacji będą często mniejsze i instalowany szybciej, niż Instalacja niestandardowa. Oznacza to również, że wiele składników, które były instalowane domyślnie w poprzednich wersjach, teraz są traktowane jako składników niestandardowych, które jawnie należy wybrać w tej wersji.

 ![Okno dialogowe Instalatora programu Visual Studio 2015](../ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

 Składniki niestandardowe obejmują Visual C++, Visual F#, SQL Server Data Tools, narzędzia mobilnych dla wielu platform i zestawów SDK i innych firm zestawy SDK i rozszerzeń. Można zainstalować dowolny niestandardowych składników w późniejszym czasie, jeśli nie zaznaczysz je podczas początkowej konfiguracji.

> [!NOTE]
> Instalacja niestandardowa automatycznie zawiera składniki, które znajdują się w przypadku instalacji domyślnej.

 Pełną listę składników niestandardowych jest następująca:

|Zestawy funkcji|Składniki|
|------------------|----------------|
|**Aktualizacje**|Visual Studio 2015 Update 3|
|**Języki programowania**|Visual C++<br />Visual F#<br />Narzędzia języka Python dla programu Visual Studio|
|**Programowanie dla systemu Windows i sieci Web**|Narzędzia publikowania ClickOnce<br />LightSwitch<br />Microsoft Office Developer Tools<br />Microsoft SQL Server Data Tools<br /> Narzędzia Microsoft Web Developer Tools<br />Narzędzia programu PowerShell dla programu Visual Studio (strona 3)<br />Zestaw deweloperski dodatku Silverlight<br />Narzędzia do tworzenia aplikacji Windows Universal<br />Narzędzia systemu Windows 10 i zestawy SDK<br />Windows 8.1 i Windows Phone 8.0/8.1 narzędzi<br />Windows 8.1, narzędzia i zestawy SDK|
|**Programowanie aplikacji mobilnych na wiele platform**|C# / .NET (Xamarin)<br />HTML/JavaScript (Apache Cordova)<br />Mobile środowiska deweloperskiego Visual C++ dla systemu iOS / Android<br />Clang with Microsoft CodeGen|
|**Popularne Narzędzia i zestawy SDK**|Dla systemu android Native Development Kit (strona 3)<br /> Zestaw SDK systemu android [Strona 3]<br />Interfejsy API Instalator zestawu android SDK (strona 3)<br />Apache Ant (strona 3)<br /> Java SE Development Kit (strona 3)<br /> Joyent Node.js (strona 3)|
|**Popularne narzędzia**|Git Pro Windows (strona 3)<br />Rozszerzenie GitHub dla programu Visual Studio (strona 3)<br /> Visual Studio Extensibility Tools|

## <a name="installing"></a>Instalowanie programu Visual Studio
 Program Visual Studio można zainstalować przy użyciu nośnika instalacyjnego (DVD), korzystając z usługi subskrypcji programu Visual Studio z witryny sieci Web [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) , pobierając Instalatora sieci Web z witryny internetowej [pobierania programu Visual Studio](https://go.microsoft.com/fwlink/?LinkId=517106) lub tworząc układ instalacji w trybie offline (Aby uzyskać więcej informacji, zobacz stronę [Tworzenie instalacji w trybie offline programu Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) ).

> [!IMPORTANT]
> Musisz mieć poświadczenia administratora, aby zainstalować [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Jednak nie są one potrzebne do używania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] po ich zainstalowaniu.

 Konto administratora lokalnego musi mieć następujące uprawnienia, które są włączone, aby zainstalować wszystkie elementy w programie Visual Studio.

|Nazwa wyświetlana obiektu lokalnych zasad|Prawa użytkownika|
|--------------------------------------|----------------|
|Tworzenie kopii zapasowych plików i katalogów|SeBackupPrivilege|
|Debugowanie programów|SeDebugPrivilege|
|Zarządzaj dziennikiem inspekcji i zabezpieczeń|SeSecurityPrivilege|

 Aby uzyskać więcej informacji na temat tego wymagania dotyczącego konta administratora lokalnego, zobacz artykuł w bazie wiedzy [SQL Server Instalacja nie powiedzie się, jeśli konto instalatora nie ma określonych praw użytkownika](https://support.microsoft.com/kb/2000257).

### <a name="BKMK_Media"></a>Korzystanie z nośnika instalacyjnego
 Aby zainstalować [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], w katalogu głównym na nośniku instalacyjnym programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Uruchom plik instalacyjny dla potrzebnej wersji:

|Wersja|Plik instalacyjny|
|-------------|-----------------------|
|Visual Studio Enterprise|vs_enterprise.exe|
|Visual Studio Professional|vs_professional.exe|
|Visual Studio Community|vs_community.exe|

### <a name="BKMK_Website"></a>Pobieranie z witryny sieci Web produktu
 Odwiedź stronę [pliki do pobrania programu Visual Studio](https://go.microsoft.com/fwlink/?LinkId=517106) i wybierz żądaną wersję programu Visual Studio.

### <a name="downloading-from-your-subscription-service"></a>Pobieranie z usługi w subskrypcji
 Odwiedź stronę [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) i wybierz żądaną wersję programu Visual Studio.

### <a name="BKMK_Offline"></a>Tworzenie układu instalacji w trybie offline
 Jeśli nie masz nośnika instalacyjnego programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lub nie masz subskrypcji programu Visual Studio lub nie chcesz instalować [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] przy użyciu Instalatora sieci Web, możesz wykonać instalację "Rozłączono", tworząc informacje o tym, co jest znane jako układ instalacji w trybie offline. Aby uzyskać więcej informacji, zobacz stronę [Tworzenie instalacji w trybie offline programu Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) .

## <a name="enterprise"></a>Wdrażanie programu Visual Studio w przedsiębiorstwie
 Informacje o sposobach wdrażania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] za pośrednictwem sieci znajdują się w [podręczniku administratora programu Visual Studio](../install/visual-studio-administrator-guide.md).

### <a name="BKMK_Virtualized"></a>Instalowanie programu Visual Studio w środowisku zwirtualizowanym
 **Problemy z wideo przy użyciu funkcji Hyper-V**

 Jeśli uruchamiasz system Windows Server 2008 R2 z włączoną funkcją Hyper-V oraz akcelerowaną kartą grafiki, może wystąpić spowolnienie systemu.

 Aby uzyskać więcej informacji, zobacz następującą stronę w witrynie sieci Web firmy Microsoft: [wydajność wideo może ulec zmniejszeniu, gdy komputer z systemem Windows server 2008 lub Windows server 2008 R2 ma włączoną rolę funkcji Hyper-V i zainstalowano przyspieszoną kartę graficzną](https://go.microsoft.com/fwlink/?LinkID=231084).

 **Emulacja urządzeń przy użyciu funkcji Hyper-V**

 Po zainstalowaniu programu Visual Studio 2015 na sprzęt rzeczywisty bez wirtualizacji, można wybrać funkcje, które umożliwiają emulacji systemu Windows oraz urządzeń z systemem Android przy użyciu funkcji Hyper-V. Po zainstalowaniu w funkcji Hyper-V, nie będzie można emulować Windows lub urządzeń z systemem Android. Jest to spowodowane emulatorów znajdują się maszyny wirtualne i obecnie nie można hostować Maszynę wirtualną w innej maszyny Wirtualnej. Obejście polega na rzeczywistych Windows lub urządzeń z systemem Android do których możesz bezpośrednio wdrażania i debugowania aplikacji.

## <a name="optionalComponents"></a>Instalowanie składników opcjonalnych
 Jeśli chcesz zainstalować składniki, które być może nie został wybrany podczas oryginalnej instalacji, należy użyć poniższej procedury.

#### <a name="to-install-optional-components"></a>Aby zainstalować składniki opcjonalne

1. W **Panelu sterowania**na stronie **programy i funkcje** wybierz wersję produktu, do której chcesz dodać jeden lub więcej składników, a następnie wybierz pozycję **Zmień**.

2. W Kreatorze instalacji wybierz **Modyfikuj**, a następnie wybierz składniki, które chcesz zainstalować.

3. Wybierz pozycję **dalej**, a następnie postępuj zgodnie z pozostałymi instrukcjami.

## <a name="helpContent"></a>Instalowanie zawartości pomocy w trybie offline
 Po zainstalowaniu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]można pobrać dodatkową zawartość pomocy, aby była dostępna w trybie offline.

#### <a name="to-install-or-uninstall-help-content"></a>Aby zainstalować lub odinstalować zawartość pomocy

1. Na pasku menu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wybierz **Pomoc**, **Dodaj i Usuń zawartość pomocy**.

2. Na karcie **Zarządzanie zawartością** w **Podgląd pomocy firmy Microsoft**wybierz źródło instalacji dla zawartości pomocy.

3. Jeśli szukasz konkretnej kolekcji pomocy, wprowadź nazwę lub słowo kluczowe w polu tekstowym **Wyszukaj** , a następnie naciśnij klawisz **Enter**.

4. Obok nazwy kolekcji pomocy wybierz łącze **Dodaj** lub **Usuń** .

5. Kliknij przycisk **Aktualizuj** .

   Więcej informacji o sposobie instalowania lub wdrażania pomocy w trybie offline można znaleźć w [podręczniku administratora podglądu pomocy](../ide/help-viewer-administrator-guide.md).

## <a name="serviceReleases"></a>Sprawdzanie wersji usług i aktualizacji produktu
 Ponieważ nie wszystkie rozszerzenia są zgodne, Visual Studio nie aktualizuje automatycznie rozszerzeń po uaktualnieniu z poprzednimi wersjami. Należy ponownie zainstalować rozszerzenia z [Visual Studio Marketplace](https://marketplace.visualstudio.com/) lub wydawcy oprogramowania.

#### <a name="to-automatically-check-for-service-releases"></a>Aby automatycznie sprawdzić, czy są dostępne poprawki

1. Na pasku menu wybierz **Narzędzia**, **Opcje**.

2. W oknie dialogowym **Opcje** rozwiń węzeł **środowisko**, a następnie wybierz pozycję **rozszerzenia i aktualizacje**. Upewnij się, że jest zaznaczone pole wyboru **automatycznie sprawdzaj dostępność aktualizacji** , a następnie wybierz przycisk **OK**.

## <a name="registering-visual-studio"></a>Rejestrowanie programu Visual Studio

1. Na pasku menu wybierz **Pomoc**, **informacje**.

     Okno dialogowe **informacje** pokazuje numer identyfikacyjny produktu (PID). Identyfikator PID i konta Windows poświadczenia (na przykład usługi Hotmail lub Outlook.com adres e-mail i hasło) musisz zarejestrować produkt.

2. Na pasku menu wybierz **Pomoc**, **zarejestruj produkt**.

## <a name="repair"></a>Naprawianie programu Visual Studio

#### <a name="to-repair-visual-studio"></a>Aby naprawić program Visual Studio

1. W **Panelu sterowania**na stronie **programy i funkcje** wybierz wydanie produktu, które chcesz naprawić, a następnie wybierz pozycję **Zmień**.

2. W Kreatorze instalacji wybierz pozycję **napraw**, wybierz pozycję **dalej**, a następnie postępuj zgodnie z pozostałymi instrukcjami.

#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>Aby naprawić program Visual Studio w trybie cichym lub pasywnym (czyli na naprawę ze źródła)

1. Na komputerze, na którym jest zainstalowany program Visual Studio, otwórz wiersz polecenia systemu Windows.

2. Wprowadź następujące parametry:

     *DVDRoot* \\< plik instalacyjny\> \</quiet&#124;/Passive > [/norestart]/Repair

## <a name="troubleshooting"></a>Rozwiązywanie problemów z instalacją
 Dzięki tym zasobom można uzyskać pomoc dotyczącą problemów z konfiguracją i instalacją:

- Forum instalacji [i instalacji programu Visual Studio](https://go.microsoft.com/fwlink/?LinkID=151190) . Przejrzyj pytania i odpowiedzi od innych użytkowników w społeczności programu Visual Studio. Jeśli nie możesz znaleźć potrzebnych informacji, zadaj własne pytania.

- [Pomoc techniczna firmy Microsoft witryny internetowej programu Visual Studio](https://go.microsoft.com/fwlink/?LinkID=251019) . Zapoznaj się z artykułami w bazie wiedzy (KB) i dowiedz się, jak się skontaktować z działem pomocy Microsoft, aby uzyskać informacje dotyczące problemów związanych z instalacją programu Visual Studio.

## <a name="relatedTopics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Tworzenie instalacji w trybie offline programu Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)|W tym artykule opisano sposób instalowania programu Visual Studio, gdy nie jest połączony z Internetem.
|[Instalowanie obok siebie różnych wersji programu Visual Studio](../install/install-visual-studio-versions-side-by-side.md)|Zawiera informacje dotyczące sposobu instalowania wielu wersji programu Visual Studio na tym samym komputerze.|
|[Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)|Zawiera listę parametrów wiersza polecenia, których można używać podczas instalowania programu Visual Studio z poziomu wiersza polecenia.|
|[Odinstalowywanie programu Visual Studio](../install/uninstall-visual-studio.md)|W tym artykule opisano sposób odinstalowywania programu Visual Studio.|
|[Podręcznik administratora programu Visual Studio](../install/visual-studio-administrator-guide.md)|Zawiera informacje dotyczące opcji wdrażania programu Visual Studio.|
|[Biblioteka obrazów programu Visual Studio](../designers/the-visual-studio-image-library.md)|Zawiera informacje dotyczące sposobu instalowania grafiki, która może być używana w aplikacjach Visual Studio.|
|[Wprowadzenie do programowania w programie Visual Studio](../ide/get-started-developing-with-visual-studio.md)|Zawiera informacje i linki, które mogą ułatwić bardziej efektywne wykorzystanie programu Visual Studio.|

## <a name="see-also"></a>Zobacz też

- [Logowanie do programu Visual Studio](../ide/signing-in-to-visual-studio.md)