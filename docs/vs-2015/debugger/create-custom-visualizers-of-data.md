---
title: Tworzenie niestandardowych wizualizatorów danych | Microsoft Docs
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
ms.openlocfilehash: 50df868f0e01d49d4c49bccae32d743d5291a066
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64820661"
---
# <a name="create-custom-visualizers-of-data"></a>Tworzenie niestandardowych wizualizatorów danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wizualizatory to składniki [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] interfejsu użytkownika debugera. *Wizualizator* tworzy okno dialogowe lub inny interfejs do wyświetlania zmiennej lub obiektu w sposób, który jest odpowiedni dla typu danych. Na przykład wizualizator HTML interpretuje ciąg HTML i wyświetla wynik w postaci, w jakiej pojawił się w oknie przeglądarki. wizualizator mapy bitowej interpretuje strukturę mapy bitowej i wyświetla grafikę, którą reprezentuje. Niektóre Wizualizatory umożliwiają modyfikowanie, a także wyświetlanie danych.  
  
 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]Debuger zawiera sześć standardowych wizualizatorów. Są to Wizualizatory tekstu, HTML, XML i JSON, które działają na obiektach ciągów; wizualizator drzewa WPF, służący do wyświetlania właściwości drzewa wizualnego obiektu WPF; i wizualizator zestawu danych, który działa dla obiektów DataSet, DataView i DataTable. Dodatkowe Wizualizatory mogą być dostępne do pobrania od firmy Microsoft Corporation w przyszłości i są dostępne w innych firmach i w społeczności. Ponadto można napisać własne Wizualizatory i zainstalować je w [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] debugerze.  
  
> [!NOTE]
> W aplikacjach ze **sklepu** obsługiwane są tylko Wizualizatory tekstu standardowego, HTML, XML i JSON. Wizualizacje niestandardowe (utworzone przez użytkownika) nie są obsługiwane.  
  
 Wizualizatory są reprezentowane w debugerze przez ikonę lupy. Gdy zobaczysz ikonę lupy w **etykietki danych**, w oknie zmiennych debugera lub w oknie dialogowym **QuickWatch** , możesz kliknąć lupę, aby wybrać wizualizator odpowiedni dla typu danych odpowiadającego obiektu.  
  
 Wizualizatory nie są obsługiwane w środowisku kompaktowym.  
  
> [!NOTE]
> Wizualizatory debugera wymagają większych uprawnień niż jest to dozwolone w przypadku aplikacji częściowo zaufanej. W związku z tym Wizualizatory nie są ładowane po zatrzymaniu w kodzie z częściowym zaufaniem. Aby debugować przy użyciu wizualizatora, należy uruchomić kod z pełnym zaufaniem.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Porady: pisanie wizualizatora](../debugger/how-to-write-a-visualizer.md)  
  
 [Wskazówki: Pisanie wizualizatora w C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  
  
 [Instrukcje: Instalowanie wizualizatora](../debugger/how-to-install-a-visualizer.md)  
  
 [Instrukcje: testowanie i debugowanie wizualizatora](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [Wizualizator API — Odwołanie](../debugger/visualizer-api-reference.md)  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)
