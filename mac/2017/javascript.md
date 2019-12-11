---
title: JavaScript i TypeScript
description: Informacje na temat pomocy technicznej dotyczącej języka JavaScript w Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: 61432695-5B12-4257-B250-48D37EED106D
ms.openlocfilehash: cc10cd6125dc19571424358fd1ce9de46f7d86c5
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74984902"
---
# <a name="javascript-and-typescript-support"></a>Obsługa języków JavaScript i TypeScript

Visual Studio dla komputerów Mac zapewnia obsługę języków JavaScript i TypeScript za pomocą wyróżniania składni, formatowania kodu i technologii IntelliSense.

![Obsługa edytora TypeScript](https://msdnshared.blob.core.windows.net/media/2018/03/TypeScript-editor.gif)

Aby uzyskać więcej informacji na temat pisania języka JavaScript, zobacz Pisanie przewodników po [kodzie JavaScript](/scripting/javascript/writing-javascript-code) .

## <a name="adding-a-javascript-file"></a>Dodawanie pliku JavaScript

Pliki JavaScript są najczęściej dodawane do ASP.NET Core projektów za pomocą okna dialogowego **nowy plik** . Aby dodać plik JavaScript, kliknij prawym przyciskiem myszy projekt i przejdź do pozycji **dodaj > nowy plik**:

![Dodawanie nowych plików do projektu](media/javascript-image1.png)

W oknie dialogowym **nowy plik** wybierz pozycję **Sieć Web > pusty plik js** lub **plik TypeScript > sieci Web**. Nadaj mu nazwę, a następnie wybierz pozycję **Nowy**:

![Tworzenie nowego pliku TypeScript na podstawie szablonu](media/javascript-image2.png)

## <a name="intellisense"></a>IntelliSense

Visual Studio dla komputerów Mac używa [JavaScript Language Service](/visualstudio/ide/javascript-intellisense) w celu udostępnienia technologii IntelliSense, co umożliwia wykonywanie inteligentnych uzupełniania kodu, informacji o parametrach i list elementów członkowskich podczas pisania kodu.

Technologia JavaScript IntelliSense w Visual Studio dla komputerów Mac może opierać się na wnioskach o typie, JSDoc lub deklaracji języka TypeScript.

- **Wnioskowanie o typie** — typ obiektu jest określany przez otaczający kontekst kodu. Aby uzyskać więcej informacji, zobacz sekcję programu Visual Studio na [technologii IntelliSense na podstawie wnioskowania o typie](/visualstudio/ide/javascript-intellisense#intellisense-based-on-type-inference).
- **JSDoc** — istnieją przypadki, w których wnioskowanie typu nie zapewnia prawidłowych informacji o typie. W takich przypadkach informacje o typie mogą być podawane jawnie przez adnotacje [JSDoc](https://jsdoc.app/about-getting-started.html) . Aby uzyskać więcej informacji, zobacz sekcję dotyczącą technologii IntelliSense w programie Visual Studio na [podstawie JSDoc](/visualstudio/ide/javascript-intellisense#intellisense-based-on-jsdoc)
- **Pliki deklaracji TypeScript** — pliki `.d.ts` są używane do udostępniania wartości JavaScript IntelliSense. Typy zadeklarowane w tym pliku mogą być używane jako typy w komentarzach JSDoc. Aby uzyskać więcej informacji, zobacz sekcję programu Visual Studio na [technologii IntelliSense w oparciu o pliki deklaracji TypeScript](/visualstudio/ide/javascript-intellisense#intellisense-based-on-typescript-declaration-files)

    ![Dodawanie pliku definicji TypeScript](media/javascript-image3.png)

## <a name="see-also"></a>Zobacz także

- [JavaScript IntelliSense (Visual Studio w systemie Windows)](/visualstudio/ide/javascript-intellisense)
