---
title: Weryfikacja kodu przy użyciu diagramów zależności
description: Dowiedz się, że aby upewnić się, że kod nie jest w konflikcie z jego projektem, należy zweryfikować kod za pomocą diagramów zależności w Visual Studio.
ms.custom: SEO-VS-2020
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
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1f2d62433d150f61e9a7e21cceb20eb715a0767a
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388363"
---
# <a name="validate-code-with-dependency-diagrams"></a>Weryfikacja kodu przy użyciu diagramów zależności

## <a name="why-use-dependency-diagrams"></a>Dlaczego warto używać diagramów zależności?

Aby upewnić się, że kod nie jest w konflikcie z jego projektem, zweryfikuj kod za pomocą diagramów zależności w Visual Studio. Może to ułatwić:

- Znajdowanie konfliktów między zależnościami w kodzie i zależnościami na diagramie zależności.

- Znajdowanie zależności, na które mogły mieć wpływ proponowane zmiany.

   Na przykład można edytować diagram zależności, aby wyświetlić potencjalne zmiany architektury, a następnie zweryfikować kod, aby zobaczyć zależności, których dotyczy problem.

- Refaktoryzację lub migrację kodu do innego projektu.

   Znajdowanie kodu lub zależności, które wymagają pracy przy przenoszeniu kodu do innej architektury.

**Wymagania**

- Visual Studio

  Aby utworzyć diagram zależności dla projektu .NET Core, musisz mieć program Visual Studio 2019 w wersji 16.2 lub nowszej.

- Rozwiązanie, które zawiera projekt modelowania z diagramem zależności. Ten diagram zależności musi być połączony z artefaktami w języku C# lub Visual Basic projektach, które chcesz zweryfikować. Zobacz [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md).

