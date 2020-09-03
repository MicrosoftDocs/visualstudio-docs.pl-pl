---
title: Weryfikacja kodu przy użyciu diagramów zależności
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, validating
- validation, dependency diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, dependency diagrams
- MSBuild, validating code
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 975fe8eac5657e245027a4811e50bbc93528cfe5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80759702"
---
# <a name="validate-code-with-dependency-diagrams"></a>Weryfikacja kodu przy użyciu diagramów zależności

## <a name="why-use-dependency-diagrams"></a>Dlaczego warto używać diagramów zależności?

Aby upewnić się, że kod nie powoduje konfliktu z projektem, zweryfikuj swój kod przy użyciu diagramów zależności w programie Visual Studio. Może to ułatwić:

- Znajdowanie konfliktów między zależnościami w kodzie i zależnościami na diagramie zależności.

- Znajdowanie zależności, na które mogły mieć wpływ proponowane zmiany.

   Na przykład można edytować diagram zależności, aby pokazać potencjalne zmiany architektury, a następnie sprawdzić poprawność kodu, aby zobaczyć zależności, których to dotyczy.

- Refaktoryzację lub migrację kodu do innego projektu.

   Znajdowanie kodu lub zależności, które wymagają pracy przy przenoszeniu kodu do innej architektury.

**Wymagania**

- Visual Studio

  Aby utworzyć diagram zależności dla projektu .NET Core, musisz mieć program Visual Studio 2019 w wersji 16,2 lub nowszej.

- Rozwiązanie, które ma projekt modelowania z diagramem zależności. Ten diagram zależności musi być połączony z artefaktami w języku C# lub Visual Basic projekty, które chcesz zweryfikować. Zobacz [Tworzenie diagramów zależności na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md).

Aby sprawdzić, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

Kod można zweryfikować ręcznie z otwartego diagramu zależności w programie Visual Studio lub z wiersza polecenia. Możesz również automatycznie sprawdzać kod podczas uruchamiania kompilacji lokalnych lub kompilacji Azure Pipelines. Zobacz [wideo Channel 9: projektowanie i weryfikowanie architektury przy użyciu diagramów zależności](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture).

> [!IMPORTANT]
> Aby uruchomić walidację warstwy przy użyciu Team Foundation Server (TFS), należy również zainstalować tę samą wersję programu Visual Studio na serwerze kompilacji.

## <a name="live-dependency-validation"></a>Walidacja aktywnej zależności

Walidacja zależności występuje w czasie rzeczywistym, a błędy są wyświetlane natychmiast w **Lista błędów**.

* Weryfikacja na żywo jest obsługiwana w językach C# i Visual Basic.

* Aby włączyć pełną analizę rozwiązań podczas korzystania z walidacji na żywo, Otwórz ustawienia opcji na pasku Gold, który pojawia się w **Lista błędów**.

  - Możesz trwale odrzucić złoty pasek, jeśli nie chcesz zobaczyć wszystkich problemów z architekturą w rozwiązaniu.
  - Jeśli nie włączysz pełnej analizy rozwiązania, analiza zostanie wykonana tylko dla edytowanych plików.

* Podczas uaktualniania projektów w celu włączenia walidacji na żywo, w oknie dialogowym zostanie wyświetlony postęp konwersji.

* Podczas aktualizowania projektu na potrzeby walidacji na żywo, wersja pakietu NuGet jest uaktualniana w taki sam sposób dla wszystkich projektów i jest najwyższa w użyciu.

* Dodawanie nowego projektu walidacji zależności wyzwala aktualizację projektu.

## <a name="see-if-an-item-supports-validation"></a>Sprawdzenie, czy element obsługuje walidację

Możesz połączyć warstwy z witrynami sieci Web, dokumentami pakietu Office, zwykłymi plikami tekstowymi i plikami w projektach, które są współużytkowane przez wiele aplikacji, ale proces sprawdzania poprawności nie uwzględni ich. Błędy walidacji nie będą widoczne w przypadku odwołań do projektów lub zestawów połączonych z oddzielnymi warstwami, jeżeli między tymi warstwami nie ma żadnych zależności. Odwołania te nie są uważane za zależności, chyba że w kodzie wykorzystano te odwołania.

