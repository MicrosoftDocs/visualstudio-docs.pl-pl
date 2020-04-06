---
title: 'Jak: Instalowanie wtyczki kontroli źródła | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c0ac87aec3d6ac2532909772238e020e33bf78f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707990"
---
# <a name="how-to-install-a-source-control-plug-in"></a>Jak: Instalowanie wtyczki kontroli źródła
Tworzenie wtyczki kontroli źródła obejmuje trzy kroki:

1. Utwórz bibliotekę DLL z funkcjami zdefiniowanymi w sekcji odwołania do interfejsu API wtyczki źródła w tej dokumentacji.

2. Zaimplementuj funkcje zdefiniowane przez wtyczkę interfejsu API formantu źródła. Gdy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zostanie to wywołane, udostępnij interfejsy i okna dialogowe z wtyczki.

3. Zarejestruj bibliotekę DLL, dokonując odpowiednich wpisów rejestru.

## <a name="integration-with-visual-studio"></a>Integracja z programem Visual Studio
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]obsługuje wtyczki kontroli źródła, które są zgodne z interfejsem API wtyczki kontroli źródła.

### <a name="register-the-source-control-plug-in"></a>Zarejestruj wtyczkę kontroli źródła
 Zanim uruchomione zintegrowane środowisko programistyczne (IDE) może wywołać do systemu kontroli źródła, należy najpierw znaleźć bibliotekę DLL dodatku DLL wtyczki kontroli źródła, która eksportuje interfejs API.

#### <a name="to-register-the-source-control-plug-in-dll"></a>Aby zarejestrować bibliotekę DLL wtyczki formantu źródła

1. Dodaj dwa wpisy pod **kluczem HKEY_LOCAL_MACHINE** w podkluczu **PROGRAMU,** który określa podklucz nazwy firmy, po którym następuje podklucz nazwa produktu. Wzorzec jest **HKEY_LOCAL_MACHINE\SOFTWARE\\\<nazwa firmy \\ \<>nazwa produktu \\ \<>wpisu>**  =  *wartość*. Dwa wpisy są zawsze nazywane **SCCServerName** i **SCCServerPath**. Każdy z nich jest zwykłym ciągiem.

    Jeśli na przykład nazwa firmy to Firma Microsoft, a produkt kontroli źródła nosi nazwę SourceSafe, ta ścieżka rejestru będzie **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe**. W tym podkluczycie pierwszy wpis, **SCCServerName**, jest ciągiem czytelnym dla użytkownika, który nazewnictwo nazewnictwa produktu. Drugi wpis, **SCCServerPath**, to pełna ścieżka do biblioteki DLL wtyczki formantu źródła, z którą ide powinien się połączyć. Poniżej przedstawiono przykładowe wpisy rejestru:

   |Przykładowy wpis rejestru|Wartość przykładowa|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Usługa źródło wizualna firmy Microsoft|
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|*c:\vss\win32\ssscc.dll*|

   > [!NOTE]
   > SCCServerPath to pełna ścieżka do wtyczki SourceSafe. Wtyczka kontroli źródła będzie używać różnych nazw firm i produktów, ale tych samych ścieżek wprowadzania rejestru.

2. Następujące opcjonalne wpisy rejestru mogą służyć do modyfikowania zachowania wtyczki kontroli źródła. Te wpisy idą w tym samym podkluczu co **SccServerName** i **SccServerPath**.

   - Wpis **HideInVisualStudioregistry** może być używany, jeśli nie chcesz, aby wtyczka kontroli źródła pojawiała się na liście **Wyboru wtyczek** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Ten wpis wpłynie również na automatyczne przełączanie do wtyczki kontroli źródła. Jednym z możliwych zastosowań dla tego wpisu jest, jeśli podasz pakiet kontroli źródła, który zastępuje wtyczkę kontroli źródła, ale chcesz ułatwić użytkownikowi migrację z korzystania z wtyczki kontroli źródła do pakietu kontroli źródła. Po zainstalowaniu pakietu kontroli źródła ustawia ten wpis rejestru, który ukrywa wtyczkę.

      **HideInVisualStudio** jest wartością DWORD i jest ustawiona na *1,* aby ukryć wtyczkę lub *0,* aby wyświetlić wtyczkę. Jeśli wpis rejestru nie jest wyświetlany, domyślnym zachowaniem jest pokazanie wtyczki.

   - Wpis rejestru **DisableSccManager** może służyć do wyłączania lub ukrywania opcji menu **Uruchom \<serwer kontroli źródła>,** która zwykle pojawia się w podmenu**Kontrola źródła** **plików.** >  Wybranie tej opcji menu wywołuje funkcję [SccRunScc.](../../extensibility/sccrunscc-function.md) Wtyczka kontroli źródła może nie obsługiwać zewnętrznego programu i dlatego można wyłączyć lub nawet ukryć opcję menu **Uruchom.**

      **DisableSccManager** jest wartością DWORD i jest ustawiona na *0,* aby włączyć opcję menu **Uruchom \<serwer kontroli źródła>,** ustawioną na *1,* aby wyłączyć opcję menu, i ustawioną na *2,* aby ukryć opcję menu. Jeśli ten wpis rejestru nie jest wyświetlany, domyślnym zachowaniem jest wyświetlenie opcji menu.

   | Przykładowy wpis do rejestru | Wartość przykładowa |
   | - |--------------|
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio | 1 |
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager | 1 |

