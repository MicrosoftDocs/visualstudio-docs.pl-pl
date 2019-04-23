---
title: 'Instrukcje: Instalowanie wtyczki kontroli źródła | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fe03499200d3528a1aed286550191fd9dfcc1451
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60039845"
---
# <a name="how-to-install-a-source-control-plug-in"></a>Instrukcje: Instalowanie wtyczki kontroli kodu źródłowego
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tworzenie wtyczki kontroli źródła obejmuje trzy kroki:  
  
1. Utworzyć bibliotekę DLL przy użyciu funkcji zdefiniowanych w sekcji odwołanie interfejsu API wtyczki kontroli źródła w niniejszej dokumentacji.  
  
2. Zaimplementuj funkcje zdefiniowane przez interfejs API wtyczki kontroli źródła. Gdy [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] wywołań, Udostępnij interfejsy i okien dialogowych z wtyczki.  
  
3. Zarejestruj plik DLL, wprowadzając wpisy rejestru odpowiednie.  
  
## <a name="integration-with-visual-studio"></a>Integracja z programem Visual Studio  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] obsługuje źródła wtyczek kontroli, które są zgodne z interfejsem API wtyczki kontroli źródła.  
  
### <a name="registering-the-source-control-plug-in"></a>Rejestrowanie wtyczka do kontroli źródła  
 Zanim uruchomionej zintegrowanego środowiska programistycznego (IDE), można wywołać w systemie kontroli źródła, najpierw musi znaleźć źródło kontrolować biblioteki DLL dodatku plug-in, który eksportuje interfejsu API.  
  
##### <a name="to-register-the-source-control-plug-in-dll"></a>Aby zarejestrować biblioteki DLL dodatku plug-in kontroli źródła  
  
1. Dodaj dwa wpisy w kluczu HKEY_LOCAL_MACHINE w podkluczu oprogramowania określający swoje podklucz nazwa firmy następuje podklucz nazwa Twojego produktu. Wzorzec jest HKEY_LOCAL_MACHINE\SOFTWARE\\ *[nazwa firmy]*\\ *[nazwa produktu]*\\ *[entry]* = wartość. Dwa wpisy zawsze są nazywane SCCServerName i SCCServerPath. Każdy jest regularne ciągu.  
  
     Na przykład jeśli nazwą firmy jest firma Microsoft i produktu kontroli źródła jest o nazwie SourceSafe, ta ścieżka rejestru wyniósłby HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe. W tym podkluczu pierwszy wpis SCCServerName, jest ciąg czytelny dla użytkownika nazwy produktu. Drugi wpis SCCServerPath, jest pełna ścieżka do źródła kontrolować IDE powinny łączyć się z biblioteki DLL dodatku plug-in. Poniżej przedstawiono przykładowe wpisy rejestru:  
  
    |Przykładowy wpis rejestru|Przykładowa wartość|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|c:\vss\win32\ssscc.dll|  
  
    > [!NOTE]
    >  SCCServerPath jest pełną ścieżką do we wtyczce programu SourceSafe. Wtyczka do kontroli źródła użyje różne nazwy firmy i produkt, ale tej samej ścieżki wpisu rejestru.  
  
