---
title: 'Przewodnik: Korzystanie z interfejsów API profilera | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
ms.assetid: c2ae0b3e-a0ca-4967-b4df-e319008f520e
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 81071a44b51b1441782b25741126873fc720ed7b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779886"
---
# <a name="walkthrough-using-profiler-apis"></a>Przewodnik: korzystanie z interfejsów API profilera

Instruktaż używa aplikacji Języka C#, aby [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zademonstrować, jak używać interfejsów API narzędzi profilowania. Za pomocą interfejsów API profilera można ograniczyć ilość danych zebranych podczas profilowania instrumentacji.

 Kroki opisane w tym instruktażu zazwyczaj dotyczą aplikacji C/C++. Dla każdego języka należy odpowiednio skonfigurować środowisko kompilacji.

 Zazwyczaj rozpocznie się analizowanie wydajności aplikacji przy użyciu przykładowego profilowania. Jeśli profilowanie próbki nie zawiera informacji wskazujących wąskie gardło, profilowanie instrumentacji może zapewnić wyższy poziom szczegółowości. Profilowanie instrumentacji jest bardzo przydatne do badania interakcji wątku.

 Jednak większy poziom szczegółowości oznacza, że więcej danych jest zbierane. Może się okazać, że profilowanie instrumentacji tworzy duże pliki danych. Ponadto instrumentacja jest bardziej prawdopodobne, aby mieć wpływ na wydajność aplikacji. Aby uzyskać więcej informacji, zobacz [Opis wartości danych instrumentacji](../profiling/understanding-instrumentation-data-values.md) i [zrozumienie wartości danych próbkowania](../profiling/understanding-sampling-data-values.md)

 Visual Studio profiler pozwala ograniczyć zbieranie danych. W tym instruktażu przedstawiono przykład ograniczenia zbierania danych przy użyciu interfejsów API profilera. Profiler programu Visual Studio udostępnia interfejs API do kontrolowania zbierania danych z poziomu aplikacji.

 ::: moniker range="vs-2017"
 Dla kodu macierzystego interfejsy API profilera programu Visual Studio znajdują się w pliku *VSPerf.dll*. Plik nagłówka *VSPerf.h*i biblioteka importu *VSPerf.lib*znajdują się w katalogu *programu Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK.*  W przypadku aplikacji 64-bitowych folder to *Microsoft Visual Studio\2017\Team Tools\Performance Tools\x64\PerfSDK*
 ::: moniker-end

 W przypadku kodu zarządzanego interfejsy API profilera znajdują się w pliku *Microsoft.VisualStudio.Profiler.dll*. Ta biblioteka DLL znajduje się w katalogu *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools.* W przypadku aplikacji 64-bitowych folderem jest *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools\x64*. Aby uzyskać więcej informacji, zobacz [Profiler](/previous-versions/ms242704(v=vs.140)).

## <a name="prerequisites"></a>Wymagania wstępne
 W tym przewodniku przyjęto założenie, że wybrane środowisko programistyczne jest skonfigurowane do obsługi debugowania i próbkowania. Następujące tematy zawierają omówienie tych wymagań wstępnych:

- [Jak: Wybierz metody zbierania](../profiling/how-to-choose-collection-methods.md)

- [Instrukcje: odwołania do informacji o symbolach w systemie Windows](../profiling/how-to-reference-windows-symbol-information.md)

 Domyślnie po uruchomieniu profilera profiler zbiera dane na poziomie globalnym. Poniższy kod na początku programu wyłącza profilowanie globalne.

```csharp
DataCollection.StopProfile(
ProfileLevel.Global,
DataCollection.CurrentId);
```

 Zbieranie danych można wyłączyć w wierszu polecenia bez użycia wywołania interfejsu API. W poniższych krokach założono, że środowisko kompilacji wiersza polecenia jest skonfigurowane do uruchamiania narzędzi profilowania i jako narzędzia programistyczne. Obejmuje to ustawienia niezbędne dla VSInstr i VSPerfCmd. Zobacz [Narzędzia do profilowania wierszy polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md).

## <a name="limit-data-collection-using-profiler-apis"></a>Ograniczanie gromadzenia danych przy użyciu interfejsów API profilera

#### <a name="to-create-the-code-to-profile"></a>Aby utworzyć kod do profilu

1. Utwórz nowy projekt języka C# w programie Visual Studio lub użyj kompilacji wiersza polecenia, w zależności od preferencji.

    > [!NOTE]
    > Kompilacja musi odwoływać się do biblioteki *Microsoft.VisualStudio.Profiler.dll,* znajdującej się w katalogu *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools.*

2. Skopiuj i wklej następujący kod do projektu:

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

#### <a name="to-collect-and-view-data-in-the-visual-studio-ide"></a>Aby zbierać i wyświetlać dane w programie Visual Studio IDE

1. Otwórz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE. W menu **Analizuj** wskaż polecenie **Profiler**, a następnie wybierz polecenie **Nowa sesja wydajności**.

2. Dodaj skompilowany plik binarny do listy **obiekty docelowe** w oknie **Eksploratora wydajności.** Kliknij prawym przyciskiem myszy pozycję **Obiekty docelowe**, a następnie wybierz polecenie **Dodaj plik binarny docelowy**. Znajdź plik binarny w oknie dialogowym **Dodawanie pliku binarnego docelowego,** a następnie kliknij przycisk **Otwórz**.

3. Wybierz **instrumentację** z listy **Metoda** na pasku narzędzi **Eksploratora wydajności.**

4. Kliknij **przycisk Uruchom z profilem**.

    Profiler będzie instrumentem i wykonać plik binarny i utworzyć plik raportu wydajności. Plik raportu o skuteczności pojawi się w węźle **Raporty** **Eksploratora wydajności**.

5. Otwórz wynikowy plik raportu wydajności.

   Domyślnie po uruchomieniu profilera profiler będzie zbierać dane na poziomie globalnym. Poniższy kod na początku programu wyłącza profilowanie globalne.

```csharp
DataCollection.StopProfile(
ProfileLevel.Global,
DataCollection.CurrentId);
```

#### <a name="to-collect-and-view-data-at-the-command-line"></a>Aby zbierać i wyświetlać dane w wierszu polecenia

1. Skompilować wersję debugowania przykładowego kodu utworzonego w procedurze "Tworzenie kodu do profilu", wcześniej w tym instruktażu.

2. Aby profilować aplikację zarządzaną, wpisz następujące polecenie, aby ustawić odpowiednie zmienne środowiskowe:

     **VsPerfCLREnv /traceon**

3. Wpisz następujące polecenie: **NAZWA \<PLIKU VSInstr>.exe**

4. Wpisz następujące polecenie: **VSPerfCmd /start:trace\</output: nazwa pliku>.vsp**

5. Wpisz następujące polecenie: **VSPerfCmd /globaloff**

6. Wykonaj swój program.

7. Wpisz następujące polecenie: **VSPerfCmd /shutdown**

8. Wpisz następujące polecenie: **VSPerfReport /calltrace:\<nazwa pliku>.vsp**

     A. *csv* jest tworzony w bieżącym katalogu z wynikami danych wydajności.

## <a name="see-also"></a>Zobacz też

- [Profiler](/previous-versions/ms242704(v=vs.140))
- [Odwołanie do interfejsu API profilera programu Visual Studio (natywne)](../profiling/visual-studio-profiler-api-reference-native.md)
- [Wprowadzenie](../profiling/getting-started-with-performance-tools.md)
- [Profil z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)
