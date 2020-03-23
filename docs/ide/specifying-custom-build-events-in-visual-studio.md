---
title: Określanie niestandardowych zdarzeń kompilacji
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
ms.openlocfilehash: fda60ffb97ecb44bd4a881cb42e4d9199cc958b8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115342"
---
# <a name="specify-custom-build-events-in-visual-studio"></a>Określanie zdarzeń kompilacji niestandardowej w programie Visual Studio

Określając zdarzenie kompilacji niestandardowej, można automatycznie uruchamiać polecenia przed rozpoczęciem kompilacji lub po jej zakończeniu. Na przykład można uruchomić plik *.bat* przed rozpoczęciem kompilacji lub skopiować nowe pliki do folderu po zakończeniu kompilacji. Tworzenie zdarzeń uruchamianych tylko wtedy, gdy kompilacja pomyślnie osiągnie te punkty w procesie kompilacji.

Aby uzyskać szczegółowe informacje na temat używanego języka programowania, zobacz następujące tematy:

- Visual Basic -[Jak: Określ zdarzenia kompilacji (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md).

- C# i F#--[Jak: Określ zdarzenia kompilacji (C#)](../ide/how-to-specify-build-events-csharp.md).

- Visual C++--[Określ zdarzenia kompilacji](/cpp/build/specifying-build-events).

## <a name="syntax"></a>Składnia

Zdarzenia kompilacji są zgodne z tą samą składnią co polecenia DOS, ale można użyć makr do łatwiejszego tworzenia zdarzeń kompilacji. Aby uzyskać listę dostępnych makr, zobacz [Okno dialogowe wiersza polecenia Zdarzenie przed kompilacją/po utworzeniu](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

Aby uzyskać najlepsze wyniki, postępuj zgodnie z tymi wskazówkami dotyczącymi formatowania:

- Dodaj `call` instrukcję przed wszystkimi zdarzeniami kompilacji, które uruchamiają pliki *.bat.*

   Przykład: `call C:\MyFile.bat`

   Przykład: `call C:\MyFile.bat call C:\MyFile2.bat`

- Łącz ścieżki plików w cudzysłów.

   Przykład (dla): [!INCLUDE[win8](../debugger/includes/win8_md.md)]"%ProgramFiles(x86)%\Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4.0 Tools\gacutil.exe" -if "$(TargetPath)"

- Oddziel wiele poleceń za pomocą podziałów wierszy.

- W razie potrzeby uwzględnij symbole wieloznaczne.

   Przykład: `for %I in (*.txt *.doc *.html) do copy %I c:\` *mójdirectory*`\`

  > [!NOTE]
  > `%I`w powyższym kodzie powinny być `%%I` w skryptach wsadowych.

## <a name="see-also"></a>Zobacz też

- [Kompilowanie i tworzenie kompilacji](../ide/compiling-and-building-in-visual-studio.md)
- [Okno dialogowe Wiersz polecenia Zdarzenie przed kompilacją/po utworzeniu](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Znaki specjalne MSBuild](../msbuild/msbuild-special-characters.md)
- [Przewodnik: kompilowanie aplikacji](../ide/walkthrough-building-an-application.md)
