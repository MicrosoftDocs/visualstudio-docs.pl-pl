---
title: Okna dialogowe Projekty i rozwiązania, Opcje
ms.date: 07/26/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.General
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1ed60e07c625665f92838cfbc671b03c605fda0d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567648"
---
# <a name="options-dialog-box-projects-and-solutions--general"></a>Okno dialogowe Opcje: \> Ogólne projekty i rozwiązania

Ta strona służy do definiowania zachowania programu Visual Studio związane z projektami i rozwiązaniami. Aby uzyskać dostęp do tych opcji, wybierz pozycję**Opcje** **narzędzi** > , rozwiń pozycję **Projekty i rozwiązania**, a następnie wybierz pozycję **Ogólne**.

Następujące opcje są dostępne na stronie **Ogólne.**

## <a name="always-show-error-list-if-build-finishes-with-errors"></a>Zawsze pokazuj listę błędów, jeśli kompilacja kończy się błędami

Otwiera okno **lista błędów** po zakończeniu kompilacji, tylko wtedy, gdy projekt nie udało się skompilować. Błędy występujące podczas procesu kompilacji są wyświetlane. Gdy ta opcja jest wyczyszczona, błędy nadal występują, ale okno nie otwiera się po zakończeniu kompilacji. Ta opcja jest domyślnie włączona.

## <a name="track-active-item-in-solution-explorer"></a>Śledzenie aktywnego elementu w Eksploratorze rozwiązań

Po wybraniu tej opcji **Eksplorator rozwiązań** zostanie automatycznie otwarty i zostanie wybrany aktywny element. Wybrany element zmienia się podczas pracy z różnymi plikami w projekcie lub rozwiązaniu lub różnymi składnikami w projektancie. Gdy ta opcja jest wyczyszczona, zaznaczenie w **Eksploratorze rozwiązań** nie zmienia się automatycznie. Ta opcja jest domyślnie włączona.

## <a name="show-advanced-build-configurations"></a>Pokaż zaawansowane konfiguracje kompilacji

Po zaznaczeniu tej opcji opcje konfiguracji kompilacji są wyświetlane w oknie dialogowym **Strony właściwości projektu** i w oknie dialogowym Strony właściwości **rozwiązania.** Po wyczyszczeniu opcje konfiguracji kompilacji nie są wyświetlane w oknie dialogowym **Strony właściwości projektu** i w oknie dialogowym Strony właściwości **rozwiązania** dla projektów języka Visual Basic i C#, które zawierają jedną konfigurację lub dwie konfiguracje debugowania i zwalniania. Jeśli projekt ma konfigurację zdefiniowaną przez użytkownika, wyświetlane są opcje konfiguracji kompilacji.

Po niezaznaczeniu polecenia w menu **Kompilacja,** takie jak **Build Solution**, Rebuild **Solution**i Clean **Solution**, są wykonywane w konfiguracji release i polecenia w menu **debugowania,** takie jak **Uruchamianie debugowania** i **Uruchamianie bez debugowania,** są wykonywane w konfiguracji debugowania.

## <a name="always-show-solution"></a>Zawsze pokazuj rozwiązanie

Po wybraniu tej opcji rozwiązanie i wszystkie polecenia, które działają na rozwiązania są zawsze wyświetlane w IDE. Po wyczyszczeniu wszystkie projekty są tworzone jako projekty autonomiczne i nie widzisz rozwiązania w Eksploratorze rozwiązań lub poleceniach, które działają na rozwiązania w IDE, jeśli rozwiązanie zawiera tylko jeden projekt.

::: moniker range="vs-2017"

## <a name="save-new-projects-when-created"></a>Zapisywanie nowych projektów podczas tworzenia

Po wybraniu tej opcji można określić lokalizację projektu w oknie dialogowym **Nowy projekt.** Po wyczyszczeniu wszystkie nowe projekty są tworzone jako projekty tymczasowe. Podczas pracy z projektami tymczasowymi można tworzyć i eksperymentować z projektem bez konieczności określania lokalizacji dysku.

::: moniker-end

## <a name="warn-user-when-the-project-location-is-not-trusted"></a>Ostrzegaj użytkownika, gdy lokalizacja projektu nie jest zaufana

Jeśli spróbujesz utworzyć nowy projekt lub otworzyć istniejący projekt w lokalizacji, która nie jest w pełni zaufana (na przykład na ścieżce UNC lub ścieżce HTTP), zostanie wyświetlony komunikat. Ta opcja służy do określania, czy wiadomość jest wyświetlana przy każdej próbie utworzenia lub otwarcia projektu w lokalizacji, która nie jest w pełni zaufana.

