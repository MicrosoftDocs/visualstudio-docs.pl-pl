---
title: 'Przewodnik: Korzystanie z interfejsów API profilera | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
ms.assetid: c2ae0b3e-a0ca-4967-b4df-e319008f520e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 203952f712fb3b28b93d570f99e6d36f56b5f2b5
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68870274"
---
# <a name="walkthrough-using-profiler-apis"></a>Przewodnik: Korzystanie z interfejsów API profilera

W tym przewodniku C# użyto aplikacji do zademonstrowania sposobu używania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interfejsów API narzędzia profilowania. Użyjesz interfejsów API profilera, aby ograniczyć ilość danych zbieranych podczas profilowania Instrumentacji.

 Kroki opisane w tym instruktażu dotyczą zwykle aplikacji C/C++ . Dla każdego języka trzeba będzie odpowiednio skonfigurować środowisko kompilacji.

 Zazwyczaj należy rozpocząć analizowanie wydajności aplikacji przy użyciu profilowania przykładowych. Jeśli przykładowe Profilowanie nie zawiera informacji, które wykreślą wąskie gardło, profilowanie Instrumentacji może zapewnić wyższy poziom szczegółowości. Profilowanie Instrumentacji jest bardzo przydatne do badania interakcji wątku.

 Jednak wyższy poziom szczegółowości oznacza, że zbierane są więcej danych. Może się okazać, że profilowanie Instrumentacji tworzy duże pliki danych. Ponadto Instrumentacja może mieć wpływ na wydajność aplikacji. Aby uzyskać więcej informacji, zobacz [Omówienie wartości danych Instrumentacji](../profiling/understanding-instrumentation-data-values.md) i [Opis wartości danych próbkowania](../profiling/understanding-sampling-data-values.md)

 Program Visual Studio profiler umożliwia ograniczenie zbierania danych. Ten Instruktaż zawiera przykład sposobu ograniczania zbierania danych przy użyciu interfejsów API profilera. Profiler programu Visual Studio udostępnia interfejs API służący do kontrolowania zbierania danych z poziomu aplikacji.

 ::: moniker range=">=vs-2019"
 W przypadku kodu natywnego interfejsy API profilera programu Visual Studio znajdują się w *VSPerf. dll*. Plik nagłówkowy, *VSPerf. h*i Biblioteka Imports *VSPerf. lib*znajdują się w katalogu *programu Microsoft Visual Studio\2019\Team Tools\Performance Tools\PerfSDK* .  W przypadku aplikacji 64-bitowych folder jest w *programie Microsoft Visual Studio\2019\Team Tools\Performance Tools\x64\PerfSDK*
 ::: moniker-end
 ::: moniker range="vs-2017"
 W przypadku kodu natywnego interfejsy API profilera programu Visual Studio znajdują się w *VSPerf. dll*. Plik nagłówkowy, *VSPerf. h*i Biblioteka Imports *VSPerf. lib*znajdują się w katalogu *programu Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK* .  W przypadku aplikacji 64-bitowych folder jest w *programie Microsoft Visual Studio\2017\Team Tools\Performance Tools\x64\PerfSDK*
 ::: moniker-end

 W przypadku kodu zarządzanego interfejsy API profilera znajdują się w *pliku Microsoft. VisualStudio. Profiler. dll*. Ta biblioteka DLL znajduje się w katalogu *programu Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools* . W przypadku aplikacji 64-bitowych folder jest w *programie Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools\x64*. Aby uzyskać więcej informacji, zobacz [Profiler](/previous-versions/ms242704(v=vs.140)).

## <a name="prerequisites"></a>Wymagania wstępne
 W tym instruktażu przyjęto założenie, że wybór środowiska programistycznego jest skonfigurowany do obsługi debugowania i próbkowania. W poniższych tematach omówiono wymagania wstępne:

- [Instrukcje: Wybieranie metod kolekcji](../profiling/how-to-choose-collection-methods.md)

- [Instrukcje: Informacje o symbolach systemu Windows](../profiling/how-to-reference-windows-symbol-information.md)

 Domyślnie po uruchomieniu profilera profiler zbiera dane na poziomie globalnym. Poniższy kod na początku programu powoduje wyłączenie profilowania globalnego.

