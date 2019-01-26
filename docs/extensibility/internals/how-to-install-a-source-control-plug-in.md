---
title: 'Instrukcje: Instalowanie wtyczki kontroli źródła | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 58a472ad20bbaee34937fcfd058710b58478dade
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54961692"
---
# <a name="how-to-install-a-source-control-plug-in"></a>Instrukcje: Instalowanie wtyczki kontroli źródła
Tworzenie wtyczki kontroli źródła obejmuje trzy kroki:  

1. Utworzyć bibliotekę DLL przy użyciu funkcji zdefiniowanych w sekcji odwołanie interfejsu API wtyczki kontroli źródła w niniejszej dokumentacji.  

2. Zaimplementuj funkcje zdefiniowane przez interfejs API wtyczki kontroli źródła. Gdy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wywołań, Udostępnij interfejsy i okien dialogowych z wtyczki.  

3. Zarejestruj plik DLL, wprowadzając wpisy rejestru odpowiednie.  

## <a name="integration-with-visual-studio"></a>Integracja z programem Visual Studio  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obsługuje źródła wtyczek kontroli, które są zgodne z interfejsem API wtyczki kontroli źródła.  

### <a name="register-the-source-control-plug-in"></a>Zarejestruj wtyczka do kontroli źródła  
 Zanim uruchomionej zintegrowanego środowiska programistycznego (IDE), można wywołać w systemie kontroli źródła, najpierw musi znaleźć źródło kontrolować biblioteki DLL dodatku plug-in, który eksportuje interfejsu API.  

#### <a name="to-register-the-source-control-plug-in-dll"></a>Aby zarejestrować biblioteki DLL dodatku plug-in kontroli źródła  

1. Dodania dwóch wpisów w obszarze **HKEY_LOCAL_MACHINE** w **oprogramowania** określa podklucz nazwę swojej firmy, który następuje podklucz nazwa Twojego produktu. Wzorzec jest **HKEY_LOCAL_MACHINE\SOFTWARE\\\<nazwa firmy >\\\<nazwa produktu >\\\<wejścia >**  =  *wartość*. Dwa wpisy zawsze są nazywane **SCCServerName** i **SCCServerPath**. Każdy jest regularne ciągu.  

    Na przykład, jeśli nazwa firmy to Microsoft produktu kontroli źródła o nazwie SourceSafe, ta ścieżka rejestru będzie **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe**. W tym podkluczu pierwszy wpis **SCCServerName**, jest ciąg czytelny dla użytkownika nazwy produktu. Drugi wpis **SCCServerPath**, jest pełna ścieżka do źródła kontrolować IDE powinny łączyć się z biblioteki DLL dodatku plug-in. Poniżej przedstawiono przykładowe wpisy rejestru:  

   |Przykładowy wpis w rejestrze|Wartość przykładowa|  
   |---------------------------|------------------|  
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|  
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|*c:\vss\win32\ssscc.dll*|  

   > [!NOTE]
   >  SCCServerPath jest pełną ścieżką do we wtyczce programu SourceSafe. Wtyczka do kontroli źródła użyje różne nazwy firmy i produkt, ale tej samej ścieżki wpisu rejestru.  

2. Następujące wpisy rejestru opcjonalnie może służyć do modyfikowania zachowania wtyczka do kontroli źródła. Te wpisy go w tym samym podkluczu jako **SccServerName** i **SccServerPath**.  

   - **HideInVisualStudioregistry** wpis może być używany, jeśli nie ma źródła kontroli plug w **wybór wtyczki** listę [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Ten wpis wpłynie również na automatyczne przełączanie do wtyczka do kontroli źródła. Jedno możliwe użycie dla tego wpisu jest, jeśli podasz pakiet do kontroli źródła, który zastępuje wtyczka do kontroli źródła, ale aby ułatwić użytkownikowi migrację za pomocą wtyczka do kontroli źródła do pakietu kontroli źródła. Po zainstalowaniu pakietu kontroli źródła, ustawia ten wpis rejestru i ukrywa dodatku typu plug-in.  

      **HideInVisualStudio** jest wartość DWORD i ustawiono *1* ukryć wtyczki lub *0* pokazanie dodatku typu plug-in. Jeśli wpis rejestru nie jest wyświetlany, zachowanie domyślne jest do wyświetlenia dodatku typu plug-in.  

   - **DisableSccManager** wpis rejestru, umożliwia wyłączenie lub ukrycie **Uruchom \<serwera kontroli źródła >** opcję menu, który zwykle pojawia się w obszarze **pliku**  >  **Kontroli źródła** podmenu. Wybranie tego menu opcji wywołania [SccRunScc](../../extensibility/sccrunscc-function.md) funkcji. Wtyczka do kontroli źródła może nie obsługuje programu zewnętrznego i dlatego może być wyłączenie lub ukrycie nawet **Uruchom** opcji menu.  

      **DisableSccManager** jest wartość DWORD i ustawiono *0* umożliwiające **Uruchom \<serwera kontroli źródła >** opcji menu równa *1* do Wyłącz opcję menu, a następnie ustaw *2* spowoduje ukrycie opcji menu. Jeśli nie ma tego wpisu rejestru, zachowanie domyślne jest do wyświetlenia opcji menu.  

   | Przykładowy wpis rejestru | Wartość przykładowa |
   | - |--------------|
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio | 1 |
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager | 1 |


3. Dodaj podklucz **SourceCodeControlProvider**w obszarze **HKEY_LOCAL_MACHINE** w **oprogramowania** podklucza.  

    W podkluczu ten wpis rejestru **ProviderRegKey** jest ustawiony na ciąg, który reprezentuje podklucza, który można umieścić w rejestrze, w kroku 1. Wzorzec jest **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey** = *oprogramowania\\< nazwa firmy\>\\< nazwa produktu \>*.  

    Oto przykłady tego podklucza.  

   |Wpis rejestru|Wartość przykładowa|  
   |--------------------|------------------|  
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|  

   > [!NOTE]
   >  Wtyczka do kontroli źródła będzie używać tego samego podklucz i nazwy wpisów, ale wartość będzie inny.  

4. Utwórz podklucz o nazwie **InstalledSCCProviders** w obszarze **SourceCodeControlProvider** podklucza, a następnie umieścić jednego wpisu tego podklucza.  

    Nazwa tego wpisu jest czytelny dla użytkownika nazwa dostawcy, (taka sama jak wartość określona dla wpisu SCCServerName), a wartość jest jeszcze raz podklucza, który został utworzony w kroku 1. Wzorzec jest **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\<display name>** = *oprogramowania\\< nazwa firmy\> \\< nazwa produktu\>*.  

    Na przykład:  

   |Przykładowy wpis rejestru|Wartość przykładowa|  
   |---------------------------|------------------|  
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|SOFTWARE\Microsoft\SourceSafe|  

   > [!NOTE]
   >  Może istnieć wiele źródła wtyczek kontroli zarejestrowanych w ten sposób. Jest to jak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] znajduje wszystkie zainstalowane wtyczki oparte na interfejsie API wtyczki kontroli źródła.  