2. Następujące wpisy rejestru opcjonalnie może służyć do modyfikowania zachowania wtyczka do kontroli źródła. Te wpisy go w tym samym podkluczu SccServerName oraz SccServerPath.  
  
    - Wpis HideInVisualStudioregistry może być używany, jeśli nie chcesz źródła kontrolki plug w celu pojawiają się na liście wybór wtyczki [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Ten wpis wpłynie również na automatyczne przełączanie do wtyczka do kontroli źródła. Jedno możliwe użycie dla tego wpisu jest, jeśli podasz pakiet do kontroli źródła, który zastępuje wtyczka do kontroli źródła, ale aby ułatwić użytkownikowi migrację za pomocą wtyczka do kontroli źródła do pakietu kontroli źródła. Po zainstalowaniu pakietu kontroli źródła, ustawia ten wpis rejestru i ukrywa dodatku typu plug-in.  
  
         HideInVisualStudio jest wartość DWORD i jest ustawiona na 1, aby ukryć wtyczki lub 0, aby wyświetlić dodatek typu plug-in. Jeśli wpis rejestru nie jest wyświetlany, zachowanie domyślne jest do wyświetlenia dodatku typu plug-in.  
  
    - Wpis rejestru DisableSccManager, umożliwia wyłączenie lub ukrycie **Uruchom \<serwera kontroli źródła >** opcję menu, który zwykle pojawia się w obszarze **pliku**  ->   **Kontrola źródła** podmenu. Wybranie tego menu opcji wywołania [SccRunScc](../../extensibility/sccrunscc-function.md) funkcji. Wtyczka do kontroli źródła może nie obsługuje programu zewnętrznego i dlatego może być wyłączenie lub ukrycie nawet **Uruchom** opcji menu.  
  
         DisableSccManager jest wartość DWORD jest ustawiona na 0 Aby włączyć **Uruchom \<serwera kontroli źródła >** ustawiona na 1, aby wyłączyć opcję menu, a wartość 2 Ukryj opcję menu opcji menu. Jeśli nie ma tego wpisu rejestru, zachowanie domyślne jest do wyświetlenia opcji menu.  
  
    |Przykładowy wpis rejestru|Przykładowa wartość|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio|1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager|1|  
  
3. Dodaj podklucz, SourceCodeControlProvider, w kluczu HKEY_LOCAL_MACHINE w podkluczu oprogramowania.  
  
     W podkluczu ten wpis rejestru ProviderRegKey ustawiono na ciąg, który reprezentuje podklucza, który można umieścić w rejestrze, w kroku 1. Wzorzec jest HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey = oprogramowania\\ *[nazwa firmy]*\\ *[nazwa produktu]*.  
  
     Oto przykłady tego podklucza.  
  
    |Wpis rejestru|Przykładowa wartość|  
    |--------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  Wtyczka do kontroli źródła będzie używać tego samego podklucz i nazwy wpisów, ale wartość będzie inny.  
  
4. Utwórz podklucz o nazwie InstalledSCCProviders w podkluczu SourceCodeControlProvider, a następnie umieścić jednego wpisu tego podklucza.  
  
     Nazwa tego wpisu jest czytelny dla użytkownika nazwa dostawcy, (taka sama jak wartość określona dla wpisu SCCServerName), a wartość jest jeszcze raz podklucza, który został utworzony w kroku 1. Wzorzec jest HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\ *[Nazwa wyświetlana]* = oprogramowania\\ *[nazwa firmy]* \\ *[nazwa produktu]*.  
  
     Na przykład:  
  
    |Przykładowy wpis rejestru|Przykładowa wartość|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  Może istnieć wiele źródła wtyczek kontroli zarejestrowanych w ten sposób. Jest to jak [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] znajduje wszystkie zainstalowane wtyczki oparte na interfejsie API wtyczki kontroli źródła.  
  
## <a name="how-an-ide-locates-the-dll"></a>Sposoby lokalizowania IDE przez biblioteki DLL  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE ma dwa sposoby znajdowania źródła kontrolować biblioteki DLL dodatku plug-in:  
  
- Znajdź wtyczki kontroli źródła domyślne, a następnie połącz się z nim w trybie dyskretnym.  
  
- Znajdź wszystkie zarejestrowane źródła wtyczek kontroli, z której użytkownik wybiera jeden.  
  
  Aby zlokalizować biblioteki DLL w pierwszym sposobie, IDE wygląda ProviderRegKey wpis w podkluczu HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider. Wskazuje wartość tego wpisu do innego podklucza. Następnie IDE szuka wpisu o nazwie SccServerPath w tym drugiego podklucza w kluczu HKEY_LOCAL_MACHINE. Wartość tego wpisu wskazuje IDE biblioteki DLL.  
  
> [!NOTE]
>  IDE nie załadować biblioteki dll z ścieżek względnych (na przykład.\NewProvider.DLL). Należy określić pełną ścieżkę do biblioteki DLL (na przykład c:\Providers\NewProvider.DLL). To wzmacnia zabezpieczenia środowiska IDE, zapobiegając ładowanie nieautoryzowani lub spersonifikowanego wtyczki bibliotek DLL.  
  
 Aby zlokalizować bibliotekę DLL w druga metoda, IDE wygląda dla wszystkich wpisów w podkluczu HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders<em>.</em> Każdy wpis ma nazwę i wartość. Środowisko IDE Wyświetla listę tych nazw użytkownika<em>.</em> Gdy użytkownik wybierze nazwę, IDE wyszukuje wartość dla wybranej nazwy, która wskazuje podklucza. IDE szuka wpisu o nazwie SccServerPath w tym podklucza w kluczu HKEY_LOCAL_MACHINE. Wartość tego wpisu wskazuje IDE poprawne biblioteki DLL.  
  
 Wtyczka do kontroli źródła musi obsługiwać obie metody wyszukiwania biblioteki DLL i w związku z tym, ustaw ProviderRegKey, zastępując wszystkie poprzednie ustawienia. Co ważniejsze jego należy dodać się do listy InstalledSccProviders, dzięki czemu użytkownik może mieć szeroki wybór wtyczki kontroli źródła do użycia.  
  
> [!NOTE]
>  Ponieważ są używane w kluczu HKEY_LOCAL_MACHINE, wtyczka do kontroli źródła tylko jedna może być rejestrowany jako domyślna wtyczka do kontroli źródła na danym komputerze (jednak [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] umożliwia użytkownikom określić, które wtyczka do kontroli źródła mają być faktycznie na użytek konkretnego rozwiązania). Podczas procesu instalacji sprawdź, jeśli wtyczka do kontroli źródła jest już skonfigurowana; Jeśli tak, poproś użytkownika, czy można ustawić nowych kontroli źródła wtyczek instalowanych domyślnie. Podczas dezinstalacji nie usuwaj innych podkluczy rejestru, które są wspólne dla wszystkich źródła wtyczek kontroli w HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider; Usuń tylko z określonego podklucza SCC.  
  
## <a name="how-the-ide-detects-version-1213-support"></a>Jak IDE wykrywa pomocy technicznej w wersji 1.2/1.3  
 Jak jest [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] wykryć, czy wtyczka obsługuje funkcjonalność w wersji 1.2 i 1.3 interfejsu API wtyczki kontroli źródła? Aby zadeklarować zaawansowana funkcja, wtyczka do kontroli źródła musi implementować odpowiednich funkcji.  
  
 Po pierwsze, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sprawdza, czy wartość zwrócona przez wywołanie metody [SccGetVersion](../../extensibility/sccgetversion-function.md). Jego musi być większa lub równa 1.2.  
  
 Następnie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Określa, czy określonego nowa funkcja jest obsługiwana, sprawdzając `lpSccCaps` argumentu [SccInitialize](../../extensibility/sccinitialize-function.md).  
  
 Jeśli oba te warunki są spełnione, można wywołać nowych funkcji, które są obsługiwane w wersji 1.2 i 1.3.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
