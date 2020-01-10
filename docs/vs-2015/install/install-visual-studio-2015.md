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
ms.openlocfilehash: dc84fc135e59a43a05ce66186c4a44e9e31f8f2c
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851055"
---
# <a name="install-visual-studio-2015"></a>Instalowanie programu Visual Studio 2015

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta strona zawiera szczegółowe informacje pomocne przy instalowaniu **programu Visual Studio 2015**, naszego zintegrowanego pakietu narzędzi zwiększających produktywność dla deweloperów. Dołączono również linki, które ułatwią Ci szybkie informacje [funkcji](https://www.visualstudio.com/news/vs2015-vs.aspx), [wersje](https://visualstudio.microsoft.com/en-US/products/compare-visual-studio-products-vs), [wymagania systemowe](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs), [pliki do pobrania](https://visualstudio.microsoft.com/downloads/), i nie tylko.

## <a name="quick-links"></a>Szybkie linki

Przed rozpoczęciem omawiania szczegółach poniżej przedstawiono listę nasze najczęściej żądanych łączy.

|||
|------------------|----------------|
|![Pobierz program Visual Studio](../install/media/downloads.png "Pliki do pobrania") |**Pliki do pobrania**: Aby zainstalować program Visual Studio 2015, możesz pobrać plik wykonywalny produktu z [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) strony (wymagana jest subskrypcja) lub użyć nośnika instalacyjnego z produktu w ramce. [Dowiedz się więcej na temat sposobu pobierania bieżącej lub poprzedniej wersji programu Visual Studio](https://www.visualstudio.com/vs/older-downloads/).|
|![Dowiedz się więcej o funkcjach](../install/media/features.png "Funkcje") |**Funkcje**: Aby dowiedzieć się więcej na temat funkcji w programie Visual Studio 2015, zobacz informacje o wersji dla [RTM](https://www.visualstudio.com/news/vs2015-vs), [Update 1](https://www.visualstudio.com/news/vs2015-update1-vs), [Update 2](https://www.visualstudio.com/news/vs2015-update2-vs), i [ Z aktualizacją 3](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs).|
|![Dowiedz się, co znajduje się w każdej jednostce SKU](../install/media/sku.png "SKU") |**Jednostki SKU**: Aby dowiedzieć się, co jest dostępne w poszczególnych wydaniach programu Visual Studio 2015, zobacz nasze [porównanie ofert programu Visual Studio](https://visualstudio.microsoft.com/en-US/products/compare-visual-studio-products-vs) strony.|
|![Wyświetl wymagania systemowe](../install/media/system-requirements.png "Wymagania systemowe") |**Wymagania systemowe**: Aby wyświetlić wymagania systemowe dla każdej wersji programu Visual Studio 2015, zobacz [zgodność programu Visual Studio 2015](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs) strony.|
|![Lokalizowanie klucza produktu](../install/media/product-keys.png "Klucze produktów") |**Klucze produktów**: Aby znaleźć klucz produktu, zobacz [jak: Znajdź Visual Studio Product Key](../install/how-to-locate-the-visual-studio-product-key.md) tematu.|
|![Dowiedz się więcej o licencjonowaniu](../install/media/licensing.png "Licencjonowanie") |**Licencjonowanie**: Aby dowiedzieć się o licencjonowaniu opcje zarówno użytkowników indywidualnych, jak i klientów korporacyjnych, zobacz [programu Visual Studio i MSDN — Licencjonowanie](https://www.microsoft.com/download/details.aspx?id=13350) oficjalny dokument.|

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
|**Języki programowania**|Visual C++<br />Visual F#<br />{1&gt;{2&gt;Python Tools for Visual Studio&lt;2}&lt;1}|
|**Windows i aplikacji sieci Web**|Narzędzia publikowania ClickOnce<br />LightSwitch<br />Microsoft Office Developer Tools<br />Microsoft SQL Server Data Tools<br /> Narzędzia Microsoft Web Developer Tools<br />Narzędzia programu PowerShell dla programu Visual Studio (strona 3)<br />Zestaw deweloperski dodatku Silverlight<br />Narzędzia do tworzenia aplikacji Windows Universal<br />Narzędzia systemu Windows 10 i zestawy SDK<br />Windows 8.1 i Windows Phone 8.0/8.1 narzędzi<br />Windows 8.1, narzędzia i zestawy SDK|
|**Cross Platform Mobile Development**|C# / .NET (Xamarin)<br />HTML/JavaScript (Apache Cordova)<br />Mobile środowiska deweloperskiego Visual C++ dla systemu iOS / Android<br />Clang with Microsoft CodeGen|
|**Typowe narzędzia i zestawy Software Development Kit**|Dla systemu android Native Development Kit (strona 3)<br /> Zestaw SDK systemu android [Strona 3]<br />Interfejsy API Instalator zestawu android SDK (strona 3)<br />Apache Ant (strona 3)<br /> Java SE Development Kit (strona 3)<br /> Joyent Node.js (strona 3)|
|**Typowe narzędzia**|Git Pro Windows (strona 3)<br />Rozszerzenie GitHub dla programu Visual Studio (strona 3)<br /> Visual Studio Extensibility Tools|

## <a name="installing"></a> Instalowanie programu Visual Studio
 Przy użyciu nośnika instalacyjnego (DVD), można zainstalować program Visual Studio, za pomocą usługi subskrypcji programu Visual Studio z [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) witryny sieci Web, pobierając Instalator sieci web z [programu Visual Studio Pliki do pobrania](https://visualstudio.microsoft.com/downloads/) witryny sieci Web, lub przez tworzenie układu instalacji w trybie offline (zobacz [Offline instalacji programu Visual Studio Utwórz](../install/create-an-offline-installation-of-visual-studio.md) strony, aby uzyskać więcej informacji).

> [!IMPORTANT]
> Musisz mieć uprawnienia administratora, aby zainstalować [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Jednak nie są potrzebne do użycia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] po jej zainstalowaniu.

 Konto administratora lokalnego musi mieć następujące uprawnienia, które są włączone, aby zainstalować wszystkie elementy w programie Visual Studio.

|Nazwa wyświetlana obiektu lokalnych zasad|Prawa użytkownika|
|--------------------------------------|----------------|
|Tworzenie kopii zapasowych plików i katalogów|SeBackupPrivilege|
|Debugowanie programów|SeDebugPrivilege|
|Zarządzaj dziennikiem inspekcji i zabezpieczeń|SeSecurityPrivilege|

 Aby uzyskać więcej informacji na temat tego wymagania konta administratora lokalnego, zobacz artykuł bazy wiedzy, [instalacji programu SQL Server kończy się niepowodzeniem, jeśli konto instalacji nie ma określonych praw użytkownika](https://support.microsoft.com/kb/2000257).

### <a name="BKMK_Media"></a> Przy użyciu nośnika instalacyjnego
 Aby zainstalować [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], w katalogu głównym na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nośnika instalacyjnego, uruchom plik instalacyjny dla wersji chcesz:

|Wersja|Plik instalacyjny|
|-------------|-----------------------|
|Visual Studio Enterprise|vs_enterprise.exe|
|Visual Studio Professional|vs_professional.exe|
|Visual Studio Community|vs_community.exe|

### <a name="BKMK_Website"></a> Pobieranie z witryny sieci Web produktu
 Odwiedź stronę [pobieranie Visual Studio](https://visualstudio.microsoft.com/downloads/) strony, a następnie wybierz wersję programu Visual Studio, który ma.

### <a name="downloading-from-your-subscription-service"></a>Pobieranie z usługi w subskrypcji
 Odwiedź stronę [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) strony, a następnie wybierz wersję programu Visual Studio, który ma.

### <a name="BKMK_Offline"></a> Tworzenie układu instalacji w trybie offline
 Jeśli nie masz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nośnika instalacyjnego, lub nie masz subskrypcji programu Visual Studio lub nie chcesz zainstalować [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] za pomocą Instalatora sieci web, można wykonać "odłączonej" instalacji, tworząc, co jest nazywane w trybie offline Układ instalacyjny. Aby uzyskać więcej informacji, zobacz [trybu Offline instalacji programu Visual Studio Utwórz](../install/create-an-offline-installation-of-visual-studio.md) strony.

## <a name="enterprise"></a> Wdrażanie programu Visual Studio w przedsiębiorstwie
 Aby uzyskać informacje o sposobie wdrażania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] za pośrednictwem sieci, zobacz [Podręcznik administratora programu Visual Studio](../install/visual-studio-administrator-guide.md).

### <a name="BKMK_Virtualized"></a> Instalowanie programu Visual Studio w środowisku wirtualnym
 **Wideo problemy z funkcją Hyper-V**

 Jeśli uruchamiasz system Windows Server 2008 R2 z włączoną funkcją Hyper-V oraz akcelerowaną kartą grafiki, może wystąpić spowolnienie systemu.

 Aby uzyskać więcej informacji, zobacz następującą stronę w witrynie internetowej firmy Microsoft: [wydajność wideo może zmniejszyć, gdy system Windows Server 2008 lub Windows Server 2008 R2, na podstawie komputer ma włączoną rolę funkcji Hyper-V i zainstalowaną akcelerowaną kartę](https://support.microsoft.com/kb/961661).

 **Emulacja urządzeń za pomocą funkcji Hyper-V**

 Po zainstalowaniu programu Visual Studio 2015 na sprzęt rzeczywisty bez wirtualizacji, można wybrać funkcje, które umożliwiają emulacji systemu Windows oraz urządzeń z systemem Android przy użyciu funkcji Hyper-V. Po zainstalowaniu w funkcji Hyper-V, nie będzie można emulować Windows lub urządzeń z systemem Android. Jest to spowodowane emulatorów znajdują się maszyny wirtualne i obecnie nie można hostować Maszynę wirtualną w innej maszyny Wirtualnej. Obejście polega na rzeczywistych Windows lub urządzeń z systemem Android do których możesz bezpośrednio wdrażania i debugowania aplikacji.

## <a name="optionalComponents"></a> Instaluje składniki opcjonalne
 Jeśli chcesz zainstalować składniki, które być może nie został wybrany podczas oryginalnej instalacji, należy użyć poniższej procedury.

#### <a name="to-install-optional-components"></a>Aby zainstalować składniki opcjonalne

1. W **Panelu sterowania**na **programy i funkcje** wybierz wydanie produktu, do którego chcesz dodać jeden lub więcej składników, a następnie wybierz **zmiany**.

2. W Kreatorze instalacji wybierz **Modyfikuj**, a następnie wybierz składniki, które chcesz zainstalować.

3. Wybierz **dalej**, a następnie postępuj zgodnie z dalszymi instrukcjami.

## <a name="helpContent"></a> Instalowanie zawartości pomocy w trybie offline
 Po zainstalowaniu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], możesz pobrać dodatkową pomoc, czemu będzie on dostępny w trybie offline.

#### <a name="to-install-or-uninstall-help-content"></a>Aby zainstalować lub odinstalować zawartość pomocy

1. Na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] menu paska, wybierz polecenie **pomocy**, **Dodawanie i usuwanie zawartości Pomocy**.

2. Na **Zarządzaj zawartością** karcie **podglądu pomocy firmy Microsoft**, wybierz źródło instalacji zawartości pomocy.

3. Jeśli szukasz określonej kolekcji pomocy, wpisz nazwę lub słowo kluczowe w **wyszukiwania** polu tekstowym, a następnie naciśnij klawisz **Enter**.

4. Obok nazwy kolekcji pomocy, chcesz, aby wybrać **Dodaj** lub **Usuń** łącza.

5. Kliknij przycisk **aktualizacji** przycisku.

   Aby uzyskać więcej informacji na temat sposobu zainstalowania lub wdrożenia pomocy w trybie offline, zobacz [Podręcznik administratora programu Podgląd Pomocy](../ide/help-viewer-administrator-guide.md).

## <a name="serviceReleases"></a> Wyszukiwanie poprawek i aktualizacji produktu
 Ponieważ nie wszystkie rozszerzenia są zgodne, Visual Studio nie aktualizuje automatycznie rozszerzeń po uaktualnieniu z poprzednimi wersjami. Należy ponownie zainstalować rozszerzenia z [Visual Studio Marketplace](https://marketplace.visualstudio.com/) lub wydawcy oprogramowania.

#### <a name="to-automatically-check-for-service-releases"></a>Aby automatycznie sprawdzić, czy są dostępne poprawki

1. Na pasku menu wybierz **narzędzia**, **opcje**.

2. W **opcje** okna dialogowego rozwiń **środowiska**, a następnie wybierz pozycję **rozszerzenia i aktualizacje**. Upewnij się, że **automatycznie sprawdzaj dostępność aktualizacji** pole wyboru jest zaznaczone, a następnie wybierz **OK**.

## <a name="registering-visual-studio"></a>Rejestrowanie programu Visual Studio

1. Na pasku menu wybierz **pomocy**, **o**.

     **o** okno dialogowe pokazuje numer identyfikacyjny produktu (PID). Identyfikator PID i konta Windows poświadczenia (na przykład usługi Hotmail lub Outlook.com adres e-mail i hasło) musisz zarejestrować produkt.

2. Na pasku menu wybierz **pomocy**, **Zarejestruj produkt**.

## <a name="repair"></a> Naprawa programu Visual Studio

#### <a name="to-repair-visual-studio"></a>Aby naprawić program Visual Studio

1. W **Panelu sterowania**na **programy i funkcje** wybierz wydanie produktu, który chcesz naprawić, a następnie wybierz **zmiany**.

2. W Kreatorze instalacji wybierz **naprawy**, wybierz **dalej**, a następnie postępuj zgodnie z dalszymi instrukcjami.

#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>Aby naprawić program Visual Studio w trybie cichym lub pasywnym (czyli na naprawę ze źródła)

1. Na komputerze, na którym jest zainstalowany program Visual Studio, otwórz wiersz polecenia systemu Windows.

2. Wprowadź następujące parametry:

     *DVDRoot* \\< plik instalacyjny\> \</quiet&#124;/passive > [/ norestart] / napraw

## <a name="troubleshooting"></a> Rozwiązywanie problemów z instalacją
 Dzięki tym zasobom można uzyskać pomoc dotyczącą problemów z konfiguracją i instalacją:

- [Visual Studio Konfiguracja i instalacja](https://social.msdn.microsoft.com/Forums/en-US/vssetup/threads) forum. Przejrzyj pytania i odpowiedzi od innych użytkowników w społeczności programu Visual Studio. Jeśli nie możesz znaleźć potrzebnych informacji, zadaj własne pytania.

- [Microsoft Support for Visual Studio](https://support.microsoft.com/ph/1117) witryny sieci Web. Zapoznaj się z artykułami w bazie wiedzy (KB) i dowiedz się, jak się skontaktować z działem pomocy Microsoft, aby uzyskać informacje dotyczące problemów związanych z instalacją programu Visual Studio.

## <a name="relatedTopics"></a> Tematy pokrewne

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
