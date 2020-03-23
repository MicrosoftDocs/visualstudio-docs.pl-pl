---
title: 'Jak: Zmiana katalogu wyjściowego kompilacji'
ms.date: 05/15/2019
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 37342796f2dd94138136bb837cf6007d19d350c4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114253"
---
# <a name="how-to-change-the-build-output-directory"></a>Jak: Zmiana katalogu wyjściowego kompilacji

Można określić lokalizację danych wyjściowych generowanych przez projekt na podstawie konfiguracji (dla debugowania, wydania lub obu).

## <a name="change-the-build-output-directory"></a>Zmiana katalogu wyjściowego kompilacji

1. Aby otworzyć strony właściwości projektu, kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratorze rozwiązań** i wybierz polecenie **Właściwości**.

2. Wybierz odpowiednią kartę na podstawie typu projektu:

   - W przypadku języka C#wybierz kartę **Kompilacja.**
   - W polu Visual Basic wybierz kartę **Kompilacja.**
   - W przypadku języka C++ lub JavaScript wybierz kartę **Ogólne.**

3. W z listy rozwijanej konfiguracji u góry wybierz konfigurację, której lokalizację pliku wyjściowego chcesz zmienić (**Debug**, **Release**lub **Wszystkie konfiguracje**).

4. Znajdź wpis ścieżki wyjściowej&mdash;na stronie, który różni się w zależności od typu projektu:

   - **Ścieżka wyjściowa** dla projektów w językach C# i JavaScript
   - **Tworzenie ścieżki wyjściowej** dla projektów języka Visual Basic
   - **Katalog danych wyjściowych** dla projektów języka Visual C++

   Wpisz ścieżkę, do których chcesz wygenerować dane wyjściowe (bezwzględne lub względem katalogu projektu głównego) lub wybierz pozycję **Przeglądaj,** aby przejść do tego folderu.

   ![Właściwość ścieżki wyjściowej dla projektu programu Visual Studio C#](media/output-path.png)
   
   > [!NOTE]
   > Niektóre projekty będą domyślnie zawierać struktury i środowiska uruchomieniowego w ścieżce kompilacji. Aby to zmienić, kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratorze rozwiązań**, wybierz pozycję **Edytuj plik projektu**i dodaj następujące elementy:
   > ```xml
   > <PropertyGroup>
   >   <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
   >   <AppendRuntimeIdentifierToOutputPath>false</AppendRuntimeIdentifierToOutputPath>
   > </PropertyGroup>
   > ```

> [!TIP]
> Jeśli dane wyjściowe nie są generowane do określonej lokalizacji, upewnij się, że budujesz odpowiednią konfigurację (na przykład **Debug** lub **Release),** wybierając ją na pasku menu programu Visual Studio.
>
> ![Selektor konfiguracji kompilacji w programie Visual Studio 2019](media/build-configuration-chooser.png)

## <a name="see-also"></a>Zobacz też

- [Strona kompilacji, Projektant projektu (C#)](../ide/reference/build-page-project-designer-csharp.md)
- [Strona Właściwości ogólne (projekt)](/cpp/build/reference/general-property-page-project)
- [Kompilowanie i tworzenie kompilacji](../ide/compiling-and-building-in-visual-studio.md)
