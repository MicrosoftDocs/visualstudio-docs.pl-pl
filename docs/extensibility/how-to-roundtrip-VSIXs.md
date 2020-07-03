---
title: Jak przełączać się do obu rozszerzeń
ms.date: 06/25/2017
ms.topic: how-to
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
author: willbrown
ms.author: madsk
manager: justinclareburt
ms.workload:
- willbrown
ms.openlocfilehash: ff2865080b7d36f1a7c3b8a7680d867b92ec9c08
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905784"
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-20192017-and-visual-studio-2015"></a>Instrukcje: Udostępnianie rozszerzeń dla programu Visual Studio 2019/2017 i Visual Studio 2015

W tym dokumencie wyjaśniono, jak przeprowadzić rundę projektów rozszerzalności między programem Visual Studio 2015 i programem Visual Studio 2019 lub Visual Studio 2017. Po zakończeniu tego uaktualnienia projekt będzie mógł otwierać, kompilować, instalować i uruchamiać programy Visual Studio 2015 i Visual Studio 2019 lub 2017. Jako odwołanie, Niektóre rozszerzenia, które mogą być rundy, między programami Visual Studio 2015 i Visual Studio 2019 lub 2017, można znaleźć w przykładach [rozszerzalności SDK programu vs](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

Jeśli planujesz kompilację tylko w programie Visual Studio 2019/2017, ale chcesz, aby plik wyjściowy VSIX działał zarówno w programie Visual Studio 2015, jak i w programie Visual Studio 2019/2017, zapoznaj się z [dokumentem migracja rozszerzenia](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

> [!NOTE]
> Ze względu na zmiany w programie Visual Studio między wersjami niektóre elementy, które działały w jednej wersji, nie działają w innej. Upewnij się, że funkcje, do których próbujesz uzyskać dostęp, są dostępne w obu wersjach lub rozszerzenie będzie miało nieoczekiwane wyniki.

Poniżej przedstawiono zarys kroków, które należy wykonać w tym dokumencie w celu przeprowadzenia rundy VSIX:

1. Zaimportuj poprawne pakiety NuGet.
2. Aktualizuj manifest rozszerzenia:
    * Miejsce docelowe instalacji
    * Wymagania wstępne
3. CSProj aktualizacji:
    * Aktualizacja `<MinimumVisualStudioVersion>` .
    * Dodaj `<VsixType>` Właściwość.
    * Dodaj właściwość debugowania `($DevEnvDir)` 3 razy.
    * Dodaj warunki do importowania narzędzi kompilacji i elementów docelowych.

4. Kompiluj i Testuj

## <a name="environment-setup"></a>Konfigurowanie środowiska

W tym dokumencie przyjęto założenie, że na maszynie zainstalowano następujące elementy:

* Program Visual Studio 2015 z zainstalowanym zestawem SDK programu VS
* Program Visual Studio 2019 lub 2017 z zainstalowanym obciążeniem rozszerzalności

## <a name="recommended-approach"></a>Zalecane podejście

Zdecydowanie zaleca się uruchomienie tego uaktualnienia z programem Visual Studio 2015 zamiast programu Visual Studio 2019 lub 2017. Główną zaletą programowania w programie Visual Studio 2015 jest upewnienie się, że nie odwołują się do zestawów, które nie są dostępne w programie Visual Studio 2015. W przypadku tworzenia aplikacji w programie Visual Studio 2019 lub 2017 istnieje ryzyko, że możesz wprowadzić zależność od zestawu, który istnieje tylko w programie Visual Studio 2019 lub 2017.

## <a name="ensure-there-is-no-reference-to-projectjson"></a>Upewnij się, że nie ma odwołań do project.jsna

W dalszej części tego dokumentu dodamy instrukcje importu warunkowego do pliku **. csproj* . Ta operacja nie będzie działała, jeśli odwołania NuGet są przechowywane w *project.jsna*. W związku z tym zaleca się przeniesienie wszystkich odwołań NuGet do pliku *packages.config* .
Jeśli projekt zawiera *project.jsw* pliku:

* Zanotuj odwołania w *project.js*.
* Z **Eksplorator rozwiązań**Usuń *project.jsna* pliku z projektu. Spowoduje to usunięcie *project.js* pliku i usunięcie go z projektu.
* Dodaj odwołania NuGet z powrotem do projektu:
  * Kliknij prawym przyciskiem myszy **rozwiązanie** i wybierz polecenie **Zarządzaj pakietami NuGet dla rozwiązania**.
  * Program Visual Studio automatycznie tworzy plik *packages.config* .

> [!NOTE]
> Jeśli projekt zawiera pakiety EnvDTE, mogą one być dodawane przez kliknięcie prawym przyciskiem myszy na **odwołaniach** , wybierając pozycję **Dodaj odwołanie** i dodając odpowiednie odwołanie. Użycie pakietów NuGet może spowodować błędy podczas próby skompilowania projektu.

## <a name="add-appropriate-build-tools"></a>Dodaj odpowiednie narzędzia do kompilacji

Musimy koniecznie dodać narzędzia do kompilacji, które pozwolą nam odpowiednio kompilować i debugować. Firma Microsoft utworzyła zestaw o nazwie Microsoft. VisualStudio. Sdk. BuildTasks.

Do kompilowania i wdrażania nowego vsixv3 w programie Visual Studio 2015 i 2019/2017 wymagane są następujące pakiety NuGet:

Wersja | Narzędzia skompilowane
--- | ---
Visual Studio 2015 | Microsoft. VisualStudio. Sdk. BuildTasks. 14.0
Visual Studio 2019 lub 2017 | Microsoft. VSSDK. BuildTool

W tym celu:

* Dodaj pakiet NuGet Microsoft. VisualStudio. Sdk. BuildTasks. 14.0 do projektu.
* Jeśli projekt nie zawiera Microsoft. VSSDK. BuildTools, Dodaj go.
* Upewnij się, że wersja Microsoft. VSSDK. BuildTools ma wartość 15. x lub nowszą.

## <a name="update-extension-manifest"></a>Aktualizuj manifest rozszerzenia

### <a name="1-installation-targets"></a>1. cele instalacji

Musimy poinformować program Visual Studio, które wersje mają być przeznaczone do tworzenia VSIX. Zwykle te odwołania są w wersji 14,0 (Visual Studio 2015), w wersji 15,0 (Visual Studio 2017) lub w wersji 16,0 (Visual Studio 2019). W naszym przypadku chcemy skompilować VSIX, który zainstaluje rozszerzenie dla obu, dlatego musimy kierować obie wersje. Jeśli chcesz, aby Twój VSIX został skompilowany i zainstalowany w wersji wcześniejszej niż 14,0, można to zrobić, ustawiając wcześniejszy numer wersji. jednak wersja 10,0 i wcześniejsze nie są już obsługiwane.

* Otwórz plik *source. Extension. vsixmanifest* w programie Visual Studio.
* Otwórz kartę **Zainstaluj obiekty docelowe** .
* Zmień **zakres wersji** na [14,0, 17,0). Element "[" informuje program Visual Studio, aby zawierał 14,0 i wszystkie wersje, które przeszły. ")" Informuje program Visual Studio, aby dołączył wszystkie wersje do, ale nie z uwzględnieniem wersji 17,0.
* Zapisz wszystkie zmiany i Zamknij wszystkie wystąpienia programu Visual Studio.

![Obraz docelowy instalacji](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2. dodanie wstępnie wymaganego pliku *rozszerzenia. vsixmanifest*

Wymagany jest Edytor podstawowy programu Visual Studio jako warunek wstępny. Otwórz program Visual Studio i użyj zaktualizowanego projektanta manifestu, aby wstawić wymagania wstępne.

Aby to zrobić ręcznie:

* Przejdź do katalogu projektu w Eksploratorze plików.
* Otwórz plik *Extension. vsixmanifest* z edytorem tekstu.
* Dodaj następujący Tag:

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* Zapisz i zamknij plik.

> [!NOTE]
> Może być konieczne ręczne edytowanie wstępnie wymaganej wersji, aby upewnić się, że jest ona zgodna ze wszystkimi wersjami programu Visual Studio 2019 lub 2017. Wynika to z faktu, że projektant wstawi wersję minimalną jako bieżącą wersję programu Visual Studio (na przykład 15.0.26208.0). Jednak ponieważ inni użytkownicy mogą mieć wcześniejszą wersję, warto ręcznie edytować ją w 15,0.

W tym momencie plik manifestu powinien wyglądać następująco:

![Przykład wymagań wstępnych](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>Modyfikuj plik projektu (csproj)

Zdecydowanie zaleca się, aby w ramach tego kroku było otwarte odwołanie do zmodyfikowanego elementu. csproj. Kilka przykładów można znaleźć [tutaj](https://github.com/Microsoft/VSSDK-Extensibility-Samples). Wybierz dowolny przykład rozszerzalności, Znajdź plik *. csproj* na potrzeby odwołania i wykonaj następujące czynności:

* Przejdź do katalogu projektu w **Eksploratorze plików**.
* Otwórz plik *Project. csproj* za pomocą edytora tekstów.

### <a name="1-update-the-minimumvisualstudioversion"></a>1. Zaktualizuj MinimumVisualStudioVersion

* Ustaw minimalną wersję programu Visual Studio `$(VisualStudioVersion)` , aby dodać do niej instrukcję warunkową. Dodaj te Tagi, jeśli nie istnieją. Upewnij się, że znaczniki są ustawione w następujący sposób:

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2. Dodaj właściwość Vsixtype.

* Dodaj następujący tag `<VsixType>v3</VsixType>` do grupy właściwości.

> [!NOTE]
> Zaleca się dodanie tego `<OutputType></OutputType>` tagu poniżej znacznika.

### <a name="3-add-the-debugging-properties"></a>3. Dodaj właściwości debugowania

* Dodaj następującą grupę właściwości:

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartProgram>$(DevEnvDir)devenv.exe</StartProgram>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* Usuń wszystkie wystąpienia następującego przykładowego kodu z pliku *. csproj* i dowolnych plików *. csproj. User* :

```xml
<StartAction>Program</StartAction>
<StartProgram>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartProgram>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4. Dodaj warunki do importowanych narzędzi kompilacji

* Dodaj dodatkowe instrukcje warunkowe do `<import>` tagów, które mają odwołanie Microsoft. VSSDK. BuildTools. Wstaw `'$(VisualStudioVersion)' != '14.0' And` na początku instrukcji Condition. Te instrukcje pojawią się w nagłówku i stopce pliku csproj.

Przykład:

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201…" Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…" />
```

* Dodaj dodatkowe instrukcje warunkowe do `<import>` tagów, które mają element Microsoft. VisualStudio. Sdk. BuildTasks. 14.0. Wstaw `'$(VisualStudioVersion)' == '14.0' And` na początku instrukcji Condition. Te instrukcje pojawią się w nagłówku i stopce pliku csproj.

Przykład:

```xml
<Import Project="packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…" />
```

* Dodaj dodatkowe instrukcje warunkowe do `<Error>` tagów, które mają odwołanie Microsoft. VSSDK. BuildTools. Zrób to, wstawiając `'$(VisualStudioVersion)' != '14.0' And` na początku instrukcji Condition. Te instrukcje pojawią się w stopce pliku csproj.

Przykład:

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…" />
```

* Dodaj dodatkowe instrukcje warunkowe do `<Error>` tagów, które mają element Microsoft. VisualStudio. Sdk. BuildTasks. 14.0. Wstaw `'$(VisualStudioVersion)' == '14.0' And` na początku instrukcji Condition. Te instrukcje pojawią się w stopce pliku csproj.

Przykład:

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" />
```

* Zapisz plik CSPROJ i zamknij go. 
  * Należy pamiętać, że jeśli używasz więcej niż jednego projektu w rozwiązaniu, ustaw ten projekt jako projekt startowy za pomocą polecenia "Ustaw jako projekt startowy" w menu kontekstowym projektu. Gwarantuje to, że program Visual Studio ponownie otworzy ten projekt po jego zwolnieniu.

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2019-or-2017"></a>Testowanie instalacji rozszerzeń w programie Visual Studio 2015 i Visual Studio 2019 lub 2017

W tym momencie projekt powinien być gotowy do kompilowania nowego vsixv3, który można zainstalować zarówno w programie Visual Studio 2015, jak i w programie Visual Studio 2017.

* Otwórz projekt w programie Visual Studio 2015.
* Skompiluj projekt i Potwierdź w danych wyjściowych, że VSIX kompiluje się poprawnie.
* Przejdź do katalogu projektu.
* Otwórz folder *\bin\debug* .
* Kliknij dwukrotnie plik VSIX i zainstaluj swoje rozszerzenie w programie Visual Studio 2015 i Visual Studio 2019/2017.
* Upewnij się, że rozszerzenie znajduje się w sekcji **Narzędzia**  >  **rozszerzenia i aktualizacje** w **zainstalowanej** części.
* Spróbuj uruchomić lub użyć rozszerzenia, aby sprawdzić, czy działa.

![Znajdź VSIX](media/finding-a-VSIX-example.png)

> [!NOTE]
> Jeśli projekt zawiesza się z komunikatem **otwierającym plik**, Wymuś wyłączenie programu Visual Studio, przejdź do katalogu projektu, Pokaż ukryte foldery i Usuń folder *. vs* .
 