3. Dodaj podklucz **SourceCodeControlProvider**, pod kluczem **HKEY_LOCAL_MACHINE** w podkluczu **SOFTWARE.**

    W ramach tego podklucza wpis rejestru **ProviderRegKey** jest ustawiony na ciąg reprezentujący podklucz, który został umieszczony w rejestrze w kroku 1. Wzorzec jest **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey** = *SOFTWARE\\<nazwa\> \\ firmy<nazwę\>produktu*.

    Poniżej przedstawiono przykładową zawartość tego podklucza.

   |Wpis rejestru|Wartość przykładowa|
   |--------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|OPROGRAMOWANIE\Microsoft\SourceSafe|

   > [!NOTE]
   > Wtyczka formantu źródła będzie używać tych samych nazw podkluczów i wpisów, ale wartość będzie inna.

4. Utwórz podklucz o nazwie **InstalledSCCProviders** w podkluczie **sourcecodecontrolprovider,** a następnie umieść jeden wpis w tym podkluczu.

    Nazwa tego wpisu jest czytelną dla użytkownika nazwą dostawcy (taką samą jak wartość określona dla wpisu SCCServerName), a wartość jest ponownie podkluczem utworzonym w kroku 1. Wzorzec jest **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\<wyświetlaną\>nazwę** = *SOFTWARE\\<\> \\ nazwa firmy\><nazwa produktu*.

    Przykład:

   |Przykładowy wpis do rejestru|Wartość przykładowa|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|OPROGRAMOWANIE\Microsoft\SourceSafe|

   > [!NOTE]
   > W ten sposób może być rejestrowanych wiele wtyczek kontroli źródła. W ten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sposób można znaleźć wszystkie zainstalowane wtyczki oparte na interfejsie API wtyczek dodatku Source Control Plug-in.

## <a name="how-an-ide-locates-the-dll"></a>Jak ide lokalizuje bibliotekę DLL
 IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ma dwa sposoby znajdowania dodatku DLL dodatku DLL wtyczki kontroli źródła:

- Znajdź domyślną wtyczkę kontroli źródła i połącz się z nią w trybie cichym.

- Znajdź wszystkie zarejestrowane wtyczki kontroli źródła, z których użytkownik wybierze jedną.

  Aby najpierw zlokalizować bibliotekę DLL, ide szuka **pod kluczem HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider** wpisu **ProviderRegKey**. Wartość tego wpisu wskazuje na inny podklucz. IDE następnie wyszukuje wpis o nazwie **SccServerPath** w tym drugim podkluczu w obszarze **HKEY_LOCAL_MACHINE**. Wartość tego wpisu wskazuje IDE do biblioteki DLL.

> [!NOTE]
> IDE nie ładuje bibliotek DLL ze ścieżek względnych (na przykład *.\NewProvider.DLL).* Należy określić pełną ścieżkę do biblioteki DLL (na przykład *c:\Providers\NewProvider.DLL*). Zwiększa to bezpieczeństwo IDE, zapobiegając ładowaniu nieautoryzowanych lub personifikowanych bibliotek DLL dodatków Wtyczek.

 Aby zlokalizować bibliotekę DLL w drugi sposób, IDE wygląda pod **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders** podklucz dla wszystkich wpisów. Każdy wpis ma nazwę i wartość. IDE wyświetla listę tych nazw do użytkownika. Gdy użytkownik wybierze nazwę, IDE znajduje wartość dla wybranej nazwy, która wskazuje podklucz. IDE wyszukuje wpis o nazwie **SccServerPath** w tym podkluczu w obszarze **HKEY_LOCAL_MACHINE**. Wartość tego wpisu wskazuje IDE do poprawnej biblioteki DLL.

 Wtyczka kontroli źródła musi obsługiwać oba sposoby znajdowania biblioteki DLL i w związku z tym ustawia **ProviderRegKey,** zastępując poprzednie ustawienie. Co ważniejsze, musi dodać się do listy **InstalledSccProviders** więc użytkownik może mieć wybór, które źródło kontroli plug-in do użycia.

> [!NOTE]
> Ponieważ używany jest **HKEY_LOCAL_MACHINE** klucz, tylko jedna wtyczka kontroli źródła może być zarejestrowana jako domyślna wtyczka formantu źródła na danym komputerze (jednak pozwala użytkownikom określić, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] które wtyczki kontroli źródła, które mają faktycznie używać dla określonego rozwiązania). Podczas procesu instalacji sprawdź, czy wtyczka kontroli źródła jest już ustawiona; jeśli tak, zapytaj użytkownika, czy ustawić nową wtyczkę formantu źródła zainstalowaną jako domyślną. Podczas dezinstalacji nie należy usuwać innych podkluczy rejestru, które są wspólne dla wszystkich wtyczek kontroli źródła w **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider;** usuń tylko konkretny podklucz SCC.

## <a name="how-the-ide-detects-version-1213-support"></a>Jak ide wykrywa obsługę wersji 1.2/1.3
 Jak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wykryć, czy wtyczka obsługuje interfejs API wtyczki source control w wersji 1.2 i 1.3? Aby zadeklarować zaawansowane możliwości, wtyczka kontroli źródła musi implementować odpowiednią funkcję:

 Najpierw [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sprawdza wartość zwróconą przez wywołanie [SccGetVersion](../../extensibility/sccgetversion-function.md). Musi być większa lub równa 1.2.

 Następnie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] określa, czy konkretne nowe możliwości jest obsługiwany `lpSccCaps` przez badanie argumentu na [SccInitialize](../../extensibility/sccinitialize-function.md).

 Jeśli oba te warunki są spełnione, można wywołać nowe funkcje obsługiwane w wersjach 1.2 i 1.3.

## <a name="see-also"></a>Zobacz też
- [Wprowadzenie do wtyczek kontroli źródła](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
