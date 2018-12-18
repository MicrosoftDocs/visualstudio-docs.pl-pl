---
title: Jak komunikacja dwukierunkowa rozszerzeń
ms.date: 06/25/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
author: willbrown
ms.author: gregvanl
manager: justinclareburt
ms.workload:
- willbrown
ms.openlocfilehash: 826089f1018bc6156cd49bab3afb19e7bb34a47d
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750735"
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-2017-and-visual-studio-2015"></a>Porady: wykonać rozszerzenia są zgodne z programu Visual Studio 2017 i Visual Studio 2015

Ten dokument wyjaśnia, jak tworzyć projekty rozszerzalności obustronne między Visual Studio 2015 i Visual Studio 2017. Po ukończeniu tego uaktualnienia projektu będzie można otworzyć, kompilacji, zainstalować i uruchomić zarówno w programie Visual Studio 2015 i Visual Studio 2017. Jako odwołanie, niektóre rozszerzenia, które mogą dwustronnej konwersji między Visual Studio 2015 i Visual Studio 2017 można znaleźć w [przykłady rozszerzania zestawu SDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

Jeśli zamierzasz tylko kompilacji w programie Visual Studio 2017, ale mają dane wyjściowe pliku VSIX do uruchamiania w programie Visual Studio 2015 i Visual Studio 2017, odwoływać się do [dokumentu migrace rozszerzenia](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

> [!NOTE]
> Z powodu zmian w programie Visual Studio między wersjami kilka rzeczy, które działały w jednej wersji nie działają w innym. Upewnij się, że w obie wersje są dostępne funkcje, o których próbujesz uzyskać dostęp, lub będzie miał rozszerzenie nieoczekiwane wyniki.

Poniżej przedstawiono zarys czynności, które zostaną wykonane w tym dokumencie, aby obustronnie konwertować VSIX:

1. Zaimportuj poprawną pakietów NuGet.
2. Zaktualizuj Manifest rozszerzenia:
    * Docelowych instalacji
    * Wymagania wstępne
3. Aktualizowanie pliku CSProj:
    * Aktualizacja `<MinimumVisualStudioVersion>`.
    * Dodaj `<VsixType>` właściwości.
    * Dodaj właściwość debugowania `($DevEnvDir)` 3 razy.
    * Dodawanie warunków do importowania narzędzia do kompilacji i elementy docelowe.

4. Tworzenie i testowanie

## <a name="environment-setup"></a>Konfigurowanie środowiska

W tym dokumencie przyjęto założenie, że masz zainstalowane na komputerze następujące:

* Visual Studio 2015 z zainstalowany zestaw SDK programu VS
* Visual Studio 2017 z zainstalowanym obciążeniem rozszerzalności

## <a name="recommended-approach"></a>Zalecanym podejściem

Zdecydowanie zaleca się rozpoczynać tego uaktualnienia programu Visual Studio 2015, zamiast programu Visual Studio 2017. Główną zaletą tworzenia w programie Visual Studio 2015 jest zapewnienie, że użytkownik nie odwołują się do zestawów, które nie są dostępne w programie Visual Studio 2015. Jeśli to zrobisz, Programowanie w programie Visual Studio 2017, istnieje ryzyko, że może powodować zależność od zestawu, który istnieje tylko w programie Visual Studio 2017.

## <a name="ensure-there-is-no-reference-to-projectjson"></a>Upewnij się, że nie ma żadnego odwołania do pliku project.json

W dalszej części tego dokumentu, firma Microsoft powoduje wstawienie instrukcje warunkowe importu w do Twojej **.csproj* pliku.  To nie będzie działać, jeśli odwołaniami NuGet są przechowywane w *project.json*. Jako takie, zalecane jest aby przenieść wszystkie odwołania NuGet do *packages.config* pliku.
Jeśli projekt zawiera *project.json* pliku:

* Zanotuj odwołania w *project.json*.
* Z **Eksploratora rozwiązań**, Usuń *project.json* pliku z projektem. Spowoduje to usunięcie *project.json* plików i usuwa go z projektu.
* Dodaj odwołania do NuGet z powrotem w do projektu:
    * Kliknij prawym przyciskiem myszy **rozwiązania** i wybierz polecenie **Zarządzaj pakietami NuGet dla rozwiązania**.
    * Program Visual Studio automatycznie tworzy *packages.config* plik.

> [!NOTE]
> Jeśli projekt zawiera pakiety EnvDTE, ich może być konieczne do dodania, klikając prawym przyciskiem myszy **odwołania** wybierając **Dodaj odwołanie do** oraz dodawania odpowiednich odwołań.  Za pomocą pakietów NuGet może tworzyć błędy podczas próby utworzenia Twojego projektu.

## <a name="add-appropriate-build-tools"></a>Dodaj odpowiednie narzędzia

Musimy mieć pewność, że dodawanie narzędzi do kompilacji, które pozwolą nam na kompilowanie i debugowanie odpowiednio. Firma Microsoft opracowała zestawu dla tego Microsoft.VisualStudio.Sdk.BuildTasks o nazwie.

Aby skompilować i wdrożyć VSIXv3 zarówno w programie Visual Studio 2015 i 2017, potrzebne będą następujące pakiety NuGet:

Wersja | Wbudowanego narzędzia
--- | ---
Visual Studio 2015 | Microsoft.VisualStudio.Sdk.BuildTasks.14.0
Visual Studio 2017 | Microsoft.VSSDK.BuildTool

Aby to zrobić:

* Dodaj pakiet NuGet Microsoft.VisualStudio.Sdk.BuildTasks.14.0 do projektu.
* Jeśli projekt nie zawiera Microsoft.VSSDK.BuildTools, należy go dodać.
* Upewnij się, wersja narzędzi Microsoft.VSSDK.BuildTools 15.x lub nowszej.

## <a name="update-extension-manifest"></a>Aktualizuj manifest rozszerzenia

### <a name="1-installation-targets"></a>1. Elementy docelowe instalacji

Dlatego trzeba poinformować programu Visual Studio, jakie wersje docelowe dla tworzenia VSIX.  Zazwyczaj te odwołania są albo w wersji 14.0 (Visual Studio 2015) lub w wersji 15.0 (Visual Studio 2017).  W tym przypadku chcemy tworzyć VSIX, na którym zostanie zainstalowane rozszerzenie w obu przypadkach, więc potrzebujemy pod kątem obie wersje.  Jeśli chcesz, aby Twoje VSIX, aby skompilować i zainstalować w wersjach wcześniejszych niż 14.0, można to zrobić, ustawiając wcześniej numer wersji; Jednak w wersji 10.0 i wcześniejszych nie są już obsługiwane.

* Otwórz *source.extension.vsixmanifest* pliku w programie Visual Studio.
* Otwórz **Instaluj obiekty docelowe** kartę.
* Zmiana **zakres wersji** do [14,0, 16,0).  "[" Informuje program Visual Studio obejmują wersje 14,0 i wszystkie wcześniejsze go.  ")" Informuje programu Visual Studio, aby uwzględnić wszystkie wersje 15.0 do, z wyjątkiem wersji 16.0.
* Zapisz wszystkie zmiany i zamknij wszystkie wystąpienia programu Visual Studio.

![Obraz przedstawiający elementy docelowe instalacji](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2. Wymagania wstępne dotyczące dodawania *extension.vsixmanifest* pliku

Wymagania wstępne to nowa funkcja w programie Visual Studio 2017.  W tym przypadku potrzebujemy Edytor rdzeni programu Visual Studio jako warunek wstępny. Ponieważ Projektant Visual Studio 2015 VSIX nie obsługuje nowy `Prerequisites` sekcji, należy edytować tej części ręcznie w kodzie XML.  Alternatywnie można otworzyć programu Visual Studio 2017 i użyj zaktualizowany manifest designer, aby wstawić wymagania wstępne.

Aby to zrobić ręcznie:

* Przejdź do katalogu projektu w Eksploratorze plików.
* Otwórz *extension.vsixmanifest* plików za pomocą edytora tekstów.
* Dodaj następujący tag:

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* Zapisz i zamknij plik.

> [!NOTE]
> Jeśli postanowisz to zrobić za pomocą projektanta VSIX w programie Visual Studio 2017, należy ręcznie zmodyfikować wymagana wstępnie wersja, aby upewnić się, że jest zgodny ze wszystkimi wersjami programu Visual Studio 2017.  Jest to spowodowane projektanta wstawi minimalnej wersji jako bieżącej wersji programu Visual Studio (na przykład 15.0.26208.0).  Jednak ponieważ inni użytkownicy mogą mieć starszej wersji, należy ręcznie edytować to ustawienie na 15.0.

W tym momencie pliku manifestu powinien wyglądać mniej więcej tak:

![Przykładowe wymagania wstępne](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>Zmodyfikuj plik projektu (myproject.csproj)

Zdecydowanie zaleca się odwołania do zmodyfikowanych plików csproj otwarty podczas wykonywania tego kroku.  Kilka przykładów można znaleźć [tutaj](https://github.com/Microsoft/VSSDK-Extensibility-Samples).  Wybierz którejkolwiek z próbek rozszerzalności, Znajdź *.csproj* pliku dla odwołania i wykonaj następujące czynności:

* Przejdź do katalogu projektu w **Eksploratora plików**.
* Otwórz *myproject.csproj* plików za pomocą edytora tekstów.

### <a name="1-update-the-minimumvisualstudioversion"></a>1. Aktualizacja MinimumVisualStudioVersion

* Ustaw wersję minimalną visual studio `$(VisualStudioVersion)` i Dodaj instrukcję warunkową dla niego.  Dodaj znaczniki, jeśli nie istnieją.  Upewnij się, że tagi są ustawione, tak jak pokazano poniżej:

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2. Dodaj właściwość VsixType.

* Dodaj następujący tag `<VsixType>v3</VsixType>` do grupy właściwości.

> [!NOTE]
> Zaleca się dodawania tego poniżej `<OutputType></OutputType>` tagu.

### <a name="3-add-the-debugging-properties"></a>3. Dodawanie właściwości debugowania

* Dodaj następujące grupy właściwości:

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartPrograms>$(DevEnvDir)devenv.exe</StartPrograms>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* Usuń wszystkie wystąpienia w poniższym przykładzie kodu z *.csproj* pliku i dowolny *. csproj.user* plików:

```xml
<StartAction>Program</StartAction>
<StartPrograms>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartPrograms>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4. Dodawanie warunków do przywozu narzędzia kompilacji

* Dodaj dodatkowe instrukcje warunkowe, aby `<import>` znaczniki, które mają odwołania Microsoft.VSSDK.BuildTools.  Wstaw `'$(VisualStudioVersion)' != '14.0' And` na wierzchu instrukcja warunku.  Te instrukcje będą wyświetlane w nagłówku i stopce pliku csproj jest niewielki.

Na przykład:

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201…" Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…" />
```

* Dodaj dodatkowe instrukcje warunkowe, aby `<import>` znaczniki, które mają Microsoft.VisualStudio.Sdk.BuildTasks.14.0. Wstaw `'$(VisualStudioVersion)' == '14.0' And` na wierzchu instrukcja warunku. Te instrukcje będą wyświetlane w nagłówku i stopce pliku csproj jest niewielki.

Na przykład:

```xml
<Import Project="packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…" />
```

* Dodaj dodatkowe instrukcje warunkowe, aby `<Error>` znaczniki, które mają odwołania Microsoft.VSSDK.BuildTools.  To zrobić, wstawiając `'$(VisualStudioVersion)' != '14.0' And` na wierzchu instrukcja warunku. Te instrukcje będą wyświetlane w stopce pliku csproj jest niewielki.

Na przykład:

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…" />
```

* Dodaj dodatkowe instrukcje warunkowe, aby `<Error>` znaczniki, które mają Microsoft.VisualStudio.Sdk.BuildTasks.14.0.  Wstaw `'$(VisualStudioVersion)' == '14.0' And` na wierzchu instrukcja warunku. Te instrukcje będą wyświetlane w stopce pliku csproj jest niewielki.

Na przykład:

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" />
```

* Zapisz plik csproj i zamknij go.

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2017"></a>Testowanie instalacji rozszerzenia w Visual Studio 2015 i Visual Studio 2017

Na tym etapie projektu powinny być gotowe do kompilowania VSIXv3, który można zainstalować na programie Visual Studio 2015 i Visual Studio 2017.

* Otwórz swój projekt w programie Visual Studio 2015.
* Skompiluj projekt i upewnij się, w danych wyjściowych, który VSIX poprawnie się kompiluje.
* Przejdź do katalogu projektu.
* Otwórz *\bin\Debug* folderu.
* Kliknij dwukrotnie plik VSIX i zainstalować rozszerzenie programu Visual Studio 2015 i Visual Studio 2017.
* Upewnij się, czy widzisz rozszerzenia w **narzędzia** > **rozszerzenia i aktualizacje** w **zainstalowane** sekcji.
* Próba uruchomienia lub używać rozszerzenia Aby sprawdzić, czy działa.

![Znajdź VSIX](media/finding-a-VSIX-example.png)

> [!NOTE]
> Jeśli projekt zawiesza się z komunikatem **otwierania pliku**, wymuszanie zamknięcia programu Visual Studio, przejdź do katalogu projektu, Pokaż ukryte foldery i Usuń *.vs* folderu.