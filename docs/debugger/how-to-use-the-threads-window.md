---
title: Debugowanie aplikacji wielowątkowej
description: Debuguj przy użyciu okna wątki i paska narzędzi lokalizacji debugowania w programie Visual Studio
ms.date: 02/14/2020
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cbde477e076203625e35ebf0109ed344679563f8
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683318"
---
# <a name="walkthrough-debug-a-multithreaded-app-using-the-threads-window-c-visual-basic-c"></a>Przewodnik: debugowanie aplikacji wielowątkowej przy użyciu okna wątków (C#, Visual Basic, C++)

Kilka elementów interfejsu użytkownika programu Visual Studio ułatwia debugowanie aplikacji wielowątkowych. W tym artykule przedstawiono funkcje debugowania wielowątkowego w oknie Edytor kodu, pasek narzędzi **Lokalizacja debugowania** i okno **wątków** . Informacje o innych narzędziach do debugowania aplikacji wielowątkowych znajdują się w temacie Wprowadzenie do [debugowania aplikacji wielowątkowych](../debugger/get-started-debugging-multithreaded-apps.md).

Ukończenie tego samouczka zajmuje zaledwie kilka minut i zapoznaje się z podstawą debugowania aplikacji wielowątkowych.

## <a name="create-a-multithreaded-app-project"></a>Tworzenie projektu aplikacji wielowątkowych

Utwórz następujący projekt aplikacji wielowątkowych do użycia w tym samouczku:

1. Otwórz program Visual Studio i Utwórz nowy projekt.

   ::: moniker range=">=vs-2019"

   Jeśli okno startowe nie jest otwarte, wybierz pozycję **plik** > **startowy**.

   W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

   W oknie **Tworzenie nowego projektu** w polu wyszukiwania wpisz lub wpisz *Console* . Następnie wybierz pozycję **C#** lub **C++** z listy język, a następnie wybierz pozycję **Windows** z listy platform. 

   Po zastosowaniu filtrów języka i platformy wybierz **aplikację konsolową** dla platformy .NET Core lub dla języka C++, a następnie wybierz przycisk **dalej**.

   > [!NOTE]
   > Jeśli nie widzisz poprawnego szablonu, przejdź do pozycji **Narzędzia**  >  **Pobierz narzędzia i funkcje...**, co spowoduje otwarcie Instalator programu Visual Studio. Wybierz pozycję **Programowanie dla wielu platform w środowisku .NET Core** lub **Programowanie aplikacji klasycznych w języku C++** , a następnie wybierz polecenie **Modyfikuj**.

   W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź *MyThreadWalkthroughApp* w polu **Nazwa projektu** . Następnie wybierz pozycję **dalej** lub **Utwórz**, zależnie od opcji.

   W przypadku platformy .NET Core wybierz zalecaną platformę docelową (.NET Core 3,1) lub .NET 5, a następnie wybierz pozycję **Utwórz**.

   ::: moniker-end
   ::: moniker range="vs-2017"
   Na górnym pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**. W lewym okienku okna dialogowego **Nowy projekt** wybierz następujące opcje:

   - W przypadku aplikacji C# w obszarze **Visual C#** wybierz pozycję **Windows Desktop**, a następnie w środkowym okienku wybierz pozycję **aplikacja konsoli (.NET Framework)**.
   - W przypadku aplikacji w języku C++ w obszarze **Visual C++** wybierz pozycję **Windows Desktop**, a następnie wybierz pozycję **Aplikacja konsolowa systemu Windows**.

   Jeśli nie widzisz **aplikacji konsolowej (.NET Framework)** lub, w przypadku języka C++, szablonu projektu **aplikacji konsoli** , przejdź do pozycji **Narzędzia**  >  **Pobierz narzędzia i funkcje...**, co spowoduje otwarcie Instalator programu Visual Studio. Wybierz pozycję **Programowanie aplikacji klasycznych dla platformy .NET** lub **Programowanie aplikacji klasycznych w języku C++** , a następnie wybierz polecenie **Modyfikuj**.

   Następnie wpisz nazwę, na przykład *MyThreadWalkthroughApp* , i kliknij przycisk **OK**.

   Wybierz przycisk **OK**.
   ::: moniker-end

   Zostanie wyświetlony nowy projekt konsoli. Po utworzeniu projektu zostanie wyświetlony plik źródłowy. W zależności od wybranego języka plik źródłowy może mieć nazwę *program.cs*, *MyThreadWalkthroughApp. cpp* lub *Module1. vb*.

