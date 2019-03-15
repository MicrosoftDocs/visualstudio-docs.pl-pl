---
title: Opcje projektów i rozwiązań — okno dialogowe
ms.date: 07/14/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.General
- VS.ToolsOptionsPages.Projects.Locations
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ad43a125074240cb6dfb3c8f2c40750b803ac322
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57867816"
---
# <a name="projects-and-solutions-page-options-dialog-box"></a>Strony Projekty i rozwiązania, okno dialogowe Opcje

Ustawia zachowanie programu Visual Studio, związane z projektami i rozwiązaniami. Aby uzyskać dostęp do tych opcji, wybierz pozycję **narzędzia** > **opcje**, rozwiń węzeł **projekty i rozwiązania**, a następnie wybierz pozycję **ogólne** .

Domyślne ścieżki folderów projektu i szablonu są ustawiane za pomocą **lokalizacje** karty, w tym samym oknie dialogowym.

## <a name="general-page"></a>Strona Ogólne

Poniższe opcje są dostępne na **ogólne** strony.

### <a name="always-show-error-list-if-build-finishes-with-errors"></a>Zawsze pokazuj lista błędów Jeżeli kompilacja zakończy się z błędami

Otwiera **lista błędów** okna po zakończeniu kompilacji, tylko wtedy, gdy nie można skompilować projektu. Błędy występujące podczas procesu kompilacji są wyświetlane. Gdy ta opcja jest wyczyszczone, nadal występują błędy, ale nie można otworzyć okna po zakończeniu kompilacji. Ta opcja jest domyślnie włączona.

### <a name="track-active-item-in-solution-explorer"></a>Śledź aktywny element w Eksploratorze rozwiązań

Po wybraniu **Eksploratora rozwiązań** automatycznie zostanie otwarty i aktywny element jest wybrany. Zmiany wybranego elementu, jak pracować z różnych plików w projekcie lub rozwiązaniu lub różne składniki w projektancie. Jeśli ta opcja jest wyczyszczone, zaznaczenie w **Eksploratora rozwiązań** nie zmienia się automatycznie. Ta opcja jest domyślnie włączona.

### <a name="show-advanced-build-configurations"></a>Pokaż zaawansowane konfiguracje kompilacji

Po wybraniu opcji konfiguracji kompilacji są wyświetlane na **strony właściwości projektu** okno dialogowe i **strony właściwości rozwiązania** okno dialogowe. Po wyczyszczeniu, opcji konfiguracji kompilacji nie są wyświetlane na **strony właściwości projektu** okno dialogowe i **strony właściwości rozwiązania** okno dialogowe dla języka Visual Basic i C# projektów, które zawierają jeden Konfiguracja lub dwie konfiguracje debugowania i wydania. Jeśli projekt ma konfigurację zdefiniowanych przez użytkownika, są wyświetlane opcje konfiguracji kompilacji.

Jeśli usunięto zaznaczenie, polecenia na **kompilacji** menu, takich jak **Kompiluj rozwiązanie**, **Kompiluj rozwiązanie**, i **czyste rozwiązanie**, są wykonywane w konfiguracji wydania i poleceń na **debugowania** menu, takich jak **Rozpocznij debugowanie** i **Rozpocznij bez debugowania**, są wykonywane na Konfiguracja debugowania.

### <a name="always-show-solution"></a>Zawsze pokazuj rozwiązanie

Po wybraniu rozwiązania i wszystkich poleceń, które działają w rozwiązaniach są zawsze wyświetlane w środowisku IDE. Po wyczyszczeniu, wszystkie projekty są tworzone jako autonomiczny projekty i rozwiązania w Eksploratorze rozwiązań lub poleceń, które działają nie jest wyświetlany w rozwiązania w środowisku IDE, jeśli rozwiązanie zawiera tylko jeden projekt.

::: moniker range="vs-2017"

### <a name="save-new-projects-when-created"></a>Zapisz nowe projekty po utworzeniu

