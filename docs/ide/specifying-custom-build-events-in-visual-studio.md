---
title: Określanie niestandardowych zdarzeń kompilacji
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e6c5bde6b6dce7655043f3dc766a5faa81fa944e
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055131"
---
# <a name="specify-custom-build-events-in-visual-studio"></a>Określanie niestandardowych zdarzeń kompilacji w programie Visual Studio

Określając to zdarzenie kompilacji niestandardowej, może automatycznie uruchomić polecenia przed uruchomieniem kompilacji lub po jej zakończeniu. Na przykład, można uruchomić *.bat* plików przed uruchomieniem kompilacji lub skopiuj nowe pliki do folderu, po zakończeniu kompilacji. Zdarzenia kompilacji są uruchamiane tylko wtedy, gdy kompilacja pomyślnie osiągnie tych punktów w procesie kompilacji.

 Aby uzyskać szczegółowe informacje o języku programowania, którego używasz zobacz następujące tematy:

-   Visual Basic —[porady: Określanie Tworzenie zdarzenia (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md).

-   C#i F#—[porady: Określanie zdarzeń kompilacji (C#)](../ide/how-to-specify-build-events-csharp.md).

-   Visual C++ —[określanie zdarzeń kompilacji](/cpp/ide/specifying-build-events).

## <a name="syntax"></a>Składnia

Zdarzenia kompilacji postępuj zgodnie z tej samej składni jako polecenia systemu DOS, ale makra umożliwia łatwiejsze tworzenie zdarzeń kompilacji. Aby uzyskać listę dostępnych makr, zobacz [okno dialogowe wiersz polecenia zdarzenia/po kompilacji — zdarzenia prekompilacyjnego](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

 Aby uzyskać najlepsze wyniki postępuj zgodnie z tymi porady dotyczące formatowania:

- Dodaj `call` instrukcji przed wszystkich zdarzeń, które są uruchamiane kompilacji *.bat* plików.

   Przykład: `call C:\MyFile.bat`

   Przykład: `call C:\MyFile.bat call C:\MyFile2.bat`

- Ścieżki plików należy ująć w znaki cudzysłowu.

   Przykład (dla [!INCLUDE[win8](../debugger/includes/win8_md.md)]): "% ProgramFiles (x86) %\Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4.0 Tools\gacutil.exe" — Jeśli "$(TargetPath)"

- Oddziel wiele poleceń przy użyciu podziały wierszy.

- Zawierać symbole wieloznaczne, zgodnie z potrzebami.

   Przykład: `for %I in (*.txt *.doc *.html) do copy %I c:\` *mydirectory*`\`

  > [!NOTE]
  >  `%I` w powyższym kodzie powinno być `%%I` w skryptach wsadowych.

## <a name="see-also"></a>Zobacz także

- [Kompilowanie i tworzenie kompilacji](../ide/compiling-and-building-in-visual-studio.md)
- [Okno dialogowe wiersz polecenia zdarzenia/po kompilacji — Zdarzenie sprzed kompilacji](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Znaki specjalne w MSBuild](../msbuild/msbuild-special-characters.md)
- [Przewodnik: kompilowanie aplikacji](../ide/walkthrough-building-an-application.md)
