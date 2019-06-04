---
title: JavaScript i TypeScript
description: Informacje na temat obsługi języka JavaScript w programie Visual Studio dla komputerów Mac
author: conceptdev
ms.author: crdun
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 61432695-5B12-4257-B250-48D37EED106D
ms.openlocfilehash: 82f3426cbba06a27f2d2f74fdd167f003ebb3eae
ms.sourcegitcommit: aeb1a1135dd789551e15aa5124099a5fe3f0f32b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66501087"
---
# <a name="javascript-and-typescript-support"></a>Obsługa języków JavaScript i TypeScript

Program Visual Studio for Mac zapewnia obsługę dla języków JavaScript i TypeScript za pośrednictwem wyróżniania składni, formatowanie kodu i technologii IntelliSense.

![Pomoc techniczna do edytora języka typescript](https://msdnshared.blob.core.windows.net/media/2018/03/TypeScript-editor.gif)

Aby uzyskać więcej informacji na temat pisania kodu JavaScript, zobacz Aby [pisanie kodu JavaScript](/scripting/javascript/writing-javascript-code) przewodników.

## <a name="adding-a-javascript-file"></a>Dodawanie pliku JavaScript

Pliki JavaScript w większości przypadków są dodawane do projektów ASP.NET Core za pomocą **nowy plik** okna dialogowego. Aby dodać plik języka javascript, kliknij prawym przyciskiem myszy nad projektem i przejdź do **Dodaj > Nowy plik**:

![dodanie nowych plików do projektu](media/javascript-image1.png)

Z **nowy plik** okno dialogowe, wybierz opcję **Web > plik JS pusty** lub **sieci Web > plik TypeScript**. Nadaj jej nazwę, a następnie wybierz **New**:

![utworzenie nowego pliku typescript na podstawie szablonu](media/javascript-image2.png)

## <a name="intellisense"></a>IntelliSense

Program Visual Studio for Mac używa [usługę językową JavaScript](/visualstudio/ide/javascript-intellisense) dostarczyć IntelliSense, co pozwala mieć inteligentnego uzupełniania kodu, informacje o parametrach i listy elementów członkowskich, podczas pisania kodu.

Funkcja intellisense języka JavaScript w programie Visual Studio dla komputerów Mac może bazować na wnioskowanie o typie, JSDoc lub TypeScript deklaracji.

- **Wnioskowanie o typie** — typ obiektu jest wybierana przez otaczającego kontekst kodu. Aby uzyskać więcej informacji, zobacz sekcję programu Visual Studio na [IntelliSense oparte na wnioskowanie o typie](/visualstudio/ide/javascript-intellisense#intellisense-based-on-type-inference).
- **Element JSDoc** — istnieją momenty, gdy wnioskowanie o typie nie udostępnia informacji poprawnego typu. W takich przypadkach informacje o typie można podać jawnie przez [JSDoc](https://jsdoc.app/about-getting-started.html) adnotacji. Aby uzyskać więcej informacji, zobacz sekcję programu Visual Studio na [IntelliSense oparte na danych JSDoc](/visualstudio/ide/javascript-intellisense#intellisense-based-on-jsdoc)
- **Pliki deklaracji TypeScript** — `.d.ts` pliki są używane do przekazania wartości do JavaScript IntelliSense. Typy zadeklarowane w tym pliku może służyć jako typy na komentarzy JSDoc. Aby uzyskać więcej informacji, zobacz sekcję programu Visual Studio na [funkcji IntelliSense na podstawie TypeScript deklaracji plików](/visualstudio/ide/javascript-intellisense#intellisense-based-on-typescript-declaration-files)

    ![Dodawanie plików definicji typescript](media/javascript-image3.png)

## <a name="see-also"></a>Zobacz także

- [Technologia JavaScript IntelliSense (Visual Studio Windows)](/visualstudio/ide/javascript-intellisense)
