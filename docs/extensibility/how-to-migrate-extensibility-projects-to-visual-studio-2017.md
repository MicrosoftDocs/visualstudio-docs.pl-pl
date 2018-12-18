---
title: 'Instrukcje: Migrowanie projektów rozszerzalności do programu Visual Studio 2017 | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/09/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 195d63e5ddb8b8536c1d0c1c4197270f5b3aa508
ms.sourcegitcommit: 331dbb12e11fcd7f5d15fab05f3c861e48126e43
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51826820"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Instrukcje: Migrowanie projektów rozszerzalności do programu Visual Studio 2017

W tym dokumencie opisano sposób uaktualniania projekty rozszerzalności programu Visual Studio 2017. Oprócz opisujących sposób zaktualizowania plików projektu, jego opisano również sposób uaktualnienia rozszerzenia manifestu v2, wersja 2 (VSIX) do nowej wersji 3 format manifestu VSIX (rozszerzeniu VSIX v3).

## <a name="install-visual-studio-2017-with-required-workloads"></a>Instalowanie programu Visual Studio 2017 przy użyciu wymagane obciążenia

Upewnij się, że ta instalacja obejmuje następujące obciążenia:

* Programowanie aplikacji klasycznych dla platformy .NET
* Programowanie rozszerzeń programu Visual Studio

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Otwórz rozwiązanie VSIX w programie Visual Studio 2017

Wszystkie projekty VSIX będzie wymagają jednokierunkowego uaktualnienia wersji głównej programu Visual Studio 2017.

Plik projektu (na przykład **.csproj*) zostaną zaktualizowane:

* MinimumVisualStudioVersion — są teraz ustawione na 15.0
* OldToolsVersion (jeśli istnieje wcześniej)-równa 14.0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Aktualizacja pakietu Microsoft.VSSDK.BuildTools NuGet

>**Uwaga:** Jeśli rozwiązanie nie odwołuje się do pakietu Microsoft.VSSDK.BuildTools NuGet, możesz pominąć ten krok.

Aby można było tworzyć rozszerzenia w nowych rozszerzeniu VSIX v3 (wersja 3), rozwiązania będzie muszą ma zostać utworzony za pomocą nowe narzędzia VSSDK kompilacji. To nie będą instalowane z Visual Studio 2017, ale v2 rozszerzenia VSIX może zawierający odwołanie do starszej wersji za pomocą narzędzia NuGet. Jeśli tak, należy ręcznie zainstalować aktualizację pakietu Microsoft.VSSDK.BuildTools NuGet dla Twojego rozwiązania.

Aby zaktualizować odwołania NuGet Microsoft.VSSDK.BuildTools:

* Kliknij prawym przyciskiem myszy rozwiązanie i wybierz polecenie **Zarządzaj pakietami NuGet dla rozwiązania**.
* Przejdź do **aktualizacje** kartę.
* Wybierz **Microsoft.VSSDK.BuildTools (Najnowsza wersja)**.
* Naciśnij klawisz **aktualizacji**.