1. Zastąp kod w pliku źródłowym kodem przykładowym języka C# lub C++ od [rozpoczęcia debugowania aplikacji wielowątkowych](../debugger/get-started-debugging-multithreaded-apps.md).

1. Wybierz pozycję **plik**  >  **Zapisz wszystko**.

## <a name="start-debugging"></a>Rozpocznij debugowanie

1. Znajdź następujące wiersze w kodzie źródłowym:

   ```csharp
   Thread.Sleep(3000);
   Console.WriteLine();
   ```

   ```C++
   Thread::Sleep(3000);
   Console.WriteLine();
   ```

1. Ustaw punkt przerwania w `Console.WriteLine();` wierszu, klikając lewym marginesem lub wybierając wiersz i naciskając klawisz **F9**.

   Punkt przerwania jest wyświetlany jako czerwony okrąg w lewym marginesie obok wiersza kodu.

1. Wybierz pozycję **Debuguj**  >  **Rozpocznij debugowanie** lub naciśnij klawisz **F5**.

   Aplikacja jest uruchamiana w trybie debugowania i wstrzymuje się w punkcie przerwania.

1. W trybie przerwania Otwórz okno **wątki** , wybierając pozycję **Debuguj**  >  **wątki systemu Windows**  >  . Aby otworzyć lub wyświetlić **wątki** oraz inne okna debugowania, musisz być w sesji debugowania.

## <a name="examine-thread-markers"></a>Sprawdzanie znaczników wątku

