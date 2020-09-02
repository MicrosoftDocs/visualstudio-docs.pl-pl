---
title: 'Instrukcje: wyświetlanie informacji o śledzeniu WPF | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: be3c6859-06e1-459e-9fd0-46375b5f55ef
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c9642902bf334ce83f95a9113059683f183c6116
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537971"
---
# <a name="how-to-display-wpf-trace-information"></a>Porady: wyświetlanie informacji o śledzeniu WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] może odbierać informacje o śledzeniu debugowania z aplikacji WPF i wyświetlać te informacje w oknie **danych wyjściowych** . Aby wyświetlić informacje o śledzeniu debugowania, należy włączyć śledzenie WPF.  
  
 Śledzenie WPF można włączyć w pliku App.Config lub programowo przy użyciu <xref:System.Diagnostics.PresentationTraceSources> klasy. Łatwiejszym sposobem włączenia śledzenia WPF jest użycie okna **Opcje** . Śledzenie WPF dla aplikacji sieci Web nie jest obsługiwane.  
  
### <a name="to-enable-or-customize-wpf-trace-information"></a>Aby włączyć lub dostosować informacje śledzenia WPF  
  
1. W menu **Tools** (Narzędzia) wybierz pozycję **Options** (Opcje).  
  
2. W oknie dialogowym **Opcje** , w polu po lewej stronie Otwórz węzeł **debugowanie** .  
  
3. W obszarze **debugowanie**kliknij **okno dane wyjściowe**.  
  
4. W obszarze **Ogólne ustawienia danych wyjściowych**wybierz pozycję **wszystkie dane wyjściowe debugowania**.  
  
5. W polu po prawej stronie Znajdź pozycję **ustawienia śledzenia WPF**.  
  
6. Otwórz węzeł **ustawienia śledzenia WPF** .  
  
7. W obszarze **ustawienia śledzenia WPF**kliknij kategorię ustawień, które chcesz włączyć (na przykład **powiązanie danych**).  
  
     Kontrolka listy rozwijanej jest wyświetlana w kolumnie ustawienia obok pozycji **powiązanie danych** lub niezależnie od wybranej kategorii.  
  
8. Kliknij listę rozwijaną i wybierz typ informacji śledzenia, które chcesz wyświetlić: **wszystkie**, **krytyczne**, **błąd**, **Ostrzeżenie**, **informacje**, **pełne**lub **ActivityTracing**.  
  
     **Krytyczne** umożliwia śledzenie tylko zdarzeń krytycznych.  
  
     **Błąd** umożliwia śledzenie zdarzeń krytycznych i błędów.  
  
     **Ostrzeżenie** umożliwia śledzenie zdarzeń krytycznych, błędów i ostrzeżeń.  
  
     **Informacje** umożliwiają śledzenie zdarzeń krytycznych, błędów, ostrzeżeń i informacji.  
  
     Funkcja **verbose** umożliwia śledzenie zdarzeń krytycznych, błędów, ostrzeżeń, informacji i pełnych.  
  
     **ActivityTracing** umożliwia śledzenie zdarzeń zatrzymania, uruchamiania, zawieszania, przesyłania i wznawiania.  
  
     Aby uzyskać więcej informacji na temat tego, co oznaczają te poziomy informacji o śledzeniu, zobacz <xref:System.Diagnostics.SourceLevels> .  
  
9. Kliknij przycisk **OK**.  
  
### <a name="to-disable-wpf-trace-information"></a>Aby wyłączyć informacje śledzenia WPF  
  
1. W menu **Tools** (Narzędzia) wybierz pozycję **Options** (Opcje).  
  
2. W oknie dialogowym **Opcje** , w polu po lewej stronie Otwórz węzeł **debugowanie** .  
  
3. W obszarze **debugowanie**kliknij **okno dane wyjściowe**.  
  
4. W polu po prawej stronie Znajdź pozycję **ustawienia śledzenia WPF**.  
  
5. Otwórz węzeł **ustawienia śledzenia WPF** .  
  
6. W obszarze **ustawienia śledzenia WPF**kliknij kategorię ustawień, które chcesz włączyć (na przykład **powiązanie danych**).  
  
     Kontrolka listy rozwijanej jest wyświetlana w kolumnie ustawienia obok pozycji **powiązanie danych** lub niezależnie od wybranej kategorii.  
  
7. Kliknij listę rozwijaną i wybierz pozycję **wyłączone**.  
  
8. Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie WPF](../debugger/debugging-wpf.md)
