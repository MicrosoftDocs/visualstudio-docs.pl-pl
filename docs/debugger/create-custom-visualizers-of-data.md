---
title: Tworzenie danych niestandardowych wizualizatorów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/07/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.visualizer.troubleshoot
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4c5f505bfa8032b0f7d59f348835e1e4969b2648
ms.sourcegitcommit: 6a955a2d179cd0e137942389f940d9fcbbe125de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2018
ms.locfileid: "51607825"
---
# <a name="create-custom-data-visualizers"></a>Tworzenie danych niestandardowych wizualizatorów 
 A *Wizualizator* jest częścią [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] interfejs użytkownika debugera, który wyświetla zmiennej lub obiektu w sposób odpowiedni do jego typu danych. Na przykład wizualizatora HTML interpretuje ciąg HTML i wyświetla wynik, jak będzie wyglądał w oknie przeglądarki. Wizualizator mapy bitowej interpretuje strukturę mapy bitowej i wyświetla grafiki, którą reprezentuje. Niektóre wizualizatorów umożliwiają modyfikowanie także wyświetlić dane.

 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] Debugera zawiera sześć wizualizatorów standardowych. Tekst, HTML, XML i JSON wizualizatorów pracować nad obiektów w postaci ciągów. Z wizualizatora drzewa WPF zostaną wyświetlone jej właściwości drzewa wizualnego obiektu WPF. Wizualizator zestawu danych działa w przypadku obiektów DataSet, DataView i DataTable. 

Więcej wizualizatorów mogą być dostępne do pobrania firmy Microsoft, innych firm i społeczności. Można również napisać własne wizualizatorów i zainstalować je w [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] debugera.

W debugerze, wizualizatora jest reprezentowany przez ikonę lupy ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "ikonę Wizualizator"). Możesz wybrać ikonę w **DataTip**, Debuger **Obejrzyj** oknie lub **QuickWatch** okno dialogowe, a następnie wybierz odpowiednią Wizualizator dla odpowiedniego obiektu.

## <a name="write-custom-visualizers"></a>Pisanie niestandardowych wizualizatorów

 > [!NOTE]
 > Aby utworzyć niestandardowego wizualizatora dla kodu natywnego, zobacz [uproszczony Wizualizator debugowania natywnego oprogramowania SQLite](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer) próbki. Wizualizatory niestandardowe nie są obsługiwane dla aplikacji 8.x platformy uniwersalnej systemu Windows i Windows.

Możesz napisać niestandardowego wizualizatora obiektu klasy zarządzanej z wyjątkiem <xref:System.Object> i <xref:System.Array>.  
  
Architektura wizualizatora debuger ma dwie części:  
  
- *Debugera po stronie* jest uruchamiany w ramach debugera programu Visual Studio i tworzy i wyświetla Wizualizator interfejsu użytkownika.  
  
- *Po stronie debugowanego obiektu* jest uruchamiany w ramach procesu programu Visual Studio debuguje ( *obiekt debugowany*). Obiekt danych do wizualizacji (np. obiekt ciągu) istnieje w obiekcie debugowanym procesie. Po stronie debugowanego obiektu wysyła po stronie debugera i wyświetla go w interfejsie użytkownika, które można utworzyć obiektu.  

Po stronie debugera, otrzymuje obiekt danych z *dostawcy obiektów* implementującej <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> interfejsu. Po stronie debugowanego obiektu wysyła za pośrednictwem *źródła obiektu*, który pochodzi od <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>. 

Dostawcy obiektów można również wysyłać dane z powrotem do źródła obiektu, co umożliwia pisanie wizualizatora, który można edytować dane. Możesz zastąpić dostawcy obiektów na komunikowanie się z Ewaluator wyrażeń i źródła obiektu.  
  
Po stronie debugowanego obiektu i debugera, komunikują się ze sobą za pośrednictwem <xref:System.IO.Stream> do obiektu metod, które serializacji danych <xref:System.IO.Stream> i deserializacji <xref:System.IO.Stream> do obiektu danych.  

Tylko wtedy, gdy typ jest typem otwartym, można napisać Wizualizator dla typu ogólnego. To ograniczenie jest taka sama jak wartość ograniczenia, korzystając z `DebuggerTypeProxy` atrybutu. Aby uzyskać więcej informacji, zobacz [używanie atrybutu DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md).  
  
Wizualizatory niestandardowe mogą mieć zagadnienia związane z zabezpieczeniami. Zobacz [zagadnienia dotyczące zabezpieczeń internetowych](../debugger/visualizer-security-considerations.md).  
  
Poniższe kroki zapewniają ogólne omówienie tworzenia wizualizatora. Aby uzyskać szczegółowe instrukcje, zobacz [wskazówki: pisanie wizualizatora w C# ](../debugger/walkthrough-writing-a-visualizer-in-csharp.md) lub [wskazówki: pisanie wizualizatora w języku Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md).  
  
### <a name="to-create-the-debugger-side"></a>Aby utworzyć po stronie debugera  
  
Aby tworzymy interfejs użytkownika wizualizatora po stronie debugera, należy utworzyć klasę, która dziedziczy po elemencie <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>i zastępowania <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> metodę w celu wyświetlenia interfejsu. Możesz użyć <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> do wyświetlenia w wizualizatorze użytkownika formularzy, okien dialogowych i formantów Windows.  
  
1.  Użyj <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> metody w celu uzyskania wizualizowanego obiektu po stronie debugera.  
  
1.  Utwórz klasę, która dziedziczy z <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>.  
  
1.  Zastąp <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> metodę w celu wyświetlenia interfejsu. Użyj <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> metody służące do wyświetlania formularzy Windows, okien dialogowych i formantów w interfejsie.  
  
4.  Zastosuj <xref:System.Diagnostics.DebuggerVisualizerAttribute>, nadając mu Wizualizator w celu wyświetlenia (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>).  
  
### <a name="to-create-the-debuggee-side"></a>Aby utworzyć po stronie debugowanego obiektu  
  
Należy określić kod po stronie debugowanego obiektu za pomocą <xref:System.Diagnostics.DebuggerVisualizerAttribute>.  
  
1.  Zastosuj <xref:System.Diagnostics.DebuggerVisualizerAttribute>, nadając mu wizualizatora (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) i źródła obiektu (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>). Jeżeli pominięto źródła obiektu wizualizatora użyje domyślnego źródła obiektu.  
  
1.  Aby umożliwić Wizualizator Edytuj również wyświetlane obiekty danych, należy zastąpić `TransferData` lub `CreateReplacementObject` metody z <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.   
  
## <a name="see-also"></a>Zobacz także
  
 [Przewodnik: pisanie wizualizatora w języku C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  

 [Przewodnik: pisanie wizualizatora w języku Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)  
  
 [Instrukcje: instalowanie wizualizatora](../debugger/how-to-install-a-visualizer.md)  
  
 [Instrukcje: testowanie i debugowanie wizualizatora](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [Interfejs API wizualizatora — dokumentacja](../debugger/visualizer-api-reference.md)  
  
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)