1. Zlokalizuj wiersz w kodzie źródłowym `Console.WriteLine();` .

   1. Kliknij prawym przyciskiem myszy w oknie **wątki** i wybierz polecenie **Pokaż wątki w źródle** ![Pokaż wątki w źródle](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") z menu.

   Na marginesie obok wiersza kodu źródłowego jest teraz wyświetlany ![znacznik](../debugger/media/dbg-thread-marker.png "Znacznik wątku")wątku ikony *znacznika wątku* . Znacznik wątku wskazuje, że wątek jest zatrzymany w tej lokalizacji. Jeśli w lokalizacji znajduje się więcej niż jeden zatrzymany wątek, zostanie wyświetlona ikona ![wiele wątków](../debugger/media/dbg-multithreaded-show-threads.png "wiele wątków") .

1. Umieść wskaźnik myszy nad znacznikiem wątku. Etykietki danych pojawia się, pokazując nazwę i identyfikator wątku dla zatrzymanego wątku lub wątków. Mogą to być nazwy wątków `<No Name>` .

   >[!TIP]
   >Aby ułatwić identyfikację wątków pustego, można zmienić ich nazwy w oknie **wątki** . Kliknij prawym przyciskiem myszy wątek i wybierz polecenie **Zmień nazwę**.

1. Kliknij prawym przyciskiem myszy znacznik wątku w kodzie źródłowym, aby wyświetlić dostępne opcje w menu skrótów.

## <a name="flag-and-unflag-threads"></a>Oflagowanie i usuwanie oflagowania wątków

Można oflagować wątki, aby śledzić wątki, do których chcemy zwrócić szczególną uwagę.

Oflaguj i Usuń flagę wątków z edytora kodu źródłowego lub z okna **wątków** . Wybierz, czy mają być wyświetlane tylko Oflagowane wątki, czy wszystkie wątki, z pasków narzędzi **Lokalizacja debugowania** lub **wątki** . Wybory wykonane z dowolnej lokalizacji mają wpływ na wszystkie lokalizacje.

### <a name="flag-and-unflag-threads-in-source-code"></a>Oflaguj i Usuń flagę wątków w kodzie źródłowym

1. Otwórz pasek narzędzi **lokalizacji debugowania** , wybierając pozycję **Wyświetl**  >  **paski narzędzi**  >  **Lokalizacja debugowania**. Możesz również kliknąć prawym przyciskiem myszy w obszarze paska narzędzi i wybrać pozycję **Debuguj lokalizację**.

1. Pasek narzędzi **Lokalizacja debugowania** ma trzy pola: **proces**, **wątek** i **Ramka stosu**. Listę rozwijaną listy **wątków** i należy zauważyć, ile wątków istnieje. Na liście **wątków** aktualnie wykonywany wątek jest oznaczony **>** symbolem.

1. W oknie kod źródłowy Umieść kursor nad ikoną znacznika wątku w odstępie czasu i wybierz ikonę flagi (lub jedną z pustych ikon flag) w etykietki danych. Ikona flagi zmienia kolor na czerwony.

   Możesz również kliknąć prawym przyciskiem myszy ikonę znacznika wątku, wskazać **flagę**, a następnie wybrać wątek do flagi z menu skrótów.

1. Na pasku narzędzi **Lokalizacja debugowania** wybierz ikonę **Pokaż tylko Oflagowane wątki** ![Pokaż oflagowane wątki](../debugger/media/dbg-threads-show-flagged.png "Pokaż oflagowane wątki")po prawej stronie pola **wątku** . Ikona jest wyszarzona, chyba że co najmniej jeden wątek jest oflagowany.

   Tylko oflagowany wątek jest teraz wyświetlany na liście rozwijanej **wątek** na pasku narzędzi. Aby ponownie pokazać wszystkie wątki, zaznacz ponownie ikonę **Pokaż tylko Oflagowane wątki** .

   >[!TIP]
   >Po oflagowaniu niektórych wątków można umieścić kursor w edytorze kodu, kliknąć prawym przyciskiem myszy i wybrać polecenie **Uruchom oflagowane wątki do kursora**. Upewnij się, że wybrano kod, który będzie sięgał wszystkich oflagowanych wątków. **Uruchamianie oflagowanych wątków do kursora** spowoduje wstrzymanie wątków w wybranym wierszu kodu, dzięki czemu można łatwiej kontrolować kolejność wykonywania przez [zamrożenie i odblokowywanie wątków](#bkmk_freeze).

1. Aby przełączyć stan oflagowane lub nieoflagowane aktualnie wykonywanego wątku, wybierz przycisk pojedynczej flagi **Przełącz bieżący wątek oflagowany stan** , po lewej stronie przycisku **Pokaż tylko Oflagowane wątki** . Oflagowanie bieżącego wątku jest przydatne do lokalizowania bieżącego wątku, gdy wyświetlane są tylko Oflagowane wątki.

1. Aby usunąć flagę wątku, umieść kursor nad znacznikiem wątku w kodzie źródłowym i wybierz ikonę czerwoną flagi, aby ją wyczyścić, lub kliknij prawym przyciskiem myszy znacznik wątku i wybierz polecenie Usuń **flagę**.

### <a name="flag-and-unflag-threads-in-the-threads-window"></a>Oflaguj i Usuń flagę wątków w oknie wątków

W oknie **wątki** oflagowane wątki mają flagi czerwona flaga obok nich, natomiast nieoflagowane wątki, jeśli są wyświetlane, mają puste ikony.

![Okno wątków](../debugger/media/dbg-threads-window.png "Okno wątków")

Wybierz ikonę flagi, aby zmienić stan wątku na oflagowane lub nieoflagowane, w zależności od jego bieżącego stanu.

Możesz również kliknąć prawym przyciskiem myszy wiersz i wybrać **flagę**, Usuń **flagę** lub usunąć **flagę ze wszystkich wątków** z menu skrótów.

Na pasku narzędzi okna **wątki** jest również **wyświetlany przycisk Pokaż tylko Oflagowane wątki** , który jest prawą ręką jedną z dwóch ikon flag. Działa tak samo jak przycisk na pasku narzędzi **lokalizacji debugowania** , a każdy przycisk steruje wyświetlaniem w obu lokalizacjach.

### <a name="other-threads-window-features"></a>Inne funkcje okna wątków

W oknie **wątki** wybierz nagłówek dowolnej kolumny, aby posortować wątki według tej kolumny. Wybierz ponownie, aby odwrócić porządek sortowania. Jeśli są wyświetlane wszystkie wątki, wybranie kolumny ikona flagi sortuje wątki według stanu oflagowanego lub nieoflagowanego.

Druga kolumna okna **wątków** (bez nagłówka) jest kolumną **bieżącego wątku** . Żółta strzałka w tej kolumnie oznacza bieżący punkt wykonania.

Kolumna **Location** wskazuje, gdzie każdy wątek pojawia się w kodzie źródłowym. Wybierz strzałkę rozwijania obok wpisu **lokalizacji** lub umieść wskaźnik myszy nad wpisem, aby wyświetlić częściowy stos wywołań dla tego wątku.

>[!TIP]
>Aby wyświetlić widok graficzny stosów wywołań dla wątków, użyj okna [stosów równoległych](../debugger/using-the-parallel-stacks-window.md) . Aby otworzyć okno, podczas debugowania wybierz kolejno opcje **Debuguj** >    >  **równoległe stosy** systemu Windows.

Oprócz **flagi flaga**, Usuń **flagę** i Usuń **flagę wszystkich wątków**, menu kontekstowe prawym przyciskiem myszy dla elementów okna **wątku** ma:

- Przycisk **Pokaż wątki w źródle** .
- **Wyświetlanie w formacie szesnastkowym**, które zmienia **Identyfikator wątku** s w oknie **wątki** z wartości dziesiętnych na format szesnastkowy.
- [Przełącz do wątku](#switch-to-another-thread), które natychmiast przełącza wykonywanie do tego wątku.
- **Zmień** nazwę, co pozwala zmienić nazwę wątku.
- [Zamrażanie i odblokowywanie](#bkmk_freeze) poleceń.

## <a name="freeze-and-thaw-thread-execution"></a><a name="bkmk_freeze"></a> Zamrażanie i odblokowywanie wykonywania wątku

Można zablokować i odblokować lub zawiesić i wznowić wątki, aby kontrolować kolejność, w jakiej wątki działają. Wątki zamrażające i rozmrażające mogą pomóc w rozwiązywaniu problemów współbieżności, takich jak zakleszczenie i sytuacje wyścigu.

> [!TIP]
> Aby obsłużyć pojedynczy wątek bez zamarzania innych wątków, co jest również typowym scenariuszem debugowania, zobacz Wprowadzenie [debugowanie aplikacji wielowątkowych](../debugger/get-started-debugging-multithreaded-apps.md#bkmk_follow_a_thread).

**Aby zablokować i odmrozić wątki:**

1. W oknie **wątki** kliknij prawym przyciskiem myszy dowolny wątek, a następnie wybierz polecenie **Zablokuj**. Ikona **wstrzymania** w kolumnie **bieżący wątek** wskazuje, że wątek jest zablokowany.

1. Wybierz **kolumny** na pasku narzędzi okna **wątki** , a następnie wybierz pozycję **Liczba wstrzymań** , aby wyświetlić kolumnę **Liczba wstrzymanych** . Wartość liczby wstrzymanych dla wątku zamrożonego to **1**.

1. Kliknij prawym przyciskiem myszy zablokowany wątek i wybierz polecenie **rozmrażanie**.

   Ikona **wstrzymania** znika, a wartość **Liczba wstrzymań** zostanie zmieniona na **0**.

## <a name="switch-to-another-thread"></a>Przełącz do innego wątku

Gdy próbujesz przełączyć się do innego wątku, **aplikacja jest w trybie przerwania** . To okno informuje o tym, że wątek nie ma żadnego kodu, który może być wyświetlany w bieżącym debugerze. Na przykład może być debugowany kod zarządzany, ale wątek jest kodem natywnym. Okno zawiera sugestie dotyczące rozwiązania problemu.

**Aby przełączyć się do innego wątku:**

1. W oknie **wątki** Zanotuj bieżący identyfikator wątku, który jest wątkiem z żółtą strzałką w kolumnie **bieżący wątek** . Aby kontynuować aplikację, należy przełączyć się z powrotem do tego wątku.

1. Kliknij prawym przyciskiem myszy inny wątek i wybierz polecenie **Przełącz do wątku** z menu kontekstowego.

1. Zwróć uwagę, że żółta lokalizacja strzałki została zmieniona w oknie **wątki** . Pierwotny znacznik bieżącego wątku pozostanie również w formie konspektu.

   Obejrzyj etykietkę narzędzia znacznika wątku w edytorze źródła kodu i listę na liście rozwijanej **wątek** na pasku narzędzi **Lokalizacja debugowania** . Zwróć uwagę, że bieżący wątek również został zmieniony.

1. Na pasku narzędzi **Lokalizacja debugowania** wybierz inny wątek z listy **wątków** . Należy zauważyć, że bieżący wątek zmienia się również w pozostałych dwóch lokalizacjach.

1. W edytorze kodu źródłowego kliknij prawym przyciskiem myszy znacznik wątku, wskaż polecenie **Przełącz do wątku**, a następnie wybierz inny wątek z listy. Zwróć uwagę, że bieżący wątek zmienia się we wszystkich trzech lokalizacjach.

Za pomocą znacznika wątku w kodzie źródłowym można przełączyć tylko na wątki, które są zatrzymane w tej lokalizacji. Za pomocą okna **wątki** i paska narzędzi **lokalizacji debugowania** można przełączyć się na dowolny wątek.

Znasz już podstawowe informacje na temat debugowania aplikacji wielowątkowych. Można obserwować, oflagować i flagować oraz zamrozić i odblokować wątki przy użyciu okna **wątki** , listy **wątków** na pasku narzędzi **Lokalizacja debugowania** lub znaczniki wątku w edytorze kodu źródłowego.

## <a name="see-also"></a>Zobacz też
- [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Instrukcje: przełączanie na inny wątek w trakcie debugowania](../debugger/how-to-switch-to-another-thread-while-debugging.md)
