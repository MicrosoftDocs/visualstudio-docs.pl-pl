---
title: Tworzenie niestandardowych wizualizatorów danych | Microsoft Docs
ms.date: 05/27/2020
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e184507415810f64060b0d2b2e92a825d642d2e
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85280879"
---
# <a name="create-custom-data-visualizers"></a>Tworzenie niestandardowych wizualizatorów danych

 *Wizualizator* jest częścią [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] interfejsu użytkownika debugera, który wyświetla zmienną lub obiekt w sposób odpowiedni dla typu danych. Na przykład wizualizator HTML interpretuje ciąg HTML i wyświetla wynik w postaci, w jakiej pojawił się w oknie przeglądarki. Wizualizator mapy bitowej interpretuje strukturę mapy bitowej i wyświetla grafikę, którą reprezentuje. Niektóre Wizualizatory pozwalają modyfikować, a także wyświetlać dane.

 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]Debuger zawiera sześć standardowych wizualizatorów. Wizualizatory tekstu, HTML, XML i JSON działają na obiektach ciągu. Wizualizator drzewa WPF wyświetla właściwości drzewa wizualnego obiektu WPF. Wizualizator zestawu danych działa dla obiektów DataSet, DataView i DataTable.

Więcej wizualizatorów może być dostępnych do pobrania przez firmę Microsoft, strony trzecie i społeczność. Możesz również napisać własne Wizualizatory i zainstalować je w [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] debugerze.

W debugerze wizualizator jest reprezentowany przez ikonę lupy ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Ikona wizualizatora"). Możesz wybrać ikonę w **etykietki danych**, oknie **czujki** debugera lub **QuickWatch** okno dialogowe, a następnie wybrać odpowiedni wizualizator dla odpowiedniego obiektu.

## <a name="write-custom-visualizers"></a>Napisz niestandardowe Wizualizatory

 > [!NOTE]
 > Aby utworzyć wizualizację niestandardową dla kodu natywnego, zobacz przykład [wizualizatora natywnego debugera oprogramowania SQLite](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer) . Wizualizacje niestandardowe nie są obsługiwane w przypadku aplikacji platformy UWP i Windows 8. x.

Można napisać niestandardowy wizualizator dla obiektu dowolnej zarządzanej klasy z wyjątkiem dla <xref:System.Object> i <xref:System.Array> .

Architektura wizualizatora debugera ma dwie części:

- *Strona debugera* działa w debugerze programu Visual Studio, a następnie tworzy i wyświetla interfejs użytkownika wizualizatora.

- *Po stronie debugowanego obiektu* w procesie programu Visual Studio jest debugowane ( *debugowanego obiektu*). Obiekt danych do wizualizacji (na przykład obiekt String) istnieje w procesie debugowanego obiektu. Po stronie debugowanego obiektu wysyła obiekt do strony debugera, co spowoduje wyświetlenie go w utworzonym interfejsie użytkownika.

Po stronie debugera odbiera obiekt danych od *dostawcy obiektów* , który implementuje <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> interfejs. Po stronie debugowanego obiektu wysyła obiekt za pośrednictwem *źródła obiektu*, który pochodzi od <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> .

Dostawca obiektów może również wysyłać dane z powrotem do źródła obiektów, co umożliwia pisanie wizualizatora, który może edytować dane. Można zastąpić dostawcę obiektów, aby komunikować się z ewaluatora wyrażeń i źródłem obiektu.

Po stronie debugowanego obiektu i debugerze komunikują się ze sobą za pomocą <xref:System.IO.Stream> metod serializacji obiektu danych do <xref:System.IO.Stream> i deserializacji z <xref:System.IO.Stream> powrotem do obiektu danych.

Wizualizator dla typu ogólnego można napisać tylko wtedy, gdy typ jest typem otwartym. To ograniczenie jest takie samo jak w przypadku ograniczenia przy użyciu `DebuggerTypeProxy` atrybutu. Aby uzyskać szczegółowe informacje, zobacz [Korzystanie z atrybutu DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md).

Wizualizacje niestandardowe mogą mieć uwagi dotyczące zabezpieczeń. Zobacz [zagadnienia dotyczące zabezpieczeń wizualizatora](../debugger/visualizer-security-considerations.md).

Poniższe kroki zapewniają ogólny przegląd tworzenia wizualizatora. Aby uzyskać szczegółowe instrukcje, zobacz [Przewodnik: pisanie wizualizatora w języku C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md) lub [Instruktaż: pisanie wizualizatora w Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md).

### <a name="to-create-the-debugger-side"></a>Aby utworzyć stronę debugera

Aby utworzyć interfejs użytkownika wizualizatora po stronie debugera, należy utworzyć klasę, która dziedziczy z <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> i zastąpić <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> metodę w celu wyświetlenia interfejsu. Możesz użyć <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> , aby wyświetlić formularze systemu Windows, okna dialogowe i kontrolki w wizualizatorze.

1. Użyj <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> metod, aby uzyskać wizualizację obiektu po stronie debugera.

1. Utwórz klasę, która dziedziczy z <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> .

1. Zastąp <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> metodę, aby wyświetlić interfejs. Użyj <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> metod, aby wyświetlić formularze systemu Windows, okna dialogowe i kontrolki w interfejsie.

4. Zastosuj <xref:System.Diagnostics.DebuggerVisualizerAttribute> , wskazując, że wizualizator ma być wyświetlany ( <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> ).

### <a name="to-create-the-visualizer-object-source-for-the-debuggee-side"></a>Aby utworzyć źródło obiektu wizualizatora dla strony debugowanego obiektu

W kodzie po stronie debugera, Edytuj <xref:System.Diagnostics.DebuggerVisualizerAttribute> , nadając jej typ do wizualizacji (Źródło obiektów debugowanego obiektu) ( <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> ). `Target`Właściwość ustawia źródło obiektu. W przypadku pominięcia źródła obiektów wizualizator użyje domyślnego źródła obiektu.

::: moniker range=">=vs-2019"
Kod po stronie debugowanego obiektu zawiera źródło obiektu, które umożliwia wizualizację. Obiekt danych może przesłonić metody <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> . Biblioteka DLL po stronie debugowanego obiektu jest niezbędna, jeśli chcesz utworzyć autonomiczny wizualizator.
::: moniker-end

W kodzie debugowanego obiektu:

- Aby umożliwić wizualizatorowi edytowanie obiektów danych, źródło obiektu musi dziedziczyć z <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> i zastąpić `TransferData` `CreateReplacementObject` metody lub.

- Jeśli musisz obsługiwać wiele elementów docelowych wizualizatora, możesz użyć następujących monikerów platformy docelowej (TFMs) w pliku projektu po stronie debugowanego obiektu.

   ```xml
   <TargetFrameworks>net20;netstandard2.0;netcoreapp2.0</TargetFrameworks>
   ```

   Są to jedyne obsługiwane TFMs.

## <a name="see-also"></a>Zobacz też

- [Przewodnik: Pisanie wizualizatora w języku C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Przewodnik: Pisanie wizualizatora w języku Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [Instrukcje: instalowanie wizualizatora](../debugger/how-to-install-a-visualizer.md)
- [Instrukcje: testowanie i debugowanie wizualizatora](../debugger/how-to-test-and-debug-a-visualizer.md)
- [Dokumentacja interfejsu API wizualizatora](../debugger/visualizer-api-reference.md)
- [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)