## <a name="how-an-ide-locates-the-dll"></a>Sposoby lokalizowania IDE przez biblioteki DLL  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE ma dwa sposoby znajdowania źródła kontrolować biblioteki DLL dodatku plug-in:  

- Znajdź wtyczki kontroli źródła domyślne, a następnie połącz się z nim w trybie dyskretnym.  

- Znajdź wszystkie zarejestrowane źródła wtyczek kontroli, z której użytkownik wybiera jeden.  

  Aby zlokalizować bibliotekę DLL w taki sposób, pierwszy, IDE wygląda w obszarze **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider** podkluczy dla wpisu **ProviderRegKey**. Wskazuje wartość tego wpisu do innego podklucza. IDE następnie szuka wpis o nazwie **SccServerPath** w tym drugiego podklucza w **HKEY_LOCAL_MACHINE**. Wartość tego wpisu wskazuje IDE biblioteki DLL.  

> [!NOTE]
>  IDE nie załadować biblioteki dll z ścieżek względnych (na przykład *.\NewProvider.DLL*). Należy określić pełną ścieżkę do biblioteki DLL (na przykład *c:\Providers\NewProvider.DLL*). To wzmacnia zabezpieczenia środowiska IDE, zapobiegając ładowanie nieautoryzowani lub spersonifikowanego wtyczki bibliotek DLL.  

 Aby zlokalizować bibliotekę DLL w druga metoda, IDE wygląda w obszarze **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders** podkluczy dla wszystkich wpisów. Każdy wpis ma nazwę i wartość. Środowisko IDE Wyświetla listę tych nazw użytkownika. Gdy użytkownik wybierze nazwę, IDE wyszukuje wartość dla wybranej nazwy, która wskazuje podklucza. IDE szuka wpis o nazwie **SccServerPath** w tym podklucza w **HKEY_LOCAL_MACHINE**. Wartość tego wpisu wskazuje IDE poprawne biblioteki DLL.  

 Wtyczka do kontroli źródła musi obsługiwać zarówno sposoby znajdowania biblioteki DLL i w związku z tym, ustawia **ProviderRegKey**, zastępując wszystkie poprzednie ustawienia. Co ważniejsze, jego musi dodać się do listy **InstalledSccProviders** , dzięki czemu użytkownik może mieć szeroki wybór wtyczki kontroli źródła do użycia.  

> [!NOTE]
>  Ponieważ **HKEY_LOCAL_MACHINE** klucz jest używany, wtyczka do kontroli źródła tylko jedna może być rejestrowany jako domyślna wtyczka do kontroli źródła na danym komputerze (jednak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] umożliwia użytkownikom określić, które wtyczka do kontroli źródła Firma chce użyć dla danego rozwiązania). Podczas procesu instalacji sprawdź, jeśli wtyczka do kontroli źródła jest już skonfigurowana; Jeśli tak, poproś użytkownika, czy można ustawić nowych kontroli źródła wtyczek instalowanych domyślnie. Podczas odinstalowywania, nie usuwaj innych podkluczy rejestru, które są wspólne dla wszystkich źródła wtyczek kontroli w **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider**; Usuń tylko z określonego podklucza SCC.  

## <a name="how-the-ide-detects-version-1213-support"></a>Jak IDE wykrywa pomocy technicznej w wersji 1.2/1.3  
 Jak jest [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wykryć, czy wtyczka obsługuje funkcjonalność w wersji 1.2 i 1.3 interfejsu API wtyczki kontroli źródła? Aby zadeklarować zaawansowana funkcja, wtyczka do kontroli źródła należy zaimplementować odpowiednich funkcji:  

 Po pierwsze, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sprawdza, czy wartość zwrócona przez wywołanie metody [SccGetVersion](../../extensibility/sccgetversion-function.md). Jego musi być większa lub równa 1.2.  

 Następnie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Określa, czy określonego nowa funkcja jest obsługiwana, sprawdzając `lpSccCaps` argumentu [SccInitialize](../../extensibility/sccinitialize-function.md).  

 Jeśli oba te warunki są spełnione, można wywołać nowych funkcji, które są obsługiwane w wersji 1.2 i 1.3.  

## <a name="see-also"></a>Zobacz także  
 [Wprowadzenie do wtyczek kontroli kodu źródłowego](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)