---
title: 'Instrukcje: uruchamianie i kończenie zbierania danych wydajności | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.summarypage
helpviewer_keywords:
- profiling tools, launching sessions
- performance sessions, launching
- performance sessions, ending
- profiling tools, ending sessions
ms.assetid: 9f6eb0d5-d9e9-4bec-b627-445065610bce
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 15c6d6c904bbab27bac541894ed6cd4f9e1f80f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202677"
---
# <a name="how-to-start-and-end-performance-data-collection"></a>Instrukcje: rozpoczynanie i zatrzymywanie zbierania danych o wydajności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Należy dodać docelowy plik binarny, który ma być profilem sesji wydajności przed rozpoczęciem profilowania. Aby dodać obiekt docelowy, kliknij prawym przyciskiem myszy pozycję **obiekty docelowe** w **Eksplorator wydajności**, a następnie kliknij polecenie **Dodaj docelowy plik binarny**. W oknie dialogowym **Dodaj docelowy plik binarny** wybierz nazwę pliku, a następnie kliknij przycisk **Otwórz**. Zostanie dodany nowy plik binarny.  
  
### <a name="to-start-profiling"></a>Aby rozpocząć profilowanie  
  
1. Kliknij prawym przyciskiem myszy nazwę sesji wydajności w oknie **Eksplorator wydajności** i wybierz jedną z następujących opcji:  
  
    - **Uruchom przy użyciu profilowania** — uruchamia aplikację i od razu rozpoczyna profilowanie.  
  
    - **Uruchamianie przy użyciu wstrzymania profilowania** — uruchamia aplikację, ale nie rozpoczyna profilowania. Profilowanie można uruchomić, wybierając pozycję **Wznów zbieranie** w oknie **kontroli zbierania danych** . Aby uzyskać więcej informacji, zobacz [jak: Wstrzymywanie i wznawianie zbierania danych wydajności](../profiling/how-to-pause-and-resume-performance-data-collection.md).  
  
### <a name="to-end-profiling"></a>Aby zakończyć profilowanie  
  
- Preferowaną metodą zakończenia sesji profilowania jest zamknięcie aplikacji. Aby natychmiast zatrzymać profilowanie, na pasku narzędzi **Eksplorator wydajności** kliknij przycisk **Zatrzymaj**.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolowanie zbierania danych](../profiling/controlling-data-collection.md)   
 [Instrukcje: Wstrzymywanie i wznawianie zbierania danych wydajności](../profiling/how-to-pause-and-resume-performance-data-collection.md)