1. Na diagramie zależności zaznacz jedną lub więcej warstw, kliknij prawym przyciskiem myszy zaznaczenie, a następnie kliknij przycisk **Wyświetl linki**.

2. W **Eksploratorze warstwy**zapoznaj się z kolumną **Obsługa walidacji** . Jeśli wartością jest false, element nie obsługuje walidacji.

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>Uwzględnienia innych projektów i zestawów .NET w walidacji

Gdy przeciągasz elementy do diagramu zależności, odwołania do odpowiednich zestawów .NET lub projektów są dodawane automatycznie do folderu odwołania do **warstwy** w projekcie modelowania. Folder ten zawiera odwołania do zestawów i projektów, które są analizowane podczas walidacji. Można dołączać inne zestawy i projekty platformy .NET do walidacji bez ręcznego przeciągania ich do diagramu zależności.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt modelowania lub folder **odwołania do warstwy** , a następnie kliknij pozycję **Dodaj odwołanie**.

2. W oknie dialogowym **Dodaj odwołanie** wybierz zespoły lub projekty, a następnie kliknij przycisk **OK**.

## <a name="validate-code-manually"></a>Ręczna walidacja kodu

Jeśli masz otwarty diagram zależności, który jest połączony z elementami rozwiązania, możesz uruchomić polecenie **Weryfikuj** skrót z diagramu. Można także użyć wiersza polecenia, aby uruchomić polecenie **MSBuild** z niestandardową właściwością **/p: ValidateArchitecture** o **wartości true**. Na przykład, po wprowadzeniu dowolnych zmian w kodzie należy regularnie wykonywać walidację warstwy tak, aby można było wcześnie wychwycić konflikty zależności.

### <a name="validate-code-from-an-open-dependency-diagram"></a>Sprawdzanie poprawności kodu z otwartego diagramu zależności

