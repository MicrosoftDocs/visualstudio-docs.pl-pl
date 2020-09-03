---
title: Zainstaluj program Visual Studio 2015 | Microsoft Docs
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
ms.openlocfilehash: d593625985924d8c8076e1bdd361ce4d08c1dfbc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548047"
---
# <a name="install-visual-studio-2015"></a>Instalowanie programu Visual Studio 2015

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta strona zawiera szczegółowe informacje ułatwiające zainstalowanie **programu Visual Studio 2015**, naszego zintegrowanego pakietu narzędzi zwiększających produktywność dla deweloperów. Dołączono także linki umożliwiające szybkie uzyskanie informacji na temat [funkcji](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-version-history), [wymagań systemowych](https://docs.microsoft.com/visualstudio/productinfo/vs2015-sysrequirements-vs), [plików do pobrania](https://visualstudio.microsoft.com/vs/older-downloads/)i innych.

## <a name="quick-links"></a>Szybkie linki

Zanim Dig się ze szczegółami, poniżej przedstawiono listę naszych najczęściej żądanych linków.

|Tytuł|Opis|
|------------------|----------------|
|![Pobierz program Visual Studio](../install/media/downloads.png "Pobieranie") |**Pobieranie**: Aby zainstalować program Visual Studio 2015, można pobrać plik wykonywalny produktu ze strony  [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) (wymagana jest subskrypcja) lub użyć nośnika instalacyjnego z produktu opakowanego. [Dowiedz się więcej na temat pobierania bieżących lub wcześniejszych wersji programu Visual Studio](https://www.visualstudio.com/vs/older-downloads/).|
|![Dowiedz się więcej o funkcjach](../install/media/features.png "Funkcje") |**Funkcje**: Aby dowiedzieć się więcej o funkcjach w programie Visual Studio 2015, zapoznaj się z informacjami o wersji [RTM](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-rtm-vs), [Update 1](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update1-vs), [Update 2](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update2-vs)i [Update 3](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update3-vs).|
|![Wyświetl wymagania systemowe](../install/media/system-requirements.png "Wymagania systemowe") |**Wymagania systemowe**: Aby wyświetlić wymagania systemowe dla każdej wersji programu Visual Studio 2015, zobacz stronę programu [Visual Studio 2015 platformy docelowej i zgodności](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs) .|
|![Lokalizowanie klucza produktu](../install/media/product-keys.png "Klucze produktów") |**Klucze produktu**: aby znaleźć klucz produktu, zobacz temat [jak znaleźć klucz produktu Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md) .|
|![Dowiedz się więcej o licencjonowaniu](../install/media/licensing.png "Licencjonowanie") |**Licencjonowanie**: Aby dowiedzieć się więcej o opcjach licencjonowania dla klientów indywidualnych lub dla przedsiębiorstw, zobacz [oficjalny dokument dotyczący licencjonowania programu Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=13350).|

## <a name="default-vs-custom-setup"></a><a name="custom"></a> Domyślne a Konfiguracja niestandardowa
 Po zainstalowaniu programu Visual Studio 2015 można uwzględnić lub wykluczyć składniki, które będą używane codziennie. Oznacza to, że instalacja domyślna będzie często mniejsza i instalowana szybciej niż instalacja niestandardowa. Oznacza to również, że wiele składników instalowanych domyślnie w poprzednich wersjach jest teraz uważanych za składniki niestandardowe, które należy jawnie wybrać w tej wersji.

 ![Okno dialogowe Instalatora programu Visual Studio 2015](../ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

 Niestandardowe składniki obejmują Visual C++, Visual F#, SQL Server narzędzia do danych, narzędzia i zestawy SDK dla wielu platform oraz zestawy SDK i rozszerzenia innych firm. Można zainstalować dowolne składniki niestandardowe w późniejszym czasie, jeśli nie zostaną wybrane podczas początkowej konfiguracji.

> [!NOTE]
> Instalacja niestandardowa automatycznie uwzględnia składniki, które są w instalacji domyślnej.

 Pełna lista składników niestandardowych jest następująca:

|Zestawy funkcji|Składniki|
|------------------|----------------|
|**Aktualizacje**|Visual Studio 2015 Update 3|
|**Języki programowania**|Visual C++<br />Visual F#<br />Python Tools for Visual Studio|
|**Programowanie dla systemu Windows i sieci Web**|Narzędzia do publikowania ClickOnce<br />LightSwitch<br />Microsoft Office Narzędzia deweloperskie<br />Narzędzia danych Microsoft SQL Server<br /> Microsoft Web Developer Tools<br />PowerShell Tools for Visual Studio (inna firma)<br />Zestaw Silverlight Development Kit<br />Narzędzia programistyczne dla aplikacji uniwersalnych systemu Windows<br />Narzędzia i zestawy SDK systemu Windows 10<br />Narzędzia Windows 8.1 i Windows Phone 8.0/8.1<br />Narzędzia Windows 8.1 i zestawy SDK|
|**Programowanie aplikacji mobilnych na wiele platform**|C#/.NET (Xamarin)<br />HTML/JavaScript (Apache Cordova)<br />Visual C++ opracowywanie aplikacji mobilnych dla systemu iOS/Android<br />Clang with Microsoft CodeGen|
|**Popularne Narzędzia i zestawy SDK**|Zestaw Android Native Development Kit (inna firma)<br /> Android SDK [inna firma]<br />Interfejsy API Instalatora Android SDK (inna firma)<br />Apache Ant (inna firma)<br /> Java SE Development Kit (inna firma)<br /> Joyent Node.js (inna firma)|
|**Popularne narzędzia**|Git dla systemu Windows (inna firma)<br />Rozszerzenie GitHub dla programu Visual Studio (inna firma)<br /> Visual Studio Extensibility Tools|

## <a name="install-visual-studio"></a><a name="installing"></a> Zainstaluj program Visual Studio
 Program Visual Studio można zainstalować przy użyciu nośnika instalacyjnego (DVD), korzystając z usługi subskrypcji programu Visual Studio z witryny sieci Web [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) , pobierając Instalatora sieci Web z witryny internetowej [pobierania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) lub tworząc układ instalacji w trybie offline (Aby uzyskać więcej informacji, zobacz stronę [Tworzenie instalacji w trybie offline programu Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) ).

> [!IMPORTANT]
> Do zainstalowania programu wymagane są poświadczenia administratora [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Nie są jednak potrzebne do użycia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] po zainstalowaniu programu.

 Aby można było zainstalować wszystko w programie Visual Studio, konto administratora lokalnego musi mieć włączone następujące uprawnienia.

|Nazwa wyświetlana obiektu zasad lokalnych|Prawo użytkownika|
|--------------------------------------|----------------|
|Tworzenie kopii zapasowych plików i katalogów|SeBackupPrivilege|
|Debugowanie programów|SeDebugPrivilege|
|Zarządzanie dziennikiem inspekcji i zabezpieczeń|SeSecurityPrivilege|

 Aby uzyskać więcej informacji na temat tego wymagania dotyczącego konta administratora lokalnego, zobacz artykuł w bazie wiedzy [SQL Server Instalacja nie powiedzie się, jeśli konto instalatora nie ma określonych praw użytkownika](https://support.microsoft.com/kb/2000257).

### <a name="use-installation-media"></a><a name="BKMK_Media"></a> Użyj nośnika instalacyjnego
 Aby zainstalować [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] program, w katalogu głównym na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nośniku instalacyjnym programu uruchom plik instalacyjny dla pożądanej wersji:

|Wersja|Plik instalacyjny|
|-------------|-----------------------|
|Visual Studio Enterprise|vs_enterprise.exe|
|Visual Studio Professional|vs_professional.exe|
|Visual Studio Community|vs_community.exe|

### <a name="download-from-the-product-website"></a><a name="BKMK_Website"></a> Pobieranie z witryny sieci Web produktu
 Odwiedź stronę [pliki do pobrania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) i wybierz żądaną wersję programu Visual Studio.

### <a name="download-from-your-subscription-service"></a>Pobierz z usługi subskrypcji
 Odwiedź stronę [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) i wybierz żądaną wersję programu Visual Studio.

### <a name="create-an-offline-installation-layout"></a><a name="BKMK_Offline"></a> Tworzenie układu instalacji w trybie offline
 Jeśli nie masz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nośnika instalacyjnego lub nie masz subskrypcji programu Visual Studio lub nie chcesz instalować programu przy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] użyciu Instalatora sieci Web, możesz wykonać instalację "Rozłączono", tworząc, co jest znane jako układ instalacji w trybie offline. Aby uzyskać więcej informacji, zobacz stronę [Tworzenie instalacji w trybie offline programu Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) .

## <a name="deploy-visual-studio-in-an-enterprise"></a><a name="enterprise"></a> Wdrażanie programu Visual Studio w przedsiębiorstwie
 Informacje o sposobach wdrażania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] za pośrednictwem sieci znajdują się w [podręczniku administratora programu Visual Studio](../install/visual-studio-administrator-guide.md).

### <a name="install-visual-studio-in-a-virtualized-environment"></a><a name="BKMK_Virtualized"></a> Instalowanie programu Visual Studio w środowisku zwirtualizowanym
 **Problemy z wideo przy użyciu funkcji Hyper-V**

 Jeśli uruchamiasz system Windows Server 2008 R2 z włączoną funkcją Hyper-V oraz akcelerowaną kartą grafiki, może wystąpić spowolnienie systemu.

 Aby uzyskać więcej informacji, zobacz [wydajność wideo może się zmniejszyć, gdy na komputerze z systemem Windows server 2008 lub Windows server 2008 R2 jest włączona rola funkcji Hyper-V, a zainstalowano przyspieszoną kartę graficzną](https://support.microsoft.com/kb/961661).

 **Emulacja urządzeń przy użyciu funkcji Hyper-V**

 Po zainstalowaniu programu Visual Studio 2015 na rzeczywistym sprzęcie bez wirtualizacji można wybrać funkcje, które umożliwiają emulację urządzeń z systemami Windows i Android przy użyciu funkcji Hyper-V. Po zainstalowaniu programu w funkcji Hyper-V nie będzie możliwe emulowanie urządzeń z systemem Windows lub Android. Wynika to z faktu, że Emulatory są maszynami wirtualnymi i obecnie nie można hostować maszyny wirtualnej w innej maszynie wirtualnej. Obejście ma na celu posiadanie rzeczywistych urządzeń z systemem Windows lub Android, do których można bezpośrednio wdrożyć i debugować aplikację.

## <a name="install-optional-components"></a><a name="optionalComponents"></a> Zainstaluj składniki opcjonalne
 Jeśli chcesz zainstalować składniki, które nie zostały wybrane podczas oryginalnej instalacji, wykonaj poniższą procedurę.

#### <a name="to-install-optional-components"></a>Aby zainstalować składniki opcjonalne

1. W **Panelu sterowania**na stronie **programy i funkcje** wybierz wersję produktu, do której chcesz dodać jeden lub więcej składników, a następnie wybierz pozycję **Zmień**.

2. W Kreatorze instalacji wybierz **Modyfikuj**, a następnie wybierz składniki, które chcesz zainstalować.

3. Wybierz pozycję **dalej**, a następnie postępuj zgodnie z pozostałymi instrukcjami.

## <a name="install-offline-help-content"></a><a name="helpContent"></a> Zainstaluj zawartość pomocy w trybie offline
 Po zainstalowaniu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] programu można pobrać dodatkową zawartość pomocy, aby była dostępna w trybie offline.

#### <a name="to-install-or-uninstall-help-content"></a>Aby zainstalować lub odinstalować zawartość pomocy

1. Na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pasku menu wybierz **Pomoc**, **Dodaj i Usuń zawartość pomocy**.

2. Na karcie **Zarządzanie zawartością** w **Podgląd pomocy firmy Microsoft**wybierz źródło instalacji dla zawartości pomocy.

3. Jeśli szukasz konkretnej kolekcji pomocy, wprowadź nazwę lub słowo kluczowe w polu tekstowym **Wyszukaj** , a następnie naciśnij klawisz **Enter**.

4. Obok nazwy kolekcji pomocy wybierz łącze **Dodaj** lub **Usuń** .

5. Kliknij przycisk **Aktualizuj** .

   Więcej informacji o sposobie instalowania lub wdrażania pomocy w trybie offline można znaleźć w [podręczniku administratora podglądu pomocy](../ide/help-viewer-administrator-guide.md).

## <a name="check-for-service-releases-and-product-updates"></a><a name="serviceReleases"></a> Sprawdź dostępność wydań usług i aktualizacji produktu
 Ponieważ nie wszystkie rozszerzenia są zgodne, program Visual Studio nie uaktualnia rozszerzeń automatycznie podczas uaktualniania z poprzednich wersji. Należy ponownie zainstalować rozszerzenia z [Visual Studio Marketplace](https://marketplace.visualstudio.com/) lub wydawcy oprogramowania.

#### <a name="to-automatically-check-for-service-releases"></a>Aby automatycznie sprawdzić, czy są dostępne poprawki

1. Na pasku menu wybierz **Narzędzia**, **Opcje**.

2. W oknie dialogowym **Opcje** rozwiń węzeł **środowisko**, a następnie wybierz pozycję **rozszerzenia i aktualizacje**. Upewnij się, że jest zaznaczone pole wyboru **automatycznie sprawdzaj dostępność aktualizacji** , a następnie wybierz przycisk **OK**.

## <a name="register-visual-studio"></a>Zarejestruj program Visual Studio

1. Na pasku menu wybierz **Pomoc**, **informacje**.

     Okno dialogowe **informacje** pokazuje numer identyfikacyjny produktu (PID). Aby zarejestrować produkt, musisz mieć poświadczenia identyfikatora PID i konta systemu Windows (takie jak adres e-mail w usłudze Hotmail lub Outlook.com).

2. Na pasku menu wybierz **Pomoc**, **zarejestruj produkt**.

## <a name="repair-visual-studio"></a><a name="repair"></a> Napraw program Visual Studio

#### <a name="to-repair-visual-studio"></a>Aby naprawić program Visual Studio

1. W **Panelu sterowania**na stronie **programy i funkcje** wybierz wydanie produktu, które chcesz naprawić, a następnie wybierz pozycję **Zmień**.

2. W Kreatorze instalacji wybierz pozycję **napraw**, wybierz pozycję **dalej**, a następnie postępuj zgodnie z pozostałymi instrukcjami.

#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>Aby naprawić program Visual Studio w trybie cichym lub pasywnym (czyli w celu naprawy ze źródła)

1. Na komputerze, na którym jest zainstalowany program Visual Studio, otwórz wiersz polecenia systemu Windows.

2. Wprowadź następujące parametry:

     *DVDRoot* \\ DVDRoot < *Plik instalacyjny* \> \<`/quiet|/passive`> [/`norestart`]/`Repair`

## <a name="troubleshoot-an-installation"></a><a name="troubleshooting"></a> Rozwiązywanie problemów z instalacją
 Użyj tych zasobów, aby uzyskać pomoc dotyczącą instalacji i problemów z instalacją:

- Forum instalacji [i instalacji programu Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/vssetup/threads) . Przejrzyj pytania i odpowiedzi od innych użytkowników w społeczności programu Visual Studio. Jeśli nie możesz znaleźć potrzebnych informacji, zadaj własne pytania.

- [Uzyskaj pomoc dotyczącą programu Visual Studio](https://visualstudio.microsoft.com/vs/support/vs2015/). Znajdź artykuły bazy wiedzy (KB) i Dowiedz się, jak skontaktować się z pomoc techniczna firmy Microsoft, aby uzyskać informacje o problemach z instalacją programu Visual Studio.

## <a name="related-topics"></a><a name="relatedTopics"></a> Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Tworzenie instalacji w trybie offline programu Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)|Opisuje sposób instalowania programu Visual Studio, gdy nie masz połączenia z Internetem.
|[Instalowanie wersji programu Visual Studio obok siebie](../install/install-visual-studio-versions-side-by-side.md)|Zawiera informacje dotyczące sposobu instalowania wielu wersji programu Visual Studio na tym samym komputerze.|
|[Używanie parametrów wiersza polecenia do instalowania programu Visual Studio](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)|Wyświetla listę parametrów wiersza polecenia, których można użyć podczas instalowania programu Visual Studio z poziomu wiersza polecenia.|
|[Odinstalowywanie programu Visual Studio](../install/uninstall-visual-studio.md)|Opisuje sposób odinstalowywania programu Visual Studio.|
|[Przewodnik administratora programu Visual Studio](../install/visual-studio-administrator-guide.md)|Zawiera informacje dotyczące opcji wdrażania programu Visual Studio.|
|[Biblioteka obrazów programu Visual Studio](../designers/the-visual-studio-image-library.md)|Zawiera informacje dotyczące sposobu instalowania grafiki, która może być używana w aplikacjach Visual Studio.|
|[Wprowadzenie do programowania w programie Visual Studio](../ide/get-started-developing-with-visual-studio.md)|Zawiera informacje i linki, które mogą ułatwić korzystanie z programu Visual Studio.|

## <a name="see-also"></a>Zobacz też

- [Visual Studio — logowanie](../ide/signing-in-to-visual-studio.md)
