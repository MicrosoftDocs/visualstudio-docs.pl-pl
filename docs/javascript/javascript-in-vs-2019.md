---
title: JavaScript i TypeScript w programie Visual Studio 2019
ms.date: 03/16/2020
ms.technology: vs-javascript
ms.topic: conceptual
dev_langs:
- JavaScript
- TypeScript
- DHTML
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.openlocfilehash: df4630182e89dad08360794057bda856ff4d677b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "79549947"
---
# <a name="javascript-and-typescript-in-visual-studio-2019"></a>JavaScript i TypeScript w programie Visual Studio 2019

## <a name="overview"></a>Omówienie

Visual Studio 2019 zapewnia bogatą obsługę programowania JavaScript, zarówno przy użyciu języka JavaScript bezpośrednio, jak i przy użyciu [języka programowania TypeScript](http://www.typescriptlang.org/), który został opracowany w celu zapewnienia bardziej wydajne i przyjemne środowisko programowania JavaScript, zwłaszcza podczas tworzenia projektów na dużą skalę. Kod JavaScript lub TypeScript można napisać w programie Visual Studio dla wielu typów aplikacji i usług.

## <a name="javascript-language-service"></a>Usługa języka JavaScript

Środowisko JavaScript w programie Visual Studio 2019 jest obsługiwane przez ten sam aparat, który zapewnia obsługę języka TypeScript. Zapewnia to lepszą obsługę funkcji, bogactwo i integrację natychmiast po wyjęciu z pudełka.

Opcja przywrócenia starszej usługi języka JavaScript nie jest już dostępna. Użytkownicy mają teraz nową usługę języka JavaScript out-of-the-box. Nowa usługa językowa jest oparta wyłącznie na usłudze języka TypeScript, która jest obsługiwana przez analizę statyczną. Dzięki temu możemy zapewnić ci lepsze narzędzia, dzięki czemu kod JavaScript może korzystać z bogatsze IntelliSense na podstawie definicji typów. Nowa usługa jest lekka i zużywa mniej pamięci niż starsza usługa, zapewniając lepszą wydajność w miarę skalowania kodu. Poprawiliśmy również wydajność usługi językowej do obsługi większych projektów.

## <a name="typescript-support"></a>Obsługa języka TypeScript

Program Visual Studio 2019 udostępnia kilka opcji integracji kompilacji TypeScript z projektem:

* [Pakiet NuGet typescript](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild). Po zainstalowaniu pakietu NuGet dla języka TypeScript 3.2 lub nowszego w projekcie odpowiednia wersja usługi języka TypeScript zostanie załadowana do edytora.
* [Pakiet TypeScript npm](https://www.npmjs.com/package/typescript). Po zainstalowaniu pakietu npm dla języka TypeScript 2.1 lub nowszego w projekcie odpowiednia wersja usługi języka TypeScript zostanie załadowana do edytora.
* Pakiet SDK typescript, dostępny domyślnie w instalatorze programu Visual Studio, a także samodzielny pakiet SDK pobierany z [portalu VS Marketplace](https://marketplace.visualstudio.com/items?itemName=TypeScriptTeam.typescript-331-vs2017).

W przypadku projektów opracowanych w programie Visual Studio 2019 firma Wezaubienie do używania pakietów TypeScript NuGet i npm w celu zwiększenia przenośności na różnych platformach i środowiskach.

Jednym z typowych zastosowań pakietu NuGet jest skompilowanie języka TypeScript przy użyciu interfejsu wiersza polecenia .NET Core. Jeśli plik projektu nie zostanie ręcznie edytowany w celu zaimportowania obiektów docelowych kompilacji z instalacji zestawu SDK TypeScript, pakiet NuGet jest jedynym sposobem włączenia kompilacji TypeScript przy użyciu poleceń .NET Core CLI, takich jak `dotnet build` i `dotnet publish`.

## <a name="remove-default-imports-aspnet-core-projects"></a>Usuwanie domyślnych importów (ASP.NET projektów podstawowych)

W starszych projektach, które używają [formatu w stylu nienawiązanego do SDK,](https://docs.microsoft.com/nuget/resources/check-project-format)może być konieczne usunięcie niektórych elementów pliku projektu.

Jeśli używasz pakietu NuGet dla obsługi MSBuild dla projektu, `Microsoft.TypeScript.Default.props` plik `Microsoft.TypeScript.targets`projektu nie może importować ani . Pliki są importowane przez pakiet NuGet, więc dołączając je oddzielnie może spowodować niezamierzone zachowanie.

1. Kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zwolnij projekt**.

1. Kliknij prawym przyciskiem myszy projekt i wybierz polecenie ** \<Edytuj *nazwę*\>pliku projektu**.

   Zostanie otwarty plik projektu.

1. Usuń odwołania `Microsoft.TypeScript.Default.props` do `Microsoft.TypeScript.targets`i .

   Importy do usunięcia wyglądają podobnie do następujących:

   ```xml
   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props')" />

   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets')" />
   ```

## <a name="projects"></a>Projekty

Aplikacje JavaScript platformy uniwersalnej systemu Windows nie są już obsługiwane w programie Visual Studio 2019. Nie można tworzyć ani otwierać projektów platformy uniwersalnej systemu JavaScript (plików z rozszerzeniem *.jsproj*). Możesz dowiedzieć się więcej, korzystając z naszej dokumentacji dotyczącej [tworzenia progresywnych aplikacji sieci Web (PWA),](/microsoft-edge/progressive-web-apps/get-started) które działają dobrze w systemie Windows.
