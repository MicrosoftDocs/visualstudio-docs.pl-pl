---
title: 'Instrukcje: zmiana katalogu wyjściowego kompilacji'
ms.date: 05/15/2019
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e4c2f2445bc7139c5bbc80a35905e24c319c9dfa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85284649"
---
# <a name="how-to-change-the-build-output-directory"></a>Instrukcje: zmiana katalogu wyjściowego kompilacji

Możesz określić lokalizację danych wyjściowych generowanych przez projekt na podstawie konfiguracji (na potrzeby debugowania, wydania lub obu).

## <a name="change-the-build-output-directory"></a>Zmiana katalogu wyjściowego kompilacji

1. Aby otworzyć strony właściwości projektu, kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**.

2. Wybierz odpowiednią kartę w zależności od typu projektu:

   - W języku C# wybierz kartę **kompilacja** .
   - W obszarze Visual Basic wybierz kartę **kompilacja** .
   - W przypadku języka C++ lub JavaScript wybierz kartę **Ogólne** .

3. Na liście rozwijanej konfiguracja w górnej części wybierz konfigurację, której lokalizację pliku wyjściowego chcesz zmienić (**debugowanie**, **wydanie**lub **wszystkie konfiguracje**).

4. Znajdź wpis ścieżki wyjściowej na stronie &mdash; , która różni się w zależności od typu projektu:

   - **Ścieżka wyjściowa** dla projektów C# i JavaScript
   - **Ścieżka wyjściowa kompilacji** dla projektów Visual Basic
   - **Katalog wyjściowy** dla projektów Visual C++

   Wpisz ścieżkę, do której mają zostać wygenerowane dane wyjściowe (bezwzględne lub względne dla katalogu głównego projektu), lub kliknij przycisk **Przeglądaj** , aby przejść do tego folderu.

   ![Właściwość ścieżki wyjściowej dla projektu C# programu Visual Studio](media/output-path.png)
   
   > [!NOTE]
   > Niektóre projekty domyślnie obejmują strukturę i środowisko uruchomieniowe w ścieżce kompilacji. Aby to zmienić, kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań**, wybierz polecenie **Edytuj plik projektu**i Dodaj następujące elementy:
   > ```xml
   > <PropertyGroup>
   >   <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
   >   <AppendRuntimeIdentifierToOutputPath>false</AppendRuntimeIdentifierToOutputPath>
   > </PropertyGroup>
   > ```

> [!TIP]
> Jeśli dane wyjściowe nie są generowane do określonej lokalizacji, upewnij się, że tworzysz odpowiednią konfigurację (na przykład **debugowanie** lub **wydanie**), wybierając ją na pasku menu programu Visual Studio.
>
> ![Selektor konfiguracji kompilacji w programie Visual Studio 2019](media/build-configuration-chooser.png)

## <a name="see-also"></a>Zobacz też

- [Strona kompilacji, Projektant projektu (C#)](../ide/reference/build-page-project-designer-csharp.md)
- [Ogólna strona właściwości (projekt)](/cpp/build/reference/general-property-page-project)
- [Kompilowanie i tworzenie kompilacji](../ide/compiling-and-building-in-visual-studio.md)