Aby sprawdzić, które wersje usługi Visual Studio obsługują tę funkcję, zobacz Obsługa wersji dla [architektury i narzędzi do modelowania.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

Kod można zweryfikować ręcznie z otwartego diagramu zależności w Visual Studio wiersza polecenia. Możesz również walidować kod automatycznie podczas uruchamiania kompilacji lokalnych Azure Pipelines kompilacji. Zobacz [channel 9 wideo: projektowanie i weryfikowanie architektury przy użyciu diagramów zależności.](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture)

> [!IMPORTANT]
> Jeśli chcesz uruchomić walidację warstwy przy użyciu programu Team Foundation Server (TFS), musisz również zainstalować tę samą wersję Visual Studio na serwerze kompilacji.

## <a name="live-dependency-validation"></a>Weryfikacja zależności na żywo

Walidacja zależności odbywa się w czasie rzeczywistym, a błędy są natychmiast wyświetlane na **liście błędów**.

* Weryfikacja na żywo jest obsługiwana dla języka C# i Visual Basic.

* Aby włączyć pełną analizę rozwiązania podczas korzystania z weryfikacji zależności na żywo, otwórz ustawienia opcji na złotym pasku wyświetlonym na **liście błędów**.

  - Jeśli nie chcesz widzieć wszystkich problemów z architekturą w rozwiązaniu, możesz trwale odrzucić złoty pasek.
  - Jeśli nie włączysz pełnej analizy rozwiązania, analiza będzie wykonywana tylko dla edytowanych plików.

* Podczas uaktualniania projektów w celu włączenia weryfikacji na żywo w oknie dialogowym jest pokazywany postęp konwersji.

* Podczas aktualizowania projektu w celu weryfikacji zależności na żywo wersja pakietu NuGet jest uaktualniana tak, aby był taki sam dla wszystkich projektów i jest najwyższej wersji w użyciu.

* Dodanie nowego projektu weryfikacji zależności wyzwala aktualizację projektu.

## <a name="see-if-an-item-supports-validation"></a>Sprawdzenie, czy element obsługuje walidację

Warstwy można łączyć z witrynami internetowymi, dokumentami pakietu Office, plikami w postaci zwykłego tekstu i plikami w projektach udostępnianych w wielu aplikacjach, ale proces walidacji nie obejmuje ich. Błędy walidacji nie będą widoczne w przypadku odwołań do projektów lub zestawów połączonych z oddzielnymi warstwami, jeżeli między tymi warstwami nie ma żadnych zależności. Odwołania te nie są uważane za zależności, chyba że w kodzie wykorzystano te odwołania.

1. Na diagramie zależności wybierz co najmniej jedną warstwę, kliknij prawym przyciskiem myszy zaznaczenie, a następnie kliknij pozycję **Wyświetl linki**.

2. W **Eksploratorze warstw** przyjrzyj się kolumnie **Obsługuje walidację.** Jeśli wartością jest false, element nie obsługuje walidacji.

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>Uwzględnienia innych projektów i zestawów .NET w walidacji

Podczas przeciągania elementów do diagramu zależności odwołania do odpowiednich zestawów lub projektów .NET są automatycznie dodawane do folderu **Odwołania** do warstwy w projekcie modelowania. Folder ten zawiera odwołania do zestawów i projektów, które są analizowane podczas walidacji. Można dołączać inne zestawy i projekty .NET do weryfikacji bez ręcznego przeciągania ich do diagramu zależności.

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt modelowania lub folder **Odwołania do warstwy,** a następnie kliknij polecenie **Dodaj odwołanie**.

2. W **oknie dialogowym** Dodawanie odwołania wybierz zestawy lub projekty, a następnie kliknij przycisk **OK.**

## <a name="validate-code-manually"></a>Ręczna walidacja kodu

Jeśli masz otwarty diagram zależności połączony z elementami rozwiązania,  możesz uruchomić polecenie Weryfikuj skrót z diagramu. Możesz również użyć wiersza polecenia, aby uruchomić **polecenie msbuild** z właściwością niestandardową **/p:ValidateArchitecture** ustawioną na **wartość True.** Na przykład, po wprowadzeniu dowolnych zmian w kodzie należy regularnie wykonywać walidację warstwy tak, aby można było wcześnie wychwycić konflikty zależności.

### <a name="validate-code-from-an-open-dependency-diagram"></a>Weryfikowanie kodu z otwartego diagramu zależności

1. Kliknij prawym przyciskiem myszy powierzchnię diagramu, a następnie kliknij polecenie **Weryfikuj architekturę**.

    > [!NOTE]
    > Domyślnie właściwość Akcja **kompilacji** w pliku diagramu zależności (.layerdiagram) jest ustawiona na wartość Weryfikuj, aby diagram został uwzględniony w procesie walidacji. 

     W **oknie Lista błędów** są raporty o wszystkich błędach, które wystąpiły. Aby uzyskać więcej informacji na temat błędów walidacji, zobacz [Rozwiązywanie problemów z walidacją warstwy.](#troubleshoot-layer-validation-issues)

2. Aby wyświetlić źródło każdego błędu, kliknij dwukrotnie błąd w **oknie Lista błędów.**

    > [!NOTE]
    > Visual Studio może pokazywać mapę kodu zamiast źródła błędu. Dzieje się tak, gdy kod jest zależny od zestawu, który nie jest określony przez diagram zależności, lub gdy w kodzie brakuje zależności określonej przez diagram zależności. Przejrzyj mapę kodu lub kod, aby ustalić, czy zależność powinna istnieć. Aby uzyskać więcej informacji na temat map kodu, zobacz [Mapowanie zależności między rozwiązaniami](../modeling/map-dependencies-across-your-solutions.md).

3. Aby zarządzać błędami, zobacz [Rozwiązywanie błędów walidacji warstwy](#resolve-layer-validation-errors).

### <a name="validate-code-at-the-command-prompt"></a>Weryfikowanie kodu w wierszu polecenia

1. Otwórz Visual Studio wiersza polecenia.

2. Wybierz jedną z następujących opcji:

   - Aby zweryfikować kod dla określonego projektu modelowania w rozwiązaniu, uruchom program MSBuild z następującą właściwością niestandardową.

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - lub —

       Przejdź do folderu zawierającego plik projektu modelowania (.modelproj) i diagram zależności, a następnie uruchom program MSBuild z następującą właściwością niestandardową:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - Aby zweryfikować kod dla wszystkich projektów modelowania w rozwiązaniu, uruchom program MSBuild z następującą właściwością niestandardową:

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - lub —

       Przejdź do folderu rozwiązania, który musi zawierać projekt modelowania zawierający diagram zależności, a następnie uruchom program MSBuild z następującą właściwością niestandardową:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     Zostaną wyświetlone wszystkie błędy. Aby uzyskać więcej informacji na temat programu MSBuild, [zobacz MSBuild](../msbuild/msbuild.md) and MSBuild Task (Zadania [MSBuild i MSBuild).](../msbuild/msbuild-task.md)

   Aby uzyskać więcej informacji na temat błędów walidacji, zobacz [Rozwiązywanie problemów z walidacją warstwy.](#troubleshoot-layer-validation-issues)

### <a name="manage-validation-errors"></a>Zarządzanie błędami walidacji

Podczas procesu projektowania możesz pominąć niektóre konflikty zgłoszone podczas walidacji. Na przykład możesz pominąć błędy, które są już poprawiane lub które nie są istotne w konkretnym scenariuszu. Jeśli pominiesz błąd, dobrym rozwiązaniem jest zalogowanie elementu roboczego w programie Team Foundation.

> [!WARNING]
> Musisz mieć już połączenie z kontrolą kodu źródłowego TFS (SCC), aby utworzyć element pracy lub połączyć się z tym elementem. Jeśli spróbujesz otworzyć połączenie z innym programem TFS SCC, Visual Studio automatycznie zamknie bieżące rozwiązanie. Przed próbą utworzenia elementu roboczego lub połączenia z nim upewnij się, że masz już połączenie z odpowiednim SCC. W nowszych wersjach Visual Studio polecenia menu nie są dostępne, jeśli nie masz połączenia z SCC.

#### <a name="create-a-work-item-for-a-validation-error"></a>Tworzenie elementu roboczego dla błędu weryfikacji

- W **oknie Lista** błędów kliknij prawym przyciskiem myszy błąd, wskaż polecenie Utwórz element **pracy,** a następnie kliknij typ elementu roboczego, który chcesz utworzyć.

Za pomocą tych zadań można zarządzać błędami walidacji w **oknie Lista** błędów:

|**Do**|**Wykonaj te kroki**|
|-|-|
|Pomijanie wybranych błędów podczas walidacji|Kliknij prawym przyciskiem myszy jeden lub wiele wybranych błędów, wskaż polecenie Zarządzaj błędami **walidacji,** a następnie kliknij pozycję **Pomiń błędy.**<br /><br /> Pominięte błędy są wyświetlane jako przekreślone. Przy następnym uruchomieniu walidacji te błędy nie pojawią się.<br /><br /> Pominięte błędy są śledzone w pliku .suppressions dla odpowiedniego pliku diagramu zależności.|
|Zaprzestanie pomijania wybranych błędów|Kliknij prawym przyciskiem myszy wybrany pominięty błąd lub błędy, wskaż polecenie Zarządzaj błędami **walidacji,** a następnie kliknij pozycję **Zatrzymaj pomijanie błędów.**<br /><br /> Wybrane pominięte błędy pojawią się przy następnym uruchomieniu walidacji.|
|Przywracanie wszystkich pominiętych błędów w **oknie Lista** błędów|Kliknij prawym przyciskiem myszy w dowolnym miejscu **okna Lista** błędów, wskaż polecenie Zarządzaj błędami **walidacji,** a następnie kliknij polecenie Pokaż **wszystkie pominięte błędy.**|
|Ukryj wszystkie pominięte błędy w **oknie Lista** błędów|Kliknij prawym przyciskiem myszy w dowolnym miejscu **okna Lista** błędów, wskaż polecenie Zarządzaj błędami **walidacji,** a następnie kliknij polecenie Ukryj **wszystkie pominięte błędy.**|

## <a name="validate-code-automatically"></a>Automatyczna walidacja kodu

Walidację warstwy możesz wykonać przy każdym uruchomieniu lokalnej kompilacji. Jeśli Twój zespół korzysta z Azure DevOps, możesz przeprowadzić walidację warstwy za pomocą zaewidencjonowyw bramowych, którą można określić, tworząc niestandardowe zadanie MSBuild, i używać raportów kompilacji do zbierania błędów walidacji. Aby utworzyć kompilacje zaewidencjonarnia bramowego, zobacz [TfVC gated check-in](/azure/devops/pipelines/build/triggers)(Kontrola kontroli wersji serwera Team Ds. kontroli wersji serwera Team).

### <a name="to-validate-code-automatically-during-a-local-build"></a>Aby walidować kod automatycznie podczas lokalnej kompilacji

Użyj edytora tekstów, aby otworzyć plik projektu modelowania (.modelproj), a następnie dołącz następującą właściwość:

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\- lub —

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt modelowania, który zawiera diagram zależności lub diagramy, a następnie kliknij polecenie **Właściwości**.

2. W **oknie** Właściwości ustaw właściwość Validate **Architecture** projektu modelowania na **wartość True**.

    Dotyczy to projektów modelowania w trakcie procesu walidacji.

3. W **Eksplorator rozwiązań** kliknij plik diagramu zależności (.layerdiagram), którego chcesz użyć do walidacji.

4. W **oknie** Właściwości upewnij się,  że właściwość Akcja kompilacji diagramu jest ustawiona na wartość **Weryfikuj**.

    Obejmuje to diagram zależności w procesie walidacji.

Aby zarządzać błędami w oknie Lista błędów, zobacz [Rozwiązywanie błędów walidacji warstwy](#resolve-layer-validation-errors).

## <a name="troubleshoot-layer-validation-issues"></a>Rozwiązywanie problemów związanych z walidacją warstwy

W poniższej tabeli opisano problemy związane z walidacją warstwy i ich rozwiązania. Problemy te różnią się od błędów, które wynikają z konfliktów między kodem i projektem. Aby uzyskać więcej informacji na temat tych błędów, zobacz [Rozwiązywanie problemów z walidacją warstwy](#troubleshoot-layer-validation-issues).

|**Problem**|**Możliwa przyczyna**|**Rozwiązanie**|
|-|-|-|
|Błędy walidacji nie występują w oczekiwany sposób.|Walidacja nie działa na diagramach zależności, które są kopiowane z innych diagramów zależności w Eksplorator rozwiązań i które znajdują się w tym samym projekcie modelowania. Diagramy zależności, które są kopiowane w ten sposób, zawierają te same odwołania co oryginalny diagram zależności.|Dodaj nowy diagram zależności do projektu modelowania.<br /><br /> Skopiuj elementy ze źródłowego diagramu zależności do nowego diagramu.|

## <a name="resolve-layer-validation-errors"></a>Rozwiązywanie błędów walidacji warstwy

Podczas weryfikowania kodu względem diagramu zależności błędy walidacji występują, gdy kod powoduje konflikt z projektem. Na przykład następujące warunki mogą powodować występowanie błędów walidacji:

- Artefakt jest przypisany do niewłaściwej warstwy. W takim przypadku przenieś artefakt.

- Artefakt, taki jak klasa, używa innej klasy w sposób, który powoduje konflikt z architekturą. W tym przypadku zrefaktoryzuj kod, aby usunąć zależność.

Aby rozwiązać te błędy, aktualizuj kod, dopóki nie przestaną pojawiać się błędy podczas walidacji. Zadanie to możesz wykonać w sposób iteracyjny.

W poniższej sekcji opisano składnię, która jest używana w tych błędach, wyjaśniono znaczenie tych błędów i zasugerowano, co można zrobić, aby je rozwiązać lub zarządzać nimi.

|**Składnia**|**Opis**|
|-|-|
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* to artefakt skojarzony z warstwą na diagramie zależności.<br /><br /> *ArtifactTypeN* jest typem *artifactn*, takim jak **klasa** lub **metoda**, na przykład:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Metoda)|
|*Nazwa przestrzeni nazw*|Nazwa przestrzeni nazw.|
|*LayerNameN*|Nazwa warstwy na diagramie zależności.|
|*Dependencytype*|Typ relacji zależności między *artefaktami Artifact1* i *Artifact2.* Na przykład artefakt *Artifact1* ma relację **wywołań** z *artefaktem Artifact2.*|

| **Składnia błędu** | **Opis błędu** |
|-|-|
| DV0001: **Nieprawidłowa zależność** | Ten problem jest zgłaszany, gdy element kodu (przestrzeń nazw, typ, element członkowski) mapowany na warstwę odwołuje się do elementu kodu zamapego na inną warstwę, ale nie ma strzałki zależności między tymi warstwami w diagramie weryfikacji zależności zawierającym te warstwy. Jest to naruszenie ograniczenia zależności. |
| DV1001: **Nieprawidłowa nazwa przestrzeni nazw** | Ten problem jest zgłaszany dla elementu kodu skojarzonego z warstwą, która właściwość "Dozwolone nazwy przestrzeni nazw" nie zawiera przestrzeni nazw, w której ten element kodu jest zdefiniowany. Jest to naruszenie ograniczenia nazewnictwa. Należy pamiętać, że składnia "Dozwolone nazwy przestrzeni nazw" ma być średnikiem listy przestrzeni nazw, w których można zdefiniować elementy kodu skojarzone z warstwą. |
| DV1002: **Zależność od nierozpoznawalnej przestrzeni nazw** | Ten problem jest zgłaszany dla elementu kodu skojarzonego z warstwą i odwołuje się do innego elementu kodu zdefiniowanego w przestrzeni nazw, która jest zdefiniowana we właściwości "Unreferenceable Namespace" warstwy. Jest to naruszenie ograniczenia nazewnictwa. Należy pamiętać, że właściwość "Unreferenceable Namespaces" jest zdefiniowana jako rozdzielana średnikami lista przestrzeni nazw, do których nie należy się odwoływać w elementach kodu skojarzonych z tą warstwą. |
| DV1003: **Niedozwolone nazwy przestrzeni nazw** | Ten problem jest zgłaszany w elemencie kodu skojarzonym z warstwą, która właściwość "Niedozwolone nazwy przestrzeni nazw" zawiera przestrzeń nazw, w której ten element kodu jest zdefiniowany. Jest to naruszenie ograniczenia nazewnictwa. Należy pamiętać, że właściwość "Niedozwolone nazwy przestrzeni nazw" jest zdefiniowana jako rozdzielana średnikami lista przestrzeni nazw, w których nie powinny być zdefiniowane elementy kodu skojarzone z tą warstwą. |
| DV2001: Obecność **diagramu warstwowego** | Ten problem jest zgłaszany w projekcie, który nie zawiera pliku diagramu zależności, ale odwołuje się do analizatorów weryfikacji zależności. Jeśli weryfikacja zależności nie została użyta, możesz usunąć "Microsoft.DependencyValidation.Analyzers" bezpośrednio z witryny Eksplorator rozwiązań lub pominąć to ostrzeżenie. Aby dodać diagram zależności, zobacz [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md). |
| DV2002: **Typy niezamapowane podstawowe** | Ten problem jest zgłaszany, gdy element kodu nie jest mapowany na żadnej warstwie. |
| DV3001: Brak **linku** | Warstwa "*LayerName*" łączy się z *artefaktem ",* którego nie można odnaleźć. Czy nie brakuje odwołania do zestawu? |
| DV9001: **Analiza architektury znalazła błędy wewnętrzne** | Wyniki mogą być niepełne. Aby uzyskać więcej informacji, zobacz szczegółowy dziennik zdarzeń kompilacji lub okno danych wyjściowych. |

## <a name="see-also"></a>Zobacz też

- [Weryfikacja zależności na żywo w Visual Studio](https://devblogs.microsoft.com/devops/live-dependency-validation-in-visual-studio-2017/)
- [Weryfikacja systemu w czasie opracowywania](../modeling/validate-your-system-during-development.md)
- [Wideo: Weryfikowanie zależności architektury w czasie rzeczywistym](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
