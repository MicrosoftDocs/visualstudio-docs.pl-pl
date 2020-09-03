---
title: Określanie niestandardowych zdarzeń kompilacji
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fabbd4dc42ac4f66c7f53b639c6e7ed1f432878c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667125"
---
# <a name="specifying-custom-build-events-in-visual-studio"></a>Określenie niestandardowych zdarzeń kompilacji w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określając niestandardowe zdarzenie kompilacji, można automatycznie uruchamiać polecenia przed rozpoczęciem kompilacji lub po zakończeniu. Na przykład można uruchomić plik bat przed rozpoczęciem kompilacji lub skopiować nowe pliki do folderu po zakończeniu kompilacji. Zdarzenia kompilacji są uruchamiane tylko wtedy, gdy kompilacja pomyślnie osiągnie te punkty w procesie kompilacji.

 Aby uzyskać szczegółowe informacje na temat języka programowania, którego używasz, zobacz następujące tematy:

- Visual Basic —[instrukcje: Określanie zdarzeń kompilacji (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md).

- Visual C# i F # —[instrukcje: Określanie zdarzeń kompilacji (C#)](../ide/how-to-specify-build-events-csharp.md).

- Visual C++ —[Określanie zdarzeń kompilacji](https://msdn.microsoft.com/library/788a6c18-2dbe-4a49-8cd6-86c1ad7a95cc).

## <a name="syntax"></a>Składnia
 Zdarzenia kompilacji są zgodne z tą samą składnią co polecenia DOS, ale można użyć makr, aby łatwiej tworzyć zdarzenia kompilacji. Aby uzyskać listę dostępnych makr, zobacz [okno dialogowe zdarzenie przed kompilacją/wiersz polecenia zdarzenia po kompilacji](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

 Aby uzyskać najlepsze wyniki, postępuj zgodnie z następującymi wskazówkami dotyczącymi formatowania:

- Dodaj `call` instrukcję przed wszystkimi zdarzeniami kompilacji, które uruchamiają pliki. bat.

     Przykład: `call C:\MyFile.bat`

     Przykład: `call C:\MyFile.bat call C:\MyFile2.bat`

- Ujmij ścieżki plików w znaki cudzysłowu.

     Przykład (for [!INCLUDE[win8](../includes/win8-md.md)] ): "% PROGRAMFILES (x86)% \ Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4,0 Tools\gacutil.exe"-If "$ (TargetPath)"

- Rozdziel wiele poleceń za pomocą podziałów wierszy.

- W razie konieczności Uwzględnij symbole wieloznaczne.

     Przykład: moje `for %I in (*.txt *.doc *.html) do copy %I c:\` *katalogi*`\`

    > [!NOTE]
    > `%I` w powyższym kodzie powinny znajdować się `%%I` w skryptach wsadowych.

## <a name="see-also"></a>Zobacz też
 [Kompilowanie i kompilowanie](../ide/compiling-and-building-in-visual-studio.md) [zdarzeń przed kompilacją/wiersz polecenia zdarzenia po kompilacji —](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md) [MSBuild Special Characters](../msbuild/msbuild-special-characters.md) [Przewodnik: kompilowanie aplikacji](../ide/walkthrough-building-an-application.md)
