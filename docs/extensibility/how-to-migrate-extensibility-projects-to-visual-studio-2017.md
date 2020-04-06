---
title: 'Jak: Migrowanie projektów rozszerzalności do programu Visual Studio 2017 | Dokumenty firmy Microsoft'
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: b0cae0261b185ee08400e5f3d25735634663f54a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710977"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Jak: Migrowanie projektów rozszerzalności do programu Visual Studio 2017

W tym dokumencie wyjaśniono, jak uaktualnić projekty rozszerzalności do programu Visual Studio 2017. Oprócz opisu sposobu aktualizowania plików projektu opisano również sposób uaktualniania z manifestu rozszerzenia w wersji 2 (VSIX v2) do nowej wersji 3 format manifestu VSIX (VSIX v3).

## <a name="install-visual-studio-2017-with-required-workloads"></a>Instalowanie programu Visual Studio 2017 z wymaganymi obciążeniami

Upewnij się, że instalacja obejmuje następujące obciążenia:

* Programowa firma .NET
* Programowanie rozszerzeń programu Visual Studio

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Otwórz rozwiązanie VSIX w programie Visual Studio 2017

Wszystkie projekty VSIX będzie wymagać głównej wersji jednokierunkowego uaktualnienia do programu Visual Studio 2017.

Plik projektu (na przykład **.csproj*) zostanie zaktualizowany:

* MinimumVisualStudioVersion - teraz ustawiona na 15,0
* OldToolsVersion (jeśli wcześniej istniał) - teraz ustawiono na 14.0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Aktualizowanie pakietu NuGet pakietu Microsoft.VSSDK.BuildTools

> [!Note]
> Jeśli rozwiązanie nie odwołuje się do pakietu Microsoft.VSSDK.BuildTools NuGet, można pominąć ten krok.

Aby utworzyć rozszerzenie w nowym formacie VSIX v3 (wersja 3), rozwiązanie będzie musiało zostać utworzone przy łączeniu nowych narzędzi kompilacji VSSDK. Zostanie to zainstalowane w programie Visual Studio 2017, ale rozszerzenie VSIX v2 może być posiadanie odwołania do starszej wersji za pośrednictwem NuGet. Jeśli tak, należy ręcznie zainstalować aktualizację pakietu Microsoft.VSSDK.BuildTools NuGet dla rozwiązania.

Aby zaktualizować odwołania NuGet do witryn Microsoft.VSSDK.BuildTools:

* Kliknij prawym przyciskiem myszy rozwiązanie i wybierz pozycję **Zarządzaj pakietami NuGet dla rozwiązania**.
* Przejdź do karty **Aktualizacje.**
* Wybierz **pozycję Microsoft.VSSDK.BuildTools (najnowsza wersja).**
* Naciśnij **przycisk Aktualizuj**.