Po wybraniu, można określić lokalizację dla projektu w **nowy projekt** okno dialogowe. Po wyczyszczeniu, wszystkie nowe projekty są tworzone jako projektów tymczasowych. Podczas pracy z projektami tymczasowej, można tworzyć i eksperymentować z projektem, bez konieczności określania lokalizacji na dysku.

::: moniker-end

### <a name="warn-user-when-the-project-location-is-not-trusted"></a>Ostrzegaj użytkownika, gdy lokalizacja projektu nie jest zaufana

Jeśli spróbujesz utworzyć nowy projekt lub Otwórz istniejący projekt w lokalizacji, która nie jest w pełni zaufany (na przykład na ścieżkę UNC lub ścieżki HTTP), zostanie wyświetlony komunikat. Użyj tej opcji, aby określić, czy komunikat jest wyświetlany za każdym razem, spróbuj utworzyć lub otworzyć projekt w lokalizacji, która nie jest w pełni zaufany.

### <a name="show-output-window-when-build-starts"></a>Pokaż okno dane wyjściowe, gdy rozpoczyna się kompilacja

Automatycznie wyświetla [okno danych wyjściowych](../../ide/reference/output-window.md) w środowisku IDE na początku rozwiązania kompilacji.

### <a name="prompt-for-symbolic-renaming-when-renaming-files"></a>Monituj o symboliczną zmianę nazwy podczas zmieniania nazw plików

Po wybraniu programu Visual Studio Wyświetla okno komunikatu z pytaniem, czy jego powinien również zmienić nazwę wszystkie odwołania w projekcie do elementu kodu.

### <a name="prompt-before-moving-files-to-a-new-location"></a>Monituj przed przeniesieniem plików do nowej lokalizacji

Po wybraniu programu Visual Studio Wyświetla okno komunikatu potwierdzenia przed lokalizacje plików zostaną zmienione przez działania w **Eksploratora rozwiązań**.

### <a name="reopen-documents-on-solution-load"></a>Otwórz dokumenty na ładowanie rozwiązań

**Wprowadzone w programie Visual Studio 2017 w wersji 15.8**

Po wybraniu pozostawione otwarte rozwiązanie poprzednio został zamknięty automatycznie otwarciem po otwarciu rozwiązania.

Ponownie otworzyć niektórych typów plików, projektantów lub można opóźnić ładowania rozwiązania. Usuń zaznaczenie pola wyboru tę opcję, aby [poprawy wydajności ładowania rozwiązań](../../ide/visual-studio-performance-tips-and-tricks.md#disable-automatic-file-restore) Jeśli nie chcesz przywrócić poprzedni kontekst tego rozwiązania.

## <a name="locations-page"></a>Strona lokalizacje

Poniższe opcje są dostępne na **lokalizacje** strony.

### <a name="projects-location"></a>Lokalizacja projektów

Określa domyślną lokalizację, gdzie program Visual Studio tworzy nowe projekty i rozwiązania folderów. Kilka okien dialogowych również użyć lokalizacji zestawu w przypadku tej opcji dla folderu punktów początkowych. Na przykład **Otwórz projekt** okno dialogowe korzysta z tej lokalizacji dla **Moje projekty** skrótów.

### <a name="user-project-templates-location"></a>Lokalizacja szablonów projektów użytkownika

Określa domyślną lokalizację, **nowy projekt** okno dialogowe używa w celu utworzenia listy **Moje szablony**. Aby uzyskać więcej informacji, zobacz [jak: Lokalizowanie i organizacja szablonów](../../ide/how-to-locate-and-organize-project-and-item-templates.md).

### <a name="user-item-templates-location"></a>Lokalizacja szablonów elementów użytkownika

Określa domyślną lokalizację, **Dodaj nowy element** okno dialogowe używa w celu utworzenia listy **Moje szablony**. Aby uzyskać więcej informacji, zobacz [jak: Lokalizowanie i organizacja szablonów](../../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Zobacz także

- [Okno dialogowe Opcje, projekty i rozwiązania, kompilowanie i uruchamianie](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Okno dialogowe Opcje, Projekty i rozwiązania, Projekty internetowe](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)
