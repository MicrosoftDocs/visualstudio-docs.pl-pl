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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e21c3699d796d6037d3b8ca0e744e792b9810b6
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67824541"
---
# <a name="validate-code-with-dependency-diagrams"></a>Weryfikacja kodu przy użyciu diagramów zależności

## <a name="why-use-dependency-diagrams"></a>Dlaczego warto używać diagramów zależności?

Aby upewnić się, że kod jest zgodny z projektem, Przeprowadź walidację kodu przy użyciu diagramów zależności w programie Visual Studio. Może to ułatwić:

- Znajdowanie konfliktów między zależnościami w kodzie i zależności na diagram zależności.

- Znajdowanie zależności, na które mogły mieć wpływ proponowane zmiany.

   Na przykład możesz edytować diagram zależności, aby pokazać potencjalne zmiany architektury i następnie walidować kod, aby zobaczyć, których to dotyczy zależności.

- Refaktoryzację lub migrację kodu do innego projektu.

   Znajdowanie kodu lub zależności, które wymagają pracy przy przenoszeniu kodu do innej architektury.

**Wymagania**

- Visual Studio

- Rozwiązanie, które ma projekt modelowania z diagramem zależności. Ten diagram zależności muszą zostać połączone z artefaktami w projektach C# lub Visual Basic, które chcesz zweryfikować. Zobacz [tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md).

> [!NOTE]
> Diagramy zależności nie są obsługiwane dla projektów .NET Core w programie Visual Studio.

Aby zobaczyć, jakie wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługę wersji narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