![Narzędzia VSSDK do kompilacji](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>Wprowadzanie zmian w manifeście rozszerzenia VSIX

Aby upewnić się, że użytkownika instalacji programu Visual Studio ma wszystkie zestawy, które są wymagane do uruchomienia rozszerzenie, należy określić wszystkie wstępnie wymagane składniki lub pakietów w pliku manifestu rozszerzenia. Gdy użytkownik próbuje zainstalować rozszerzenie, Instalator VSIX sprawdzi, czy wszystkie wstępnie wymagane składniki są zainstalowane. Jeśli niektóre są spełnione, użytkownik zostanie wyświetlony monit zainstalowanie brakujących składników jako część procesu instalacji rozszerzenia.

>**Uwaga:** co najmniej wszystkie rozszerzenia należy określić składnika edytora podstawowych funkcji programu Visual Studio jako warunek wstępny.

* Edytuj plik manifestu rozszerzenia (zwykle nazywane *source.extension.vsixmanifest*).
* Upewnij się, `InstallationTarget` obejmuje 15.0.
* Dodaj wymagania wstępne instalacji wymagane (jak pokazano w poniższym przykładzie).
  * Zalecane jest określenie tylko identyfikatory składnika wymagań wstępnych dotyczących instalacji.
  * Zobacz sekcję na końcu tego dokumentu, aby [instrukcje dotyczące identyfikowania identyfikatorów składników](#find-component-ids).

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

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Opcja: Użycie projektanta do wprowadzania zmian w manifeście rozszerzenia VSIX

Zamiast bezpośrednio edytować plik manifestu XML, można użyć nowej **wymagania wstępne** karcie Manifest Designer, aby wybrać wymagań wstępnych i XML zostanie zaktualizowany dla Ciebie.

>**Uwaga:** Manifest Designer tylko pozwoli wybrać składniki (obciążeń i pakietów), które są instalowane w bieżącym wystąpieniu programu Visual Studio. Jeśli potrzebujesz dodać wymaganiem wstępnym dla obciążenia, pakietem lub składnika, który nie jest obecnie zainstalowany bezpośrednio edytować kod XML manifestu.

* Otwórz *source.extension.vsixmanifest [projekt]* pliku.
* Wybierz **wymagania wstępne** kartę, a następnie naciśnij klawisz **New** przycisku.

  ![Manifestu VSIX](media/vsix-manifest-designer.png)

* **Dodawanie nowych wymagań wstępnych** zostanie otwarte okno.

  ![Dodaj wstępnie wymaganego składnika vsix](media/add-vsix-prerequisite.png)

* Kliknij listę rozwijaną **nazwa** i wybierz żądany wymagań wstępnych.
* Aktualizacja wersji, jeśli jest to wymagane.

  >Uwaga: Pola wersji zostaną wstępnie wypełnione wersję aktualnie zainstalowany składnik z zakresu obejmujące do (z wyjątkiem) następnej wersji głównej składnika.

  ![Dodaj warunek wstępny roslyn](media/add-roslyn-prerequisite.png)

* Naciśnij klawisz **OK**.

## <a name="update-debug-settings-for-the-project"></a>Aktualizowanie ustawień debugowania dla projektu

Jeśli chcesz debugować rozszerzenia w eksperymentalnym wystąpieniu programu Visual Studio, upewnij się, że ustawienia projektu dla **debugowania** > **Akcja uruchamiania** ma **Start zewnętrznych Program:** wartość *devenv.exe* plików instalacji programu Visual Studio 2017.

Jak może wyglądać: *\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe C:\Program Files (x86)*

![Uruchom zewnętrzny program](media/start-external-program.png)

>**Uwaga:** Akcja uruchamiania debugowania są zwykle przechowywane w *. csproj.user* pliku. Ten plik zwykle znajduje się w *.gitignore* plików i, w związku z tym, nie są zwykle zapisywane z innych plików projektów, gdy zatwierdzone do kontroli źródła. Jako takie jeśli zostały pobrane rozwiązania świeże z kontroli źródła prawdopodobnie projekt będzie miał żadne wartości, ustaw w przypadku ustawienia Akcja początkowa. Nowe projekty VSIX utworzonych za pomocą programu Visual Studio 2017 będzie miał *. csproj.user* plik utworzony przy użyciu ustawień domyślnych, wskazując w bieżącym katalogu instalacji programu Visual Studio. Jednak jeśli migrujesz rozszerzenie VSIX v2 jest prawdopodobne, że *. csproj.user* plik będzie zawierał odwołania do katalogu instalacyjnego poprzedniej wersji programu Visual Studio. Ustawienie wartości dla **debugowania** > **Akcja uruchamiania** umożliwi prawidłowe wystąpienie eksperymentalne programu Visual Studio, można uruchomić podczas próby debugowania rozszerzenia.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Sprawdź, czy rozszerzenie tworzy poprawnie (jako rozszerzeniu VSIX v3)

* Skompiluj projekt VSIX.
* Rozpakuj wygenerowanego pliku VSIX.
  * Domyślnie plik VSIX znajduje się wewnątrz *bin/Debug* lub *bin/Release* jako *.vsix [YourCustomExtension]*.
  * Zmień nazwę *.vsix* do *zip* łatwe wyświetlanie zawartości.
* Sprawdź, czy istnienie trzy pliki:
  * *Extension.vsixmanifest*
  * *Manifest.JSON*
  * *Catalog.JSON*

## <a name="check-when-all-required-prerequisites-are-installed"></a>Sprawdź, gdy wszystkie wymagane wstępnie wymagane składniki są zainstalowane

Sprawdź, czy VSIX pomyślnie instaluje na komputerze przy użyciu wszystkich wymaganych wstępnie wymagane składniki, które są zainstalowane.

>**Uwaga:** przed zainstalowaniem dowolnego rozszerzenia, zamknij wszystkie wystąpienia programu Visual Studio.

Próba zainstalowania rozszerzenia:

* W programie Visual Studio 2017

![Instalator VSIX w programie Visual Studio 2017](media/vsixinstaller-vs-2017.png)

* Opcjonalnie: Sprawdzenie w poprzednich wersjach programu Visual Studio.
  * Okazuje się zgodności z poprzednimi wersjami.
  * Powinna działać w przypadku programu Visual Studio 2012, Visual Studio 2013, Visual Studio 2015.
* Opcjonalnie: Sprawdź, czy sprawdzanie wersji Instalator VSIX zapewnia szeroki wybór wersji.
  * Zawiera poprzednie wersje programu Visual Studio (jeśli jest zainstalowana).
  * Zawiera program Visual Studio 2017.

Ostatnio otwarto programu Visual Studio, może zostać wyświetlony okno dialogowe następująco:

![uruchamianie procesów w programie VS](media/vs-running-processes.png)

Poczekaj na zamknięcie procesów lub ręcznie zakończenia zadania. Można znaleźć procesy, przez nazwę listy lub o identyfikatorze PID wymienione w nawiasach.

>**Uwaga:** te procesy nie automatycznie wyłączy po uruchomieniu wystąpienia programu Visual Studio. Upewnij się, zostało Zamknij wszystkie wystąpienia programu Visual Studio na komputerze — łącznie z tymi od innych użytkowników, następnie kontynuuj spróbować ponownie.

## <a name="check-when-missing-the-required-prerequisites"></a>Sprawdź, gdy brak wymagań wstępnych

* Próby instalacji rozszerzenia na maszynie z programem Visual Studio 2017 ten nie zawiera wszystkie składniki, które są zdefiniowane w sekcji wymagania wstępne (powyżej).
* Sprawdź, czy instalacja określa Brak składników/s i wyświetla je jako warunek wstępny Instalator VSIX.
* Uwaga: Podniesienia uprawnień będzie być wymagane, jeśli wszystkie wstępnie wymagane składniki, które muszą zostać zainstalowane z rozszerzeniem.

![Brak wstępnie wymaganego składnika Instalator VSIX](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>Podjąć decyzję na temat składników

Podczas wyszukiwania zależności, można zauważyć, że jedną zależność może mapować do wielu składników. Aby określić zależności, które należy określić jako swojej wymagań wstępnych, zalecamy wybranie składnik, który ma funkcjonalność podobną do rozszerzenia i również wziąć pod uwagę użytkowników i jakiego rodzaju składników będzie najczęściej zainstalowanie lub w takich sytuacjach przydałaby należy uwzględnić następujące kwestie instalacji. Zalecamy również tworzenie rozszerzeń w taki sposób, w którym wymagania wstępne spełniają tylko minimalne, która umożliwi Twojego rozszerzenia uruchomić i dodatkowych funkcji, poproś być nieaktywne, jeśli niektórych składników nie są wykrywane.

Aby zapewnić dalsze wskazówki, zidentyfikowaliśmy kilka popularnych typów rozszerzeń i ich sugerowane wymagania wstępne:

Typ rozszerzenia | Nazwa wyświetlana | Id
--- | --- | ---
Edytor | Edytor rdzeni programu Visual Studio  | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# i Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Podstawowe składniki dla obciążenia zarządzanego pulpitu | Microsoft.VisualStudio.Component.ManagedDesktop.Core
Debuger | Debuger Just In Time | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="find-component-ids"></a>Znajdź identyfikatory składnika

Posortowane według produktu Visual Studio składniki na liście wynosi [identyfikatory obciążeń i składników programu Visual Studio 2017](https://aka.ms/vs2017componentIDs). Te identyfikatory składników na użytek swoim identyfikatorem wymagań wstępnych w manifeście.

Jeśli wiesz, który składnik zawiera określonego pliku binarnego, Pobierz [składnika -> arkusza kalkulacyjnego mapowania binarne](https://aka.ms/vs2017componentid-binaries).

### <a name="vs2017-componentbinarymappingxlsx"></a>Program vs2017 ComponentBinaryMapping.xlsx

Istnieją cztery kolumny w arkuszu programu Excel: **nazwa składnika**, **ComponentId**, **wersji**, i **binarnego / nazwy plików**.  Filtry można użyć do wyszukiwania i znajdowania określonych składników i plikach binarnych.

Dla wszystkich odwołań należy najpierw określić, które nie są w składniku core editor (Microsoft.VisualStudio.Component.CoreEditor).  Co najmniej wymagamy składnika edytora podstawowych, należy określić jako warunek wstępny dla wszystkich rozszerzeń. Odwołań, które są pozostawiane, które nie znajdują się w edytorze podstawowych funkcji, należy dodać filtry w **pliki binarne / nazwy plików** sekcję, aby znaleźć składników, które zawierają dowolne spośród podzbiór tych odwołań.

Przykłady:

* Jeśli masz rozszerzenia debugera i dowiedzieć się, że projekt zawiera odwołanie do *VSDebugEng.dll* i *VSDebug.dll*, kliknij przycisk filtru w **pliki binarne / nazwy plików**nagłówka.  Wyszukaj frazę "VSDebugEng.dll" i wybierz *OK*.  Następnie kliknij przycisk filtru w **pliki binarne / nazwy plików** ponownie nagłówek i poszukaj pozycji "VSDebug.dll".  Zaznacz pole wyboru **Dodaj bieżące zaznaczenie do filtru** i wybierz **OK**.  Teraz wyglądać za pośrednictwem **nazwa składnika** można znaleźć składnika, który jest powiązany typ rozszerzenia. W tym przykładzie wybrano będzie Just-In-Time debugera i dodać go do Twojego vsixmanifest.
* Jeśli wiesz, że projektu zajmuje się elementy debugera, można wyszukać "debugera" w polu wyszukiwania filtr aby zobaczyć, jakie składniki zawierają debugera w jego nazwę.

## <a name="specify-a-visual-studio-2017-release"></a>Określanie wersji programu Visual Studio 2017

Jeśli rozszerzenie wymaga określonej wersji programu Visual Studio 2017, na przykład, zależy od funkcją udostępnioną w 15.3, należy określić numer kompilacji w VSIX użytkownika **InstallationTarget**. Na przykład wersja 15.3 ma numer kompilacji "15.0.26730.3". Możesz zobaczyć mapowanie wersji numery kompilacji [tutaj](../install/visual-studio-build-numbers-and-release-dates.md). Za pomocą numeru wersji "15.3" nie będą działać poprawnie.

Jeśli Twojego rozszerzenia wymaga 15.3 lub nowszej, może zadeklarować **wersji InstallationTarget** jako [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```
