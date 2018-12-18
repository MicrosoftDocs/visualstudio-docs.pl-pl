---
title: Architektura wizualizatora | Dokumentacja firmy Microsoft
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
ms.assetid: 6aad395f-7170-4d9e-b2b8-a5faf453380e
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7a3255b8e8b91f074308a0238719f26af6cf665
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736162"
---
# <a name="visualizer-architecture"></a>Architektura wizualizatora
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Architektura wizualizatora debuger ma dwie części:  
  
- *Debugera po stronie* jest uruchamiany w ramach debugera programu Visual Studio. Kod po stronie debugera tworzy i wyświetla interfejsu użytkownika dla usługi wizualizatora.  
  
- *Po stronie debugowanego obiektu* jest uruchamiany w ramach procesu programu Visual Studio debuguje ( *obiekt debugowany*).  
  
  Wizualizatora jest składnikiem debugera, które umożliwiają debugerowi wyświetlić (*wizualizować*) zawartości obiektu danych w postaci zrozumiałe i zrozumiałej. Niektóre wizualizatorów obsługuje także edytować obiekt danych. Pisząc wizualizatory niestandardowe, można rozszerzyć debuger mógł obsłużyć własne niestandardowe typy danych.  
  
  Obiekt danych, aby być wizualizowane znajduje się w debugowanym procesie ( *obiekt debugowany* procesu). Interfejs użytkownika, który spowoduje wyświetlenie danych jest tworzony w ramach procesu debugera programu Visual Studio:  
  
|Proces w debugerze|Obiekt debugowany proces|  
|----------------------|----------------------|  
|Interfejs użytkownika (DataTips, okno czujki QuickWatch) debugera|Można wywołać obiektu danych|  
  
 Aby zwizualizować obiekt danych w ramach interfejsu debugera, należy kodu do komunikowania się między dwoma procesami. W związku z tym, architektura wizualizatora składa się z dwóch części: *debugera po stronie* kodu i *po stronie debugowanego obiektu* kodu.  
  
 Kod po stronie debuger umożliwia utworzenie własnego interfejsu użytkownika, który może być wywoływany przy użyciu interfejsu debugera, takie jak etykietki danych, okno czujki lub QuickWatch. Interfejs Wizualizator jest tworzona przy użyciu <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> klasy i <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> interfejsu. Tak jak wszystkie interfejsy API wizualizatora, DialogDebuggerVisualizer i IDialogVisualizerService znajdują się w <xref:Microsoft.VisualStudio.DebuggerVisualizers> przestrzeni nazw.  
  
|Po stronie debugera|Po stronie debugowanego obiektu|  
|-------------------|-------------------|  
|Klasa DialogDebuggerVisualizer<br /><br /> Interfejs IDialogVisualizerService|Obiekt danych|  
  
 Interfejs użytkownika pobiera dane, które mają być wizualizowane od dostawcy obiektu, który znajduje się na stronie debugera:  
  
|Po stronie debugera|Po stronie debugowanego obiektu|  
|-------------------|-------------------|  
|Klasa DialogDebuggerVisualizer<br /><br /> Interfejs IDialogVisualizerService|Obiekt danych|  
|Obiekt dostawcy (implementuje <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>)||  
  
 Brak odpowiedniego obiektu po stronie debugowanego obiektu o nazwie źródła obiektu:  
  
|Po stronie debugera|Po stronie debugowanego obiektu|  
|-------------------|-------------------|  
|Klasa DialogDebuggerVisualizer<br /><br /> Interfejs IDialogVisualizerService|Obiekt danych|  
|Obiekt dostawcy (implementuje <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>)|Obiekt źródłowy (pochodną <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>)|  
  
 Dostawca obiektu udostępnia dane obiektu, który ma być wizualizowane do Wizualizator interfejsu użytkownika. Dostawca obiekt otrzymuje dane obiektu ze źródła obiektu. Obiekt dostawcy i źródła obiektu zapewniają interfejsy API w celu przekazywania danych obiektu między po stronie debugera i debugee.  
  
 Wizualizator co należy uzyskać obiekt danych, aby być wizualizowane. W poniższej tabeli przedstawiono odpowiednie interfejsy API, w tym celu użyć obiektu dostawcy i źródła obiektu:  
  
|Obiekt dostawcy|Źródło obiektu|  
|---------------------|-------------------|  
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A><br /><br /> —lub—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A>|  
  
 Zwróć uwagę, dostawcy obiektów można użyć dowolnego <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> lub <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>. Albo interfejsu API powoduje wywołanie <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A> źródła obiektu. Wywołanie <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A?displayProperty=fullName> wypełnia [System.IO.Stream] (<!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  -->), która reprezentuje serializowane postaci obiekt, który jest wizualizowanego.  
  
 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> deserializuje dane z powrotem do obiektu formularza, który następnie można wyświetlić w interfejsie użytkownika, możesz utworzyć przy użyciu <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> wypełnia dane pierwotne <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  -->, które należy wykonać deserializacji samodzielnie. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> działa przez wywołanie metody <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> można pobrać Zserializowany <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  -->, a następnie deserializacji danych. Użyj <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> gdy obiekt jest niemożliwa, .NET i wymaga niestandardowej serializacji. W takim przypadku konieczne jest również przesłonięcie <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.Serialize%2A?displayProperty=fullName> metody.  
  
 Jeśli tworzysz Wizualizator tylko do odczytu, komunikacja jednokierunkowa przy użyciu <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> lub <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A> jest wystarczająca. Jeśli tworzysz visualizer, który obsługuje edycji obiektów danych, należy wykonać więcej. Musi umożliwiać odesłania obiektu danych od dostawcy obiektu do źródłowego obiektu również. W poniższej tabeli przedstawiono dostawcy obiektów i interfejsów API źródła obiektu do tego celu:  
  
|Obiekt dostawcy|Źródło obiektu|  
|---------------------|-------------------|  
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A><br /><br /> —lub—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>|  
  
 Zwróć uwagę, ponownie, że istnieją dwa interfejsy API, których można użyć dostawcy obiektów. Dane są zawsze wysyłane z dostawcy obiektów do źródła obiektu jako <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  -->, ale <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> wymaga, że serializacji obiektu do <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  --> samodzielnie.  
  
 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A> pobiera obiekt, który podasz, serializuje do <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  -->, następnie wywołuje <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> wysyłać <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  --> do <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>.  
  
 Przy użyciu jednej z metod Zastąp tworzy nowy obiekt danych w debugowanym obiekcie, który zastępuje wizualizowanego obiektu. Jeśli chcesz zmienić zawartość oryginalnego obiektu bez zastąpienia, użyj jednej z metod transferu, pokazano w poniższej tabeli. Te interfejsy API transferu danych w obu kierunkach w tym samym czasie, bez zastępowania obiektu, który jest wizualizowanego:  
  
|Obiekt dostawcy|Źródło obiektu|  
|---------------------|-------------------|  
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferData%2A><br /><br /> —lub—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.TransferData%2A>|  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: pisanie wizualizatora](../debugger/how-to-write-a-visualizer.md)   
 [Wskazówki: Pisanie wizualizatora w języku C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)   
 [Wskazówki: Pisanie wizualizatora w języku Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)   
 [Wskazówki: Pisanie wizualizatora w języku Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)   
 [Zagadnienia dotyczące zabezpieczeń wizualizatora](../debugger/visualizer-security-considerations.md)



