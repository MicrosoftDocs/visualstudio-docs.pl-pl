---
title: JavaScript i TypeScript
description: Informacje na temat obsługi języka JavaScript w programie Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: 61432695-5B12-4257-B250-48D37EED106D
ms.openlocfilehash: 5f1a400506f7766ba22ffbc1debde687b1709a21
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760929"
---
# <a name="javascript-and-typescript-support"></a>Obsługa języków JavaScript i TypeScript

Visual Studio dla komputerów Mac zapewnia obsługę języków JavaScript i TypeScript dzięki wyróżnianiu składni, formatowaniu kodu i funkcji IntelliSense.

![Obsługa edytora języka typescript](/visualstudio/mac/media/tsjseditor-2019.gif)

Aby uzyskać więcej informacji na temat pisania kodu JavaScript, zobacz [Przewodniki dotyczące pisania kodu JavaScript.](/scripting/javascript/writing-javascript-code)

## <a name="adding-a-javascript-file"></a>Dodawanie pliku JavaScript

Pliki JavaScript są najczęściej dodawane do ASP.NET Core za pośrednictwem okna **dialogowego Nowy** plik. Aby dodać plik JavaScript, kliknij prawym przyciskiem myszy projekt i przejdź do > **Nowy plik:**

![dodawanie nowych plików do projektu](media/javascript-image1.png)

W **oknie dialogowym New File (Nowy** plik) wybierz pozycję Web > Empty JS file (Pusty plik **JS)** lub Web > TypeScript file (Plik **TypeScript).** Nadaj mu nazwę, a następnie wybierz pozycję **Nowy:**

![Tworzenie nowego pliku typescript na podstawie szablonu](media/javascript-image2.png)

## <a name="intellisense"></a>IntelliSense

Visual Studio dla komputerów Mac używa narzędzia [JavaScript Language Service](/visualstudio/ide/javascript-intellisense) do zapewnienia funkcji IntelliSense, co umożliwia inteligentne uzupełnianie kodu, informacje o parametrach i listy członkowskie podczas pisania kodu.

Funkcja IntelliSense języka JavaScript w Visual Studio dla komputerów Mac może być oparta na wnioskowania o typie, deklaracji JSDoc lub TypeScript.

- **Wnioskowanie o typie** — typ obiektu jest rozsyłany przez otaczający kontekst kodu. Aby uzyskać więcej informacji, zobacz sekcję Visual Studio na temat [funkcji IntelliSense opartej na wnioskowania o typie](/visualstudio/ide/javascript-intellisense#intellisense-based-on-type-inference).
- **JSDoc** — czasami wnioskowanie o typie nie zawiera prawidłowych informacji o typie. W takich przypadkach informacje o typie mogą być udostępniane jawnie przez adnotacje [JSDoc.](https://jsdoc.app/about-getting-started.html) Aby uzyskać więcej informacji, zobacz sekcję Visual Studio na temat [funkcji IntelliSense opartej na pliku JSDoc](/visualstudio/ide/javascript-intellisense#intellisense-based-on-jsdoc)
- **Pliki deklaracji TypeScript** `.d.ts` — pliki są używane do podania wartości dla funkcji IntelliSense języka JavaScript. Typy zadeklarowane w tym pliku mogą być używane jako typy w komentarzach JSDoc. Aby uzyskać więcej informacji, zobacz sekcję Visual Studio na temat [funkcji IntelliSense opartej na plikach deklaracji języka TypeScript](/visualstudio/ide/javascript-intellisense#intellisense-based-on-typescript-declaration-files)

    ![dodawanie pliku definicji typescript](media/javascript-image3.png)

## <a name="see-also"></a>Zobacz też

- [JavaScript IntelliSense (Visual Studio w systemie Windows)](/visualstudio/ide/javascript-intellisense)