## <a name="show-output-window-when-build-starts"></a>Pokaż okno Dane wyjściowe podczas uruchamiania kompilacji

Automatycznie wyświetla [okno Dane wyjściowe](../../ide/reference/output-window.md) w IDE na początku kompilacji rozwiązania.

## <a name="prompt-for-symbolic-renaming-when-renaming-files"></a>Monitowanie o symboliczną zmianę nazwy podczas zmiany nazwy plików

Po wybraniu tej opcji program Visual Studio wyświetla okno komunikatu z pytaniem, czy należy również zmienić nazwę wszystkich odwołań w projekcie do elementu kodu.

## <a name="prompt-before-moving-files-to-a-new-location"></a>Monitowanie przed przeniesieniem plików do nowej lokalizacji

Po wybraniu tej opcji program Visual Studio wyświetla okno komunikatu potwierdzającego, zanim lokalizacje plików zostaną zmienione przez akcje w **Eksploratorze rozwiązań**.

## <a name="reopen-documents-on-solution-load"></a>Ponowne otwieranie dokumentów przy obciążeniu rozwiązania

Po wybraniu tej opcji dokumenty, które pozostały otwarte podczas poprzedniego zamknięcia rozwiązania, są automatycznie otwierane po otwarciu rozwiązania.

Ponowne otwarcie niektórych typów plików lub projektantów może opóźnić załadowanie rozwiązania. Odznacz tę opcję, aby [zwiększyć wydajność ładowania rozwiązania,](../../ide/visual-studio-performance-tips-and-tricks.md#disable-automatic-file-restore) jeśli nie chcesz przywracać poprzedniego kontekstu rozwiązania.

::: moniker range=">=vs-2019"

## <a name="restore-solution-explorer-project-hierarchy-state-on-solution-load"></a>Przywróć stan hierarchii projektu Eksploratora rozwiązań przy obciążeniu rozwiązania

Po wybraniu tej opcji przywraca stan węzłów w Eksploratorze rozwiązań w odniesieniu do tego, czy zostały one rozwinięte, czy zwinięte podczas ostatniego otwarcia rozwiązania. Usuń zaznaczenie tej opcji, aby skrócić czas ładowania rozwiązania dla dużych rozwiązań.

> [!TIP]
> Jeśli ta opcja zostanie wyłączona, łatwym sposobem przejścia do aktywnego dokumentu w Eksploratorze rozwiązań jest **wybranie opcji Synchronizuj z aktywnym dokumentem** na pasku narzędzi **Eksploratora rozwiązań.**
>
> ![Synchronizacja z aktywnym dokumentem w Eksploratorze rozwiązań](media/sync-active-document.png)

## <a name="open-sdk-style-project-files-with-double-click-or-the-enter-key"></a>Otwieranie plików projektu w stylu SDK za pomocą dwukrotnego kliknięcia lub klawisza Enter

Po wybraniu tej opcji i dwukrotnym kliknięciu węzła projektu w stylu SDK w Eksploratorze \*rozwiązań lub wybraniu go, a następnie **naciśnięciu klawisza Enter**, plik projektu (na przykład plik csproj) zostanie otwarty jako kod XML w edytorze. Po usunięciu zaznaczenia dwukrotne kliknięcie węzła projektu w stylu SDK w Eksploratorze rozwiązań lub wybranie go i **naciśnięcie klawisza Enter** powoduje tylko rozwinięcie lub zwijanie węzła.

Jeśli nie masz zaznaczonej tej opcji i chcesz edytować plik projektu w stylu SDK, kliknij prawym przyciskiem myszy węzeł projektu w Eksploratorze rozwiązań i wybierz pozycję **Edytuj plik projektu**. W przypadku innych typów projektów należy najpierw zwolnić projekt przed edycją go w programie Visual Studio.

> [!TIP]
> *Projekt w stylu SDK*lub [SDK projektu](../../msbuild/how-to-use-project-sdk.md)ma nowszy, bardziej usprawniony format pliku projektu, który został wprowadzony za pomocą programu MSBuild 15.0. Projekt w stylu SDK `Sdk` zawiera atrybut `Project` elementu, `<Project Sdk="Microsoft.NET.Sdk">`na przykład . Visual Studio tworzy projekt w stylu SDK podczas tworzenia nowego projektu .NET Core z jednego z szablonów programu Visual Studio, na przykład.

::: moniker-end

## <a name="see-also"></a>Zobacz też

- [Okno dialogowe Opcje: \> Lokalizacje projektów i rozwiązań](projects-solutions-locations-options.md)
- [Okno dialogowe Opcje, Projekty i rozwiązania, Tworzenie i uruchamianie](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Okno dialogowe Opcje, Projekty i rozwiązania, Projekty internetowe](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)
