---
title: 'Instrukcje: Instalowanie wtyczki kontroli źródła | Microsoft Docs'
description: Dowiedz się, jak zainstalować wtyczkę kontroli źródła w programie Visual Studio, integrując ją z interfejsem API dodatku plug-in kontroli źródła programu Visual Studio i rejestrując jego bibliotekę DLL.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4a0798cb7763ff2766d2de2bb00a80759be8fd3e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078815"
---
# <a name="how-to-install-a-source-control-plug-in"></a>Instrukcje: Instalowanie wtyczki kontroli źródła
Tworzenie wtyczki kontroli źródła obejmuje trzy kroki:

1. Utwórz bibliotekę DLL z funkcjami zdefiniowanymi w sekcji Dokumentacja interfejsu API wtyczki kontroli źródła w tej dokumentacji.

2. Zaimplementuj funkcje zdefiniowane w interfejsie API kontroli źródła. Gdy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] są dla niego wywołania, należy udostępnić interfejsy i okna dialogowe dostępne z wtyczki.

3. Zarejestruj bibliotekę DLL, wprowadzając odpowiednie wpisy rejestru.

## <a name="integration-with-visual-studio"></a>Integracja z programem Visual Studio
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obsługuje wtyczki kontroli źródła, które są zgodne z interfejsem API kontroli źródła.

### <a name="register-the-source-control-plug-in"></a>Rejestrowanie wtyczki kontroli źródła
 Zanim uruchomione zintegrowane środowisko programistyczne (IDE) może wywołać system kontroli źródła, należy najpierw znaleźć bibliotekę DLL wtyczki kontroli źródła, która eksportuje interfejs API.

#### <a name="to-register-the-source-control-plug-in-dll"></a>Aby zarejestrować plik DLL wtyczki kontroli źródła

1. Dodaj dwa wpisy w kluczu **HKEY_LOCAL_MACHINE** w podkluczu **oprogramowania** , który określa podklucz nazwy firmy, po którym następuje podklucz nazwy produktu. Wzorzec jest **\\ \<company name> \\HKEY_LOCAL_MACHINE\SOFTWARE\<product name> \\ wartością \<entry>**  =  . Te dwa wpisy są zawsze nazywane **SCCServerName** i **SCCServerPath**. Każdy jest ciągiem regularnym.

    Na przykład jeśli Twoja firma to firma Microsoft, a Twój produkt kontroli źródła nosi nazwę SourceSafe, ta ścieżka rejestru byłaby **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe**. W tym podkluczu pierwszy wpis, **SCCServerName**, jest odczytany przez użytkownika ciąg nazewnictwa produktu. Drugi wpis, **SCCServerPath**, jest pełną ścieżką do biblioteki DLL wtyczki kontroli źródła, z którą ma nawiązać połączenie IDE. Poniżej przedstawiono przykładowe wpisy rejestru:

   |Wpis rejestru przykładowego|Wartość przykładowa|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Program Microsoft Visual SourceSafe|
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|*c:\vss\win32\ssscc.dll*|

   > [!NOTE]
   > SCCServerPath to pełna ścieżka do wtyczki programu SourceSafe. Wtyczka do kontroli źródła będzie używać innych nazw firmowych i produktów, ale te same ścieżki wpisów rejestru.

2. Poniższe opcjonalne wpisy rejestru mogą służyć do modyfikacji zachowania wtyczki kontroli źródła. Te wpisy przechodzą do tego samego podklucza, co **SCCServerName** i **SCCServerPath**.

   - Wpisu **HideInVisualStudioregistry** można użyć, jeśli nie chcesz, aby dana wtyczka kontroli źródła była wyświetlana na liście **wyboru wtyczki** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Ten wpis wpłynie również na automatyczne przełączanie do wtyczki kontroli źródła. Jednym z możliwych użycia dla tego wpisu jest dostarczenie pakietu kontroli źródła, który zastępuje wtyczkę kontroli źródła, ale chcesz ułatwić użytkownikowi przeprowadzenie migracji z programu przy użyciu wtyczki kontroli źródła do pakietu kontroli źródła. Po zainstalowaniu pakietu kontroli źródła ustawia ten wpis rejestru, który ukrywa wtyczkę.

      **HideInVisualStudio** jest wartością typu DWORD i jest ustawiona na *1* , aby ukryć wtyczkę lub *0* w celu wyświetlenia wtyczki. Jeśli wpis rejestru nie jest wyświetlany, domyślnym zachowaniem jest wyświetlenie wtyczki.

   - Wpis rejestru **DisableSccManager** może służyć do wyłączania lub ukrywania opcji menu **uruchamiania \<Source Control Server>** , która jest zwykle wyświetlana w podmenu   >  **kontroli źródła** pliku. Wybranie tej opcji menu wywołuje funkcję [SccRunScc](../../extensibility/sccrunscc-function.md) . Wtyczka do kontroli źródła może nie obsługiwać programu zewnętrznego, w związku z czym można wyłączyć lub nawet ukryć opcję menu **uruchamiania** .

      **DisableSccManager** jest wartością typu DWORD i jest ustawiona na *0* , aby włączyć opcję menu **uruchamiania \<Source Control Server>** , ustawić wartość *1* , aby wyłączyć opcję menu i ustawić wartość *2* , aby ukryć opcję menu. Jeśli ten wpis rejestru nie jest wyświetlany, domyślnym zachowaniem jest wyświetlenie opcji menu.

   | Wpis rejestru przykładowego | Wartość przykładowa |
   | - |--------------|
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio | 1 |
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager | 1 |

