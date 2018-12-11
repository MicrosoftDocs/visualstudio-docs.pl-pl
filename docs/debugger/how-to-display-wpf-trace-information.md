---
title: 'Porady: wyświetlanie informacji o śledzeniu WPF | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: be3c6859-06e1-459e-9fd0-46375b5f55ef
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 99fc861c627a094f9f5e4e67a6b034ecdd407688
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476227"
---
# <a name="how-to-display-wpf-trace-information"></a>Porady: wyświetlanie informacji o śledzeniu WPF
[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] można otrzymywać informacje o śledzeniu debugowania aplikacji WPF i wyświetlić te informacje w **dane wyjściowe** okna. Aby wyświetlić informacje o śledzeniu debugowania, można włączyć śledzenie WPF.  
  
 Można włączyć śledzenie WPF w pliku App.Config, lub programowo przy użyciu <xref:System.Diagnostics.PresentationTraceSources> klasy. Łatwiejszy sposób włączania śledzenia WPF polega na użyciu **opcje** okna. Śledzenie WPF dla aplikacji sieci web nie jest obsługiwana.  
  
### <a name="to-enable-or-customize-wpf-trace-information"></a>Aby włączyć lub dostosować informacje o śledzeniu WPF  
  
1.  Na **narzędzia** menu, wybierz opcję **opcje**.  
  
2.  W **opcje** otwarte okno dialogowe, w polu po lewej stronie, **debugowanie** węzła.  
  
3.  W obszarze **debugowanie**, kliknij przycisk **okno danych wyjściowych**.  
  
4.  W obszarze **ogólne ustawienia wyjściowej**, wybierz pozycję **wszystkie dane wyjściowe debugowania**.  
  
5.  W polu po prawej stronie Wyszukaj **ustawienia śledzenia WPF**.  
  
6.  Otwórz **ustawienia śledzenia WPF** węzła.  
  
7.  W obszarze **ustawienia śledzenia WPF**, kliknij kategorię ustawień, które chcesz włączyć (na przykład **powiązania danych**).  
  
     Formant listy rozwijanej w kolumnie jest wyświetlana ustawień obok pozycji **powiązania danych** lub kliknięcia niezależnie od kategorii.  
  
8.  Kliknij przycisk listy rozwijanej i wybierz typ informacji o śledzeniu, który chcesz wyświetlić: **wszystkie**, **krytyczny**, **błąd**, **ostrzeżenie**,  **Informacje o**, **pełne**, lub **ActivityTracing**.  
  
     **Krytyczne** umożliwia śledzenie tylko zdarzenia krytyczne.  
  
     **Błąd** włącza śledzenie zdarzeń błędu i krytyczne.  
  
     **Ostrzeżenie** umożliwia śledzenie krytyczna, błąd i ostrzeżenie zdarzenia.  
  
     **Informacje o** włącza śledzenie zdarzeń krytyczny, błąd, ostrzeżenie i informacje.  
  
     **Pełne** włącza śledzenie zdarzeń krytyczny, błąd, ostrzeżenie, informacje i pełne.  
  
     **ActivityTracing** włącza śledzenie zdarzeń Stop, Start Wstrzymaj, Transfer i wznowienia.  
  
     Aby uzyskać więcej informacji o te poziomy śledzenia informacji o znaczeniu, zobacz <xref:System.Diagnostics.SourceLevels>.  
  
9. Kliknij przycisk **OK**.  
  
### <a name="to-disable-wpf-trace-information"></a>Aby wyłączyć informacji o śledzeniu WPF  
  
1.  Na **narzędzia** menu, wybierz opcję **opcje**.  
  
2.  W **opcje** otwarte okno dialogowe, w polu po lewej stronie, **debugowanie** węzła.  
  
3.  W obszarze **debugowanie**, kliknij przycisk **okno danych wyjściowych**.  
  
4.  W polu po prawej stronie Wyszukaj **ustawienia śledzenia WPF**.  
  
5.  Otwórz **ustawienia śledzenia WPF** węzła.  
  
6.  W obszarze **ustawienia śledzenia WPF**, kliknij kategorię ustawień, które chcesz włączyć (na przykład **powiązania danych**).  
  
     Formant listy rozwijanej w kolumnie jest wyświetlana ustawień obok pozycji **powiązania danych** lub kliknięcia niezależnie od kategorii.  
  
7.  Kliknij przycisk listy rozwijanej i wybierz **poza**.  
  
8.  Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie WPF](../debugger/debugging-wpf.md)