```csharp
DataCollection.StopProfile(
ProfileLevel.Global,
DataCollection.CurrentId);
```

 Zbieranie danych można wyłączyć w wierszu polecenia bez użycia wywołania interfejsu API. W poniższych krokach przyjęto założenie, że środowisko kompilacji wiersza polecenia jest skonfigurowane do uruchamiania narzędzi profilowania i narzędzi deweloperskich. Obejmuje to ustawienia niezbędne dla VSInstr i VSPerfCmd. Zobacz [narzędzia profilowania wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md).

## <a name="limit-data-collection-using-profiler-apis"></a>Ograniczanie zbierania danych za pomocą interfejsów API profilera

#### <a name="to-create-the-code-to-profile"></a>Aby utworzyć kod do profilowania

1. Utwórz nowy C# projekt w programie Visual Studio lub użyj kompilacji wiersza polecenia, w zależności od preferencji.

    > [!NOTE]
    > Kompilacja musi odwoływać się do biblioteki *Microsoft. VisualStudio. Profiler. dll* znajdującej się w katalogu *programu Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools* .

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

#### <a name="to-collect-and-view-data-in-the-visual-studio-ide"></a>Aby zbierać i wyświetlać dane w środowisku IDE programu Visual Studio

1. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Otwórz środowisko IDE. W menu **Analizuj** wskaż polecenie **Profiler**, a następnie wybierz pozycję **Nowa sesja wydajności**.

2. Dodaj skompilowany plik binarny do listy targets w oknie **Eksplorator wydajności** . Kliknij prawym przyciskiem myszy element **docelowy**, a następnie wybierz polecenie **Dodaj docelowy plik binarny**. Zlokalizuj plik binarny w oknie dialogowym **Dodaj docelowy plik binarny** , a następnie kliknij przycisk **Otwórz**.

3. Wybierz pozycję Instrumentacja z listy **Metoda** na pasku narzędzi **Eksplorator wydajności** .

4. Kliknij przycisk **Uruchom z profilem**.

    Profiler będzie Instrumentacją i wykonywaniem pliku binarnego oraz utworzyć plik raportu wydajności. Plik raportu wydajności zostanie wyświetlony w węźle **raporty** w **Eksplorator wydajności**.

5. Otwórz wynikowy plik raportu wydajności.

   Domyślnie po uruchomieniu profilera Profiler będzie zbierać dane na poziomie globalnym. Poniższy kod na początku programu powoduje wyłączenie profilowania globalnego.

```csharp
DataCollection.StopProfile(
ProfileLevel.Global,
DataCollection.CurrentId);
```

#### <a name="to-collect-and-view-data-at-the-command-line"></a>Aby zbierać i wyświetlać dane w wierszu polecenia

1. Skompiluj wersję Debug przykładowego kodu, który został utworzony w procedurze "Tworzenie kodu do profilu" wcześniej w tym instruktażu.

2. Aby profilować aplikację zarządzaną, wpisz następujące polecenie, aby ustawić odpowiednie zmienne środowiskowe:

     **VsPerfCLREnv/TRACEON**

3. Wpisz następujące polecenie: **VSInstr \<filename>.exe**

4. Wpisz następujące polecenie: **VSPerfCmd/Start: Trace/Output:\<filename >. vsp**

5. Wpisz następujące polecenie: **Narzędzia VSPerfCmd /globaloff**

6. Wykonaj swój program.

7. Wpisz następujące polecenie: **Narzędzia VSPerfCmd/shutdown**

8. Wpisz następujące polecenie: **VSPerfReport/calltrace:\<filename >. vsp**

     Z. plik *CSV* jest tworzony w bieżącym katalogu z wynikowymi danymi o wydajności.

## <a name="see-also"></a>Zobacz także

- [Profiler](/previous-versions/ms242704(v=vs.140))
- [Dokumentacja interfejsu API programu Visual Studio profiler (natywna)](../profiling/visual-studio-profiler-api-reference-native.md)
- [Wprowadzenie](../profiling/getting-started-with-performance-tools.md)
- [Profil z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)