3. Dodaj podklucz **SourceCodeControlProvider** w kluczu **HKEY_LOCAL_MACHINE** w podkluczu **oprogramowania** .

    W tym podkluczu wpis rejestru **ProviderRegKey** jest ustawiony na ciąg, który reprezentuje podklucz umieszczony w rejestrze w kroku 1. Wzorzec to **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey**  =  *Software \\<nazwa firmy \> \\<nazwa \> produktu*.

    Poniżej znajduje się Przykładowa zawartość dla tego podklucza.

   |Wpis rejestru|Wartość przykładowa|
   |--------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|

   > [!NOTE]
   > Wtyczka do kontroli źródła będzie używać tego samego podklucza i nazw wpisów, ale wartość będzie różna.

4. Utwórz podklucz o nazwie **InstalledSccProviders** w podkluczu **SourceCodeControlProvider** , a następnie umieść jeden wpis w tym podkluczu.

    Nazwa tego wpisu to nazwa dostawcy (taka sama jak wartość określona dla wpisu SCCServerName), a wartość to, po ponownym uruchomieniu, podklucz utworzony w kroku 1. Wzorzec jest **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\<nazwa \> wyświetlana**  =  *oprogramowania \\<nazwa firmy \> \\<nazwa \> produktu*.

    Na przykład:

   |Wpis rejestru przykładowego|Wartość przykładowa|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|SOFTWARE\Microsoft\SourceSafe|

   > [!NOTE]
   > W ten sposób można zarejestrować wiele wtyczek kontroli źródła. W ten sposób znajduje się wszystkie zainstalowane wtyczki usługi Plug-in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] oparte na interfejsie API kontroli źródła.

## <a name="how-an-ide-locates-the-dll"></a>Sposób lokalizowania biblioteki DLL przez środowisko IDE
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE ma dwa sposoby znajdowania biblioteki DLL wtyczki kontroli źródła:

- Znajdź domyślną wtyczkę kontroli źródła i Połącz się z nią w trybie dyskretnym.

- Znajdź wszystkie zarejestrowane wtyczki kontroli źródła, z których użytkownik wybiera jeden.

  Aby zlokalizować bibliotekę DLL w pierwszej kolejności, środowisko IDE będzie wyglądało w podkluczu **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider** dla wpisu **ProviderRegKey**. Wartość tego wpisu wskazuje na inny podklucz. IDE szuka wpisu o nazwie **SCCServerPath** w tym drugim podkluczu w **HKEY_LOCAL_MACHINE**. Wartość tego wpisu wskazuje IDE do biblioteki DLL.

> [!NOTE]
> IDE nie ładuje bibliotek DLL ze ścieżek względnych (na przykład *.\NewProvider.DLL*). Należy określić pełną ścieżkę do biblioteki DLL (na przykład *c:\Providers\NewProvider.DLL*). Zwiększa to bezpieczeństwo środowiska IDE, uniemożliwiając ładowanie nieautoryzowanych lub personifikowanych bibliotek DLL wtyczek.

 Aby zlokalizować bibliotekę DLL w drugi sposób, środowisko IDE będzie wyglądało w podkluczu **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders** dla wszystkich wpisów. Każdy wpis ma nazwę i wartość. IDE wyświetla listę tych nazw dla użytkownika. Gdy użytkownik wybierze nazwę, IDE znajdzie wartość wybranej nazwy, która wskazuje podklucz. IDE szuka wpisu o nazwie **SCCServerPath** w tym podkluczu w obszarze **HKEY_LOCAL_MACHINE**. Wartość tego wpisu wskazuje IDE do poprawnej biblioteki DLL.

 Wtyczka do kontroli źródła musi obsługiwać oba sposoby znajdowania biblioteki DLL, a w związku z tym ustawia **ProviderRegKey**, zastępując wszystkie poprzednie ustawienia. Co ważniejsze, należy dodać sam do listy **InstalledSccProviders** , aby użytkownik mógł wybrać wtyczkę kontroli źródła, która ma być używana.

> [!NOTE]
> Ponieważ klucz **HKEY_LOCAL_MACHINE** jest używany, tylko jedna wtyczka do kontroli źródła może być zarejestrowana jako domyślna Wtyczka kontroli źródła na danej maszynie (Jednakże [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] umożliwia użytkownikom określenie wtyczki kontroli źródła, które chcą rzeczywiście używać dla danego rozwiązania). W trakcie procesu instalacji sprawdź, czy wtyczka kontroli źródła została już ustawiona. Jeśli tak, poproszenie użytkownika o to, czy nie ustawili nowej wtyczki kontroli źródła, która jest instalowana domyślnie. Podczas dezinstalacji nie należy usuwać innych podkluczy rejestru, które są wspólne dla wszystkich wtyczek kontroli źródła w **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider**; Usuń tylko określony podklucz SCC.

## <a name="how-the-ide-detects-version-1213-support"></a>Jak środowisko IDE wykrywa obsługę wersji 1.2/1.3
 Jak program [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wykrywa, czy wtyczka obsługuje interfejs API wtyczki kontroli źródła w wersji 1,2 i 1,3? Aby zadeklarować zaawansowaną funkcję, wtyczka do kontroli źródła musi implementować odpowiednią funkcję:

 Najpierw [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sprawdza wartość zwracaną przez wywołanie [SccGetVersion](../../extensibility/sccgetversion-function.md). Musi być większe lub równe 1,2.

 Następnie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] określa, czy konkretne nowe możliwości są obsługiwane przez badanie `lpSccCaps` argumentu w [SccInitialize](../../extensibility/sccinitialize-function.md).

 Jeśli oba te warunki są spełnione, można wywołać nowe funkcje obsługiwane w wersjach 1,2 i 1,3.

## <a name="see-also"></a>Zobacz też
- [Wprowadzenie do wtyczek kontroli źródła](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
