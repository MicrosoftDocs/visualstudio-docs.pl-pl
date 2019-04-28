---
title: Architektura wizualizatora | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 6aad395f-7170-4d9e-b2b8-a5faf453380e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3064f387c0a6233b1cd38c4ed81680ef7991abd4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62901156"
---
# <a name="visualizer-architecture"></a>Architektura wizualizatora
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

 Zwróć uwagę, dostawcy obiektów można użyć dowolnego <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> lub <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>. Albo interfejsu API powoduje wywołanie <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A> źródła obiektu. Wywołanie <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A?displayProperty=fullName> wypełnia <xref:System.IO.Stream?displayProperty=fullName>, która reprezentuje serializowane postaci obiekt, który jest wizualizowanego.

 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> deserializuje dane z powrotem do obiektu formularza, który następnie można wyświetlić w interfejsie użytkownika, możesz utworzyć przy użyciu <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> wypełnia dane pierwotne `Stream`, które należy wykonać deserializacji samodzielnie. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> działa przez wywołanie metody <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> można pobrać Zserializowany `Stream`, a następnie deserializacji danych. Użyj <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> gdy obiekt jest niemożliwa, .NET i wymaga niestandardowej serializacji. W takim przypadku konieczne jest również przesłonięcie <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.Serialize%2A?displayProperty=fullName> metody.

 Jeśli tworzysz Wizualizator tylko do odczytu, komunikacja jednokierunkowa przy użyciu <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> lub <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A> jest wystarczająca. Jeśli tworzysz visualizer, który obsługuje edycji obiektów danych, należy wykonać więcej. Musi umożliwiać odesłania obiektu danych od dostawcy obiektu do źródłowego obiektu również. W poniższej tabeli przedstawiono dostawcy obiektów i interfejsów API źródła obiektu do tego celu:

|Obiekt dostawcy|Źródło obiektu|
|---------------------|-------------------|
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A><br /><br /> —lub—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>|

 Zwróć uwagę, ponownie, że istnieją dwa interfejsy API, których można użyć dostawcy obiektów. Dane są zawsze wysyłane z dostawcy obiektów do źródła obiektu jako `Stream`, ale <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> wymaga, że serializacji obiektu do `Stream` samodzielnie.

 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A> pobiera obiekt, który podasz, serializuje do `Stream`, następnie wywołuje <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> wysyłać `Stream` do <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>.

 Przy użyciu jednej z metod Zastąp tworzy nowy obiekt danych w debugowanym obiekcie, który zastępuje wizualizowanego obiektu. Jeśli chcesz zmienić zawartość oryginalnego obiektu bez zastąpienia, użyj jednej z metod transferu, pokazano w poniższej tabeli. Te interfejsy API transferu danych w obu kierunkach w tym samym czasie, bez zastępowania obiektu, który jest wizualizowanego:

|Obiekt dostawcy|Źródło obiektu|
|---------------------|-------------------|
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferData%2A><br /><br /> —lub—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.TransferData%2A>|

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Pisanie wizualizatora](/visualstudio/debugger/create-custom-visualizers-of-data)
- [Przewodnik: Pisanie wizualizatora w języku C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Przewodnik: Pisanie wizualizatora w języku Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [Przewodnik: Pisanie wizualizatora w języku Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [Zagadnienia dotyczące zabezpieczeń wizualizatora](../debugger/visualizer-security-considerations.md)