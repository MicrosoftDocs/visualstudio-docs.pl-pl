---
title: Architektura wizualizatora | Microsoft Docs
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
ms.openlocfilehash: 5c92723a1b6abb371b44f1793f9ea5b1f8ad3bca
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728478"
---
# <a name="visualizer-architecture"></a>Architektura wizualizatora
Architektura wizualizatora debugera ma dwie części:

- *Strona debugera* działa w debugerze programu Visual Studio. Kod po stronie debugera tworzy i wyświetla interfejs użytkownika wizualizatora.

- *Po stronie debugowanego obiektu* w procesie programu Visual Studio jest debugowane ( *debugowanego obiektu*).

  Wizualizator to składnik debugera, który umożliwia debugerowi wyświetlanie (*wizualizowanie*) zawartości obiektu danych w zrozumiałej, zrozumiałej postaci. Niektóre Wizualizatory obsługują również Edytowanie obiektu danych. Pisząc niestandardowe wizualizacje, możesz rozwinąć debuger, aby obsługiwał własne niestandardowe typy danych.

  Obiekt danych do wizualizacji znajduje się w debugowanym procesie (proces *debugowanego obiektu* ). Interfejs użytkownika, który będzie wyświetlał dane, zostanie utworzony w ramach procesu debugera programu Visual Studio:

|Proces debugera|Proces debugowanego obiektu|
|----------------------|----------------------|
|Debuger interfejsu użytkownika (etykietki danych, okno czujki, QuickWatch)|Obiekt danych do wizualizacji|

 Aby wizualizować obiekt danych w interfejsie debugera, potrzebny jest kod do komunikacji między dwoma procesami. W związku z tym Architektura wizualizatora składa się z dwóch części: kodu *bocznego debugera* i kodu *po stronie debugowanego obiektu* .

 Kod po stronie debugera tworzy własny interfejs użytkownika, który może być wywoływany z interfejsu debugera, takiego jak etykietki danych, okno czujki lub QuickWatch. Interfejs wizualizatora jest tworzony przy użyciu klasy <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> i interfejsu <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService>. Podobnie jak wszystkie interfejsy API wizualizatora, DialogDebuggerVisualizer i IDialogVisualizerService znajdują się w przestrzeni nazw <xref:Microsoft.VisualStudio.DebuggerVisualizers>.

|Strona debugera|Debugowanego obiektu|
|-------------------|-------------------|
|Klasa DialogDebuggerVisualizer<br /><br /> IDialogVisualizerService, interfejs|Obiekt danych|

 Interfejs użytkownika pobiera dane do wizualizacji od dostawcy obiektów, który istnieje po stronie debugera:

|Strona debugera|Debugowanego obiektu|
|-------------------|-------------------|
|Klasa DialogDebuggerVisualizer<br /><br /> IDialogVisualizerService, interfejs|Obiekt danych|
|Dostawca obiektów (implementuje <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>)||

 Po stronie debugowanego obiektu o nazwie źródło obiektu istnieje odpowiedni obiekt:

|Strona debugera|Debugowanego obiektu|
|-------------------|-------------------|
|Klasa DialogDebuggerVisualizer<br /><br /> IDialogVisualizerService, interfejs|Obiekt danych|
|Dostawca obiektów (implementuje <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>)|Źródło obiektu (pochodzące z <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>)|

 Dostawca obiektów udostępnia dane obiektów, które mają być wizualizacje w interfejsie użytkownika wizualizatora. Dostawca obiektów pobiera dane obiektu ze źródła obiektu. Dostawca obiektów i źródło obiektów zapewniają interfejsy API do przekazywania danych obiektu między stroną debugera a stroną debugee.

 Każdy wizualizator musi pobrać obiekt danych do wizualizacji. W poniższej tabeli przedstawiono interfejsy API odpowiednie do użycia przez dostawcę obiektów i źródło obiektów:

|Dostawca obiektów|Źródło obiektu|
|---------------------|-------------------|
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A><br /><br /> —lub—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A>|

 Zwróć uwagę, że dostawca obiektów może używać obu <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> lub <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>. Interfejs API powoduje wywołanie <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A> w źródle obiektu. Wywołanie <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A?displayProperty=fullName> wypełnia <xref:System.IO.Stream?displayProperty=fullName>, który reprezentuje serializowaną postać wizualizacji obiektu.

 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> deserializacji danych z powrotem do formularza obiektu, który można następnie wyświetlić w interfejsie użytkownika utworzonym przy użyciu <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> wypełnia dane jako pierwotne `Stream`, które należy zdeserializować samodzielnie. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> działa przez wywoływanie <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> w celu uzyskania serializowanych `Stream`, a następnie deserializacji danych. Użyj <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName>, gdy obiekt nie jest możliwy do serializacji przez platformę .NET i wymaga serializacji niestandardowej. W takim przypadku należy również zastąpić metodę <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.Serialize%2A?displayProperty=fullName>.

 Jeśli tworzysz wizualizator tylko do odczytu, wystarczy jednokierunkową komunikację z <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> lub <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>. Jeśli tworzysz wizualizator, który obsługuje edytowanie obiektów danych, musisz wykonać więcej czynności. Musisz być w stanie wysłać obiekt danych z dostawcy obiektów z powrotem do źródła obiektu. W poniższej tabeli przedstawiono dostawcę obiektów i interfejsy API źródła obiektów używane w tym celu:

|Dostawca obiektów|Źródło obiektu|
|---------------------|-------------------|
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A><br /><br /> —lub—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>|

 Zwróć uwagę, że istnieją dwa interfejsy API, z których może korzystać dostawca obiektów. Dane są zawsze wysyłane z dostawcy obiektów do źródła obiektu jako `Stream`, ale <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> wymaga serializacji obiektu do `Stream` samodzielnie.

 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A> pobiera obiekt, który jest udostępniany, serializować go do `Stream`, a następnie wywołuje <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> w celu wysłania `Stream` do <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>.

 Użycie jednej z metod zamiany powoduje utworzenie nowego obiektu danych w debugowanego obiektu, który zastępuje wizualizację obiektu. Jeśli chcesz zmienić zawartość oryginalnego obiektu bez zastępowania, użyj jednej z metod transferu przedstawionych w poniższej tabeli. Te interfejsy API przesyłają dane w obu kierunkach w tym samym czasie, bez zastępowania obiektu, który jest wizualizacją:

|Dostawca obiektów|Źródło obiektu|
|---------------------|-------------------|
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferData%2A><br /><br /> —lub—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.TransferData%2A>|

## <a name="see-also"></a>Zobacz także
- [Instrukcje: pisanie wizualizatora](/visualstudio/debugger/create-custom-visualizers-of-data)
- [Przewodnik: pisanie wizualizatora w języku C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Przewodnik: pisanie wizualizatora w języku Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [Przewodnik: pisanie wizualizatora w języku Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [Zagadnienia dotyczące zabezpieczeń wizualizatora](../debugger/visualizer-security-considerations.md)