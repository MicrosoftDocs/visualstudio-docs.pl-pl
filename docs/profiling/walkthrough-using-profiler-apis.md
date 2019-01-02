---
title: 'Przewodnik: Za pomocą interfejsów API Profiler | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
ms.assetid: c2ae0b3e-a0ca-4967-b4df-e319008f520e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09368aceed6828e63c0e5c9d20a77d1787bc2c57
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53891271"
---
# <a name="walkthrough-using-profiler-apis"></a>Przewodnik: Za pomocą interfejsów API profilera

Przewodnik używa aplikacji w języku C# do prezentują sposób użycia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] API narzędzi profilowania. Użyjesz interfejsów API profilera, aby ograniczyć ilość danych zebranych podczas profilowania instrumentacji.  
  
 Kroki opisane w tym przewodniku dotyczą ogólnie aplikacji C/C++. Dla każdego języka będzie trzeba odpowiednio skonfigurować środowiska kompilacji.  
  
 Zazwyczaj powoduje rozpoczęcie analizowania wydajności aplikacji za pomocą profilowania próbki. Jeśli przykładowe profilowania nie zapewnia informacje manifestu "wąskie gardło", profilowanie Instrumentacji może zapewnić większy poziom szczegółowości. Profilowanie Instrumentacji jest bardzo przydatne w przypadku badania interakcji wątku.  
  
 Większy poziom szczegółowości oznacza jednak, że dane są zbierane. Może się okazać, że profilowanie Instrumentacji tworzy duże pliki danych. Ponadto Instrumentacji jest bardziej prawdopodobne wpłynąć na wydajność aplikacji. Aby uzyskać więcej informacji, zobacz [zrozumieć wartościami danych Instrumentacji](../profiling/understanding-instrumentation-data-values.md) i [zrozumieć z wartościami danych próbkowania](../profiling/understanding-sampling-data-values.md)  
  
 Profilera Visual Studio umożliwia ograniczenie zbierania danych. Ten przewodnik udostępnia przykładowy sposób ograniczyć zbieranie danych przy użyciu interfejsów API profilera. Profilera Visual Studio zapewnia kontrolowanie zbierania danych z aplikacji interfejsu API.  
  
 Dla kodu natywnego programu Visual Studio profiler interfejsów API znajdują się w *VSPerf.dll*. Plik nagłówkowy *VSPerf.h*i bibliotekę importu *VSPerf.lib*, znajdują się w *programu Microsoft Visual Studio\2017\Team narzędzia Tools\PerfSDK* katalog.  Dla aplikacji 64-bitowych jest folder *Tools\x64\PerfSDK narzędzia Studio\2017\Team Visual firmy Microsoft*
  
 Dla kodu zarządzanego, program profilujący interfejsów API znajdują się w *Microsoft.VisualStudio.Profiler.dll*. Ta biblioteka DLL znajduje się w *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools* katalogu. Dla aplikacji 64-bitowych jest folder *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools\x64*. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Profiler>. 
 
  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym przewodniku przyjęto założenie, że preferowanego środowiska deweloperskiego jest skonfigurowany do obsługi debugowania i pobierania próbek. Przegląd wymagań wstępnych można znaleźć w następujących tematach:  
  
 [Instrukcje: Wybieranie metod kolekcji](../profiling/how-to-choose-collection-methods.md)  
  
 [Instrukcje: Informacje o symbolach Windows odwołania](../profiling/how-to-reference-windows-symbol-information.md)  
  
 Domyślnie po uruchomieniu profilera, profiler zbiera dane na poziomie globalnym. Następujący kod na początku programu, włącza globalnego profilowania na wyłączone.  
  
