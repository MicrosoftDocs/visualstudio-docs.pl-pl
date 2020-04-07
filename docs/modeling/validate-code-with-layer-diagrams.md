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
ms.sourcegitcommit: 273b657e115c1756adb84e0e56b6f2c709bcee76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2020
ms.locfileid: "80759702"
---
# <a name="validate-code-with-dependency-diagrams"></a>Weryfikacja kodu przy użyciu diagramów zależności

## <a name="why-use-dependency-diagrams"></a>Dlaczego warto używać diagramów zależności?

Aby upewnić się, że kod nie jest w konflikcie z jego projektu, sprawdź poprawność kodu z diagramów zależności w programie Visual Studio. Może to ułatwić:

- Znajdź konflikty między zależnościami w kodzie i zależności na diagramie zależności.

- Znajdowanie zależności, na które mogły mieć wpływ proponowane zmiany.

   Na przykład można edytować diagram zależności, aby wyświetlić potencjalne zmiany architektury, a następnie sprawdzić poprawność kodu, aby wyświetlić zależności, których dotyczy problem.

- Refaktoryzację lub migrację kodu do innego projektu.

   Znajdowanie kodu lub zależności, które wymagają pracy przy przenoszeniu kodu do innej architektury.

**Wymagania**

- Visual Studio

  Aby utworzyć diagram zależności dla projektu .NET Core, musisz mieć visual studio 2019 w wersji 16.2 lub nowszej.

- Rozwiązanie, które ma projekt modelowania z diagramem zależności. Ten diagram zależności musi być połączony z artefaktami w projektach języka C# lub Visual Basic, które chcesz sprawdzić poprawność. Zobacz [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md).

