---
title: Korzystanie z Clang-uporządkowanego w programie Visual Studio
ms.date: 10/04/2019
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.clangtidy
author: frozenpandaman
ms.author: efessler
ms.workload:
- cplusplus
ms.openlocfilehash: 430d0e271f83332f7163c9c0c947f96756ca7a7d
ms.sourcegitcommit: e95dd8cedcd180e0bce6a75c86cf861757918290
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2019
ms.locfileid: "72165193"
---
# <a name="using-clang-tidy-in-visual-studio"></a>Korzystanie z Clang-uporządkowanego w programie Visual Studio

Analiza kodu natywnie obsługuje [Clang-uporządkowanego](https://clang.llvm.org/extra/clang-tidy/) dla projektów MSBuild i cmake, niezależnie od tego, czy są używane zestawy narzędzi CLANG czy MSVC. Testy Clang-uporządkowanego mogą być uruchamiane w ramach analizy kodu w tle, wyświetlane jako ostrzeżenia w edytorze (zygzaki) i wyświetlane w Lista błędów.

Aby można było używać Clang-uporządkowanego, składnik "C++ Clang Tools for Windows" musi zostać zainstalowany za pośrednictwem Instalator programu Visual Studio.

Clang-uporządkowanego jest domyślnym narzędziem do analizy przy użyciu zestawu narzędzi LLVM/Clang-CL, dostępnego zarówno w programie MSBuild, jak i w CMake. Można ją skonfigurować do uruchamiania razem lub zastępować standardowe środowisko analizy kodu przy użyciu zestawu narzędzi MSVC; w przypadku korzystania z narzędzia Clang-CL zestaw narzędzi Microsoft Code Analysis nie będzie dostępny.

Clang-uporządkowanego jest uruchamiany po pomyślnej kompilacji; może być konieczne rozwiązanie błędów kodu źródłowego w celu uzyskania wyników Clang-uporządkowanego.


## <a name="msbuild"></a>MSBuild

Można skonfigurować Clang-uporządkowanego do uruchamiania w ramach analizy kodu i kompilacji na stronie**ogólnej** **analizy kodu** >  w okno właściwości projektu. Opcje konfigurowania narzędzia znajdują się w podmenu Clang-uporządkowanego.

Aby uzyskać więcej informacji, zobacz [jak: Ustawianie właściwości analizy kodu dla C/C++ projects @ no__t-1.

## <a name="cmake"></a>Narzędzia CMake

W projektach CMake można skonfigurować kontrole Clang-uporządkowanego w `CMakeSettings.json`. Po otwarciu kliknij pozycję "Edytuj kod JSON" w prawym górnym rogu edytora ustawień projektu CMake. Następujące klucze są rozpoznawane:

- `enableMicrosoftCodeAnalysis`: Włącza analizę kodu firmy Microsoft
- `enableClangTidyCodeAnalysis`: Włącza analizę Clang-uporządkowanego
- `clangTidyChecks`: Konfiguracja Clang-uporządkowanego, określona jako rozdzielana przecinkami lista, tj. czeków, które mają być włączone lub wyłączone.

Jeśli żadna z opcji "Włącz" nie zostanie określona, program Visual Studio wybierze narzędzie do analizy pasujące do używanego zestawu narzędzi platformy.

## <a name="warning-display"></a>Wyświetlanie ostrzeżeń

Uruchomienia Clang-uporządkowanego powodują ostrzeżenia wyświetlane w Lista błędów, a jak w edytorze. Użyj kolumny "Kategoria" w Lista błędów, aby sortować i organizować ostrzeżenia Clang-uporządkowanego. Ostrzeżenia w edytorze można skonfigurować przez przełączenie ustawienia "Wyłącz Zawijanie analizy kodu" w obszarze **narzędzia** > **Opcje**.

## <a name="clang-tidy-configuration"></a>Clang — konfiguracja uporządkowanego

Można skonfigurować sprawdzanie, czy Clang-uporządkowanego działa w programie Visual Studio za pomocą opcji **checks Clang-uporządkowanego** . Dane wejściowe są przekazywane do argumentu **--checks** narzędzia. Każdą następną konfigurację można uwzględnić w plikach Custom **. Clang-uporządkowanego** . Aby uzyskać więcej informacji, zobacz [dokumentację Clang-uporządkowanego w witrynie LLVM.org](https://clang.llvm.org/extra/clang-tidy/) .

## <a name="see-also"></a>Zobacz też

- [Obsługa Clang/LLVM dla projektów MSBuild](https://aka.ms/cpp/clangmsbuild)
- [Obsługa Clang/LLVM dla projektów CMake](https://aka.ms/cpp/clangcmake)
