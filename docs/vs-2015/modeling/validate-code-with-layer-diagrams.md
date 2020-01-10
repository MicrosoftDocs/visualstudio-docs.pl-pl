---
title: Sprawdzanie poprawności kodu przy użyciu diagramów warstw | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, validating
- validation, layer diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, layer diagrams
- MSBuild, validating code
ms.assetid: 70cbe55d-4b33-4355-b0a7-88c770a6f75c
caps.latest.revision: 84
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 45b82ece15cfef4d313764027c0220453a6d4849
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75845429"
---
# <a name="validate-code-with-layer-diagrams"></a>Weryfikacja kodu przy użyciu diagramów warstw
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby upewnić się, że kod nie powoduje konfliktu z projektem, zweryfikuj swój kod za pomocą diagramów warstwowych w programie Visual Studio. Może to ułatwić:

- Znajdowanie konfliktów między zależnościami w kodzie i na diagramie warstwowym.

- Znajdowanie zależności, na które mogły mieć wpływ proponowane zmiany.

   Na przykład możesz edytować diagram warstwowy, aby pokazać potencjalne zmiany architektury, a następnie walidować kod, aby zobaczyć zależności, na które miały wpływ zmiany.

- Refaktoryzację lub migrację kodu do innego projektu.

   Znajdowanie kodu lub zależności, które wymagają pracy przy przenoszeniu kodu do innej architektury.

  **Requirements**

- {1&gt;Visual Studio&lt;1}

- Program Visual Studio na serwerze Team Foundation Build umożliwia automatyczne sprawdzanie poprawności kodu za pomocą Team Foundation Build

- Rozwiązanie, które ma projekt modelowania z diagramem warstwowym. Diagram warstwowy musi być połączony z artefaktami w projektach Visual C# .NET lub Visual Basic .NET, które chcesz walidować. Zobacz [Tworzenie diagramów warstwy na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md).

  Aby sprawdzić, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

  Możesz walidować kod ręcznie z otwartego diagramu warstwowego w Visual Studio lub z wiersza polecenia. Kod możesz również walidować automatycznie podczas uruchamiania lokalnych kompilacji lub programu Team Foundation Build. Zobacz [wideo Channel 9: projektowanie i weryfikowanie architektury przy użyciu diagramów warstwowych](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture).

> [!IMPORTANT]
> Aby uruchomić walidację warstwy w programie Team Foundation Build, należy również zainstalować tę samą wersję programu Visual Studio na serwerze kompilacji.

