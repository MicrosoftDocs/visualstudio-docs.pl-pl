---
title: 'Instrukcje: Określ polecenia przed i po Instrumentacji | Dokumentacja firmy Microsoft'
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c80e16b3566fd0687b74c5a43363864038f88cbf
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53861465"
---
# <a name="how-to-specify-pre--and-post-instrument-commands"></a>Instrukcje: Określanie poleceń przed i po instrumentacji

Możesz określić polecenia, które są uruchamiane przed lub po są instrumentowane pliki binarne w sesji wydajności. Wszystkie polecenia, które mogą być wystawiane z wiersza polecenia można określić jako przed Instrumentacją lub zdarzenia po instrumentacji. Na przykład można określić poleceń, które automatyzują ponownego podpisywania zestawu za pomocą klucza silnej nazwy w pliku wsadowym, który jest wykonywany po są instrumentowane pliki binarne.

Można określić poleceń dla instrumentowanych danych binarnych w trakcie uruchomienia profilowania, lub dla pojedynczych plików binarnych. Jednakże można określić tylko jedno polecenie przed Instrumentacją do uruchomienia przed i tylko jedno polecenie po Instrumentacji do uruchomienia po zakończeniu procesu instrumentacji. Nie można określić poleceń dla obu wszystkie pliki binarne i pojedynczych plików binarnych. Po określeniu polecenia dla wszystkich plików binarnych, polecenia są uruchamiane przed lub po Instrumentacji każdym pliku binarnego w sesji.

Katalog roboczy, w którym są wykonywane polecenia zależy od systemu operacyjnego, na którym uruchomiony jest program [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] i na platformie docelowej profilowanej aplikacji.

Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

## <a name="to-specify-pre-instrument-commands"></a>Aby określić polecenie przed Instrumentacją

1. Wykonaj jedną z następujących czynności:

    - Aby określić polecenia przed Instrumentacją dla wszystkich plików binarnych w sesji wydajności, wybierz węzeł sesji wydajności w **Eksplorator wydajności**, a następnie kliknij prawym przyciskiem myszy i wybierz **właściwości**.

    - Aby określić polecenie przed Instrumentacją dla określonego pliku binarnego, kliknij prawym przyciskiem myszy nazwę pliku binarnego w **cele** listę sesji wydajności, a następnie wybierz **właściwości**.

2. W **stron właściwości**, kliknij przycisk **Instrumentacji**.

3. Wpisz polecenie w **wiersza polecenia** polu tekstowym w obszarze **zdarzenia przed Instrumentacją**.

    > [!NOTE]
    > Możesz kliknąć przycisk wielokropka **(...)**  która jest przyległa do **wiersza polecenia** pole, aby przejść do, a następnie wybierz odpowiedni plik .exe, cmd lub bat.

4. Kliknij przycisk **OK**.

     Aby wyłączyć polecenia uruchamiane bez usuwania go, wybierz **Wyklucz z Instrumentacji** pole wyboru. Aby zmodyfikować kompilatora lub konsolidatora, ustawienia, należy użyć strony właściwości projektu.

## <a name="to-specify-post-instrument-commands"></a>Aby określić polecenie po Instrumentacji

1. Wykonaj jedną z następujących czynności:

    - Aby określić polecenia po instrumentacji dla wszystkich plików binarnych w sesji wydajności, wybierz węzeł sesji wydajności w **Eksplorator wydajności**, a następnie kliknij prawym przyciskiem myszy i wybierz **właściwości**.

    - Aby określić polecenie po instrumentacji dla określonego pliku binarnego, kliknij prawym przyciskiem myszy nazwę pliku binarnego w **cele** listę sesji wydajności, a następnie wybierz **właściwości**.

2. W **stron właściwości**, kliknij przycisk **Instrumentacji**.

3. Wpisz polecenie w **wiersza polecenia** polu tekstowym w obszarze **zdarzenia po Instrumentacji**.

    > [!NOTE]
    > Możesz kliknąć przycisk wielokropka **(...)**  która jest przyległa do **wiersza polecenia** pole, aby przejść do, a następnie wybierz odpowiedni plik .exe, cmd lub bat.

4. Kliknij przycisk **OK**.

     Aby wyłączyć polecenia uruchamiane bez usuwania go, wybierz **Wyklucz z Instrumentacji** pole wyboru. Aby zmodyfikować kompilatora lub konsolidatora, ustawienia, należy użyć strony właściwości projektu.

## <a name="see-also"></a>Zobacz także

[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