Aby zobaczyć, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa architektury i modelowania w wersji.](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

Kod można sprawdzić ręcznie z otwartego diagramu zależności w programie Visual Studio lub z wiersza polecenia. Można również sprawdzić poprawność kodu automatycznie podczas uruchamiania kompilacji lokalnych lub kompilacji usługi Azure Potoki. Zobacz [Channel 9 Video: Projektowanie i sprawdzanie poprawności architektury przy użyciu diagramów zależności](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture).

> [!IMPORTANT]
> Jeśli chcesz uruchomić sprawdzanie poprawności warstwy przy użyciu programu Team Foundation Server (TFS), należy również zainstalować tę samą wersję programu Visual Studio na serwerze kompilacji.

## <a name="live-dependency-validation"></a>Sprawdzanie poprawności zależności na żywo

Sprawdzanie poprawności zależności odbywa się w czasie rzeczywistym, a błędy są wyświetlane natychmiast na **liście błędów**.

* Sprawdzanie poprawności na żywo jest obsługiwane dla języka C# i Visual Basic.

* Aby włączyć pełną analizę rozwiązania podczas korzystania z sprawdzania poprawności zależności na żywo, otwórz ustawienia opcji z paska złota, który pojawia się na **liście błędów**.

  - Możesz trwale odrzucić sztabka złota, jeśli nie jesteś zainteresowany zobaczeniem wszystkich problemów architektonicznych w rozwiązaniu.
  - Jeśli nie włączysz pełnej analizy rozwiązania, analiza jest wykonywana tylko dla edytowanych plików.

* Podczas uaktualniania projektów w celu włączenia sprawdzania poprawności na żywo okno dialogowe pokazuje postęp konwersji.

* Podczas aktualizowania projektu do sprawdzania poprawności zależności na żywo, wersja pakietu NuGet jest uaktualniany do tego samego dla wszystkich projektów i jest najwyższą wersją w użyciu.

* Dodanie nowego projektu sprawdzania poprawności zależności wyzwala aktualizację projektu.

## <a name="see-if-an-item-supports-validation"></a>Sprawdzenie, czy element obsługuje walidację

Warstwy można łączyć z witrynami sieci Web, dokumentami pakietu Office, plikami tekstowymi i plikami w projektach udostępnianych w wielu aplikacjach, ale proces sprawdzania poprawności nie będzie ich uwzględniał. Błędy walidacji nie będą widoczne w przypadku odwołań do projektów lub zestawów połączonych z oddzielnymi warstwami, jeżeli między tymi warstwami nie ma żadnych zależności. Odwołania te nie są uważane za zależności, chyba że w kodzie wykorzystano te odwołania.

1. Na diagramie zależności zaznacz jedną lub więcej warstw, kliknij prawym przyciskiem myszy zaznaczenie, a następnie kliknij polecenie **Wyświetl łącza**.

2. W **Eksploratorze warstw**zajrzy na kolumnę **Obsługuje sprawdzanie poprawności.** Jeśli wartością jest false, element nie obsługuje walidacji.

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>Uwzględnienia innych projektów i zestawów .NET w walidacji

Podczas przeciągania elementów do diagramu zależności odwołania do odpowiednich zestawów lub projektów platformy .NET są automatycznie dodawane do folderu **Odsysania warstw** w projekcie modelowania. Folder ten zawiera odwołania do zestawów i projektów, które są analizowane podczas walidacji. Można dołączyć inne zestawy i projekty platformy .NET do sprawdzania poprawności bez ręcznego przeciągania ich do diagramu zależności.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt modelowania lub folder **Odsyłania do warstwy,** a następnie kliknij polecenie **Dodaj odwołanie**.

2. W oknie dialogowym **Dodawanie odwołania** zaznacz zestawy lub projekty, a następnie kliknij przycisk **OK**.

## <a name="validate-code-manually"></a>Ręczna walidacja kodu

Jeśli masz otwarty diagram zależności, który jest połączony z elementami rozwiązania, można uruchomić **polecenie Poprawność** skrótu z diagramu. Można również użyć wiersza polecenia, aby uruchomić polecenie **msbuild** z właściwość niestandardową **/p:ValidateArchitecture** ustawioną na **True**. Na przykład, po wprowadzeniu dowolnych zmian w kodzie należy regularnie wykonywać walidację warstwy tak, aby można było wcześnie wychwycić konflikty zależności.

### <a name="validate-code-from-an-open-dependency-diagram"></a>Sprawdzanie poprawności kodu z otwartego diagramu zależności

1. Kliknij prawym przyciskiem myszy powierzchnię diagramu, a następnie kliknij polecenie **Sprawdź poprawność architektury**.

    > [!NOTE]
    > Domyślnie właściwość **Build Action** na diagramie zależności (layerdiagram) jest ustawiona na **Sprawdź poprawność,** dzięki czemu diagram jest uwzględniony w procesie sprawdzania poprawności.

     Okno **Lista błędów** zgłasza wszelkie błędy, które występują. Aby uzyskać więcej informacji na temat błędów sprawdzania poprawności, zobacz [Rozwiązywanie problemów z sprawdzaniem poprawności warstwy](#troubleshoot-layer-validation-issues).

2. Aby wyświetlić źródło każdego błędu, kliknij dwukrotnie błąd w oknie **Lista błędów.**

    > [!NOTE]
    > Visual Studio może wyświetlać mapę kodu zamiast źródła błędu. Dzieje się tak, gdy kod ma zależność od zestawu, który nie jest określony przez diagram zależności lub brakuje kodu zależności, która jest określona przez diagram zależności. Przejrzyj mapę kodu lub kod, aby ustalić, czy zależność powinna istnieć. Aby uzyskać więcej informacji na temat map kodu, zobacz [Mapowanie zależności między rozwiązaniami](../modeling/map-dependencies-across-your-solutions.md).

3. Aby zarządzać błędami, zobacz [Rozwiązywanie problemów z sprawdzaniem poprawności warstwy](#resolve-layer-validation-errors).

### <a name="validate-code-at-the-command-prompt"></a>Sprawdzanie poprawności kodu w wierszu polecenia

1. Otwórz wiersz polecenia programu Visual Studio.

2. Wybierz jedną z następujących opcji:

   - Aby sprawdzić poprawność kodu względem określonego projektu modelowania w rozwiązaniu, uruchom MSBuild z następującą właściwością niestandardową.

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - lub -

       Przejdź do folderu zawierającego plik projektu modelowania (modelproj) i diagram zależności, a następnie uruchom msbuild z następującą właściwością niestandardową:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - Aby sprawdzić poprawność kodu względem wszystkich projektów modelowania w rozwiązaniu, uruchom MSBuild z następującą właściwością niestandardową:

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - lub -

       Przejdź do folderu rozwiązania, który musi zawierać projekt modelowania, który zawiera diagram zależności, a następnie uruchom MSBuild z następującą właściwością niestandardową:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     Zostaną wyświetlone wszystkie błędy. Aby uzyskać więcej informacji na temat MSBuild, zobacz [MSBuild](../msbuild/msbuild.md) i [MSBuild Task](../msbuild/msbuild-task.md).

   Aby uzyskać więcej informacji na temat błędów sprawdzania poprawności, zobacz [Rozwiązywanie problemów z sprawdzaniem poprawności warstwy](#troubleshoot-layer-validation-issues).

### <a name="manage-validation-errors"></a>Zarządzanie błędami walidacji

Podczas procesu projektowania możesz pominąć niektóre konflikty zgłoszone podczas walidacji. Na przykład możesz pominąć błędy, które są już poprawiane lub które nie są istotne w konkretnym scenariuszu. Po wygaszenie błędu, jest dobrą praktyką, aby zalogować element pracy w Team Foundation.

> [!WARNING]
> Aby utworzyć element roboczy, musisz już nawiązać połączenie z formantem kodu źródłowego TFS (SCC). Jeśli spróbujesz otworzyć połączenie z innym TFS SCC, Visual Studio zamyka bieżące rozwiązanie automatycznie. Upewnij się, że są już połączone z odpowiednim SCC przed podjęciem próby utworzenia lub łączenia z elementem pracy. W późniejszych wersjach programu Visual Studio polecenia menu nie są dostępne, jeśli nie są połączone z SCC.

#### <a name="create-a-work-item-for-a-validation-error"></a>Tworzenie elementu roboczego dla błędu sprawdzania poprawności

- W oknie **Lista błędów** kliknij prawym przyciskiem myszy błąd, wskaż polecenie **Utwórz element pracy**, a następnie kliknij typ elementu pracy, który chcesz utworzyć.

Te zadania obejmują zarządzanie błędami sprawdzania poprawności w oknie **Lista błędów:**

|**Do**|**Wykonaj następujące kroki**|
|-|-|
|Pomijanie wybranych błędów podczas walidacji|Kliknij prawym przyciskiem myszy jeden lub wiele zaznaczonych błędów, wskaż polecenie **Zarządzaj błędami sprawdzania poprawności,** a następnie kliknij polecenie **Pomiń błędy**.<br /><br /> Pominięte błędy są wyświetlane jako przekreślone. Przy następnym uruchomieniu walidacji te błędy nie pojawią się.<br /><br /> Pominięte błędy są śledzone w pliku .suppressions dla odpowiedniego pliku diagramu zależności.|
|Zaprzestanie pomijania wybranych błędów|Kliknij prawym przyciskiem myszy zaznaczony wygaszony błąd lub błędy, wskaż polecenie **Zarządzaj błędami sprawdzania poprawności,** a następnie kliknij polecenie **Zatrzymaj pomijanie błędów**.<br /><br /> Wybrane pominięte błędy pojawią się przy następnym uruchomieniu walidacji.|
|Przywracanie wszystkich pominiętych błędów w oknie **Lista błędów**|Kliknij prawym przyciskiem myszy dowolne miejsce w oknie **Lista błędów,** wskaż polecenie **Zarządzaj błędami sprawdzania poprawności,** a następnie kliknij polecenie **Pokaż wszystkie pominięte błędy**.|
|Ukrywanie wszystkich pominiętych błędów w oknie **Lista błędów**|Kliknij prawym przyciskiem myszy dowolne miejsce w oknie **Lista błędów,** wskaż polecenie **Zarządzaj błędami sprawdzania poprawności,** a następnie kliknij polecenie **Ukryj wszystkie pominięte błędy**.|

## <a name="validate-code-automatically"></a>Automatyczna walidacja kodu

Walidację warstwy możesz wykonać przy każdym uruchomieniu lokalnej kompilacji. Jeśli zespół używa usługi Azure DevOps, można wykonać sprawdzanie poprawności warstwy z gated ewidencjonowania, które można określić, tworząc niestandardowe zadanie MSBuild i używać raportów kompilacji do zbierania błędów sprawdzania poprawności. Aby utworzyć kompilacje ewidencjonowania z bramką, zobacz [TFVC gated check-in](/azure/devops/pipelines/build/triggers).

### <a name="to-validate-code-automatically-during-a-local-build"></a>Aby walidować kod automatycznie podczas lokalnej kompilacji

Użyj edytora tekstów, aby otworzyć plik projektu modelowania (.modelproj), a następnie dołącz następującą właściwość:

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\-lub -

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt modelowania zawierający diagram zależności lub diagramy, a następnie kliknij polecenie **Właściwości**.

2. W oknie **Właściwości** ustaw właściwość Sprawdź **architekturę** projektu modelowania na **True**.

    Dotyczy to projektów modelowania w trakcie procesu walidacji.

3. W **Eksploratorze rozwiązań**kliknij plik diagramu zależności (layerdiagram), którego chcesz użyć do weryfikacji.

4. W oknie **Właściwości** upewnij się, że właściwość **kompilacji** diagramu jest ustawiona na **Sprawdź poprawność**.

    Obejmuje to diagram zależności w procesie sprawdzania poprawności.

Aby zarządzać błędami w oknie Lista błędów, zobacz [Rozwiązywanie problemów z sprawdzaniem poprawności warstwy](#resolve-layer-validation-errors).

## <a name="troubleshoot-layer-validation-issues"></a>Rozwiązywanie problemów związanych z walidacją warstwy

W poniższej tabeli opisano problemy związane z walidacją warstwy i ich rozwiązania. Problemy te różnią się od błędów, które wynikają z konfliktów między kodem i projektem. Aby uzyskać więcej informacji na temat tych błędów, zobacz [Rozwiązywanie problemów z sprawdzaniem poprawności warstwy](#troubleshoot-layer-validation-issues).

|**Problem**|**Możliwa przyczyna**|**Rozdzielczość**|
|-|-|-|
|Błędy walidacji nie występują w oczekiwany sposób.|Sprawdzanie poprawności nie działa na diagramach zależności, które są kopiowane z innych diagramów zależności w Eksploratorze rozwiązań i które znajdują się w tym samym projekcie modelowania. diagramy zależności, które są kopiowane w ten sposób zawierają te same odwołania jak oryginalny diagram zależności.|Dodaj nowy diagram zależności do projektu modelowania.<br /><br /> Skopiuj elementy z diagramu zależności źródłowych do nowego diagramu.|

## <a name="resolve-layer-validation-errors"></a>Rozwiązywanie problemów z błędami sprawdzania poprawności warstw

Podczas sprawdzania poprawności kodu względem diagramu zależności błędy sprawdzania poprawności występują, gdy kod jest w konflikcie z projektem. Na przykład następujące warunki mogą powodować występowanie błędów walidacji:

- Artefakt jest przypisany do niewłaściwej warstwy. W takim przypadku przenieś artefakt.

- Artefakt, taki jak klasa, używa innej klasy w sposób, który powoduje konflikt z architekturą. W tym przypadku zrefaktoryzuj kod, aby usunąć zależność.

Aby rozwiązać te błędy, aktualizuj kod, dopóki nie przestaną pojawiać się błędy podczas walidacji. Zadanie to możesz wykonać w sposób iteracyjny.

W poniższej sekcji opisano składnię, która jest używana w tych błędach, wyjaśniono znaczenie tych błędów i zasugerowano, co można zrobić, aby je rozwiązać lub zarządzać nimi.

|**Składni**|**Opis**|
|-|-|
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* jest artefakt, który jest skojarzony z warstwą na diagramie zależności.<br /><br /> *ArtifactTypeN* jest typem *ArtifactN*, takim jak **klasa** lub **metoda,** na przykład:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Metoda)|
|*Nazwa przestrzeni nazwNameN*|Nazwa przestrzeni nazw.|
|*Nazwa warstwy*|Nazwa warstwy na diagramie zależności.|
|*Dependencytype*|Typ relacji zależności między *Artifact1* i *Artifact2*. Na przykład *Artifact1* ma relację **Wywołania** z *Artifact2*.|

| **Składnia błędów** | **Opis błędu** |
|-|-|
| DV0001: **Nieprawidłowe uzależnienie** | Ten problem jest zgłaszany, gdy element kodu (obszar nazw, typ, element członkowski) mapowany na warstwę odwołuje się do elementu kodu mapowane do innej warstwy, ale nie ma strzałki zależności między tymi warstwami w diagramie sprawdzania poprawności zależności zawierającego te warstwy. Jest to naruszenie ograniczenia zależności. |
| DV1001: **Nieprawidłowa nazwa obszaru nazw** | Ten problem jest zgłaszany na element kodu skojarzony z warstwą, która "Dozwolone nazwy obszaru nazw" właściwość nie zawiera obszaru nazw, w którym ten element kodu jest zdefiniowany. Jest to naruszenie ograniczenia nazewnictwa. Należy zauważyć, że składnia "Dozwolone nazwy obszaru nazw" ma być półkropka lista obszarów nazw, w których elementy kodu skojarzone z są warstwy mogą być zdefiniowane. |
| DV1002: **Zależność od obszaru nazw bez odwołań** | Ten problem jest zgłaszany na element kodu skojarzony z warstwą i odwołuje się do innego elementu kodu zdefiniowanego w obszarze nazw, który jest zdefiniowany we właściwości "Unreferenceable Namespace" warstwy. Jest to naruszenie ograniczenia nazewnictwa. Należy zauważyć, że właściwość "Unre referenceable Namespaces" jest zdefiniowana jako oddzielona średnika lista obszarów nazw, do których nie należy się odwoływać w elementach kodu skojarzonych z tą warstwą. |
| DV1003: **Niedozwolona nazwa obszaru nazw** | Ten problem jest zgłaszany na element kodu skojarzony z warstwą, która "Niedozwolone nazwy obszaru nazw" właściwość zawiera obszar nazw, w którym ten element kodu jest zdefiniowany. Jest to naruszenie ograniczenia nazewnictwa. Należy zauważyć, że właściwość "Niedozwolona nazwa obszaru nazw" jest zdefiniowana jako oddzielona średnika lista obszarów nazw, w których nie należy definiować elementów kodu skojarzonych z tą warstwą. |
| DV2001: **Obecność diagramu warstwowego** | Ten problem jest zgłaszany w projekcie, który nie zawiera pliku diagramu zależności, ale odnosi się do analizatorów sprawdzania poprawności zależności. Jeśli sprawdzanie poprawności zależności nie zostało użyte, można usunąć "Microsoft.DependencyValidation.Analyzers" bezpośrednio z Eksploratora rozwiązań lub pominąć to ostrzeżenie. Aby dodać diagram zależności, zobacz [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md). |
| DV2002: **Baza typów niemapowanych** | Ten problem jest zgłaszany, gdy element kodu nie jest mapowany na dowolną warstwę. |
| DV3001: **Brak łącza** | Layer '*LayerName*' łączy się z '*Artifact*', którego nie można odnaleźć. Czy nie brakuje odwołania do zestawu? |
| DV9001: **Analiza architektoniczna wykryła błędy wewnętrzne** | Wyniki mogą być niepełne. Aby uzyskać więcej informacji, zobacz szczegółowy dziennik zdarzeń kompilacji lub okno danych wyjściowych. |

## <a name="see-also"></a>Zobacz też

- [Sprawdzanie poprawności zależności na żywo w programie Visual Studio](https://devblogs.microsoft.com/devops/live-dependency-validation-in-visual-studio-2017/)
- [Weryfikacja systemu w czasie opracowywania](../modeling/validate-your-system-during-development.md)
- [Klip wideo: sprawdzanie poprawności zależności architektury w czasie rzeczywistym](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
