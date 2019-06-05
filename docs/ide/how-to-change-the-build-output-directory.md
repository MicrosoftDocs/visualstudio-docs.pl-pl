---
title: 'Instrukcje: Zmiana katalogu wyjściowego kompilacji'
ms.date: 05/15/2019
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9dce876b477dfb802b9cf64214af2ca1cec6a4e
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2019
ms.locfileid: "66715356"
---
# <a name="how-to-change-the-build-output-directory"></a>Instrukcje: Zmiana katalogu wyjściowego kompilacji

Można określić lokalizacji dane wyjściowe generowane przez projekt na podstawie — konfiguracja (w przypadku debugowania, wersji lub obu).

## <a name="change-the-build-output-directory"></a>Zmiana katalogu wyjściowego kompilacji

1. Aby otworzyć strony właściwości projektu, kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz **właściwości**.

2. Wybierz odpowiednią kartę, na podstawie od typu projektu:

   - Aby uzyskać C#, wybierz opcję **kompilacji** kartę.
   - Dla języka Visual Basic, wybierz **skompilować** kartę.
   - Aby uzyskać C++ lub JavaScript, wybierz **ogólne** kartę.

3. W konfiguracji listy rozwijanej u góry wybierz konfigurację, której dane wyjściowe chcesz zmienić lokalizację plików (**debugowania**, **wersji**, lub **wszystkie konfiguracje**).

4. Znajdowanie wpisu ścieżka danych wyjściowych na stronie&mdash;różni się w zależności od typu projektu:

   - **Ścieżka wyjściowa** dla C# i projektów języka JavaScript
   - **Kompiluj ścieżkę wyjściową** dla projektów języka Visual Basic
   - **Katalog wyjściowy** wizualizacji C++ projektów

   Wpisz ścieżkę, aby wygenerować dane wyjściowe (bezwzględną lub względną do katalogu głównego projektu), lub wybierz **Przeglądaj** aby przejść do tego folderu, zamiast tego.

   ![Dane wyjściowe właściwości ścieżki dla programu Visual Studio C# projektu](media/output-path.png)

> [!TIP]
> Jeśli nie Trwa generowanie danych wyjściowych do lokalizacji, który określiłeś, upewnij się, w przypadku tworzenia odpowiedniej konfiguracji (na przykład **debugowania** lub **wersji**), wybierając ją na pasku menu Program Visual Studio.
>
> ![Tworzenie konfiguracji selektora w Visual Studio 2019 r.](media/build-configuration-chooser.png)

## <a name="see-also"></a>Zobacz także

- [Strona kompilacji, Projektant projektu (C#)](../ide/reference/build-page-project-designer-csharp.md)
- [Strona właściwości ogólnych (projekt)](/cpp/build/reference/general-property-page-project)
- [Kompilowanie i tworzenie kompilacji](../ide/compiling-and-building-in-visual-studio.md)