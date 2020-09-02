---
title: 'Instrukcje: Określanie poleceń przed i po Instrumentacji | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: ab7ecbe97ba0b174a1cc4c0f0d169834ce25e8d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64788899"
---
# <a name="how-to-specify-pre--and-post-instrument-commands"></a>Porady: określanie poleceń pre- i post-instrumentalnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz określić polecenia, które są uruchamiane przed lub po wykonaniu plików binarnych w sesji wydajności. Każde polecenie, które może zostać wystawione z wiersza polecenia, można określić jako zdarzenie wstępne lub po nim. Na przykład można określić polecenia, które automatyzują ponowny podpisanie zestawu przy użyciu klucza silnej nazwy w pliku wsadowym, który jest wykonywany po Instrumentacji plików binarnych.  
  
 Można określić polecenia dla wszystkich plików binarnych instrumentacji w przebiegu profilowania lub dla poszczególnych plików binarnych. Można jednak określić tylko jedno polecenie przedprodukcyjne do uruchomienia przed i tylko jedno polecenie, które zostanie uruchomione po zakończeniu procesu instrumentacji. Nie można określić poleceń dla wszystkich plików binarnych i dla pojedynczych plików binarnych. Po określeniu poleceń dla wszystkich plików binarnych polecenia są uruchamiane przed lub po Instrumentacji każdego pliku binarnego w sesji.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Katalog roboczy, w którym polecenia są wykonywane, zależy od systen operacyjnego, w którym jest uruchomiona [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] , oraz na platformie docelowej profilowanej aplikacji.  
  
  **32-bitowe komputery**  
  
  Na komputerach 32-bitowych domyślnym katalogiem narzędzi profilera jest Drive\Program Files\Microsoft Visual Studio 10.0 \ Team Tools\Performance Tools.  
  
  **Komputery 64-bitowe**  
  
  Na komputerach 64-bitowych określ ścieżkę zgodną z platformą docelową profilowanej aplikacji:  
  
- W przypadku aplikacji 32-bitowych domyślnym katalogiem narzędzi profilera jest:  
  
   *Dysk*\Program Files (x86) \Microsoft Visual Studio 10.0 \ Team Tools\Performance Tools  
  
- W przypadku aplikacji 64-bitowych domyślnym katalogiem narzędzi profilera jest:  
  
   *Dysk*\Program Files (x86) \Microsoft Visual Studio 10.0 \ Team Tools\Performance Tools\x64  
  
### <a name="to-specify-pre-instrument-commands"></a>Aby określić polecenia przed Instrumentacją  
  
1. Wykonaj jedną z następujących czynności:  
  
    - Aby określić polecenia przed Instrumentacją dla wszystkich plików binarnych w sesji wydajności, wybierz węzeł sesja wydajności w **Eksplorator wydajności**, a następnie kliknij prawym przyciskiem myszy i wybierz polecenie **Właściwości**.  
  
    - Aby określić polecenia przed Instrumentacją dla określonego pliku binarnego, kliknij prawym przyciskiem myszy nazwę pliku binarnego na liście **targets** sesji wydajności, a następnie wybierz polecenie **Właściwości**.  
  
2. Na **stronie właściwości**kliknij pozycję **Instrumentacja**.  
  
3. Wpisz polecenie w polu tekstowym **wiersz polecenia** w obszarze **zdarzenia przed Instrumentacją**.  
  
    > [!NOTE]
    > Możesz kliknąć przycisk wielokropka **(...)** , który jest przyległy do pola **wiersza polecenia** , aby wyszukać i wybrać odpowiedni plik exe, cmd lub bat.  
  
4. Kliknij przycisk **OK**.  
  
     Aby wyłączyć uruchamianie polecenia bez usuwania, zaznacz pole wyboru **Wyklucz z Instrumentacji** . Aby zmodyfikować ustawienia kompilatora lub konsolidatora, użyj stron właściwości projektu.  
  
### <a name="to-specify-post-instrument-commands"></a>Aby określić polecenia po Instrumentacji  
  
1. Wykonaj jedną z następujących czynności:  
  
    - Aby określić polecenia dla wszystkich plików binarnych w sesji wydajności, zaznacz węzeł sesja wydajności w **Eksplorator wydajności**, a następnie kliknij prawym przyciskiem myszy i wybierz polecenie **Właściwości**.  
  
    - Aby określić polecenia dla określonego pliku binarnego, kliknij prawym przyciskiem myszy nazwę pliku binarnego na liście **targets** sesji wydajności, a następnie wybierz polecenie **Właściwości**.  
  
2. Na **stronie właściwości**kliknij pozycję **Instrumentacja**.  
  
3. Wpisz polecenie w polu tekstowym **wiersz polecenia** w obszarze **zdarzenia po Instrumentacji**.  
  
    > [!NOTE]
    > Możesz kliknąć przycisk wielokropka **(...)** , który jest przyległy do pola **wiersza polecenia** , aby wyszukać i wybrać odpowiedni plik exe, cmd lub bat.  
  
4. Kliknij przycisk **OK**.  
  
     Aby wyłączyć uruchamianie polecenia bez usuwania, zaznacz pole wyboru **Wyklucz z Instrumentacji** . Aby zmodyfikować ustawienia kompilatora lub konsolidatora, użyj stron właściwości projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