Możesz walidować kod ręcznie z diagramu Otwórz zależności w programie Visual Studio lub z wiersza polecenia. Możesz również walidować kod automatycznie podczas uruchamiania lokalnych kompilacji lub Azure potoki kompilacji. Zobacz [wideo Channel 9: Projektowanie i Walidacja architektury za pomocą diagramów zależności](http://go.microsoft.com/fwlink/?LinkID=252073).

> [!IMPORTANT]
> Jeśli chcesz uruchomić walidację warstwy za pomocą Team Foundation Server (TFS), należy również zainstalować tę samą wersję programu Visual Studio na serwerze kompilacji.

## <a name="live-dependency-validation"></a>Weryfikacja zależności na żywo

Weryfikacja odbywa się w czasie rzeczywistym i błędy są wyświetlane od razu w **lista błędów**.

* Weryfikacja na żywo jest obsługiwana dla języka C# i Visual Basic.

* Aby włączyć pełnej analizy rozwiązania, gdy za pomocą weryfikacji zależności na żywo, należy otworzyć ustawienia opcji z złoty pasek jest wyświetlany w **lista błędów**.

  - Złoty pasek można odrzucić trwale, jeśli nie jesteś wyświetlenie wszystkich problemów architektury w rozwiązaniu.
  - Jeśli nie włączysz pełnej analizy rozwiązania analiza odbywa się tylko dla plików edytowany.

* Podczas uaktualniania projektów, można włączyć weryfikację na żywo, okna dialogowego pokazuje postęp konwersji.

* Kiedy uaktualniasz projekt weryfikacji zależności na żywo, wersją pakietu NuGet została uaktualniona do być taka sama dla wszystkich projektów i jest najwyższa wersja w użyciu.

* Dodawanie nowych wyzwalaczy projektu weryfikacji zależności aktualizacji projektu.

## <a name="see-if-an-item-supports-validation"></a>Sprawdzenie, czy element obsługuje walidację

Możesz połączyć warstwy z witryn sieci Web, dokumentów pakietu Office, plikami ze zwykłym tekstem i plikami w projektach, które są współużytkowane przez wiele aplikacji, ale proces walidacji nie uwzględni je. Błędy walidacji nie będą widoczne w przypadku odwołań do projektów lub zestawów połączonych z oddzielnymi warstwami, jeżeli między tymi warstwami nie ma żadnych zależności. Odwołania te nie są uważane za zależności, chyba że w kodzie wykorzystano te odwołania.

1. Na diagramie zależności zaznacz jedną lub więcej warstw, kliknij prawym przyciskiem myszy zaznaczenie, a następnie kliknij **Wyświetl łącza**.

2. W **Eksplorator warstw**, Przyjrzyj się **obsługuje walidację** kolumny. Jeśli wartością jest false, element nie obsługuje walidacji.

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>Uwzględnienia innych projektów i zestawów .NET w walidacji

Podczas przeciągania elementów do diagramu zależności odwołania do projektów lub odpowiednich zestawów .NET są dodawane automatycznie do **odwołania do warstwy** folderu w projekcie modelowania. Folder ten zawiera odwołania do zestawów i projektów, które są analizowane podczas walidacji. Może zawierać innych zestawów platformy .NET i projekty do walidacji bez ręcznego przeciągania ich na diagram zależności.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt modelowania lub **odwołania do warstwy** folder, a następnie kliknij **Dodaj odwołanie**.

2. W **Dodaj odwołanie** okno dialogowe, zaznacz zestawy lub projekty, a następnie kliknij przycisk **OK**.

## <a name="validate-code-manually"></a>Ręczna walidacja kodu

Jeśli masz diagram Otwórz zależności, który jest połączony z elementami rozwiązania, możesz uruchomić **weryfikacji** polecenie skrótu z diagramu. Można również użyć wiersza polecenia do uruchomienia **msbuild** polecenia **validatearchitecture** wartość właściwości niestandardowej **True**. Na przykład, po wprowadzeniu dowolnych zmian w kodzie należy regularnie wykonywać walidację warstwy tak, aby można było wcześnie wychwycić konflikty zależności.

### <a name="validate-code-from-an-open-dependency-diagram"></a>Sprawdzanie poprawności kodu z diagramu Otwórz zależności

1. Kliknij prawym przyciskiem myszy powierzchnię diagramu, a następnie kliknij przycisk **sprawdzanie poprawności architektury**.

    > [!NOTE]
    > Domyślnie **Build Action** właściwość zależności pliku diagramu (.layerdiagram) jest ustawiona na **weryfikacji** tak, aby diagram znajduje się w trakcie procesu walidacji.

     **Lista błędów** okna raporty o błędach. Aby uzyskać więcej informacji na temat błędów sprawdzania poprawności, zobacz [rozwiązać problemy ze sprawdzaniem poprawności warstwy](#troubleshoot-layer-validation-issues).

2. Aby wyświetlić źródło każdego błędu, klikaj dwukrotnie poszczególne błędy w **lista błędów** okna.

    > [!NOTE]
    > Program Visual Studio może wyświetlać mapę kodu, zamiast źródła błędu. Dzieje się tak, gdy kod ma zależność od zestawu, który nie jest określona przez diagram zależności lub w kodzie brakuje zależności, która jest określona przez diagram zależności. Przejrzyj mapy kodu lub kod w celu określenia, czy powinna istnieć zależność. Aby uzyskać więcej informacji na temat map kodu, zobacz [mapowanie zależności w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md).

3. Aby zarządzać błędami, zobacz [Rozwiązywanie błędów walidacji warstwy](#resolve-layer-validation-errors).

### <a name="validate-code-at-the-command-prompt"></a>Sprawdź poprawność kodu w wierszu polecenia

1. Otwórz wiersz polecenia programu Visual Studio.

2. Wybierz jedną z następujących opcji:

   - Aby walidować kod dla określonego projektu modelowania w rozwiązaniu, należy uruchomić program MSBuild z następującymi niestandardowymi właściwościami.

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - lub —

       Przejdź do folderu, który zawiera projektu modelowania (.modelproj) plików i zależności na diagramie, a następnie uruchom program MSBuild z następującymi niestandardowymi właściwościami:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - Aby walidować kod dla wszystkich projektów modelowania w rozwiązaniu, należy uruchomić program MSBuild z następującymi niestandardowymi właściwościami:

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - lub —

       Przejdź do folderu rozwiązania, który musi zawierać projekt modelowania, który zawiera diagram zależności, a następnie uruchomić program MSBuild z następującymi niestandardowymi właściwościami:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     Zostaną wyświetlone wszystkie błędy. Aby uzyskać więcej informacji na temat programu MSBuild, zobacz [MSBuild](../msbuild/msbuild.md) i [zadanie MSBuild](../msbuild/msbuild-task.md).

   Aby uzyskać więcej informacji na temat błędów sprawdzania poprawności, zobacz [rozwiązać problemy ze sprawdzaniem poprawności warstwy](#troubleshoot-layer-validation-issues).

### <a name="manage-validation-errors"></a>Zarządzanie błędami walidacji

Podczas procesu projektowania możesz pominąć niektóre konflikty zgłoszone podczas walidacji. Na przykład możesz pominąć błędy, które są już poprawiane lub które nie są istotne w konkretnym scenariuszu. Gdy błąd zostanie pominięty, jest dobrym rozwiązaniem do dziennika element roboczy w programie Team Foundation.

> [!WARNING]
> Możesz musi już być podłączony do TFS źródła kodu kontrolki (SCC) można utworzyć lub połączyć elementu roboczego. Jeśli próbujesz nawiązać połączenie z inną SCC TFS, Visual Studio powoduje zamknięcie bieżącego rozwiązania automatycznie. Upewnij się, że jesteś podłączony do odpowiednich SCC przed przystąpieniem do tworzenia lub łącze do elementu roboczego. W kolejnych wersjach programu Visual Studio polecenia menu nie są dostępne, jeśli nie są połączone SCC.

#### <a name="create-a-work-item-for-a-validation-error"></a>Utwórz element roboczy dla błędu walidacji

- W **lista błędów** okna, kliknij błąd prawym przyciskiem myszy, wskaż opcję **Utwórz element pracy**, a następnie kliknij typ elementu roboczego, który chcesz utworzyć.

Te zadania umożliwiają zarządzanie błędami walidacji w **lista błędów** okna:

|**To**|**Wykonaj następujące kroki**|
|-|-|
|Pomijanie wybranych błędów podczas walidacji|Kliknij prawym przyciskiem myszy jeden lub kilka zaznaczonych błędów, wskaż opcję **zarządzanie błędami walidacji**, a następnie kliknij przycisk **Pomiń błędy**.<br /><br /> Pominięte błędy są wyświetlane jako przekreślone. Przy następnym uruchomieniu walidacji te błędy nie pojawią się.<br /><br /> Pominięte błędy są śledzone w pliku .suppressions związanym z odpowiedniego pliku diagramu zależności.|
|Zaprzestanie pomijania wybranych błędów|Kliknij prawym przyciskiem myszy wybrany pominięty błąd lub błędy, wskaż opcję **zarządzanie błędami walidacji**, a następnie kliknij przycisk **Przestań pomijać błędy**.<br /><br /> Wybrane pominięte błędy pojawią się przy następnym uruchomieniu walidacji.|
|Przywracanie wszystkich pominiętych błędów w **lista błędów** okna|Kliknij prawym przyciskiem myszy w dowolnym miejscu w **lista błędów** okna, wskaż **zarządzanie błędami walidacji**, a następnie kliknij przycisk **Pokaż wszystkie pominięte błędy**.|
|Ukrywanie wszystkich pominiętych błędów w **lista błędów** okna|Kliknij prawym przyciskiem myszy w dowolnym miejscu w **lista błędów** okna, wskaż **zarządzanie błędami walidacji**, a następnie kliknij przycisk **Pokaż wszystkie pominięte błędy**.|

## <a name="validate-code-automatically"></a>Automatyczna walidacja kodu

Walidację warstwy możesz wykonać przy każdym uruchomieniu lokalnej kompilacji. Jeśli Twój zespół używa DevOps platformy Azure, możesz wykonać walidację warstwy z bramkowanymi ewidencjonowaniami, którą można określić, tworząc niestandardowe zadanie MSBuild, a następnie używając raportów kompilacji do zbierania błędów sprawdzania poprawności. Aby utworzyć kompilacje z bramkowanym ewidencjonowaniem, zobacz [TFVC ewidencjonowanie](/azure/devops/pipelines/build/triggers#gated).

### <a name="to-validate-code-automatically-during-a-local-build"></a>Aby walidować kod automatycznie podczas lokalnej kompilacji

Użyj edytora tekstów, aby otworzyć plik projektu modelowania (.modelproj), a następnie dołącz następującą właściwość:

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\- lub —

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt modelowania, który zawiera diagram zależności lub diagramów, a następnie kliknij **właściwości**.

2. W **właściwości** okna, Ustaw projekt modelowania **sprawdzanie poprawności architektury** właściwości **True**.

    Dotyczy to projektów modelowania w trakcie procesu walidacji.

3. W **Eksploratora rozwiązań**, kliknij plik diagramu (.layerdiagram) zależności, którego chcesz używać do sprawdzania poprawności.

4. W **właściwości** okna, upewnij się, że diagram **Build Action** właściwość jest ustawiona na **weryfikacji**.

    Obejmuje to diagram zależności w trakcie procesu walidacji.

Aby zarządzać błędami w oknie Lista błędów, zobacz [Rozwiązywanie błędów walidacji warstwy](#resolve-layer-validation-errors).

## <a name="troubleshoot-layer-validation-issues"></a>Rozwiązywanie problemów związanych z walidacją warstwy

W poniższej tabeli opisano problemy związane z walidacją warstwy i ich rozwiązania. Problemy te różnią się od błędów, które wynikają z konfliktów między kodem i projektem. Aby uzyskać więcej informacji na temat tych błędów, zobacz [rozwiązać problemy ze sprawdzaniem poprawności warstwy](#troubleshoot-layer-validation-issues).

|**Problem**|**Możliwa przyczyna**|**Rozdzielczość**|
|-|-|-|
|Błędy walidacji nie występują w oczekiwany sposób.|Walidacja nie działa na diagramach zależności, które są kopiowane z innych diagramów zależności w Eksploratorze rozwiązań, które działają w tym samym projekcie modelowania. Diagramy zależności, które są kopiowane w ten sposób zawierają te same odwołania, co oryginalny diagram zależności.|Dodaj nowy diagram zależności do projektu modelowania.<br /><br /> Skopiuj elementy z diagramu źródłowego zależności do nowego diagramu.|

## <a name="resolve-layer-validation-errors"></a>Rozwiązywanie błędów walidacji warstwy

Podczas walidacji kodu na podstawie diagram zależności, błędy walidacji występują, gdy kod jest niezgodny z projektem. Na przykład następujące warunki mogą powodować występowanie błędów walidacji:

- Artefakt jest przypisany do niewłaściwej warstwy. W takim przypadku przenieś artefakt.

- Artefakt, taki jak klasa, używa innej klasy w sposób, który powoduje konflikt z architekturą. W tym przypadku zrefaktoryzuj kod, aby usunąć zależność.

Aby rozwiązać te błędy, aktualizuj kod, dopóki nie przestaną pojawiać się błędy podczas walidacji. Zadanie to możesz wykonać w sposób iteracyjny.

W poniższej sekcji opisano składnię, która jest używana w tych błędach, wyjaśniono znaczenie tych błędów i zasugerowano, co można zrobić, aby je rozwiązać lub zarządzać nimi.

|**Składnia**|**Opis**|
|-|-|
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* jest artefaktem skojarzonym z warstwą na diagramie zależności.<br /><br /> *ArtifactTypeN* jest typem *ArtifactN*, takich jak **klasy** lub **metoda**, na przykład:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Metoda)|
|*NamespaceNameN*|Nazwa przestrzeni nazw.|
|*LayerNameN*|Nazwa warstwy na diagramie zależności.|
|*DependencyType*|Typ relacji zależności między *Artifact1* i *Artifact2*. Na przykład *Artifact1* ma **wywołania** relacji z *Artifact2*.|

| **Błąd składni** | **Opis błędu** |
|-|-|
| DV0001: **Nieprawidłowa zależność** | Ten problem jest zgłaszany, gdy element kodu (przestrzeń nazw, typu, składowej) mapowany do odwołania do warstwy element kodu zamapowana do innej warstwy, ale nie ma żadnych strzałki zależności między te warstwy diagram sprawdzania poprawności zależności zawierający tej warstwy. Jest to naruszenie ograniczenia zależności. |
| DV1001: **Nazwa Nieprawidłowa przestrzeń nazw** | Ten problem, jest zgłaszany na element kodu skojarzone z warstwą, którego właściwość "Dozwolone nazwy Namespace" nie zawiera przestrzeń nazw, w którym zdefiniowano element tego kodu. Jest to naruszenie ograniczenia nazewnictwa. Należy zauważyć, że składnia "Dozwolone nazwy Namespace", które ma być rozdzielana średnikami lista przestrzeni nazw w kodzie, które elementy związane z są warstwy mogą być zdefiniowane. |
| DV1002: **Zależność od unreferenceable przestrzeni nazw** | Ten problem, jest zgłaszany na element kodu skojarzone z warstwą i odwoływanie się do innego elementu kod zdefiniowany w przestrzeni nazw, która jest zdefiniowana we właściwości "Unreferenceable Namespace" warstwy. Jest to naruszenie ograniczenia nazewnictwa. Należy pamiętać, że właściwość "Unreferenceable przestrzeni nazw" jest zdefiniowana jako Rozdzielana średnikami lista przestrzeni nazw, które nie powinny istnieć odwołania w elementach kodu skojarzonych z tą warstwą. |
| DV1003: **Niedozwolona przestrzeni nazw** | Ten problem, jest zgłaszany na element kodu skojarzone z warstwą zawierającą właściwość "Niedozwolone nazwy Namespace" w przestrzeni nazw, w którym zdefiniowano element tego kodu. Jest to naruszenie ograniczenia nazewnictwa. Należy pamiętać, że właściwość "Name niedozwolone przestrzeni nazw" jest zdefiniowana jako Rozdzielana średnikami lista nazw w kodzie, który nie powinien być zdefiniowany elementy skojarzone z tą warstwą. |
| DV3001: **Brakujące łącze** | Warstwa "*LayerName*"łączy"*artefaktu*" którego nie można znaleźć. Czy nie brakuje odwołania do zestawu? |
| DV9001: **Analiza architektoniczna znalazła błędy wewnętrzne** | Wyniki mogą być niepełne. Aby uzyskać więcej informacji, zobacz szczegółowy dziennik zdarzeń kompilacji lub okno danych wyjściowych. |

## <a name="see-also"></a>Zobacz także

- [Walidacja aktywnych zależności w programie Visual Studio](https://devblogs.microsoft.com/devops/live-dependency-validation-in-visual-studio-2017/)
- [Weryfikacja systemu w czasie opracowywania](../modeling/validate-your-system-during-development.md)
- [Wideo: Sprawdzanie poprawności zależności architektury w czasie rzeczywistym](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
