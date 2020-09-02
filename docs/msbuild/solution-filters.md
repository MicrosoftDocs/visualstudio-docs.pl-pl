---
title: Filtry rozwiązań w programie MSBuild
description: Objaśnia filtry rozwiązań i pokazuje, jak utworzyć plik filtru rozwiązania przy użyciu programu MSBuild.
ms.date: 07/28/2020
ms.topic: reference
helpviewer_keywords:
- MSBuild, solution filters
- solution filters [MSBuild]
author: ghogen
ms.author: ghogen
manager: jillfra
monikerRange: '>= vs-2019'
ms.openlocfilehash: 998103828d20827e8a1d99e0cc34d7f9beb6bd7c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "87401036"
---
# <a name="solution-filters-in-msbuild"></a>Filtry rozwiązań w programie MSBuild

Pliki filtrów rozwiązań to pliki JSON z rozszerzeniem *. slnf* , które wskazują projekty do skompilowania lub załadowania ze wszystkich projektów w rozwiązaniu. Począwszy od programu MSBuild 16,7, można wywołać MSBuild w pliku filtru rozwiązania, aby skompilować rozwiązanie z włączonym filtrowaniem. 

> [!NOTE]
> Plik filtru rozwiązania zmniejsza zestaw projektów, które będą ładowane lub kompilowane i upraszczają format. Plik rozwiązania jest nadal wymagany.

## <a name="build-a-solution-filter-from-the-command-line"></a>Kompiluj filtr rozwiązania z wiersza polecenia

Kompilowanie pliku filtru rozwiązania z wiersza polecenia używa dokładnie tej samej składni co Kompilowanie pliku rozwiązania. Określ plik filtru rozwiązania zamiast rozwiązania do skompilowania z włączonym filtrowaniem w następujący sposób:

```console
msbuild [options] solutionFilterFile.slnf
```

Możesz również dołączać przełączniki i dodatkowe właściwości jako normalne. Zobacz [informacje dotyczące wiersza polecenia programu MSBuild](msbuild-command-line-reference.md). To polecenie kompiluje filtrowane projekty i wszystkie projekty, od których zależą. Podczas kompilowania filtra rozwiązania z wiersza polecenia MSBuild automatycznie następuje zależności. Kompiluje projekt, jeśli jest określony w filtrze lub do którego odwołuje się projekt, który został skompilowany.

## <a name="solution-filter-files"></a>Pliki filtrów rozwiązań

Możesz użyć programu Visual Studio do pracy z plikami filtrów rozwiązań. Otwarcie filtru rozwiązania w programie Visual Studio powoduje wyświetlenie niezaładowanych projektów oraz załadowane projekty i zapewnia opcję ładowania większej liczby projektów w celu wybrania ich do skompilowania. Możliwe jest załadowanie wszystkich projektów, które są zależne od projektu, tylko do kompilacji, ale nie jest to wymagane. Zobacz [filtrowane rozwiązania](../ide/filtered-solutions.md).

Filtr rozwiązania nie musi znajdować się w tym samym folderze co rozwiązanie. Ścieżka do pliku rozwiązania jest określana względem lokalizacji pliku filtru rozwiązania, ale ścieżki do każdego projektu są względne dla samego pliku rozwiązania i powinny być zgodne ze ścieżkami projektu w pliku rozwiązania. W poniższym przykładzie pokazano sposób użycia ścieżek względnych:

```json
{
  "solution": {
    "path": "..\\..\\Documents\\GitHub\\msbuild\\MSBuild.sln",
    "projects": [
      "src\\Build.OM.UnitTests\\Microsoft.Build.Engine.OM.UnitTests.csproj"
    ]
  }
}
```

Ukośniki odwrotne w ścieżkach muszą być podwojone, ponieważ są dla nich zmienione.

## <a name="example"></a>Przykład

Oto przykład odfiltrowanego rozwiązania w programie Visual Studio:

![Zrzut ekranu przefiltrowanego rozwiązania w programie Visual Studio](media/solution-with-filter.png)

W tym rozwiązaniu ClassLibrary1 jest używany przez elementy projects i ProjectB, a więc ClassLibrary1 jest wymieniony jako odwołanie do projektu.

Oto plik filtru rozwiązania generowany przez program Visual Studio:

```json
{
  "solution": {
    "path": "MyApplication.sln",
    "projects": [
      "MyApplication\\MyApplication.csproj",
      "ProjectA\\ProjectA.csproj"
    ]
  }
}
```

W tym przykładzie podczas kompilowania z włączonym filtrowaniem (przy użyciu polecenia `MSBuild [options] MyFilter.slnf` ) MSBuild kompiluje aplikacje i projekt, ponieważ są one jawnie wymienione w pliku filtru rozwiązania. W ramach kompilowania projektu, MSBuild kompiluje ClassLibrary1, ponieważ zależy od niego projekt.  ProjectB nie jest skompilowany. (W tej dyskusji założono czystą kompilację. Jeśli projekty zostały skompilowane wcześniej, zazwyczaj reguły dotyczą pomijania projektów, które są już aktualne.

## <a name="see-also"></a>Zobacz też

- [Rozwiązania filtrowane](../ide/filtered-solutions.md)
- [Dokumentacja wiersza polecenia programu MSBuild](msbuild-command-line-reference.md)
