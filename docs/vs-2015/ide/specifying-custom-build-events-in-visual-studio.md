---
title: Określanie niestandardowych zdarzeń kompilacji
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f2dbb785bcc3092872763d23e968cbf699603286
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067106"
---
# <a name="specifying-custom-build-events-in-visual-studio"></a>Określenie niestandardowych zdarzeń kompilacji w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określając to zdarzenie kompilacji niestandardowej, może automatycznie uruchomić polecenia przed uruchomieniem kompilacji lub po jej zakończeniu. Można na przykład, uruchom plik bat przed kompilacją rozpoczyna się lub skopiuj nowe pliki do folderu, po zakończeniu kompilacji. Zdarzenia kompilacji są uruchamiane tylko wtedy, gdy kompilacja pomyślnie osiągnie tych punktów w procesie kompilacji.

 Aby uzyskać szczegółowe informacje o języku programowania, którego używasz zobacz następujące tematy:

-   Visual Basic —[porady: Określanie zdarzeń kompilacji (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md).

-   Wizualne C# i F#—[porady: Określanie zdarzeń kompilacji (C#)](../ide/how-to-specify-build-events-csharp.md).

-   Visual C++ —[określanie zdarzeń kompilacji](http://msdn.microsoft.com/library/788a6c18-2dbe-4a49-8cd6-86c1ad7a95cc).

## <a name="syntax"></a>Składnia
 Zdarzenia kompilacji postępuj zgodnie z tej samej składni jako polecenia systemu DOS, ale makra umożliwia łatwiejsze tworzenie zdarzeń kompilacji. Aby uzyskać listę dostępnych makr, zobacz [prekompilacji zdarzeń/po kompilacji — zdarzenie wiersza polecenia okno dialogowe](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

 Aby uzyskać najlepsze wyniki postępuj zgodnie z tymi porady dotyczące formatowania:

-   Dodaj `call` instrukcji, zanim wszystkie zdarzenia kompilacji, uruchamiać pliki bat.

     Przykład: `call C:\MyFile.bat`

     Przykład: `call C:\MyFile.bat call C:\MyFile2.bat`

-   Ścieżki plików należy ująć w znaki cudzysłowu.

     Przykład (dla [!INCLUDE[win8](../includes/win8-md.md)]): "% ProgramFiles (x86) %\Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4.0 Tools\gacutil.exe" — Jeśli "$(TargetPath)"

-   Oddziel wiele poleceń przy użyciu podziały wierszy.

-   Zawierać symbole wieloznaczne, zgodnie z potrzebami.

     Przykład: `for %I in (*.txt *.doc *.html) do copy %I c:\` *mydirectory*`\`

    > [!NOTE]
    >  `%I` w powyższym kodzie powinno być `%%I` w skryptach wsadowych.

## <a name="see-also"></a>Zobacz też
 [Kompilowanie i tworzenie](../ide/compiling-and-building-in-visual-studio.md) [wstępnie zdarzeń/po kompilacji — zdarzenia kompilacji wiersza polecenia okno dialogowe](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md) [znaki specjalne w programie MSBuild](../msbuild/msbuild-special-characters.md) [wskazówki: tworzenie aplikacji](../ide/walkthrough-building-an-application.md)
