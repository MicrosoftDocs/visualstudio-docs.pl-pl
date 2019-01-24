---
title: 'Przewodnik: Za pomocą interfejsów API Profiler | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
ms.assetid: c2ae0b3e-a0ca-4967-b4df-e319008f520e
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 82d6c16c75cb2605bcdb8382d461d3557846fcc2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54769638"
---
# <a name="walkthrough-using-profiler-apis"></a>Przewodnik: Za pomocą interfejsów API Profiler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Przewodnik używa aplikacji w języku C# do prezentują sposób użycia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] API narzędzi profilowania. Użyjesz interfejsów API profilera, aby ograniczyć ilość danych zebranych podczas profilowania instrumentacji.  
  
 Kroki opisane w tym przewodniku dotyczą ogólnie aplikacji C/C++. Dla każdego języka będzie trzeba odpowiednio skonfigurować środowiska kompilacji.  
  
 Zazwyczaj powoduje rozpoczęcie analizowania wydajności aplikacji za pomocą profilowania próbki. Jeśli przykładowe profilowania nie zapewnia informacje manifestu "wąskie gardło", profilowanie Instrumentacji może zapewnić większy poziom szczegółowości. Profilowanie Instrumentacji jest bardzo przydatne w przypadku badania interakcji wątku.  
  
 Większy poziom szczegółowości oznacza jednak, że dane są zbierane. Może się okazać, że profilowanie Instrumentacji tworzy duże pliki danych. Ponadto Instrumentacji jest bardziej prawdopodobne wpłynąć na wydajność aplikacji. Aby uzyskać więcej informacji, zobacz [wartościami danych Instrumentacji opis](../profiling/understanding-instrumentation-data-values.md) i [opis z wartościami danych próbkowania](../profiling/understanding-sampling-data-values.md)  
  
 Profilera Visual Studio umożliwia ograniczenie zbierania danych. Ten przewodnik udostępnia przykładowy sposób ograniczyć zbieranie danych przy użyciu interfejsów API profilera. Profilera Visual Studio zapewnia kontrolowanie zbierania danych z aplikacji interfejsu API.  
  
 Dla kodu natywnego programu Visual Studio profiler interfejsów API znajdują się w VSPerf.dll. Plik nagłówkowy, VSPerf.h i Biblioteka importowana VSPerf.lib, znajdują się w katalogu narzędzi Narzędzia 9\Team programu Microsoft Visual Studio.  
  
 Dla kodu zarządzanego program profilujący interfejsów API znajdują się w Microsoft.VisualStudio.Profiler.dll. Ta biblioteka DLL znajduje się w katalogu narzędzi Narzędzia 9\Team programu Microsoft Visual Studio. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Profiler>.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym przewodniku przyjęto założenie, że preferowanego środowiska deweloperskiego jest skonfigurowany do obsługi debugowania i pobierania próbek. Przegląd wymagań wstępnych można znaleźć w następujących tematach:  
  
 [Instrukcje: Wybieranie metod zbierania](../profiling/how-to-choose-collection-methods.md)  
  
 [Instrukcje: Odwołania do informacji o symbolach w systemie Windows](../profiling/how-to-reference-windows-symbol-information.md)  
  
 Domyślnie po uruchomieniu profilera, profiler zbiera dane na poziomie globalnym. Następujący kod na początku programu, włącza globalnego profilowania na wyłączone.  
  
```  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
 Bez użycia wywołanie interfejsu API, można wyłączyć zbieranie danych w wierszu polecenia. W następujących krokach założono, środowiska kompilacji wiersza polecenia jest skonfigurowany do uruchamiania narzędzia profilowania i własne narzędzia programistyczne. W tym ustawienia wymagane dla VSInstr i narzędzia VSPerfCmd. Zobacz narzędzi profilowania z wiersza polecenia.  
  
## <a name="limiting-data-collection-using-profiler-apis"></a>Ograniczanie kolekcji danych za pomocą interfejsów API Profiler  
  
#### <a name="to-create-the-code-to-profile"></a>Aby utworzyć kod do profilu  
  
1.  Utwórz nowy projekt C# w programie Visual Studio, lub użyć kompilacji wiersza polecenia, w zależności od preferencji.  
  
    > [!NOTE]
    >  Kompilacja musi odwoływać się biblioteki Microsoft.VisualStudio.Profiler.dll, znajduje się w katalogu narzędzi Narzędzia 9\Team programu Microsoft Visual Studio.  
  
2.  Skopiuj i wklej następujący kod do projektu:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using Microsoft.VisualStudio.Profiler;  
  
    namespace ConsoleApplication2  
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
              A a;  
              a = new A(2);  
              int x;      
              Console.WriteLine("2 square is {0}", a.DoNotProfileThis());  
              DataCollection.StartProfile(  
                  ProfileLevel.Global,  
                  DataCollection.CurrentId);  
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
  
1. Otwórz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE. Do **analizy** menu wskaż **Profiler**, a następnie wybierz pozycję **nowej sesji wydajności.**  
  
2. Dodaj swoje skompilowanych plików binarnych do **cele** listy w **Eksplorator wydajności** okna. Kliknij prawym przyciskiem myszy **cele**, a następnie wybierz pozycję **Dodaj binarne docelowej**. Znajdź plik binarny w **Dodaj binarne docelowej** okno dialogowe, a następnie kliknij przycisk **Otwórz**.  
  
3. Wybierz **Instrumentacji** z **metoda** listy na **Eksplorator wydajności** paska narzędzi.  
  
4. Kliknij przycisk **Uruchom za pomocą profilowania**.  
  
    Program profilujący zostanie Instrumentacja wykonania pliku binarnego i utworzenia pliku raportu wydajności. Plik raportu wydajności będą wyświetlane w **raporty** węźle **Eksplorator wydajności**.  
  
5. Otwórz wynikowy plik raportu wydajności.  
  
   Domyślnie po uruchomieniu profilera, program profilujący będzie zbierać dane na poziomie globalnym. Następujący kod na początku programu, włącza globalnego profilowania na wyłączone.  
  
```  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
#### <a name="to-collect-and-view-data-at-the-command-line"></a>Do gromadzenia i wyświetlania danych w wierszu polecenia  
  
1.  Kompiluj wersję debugowania przykładowy kod, który został utworzony w procedurze "Tworzenie kodu do profil", we wcześniejszej części tego przewodnika.  
  
2.  Aby profilować aplikację zarządzaną, wpisz następujące polecenie, aby ustawić odpowiednie zmienne środowiskowe:  
  
     **VsPefCLREnv /traceon**  
  
3.  Wpisz następujące polecenie:**VSInstr \<nazwa pliku > .exe**  
  
4.  Wpisz następujące polecenie:**/Output polecenia VSPerfCmd:\<nazwa pliku > .vsp**  
  
5.  Wpisz następujące polecenie:**VSPerfCmd /globaloff**  
  
6.  Wykonywanie programu.  
  
7.  Wpisz następujące polecenie:**VSPerfCmd/shutdown**  
  
8.  Wpisz następujące polecenie:**VSPerfReport/calltrace:\<nazwa pliku > .vsp**  
  
     Plik CSV jest tworzony w bieżącym katalogu z wynikowe dane dotyczące wydajności.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Profiler>   
 [Dokumentacja interfejsu API Profiler programu Visual Studio (Native)](../profiling/visual-studio-profiler-api-reference-native.md)   
 [Wprowadzenie](../profiling/getting-started-with-performance-tools.md)   
 [Profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)
