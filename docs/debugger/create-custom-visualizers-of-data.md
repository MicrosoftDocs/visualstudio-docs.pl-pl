---
title: Tworzenie niestandardowych wizualizatorów danych | Microsoft Docs
description: Visual Studio debugera to składniki, które wyświetlają dane. Dowiedz się więcej o sześciu standardowych wizualizatorach i o tym, jak pisać lub pobierać inne.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b8310133520231434ba7ed342a5e855892e3c53a
ms.sourcegitcommit: d0061f62c8543ff0db500972d9402a7f00e017c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2021
ms.locfileid: "114201744"
---
# <a name="create-custom-data-visualizers"></a>Tworzenie niestandardowych wizualizatorów danych

 *Wizualizator* jest częścią interfejsu użytkownika debugera, który wyświetla zmienną lub obiekt w sposób odpowiedni [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] dla jego typu danych. Na przykład wizualizator HTML interpretuje ciąg HTML i wyświetla wynik w sposób, w który będzie wyświetlany w oknie przeglądarki. Wizualizator mapy bitowej interpretuje strukturę mapy bitowej i wyświetla grafikę, która reprezentuje. Niektóre wizualizatory umożliwiają modyfikowanie i wyświetlanie danych.

 Debuger [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] zawiera sześć standardowych wizualizatorów. Wizualizatory tekstu, kodu HTML, XML i JSON działają na obiektach ciągów. Wizualizator drzewa WPF wyświetla właściwości drzewa wizualnego obiektu WPF. Wizualizator zestawu danych działa dla obiektów DataSet, DataView i DataTable.

Więcej wizualizatorów może być dostępnych do pobrania od firmy Microsoft, innych firm i społeczności. Możesz również napisać własne wizualizatory i zainstalować je w [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] debugerze.