![Narzędzia do tworzenia vssdk](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>Wprowadzanie zmian w manifeście rozszerzenia VSIX

Aby upewnić się, że instalacja użytkownika programu Visual Studio ma wszystkie zestawy wymagane do uruchomienia rozszerzenia, należy określić wszystkie składniki wymagań wstępnych lub pakiety w pliku manifestu rozszerzenia. Gdy użytkownik próbuje zainstalować rozszerzenie, VSIXInstaller sprawdzi, czy wszystkie wymagania wstępne są zainstalowane. Jeśli niektórych brakuje, użytkownik zostanie poproszony o zainstalowanie brakujących składników w ramach procesu instalacji rozszerzenia.

> [!Note]
> Co najmniej wszystkie rozszerzenia należy określić składnik edytora podstawowego programu Visual Studio jako warunek wstępny.

* Edytuj plik manifestu rozszerzenia (zwykle nazywany *source.extension.vsixmanifest).*
* Upewnij `InstallationTarget` się, że zawiera 15.0.
* Dodaj wymagane wymagania wstępne instalacji (jak pokazano w poniższym przykładzie).
  * Zaleca się określenie tylko identyfikatorów składników dla wymagań wstępnych instalacji.
  * Instrukcje [dotyczące identyfikacji identyfikatorów komponentów](#find-component-ids)można znaleźć w sekcji na końcu tego dokumentu.

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

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Opcja: Użyj projektanta, aby wprowadzić zmiany w manifeście rozszerzenia VSIX

Zamiast bezpośrednio edytować manifest XML, można użyć nowej karty **Wymagania wstępne** w Projektant manifestu, aby wybrać wymagania wstępne i XML zostaną zaktualizowane dla Ciebie.

> [!Note]
> Projektant manifestów umożliwia tylko wybranie składników (nie obciążeń lub pakietów), które są zainstalowane w bieżącym wystąpieniu programu Visual Studio. Jeśli musisz dodać warunek wstępny dla obciążenia, pakietu lub składnika, który nie jest aktualnie zainstalowany, edytuj bezpośrednio w manifeście XML.

* Plik open *source.extension.vsixmanifest [Design].*
* Wybierz kartę **Wymagania wstępne** i naciśnij przycisk **Nowy.**

   ![Projektant manifestu VSIX](media/vsix-manifest-designer.png)

* Zostanie otwarte okno **Dodaj nowe wymaganie.**

   ![dodaj warunek wstępny vsix](media/add-vsix-prerequisite.png)

* Kliknij na rozwijanie **name** i wybierz żądany warunek wstępny.
* W razie potrzeby zaktualizuj wersję.

   > [!Note]
   > Pole wersji zostanie wstępnie wypełnione wersją aktualnie zainstalowanego składnika, z zakresem obejmującym do (ale nie wliczając) następnej wersji głównej składnika.

   ![dodaj warunek wstępny roslyn](media/add-roslyn-prerequisite.png)

* Naciśnij przycisk **OK**.

## <a name="update-debug-settings-for-the-project"></a>Aktualizowanie ustawień debugowania dla projektu

Jeśli chcesz debugować rozszerzenie w eksperymentalnym wystąpieniu programu Visual Studio, upewnij się, że ustawienia projektu dla > **akcji** **Rozpocznij debugowania**mają wartość **Start zewnętrzna:** ustawiona na plik *devenv.exe* instalacji programu Visual Studio 2017.

Może wyglądać następująco: *C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe*

![uruchamianie programu zewnętrznego](media/start-external-program.png)

> [!Note]
> Akcja uruchamiania debugowania jest zazwyczaj przechowywana w pliku *csproj.user.* Ten plik jest zwykle zawarty w pliku *.gitignore* i dlatego nie jest zwykle zapisywany z innymi plikami projektu, gdy jest zaangażowany w kontrolę źródła. W związku z tym, jeśli pobrano rozwiązanie świeże z kontroli źródła jest prawdopodobne, że projekt nie będzie miał żadnych wartości ustawionych dla akcji startowej. Nowe projekty VSIX utworzone za pomocą programu Visual Studio 2017 będą miały plik *csproj.user* utworzony z domyślnymi punktami wskazującymi bieżący katalog instalacji programu Visual Studio. Jednak w przypadku migracji rozszerzenia VSIX v2, jest prawdopodobne, że plik *csproj.user* będzie zawierać odwołania do katalogu instalacji poprzedniej wersji programu Visual Studio. Ustawienie wartości dla **debugowania** > **akcji Start** pozwoli poprawne wystąpienie eksperymentalne programu Visual Studio do uruchomienia podczas próby debugowania rozszerzenia.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Sprawdź, czy rozszerzenie tworzy poprawnie (jako VSIX v3)

* Tworzenie projektu VSIX.
* Rozpakuj wygenerowany VSIX.
  * Domyślnie plik VSIX znajduje się wewnątrz *bin/debugowania* lub *bin/release* jako *[YourCustomExtension].vsix*.
  * Zmień nazwę *pliku .vsix* na *.zip,* aby łatwo wyświetlić zawartość.
* Sprawdź istnienie trzech plików:
  * *Extension.vsixmanifest*
  * *manifest.json*
  * *katalog.json*

## <a name="check-when-all-required-prerequisites-are-installed"></a>Sprawdź, kiedy są zainstalowane wszystkie wymagane wymagania wstępne

Przetestuj, czy vsix instaluje się pomyślnie na komputerze ze wszystkimi wymaganymi wymaganiami wstępnymi zainstalowanymi.

> [!Note]
> Przed zainstalowaniem dowolnego rozszerzenia należy zamknąć wszystkie wystąpienia programu Visual Studio.

Spróbuj zainstalować rozszerzenie:

* W programie Visual Studio 2017

![Instalator VSIX w programie Visual Studio 2017](media/vsixinstaller-vs-2017.png)

* Opcjonalnie: Sprawdź poprzednie wersje programu Visual Studio.
  * Udowadnia zgodność wsteczną.
  * Powinien działać dla programu Visual Studio 2012, Visual Studio 2013, Visual Studio 2015.
* Opcjonalnie: Sprawdź, czy moduł sprawdzania wersji instalatora VSIX oferuje wybór wersji.
  * Zawiera poprzednie wersje programu Visual Studio (jeśli jest zainstalowany).
  * Zawiera program Visual Studio 2017.

Jeśli program Visual Studio został niedawno otwarty, może zostać wyświetlone okno dialogowe w ten sposób:

![a uruchomione procesy](media/vs-running-processes.png)

Poczekaj na zamknięcie procesów lub ręcznie zakończ zadania. Procesy można znaleźć według wymienionej nazwy lub z identyfikatorem PID wymienionym w nawiasie.

> [!Note]
> Te procesy nie zostaną automatycznie zamknięte, gdy jest uruchomione wystąpienie programu Visual Studio. Upewnij się, że zostały zamknięte wszystkie wystąpienia programu Visual Studio na komputerze — w tym od innych użytkowników, a następnie kontynuować ponawianie próby.

## <a name="check-when-missing-the-required-prerequisites"></a>Sprawdź, czy brakuje wymaganych wymagań wstępnych

* Spróbuj zainstalować rozszerzenie na komputerze z programem Visual Studio 2017, który nie zawiera wszystkich składników zdefiniowanych w wymagania wstępne (powyżej).
* Sprawdź, czy instalacja identyfikuje brakujący składnik/s i wyświetla je jako warunek wstępny w programie VSIXInstaller.
* Uwaga: Podniesienie uprawnień będzie wymagane, jeśli konieczne jest zainstalowanie jakichkolwiek wymagań wstępnych z rozszerzeniem.

![vsixinstaller brak wstępnego](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>Zdecyduj się na komponenty

Podczas wyszukywanie zależności, można znaleźć, że jedna zależność może mapować do wielu składników. Aby określić, które zależności należy określić jako warunek wstępny, zalecamy wybranie składnika, który ma funkcję podobną do rozszerzenia, a także rozważenie użytkowników i jakiego typu składników najprawdopodobniej zostały zainstalowane lub nie miałyby nic przeciwko instalacji. Sugerujemy również tworzenie rozszerzeń w sposób, w którym wymagane wymagania wstępne spełniają tylko minimum, które pozwolą na uruchomienie rozszerzenia i dodatkowe funkcje mają je uśpione, jeśli niektóre składniki nie zostaną wykryte.

Aby zapewnić dalsze wskazówki, zidentyfikowaliśmy kilka typowych typów rozszerzeń i sugerowane warunki wstępne:

Typ rozszerzenia | Nazwa wyświetlana | ID
--- | --- | ---
Edytor | Edytor podstawowy programu Visual Studio | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# i Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Rdzeń zarządzanego obciążenia pulpitu | Microsoft.VisualStudio.Component.ManagedDesktop.Core
Debuger | Debuger just-in-time | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="find-component-ids"></a>Znajdowanie identyfikatorów składników

Lista składników posortowanych według produktu programu Visual Studio znajduje się w [programie Visual Studio 2017 obciążenia i identyfikatorów składników.](/visualstudio/install/workload-and-component-ids?view=vs-2019) Użyj tych identyfikatorów składników dla identyfikatorów wstępnych w manifeście.

Jeśli nie masz pewności, który składnik zawiera określony składnik, pobierz [arkusz kalkulacyjny Mapowanie -> Binarne.](https://aka.ms/vs2017componentid-binaries)

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017-ComponentBinaryMapping.xlsx

W arkuszu programu Excel znajdują się cztery kolumny: **Nazwa składnika,** **Identyfikator składnika,** **Wersja**i **Nazwy binarne / Pliki**.  Za pomocą filtrów można wyszukiwać i znajdować określone składniki i pliki binarne.

W przypadku wszystkich odwołań należy najpierw określić, które z nich znajdują się w elementów w edytorze podstawowym (Microsoft.VisualStudio.Component.CoreEditor).  Co najmniej wymagamy, aby podstawowy składnik edytora został określony jako warunek wstępny dla wszystkich rozszerzeń. Spośród pozostałych odwołań, które nie znajdują się w edytorze podstawowym, dodaj filtry w sekcji **Pliki binarne / Nazwy plików,** aby znaleźć składniki, które mają którykolwiek z podzbiorów tych odwołań.

Przykłady:

* Jeśli masz rozszerzenie debugera i wiesz, że projekt ma odwołanie do *vsDebugEng.dll* i *VSDebug.dll*, kliknij przycisk filtru w nagłówku **Pliki binarne / Nazwy plików.**  Wyszukaj "VSDebugEng.dll" i wybierz *przycisk OK*.  Następnie kliknij przycisk filtru w nagłówku **Nazwy plików / Pliki** ponownie i wyszukaj "VSDebug.dll".  Zaznacz pole wyboru **Dodaj bieżące zaznaczenie, aby filtrować** i wybierz **przycisk OK**.  Teraz przejrzyj **nazwę składnika,** aby znaleźć składnik, który jest najbardziej związany z typem rozszerzenia. W tym przykładzie należy wybrać debuger just-in-time i dodać go do vsixmanifest.
* Jeśli wiesz, że projekt zajmuje się elementami debugera, możesz wyszukać w polu wyszukiwania filtru wyszukiwanie, aby zobaczyć, jakie składniki zawierają debuger w jego nazwie.

## <a name="specify-a-visual-studio-2017-release"></a>Określanie wersji programu Visual Studio 2017

Jeśli rozszerzenie wymaga określonej wersji programu Visual Studio 2017, na przykład zależy to od funkcji wydanej w wersji 15.3, należy określić numer kompilacji w programie VSIX **InstallationTarget**. Na przykład wersja 15.3 ma numer kompilacji "15.0.26730.3". Możesz zobaczyć mapowanie wersji do tworzenia numerów [tutaj](../install/visual-studio-build-numbers-and-release-dates.md). Użycie numeru wydania "15.3" nie będzie działać poprawnie.

Jeśli rozszerzenie wymaga wersji 15.3 lub **nowszej, należy zadeklarować wersję InstallationTarget** jako [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```
