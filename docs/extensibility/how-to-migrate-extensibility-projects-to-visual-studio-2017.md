---
title: 'Instrukcje: Migrowanie projektów rozszerzalności do programu Visual Studio 2017 | Microsoft Docs'
ms.date: 11/09/2016
ms.topic: how-to
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 37f7259c1133ea51e004b5f6b2061427ff71dea0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905838"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Instrukcje: Migrowanie projektów rozszerzalności do programu Visual Studio 2017

W tym dokumencie wyjaśniono, jak uaktualnić projekty rozszerzalności do programu Visual Studio 2017. Oprócz opisywania sposobu aktualizowania plików projektu opisano również sposób uaktualniania z manifestu rozszerzenia w wersji 2 (VSIX v2) do nowego formatu manifestu VSIX w wersji 3 (VSIX v3).

## <a name="install-visual-studio-2017-with-required-workloads"></a>Zainstaluj program Visual Studio 2017 z wymaganymi obciążeniami

Upewnij się, że instalacja obejmuje następujące obciążenia:

* Programowanie aplikacji klasycznych dla platformy .NET
* Programowanie rozszerzeń programu Visual Studio

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Otwórz rozwiązanie VSIX w programie Visual Studio 2017

Wszystkie projekty VSIX będą wymagały jednokierunkowego uaktualnienia do programu Visual Studio 2017.

Plik projektu (na przykład **. csproj*) zostanie zaktualizowany:

* MinimumVisualStudioVersion — teraz ustawiono 15,0
* OldToolsVersion (jeśli wcześniej istnieje) — teraz ustawiona na 14,0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Aktualizowanie pakietu NuGet Microsoft. VSSDK. BuildTools

> [!Note]
> Jeśli rozwiązanie nie odwołuje się do pakietu NuGet Microsoft. VSSDK. BuildTools, można pominąć ten krok.

Aby możliwe było skompilowanie rozszerzenia w nowym formacie VSIX v3 (wersja 3), Twoje rozwiązanie będzie musiało zostać skompilowane przy użyciu nowych narzędzi kompilacji VSSDK. Zostanie ona zainstalowana z programem Visual Studio 2017, ale rozszerzenie VSIX v2 może zawierać odwołanie do starszej wersji za pośrednictwem programu NuGet. W takim przypadku konieczne będzie ręczne zainstalowanie aktualizacji pakietu NuGet Microsoft. VSSDK. BuildTools dla Twojego rozwiązania.

Aby zaktualizować odwołania NuGet do Microsoft. VSSDK. BuildTools:

* Kliknij prawym przyciskiem myszy rozwiązanie i wybierz polecenie **Zarządzaj pakietami NuGet dla rozwiązania**.
* Przejdź do karty **aktualizacje** .
* Wybierz **Microsoft. VSSDK. BuildTools (Najnowsza wersja)**.
* Naciśnij przycisk **Aktualizuj**.

