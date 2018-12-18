---
title: 'Porady: Określanie poleceń przed i po Instrumentacji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.property.instrument
helpviewer_keywords:
- profiling tools, pre-instrument events
- events [Visual Studio], pre-instrument
- pre-instrument events, performance tools
ms.assetid: 6a8d5340-1d1b-4d81-88dd-8e1f435eb828
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b88d49be8ee4651d82135b3e8d27bef8218ffd43
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51772225"
---
# <a name="how-to-specify-pre--and-post-instrument-commands"></a>Porady: określanie poleceń pre- i post-instrumentalnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz określić polecenia, które są uruchamiane przed lub po są instrumentowane pliki binarne w sesji wydajności. Wszystkie polecenia, które mogą być wystawiane z wiersza polecenia można określić jako przed Instrumentacją lub zdarzenia po instrumentacji. Na przykład można określić poleceń, które automatyzują ponownego podpisywania zestawu za pomocą klucza silnej nazwy w pliku wsadowym, który jest wykonywany po są instrumentowane pliki binarne.  
  
 Można określić poleceń dla instrumentowanych danych binarnych w trakcie uruchomienia profilowania, lub dla pojedynczych plików binarnych. Jednakże można określić tylko jedno polecenie przed Instrumentacją do uruchomienia przed i tylko jedno polecenie po Instrumentacji do uruchomienia po zakończeniu procesu instrumentacji. Nie można określić poleceń dla obu wszystkie pliki binarne i pojedynczych plików binarnych. Po określeniu polecenia dla wszystkich plików binarnych, polecenia są uruchamiane przed lub po Instrumentacji każdym pliku binarnego w sesji.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Katalog roboczy, w którym są wykonywane polecenia zależy od systen operacyjne, w którym jest uruchomiony [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] i na platformie docelowej profilowanej aplikacji.  
  
  **32-bitowych komputerów**  
  
  Na komputerach z 32-bitowych domyślny katalog narzędzia profiler jest 10.0\Team: dysk rozruchowy\Program Files\Microsoft Visual Studio Tools narzędzia.  
  
  **komputerów 64-bitowych**  
  
  Na komputerach 64-bitowego wpisz ścieżkę zależnie od platformy docelowej profilowanej aplikacji:  
  
- Dla 32-bitowych aplikacji domyślny katalog narzędzia profiler jest:  
  
   *Drive*\Program Files (x86)\Microsoft Visual Studio 10.0\Team Tools\Performance Tools  
  
- Dla aplikacji 64-bitowych jest domyślny katalog narzędzi profilera:  
  
   *Drive*\Program Files (x86)\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\x64  
  
### <a name="to-specify-pre-instrument-commands"></a>Aby określić polecenie przed Instrumentacją  
  
1.  Wykonaj jedną z następujących czynności:  
  
    -   Aby określić polecenia przed Instrumentacją dla wszystkich plików binarnych w sesji wydajności, wybierz węzeł sesji wydajności w **Eksplorator wydajności**, a następnie kliknij prawym przyciskiem myszy i wybierz **właściwości**.  
  
    -   Aby określić polecenie przed Instrumentacją dla określonego pliku binarnego, kliknij prawym przyciskiem myszy nazwę pliku binarnego w **cele** listę sesji wydajności, a następnie wybierz **właściwości**.  
  
2.  W **stron właściwości**, kliknij przycisk **Instrumentacji**.  
  
3.  Wpisz polecenie w **wiersza polecenia** polu tekstowym w obszarze **zdarzenia przed Instrumentacją**.  
  
    > [!NOTE]
    >  Możesz kliknąć przycisk wielokropka **(...)**  która jest przyległa do **wiersza polecenia** pole, aby przejść do, a następnie wybierz odpowiedni plik .exe, cmd lub bat.  
  
4.  Kliknij przycisk **OK**.  
  
     Aby wyłączyć polecenia uruchamiane bez usuwania go, wybierz **Wyklucz z Instrumentacji** pole wyboru. Aby zmodyfikować kompilatora lub konsolidatora, ustawienia, należy użyć strony właściwości projektu.  
  
### <a name="to-specify-post-instrument-commands"></a>Aby określić polecenie po Instrumentacji  
  
1.  Wykonaj jedną z następujących czynności:  
  
    -   Aby określić polecenia po instrumentacji dla wszystkich plików binarnych w sesji wydajności, wybierz węzeł sesji wydajności w **Eksplorator wydajności**, a następnie kliknij prawym przyciskiem myszy i wybierz **właściwości**.  
  
    -   Aby określić polecenie po instrumentacji dla określonego pliku binarnego, kliknij prawym przyciskiem myszy nazwę pliku binarnego w **cele** listę sesji wydajności, a następnie wybierz **właściwości**.  
  
2.  W **stron właściwości**, kliknij przycisk **Instrumentacji**.  
  
3.  Wpisz polecenie w **wiersza polecenia** polu tekstowym w obszarze **zdarzenia po Instrumentacji**.  
  
    > [!NOTE]
    >  Możesz kliknąć przycisk wielokropka **(...)**  która jest przyległa do **wiersza polecenia** pole, aby przejść do, a następnie wybierz odpowiedni plik .exe, cmd lub bat.  
  
4.  Kliknij przycisk **OK**.  
  
     Aby wyłączyć polecenia uruchamiane bez usuwania go, wybierz **Wyklucz z Instrumentacji** pole wyboru. Aby zmodyfikować kompilatora lub konsolidatora, ustawienia, należy użyć strony właściwości projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)



