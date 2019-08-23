---
title: Projekty i rozwiązania, Opcje — okno dialogowe
ms.date: 07/26/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.General
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 31d829a668a2c9690333315c30904623187fe51d
ms.sourcegitcommit: f42b5318c5c93e2b5ecff44f408fab8bcdfb193d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69976735"
---
# <a name="options-dialog-box-projects-and-solutions--general"></a>Opcje — okno dialogowe: Ogólne projekty i \> rozwiązania

Ta strona służy do definiowania zachowań programu Visual Studio związanych z projektami i rozwiązaniami. Aby uzyskać dostęp do tych opcji, wybierz pozycję **Narzędzia** > **Opcje**, rozwiń węzeł **projekty i rozwiązania**, a następnie wybierz pozycję **Ogólne**.

Poniższe opcje są dostępne na stronie **Ogólne** .

## <a name="always-show-error-list-if-build-finishes-with-errors"></a>Zawsze pokazuj Lista błędów, jeśli kompilacja zakończy się z błędami

Otwiera okno **Lista błędów** po zakończeniu kompilacji, tylko wtedy, gdy kompilacja projektu nie powiodła się. Zostaną wyświetlone błędy występujące podczas procesu kompilacji. Gdy ta opcja jest wyczyszczona, błędy nadal występują, ale okno nie jest otwierane po zakończeniu kompilacji. Ta opcja jest domyślnie włączona.

## <a name="track-active-item-in-solution-explorer"></a>Śledź aktywny element w Eksplorator rozwiązań

Po wybraniu **Eksplorator rozwiązań** automatycznie otwierane, a aktywny element jest zaznaczony. Wybrany element zmienia się podczas pracy z różnymi plikami w projekcie lub rozwiązaniu lub różnymi składnikami projektanta. Gdy ta opcja jest wyczyszczona, wybór w **Eksplorator rozwiązań** nie zmienia się automatycznie. Ta opcja jest domyślnie włączona.

## <a name="show-advanced-build-configurations"></a>Pokaż zaawansowane konfiguracje kompilacji

Po wybraniu opcji konfiguracji kompilacji są wyświetlane w oknie dialogowym **strony właściwości projektu** i w oknie dialogowym **strony właściwości rozwiązania** . Po wyczyszczeniu opcje konfiguracji kompilacji nie są wyświetlane w oknie dialogowym **strony właściwości projektu** i w oknie dialogowym **strony właściwości rozwiązania** dla Visual Basic i C# projektów, które zawierają jedną konfigurację lub dwie konfiguracje Debugowanie i wydanie. Jeśli projekt zawiera konfigurację zdefiniowaną przez użytkownika, są wyświetlane opcje konfiguracji kompilacji.

Po zaznaczeniu tej opcji polecenia w menu **kompilacja** , takie jak Kompilowanie **rozwiązania**, ponowne **Kompilowanie rozwiązania**i **czyste rozwiązanie**, są wykonywane w konfiguracji wydania i polecenia w menu **Debuguj** , takie jak **Start Debugowanie** i **Uruchamianie bez debugowania**jest wykonywane w konfiguracji debugowania.

## <a name="always-show-solution"></a>Zawsze pokazuj rozwiązanie

Po wybraniu rozwiązanie i wszystkie polecenia działające na rozwiązaniach są zawsze wyświetlane w środowisku IDE. Po wyczyszczeniu wszystkie projekty są tworzone jako projekty autonomiczne, a rozwiązanie nie jest widoczne w Eksplorator rozwiązań lub polecenia, które działają na rozwiązaniach w IDE, jeśli rozwiązanie zawiera tylko jeden projekt.

::: moniker range="vs-2017"

## <a name="save-new-projects-when-created"></a>Zapisuj nowe projekty po utworzeniu

Po wybraniu można określić lokalizację projektu w oknie dialogowym **Nowy projekt** . Po wyczyszczeniu wszystkie nowe projekty są tworzone jako projekty tymczasowe. Podczas pracy z projektami tymczasowymi można tworzyć i eksperymentować z projektem bez konieczności określania lokalizacji na dysku.

::: moniker-end

## <a name="warn-user-when-the-project-location-is-not-trusted"></a>Ostrzegaj użytkownika, gdy Lokalizacja projektu nie jest zaufana

Jeśli spróbujesz utworzyć nowy projekt lub otworzyć istniejący projekt w lokalizacji, która nie jest w pełni zaufana (na przykład w ścieżce UNC lub w ścieżce HTTP), zostanie wyświetlony komunikat. Użyj tej opcji, aby określić, czy komunikat jest wyświetlany za każdym razem, gdy próbujesz utworzyć lub otworzyć projekt w lokalizacji, która nie jest w pełni zaufana.