```csharp  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
 Można wyłączyć zbieranie danych w wierszu polecenia, bez korzystania z wywołania interfejsu API. W następujących krokach założono, środowiska kompilacji wiersza polecenia jest skonfigurowany do uruchamiania narzędzia profilowania i własne narzędzia programistyczne. W tym ustawienia wymagane dla VSInstr i narzędzia VSPerfCmd. Zobacz [wiersza polecenia, narzędzia profilowania](../profiling/using-the-profiling-tools-from-the-command-line.md).  
  
## <a name="limit-data-collection-using-profiler-apis"></a>Ograniczenie zbierania danych przy użyciu interfejsów API profilera  
  
#### <a name="to-create-the-code-to-profile"></a>Aby utworzyć kod do profilu  
  
1.  Utwórz nowy projekt C# w programie Visual Studio, lub użyć kompilacji wiersza polecenia, w zależności od preferencji.  
  
    > [!NOTE]
    >  Musi odwoływać się do kompilacji *Microsoft.VisualStudio.Profiler.dll* biblioteki, na terenie *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools* katalogu.  
  
2.  Skopiuj i wklej następujący kod do projektu:  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using Microsoft.VisualStudio.Profiler;  
  
    namespace ConsoleApplication1  
    {  
        class Program  
        {  
            public class A  
            {  
                private int _x;  
  
                public A(int x)  
                {  
                    _x = x;  
                }  
  
                public int DoNotProfileThis()  
                {  
                    return _x * _x;  
                }  
  
                public int OnlyProfileThis()  
                {  
                    return _x + _x;  
                }  
  
                public static void Main()  
                {  
                    DataCollection.StopProfile(  
                    ProfileLevel.Global,  
                    DataCollection.CurrentId); 

                    A a = new A(2);  
                    Console.WriteLine("2 square is {0}", a.DoNotProfileThis()); 

                    DataCollection.StartProfile(  
                    ProfileLevel.Global,  
                    DataCollection.CurrentId);

                    int x;  
                    x = a.OnlyProfileThis();  

                    DataCollection.StopProfile(  
                    ProfileLevel.Global,   
                    DataCollection.CurrentId);  

                    Console.WriteLine("2 doubled is {0}", x);  
                }  
            }  
  
        }  
    }  
    ```  
  
#### <a name="to-collect-and-view-data-in-the-visual-studio-ide"></a>Do gromadzenia i wyświetlania danych w środowisku IDE programu Visual Studio  
  
1. Otwórz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE. Do **analizy** menu wskaż **Profiler**, a następnie wybierz pozycję **nowa sesja wydajności**.  
  
2. Dodaj swoje skompilowanych plików binarnych do **cele** listy w **Eksplorator wydajności** okna. Kliknij prawym przyciskiem myszy **cele**, a następnie wybierz pozycję **Dodaj binarne docelowej**. Znajdź plik binarny w **Dodaj binarne docelowej** okno dialogowe, a następnie kliknij przycisk **Otwórz**.  
  
3. Wybierz **Instrumentacji** z **metoda** listy na **Eksplorator wydajności** paska narzędzi.  
  
4. Kliknij przycisk **Uruchom za pomocą profilowania**.  
  
    Program profilujący zostanie Instrumentacja wykonania pliku binarnego i utworzenia pliku raportu wydajności. Plik raportu wydajności będą wyświetlane w **raporty** węźle **Eksplorator wydajności**.  
  
5. Otwórz wynikowy plik raportu wydajności.  
  
   Domyślnie po uruchomieniu profilera, program profilujący będzie zbierać dane na poziomie globalnym. Następujący kod na początku programu, włącza globalnego profilowania na wyłączone.  
  
```csharp  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
#### <a name="to-collect-and-view-data-at-the-command-line"></a>Do gromadzenia i wyświetlania danych w wierszu polecenia  
  
1.  Kompiluj wersję debugowania przykładowy kod, który został utworzony w procedurze "Tworzenie kodu do profil", we wcześniejszej części tego przewodnika.  
  
2.  Aby profilować aplikację zarządzaną, wpisz następujące polecenie, aby ustawić odpowiednie zmienne środowiskowe:  
  
     **VsPerfCLREnv /traceon**  
  
3.  Wpisz następujące polecenie: **Narzędzie VSInstr \<nazwa pliku > .exe**  
  
4.  Wpisz następujące polecenie: **/ OUTPUT polecenia VSPerfCmd:\<nazwa pliku > .vsp**  
  
5.  Wpisz następujące polecenie: **Narzędzia VSPerfCmd /globaloff**  
  
6.  Wykonywanie programu.  
  
7.  Wpisz następujące polecenie: **Narzędzia VSPerfCmd/shutdown**  
  
8.  Wpisz następujące polecenie: **VSPerfReport/calltrace:\<nazwa pliku > .vsp**  
  
     ELEMENT. *csv* plik zostanie utworzony w bieżącym katalogu z wynikowe dane dotyczące wydajności.  
  
## <a name="see-also"></a>Zobacz także  
 <xref:Microsoft.VisualStudio.Profiler>   
 [Visual Studio interfejsy API profilera (native)](../profiling/visual-studio-profiler-api-reference-native.md)   
 [Wprowadzenie](../profiling/getting-started-with-performance-tools.md)   
 [Profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)
