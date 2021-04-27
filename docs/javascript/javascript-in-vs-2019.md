---
title: JavaScript i TypeScript w programie Visual Studio 2019
description: Dowiedz się, Visual Studio 2019 r. zapewnia rozbudowaną obsługę programowania w języku JavaScript, zarówno bezpośrednio przy użyciu języka JavaScript, jak i języka programowania TypeScript.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 03/16/2020
ms.technology: vs-javascript
ms.topic: conceptual
dev_langs:
- JavaScript
- TypeScript
- DHTML
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: '>= vs-2019'
ms.openlocfilehash: 267bd8567b60a66bcf9d78c3aef8f02bbc942e0d
ms.sourcegitcommit: e12d6cdaeb37564f05361965db2ec8ad0d4f21ad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2021
ms.locfileid: "108025881"
---
# <a name="javascript-and-typescript-in-visual-studio-2019"></a>JavaScript i TypeScript w programie Visual Studio 2019

## <a name="overview"></a>Omówienie

Program Visual Studio 2019 zapewnia rozbudowaną obsługę programowania w języku JavaScript, zarówno bezpośrednio przy użyciu języka JavaScript, jak i języka programowania [TypeScript,](http://www.typescriptlang.org/)który został opracowany w celu zapewnienia bardziej wydajnego i bardziej wydajnego środowiska programowania w języku JavaScript, szczególnie w przypadku opracowywania projektów na dużą skalę. Kod JavaScript lub TypeScript można pisać w Visual Studio dla wielu typów aplikacji i usług.

## <a name="javascript-language-service"></a>Usługa języka JavaScript

Środowisko języka JavaScript w Visual Studio 2019 r. jest obsługiwane przez ten sam aparat, który zapewnia obsługę języka TypeScript. Zapewnia to lepszą obsługę funkcji, rozbudowę i natychmiastową integrację.

Opcja przywracania do starszej wersji usługi językowej JavaScript nie jest już dostępna. Użytkownicy mają teraz od teraz nową usługę językową JavaScript. Nowa usługa językowa jest oparta wyłącznie na usłudze językowej TypeScript, która jest oparta na analizie statycznej. Dzięki temu możemy zapewnić lepsze narzędzia, dzięki czemu kod JavaScript może korzystać z bardziej rozbudowanych funkcji IntelliSense opartych na definicjach typów. Nowa usługa jest lekki i zużywa mniej pamięci niż starsza usługa, zapewniając lepszą wydajność podczas skalowania kodu. Poprawiliśmy również wydajność usługi językowej w celu obsługi większych projektów.

## <a name="typescript-support"></a>Obsługa języka TypeScript

Visual Studio 2019 udostępnia kilka opcji integracji kompilacji języka TypeScript z projektem:

* Pakiet [NuGet języka TypeScript.](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild) Gdy pakiet NuGet dla języka TypeScript 3.2 lub wyższego zostanie zainstalowany w projekcie, odpowiednia wersja usługi językowej TypeScript zostanie załadowana do edytora.
* Pakiet [npm języka TypeScript.](https://www.npmjs.com/package/typescript) Po zainstalowaniu pakietu npm dla języka TypeScript 2.1 lub wyższego w projekcie odpowiednia wersja usługi językowej TypeScript zostanie załadowana do edytora.
* Plik TypeScript SDK, domyślnie dostępny w instalatorze programu Visual Studio, a także autonomiczny zestaw SDK do pobrania z witryny [VS Marketplace.](https://marketplace.visualstudio.com/items?itemName=TypeScriptTeam.typescript-395)

> [!TIP]
> W przypadku projektów opracowywanych w programie Visual Studio 2019 zachęcamy do korzystania z pakietu NuGet języka TypeScript lub pakietu npm języka TypeScript w celu zwiększenia przenośności na różnych platformach i w różnych środowiskach. Aby uzyskać więcej informacji, zobacz Compile TypeScript code using NuGet (Kompilowanie kodu [TypeScript przy użyciu narzędzia NuGet)](../javascript/compile-typescript-code-nuget.md) i Compile TypeScript code using tsc (Kompilowanie kodu [TypeScript przy użyciu tsc).](../javascript/compile-typescript-code-npm.md)

## <a name="projects"></a>Projekty

Aplikacje JavaScript platformy uniwersalnej systemu Windows nie są już obsługiwane w programie Visual Studio 2019. Nie można tworzyć ani otwierać projektów platformy UWP w języku JavaScript (plików z rozszerzeniem *.jsproj).* Więcej informacji można znaleźć w naszej dokumentacji dotyczącej tworzenia progresywnych [Web Apps (PWA),](/microsoft-edge/progressive-web-apps-chromium) które działają dobrze w systemie Windows.