## <a name="show-output-window-when-build-starts"></a>Pokaż okno danych wyjściowych po rozpoczęciu kompilacji

Automatycznie wyświetla [okno dane wyjściowe](../../ide/reference/output-window.md) w środowisku IDE na początku kompilacji rozwiązania.

## <a name="prompt-for-symbolic-renaming-when-renaming-files"></a>Monituj o zmianę nazwy symbolicznej podczas zmiany nazwy plików

Po wybraniu program Visual Studio wyświetli okno komunikatu z pytaniem, czy należy również zmienić nazwy wszystkich odwołań w projekcie na element kodu.

## <a name="prompt-before-moving-files-to-a-new-location"></a>Monituj przed przeniesieniem plików do nowej lokalizacji

Po wybraniu tego pola program Visual Studio wyświetla komunikat potwierdzenia przed zmianą lokalizacji plików przez akcje w **Eksplorator rozwiązań**.

## <a name="reopen-documents-on-solution-load"></a>Otwieraj ponownie dokumenty po załadowaniu rozwiązania

Po wybraniu dokumenty, które zostały pozostawione, otwierają się przed zamknięciem rozwiązania, są automatycznie otwierane po otwarciu rozwiązania.

Ponowne otwieranie niektórych typów plików lub projektantów może opóźnić ładowanie rozwiązania. Usuń zaznaczenie tej opcji, aby [zwiększyć wydajność ładowania rozwiązań](../../ide/visual-studio-performance-tips-and-tricks.md#disable-automatic-file-restore) , jeśli nie chcesz przywrócić poprzedniego kontekstu rozwiązania.

::: moniker range=">=vs-2019"

## <a name="restore-solution-explorer-project-hierarchy-state-on-solution-load"></a>Przywróć stan hierarchii projektu Eksplorator rozwiązań podczas ładowania rozwiązania

Po wybraniu przywraca stan węzłów w Eksplorator rozwiązań w odniesieniu do tego, czy były rozwinięte czy zwinięte podczas ostatniego otwarcia rozwiązania. Usuń zaznaczenie tej opcji, aby skrócić czas ładowania rozwiązania dla dużych rozwiązań.

> [!TIP]
> Jeśli wyłączysz tę opcję, prostym sposobem przejścia do aktywnego dokumentu w Eksplorator rozwiązań jest wybranie opcji **Synchronizuj z aktywnym dokumentem** na pasku narzędzi **Eksplorator rozwiązań** .
>
> ![Synchronizuj z aktywnym dokumentem w Eksplorator rozwiązań](media/sync-active-document.png)

## <a name="open-sdk-style-project-files-with-double-click-or-the-enter-key"></a>Otwieranie plików projektu w stylu zestawu SDK przy użyciu dwukrotnego kliknięcia lub klawisza ENTER

Gdy ta opcja jest zaznaczona, kliknij dwukrotnie węzeł projektu w stylu zestawu SDK w Eksplorator rozwiązań lub wybierz go, a następnie naciśnij klawisz **Enter**, plik projektu (na przykład \*plik. csproj) zostanie otwarty jako XML w edytorze. Po zaznaczeniu tej opcji kliknij dwukrotnie węzeł projektu w stylu zestawu SDK w Eksplorator rozwiązań lub wybierz go, a naciśnięcie klawisza **Enter** ma wpływ na rozwijanie lub zwijanie węzła.

Jeśli ta opcja nie jest zaznaczona i chcesz edytować plik projektu w stylu zestawu SDK, kliknij prawym przyciskiem myszy węzeł projektu w Eksplorator rozwiązań a następnie wybierz polecenie **Edytuj plik projektu**. W przypadku innych typów projektów należy najpierw zwolnić projekt przed jego edycją w programie Visual Studio.

> [!TIP]
> *Projekt w stylu zestawu SDK*lub [zestaw SDK projektu](../../msbuild/how-to-use-project-sdk.md)ma nowszy, bardziej zoptymalizowany format pliku projektu, który został wprowadzony w programie MSBuild 15,0. Projekt `Sdk` wstyluzestawuSDK`<Project Sdk="Microsoft.NET.Sdk">`zawiera atrybut w elemencie,naprzykład.`Project` Program Visual Studio tworzy projekt w stylu zestawu SDK podczas tworzenia nowego projektu .NET Core z jednego z szablonów programu Visual Studio, na przykład.

::: moniker-end

## <a name="see-also"></a>Zobacz także

- [Opcje — okno dialogowe: Lokalizacje projektów i \> rozwiązań](projects-solutions-locations-options.md)
- [Okno dialogowe Opcje, projekty i rozwiązania, kompilacja i uruchomienie](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Okno dialogowe Opcje, Projekty i rozwiązania, Projekty internetowe](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)