1. Kliknij prawym przyciskiem myszy powierzchnię diagramu, a następnie kliknij polecenie **Weryfikuj architekturę**.

    > [!NOTE]
    > Domyślnie właściwość **Akcja kompilacji** w pliku diagramu zależności (. layerdiagram) jest ustawiona na **Sprawdź poprawność** , aby diagram został uwzględniony w procesie walidacji.

     W oknie **Lista błędów** są raportowane wszystkie błędy, które wystąpiły. Aby uzyskać więcej informacji o błędach walidacji, zobacz [Rozwiązywanie problemów z walidacją warstwy](#troubleshoot-layer-validation-issues).

2. Aby wyświetlić źródło każdego błędu, kliknij dwukrotnie błąd w oknie **Lista błędów** .

    > [!NOTE]
    > Program Visual Studio może wyświetlić mapę kodu zamiast źródła błędu. Dzieje się tak, gdy kod ma zależność od zestawu, który nie jest określony przez diagram zależności, albo w kodzie brakuje zależności określonej przez diagram zależności. Przejrzyj mapę kodu lub kod, aby określić, czy zależność powinna istnieć. Aby uzyskać więcej informacji na temat map kodu, zobacz [zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md).

3. Aby zarządzać błędami, zobacz [Rozwiązywanie błędów walidacji warstwy](#resolve-layer-validation-errors).

### <a name="validate-code-at-the-command-prompt"></a>Sprawdzanie poprawności kodu przy użyciu wiersza polecenia

1. Otwórz wiersz polecenia programu Visual Studio.

2. Wybierz jedną z następujących opcji:

   - Aby sprawdzić poprawność kodu względem określonego projektu modelowania w rozwiązaniu, uruchom program MSBuild z następującą właściwością niestandardową.

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - oraz

       Przejdź do folderu, który zawiera plik projektu modelowania (. modelproj) i diagram zależności, a następnie uruchom program MSBuild z następującą właściwością niestandardową:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - Aby sprawdzić poprawność kodu względem wszystkich projektów modelowania w rozwiązaniu, uruchom program MSBuild z następującą właściwością niestandardową:

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - oraz

       Przejdź do folderu rozwiązania, który musi zawierać projekt modelowania zawierający diagram zależności, a następnie uruchom program MSBuild z następującą właściwością niestandardową:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     Zostaną wyświetlone wszystkie błędy. Aby uzyskać więcej informacji na temat programu MSBuild, zobacz [MSBuild](../msbuild/msbuild.md) i [MSBuild — zadanie](../msbuild/msbuild-task.md).

   Aby uzyskać więcej informacji o błędach walidacji, zobacz [Rozwiązywanie problemów z walidacją warstwy](#troubleshoot-layer-validation-issues).

### <a name="manage-validation-errors"></a>Zarządzanie błędami walidacji

Podczas procesu projektowania możesz pominąć niektóre konflikty zgłoszone podczas walidacji. Na przykład możesz pominąć błędy, które są już poprawiane lub które nie są istotne w konkretnym scenariuszu. W przypadku pominięcia błędu dobrym sposobem jest zarejestrowanie elementu pracy w programie Team Foundation.

> [!WARNING]
> Aby utworzyć element roboczy lub połączyć się z nim, musisz mieć już połączenie z kontrolą kodu źródłowego (SCC) programu TFS. Jeśli spróbujesz otworzyć połączenie z innym TFS SCC, program Visual Studio automatycznie zamknie bieżące rozwiązanie. Upewnij się, że masz już połączenie z odpowiednim SCC, przed podjęciem próby utworzenia lub połączenia z elementem roboczym. W nowszych wersjach programu Visual Studio polecenia menu nie są dostępne, jeśli nie masz połączenia z SCC.

#### <a name="create-a-work-item-for-a-validation-error"></a>Utwórz element roboczy dla błędu walidacji

- W oknie **Lista błędów** kliknij prawym przyciskiem myszy błąd, wskaż polecenie **Utwórz element roboczy**, a następnie kliknij typ elementu pracy, który chcesz utworzyć.

Te zadania umożliwiają zarządzanie błędami walidacji w oknie **Lista błędów** :

|**Działanie**|**Wykonaj następujące kroki**|
|-|-|
|Pomijanie wybranych błędów podczas walidacji|Kliknij prawym przyciskiem myszy jeden lub wiele wybranych błędów, wskaż **zarządzanie błędami walidacji**, a następnie kliknij przycisk **Pomiń błędy**.<br /><br /> Pominięte błędy są wyświetlane jako przekreślone. Przy następnym uruchomieniu walidacji te błędy nie pojawią się.<br /><br /> Pominięte błędy są śledzone w pliku. pominięć dla odpowiedniego pliku diagramu zależności.|
|Zaprzestanie pomijania wybranych błędów|Kliknij prawym przyciskiem myszy wybrany pominięty błąd lub błędy, wskaż polecenie **Zarządzaj błędami walidacji**, a następnie kliknij przycisk **Zatrzymaj pomijanie błędów**.<br /><br /> Wybrane pominięte błędy pojawią się przy następnym uruchomieniu walidacji.|
|Przywróć wszystkie pominięte błędy w oknie **Lista błędów**|Kliknij prawym przyciskiem myszy w dowolnym miejscu okna **Lista błędów** , wskaż polecenie **Zarządzaj błędami walidacji**, a następnie kliknij przycisk **Pokaż wszystkie pominięte błędy**.|
|Ukryj wszystkie pominięte błędy w oknie **Lista błędów**|Kliknij prawym przyciskiem myszy w dowolnym miejscu okna **Lista błędów** , wskaż polecenie **Zarządzaj błędami walidacji**, a następnie kliknij przycisk **Ukryj wszystkie pominięte błędy**.|

## <a name="validate-code-automatically"></a>Automatyczna walidacja kodu

Walidację warstwy możesz wykonać przy każdym uruchomieniu lokalnej kompilacji. Jeśli Twój zespół korzysta z usługi Azure DevOps, można przeprowadzić walidację warstwy za pomocą warunkowych zaewidencjonowania, które można określić przez utworzenie niestandardowego zadania programu MSBuild i użycie raportów kompilacji do zbierania błędów walidacji. Aby utworzyć kompilacje ewidencjonowania warunkowego, zobacz [TFVC ewidencjonowanie warunkowe](/azure/devops/pipelines/build/triggers).

### <a name="to-validate-code-automatically-during-a-local-build"></a>Aby walidować kod automatycznie podczas lokalnej kompilacji

Użyj edytora tekstów, aby otworzyć plik projektu modelowania (.modelproj), a następnie dołącz następującą właściwość:

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\- oraz

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt modelowania zawierający diagram zależności lub diagramy, a następnie kliknij polecenie **Właściwości**.

2. W oknie **Właściwości** ustaw właściwość **Architektura walidacji** projektu modelowania na **wartość true**.

    Dotyczy to projektów modelowania w trakcie procesu walidacji.

3. W **Eksplorator rozwiązań**kliknij plik diagramu zależności (layerdiagram), który ma być używany do walidacji.

4. W oknie **Właściwości** upewnij się, że właściwość **Akcja kompilacji** diagramu jest ustawiona na **Sprawdź poprawność**.

    Obejmuje to diagram zależności w procesie walidacji.

Aby zarządzać błędami w oknie Lista błędów, zobacz [Rozwiązywanie błędów walidacji warstwy](#resolve-layer-validation-errors).

## <a name="troubleshoot-layer-validation-issues"></a>Rozwiązywanie problemów związanych z walidacją warstwy

W poniższej tabeli opisano problemy związane z walidacją warstwy i ich rozwiązania. Problemy te różnią się od błędów, które wynikają z konfliktów między kodem i projektem. Aby uzyskać więcej informacji o tych błędach, zobacz [Rozwiązywanie problemów z walidacją warstwy](#troubleshoot-layer-validation-issues).

|**Problem**|**Możliwa przyczyna**|**Rozdzielczość**|
|-|-|-|
|Błędy walidacji nie występują w oczekiwany sposób.|Walidacja nie działa na diagramach zależności, które są kopiowane z innych diagramów zależności w Eksplorator rozwiązań i które znajdują się w tym samym projekcie modelowania. Diagramy zależności, które są kopiowane w ten sposób, zawierają te same odwołania, jak oryginalny diagram zależności.|Dodaj nowy diagram zależności do projektu modelowania.<br /><br /> Skopiuj elementy z diagramu zależności źródłowej do nowego diagramu.|

## <a name="resolve-layer-validation-errors"></a>Rozwiązywanie błędów walidacji warstwy

Podczas sprawdzania poprawności kodu względem diagramu zależności, błędy walidacji występują, gdy kod powoduje konflikt z projektem. Na przykład następujące warunki mogą powodować występowanie błędów walidacji:

- Artefakt jest przypisany do niewłaściwej warstwy. W takim przypadku przenieś artefakt.

- Artefakt, taki jak klasa, używa innej klasy w sposób, który powoduje konflikt z architekturą. W tym przypadku zrefaktoryzuj kod, aby usunąć zależność.

Aby rozwiązać te błędy, aktualizuj kod, dopóki nie przestaną pojawiać się błędy podczas walidacji. Zadanie to możesz wykonać w sposób iteracyjny.

W poniższej sekcji opisano składnię, która jest używana w tych błędach, wyjaśniono znaczenie tych błędów i zasugerowano, co można zrobić, aby je rozwiązać lub zarządzać nimi.

|**Składnia**|**Opis**|
|-|-|
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* to artefakt, który jest skojarzony z warstwą na diagramie zależności.<br /><br /> *ArtifactTypeN* jest typem *ArtifactN*, takim jak **Klasa** lub **Metoda**, na przykład:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Metoda)|
|*NamespaceNameN*|Nazwa przestrzeni nazw.|
|*LayerNameN*|Nazwa warstwy na diagramie zależności.|
|*DependencyType*|Typ relacji zależności między *Artifact1* i *Artifact2*. Na przykład *Artifact1* ma związek **wywołań** z *Artifact2*.|

| **Składnia błędu** | **Opis błędu** |
|-|-|
| DV0001: **nieprawidłowa zależność** | Ten problem jest raportowany, gdy element kodu (przestrzeń nazw, typ, członek) mapowany na warstwę odwołuje się do elementu kodu zamapowanego na inną warstwę, ale nie ma żadnej strzałki zależności między tymi warstwami w diagramie walidacji zależności zawierających te warstwy. Jest to naruszenie ograniczenia zależności. |
| DV1001: **Nieprawidłowa nazwa przestrzeni nazw** | Ten problem jest raportowany w elemencie kodu skojarzonym z warstwą, której właściwość "dozwolone nazwy przestrzeni nazw" nie zawiera przestrzeni nazw, w której jest zdefiniowany ten element kodu. Jest to naruszenie ograniczenia nazw. Należy zauważyć, że składnia "dozwolonych nazw przestrzeni nazw" ma być listą rozdzielaną średnikami przestrzeni nazw, w których elementy kodu skojarzone z to warstwy mogą być zdefiniowane. |
| DV1002: **zależność od przestrzeni nazw bez odwołania** | Ten problem jest raportowany dla elementu kodu skojarzonego z warstwą i odwołującego się do innego elementu kodu zdefiniowanego w przestrzeni nazw, który jest zdefiniowany w właściwości "Przestrzeń nazw", która nie jest do odwołania. Jest to naruszenie ograniczenia nazw. Należy zauważyć, że właściwość "przestrzenie nazw, których nie można odwołać" jest zdefiniowana jako rozdzielana średnikami lista przestrzeni nazw, do których nie należy odwoływać się w elementach kodu skojarzonych z tą warstwą. |
| DV1003: **niedozwolona nazwa przestrzeni nazw** | Ten problem jest raportowany w elemencie kodu skojarzonym z warstwą, której właściwość "niedozwolone nazwy przestrzeni nazw" zawiera przestrzeń nazw, w której jest zdefiniowany ten element kodu. Jest to naruszenie ograniczenia nazw. Należy zauważyć, że właściwość "niedozwolone nazwy przestrzeni nazw" jest definiowana jako rozdzielana średnikami lista przestrzeni nazw, w których nie należy definiować elementów kodu skojarzonych z tą warstwą. |
| DV2001: **obecność diagramu warstwowego** | Ten problem jest raportowany w projekcie, który nie zawiera pliku diagramu zależności, ale odwołuje się do analizatorów walidacji zależności. Jeśli walidacja zależności nie została użyta, można usunąć "Microsoft. DependencyValidation. analizatory" bezpośrednio z Eksplorator rozwiązań lub pominąć to ostrzeżenie. Aby dodać diagram zależności, zobacz [Tworzenie diagramów zależności na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md). |
| DV2002: **Niemapowane typy podstawowe** | Ten problem jest raportowany, gdy element kodu nie jest zamapowany na żadną warstwę. |
| DV3001: **Brak linku** | Warstwa "*LayerName*" łączy się z "*artefaktem*", którego nie można znaleźć. Czy nie brakuje odwołania do zestawu? |
| DV9001: **Analiza architektury znalazła błędy wewnętrzne** | Wyniki mogą być niepełne. Aby uzyskać więcej informacji, zobacz szczegółowy dziennik zdarzeń kompilacji lub okno danych wyjściowych. |

## <a name="see-also"></a>Zobacz też

- [Walidacja zależności na żywo w programie Visual Studio](https://devblogs.microsoft.com/devops/live-dependency-validation-in-visual-studio-2017/)
- [Weryfikacja systemu w czasie opracowywania](../modeling/validate-your-system-during-development.md)
- [Wideo: Weryfikuj zależności architektury w czasie rzeczywistym](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
