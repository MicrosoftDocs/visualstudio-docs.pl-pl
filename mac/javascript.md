---
title: JavaScript i TypeScript
description: Informacje dotyczące obsługi języka JavaScript w programie Visual Studio dla komputerów Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: 61432695-5B12-4257-B250-48D37EED106D
ms.openlocfilehash: d2ce3b3cdbf1a4cf1f19956a7327d73c0bb34b62
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "72807150"
---
# <a name="javascript-and-typescript-support"></a>Obsługa języka JavaScript i TypeScript

Program Visual Studio dla komputerów Mac zapewnia obsługę języka JavaScript i TypeScript za pomocą wyróżniania składni, formatowania kodu i intellisense.

![obsługa edytora maszyn](media/tsjseditor-2019.gif)

Aby uzyskać więcej informacji na temat pisania języka JavaScript, zobacz podręczniki [do pisania kodu JavaScript.](/scripting/javascript/writing-javascript-code)

## <a name="adding-a-javascript-file"></a>Dodawanie pliku JavaScript

Pliki JavaScript są najczęściej dodawane do projektów ASP.NET Core za pośrednictwem okna dialogowego **Nowy plik.** Aby dodać plik javascript, kliknij prawym przyciskiem myszy projekt i przejdź do **dodaj > nowy plik:**

![dodawanie nowych plików do projektu](media/javascript-image1.png)

W oknie dialogowym **Nowy plik** wybierz pozycję Web > **Empty JS file** or Web > **TypeScript .** Nadaj mu nazwę, a następnie wybierz pozycję **Nowy:**

![tworzenie nowego pliku maszynopisu z szablonu](media/javascript-image2.png)

## <a name="intellisense"></a>IntelliSense

Visual Studio dla komputerów Mac używa [usługi języka JavaScript](/visualstudio/ide/javascript-intellisense) w celu zapewnienia intelliSense, co pozwala na inteligentne uzupełnianie kodu, informacje o parametrach i listy członków podczas pisania kodu.

Technologia JavaScript IntelliSense w programie Visual Studio dla komputerów Mac może być oparta na wnioskowanie o typie, deklaracjach JSDoc lub TypeScript.

- **Wnioskowanie o typie** — typ obiektu jest obliczany przez otaczający kontekst kodu. Aby uzyskać więcej informacji, zobacz sekcję programu Visual Studio dotyczącą [programu IntelliSense na podstawie wnioskowania o typie](/visualstudio/ide/javascript-intellisense#intellisense-based-on-type-inference).
- **JSDoc** — istnieją chwile, gdy wnioskowanie o typie nie zapewnia poprawne informacje o typie. W takich przypadkach informacje o typie mogą być dostarczane jawnie przez adnotacje [JSDoc.](https://jsdoc.app/about-getting-started.html) Aby uzyskać więcej informacji, zobacz sekcję programu Visual Studio dotyczącą [technologii IntelliSense na podstawie](/visualstudio/ide/javascript-intellisense#intellisense-based-on-jsdoc)
- **Pliki deklaracji TypeScript** — `.d.ts` pliki są używane do dostarczania wartości dla JavaScript IntelliSense. Typy zadeklarowane w tym pliku mogą być używane jako typy w komentarzach JSDoc. Aby uzyskać więcej informacji, zobacz sekcję programu Visual Studio dotyczącą [programu IntelliSense na podstawie plików deklaracji TypeScript](/visualstudio/ide/javascript-intellisense#intellisense-based-on-typescript-declaration-files)

    ![dodawanie pliku definicji pisma maszynowego](media/javascript-type-intellisense-2019.gif)

## <a name="see-also"></a>Zobacz też

- [JavaScript IntelliSense (Visual Studio w systemie Windows)](/visualstudio/ide/javascript-intellisense)
