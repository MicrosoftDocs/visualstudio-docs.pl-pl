---
title: Określanie niestandardowych zdarzeń kompilacji
description: Dowiedz się, jak można automatycznie uruchamiać polecenia w programie Visual Studio przed rozpoczęciem kompilacji lub po zakończeniu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1d339f9bbf170d2df545e69c698f786198695ad
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136787"
---
# <a name="specify-custom-build-events-in-visual-studio"></a>Określanie niestandardowych zdarzeń kompilacji w programie Visual Studio

Określając niestandardowe zdarzenie kompilacji, można automatycznie uruchamiać polecenia przed rozpoczęciem kompilacji lub po zakończeniu. Na przykład można uruchomić plik *bat* przed rozpoczęciem kompilacji lub skopiować nowe pliki do folderu po zakończeniu kompilacji. Zdarzenia kompilacji są uruchamiane tylko wtedy, gdy kompilacja pomyślnie osiągnie te punkty w procesie kompilacji.

Aby uzyskać szczegółowe informacje na temat języka programowania, którego używasz, zobacz następujące tematy:

- Visual Basic —[instrukcje: Określanie zdarzeń kompilacji (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md).

- C# i F # —[How to: Określanie zdarzeń kompilacji (C#)](../ide/how-to-specify-build-events-csharp.md).

- Visual C++--[Określ zdarzenia kompilacji](/cpp/build/specifying-build-events).

## <a name="syntax"></a>Składnia

Zdarzenia kompilacji są zgodne z tą samą składnią co polecenia DOS, ale można użyć makr, aby łatwiej tworzyć zdarzenia kompilacji. Aby uzyskać listę dostępnych makr, zobacz [okno dialogowe zdarzenie przed kompilacją/wiersz polecenia zdarzenia po kompilacji](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

Aby uzyskać najlepsze wyniki, postępuj zgodnie z następującymi wskazówkami dotyczącymi formatowania:

- Dodaj `call` instrukcję przed wszystkimi zdarzeniami kompilacji, które uruchamiają pliki *. bat* .

   Przykład: `call C:\MyFile.bat`

   Przykład: `call C:\MyFile.bat call C:\MyFile2.bat`

- Ujmij ścieżki plików w znaki cudzysłowu.

   Przykład (for [!INCLUDE[win8](../debugger/includes/win8_md.md)] ): "% PROGRAMFILES (x86)% \ Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4,0 Tools\gacutil.exe"-If "$ (TargetPath)"

- Rozdziel wiele poleceń za pomocą podziałów wierszy.

- W razie konieczności Uwzględnij symbole wieloznaczne.

   Przykład: moje `for %I in (*.txt *.doc *.html) do copy %I c:\` *katalogi*`\`

  > [!NOTE]
  > `%I` w powyższym kodzie powinny znajdować się `%%I` w skryptach wsadowych.

## <a name="see-also"></a>Zobacz też

- [Kompilowanie i tworzenie kompilacji](../ide/compiling-and-building-in-visual-studio.md)
- [Zdarzenie przed kompilacją/wiersz polecenia zdarzenia po kompilacji](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Znaki specjalne w programie MSBuild](../msbuild/msbuild-special-characters.md)
- [Przewodnik: kompilowanie aplikacji](../ide/walkthrough-building-an-application.md)