W debugerze wizualizator jest reprezentowany przez ikonę ![lupy VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Ikona wizualizatora"). Możesz wybrać ikonę w oknie **DataTip,** debuger **Watch** (Czujka debugera) lub **QuickWatch (QuickWatch),** a następnie wybrać odpowiedni wizualizator dla odpowiedniego obiektu.

## <a name="write-custom-visualizers"></a>Pisanie niestandardowych wizualizatorów

 > [!NOTE]
 > Aby utworzyć niestandardowy wizualizator dla kodu natywnego, zobacz przykład natywnego wizualizatora [debugera SQLite.](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer) Niestandardowe wizualizatory nie są obsługiwane w przypadku aplikacji platformy UWP Windows 8.x.

Możesz napisać niestandardowy wizualizator dla obiektu dowolnej klasy zarządzanej z wyjątkiem <xref:System.Object> i <xref:System.Array> .

Architektura wizualizatora debugera ma dwie części:

- Strona *debugera działa* w Visual Studio, a następnie tworzy i wyświetla interfejs użytkownika wizualizatora.

- Strona *debugera jest* uruchamiana w ramach procesu, Visual Studio debugowanie *(debuger).* Obiekt danych do wizualizacji (na przykład obiekt String) istnieje w procesie debugowania. Strona debugera wysyła obiekt do strony debugera, który wyświetla go w interfejsie użytkownika, który tworzysz.

Strona debugera odbiera obiekt danych od dostawcy *obiektów,* który implementuje <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> interfejs. Strona debugera wysyła obiekt za pośrednictwem *źródła obiektu*, które pochodzi od <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> klasy .

Dostawca obiektów może również wysyłać dane z powrotem do źródła obiektu, co umożliwia napisanie wizualizatora, który może edytować dane. Przesłoń dostawcę obiektów, aby sgadywnie z ewaluatorem wyrażeń i źródłem obiektu.

Strona debugera i debuger komunikują się ze sobą za pośrednictwem metod, które serializują obiekt danych do <xref:System.IO.Stream> obiektu i deserializują obiekt z powrotem <xref:System.IO.Stream> do obiektu <xref:System.IO.Stream> danych.

Wizualizator dla typu ogólnego można napisać tylko wtedy, gdy typ jest typu otwartego. To ograniczenie jest takie samo jak ograniczenie podczas korzystania z `DebuggerTypeProxy` atrybutu . Aby uzyskać szczegółowe informacje, [zobacz Use the DebuggerTypeProxy attribute (Używanie atrybutu DebuggerTypeProxy).](../debugger/using-debuggertypeproxy-attribute.md)

Niestandardowe wizualizatory mogą mieć uwagi dotyczące zabezpieczeń. Zobacz [Visualizer security considerations (Zagadnienia dotyczące zabezpieczeń wizualizatora).](../debugger/visualizer-security-considerations.md)

Poniższe kroki zapewniają ogólne omówienie tworzenia wizualizatora. Aby uzyskać szczegółowe instrukcje, zobacz [Przewodnik: pisanie](../debugger/walkthrough-writing-a-visualizer-in-csharp.md) wizualizatora w języku C# lub [Przewodnik: pisanie wizualizatora w Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md).

### <a name="to-create-the-debugger-side"></a>Aby utworzyć stronę debugera

Aby utworzyć interfejs użytkownika wizualizatora po stronie debugera, należy utworzyć klasę dziedziczącą z klasy i zastąpić metodę w celu wyświetlenia <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> interfejsu. Umożliwia wyświetlanie formularzy Windows, okien dialogowych i kontrolek <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> w wizualizatorze.

1. Użyj <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> metod w celu uzyskania wizualizowanego obiektu po stronie debugera.

1. Utwórz klasę dziedziczącą z <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> klasy .

1. Zastąp metodę <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> , aby wyświetlić interfejs. Metody <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> do wyświetlania Windows, okien dialogowych i kontrolek w interfejsie.

1. Zastosuj <xref:System.Diagnostics.DebuggerVisualizerAttribute> , nadając mu wizualizator do wyświetlenia ( <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> ).

#### <a name="special-debugger-side-considerations-for-net-50"></a>Specjalne zagadnienia po stronie debugera dla programu .NET 5.0+

Niestandardowe wizualizatory przesyłują dane *między stronami debugera* i *debugera* za pośrednictwem serializacji binarnej przy <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> użyciu klasy domyślnie. Jednak ten rodzaj serializacji jest ograniczany w programie .NET 5 i  jego systemach z powodu problemów z zabezpieczeniami związanych z jego nienaprawialnymi lukami w zabezpieczeniach.
Ponadto została oznaczona jako całkowicie przestarzała w programie ASP.NET Core 5, a jego użycie będzie zgłaszane zgodnie z opisem w [dokumentacji](/dotnet/core/compatibility/core-libraries/5.0/binaryformatter-serialization-obsolete)ASP.NET Core .
W związku z tym w tej sekcji opisano niezbędne kroki, które należy wykonać, aby wizualizator był nadal obsługiwany w tym scenariuszu.

- Ze względu na zgodność metoda, która została <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A> przesłonięta w poprzedniej sekcji, nadal przyjmuje element <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> . Niemniej jednak w rzeczywistości jest to typ <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider2> .
W związku z tym `objectProvider` rzutuj obiekt na zaktualizowany interfejs.

- Podczas wysyłania obiektów, takich jak polecenia lub dane, do strony *debugera* użyj metody w celu przekazania jej do strumienia, określi najlepszy format serializacji do użycia na podstawie środowiska uruchomieniowego procesu `IVisualizerObjectProvider2.Serialize` *debugowania.*
Następnie przekaż strumień do `IVisualizerObjectProvider2.TransferData` metody .

- Jeśli składnik wizualizatora po stronie *debugera* musi zwrócić wszystko po stronie debugera, zostanie on umieszczony w *obiekcie* <xref:System.IO.Stream> zwróconym przez <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferData%2A> metodę . Użyj metody `IVisualizerObjectProvider2.GetDeserializableObjectFrom` , aby pobrać z niego wystąpienie i <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDeserializableObject> przetworzyć je zgodnie z potrzebami.

Zapoznaj się z sekcją Specjalne zagadnienia dotyczące strony debugowania dla programu [.NET 5.0+,](#special-debuggee-side-considerations-for-net-50) aby dowiedzieć się, jakie inne zmiany są wymagane po stronie *debugera,* gdy używanie serializacji binarnej nie jest obsługiwane.

> [!NOTE]
> Jeśli chcesz uzyskać więcej informacji na temat problemu, zobacz Przewodnik po zabezpieczeniach [BinaryFormatter](/dotnet/standard/serialization/binaryformatter-security-guide).

### <a name="to-create-the-visualizer-object-source-for-the-debuggee-side"></a>Aby utworzyć źródło obiektu wizualizatora po stronie debugera

W kodzie po stronie debugera edytuj obiekt , nadając mu typ do wizualizacji (źródło obiektu po stronie <xref:System.Diagnostics.DebuggerVisualizerAttribute> debugera) ( <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> ). Właściwość `Target` ustawia źródło obiektu. Jeśli pominiesz źródło obiektu, wizualizator użyje domyślnego źródła obiektu.

::: moniker range=">=vs-2019"
Kod po stronie debugera zawiera źródło obiektu, które jest wizualizowane. Obiekt danych może przesłonić metody <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> . Biblioteka DLL po stronie debugera jest niezbędna, jeśli chcesz utworzyć autonomiczny wizualizator.
::: moniker-end

W kodzie po stronie debugera:

- Aby wizualizator edytować obiekty danych, źródło obiektu musi dziedziczyć z metod <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> i przesłonić `TransferData` metody lub `CreateReplacementObject` .

- Jeśli w wizualizatorze chcesz obsługiwać wielowątkową platformę docelową, możesz użyć następujących monikerów struktury docelowej (TFM) w pliku projektu po stronie debugera.

   ```xml
   <TargetFrameworks>net20;netstandard2.0;netcoreapp2.0</TargetFrameworks>
   ```

   Są to jedyne obsługiwane tfmy.

#### <a name="special-debuggee-side-considerations-for-net-50"></a>Specjalne zagadnienia dotyczące strony debugowania dla programu .NET 5.0+

> [!IMPORTANT]
> Aby wizualizator działał w programie .NET 5.0 lub jego dodatkowymi krokami, mogą być wymagane dodatkowe kroki ze względu na kwestie związane z zabezpieczeniami dotyczącymi podstawowej binarnej metody serializacji używanej domyślnie. Przeczytaj tę [sekcję przed](#special-debugger-side-considerations-for-net-50) kontynuowaniem.

- Jeśli wizualizator implementuje metodę , użyj nowo dodanej <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.TransferData%2A> <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetDeserializableObject%2A> metody dostępnej w najnowszej wersji programu `VisualizerObjectSource` . Zwracana wartość pomaga określić format serializacji obiektu (binarny lub JSON) i deserializować bazowy obiekt, aby można go <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDeserializableObject> było użyć.

- Jeśli strona *debugera* zwraca dane po stronie *debugera* jako część `TransferData` wywołania, serializuj odpowiedź do strumienia po stronie *debugera* za pomocą <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.Serialize%2A> metody .

## <a name="see-also"></a>Zobacz też

- [Przewodnik: Pisanie wizualizatora w języku C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Przewodnik: Pisanie wizualizatora w języku Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [Instrukcje: instalowanie wizualizatora](../debugger/how-to-install-a-visualizer.md)
- [Instrukcje: testowanie i debugowanie wizualizatora](../debugger/how-to-test-and-debug-a-visualizer.md)
- [Interfejs API wizualizatora — dokumentacja](../debugger/visualizer-api-reference.md)
- [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)