- [Sprawdź, czy element obsługuje walidację](#SupportsValidation)

- [Uwzględnij inne zestawy i projekty platformy .NET na potrzeby walidacji](#IncludeReferences)

- [Ręczne Weryfikowanie kodu](#ValidateManually)

- [Automatycznie Weryfikuj kod](#ValidateAuto)

- [Rozwiązywanie problemów z walidacją warstwy](#TroubleshootingValidation)

- [Zrozumienie i rozwiązywanie błędów walidacji warstwy](#UnderstandingValidationErrors)

## <a name="SupportsValidation"></a>Sprawdź, czy element obsługuje walidację
 Możesz połączyć warstwy z witrynami sieci Web, dokumentami pakietu Office, zwykłymi plikami tekstowymi i plikami w projektach, które są współużytkowane przez wiele aplikacji, ale proces sprawdzania poprawności nie uwzględni ich. Błędy walidacji nie będą widoczne w przypadku odwołań do projektów lub zestawów połączonych z oddzielnymi warstwami, jeżeli między tymi warstwami nie ma żadnych zależności. Odwołania te nie są uważane za zależności, chyba że w kodzie wykorzystano te odwołania.

1. Na diagramie warstwy zaznacz jedną lub więcej warstw, kliknij prawym przyciskiem myszy zaznaczenie, a następnie kliknij polecenie **Wyświetl linki**.

2. W **Eksploratorze warstwy**zapoznaj się z kolumną **Obsługa walidacji** . Jeśli wartością jest false, element nie obsługuje walidacji.

## <a name="IncludeReferences"></a>Uwzględnij inne zestawy i projekty platformy .NET na potrzeby walidacji
 Gdy przeciągasz elementy do diagramu warstwowego, odwołania do odpowiednich zestawów .NET lub projektów są dodawane automatycznie do folderu **odwołania do warstwy** w projekcie modelowania. Folder ten zawiera odwołania do zestawów i projektów, które są analizowane podczas walidacji. Możesz dołączyć inne projekty i zestawy .NET do walidacji bez ręcznego przeciągania ich do diagramu warstwowego.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt modelowania lub folder **odwołania do warstwy** , a następnie kliknij pozycję **Dodaj odwołanie**.

2. W oknie dialogowym **Dodaj odwołanie** wybierz zespoły lub projekty, a następnie kliknij przycisk **OK**.

## <a name="ValidateManually"></a>Ręczne Weryfikowanie kodu
 Jeśli masz otwarty diagram warstwowy, który jest połączony z elementami rozwiązania, możesz uruchomić polecenie **Weryfikuj** skrót z diagramu. Można także użyć wiersza polecenia, aby uruchomić polecenie **MSBuild** z niestandardową właściwością **/p: ValidateArchitecture** o **wartości true**. Na przykład, po wprowadzeniu dowolnych zmian w kodzie należy regularnie wykonywać walidację warstwy tak, aby można było wcześnie wychwycić konflikty zależności.

#### <a name="to-validate-code-from-an-open-layer-diagram"></a>Aby walidować kod z otwartego diagramu warstwowego

1. Kliknij prawym przyciskiem myszy powierzchnię diagramu, a następnie kliknij polecenie **Weryfikuj architekturę**.

    > [!NOTE]
    > Domyślnie właściwość **Akcja kompilacji** w pliku diagramu warstwowego (. layerdiagram) jest ustawiona na **Sprawdź poprawność** , aby diagram został uwzględniony w procesie walidacji.

     W oknie **Lista błędów** są raportowane wszystkie błędy, które wystąpiły. Aby uzyskać więcej informacji o błędach walidacji, zobacz [Omówienie i rozwiązywanie błędów walidacji warstwy](#UnderstandingValidationErrors).

2. Aby wyświetlić źródło każdego błędu, kliknij dwukrotnie błąd w oknie **Lista błędów** .

    > [!NOTE]
    > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] może pokazać mapę kodu zamiast źródła błędu. Dzieje się tak, gdy kod ma zależność z zestawem, która nie jest określona przez diagram warstwowy, lub gdy w kodzie brakuje zależności, która jest określona przez diagram warstwowy. Przejrzyj mapę kodu lub kod, aby określić, czy zależność powinna istnieć. Aby uzyskać więcej informacji na temat map kodu, zobacz [zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md).

3. Aby zarządzać błędami, zobacz [zarządzanie błędami walidacji](#ManageErrors).

#### <a name="to-validate-code-at-the-command-prompt"></a>Aby walidować kod z wiersza polecenia

1. Otwórz wiersz polecenia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

2. Wybierz jedną z następujących opcji:

   - Aby sprawdzić poprawność kodu względem określonego projektu modelowania w rozwiązaniu, uruchom [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] z następującą właściwością niestandardową.

     ```
     msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
     ```

     - lub —

       Przejdź do folderu, który zawiera plik projektu modelowania (. modelproj) i diagram warstwowy, a następnie uruchom [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] z następującą właściwością niestandardową:

     ```
     msbuild /p:ValidateArchitecture=true
     ```

   - Aby sprawdzić poprawność kodu względem wszystkich projektów modelowania w rozwiązaniu, uruchom [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] z następującą właściwością niestandardową:

     ```
     msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
     ```

     - lub —

       Przejdź do folderu rozwiązania, który musi zawierać projekt modelowania zawierający diagram warstwowy, a następnie uruchom [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] z następującą właściwością niestandardową:

     ```
     msbuild /p:ValidateArchitecture=true
     ```

     Zostaną wyświetlone wszystkie błędy. Aby uzyskać więcej informacji na temat [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], zobacz [MSBuild](../msbuild/msbuild.md) i [MSBuild Task](../msbuild/msbuild-task.md).

   Aby uzyskać więcej informacji o błędach walidacji, zobacz [Omówienie i rozwiązywanie błędów walidacji warstwy](#UnderstandingValidationErrors).

### <a name="ManageErrors"></a>Zarządzanie błędami walidacji
 Podczas procesu projektowania możesz pominąć niektóre konflikty zgłoszone podczas walidacji. Na przykład możesz pominąć błędy, które są już poprawiane lub które nie są istotne w konkretnym scenariuszu. W przypadku pominięcia błędu dobrym sposobem jest zarejestrowanie elementu pracy w [!INCLUDE[esprfound](../includes/esprfound-md.md)].

> [!WARNING]
> Aby utworzyć element roboczy lub połączyć się z nim, musisz mieć już połączenie z kontrolą kodu źródłowego (SCC) programu TFS. Jeśli spróbujesz otworzyć połączenie z innym TFS SCC, program Visual Studio automatycznie zamknie bieżące rozwiązanie. Upewnij się, że masz już połączenie z odpowiednim SCC, przed podjęciem próby utworzenia lub połączenia z elementem roboczym. W nowszych wersjach programu Visual Studio polecenia menu nie są dostępne, jeśli nie masz połączenia z SCC.

##### <a name="to-create-a-work-item-for-a-validation-error"></a>Aby utworzyć element roboczy dla błędu walidacji

- W oknie **Lista błędów** kliknij prawym przyciskiem myszy błąd, wskaż polecenie **Utwórz element roboczy**, a następnie kliknij typ elementu pracy, który chcesz utworzyć.

  Te zadania umożliwiają zarządzanie błędami walidacji w oknie **Lista błędów** :

|**To**|**Wykonaj następujące kroki**|
|------------|----------------------------|
|Pomijanie wybranych błędów podczas walidacji|Kliknij prawym przyciskiem myszy jeden lub wiele wybranych błędów, wskaż **zarządzanie błędami walidacji**, a następnie kliknij przycisk **Pomiń błędy**.<br /><br /> Pominięte błędy są wyświetlane jako przekreślone. Przy następnym uruchomieniu walidacji te błędy nie pojawią się.<br /><br /> Pominięte błędy są śledzone w pliku .suppressions związanym z odpowiadającym im plikiem diagramu warstwowego.|
|Zaprzestanie pomijania wybranych błędów|Kliknij prawym przyciskiem myszy wybrany pominięty błąd lub błędy, wskaż polecenie **Zarządzaj błędami walidacji**, a następnie kliknij przycisk **Zatrzymaj pomijanie błędów**.<br /><br /> Wybrane pominięte błędy pojawią się przy następnym uruchomieniu walidacji.|
|Przywróć wszystkie pominięte błędy w oknie **Lista błędów**|Kliknij prawym przyciskiem myszy w dowolnym miejscu okna **Lista błędów** , wskaż polecenie **Zarządzaj błędami walidacji**, a następnie kliknij przycisk **Pokaż wszystkie pominięte błędy**.|
|Ukryj wszystkie pominięte błędy w oknie **Lista błędów**|Kliknij prawym przyciskiem myszy w dowolnym miejscu okna **Lista błędów** , wskaż polecenie **Zarządzaj błędami walidacji**, a następnie kliknij przycisk **Ukryj wszystkie pominięte błędy**.|

## <a name="ValidateAuto"></a>Automatycznie Weryfikuj kod
 Walidację warstwy możesz wykonać przy każdym uruchomieniu lokalnej kompilacji. Jeśli Twój zespół używa programu Team Foundation Build, możesz wykonać walidację warstwy z bramkowanymi ewidencjonowaniami, którą można określić, tworząc niestandardowe zadanie MSBuild, a następnie używając raportów kompilacji do zbierania błędów walidacji. Aby utworzyć kompilacje ewidencjonowania warunkowego, zobacz temat [Weryfikowanie zmian przy użyciu procesu kompilacji warunkowego zaewidencjonowania](https://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec).

#### <a name="to-validate-code-automatically-during-a-local-build"></a>Aby walidować kod automatycznie podczas lokalnej kompilacji

- Użyj edytora tekstów, aby otworzyć plik projektu modelowania (.modelproj), a następnie dołącz następującą właściwość:

```
<ValidateArchitecture>true</ValidateArchitecture>
```

 \- lub —

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt modelowania zawierający diagram lub diagram warstwy, a następnie kliknij polecenie **Właściwości**.

2. W oknie **Właściwości** ustaw właściwość **Architektura walidacji** projektu modelowania na **wartość true**.

    Dotyczy to projektów modelowania w trakcie procesu walidacji.

3. W **Eksplorator rozwiązań**kliknij plik diagramu warstwowego (. layerdiagram), który ma być używany do walidacji.

4. W oknie **Właściwości** upewnij się, że właściwość **Akcja kompilacji** diagramu jest ustawiona na **Sprawdź poprawność**.

    Obejmuje to diagram warstwowy w trakcie procesu walidacji.

   Aby zarządzać błędami w oknie Lista błędów, zobacz [zarządzanie błędami walidacji](#ManageErrors).

#### <a name="to-validate-code-automatically-during-a-team-foundation-build"></a>Aby walidować kod automatycznie podczas działania programu Team Foundation Build

1. W **Team Explorer**kliknij dwukrotnie definicję kompilacji, a następnie kliknij przycisk **proces**.

2. W obszarze **parametry procesu kompilacji**rozwiń pozycję **kompilacja**, a następnie wpisz następujące polecenie w parametrze **argumenty MSBuild** :

    `/p:ValidateArchitecture=true`

   Aby uzyskać więcej informacji o błędach walidacji, zobacz [Omówienie i rozwiązywanie błędów walidacji warstwy](#UnderstandingValidationErrors). Aby uzyskać więcej informacji na temat [!INCLUDE[esprbuild](../includes/esprbuild-md.md)], zobacz:

- [Kompiluj aplikację](/azure/devops/pipelines/index)

- [Użyj szablonu domyślnego dla procesu kompilacji](https://msdn.microsoft.com/library/43930b12-c21b-4599-a980-2995e3d16e31)

- [Modyfikowanie starszej kompilacji opartej na UpgradeTemplate. XAML](https://msdn.microsoft.com/library/ee1a8259-1dd1-4a10-9563-66c5446ef41c)

- [Dostosuj szablon procesu kompilacji](https://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)

- [Monitoruj postęp uruchomionej kompilacji](https://msdn.microsoft.com/library/e51e3bad-2d1d-4b7b-bfcc-c43439c6c8ef)

## <a name="TroubleshootingValidation"></a>Rozwiązywanie problemów z walidacją warstwy
 W poniższej tabeli opisano problemy związane z walidacją warstwy i ich rozwiązania. Problemy te różnią się od błędów, które wynikają z konfliktów między kodem i projektem. Aby uzyskać więcej informacji o tych błędach, zobacz [Omówienie i rozwiązywanie błędów walidacji warstwy](#UnderstandingValidationErrors).

|**Problem**|**Możliwa przyczyna**|**Rozdzielczość**|
|---------------|------------------------|--------------------|
|Błędy walidacji nie występują w oczekiwany sposób.|Walidacja nie działa na diagramach warstwowych, które są kopiowane z innych diagramów warstwowych w Eksploratorze rozwiązań i które są w tym samym projekcie modelowania. Diagramy warstwowe kopiowane w ten sposób zawierają te same odwołania, co oryginalny diagram warstwowe.|Dodaj nowy diagram warstwowy do projektu modelowania.<br /><br /> Skopiuj elementy ze źródłowego diagramu warstwowego do nowego diagramu.|

## <a name="UnderstandingValidationErrors"></a>Zrozumienie i rozwiązywanie błędów walidacji warstwy
 Podczas walidacji kodu na podstawie diagramu warstwowego błędy walidacji występują, gdy kod jest niezgodny z projektem. Na przykład następujące warunki mogą powodować występowanie błędów walidacji:

- Artefakt jest przypisany do niewłaściwej warstwy. W takim przypadku przenieś artefakt.

- Artefakt, taki jak klasa, używa innej klasy w sposób, który powoduje konflikt z architekturą. W tym przypadku zrefaktoryzuj kod, aby usunąć zależność.

  Aby rozwiązać te błędy, aktualizuj kod, dopóki nie przestaną pojawiać się błędy podczas walidacji. Zadanie to możesz wykonać w sposób iteracyjny.

  W poniższej sekcji opisano składnię, która jest używana w tych błędach, wyjaśniono znaczenie tych błędów i zasugerowano, co można zrobić, aby je rozwiązać lub zarządzać nimi.

|**Składnia**|**Opis**|
|----------------|---------------------|
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* to artefakt, który jest skojarzony z warstwą na diagramie warstwowym.<br /><br /> *ArtifactTypeN* jest typem *ArtifactN*, takim jak **Klasa** lub **Metoda**, na przykład:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Metoda)|
|*NamespaceNameN*|Nazwa przestrzeni nazw.|
|*LayerNameN*|Nazwa warstwy na diagramie warstwowym.|
|*DependencyType*|Typ relacji zależności między *Artifact1* i *Artifact2*. Na przykład *Artifact1* ma związek **wywołań** z *Artifact2*.|

|**Składnia błędu**|**Opis błędu**|
|----------------------|---------------------------|
|AV0001: nieprawidłowa zależność: *Artifact1*(*ArtifactType1*)--> *Artifact2*(*ArtifactType2*)<br /><br /> Warstwy: *LayerName1*, *LayerName2* &#124; zależności: *DependencyType*|*Artifact1* w *LayerName1* nie powinna mieć zależności od *Artifact2* w *LayerName2* , ponieważ *LayerName1* nie ma bezpośredniej zależności od *LayerName2*.|
|AV1001: nieprawidłowa przestrzeń nazw: *artefakt*<br /><br /> Warstwa: *LayerName* &#124; Wymagana przestrzeń nazw: *NamespaceName1* &#124; Current Namespace: *NamespaceName2*|*Warstwaname* wymaga, aby skojarzone artefakty musiały należeć do *NamespaceName1*. *Artefakt* jest w *NamespaceName2*, a nie *NamespaceName1*.|
|AV1002: zależy od niedozwolonej przestrzeni nazw: *Artifact1*(*ArtifactType1*) &#124; *Artifact2*(*ArtifactType2*)<br /><br /> *Warstwa:* &#124; *DependencyType* zabroniony obszar nazw: *NamespaceName* &#124; zależności:|*Warstwaname* wymaga, aby skojarzone artefakty nie zależały od *nazwy przestrzeni nazw*. *Artifact1* nie może zależeć od *Artifact2* , ponieważ *Artifact2* znajduje się w *przestrzeni nazw*.|
|AV1003: w przestrzeni nazw zabroniony: *artefakt*(*artefakttype*)<br /><br /> Warstwa: &#124; niedozwolona przestrzeń nazw w warstwiename: *NamespaceName*|*Warstwaname* wymaga, aby skojarzone artefakty nie należały do *przestrzeni nazwname*. *Artefakt* należy do *przestrzeni nazw*.|
|AV3001: brak linku: warstwa "*LayerName*" łączy się z "*artefaktem*", którego nie można znaleźć. Czy nie brakuje odwołania do zestawu?|W obszarze *LayerName* znajdują się linki do artefaktu, którego nie można znaleźć. Na przykład, może brakować łącza do klasy, ponieważ w projekcie modelowania brakuje odwołania do zestawu, który zawiera klasę.|
|AV9001: Analiza architektoniczna znalazła błędy wewnętrzne. Wyniki mogą być niepełne. Aby uzyskać więcej informacji, zobacz szczegółowy dziennik zdarzeń kompilacji lub okno danych wyjściowych.|Zobacz dziennik zdarzeń kompilacji lub okno danych wyjściowych, aby uzyskać więcej szczegółów.|

## <a name="security"></a>Zabezpieczenia

## <a name="see-also"></a>Zobacz też
 [Weryfikacja systemu w czasie opracowywania](../modeling/validate-your-system-during-development.md)
