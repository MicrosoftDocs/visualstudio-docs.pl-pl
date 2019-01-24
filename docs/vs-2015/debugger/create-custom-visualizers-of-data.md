---
title: Tworzenie niestandardowych Wizualizatorów danych | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.visualizer.troubleshoot
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f890277190b9b4d28873e1fe394abdcd95b8a3a6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54760478"
---
# <a name="create-custom-visualizers-of-data"></a>Tworzenie niestandardowych Wizualizatorów danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wizualizatory są składnikami [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] interfejs użytkownika debugera. A *Wizualizator* tworzy okno dialogowe lub inny interfejs do wyświetlania zmiennej lub obiektu w sposób, który jest odpowiedni do jego typu danych. Na przykład wizualizatora HTML interpretuje ciąg HTML i wyświetla wynik, jak będzie wyglądał w oknie przeglądarki; Wizualizator mapy bitowej interpretuje strukturę mapy bitowej i wyświetla grafiki, którą reprezentuje. Niektóre wizualizatorów umożliwiają modyfikowanie, a także wyświetlić dane.  
  
 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] Debugera zawiera sześć wizualizatorów standardowych. Są to tekst, HTML, XML i JSON wizualizatorów, z których wszystkie pracować nad obiektów w postaci ciągów; z wizualizatora drzewa WPF, do wyświetlania właściwości WPF drzewa wizualnego w obiekcie; i Wizualizator zestawu danych, która działa w przypadku obiektów DataSet, DataView i DataTable. Dodatkowe wizualizatorów mogą być dostępne do pobrania firmy Microsoft Corporation w przyszłości i są dostępne w innych firm i społeczności. Ponadto możesz napisać własne wizualizatorów i zainstalować je w [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] debugera.  
  
> [!NOTE]
>  W **Store** aplikacji, tylko standardowy tekst, HTML, XML i JSON wizualizatory są obsługiwane. Wizualizatory niestandardowe (utworzone przez użytkownika) nie są obsługiwane.  
  
 Wizualizatory są reprezentowane w debugerze przez ikonę lupy. Po wyświetleniu ikoną lupy w **DataTip**, w oknie zmiennych debugera, lub w **QuickWatch** okno dialogowe, możesz kliknąć ikonę lupy, aby wybrać odpowiedni typ danych wizualizatora odpowiedniego obiektu.  
  
 Wizualizatory nie są obsługiwane w Compact Framework.  
  
> [!NOTE]
>  Wizualizatory debugera wymagają większe uprawnienia niż jest to dozwolone przez aplikację do częściowego zaufania. W rezultacie wizualizatory nie są ładowane, gdy zostały zatrzymane w kod z częściowej relacji zaufania. Aby debugować za pomocą wizualizatora, należy uruchomić kod z pełnym zaufaniem.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Pisanie wizualizatora](../debugger/how-to-write-a-visualizer.md)  
  
 [Przewodnik: Pisanie wizualizatora w języku C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  
  
 [Instrukcje: Instalowanie wizualizatora](../debugger/how-to-install-a-visualizer.md)  
  
 [Instrukcje: Testowanie i debugowanie wizualizatora](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [Interfejs API wizualizatora — dokumentacja](../debugger/visualizer-api-reference.md)  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)
