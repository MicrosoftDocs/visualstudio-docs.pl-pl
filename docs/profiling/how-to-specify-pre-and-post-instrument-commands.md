---
title: 'Jak: Określanie poleceń wstępnych i poprzyrządowych | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.instrument
helpviewer_keywords:
- profiling tools, pre-instrument events
- events [Visual Studio], pre-instrument
- pre-instrument events, performance tools
ms.assetid: 6a8d5340-1d1b-4d81-88dd-8e1f435eb828
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 22ad5558ed01e5bb1b8d12b7a4cc65b4d677d0cd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778716"
---
# <a name="how-to-specify-pre--and-post-instrument-commands"></a>Instrukcje: określanie poleceń przed i po instrumentacji

Można określić polecenia, które są uruchamiane przed lub po instrumencie plików binarnych w sesji wydajności. Każde polecenie, które może zostać wydane z wiersza polecenia, można określić jako zdarzenie wstępne lub po instrumencie. Na przykład można określić polecenia, które automatyzują rezygnację zestawu z kluczem silnej nazwy w pliku wsadowym, który jest wykonywany po inastruowaniu plików binarnych.

Można określić polecenia dla wszystkich instrumentowanych plików binarnych w przebiegu profilowania lub dla poszczególnych plików binarnych. Można jednak określić tylko jedno polecenie wstępnego instrumencie do uruchomienia przed i tylko jedno polecenie po instrumencie, aby uruchomić po procesie instrumentacji. Nie można określić poleceń dla wszystkich plików binarnych i dla poszczególnych plików binarnych. Po określeniu poleceń dla wszystkich plików binarnych polecenia są uruchamiane przed lub po instrumentacji każdego pliku binarnego w sesji.

Katalog roboczy, w którym polecenia są wykonywane, zależy od [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] systemu operacyjnego, w którym są uruchomione i na platformie docelowej profilowanej aplikacji.

Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

## <a name="to-specify-pre-instrument-commands"></a>Aby określić polecenia przyrządów przyrządów wstępnych

1. Wykonaj jedną z następujących czynności:

    - Aby określić polecenia wstępnego instrumencie dla wszystkich plików binarnych w sesji wydajności, wybierz węzeł sesji wydajności w **Eksploratorze wydajności,** a następnie kliknij prawym przyciskiem myszy i wybierz polecenie **Właściwości**.

    - Aby określić polecenia wstępnego instrumencie dla określonego pliku binarnego, kliknij prawym przyciskiem myszy nazwę pliku binarnego na liście **Cele** sesji wydajności, a następnie wybierz polecenie **Właściwości**.

2. Na **stronach właściwości**kliknij pozycję **Instrumentacja**.

3. Wpisz polecenie w polu tekstowym **wiersza polecenia** w obszarze **Zdarzenia przedarządowe**.

    > [!NOTE]
    > Można kliknąć przycisk wielokropka **(...)** sąsiadujący z **polem wiersza polecenia,** aby przejść do odpowiedniego pliku .exe, .cmd lub .cmd.

4. Kliknij przycisk **OK**.

     Aby wyłączyć uruchomienie polecenia bez jego usuwania, zaznacz pole wyboru **Wyklucz z instrumentacji.** Aby zmodyfikować ustawienia kompilatora lub konsolidatora, użyj stron właściwości projektu.

## <a name="to-specify-post-instrument-commands"></a>Aby określić polecenia post-instrument

1. Wykonaj jedną z następujących czynności:

    - Aby określić polecenia post-instrument dla wszystkich plików binarnych w sesji wydajności, wybierz węzeł sesji wydajności w **Eksploratorze wydajności,** a następnie kliknij prawym przyciskiem myszy i wybierz polecenie **Właściwości**.

    - Aby określić polecenia post-instrument dla określonego pliku binarnego, kliknij prawym przyciskiem myszy nazwę pliku binarnego na liście **Cele** sesji wydajności, a następnie wybierz polecenie **Właściwości**.

2. Na **stronach właściwości**kliknij pozycję **Instrumentacja**.

3. Wpisz polecenie w polu tekstowym **wiersza polecenia** w obszarze **Zdarzenia postprzyrządowe**.

    > [!NOTE]
    > Można kliknąć przycisk wielokropka **(...)** sąsiadujący z **polem wiersza polecenia,** aby przejść do odpowiedniego pliku .exe, .cmd lub .cmd.

4. Kliknij przycisk **OK**.

     Aby wyłączyć uruchomienie polecenia bez jego usuwania, zaznacz pole wyboru **Wyklucz z instrumentacji.** Aby zmodyfikować ustawienia kompilatora lub konsolidatora, użyj stron właściwości projektu.

## <a name="see-also"></a>Zobacz też

[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
