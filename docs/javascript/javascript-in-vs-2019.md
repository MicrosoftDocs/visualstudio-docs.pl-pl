---
title: JavaScript i TypeScript w programie Visual Studio 2019
ms.date: 03/27/2019
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
ms.openlocfilehash: 3412e1d27a365a6c6302c56ada865f33a436b639
ms.sourcegitcommit: 978df2feb5e64228d2e3dd430b299a5c234cda17
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72888621"
---
# <a name="javascript-and-typescript-in-visual-studio-2019"></a>JavaScript i TypeScript w programie Visual Studio 2019

## <a name="overview"></a>Omówienie

Program Visual Studio 2019 zapewnia rozbudowaną obsługę programowania w języku JavaScript, zarówno przy użyciu języka JavaScript, jak i przy użyciu [języka programowania TypeScript](http://www.typescriptlang.org/), który został opracowany w celu zapewnienia bardziej wydajnego i efektywnego programowania kodu JavaScript środowisko, szczególnie podczas opracowywania projektów na dużą skalę. Można napisać kod JavaScript lub TypeScript w programie Visual Studio dla wielu typów i usług aplikacji.

## <a name="javascript-language-service"></a>Usługa języka JavaScript

Środowisko JavaScript w programie Visual Studio 2019 jest obsługiwane przez ten sam aparat, który zapewnia obsługę języka TypeScript. Zapewnia to lepszą pomoc techniczną, rozbudowaną i integrację.

Opcja przywrócenia starszej wersji usługi językowej JavaScript nie jest już dostępna. Użytkownicy mają teraz nową usługę językową JavaScript. Nowa usługa języka jest oparta wyłącznie na usłudze języka TypeScript, która jest obsługiwana przez analizę statyczną. Dzięki temu możemy zapewnić lepsze narzędzia, dzięki czemu kod JavaScript może korzystać z bogatszej technologii IntelliSense na podstawie definicji typów. Nowa usługa jest lekki i zużywa mniejszą ilość pamięci niż Starsza usługa, co zapewnia lepszą wydajność w miarę skalowania kodu. Ulepszono również wydajność usługi językowej w celu obsługi większych projektów.

## <a name="typescript-support"></a>Obsługa języka TypeScript

Program Visual Studio 2019 udostępnia kilka opcji integracji kompilacji języka TypeScript z projektem:

* [Pakiet NuGet języka TypeScript](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild). Gdy pakiet NuGet dla języka TypeScript 3,2 lub nowszego jest zainstalowany w projekcie, odpowiednia wersja usługi języka TypeScript zostanie załadowana w edytorze.
* TypeScript SDK, dostępna domyślnie w Instalatorze programu Visual Studio, a także do pobrania autonomicznego zestawu SDK z [witryny vs Marketplace](https://marketplace.visualstudio.com/items?itemName=TypeScriptTeam.typescript-331-vs2017).
* [Pakiet TypeScript npm](https://www.npmjs.com/package/typescript). Gdy pakiet npm dla języka TypeScript 2,1 lub nowszego jest instalowany w projekcie, odpowiednia wersja usługi języka TypeScript zostanie załadowana w edytorze.

W przypadku projektów utworzonych w programie Visual Studio 2019 zachęcamy do korzystania z pakietów NuGet i npm języka TypeScript w celu uzyskania większej przenośności na różnych platformach i środowiskach.

## <a name="projects"></a>Projekty

Aplikacje JavaScript platformy uniwersalnej systemu Windows nie są już obsługiwane w programie Visual Studio 2019. Nie można tworzyć ani otwierać projektów platformy UWP JavaScript (pliki z rozszerzeniem *JSProj*). Więcej informacji można znaleźć w naszej dokumentacji dotyczącej [tworzenia progresywnych Web Apps (PWAs)](/microsoft-edge/progressive-web-apps/get-started) , które działają prawidłowo w systemie Windows.
