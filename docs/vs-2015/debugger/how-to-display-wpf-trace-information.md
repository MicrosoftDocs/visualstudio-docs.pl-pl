---
title: 'Instrukcje: Wyświetlanie informacji o śledzeniu WPF | Dokumentacja firmy Microsoft'
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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60113785"
---
# <a name="how-to-display-wpf-trace-information"></a>Instrukcje: Wyświetlanie informacji o śledzeniu WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] można otrzymywać informacje o śledzeniu debugowania aplikacji WPF i wyświetlić te informacje w **dane wyjściowe** okna. Aby wyświetlić informacje o śledzeniu debugowania, można włączyć śledzenie WPF.  
  
 Możesz włączyć śledzenie WPF, w pliku App.Config, lub programowo przy użyciu <xref:System.Diagnostics.PresentationTraceSources> klasy. Łatwiejszy sposób monitorowania zdarzeń zachodzących WPF polega na użyciu **opcje** okna. Śledzenie WPF dla aplikacji sieci web nie jest obsługiwane.  
  
### <a name="to-enable-or-customize-wpf-trace-information"></a>Aby włączyć lub dostosować informacje o śledzeniu WPF  
  
1. Na **narzędzia** menu, wybierz opcję **opcje**.  
  
2. W **opcje** otwarte okno dialogowe, w polu po lewej stronie, **debugowanie** węzła.  
  
3. W obszarze **debugowanie**, kliknij przycisk **okno danych wyjściowych**.  
  
4. W obszarze **ogólne ustawienia danych wyjściowych**, wybierz opcję **wszystkie dane wyjściowe debugowania**.  
  
5. W polu po prawej stronie Wyszukaj **ustawienia śledzenia WPF**.  
  
6. Otwórz **ustawienia śledzenia WPF** węzła.  
  
7. W obszarze **ustawienia śledzenia WPF**, kliknij kategorię ustawień, które chcesz włączyć (na przykład **powiązanie danych**).  
  
     Kontrolka listy rozwijanej pojawia się w kolumnie ustawień obok **powiązanie danych** lub kliknięty niezależnie od kategorii.  
  
8. Kliknij przycisk listy rozwijanej i wybierz typ informacji śledzenia, które mają być wyświetlane: **Wszystkie**, **krytyczne**, **błąd**, **ostrzeżenie**, **informacji**, **pełne**, lub **ActivityTracing**.  
  
     **Krytyczne** umożliwia śledzenie tylko zdarzenia krytyczne.  
  
     **Błąd** włącza śledzenie zdarzeń krytycznych i błędów.  
  
     **Ostrzeżenie** umożliwia śledzenie krytyczna, błąd i ostrzeżenie zdarzenia.  
  
     **Informacje o** włącza śledzenie zdarzeń krytycznych, błąd, ostrzeżenie i informacje.  
  
     **Pełne** włącza śledzenie zdarzeń krytycznych, błąd, ostrzeżenie, informacje i pełne.  
  
     **ActivityTracing** włącza śledzenie Stop, uruchamianie, wstrzymywanie, transferu i Wznów zdarzeń.  
  
     Aby uzyskać więcej informacji na temat tych poziomów informacje o śledzeniu znaczenie, zobacz <xref:System.Diagnostics.SourceLevels>.  
  
9. Kliknij przycisk **OK**.  
  
### <a name="to-disable-wpf-trace-information"></a>Aby wyłączyć informacji o śledzeniu WPF  
  
1. Na **narzędzia** menu, wybierz opcję **opcje**.  
  
2. W **opcje** otwarte okno dialogowe, w polu po lewej stronie, **debugowanie** węzła.  
  
3. W obszarze **debugowanie**, kliknij przycisk **okno danych wyjściowych**.  
  
4. W polu po prawej stronie Wyszukaj **ustawienia śledzenia WPF**.  
  
5. Otwórz **ustawienia śledzenia WPF** węzła.  
  
6. W obszarze **ustawienia śledzenia WPF**, kliknij kategorię ustawień, które chcesz włączyć (na przykład **powiązanie danych**).  
  
     Kontrolka listy rozwijanej pojawia się w kolumnie ustawień obok **powiązanie danych** lub kliknięty niezależnie od kategorii.  
  
7. Kliknij przycisk listy rozwijanej i wybierz **poza**.  
  
8. Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie WPF](../debugger/debugging-wpf.md)