![Narzędzia kompilacji VSSDK](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>Wprowadzanie zmian do manifestu rozszerzenia VSIX

Aby upewnić się, że instalacja programu Visual Studio przez użytkownika ma wszystkie zestawy wymagane do uruchomienia rozszerzenia, określ wszystkie wstępnie wymagane składniki lub pakiety w pliku manifestu rozszerzenia. Gdy użytkownik próbuje zainstalować rozszerzenie, Instalator VSIX sprawdzi, czy zostały zainstalowane wszystkie wymagania wstępne. Jeśli brakuje niektórych, użytkownik zostanie poproszony o zainstalowanie brakujące składniki w ramach procesu instalacji rozszerzenia.

> [!Note]
> Jako warunek wstępny dla wszystkich rozszerzeń należy określić składnik edytora podstawowego programu Visual Studio.

* Edytuj plik manifestu rozszerzenia (zwykle nosi nazwę *source. Extension. vsixmanifest*).
* Upewnij się, że `InstallationTarget` zawiera 15,0.
* Dodaj wymagane wymagania wstępne instalacji (jak pokazano w poniższym przykładzie).
  * Zalecamy określenie wyłącznie identyfikatorów składników na potrzeby instalacji wstępnej.
  * Zapoznaj się z sekcją na końcu tego dokumentu, aby uzyskać [instrukcje dotyczące identyfikowania identyfikatorów składników](#find-component-ids).

Przykład:

```xml
<PackageManifest>
 ...
    <Prerequisites>
        <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Component.DiagnosticTools" Version="[15.0.25814.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Shell.12.0" Version="[12.0]" />
    </Prerequisites>
 ...
</PackageManifest>
```

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Opcja: Użyj projektanta, aby wprowadzić zmiany do manifestu rozszerzenia VSIX

Zamiast bezpośrednio edytować manifest XML, można użyć karty nowe **wymagania wstępne** w Projektancie manifestów, aby wybrać wymagania wstępne, a plik XML zostanie zaktualizowany.

> [!Note]
> Projektant manifestów zezwoli tylko na wybór składników (nie obciążeń lub pakietów) zainstalowanych w bieżącym wystąpieniu programu Visual Studio. Jeśli musisz dodać wymaganie wstępne dla obciążenia, pakietu lub składnika, który nie jest aktualnie zainstalowany, edytuj plik XML manifestu bezpośrednio.

* Plik Open *source. Extension. vsixmanifest [Design]* .
* Wybierz kartę **wymagania wstępne** i naciśnij przycisk **Nowy** .

   ![Projektant manifestu VSIX](media/vsix-manifest-designer.png)

* Zostanie otwarte okno **Dodaj nowe wymaganie wstępne** .

   ![Dodaj wymaganie wstępne VSIX](media/add-vsix-prerequisite.png)

* Kliknij listę rozwijaną **Nazwa** i wybierz żądany warunek wstępny.
* W razie potrzeby zaktualizuj wersję.

   > [!Note]
   > Pole wersja zostanie wstępnie wypełnione wersją aktualnie zainstalowanego składnika, z zakresem obejmującym do (ale nie włącznie) następną wersję główną składnika.

   ![Dodaj wymaganie wstępne Roslyn](media/add-roslyn-prerequisite.png)

* Naciśnij przycisk **OK**.

## <a name="update-debug-settings-for-the-project"></a>Aktualizuj ustawienia debugowania dla projektu

Jeśli chcesz debugować rozszerzenie w eksperymentalnym wystąpieniu programu Visual Studio, upewnij się, że ustawienia projektu dla **Debug**  >  **akcji Rozpocznij** debugowanie mają wartość **Uruchom zewnętrzny program:** Value ustawiony jako plik *devenv.exe* instalacji programu Visual Studio 2017.

Może wyglądać następująco: *C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe*

![Uruchom program zewnętrzny](media/start-external-program.png)

> [!Note]
> Akcja uruchamiania debugowania jest zazwyczaj przechowywana w pliku *. csproj. User* . Ten plik jest zwykle zawarty w pliku *. gitignore* , dlatego nie jest zwykle zapisywany z innymi plikami projektu w przypadku zatwierdzenia do kontroli źródła. W związku z tym w przypadku ściągnięcia rozwiązania z kontroli źródła prawdopodobnie projekt nie będzie miał wartości ustawionych dla akcji Rozpocznij. Nowe projekty VSIX utworzone za pomocą programu Visual Studio 2017 będą mieć utworzony plik *. csproj. User* z wartościami domyślnymi wskazującymi bieżący katalog instalacyjny programu Visual Studio. Jednak w przypadku migrowania rozszerzenia VSIX v2 prawdopodobnie plik *. csproj. User* będzie zawierał odwołania do poprzedniego katalogu instalacyjnego wersji programu Visual Studio. Ustawienie wartości **Debug**  >  **akcji Rozpocznij** debugowanie spowoduje, że podczas próby debugowania rozszerzenia zostanie uruchomione poprawne wystąpienie eksperymentalne programu Visual Studio.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Sprawdź, czy rozszerzenie jest poprawnie skompilowane (jako VSIX v3)

* Kompiluj projekt VSIX.
* Rozpakuj wygenerowany VSIX.
  * Domyślnie plik VSIX przebywa wewnątrz *bin/debug* lub *bin/Release* jako *[YourCustomExtension]. vsix*.
  * Zmień nazwę pliku *VSIX* na *zip* , aby łatwo wyświetlić jego zawartość.
* Sprawdź, czy istnieją trzy pliki:
  * *rozszerzenie. vsixmanifest*
  * *manifest.jsna*
  * *catalog.jsna*

## <a name="check-when-all-required-prerequisites-are-installed"></a>Sprawdź, czy zainstalowano wszystkie wymagane wymagania wstępne

Sprawdź, czy VSIX zostały pomyślnie zainstalowane na komputerze, na którym zainstalowano wszystkie wymagane wymagania wstępne.

> [!Note]
> Przed zainstalowaniem dowolnego rozszerzenia Zamknij wszystkie wystąpienia programu Visual Studio.

Podjęto próbę zainstalowania rozszerzenia:

* W programie Visual Studio 2017

![Instalator VSIX w programie Visual Studio 2017](media/vsixinstaller-vs-2017.png)

* Opcjonalne: Sprawdź poprzednie wersje programu Visual Studio.
  * Udowadnia zgodność z poprzednimi wersjami.
  * Należy korzystać z programu Visual Studio 2012, Visual Studio 2013, Visual Studio 2015.
* Opcjonalnie: Sprawdź, czy narzędzie sprawdzania wersji Instalatora VSIX oferuje wybór wersji.
  * Obejmuje poprzednie wersje programu Visual Studio (jeśli jest zainstalowana).
  * Zawiera program Visual Studio 2017.

Jeśli program Visual Studio został niedawno otwarty, może zostać wyświetlone okno dialogowe podobne do tego:

![procesy uruchamiania programu vs](media/vs-running-processes.png)

Zaczekaj na zamknięcie procesów lub ręcznie Zakończ zadania. Procesy można znaleźć według nazwy lub identyfikatora PID wymienionego w nawiasach.

> [!Note]
> Te procesy nie zostaną automatycznie zamknięte w trakcie działania wystąpienia programu Visual Studio. Upewnij się, że zamknięto wszystkie wystąpienia programu Visual Studio na komputerze — w tym te pochodzące od innych użytkowników, a następnie ponów próbę.

## <a name="check-when-missing-the-required-prerequisites"></a>Sprawdź, kiedy brakuje wymaganych wymagań wstępnych

* Podjęto próbę zainstalowania rozszerzenia na komputerze z programem Visual Studio 2017, który nie zawiera wszystkich składników zdefiniowanych w wymaganiach wstępnych (powyżej).
* Sprawdź, czy podczas instalacji zidentyfikowano brakujące składniki/s, a następnie Wyświetl listę ich jako warunek wstępny w Instalator VSIX.
* Uwaga: podniesienie uprawnień będzie wymagane, jeśli wymagane jest zainstalowanie jakichkolwiek wymagań wstępnych z rozszerzeniem.

![Instalator VSIX brak wymagania wstępnego](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>Decydowanie o składnikach

Podczas wyszukiwania zależności można zamapować jedną zależność na wiele składników. Aby określić, które zależności należy określić jako wymaganie wstępne, zalecamy wybranie składnika, który ma funkcjonalność podobną do Twojego rozszerzenia, a także uwzględnienie użytkowników i rodzaju składników, które prawdopodobnie zainstalują lub nie będą mieć na nie znaczenia. Zalecamy również Kompilowanie rozszerzeń w taki sposób, w jaki wymagane wymagania wstępne spełnią tylko minimum, które umożliwią uruchomienie rozszerzenia i w przypadku dodatkowych funkcji, jeśli nie zostaną wykryte pewne składniki.

Aby zapewnić dalsze wskazówki, zidentyfikowano kilka wspólnych typów rozszerzeń i ich sugerowane wymagania wstępne:

Typ rozszerzenia | Nazwa wyświetlana | ID
--- | --- | ---
Edytor | Visual Studio Core Editor | Microsoft. VisualStudio. Component. CoreEditor
Roslyn | C# i Visual Basic | Microsoft. VisualStudio. Component. Roslyn. LanguageServices
WPF | Rdzeń obciążeń zarządzanych komputerów stacjonarnych | Microsoft. VisualStudio. Component. ManagedDesktop. Core
Debuger | Debuger just in Time | Microsoft. VisualStudio. Component. Debugger. JustInTime

## <a name="find-component-ids"></a>Znajdowanie identyfikatorów składników

Lista składników posortowanych przez program Visual Studio jest w [obciążeniu i identyfikatorach składników programu Visual studio 2017](/visualstudio/install/workload-and-component-ids?view=vs-2019). Użyj tych identyfikatorów składników dla identyfikatorów wymagań wstępnych w manifeście.

Jeśli nie masz pewności, który składnik zawiera określony plik binarny, Pobierz [Arkusz danych mapowania binarnego składnika >](https://aka.ms/vs2017componentid-binaries).

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017-ComponentBinaryMapping.xlsx

Arkusz programu Excel zawiera cztery kolumny: **nazwę składnika**, **ComponentID**, **wersję**i **nazwy plików binarnych/nazw**.  Filtrów można użyć do wyszukiwania i znajdowania określonych składników i plików binarnych.

W przypadku wszystkich odwołań należy najpierw określić, które z nich znajdują się w składniku podstawowego edytora (Microsoft. VisualStudio. Component. CoreEditor).  Minimalnym wymaganiem jest określenie podstawowego składnika edytora jako wymagań wstępnych dla wszystkich rozszerzeń. Odwołań, które nie znajdują się w podstawowym edytorze, Dodaj filtry w sekcji **nazwy plików binarnych/nazw** , aby znaleźć składniki, które mają dowolne z podzestawów tych odwołań.

Przykłady:

* Jeśli masz rozszerzenie debugera i wiesz, że projekt zawiera odwołanie do *VSDebugEng.dll* i *VSDebug.dll*, kliknij przycisk Filtr w nagłówku **plików binarnych/nazw plików** .  Wyszukaj ciąg "VSDebugEng.dll" i wybierz pozycję *OK*.  Kliknij ponownie przycisk Filtr w nagłówku plików **binarnych/nazw plików** , a następnie wyszukaj ciąg "VSDebug.dll".  Zaznacz pole wyboru **Dodaj bieżące zaznaczenie do filtru** i wybierz **przycisk OK**.  Sprawdź teraz **nazwę składnika** , aby znaleźć składnik, który jest najbardziej powiązany z typem rozszerzenia. W tym przykładzie należy wybrać debuger just in Time i dodać go do vsixmanifest.
* Jeśli wiesz, że projekt zajmuje się elementami debugera, możesz wyszukać "debuger" w polu wyszukiwania filtru, aby zobaczyć, jakie składniki zawierają debuger w nazwie.

## <a name="specify-a-visual-studio-2017-release"></a>Określ wersję 2017 programu Visual Studio

Jeśli rozszerzenie wymaga określonej wersji programu Visual Studio 2017, na przykład zależy od funkcji wydanej w 15,3, należy określić numer kompilacji w **INSTALLATIONTARGET**VSIX. Na przykład wersja 15,3 ma numer kompilacji "15.0.26730.3". W [tym miejscu](../install/visual-studio-build-numbers-and-release-dates.md)możesz zobaczyć mapowanie wydań, aby kompilować numery. Użycie numeru wydania "15,3" nie będzie działało poprawnie.

Jeśli rozszerzenie wymaga 15,3 lub nowszego, należy zadeklarować **wersję InstallationTarget** jako [15.0.26730.3, 16,0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```
