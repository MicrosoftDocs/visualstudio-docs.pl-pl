---
title: Określ polecenia przed i po Instrumentacji | Microsoft Docs
description: Dowiedz się, w jaki sposób można określić polecenia, które są uruchamiane przed lub po plikach binarnych w sesji wydajności.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.instrument
helpviewer_keywords:
- profiling tools, pre-instrument events
- events [Visual Studio], pre-instrument
- pre-instrument events, performance tools
ms.assetid: 6a8d5340-1d1b-4d81-88dd-8e1f435eb828
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7f5bc12a8b0ffb7ef0fa1a78b771ced829f4d73c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955817"
---
# <a name="how-to-specify-pre--and-post-instrument-commands"></a>Instrukcje: określanie poleceń przed i po instrumentacji

Możesz określić polecenia, które są uruchamiane przed lub po wykonaniu plików binarnych w sesji wydajności. Każde polecenie, które może zostać wystawione z wiersza polecenia, można określić jako zdarzenie wstępne lub po nim. Na przykład można określić polecenia, które automatyzują ponowny podpisanie zestawu przy użyciu klucza silnej nazwy w pliku wsadowym, który jest wykonywany po Instrumentacji plików binarnych.

Można określić polecenia dla wszystkich plików binarnych instrumentacji w przebiegu profilowania lub dla poszczególnych plików binarnych. Można jednak określić tylko jedno polecenie przedprodukcyjne do uruchomienia przed i tylko jedno polecenie, które zostanie uruchomione po zakończeniu procesu instrumentacji. Nie można określić poleceń dla wszystkich plików binarnych i dla pojedynczych plików binarnych. Po określeniu poleceń dla wszystkich plików binarnych polecenia są uruchamiane przed lub po Instrumentacji każdego pliku binarnego w sesji.

Katalog roboczy, w którym polecenia są wykonywane, zależy od systemu operacyjnego, w którym jest uruchomiony program [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] , oraz na platformie docelowej profilowanej aplikacji.

Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

## <a name="to-specify-pre-instrument-commands"></a>Aby określić polecenia przed Instrumentacją

1. Wykonaj jedną z następujących czynności:

    - Aby określić polecenia przed Instrumentacją dla wszystkich plików binarnych w sesji wydajności, wybierz węzeł sesja wydajności w **Eksplorator wydajności**, a następnie kliknij prawym przyciskiem myszy i wybierz polecenie **Właściwości**.

    - Aby określić polecenia przed Instrumentacją dla określonego pliku binarnego, kliknij prawym przyciskiem myszy nazwę pliku binarnego na liście **targets** sesji wydajności, a następnie wybierz polecenie **Właściwości**.

2. Na **stronie właściwości** kliknij pozycję **Instrumentacja**.

3. Wpisz polecenie w polu tekstowym **wiersz polecenia** w obszarze **zdarzenia przed Instrumentacją**.

    > [!NOTE]
    > Możesz kliknąć przycisk wielokropka **(...)** , który jest przyległy do pola **wiersza polecenia** , aby wyszukać i wybrać odpowiedni plik exe, cmd lub bat.

4. Kliknij przycisk **OK**.

     Aby wyłączyć uruchamianie polecenia bez usuwania, zaznacz pole wyboru **Wyklucz z Instrumentacji** . Aby zmodyfikować ustawienia kompilatora lub konsolidatora, użyj stron właściwości projektu.

## <a name="to-specify-post-instrument-commands"></a>Aby określić polecenia po Instrumentacji

1. Wykonaj jedną z następujących czynności:

    - Aby określić polecenia dla wszystkich plików binarnych w sesji wydajności, zaznacz węzeł sesja wydajności w **Eksplorator wydajności**, a następnie kliknij prawym przyciskiem myszy i wybierz polecenie **Właściwości**.

    - Aby określić polecenia dla określonego pliku binarnego, kliknij prawym przyciskiem myszy nazwę pliku binarnego na liście **targets** sesji wydajności, a następnie wybierz polecenie **Właściwości**.

2. Na **stronie właściwości** kliknij pozycję **Instrumentacja**.

3. Wpisz polecenie w polu tekstowym **wiersz polecenia** w obszarze **zdarzenia po Instrumentacji**.

    > [!NOTE]
    > Możesz kliknąć przycisk wielokropka **(...)** , który jest przyległy do pola **wiersza polecenia** , aby wyszukać i wybrać odpowiedni plik exe, cmd lub bat.

4. Kliknij przycisk **OK**.

     Aby wyłączyć uruchamianie polecenia bez usuwania, zaznacz pole wyboru **Wyklucz z Instrumentacji** . Aby zmodyfikować ustawienia kompilatora lub konsolidatora, użyj stron właściwości projektu.

## <a name="see-also"></a>Zobacz też

[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
