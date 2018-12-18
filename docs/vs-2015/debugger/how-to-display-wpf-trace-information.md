---
title: 'Porady: wyświetlanie informacji o śledzeniu WPF | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 0a91d9f1f58a6905d50e14351bbbaf6fe732c60f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51771244"
---
# <a name="how-to-display-wpf-trace-information"></a>Porady: wyświetlanie informacji o śledzeniu WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] można otrzymywać informacje o śledzeniu debugowania aplikacji WPF i wyświetlić te informacje w **dane wyjściowe** okna. Aby wyświetlić informacje o śledzeniu debugowania, można włączyć śledzenie WPF.  
  
 Możesz włączyć śledzenie WPF, w pliku App.Config, lub programowo przy użyciu <xref:System.Diagnostics.PresentationTraceSources> klasy. Łatwiejszy sposób monitorowania zdarzeń zachodzących WPF polega na użyciu **opcje** okna. Śledzenie WPF dla aplikacji sieci web nie jest obsługiwane.  
  
### <a name="to-enable-or-customize-wpf-trace-information"></a>Aby włączyć lub dostosować informacje o śledzeniu WPF  
  
1.  Na **narzędzia** menu, wybierz opcję **opcje**.  
  
2.  W **opcje** otwarte okno dialogowe, w polu po lewej stronie, **debugowanie** węzła.  
  
3.  W obszarze **debugowanie**, kliknij przycisk **okno danych wyjściowych**.  
  
4.  W obszarze **ogólne ustawienia danych wyjściowych**, wybierz opcję **wszystkie dane wyjściowe debugowania**.  
  
5.  W polu po prawej stronie Wyszukaj **ustawienia śledzenia WPF**.  
  
6.  Otwórz **ustawienia śledzenia WPF** węzła.  
  
7.  W obszarze **ustawienia śledzenia WPF**, kliknij kategorię ustawień, które chcesz włączyć (na przykład **powiązanie danych**).  
  
     Kontrolka listy rozwijanej pojawia się w kolumnie ustawień obok **powiązanie danych** lub kliknięty niezależnie od kategorii.  
  
8.  Kliknij przycisk listy rozwijanej i wybierz typ informacji śledzenia, które mają być wyświetlane: **wszystkich**, **krytyczny**, **błąd**, **ostrzeżenie**,  **Informacje o**, **pełne**, lub **ActivityTracing**.  
  
     **Krytyczne** umożliwia śledzenie tylko zdarzenia krytyczne.  
  
     **Błąd** włącza śledzenie zdarzeń krytycznych i błędów.  
  
     **Ostrzeżenie** umożliwia śledzenie krytyczna, błąd i ostrzeżenie zdarzenia.  
  
     **Informacje o** włącza śledzenie zdarzeń krytycznych, błąd, ostrzeżenie i informacje.  
  
     **Pełne** włącza śledzenie zdarzeń krytycznych, błąd, ostrzeżenie, informacje i pełne.  
  
     **ActivityTracing** włącza śledzenie Stop, uruchamianie, wstrzymywanie, transferu i Wznów zdarzeń.  
  
     Aby uzyskać więcej informacji na temat tych poziomów informacje o śledzeniu znaczenie, zobacz <xref:System.Diagnostics.SourceLevels>.  
  
9. Kliknij przycisk **OK**.  
  
### <a name="to-disable-wpf-trace-information"></a>Aby wyłączyć informacji o śledzeniu WPF  
  
1.  Na **narzędzia** menu, wybierz opcję **opcje**.  
  
2.  W **opcje** otwarte okno dialogowe, w polu po lewej stronie, **debugowanie** węzła.  
  
3.  W obszarze **debugowanie**, kliknij przycisk **okno danych wyjściowych**.  
  
4.  W polu po prawej stronie Wyszukaj **ustawienia śledzenia WPF**.  
  
5.  Otwórz **ustawienia śledzenia WPF** węzła.  
  
6.  W obszarze **ustawienia śledzenia WPF**, kliknij kategorię ustawień, które chcesz włączyć (na przykład **powiązanie danych**).  
  
     Kontrolka listy rozwijanej pojawia się w kolumnie ustawień obok **powiązanie danych** lub kliknięty niezależnie od kategorii.  
  
7.  Kliknij przycisk listy rozwijanej i wybierz **poza**.  
  
8.  Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie WPF](../debugger/debugging-wpf.md)



