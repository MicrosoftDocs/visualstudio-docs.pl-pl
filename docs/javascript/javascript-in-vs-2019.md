---
title: JavaScript i TypeScript w programie Visual Studio 2019 r.
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
ms.openlocfilehash: 3000510c6bb6079629a3df05909417593569c932
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60077332"
---
# <a name="javascript-and-typescript-in-visual-studio-2019"></a>JavaScript i TypeScript w programie Visual Studio 2019 r.

## <a name="overview"></a>Omówienie

Visual Studio 2019 udostępnia, zaawansowana obsługa programowania języka JavaScript, zarówno bezpośrednio przy użyciu języka JavaScript, a także za pomocą [TypeScript język programowania](http://www.typescriptlang.org), który został opracowany, aby zapewnić JavaScript i bardziej wydajna środowisko programistyczne, szczególnie w przypadku, gdy tworzenie projektów w dużej skali. W przypadku wielu typów aplikacji i usług, można napisać kod JavaScript lub TypeScript w programie Visual Studio.

## <a name="javascript-language-service"></a>Usługa języka JavaScript

Środowisko języka JavaScript w programie Visual Studio 2019 r jest obsługiwana przez tego samego aparatu, który zapewnia obsługę TypeScript. Daje lepszą obsługę funkcji, złożonością i integracji natychmiast out-of--box.

Możliwość przywrócenia starszej wersji usługi językowej JavaScript nie jest już dostępna. Użytkownicy mają teraz nowe JavaScript language usługi out-of box. Nowa usługa języka zależy wyłącznie usługi języka TypeScript, która jest obsługiwana przez analizę statyczną. Pozwala to nam umożliwiają lepsze narzędzia, dzięki czemu kod JavaScript może być korzystne ulepszoną funkcję IntelliSense, na podstawie definicji typu. Nowa usługa ma uproszczoną konstrukcję i zużywa mniej pamięci niż starszej wersji usługi, zapewniając lepszą wydajność w miarę skalowania kodu. Poprawiono również wydajność, aby obsłużyć większe projekty wersję usługi języka.

## <a name="typescript-support"></a>Obsługa TypeScript

Visual Studio 2019 udostępnia kilka rozwiązań integracji kompilacji TypeScript do projektu:

* [Pakiet TypeScript NuGet](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild). Po zainstalowaniu do projektu pakiet NuGet dla TypeScript 3.2 lub nowszej odpowiednią wersję usługi języka TypeScript pobiera załadowany w edytorze.
* TypeScript SDK oferowana domyślnie w Instalatorze programu Visual Studio, a także autonomiczny pakiet zestawu SDK do pobrania z [VS Marketplace](https://marketplace.visualstudio.com/items?itemName=TypeScriptTeam.typescript-331-vs2017).
* [Pakiet npm TypeScript](https://www.npmjs.com/package/typescript). Po zainstalowaniu pakietu npm dla TypeScript 2.1 lub nowszej do projektu odpowiednią wersję usługi języka TypeScript pobiera załadowany w edytorze.

W przypadku projektów opracowane w programie Visual Studio 2019 firma Microsoft zachęca do na użytek pakietów npm i TypeScript NuGet mobilność na różnych platformach i środowisk.

## <a name="projects"></a>Projekty

Aplikacje JavaScript platformy uniwersalnej systemu Windows nie są już obsługiwane w programie Visual Studio 2019. Nie można utworzyć lub otworzyć projekty języka JavaScript platformy uniwersalnej systemu Windows (pliki z rozszerzeniem *.jsproj*). Dowiedz się więcej przy użyciu naszej dokumentacji w [tworzenie aplikacji sieci Web progresywnego (PWAs)](https://docs.microsoft.com/microsoft-edge/progressive-web-apps/get-started) , działają na Windows.
