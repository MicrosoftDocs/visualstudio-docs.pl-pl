---
title: Debugowanie aplikacji równoległych | Dokumentacja firmy Microsoft
description: Debugowanie za pomocą okna zadań równoległych i stosów przetwarzania równoległego w programie Visual Studio
ms.date: 02/14/2020
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks walkthrough
- parallel stacks toolwindow
- parallel tasks toolwindow
- parallel applications, debugging [C++]
- debugging, parallel applications
- parallel applications, debugging [Visual Basic]
- parallel applications, debugging [C#]
ms.assetid: 2820ac4c-c893-4d87-8c62-83981d561493
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c9079fc17da9f89ceae61cbd7d4f086f1db133cf
ms.sourcegitcommit: 6ef52c2030b37ea7a64fddb32f050ecfb77dd918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416428"
---
# <a name="walkthrough-debugging-a-parallel-application-in-visual-studio-c-visual-basic-c"></a>Przewodnik: debugowanie aplikacji równoległej w programie Visual StudioC#(, Visual Basic C++,)

W tym instruktażu pokazano, jak używać równoległych **zadań** i **równoległych stosów** systemu Windows do debugowania aplikacji równoległej. Te okna pomagają zrozumieć i sprawdzić zachowanie w czasie wykonywania kodu, który używa [biblioteki zadań równoległych (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) lub [środowisko uruchomieniowe współbieżności](/cpp/parallel/concrt/concurrency-runtime). Ten przewodnik zawiera przykładowy kod, który ma wbudowane punkty przerwania. Po przerwie w kodzie przewodnik pokazuje, jak używać **zadań równoległych** i **stosów równoległych** , aby je przeanalizować.

 Ten przewodnik zawiera wskazówki te zadania:

- Jak wyświetlić stosy wywołań wszystkich wątków w jednym widoku.

- Jak wyświetlić listę wystąpień `System.Threading.Tasks.Task` utworzonych w aplikacji.

- Jak wyświetlić stosy wywołań rzeczywistych zadań zamiast wątków.

- Jak nawigować do kodu z okien **zadań równoległych** i **stosów równoległych** .

- Jak windows poradzić sobie z skalę za pomocą grupowania, powiększania i inne powiązane funkcje.

## <a name="prerequisites"></a>Wymagania wstępne
 W tym instruktażu przyjęto założenie, że **tylko mój kod** jest włączona (jest włączona domyślnie w nowszych wersjach programu Visual Studio). W menu **Narzędzia** kliknij pozycję **Opcje**, rozwiń węzeł **debugowanie** , wybierz pozycję **ogólne**, a następnie wybierz pozycję **Włącz tylko mój kod (tylko zarządzane)** . Jeśli ta funkcja nie jest ustawiona, nadal można korzystać z tego przewodnika, ale wyniki mogą się różnić od przedstawionych na ilustracjach.

## <a name="c-sample"></a>Przykładowy języka C#
 Użycie przykładowy języka C#, w tym przewodniku również założenie, że kod zewnętrzny jest ukryty. Aby sprawdzić, czy jest wyświetlany kod zewnętrzny, kliknij prawym przyciskiem myszy **nazwę** nagłówka tabeli okna **stosu wywołań** , a następnie zaznacz lub wyczyść pole **Pokaż kod zewnętrzny**. Jeśli ta funkcja nie jest ustawiona, nadal można korzystać z tego przewodnika, ale wyniki mogą się różnić od przedstawionych na ilustracjach.

## <a name="c-sample"></a>Przykład w języku C++
 Jeśli używasz przykładowej języka C++, możesz zignorować odwołania do zewnętrznego kodu w tym temacie. Kod zewnętrzny dotyczy tylko przykładowy języka C#.

## <a name="illustrations"></a>Ilustracje
 Ilustracje w tym temacie są rejestrowane na komputerze czterordzeniowe działa aplikacja przykładowa języka C#. Mimo, że inne konfiguracje można użyć w celu przeprowadzenia tego instruktażu, ilustracje mogą różnić się od wyświetlanych na komputerze.

## <a name="creating-the-sample-project"></a>Tworzenie przykładowego projektu
 Przykładowy kod w tym instruktażu jest dla aplikacji, która nie wykonuje żadnych działań. Celem jest po prostu, aby zrozumieć, jak używać okien narzędzi do debugowania aplikacji równoległej.

#### <a name="to-create-the-sample-project"></a>Aby utworzyć projekt przykładowy

1. Otwórz program Visual Studio i Utwórz nowy projekt.

   ::: moniker range=">=vs-2019"

   Jeśli okno startowe nie jest otwarte, wybierz polecenie **plik** > **Start okna**.

   W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

   W oknie **Tworzenie nowego projektu** w polu wyszukiwania wpisz lub wpisz *Console* . Następnie wybierz **C#** , **C++** lub **Visual Basic** z listy język, a następnie wybierz pozycję **Windows** z listy platform. 

   Po zastosowaniu filtrów języka i platformy wybierz pozycję **aplikacja konsoli (.NET Core)** lub dla C++szablonu **Aplikacja konsolowa** , a następnie wybierz przycisk **dalej**.

   > [!NOTE]
   > Jeśli nie widzisz poprawnego szablonu, przejdź do pozycji **narzędzia** > **Pobierz narzędzia i funkcje...** , co spowoduje otwarcie Instalator programu Visual Studio. Wybierz pozycję **Programowanie aplikacji klasycznych dla platformy .NET** lub **opracowywanie aplikacji C++ klasycznych** , a następnie wybierz **Modyfikuj**.

   W oknie **Konfigurowanie nowego projektu** wpisz nazwę lub użyj nazwy domyślnej w polu **Nazwa projektu** . Następnie wybierz pozycję **Utwórz**.

   ::: moniker-end
   ::: moniker range="vs-2017"
   Na górnym pasku menu wybierz kolejno pozycje **plik** > **Nowy** > **projekt**. W lewym okienku okna dialogowego **Nowy projekt** wybierz następujące opcje:

   - W przypadku C# aplikacji w obszarze **C#Wizualizacja**wybierz pozycję **Windows Desktop**, a następnie w środkowym okienku wybierz pozycję **aplikacja konsoli (.NET Framework)** .
   - W przypadku aplikacji Visual Basic w obszarze **Visual Basic**wybierz pozycję **Windows Desktop**, a następnie w środkowym okienku wybierz pozycję **aplikacja konsoli (.NET Framework)** .
   - W przypadku C++ aplikacji w obszarze **C++Wizualizacja**wybierz pozycję **Windows Desktop**, a następnie wybierz pozycję **Aplikacja konsolowa systemu Windows**.

   Jeśli nie widzisz **aplikacji konsolowej (.NET Core)** lub C++dla programu szablonu projektu **aplikacji konsoli** , przejdź do pozycji **Narzędzia** > **Pobierz narzędzia i funkcje...** , co spowoduje otwarcie Instalator programu Visual Studio. Wybierz pozycję **Programowanie aplikacji klasycznych dla platformy .NET** lub **opracowywanie aplikacji C++ klasycznych** , a następnie wybierz **Modyfikuj**.

   Następnie wpisz nazwę lub użyj nazwy domyślnej, a następnie kliknij przycisk **OK**.

   Kliknij przycisk **OK**.
   ::: moniker-end

   Zostanie wyświetlony nowy projekt konsoli. Po utworzeniu projektu zostanie wyświetlony plik źródłowy.

1. Otwórz plik kodu .cpp, .cs lub .vb w projekcie. Usunąć jej zawartość, aby utworzyć plik pusty kod.

1. Wklej następujący kod w języku wybranym do pliku kodu pusty.

   [!code-csharp[Debugger#1](../debugger/codesnippet/CSharp/walkthrough-debugging-a-parallel-application_1.cs)]
   [!code-cpp[Debugger#1](../debugger/codesnippet/CPP/walkthrough-debugging-a-parallel-application_1.cpp)]
   [!code-vb[Debugger#1](../debugger/codesnippet/VisualBasic/walkthrough-debugging-a-parallel-application_1.vb)]

1. W menu **plik** kliknij polecenie **Zapisz wszystko**.

1. W menu **kompilacja** kliknij polecenie **Kompiluj ponownie rozwiązanie**.

    Należy zauważyć, że istnieją cztery wywołania `Debugger.Break` (`DebugBreak` w C++ próbce), dlatego nie trzeba wstawiać punktów przerwania; po prostu uruchomienie aplikacji spowoduje jej przerwanie w debugerze do czterech razy.

## <a name="using-the-parallel-stacks-window-threads-view"></a>Za pomocą równoległych stosów okna: widoku wątków
 W menu **debugowanie** kliknij **Rozpocznij debugowanie**. Poczekaj, aż pierwszy punkt przerwania, aby zostanie osiągnięty.

#### <a name="to-view-the-call-stack-of-a-single-thread"></a>Aby wyświetlić stos wywołań jest jeden wątek

1. W menu **debugowanie** wskaż polecenie **Windows** , a następnie kliknij pozycję **wątki**. Zadokuj okno **wątków** w dolnej części programu Visual Studio.

2. W menu **debugowanie** wskaż polecenie **Windows** , a następnie kliknij pozycję **stos wywołań**. Zadokuj okno **stosu wywołań** w dolnej części programu Visual Studio.

3. Kliknij dwukrotnie wątek w oknie **wątki** , aby go zmienić. Wątki bieżącego mają żółta strzałka. Po zmianie bieżącego wątku jego stos wywołań jest wyświetlany w oknie **stosu wywołań** .

#### <a name="to-examine-the-parallel-stacks-window"></a>Aby sprawdzić z okna stosów równoległych

1. W menu **debugowanie** wskaż polecenie **Windows** , a następnie kliknij pozycję **stosy równoległe**. Upewnij się, że w polu w lewym górnym rogu zaznaczone są **wątki** .

     Korzystając z okna **stosów równoległych** , można wyświetlać wiele stosów wywołań jednocześnie w jednym widoku. Na poniższej ilustracji przedstawiono okno **stosów równoległych** nad oknem **stosu wywołań** .

     ![Widok wątków w oknie stosów równoległych](../debugger/media/pdb_walkthrough_1.png "PDB_Walkthrough_1")

     Stos wywołań wątku głównego, który pojawia się w jednym z pól i stosy wywołań cztery wątki są grupowane w innym polu. Cztery wątki są pogrupowane ze względu na to, że ich ramki stosu korzystają z tych samych kontekstów metody; oznacza to, że znajdują się w tych samych metodach: `A`, `B`i `C`. Aby wyświetlić identyfikatory wątku i nazwy wątków, które współużytkują to samo pole, umieść kursor nad polem z nagłówkiem (**4 wątki**). Bieżący wątek jest wyświetlany czcionką pogrubioną.

     ![Etykietka narzędzia pokazująca identyfikatory i nazwy wątków](../debugger/media/pdb_walkthrough_1a.png "PDB_Walkthrough_1A")

     Żółta strzałka wskazuje aktywną ramkę stosu bieżącego wątku.

     Można ustawić, ile szczegółów ma być pokazywanych dla ramek stosu (**nazw modułów**, **typów parametrów**, **nazw parametrów**, **wartości parametrów**, **numerów wierszy** i **przesunięć bajtów**), klikając prawym przyciskiem myszy w oknie **stos wywołań** .

     Niebieskie podświetlenie wokół pola wskazuje, czy bieżący wątek jest częścią tego pola. Ramki stosu pogrubienia w etykietce narzędzia również wskazuje bieżącego wątku. W przypadku dwukrotnego kliknięcia wątku głównego w oknie wątki można obserwować, że niebieskie podświetlenie w oknie **stosów równoległych** jest odpowiednio przenoszone.

     ![Podświetlony główny wątek w oknie stosów równoległych](../debugger/media/pdb_walkthrough_1c.png "PDB_Walkthrough_1C")

#### <a name="to-resume-execution-until-the-second-breakpoint"></a>Aby wznowić wykonywanie aż do drugiego punktu przerwania

1. Aby wznowić wykonywanie do momentu, gdy drugi punkt przerwania zostanie osiągnięty, w menu **debugowanie** kliknij przycisk **Kontynuuj**. Poniższa ilustracja przedstawia drzewo wątku na drugi punkt przerwania.

     ![Okno stosów równoległych pokazujące wiele gałęzi](../debugger/media/pdb_walkthrough_2.png "PDB_Walkthrough_2")

     W pierwszym punkcie przerwania wszystkie cztery wątki zmieniał się od S.A do S.B S.C metod. Te informacje są nadal widoczne w oknie **stosów równoległych** , ale cztery wątki mają dalsze postępy. Jeden z nich nadal S.D, a następnie Południowowschodnia Inny ciąg dalszy S.F S.G oraz S.H. Dwie pozostałe nadal S.I i S.J oraz z jednej dla jednej z nich próby S.K i innych nadal kod zewnętrzny niezwiązanych z użytkownikiem.

     Możesz umieścić kursor na nagłówku pola, na przykład **1 wątek** lub **2 wątki**, aby wyświetlić identyfikatory wątków wątków. Możesz umieścić kursor ramek stosu, aby wyświetlić identyfikatory wątków oraz inne szczegóły ramek. Niebieskie podświetlenie oznacza bieżący wątek, a żółta strzałka wskazuje aktywną ramkę stosu bieżącego wątku.

     Ikona ręczników wątków (interweaved wierszy) wskazują ramek stosu active nieaktualnych wątków. W oknie **stos wywołań** kliknij dwukrotnie przycisk S, aby przełączyć ramki. Okno **stosów równoległych** wskazuje bieżącą ramkę stosu bieżącego wątku przy użyciu zielonej ikony strzałki zakrzywionej.

     W oknie **wątki** Przełącz się między wątkami i sprawdź, czy widok w oknie **stosów równoległych** został zaktualizowany.

     Możesz przełączyć się do innego wątku lub do innej ramki innego wątku, używając menu skrótów w oknie **stosów równoległych** . Na przykład kliknij prawym przyciskiem myszy pozycję S. J, wskaż polecenie **Przełącz na ramkę**, a następnie kliknij polecenie.

     ![Równoległe stosy ścieżek wykonywania](../debugger/media/pdb_walkthrough_2b.png "PDB_Walkthrough_2B")

     Kliknij prawym przyciskiem myszy pozycję S. C i wskaż polecenie **Przełącz do ramki**. Jedno z poleceń ma znacznik wyboru wskazujący ramka stosu w bieżącym wątku. Możesz przełączyć się do tej ramki w tym samym wątku (przeniesie zieloną strzałkę), lub możesz przełączyć się do innego wątku (niebieskie podświetlenie przenosi także). Poniższa ilustracja przedstawia podmenu.

     ![Menu stosów z 2 opcjami w języku C, a J jest bieżąca](../debugger/media/pdb_walkthrough_3.png "PDB_Walkthrough_3")

     Gdy kontekst metody jest skojarzony tylko z jedną ramką stosu, w nagłówku pola jest wyświetlany **1 wątek** i można przełączyć się do niego, klikając dwukrotnie. Jeśli klikniesz dwukrotnie kontekst metody, który ma więcej niż 1 ramkę skojarzonych z nim, następnie menu automatycznie pojawi się. Jak wskaźnik nad kontekstów metody, zwróć uwagę, czarny trójkąt po prawej stronie. Ponadto kliknięcie tego trójkąt Wyświetla menu skrótów.

     Dla dużych aplikacji, które mają wiele wątków można skoncentrować się na określony podzbiór wątków. Okno **stosów równoległych** może wyświetlać stosy wywołań tylko dla wątków oflagowanych. Aby Oflaguj wątki, należy użyć menu skrótów lub pierwszej komórki wątku.

     Na pasku narzędzi kliknij przycisk **Pokaż tylko Oflagowane** obok pola listy.

     ![Okno i etykietka narzędzia stosów równoległych](../debugger/media/pdb_walkthrough_3a.png "PDB_Walkthrough_3A")

     Teraz tylko Oflagowane wątki pojawiają się w oknie **stosów równoległych** .

#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Aby wznowić wykonywanie aż do trzeciego punktu przerwania

1. Aby wznowić wykonywanie do momentu, gdy trzeci punkt przerwania zostanie osiągnięty, w menu **debugowanie** kliknij przycisk **Kontynuuj**.

     Wiele wątków znajdują się w tej samej metody, ale metoda nie jest na początku stos wywołań, metoda pojawia się w różnych polach. S.L, zawiera trzy wątków, która jest wyświetlana w trzy pola to na przykład w bieżącym punkcie przerwania. Kliknij dwukrotnie opcję Brak miejsca

     ![Ścieżka wykonywania w oknie stosów równoległych](../debugger/media/pdb_walkthrough_3b.png "PDB_Walkthrough_3B")

     Zauważ, że S.L jest pogrubiony w innych polach, dzięki czemu można zobaczyć, gdzie indziej pojawia się. Jeśli chcesz zobaczyć, które ramki są wywoływane do S. L i które ramki wywołuje, kliknij przycisk **Przełącz widok metody** na pasku narzędzi. Na poniższej ilustracji przedstawiono widok metody okna **stosów równoległych** .

     ![Widok metody w oknie stosów równoległych](../debugger/media/pdb_walkthrough_4.png "PDW_Walkthrough_4")

     Zwróć uwagę, jak diagramu przestawiać na wybranej metody i umieszczony ją w swoje własne polu w środku widoku. Wywoływane a obiektami wywołującymi są wyświetlane u góry i u dołu. Kliknij ponownie przycisk **Przełącz widok metody** , aby opuścić ten tryb.

     Menu skrótów okna **stosów równoległych** ma również następujące inne elementy.

    - **Wyświetlacz szesnastkowy** przełącza liczby w etykietach narzędzi między dziesiętną i szesnastkową.

    - **Ustawienia symboli** otwierają odpowiednie okna dialogowe.

    - **Pokaż wątki w źródle** powoduje przełączenie wyświetlania znaczników wątków w kodzie źródłowym, który pokazuje lokalizację wątków w kodzie źródłowym.

    - **Pokaż kod zewnętrzny** wyświetla wszystkie ramki nawet wtedy, gdy nie znajdują się one w kodzie użytkownika. Wypróbuj ją, aby wyświetlić diagram Rozwiń, aby uwzględnić dodatkowe ramki, (które mogą być nieaktywne, ponieważ nie masz symboli dla nich).

2. W oknie **stosów równoległych** upewnij się, że przycisk **Autoprzewijanie do bieżącej ramki stosu** znajduje się na pasku narzędzi.

     Jeśli masz dużych diagramów w kroku do następnego punktu przerwania, może być widok, aby automatycznie przewiń do aktywną ramkę stosu bieżącego wątku; oznacza to, że wątek, który najpierw trafiony punkt przerwania.

3. Przed kontynuowaniem w oknie **stosów równoległych** przewiń cały widok w lewo i w dół.

#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Aby wznowić wykonywanie aż do czwartej punktu przerwania

1. Aby wznowić wykonywanie do momentu, gdy czwarty punkt przerwania zostanie osiągnięty, w menu **debugowanie** kliknij przycisk **Kontynuuj**.

     Zwróć uwagę jak autoscrolled widoku w miejscu. Przełącz wątki w oknie **wątki** lub Przełącz ramki stosu w oknie **stos wywołań** i zwróć uwagę na to, jak widok zawsze przewija do właściwej ramki. Wyłącz opcję **Automatyczne przewijanie do bieżącej ramki narzędzia** i Sprawdź różnicę.

     **Widok oka ptaka** pomaga również w przypadku dużych diagramów w oknie **stosów równoległych** . Domyślnie **Widok oka ptaka** jest włączony. Ale można ją wyłączyć, klikając przycisk między pasków przewijania w prawym dolnym rogu okna, jak pokazano na poniższej ilustracji.

     ![Widok&#45;oka ptaka w oknie stosów równoległych](../debugger/media/pdb_walkthrough_5.png "PDB_Walkthrough_5")

     W widok można przenieść prostokąt, Przesuń szybko w całym na diagramie.

     Innym sposobem na przenoszenie diagramu w dowolnym kierunku jest do pustego obszaru diagramu, kliknij i przeciągnij go w odpowiednie miejsce.

     Aby powiększyć i diagramu, naciśnij i przytrzymaj klawisz CTRL podczas przenoszenia kółka myszy. Alternatywnie kliknij przycisku Powiększenie na pasku narzędzi, a następnie użyj narzędzie do powiększania.

     Możesz również wyświetlić stosy w kierunku góry zamiast na dole, klikając menu **Narzędzia** , klikając polecenie **Opcje**, a następnie wybierając lub wyczyścić opcję w obszarze węzła **debugowanie** .

2. Przed kontynuowaniem w menu **debugowanie** kliknij polecenie **Zatrzymaj debugowanie** , aby zakończyć wykonywanie.

## <a name="using-the-parallel-tasks-window-and-the-tasks-view-of-the-parallel-stacks-window"></a>Za pomocą okno zadań równoległych i widok zadań z okna stosów równoległych
 Zalecane jest, wykonaj wcześniejsze procedury, aby kontynuować.

#### <a name="to-restart-the-application-until-the-first-breakpoint-is-hit"></a>Uruchom aplikację do momentu pierwszy punkt przerwania zostaje trafiony

1. W menu **debugowanie** kliknij **Rozpocznij debugowanie** i poczekaj na naciśnięcie pierwszego punktu przerwania.

2. W menu **debugowanie** wskaż polecenie **Windows** , a następnie kliknij pozycję **wątki**. Zadokuj okno **wątków** w dolnej części programu Visual Studio.

3. W menu **debugowanie** wskaż polecenie **Windows** i kliknij pozycję **stos wywołań**. Zadokuj okno **stosu wywołań** w dolnej części programu Visual Studio.

4. Kliknij dwukrotnie wątek w oknie **wątki** , aby go bieżące. Wątki bieżącego mają żółtą strzałką. Inne okna są aktualizowane, po zmianie bieżącego wątku. Następnie zostanie omówiony zadania.

5. W menu **debugowanie** wskaż polecenie **Windows**, a następnie kliknij pozycję **zadania**. Na poniższej ilustracji przedstawiono okno **zadania** .

     ![Cztery uruchomione zadania w oknie zadań](../debugger/media/pdb_walkthrough_6.png "PDW_Walkthrough_6")

     Dla każdego uruchomionego zadania można odczytać Identyfikatora, który jest zwracany przez właściwość o tej samej nazwie, identyfikator i nazwę wątku, który działa, jego lokalizacji (przesuwania wskaźnika w obrębie tego wyświetla etykietkę narzędzia, która ma całego stosu). Ponadto w kolumnie **zadanie** można zobaczyć metodę, która została przeniesiona do zadania; Innymi słowy, punkt początkowy.

     Można sortować dowolnej kolumny. Zwróć uwagę, symbol sortowania, który wskazuje sortowanie kolumn i kierunek. Można również zmienić kolejność kolumn, przeciągając je w lewo lub w prawo.

     Żółta strzałka wskazuje bieżącego zadania. Zadania można przełączać, klikając dwukrotnie zadania lub za pomocą menu skrótów. Po przełączeniu się z zadaniami, podstawowy wątek staje się bieżącym i inne okna są aktualizowane.

     Ręcznie przełączyć się z jednego zadania do innego, żółta strzałka przesuwa się, ale biały strzałek nadal zawiera zadania, który spowodował debuger przerywa.

#### <a name="to-resume-execution-until-the-second-breakpoint"></a>Aby wznowić wykonywanie aż do drugiego punktu przerwania

1. Aby wznowić wykonywanie do momentu, gdy drugi punkt przerwania zostanie osiągnięty, w menu **debugowanie** kliknij przycisk **Kontynuuj**.

     Wcześniej w kolumnie **stan** są wyświetlane wszystkie zadania jako aktywne, ale teraz są blokowane dwa z zadań. Zadania mogą zostać zablokowane w wielu różnych powodów. W kolumnie **stan** Umieść kursor nad zadaniem oczekującym, aby dowiedzieć się, dlaczego jest on zablokowany. Na przykład na poniższej ilustracji, zadanie 3 oczekuje na zadanie 4.

     ![Dwa zadania oczekujące w oknie zadań](../debugger/media/pdb_walkthrough_7.png "PDB_Walkthrough_7")

     Zadanie 4, z kolei czeka na monitorze własnością wątku przydzielony do zadania 2. (Kliknij prawym przyciskiem myszy wiersz nagłówka i wybierz **kolumny** > **przypisanie wątku** , aby wyświetlić wartość przypisania wątku dla zadania 2).

     ![Oczekujące zadanie i etykietka narzędzia w oknie zadań](../debugger/media/pdb_walkthrough_7a.png "PDB_Walkthrough_7A")

     Można oflagować zadanie, klikając flagę w pierwszej kolumnie okna **zadania** .

     Można użyć oflagowania do śledzenia zadań między różnymi punktami przerwania w tej samej sesji debugowania lub do filtrowania zadań, których stosy wywołań są wyświetlane w oknie **stosów równoległych** .

     Gdy wcześniej użyto okna **stosów równoległych** , oglądasz wątki aplikacji. Ponownie Wyświetl okno **stosów równoległych** , ale ten czas wyświetli zadania aplikacji. W tym celu wybierz pozycję **zadania** w polu w lewym górnym rogu. Na poniższej ilustracji przedstawiono zadania.

     ![Widok zadań w oknie stosów równoległych](../debugger/media/pdb_walkthrough_8.png "PDB_Walkthrough_8")

     Wątki, które nie są aktualnie wykonywane zadania, nie są wyświetlane w widoku zadania okna **stosów równoległych** . Ponadto dla wątków, które są wykonywane zadania, niektóre ramek stosu, które nie mają znaczenia dla zadania są filtrowane z górnej i dolnej części stosu.

     Ponownie Wyświetl okno **zadań** . Kliknij prawym przyciskiem myszy nagłówek dowolnej kolumny, aby wyświetlić menu skrótów dla kolumny.

     Aby dodać lub usunąć kolumny, można użyć menu skrótów. Na przykład nie jest zaznaczone kolumny domeny aplikacji; w związku z tym nie jest wyświetlany na liście. Kliknij przycisk **nadrzędne**. Kolumna **nadrzędna** jest wyświetlana bez wartości dla żadnego z czterech zadań.

#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Aby wznowić wykonywanie aż do trzeciego punktu przerwania

1. Aby wznowić wykonywanie do momentu, gdy trzeci punkt przerwania zostanie osiągnięty, w menu **debugowanie** kliknij przycisk **Kontynuuj**.

     Nowe zadanie zadanie 5, jest teraz uruchomiona i obecnie oczekuje zadanie 4. Możesz sprawdzić, czy kursor znajduje się nad zadaniem oczekującym w oknie **stanu** . Zwróć uwagę, że zadanie 4 jest elementem nadrzędnym zadania 5 w kolumnie **nadrzędnej** .

     Aby lepiej wizualizować relację nadrzędny-podrzędny, kliknij prawym przyciskiem myszy wiersz nagłówka kolumny, a następnie kliknij pozycję **nadrzędny widok podrzędny**. Powinny być widoczne na poniższej ilustracji.

     ![Nadrzędny&#45;widok podrzędny w oknie zadania](../debugger/media/pdb_walkthrough_9.png "PDB_Walkthrough_9")

     Zwróć uwagę, że zadanie 4 i zadanie 5 są uruchomione w tym samym wątku (Pokaż kolumnę **przypisania wątku** , jeśli jest ukryta). Te informacje nie są wyświetlane w oknie **wątki** ; wyświetlenie go w tym miejscu jest kolejną zaletą okna **zadań** . Aby to potwierdzić, Wyświetl okno **stosów równoległych** . Upewnij się, że oglądasz **zadania**. Zlokalizuj zadania 4 i 5, klikając je dwukrotnie w oknie **zadania** . Gdy to zrobisz, zostanie zaktualizowane niebieskie podświetlenie w oknie **stosów równoległych** . Możesz również zlokalizować zadania 4 i 5, skanując etykietki narzędzi w oknie **stosów równoległych** .

     ![Widok zadań w oknie stosów równoległych](../debugger/media/pdb_walkthrough_9a.png "PDB_Walkthrough_9A")

     W oknie **stosów równoległych** kliknij prawym przyciskiem myszy pozycję S. P, a następnie kliknij polecenie **Przejdź do wątku**. Okno przełącza do widoku wątków i odpowiednie ramki znajduje się w widoku. Zarówno do zadań są widoczne na tym samym wątku.

     ![Wyróżniony wątek w widoku wątków](../debugger/media/pdb_walkthrough_9b.png "PDB_Walkthrough_9B")

     Jest to kolejna korzyść w widoku zadania w oknie **stosów równoległych** w porównaniu do okna **wątki** .

#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Aby wznowić wykonywanie aż do czwartej punktu przerwania

1. Aby wznowić wykonywanie do momentu, gdy trzeci punkt przerwania zostanie osiągnięty, w menu **debugowanie** kliknij przycisk **Kontynuuj**. Kliknij nagłówek kolumny **ID** , aby posortować według identyfikatora. Powinny być widoczne na poniższej ilustracji.

     ![Cztery Stany zadań w oknie stosów równoległych](../debugger/media/pdb_walkthrough_10.png "PDB_Walkthrough_10")

     Ponieważ zadanie 5 zostało ukończone, jest już wyświetlany. Jeśli nie jest to przypadek na komputerze, a zakleszczenie nie jest wyświetlane, krok jeden raz, naciskając klawisz **F11**.

     Zadanie 3 zadanie 4 teraz oczekują od siebie i są blokowane. Dostępne są także 5 nowych zadań, które są elementami podrzędnymi zadanie 2, a teraz są planowane. Zaplanowane zadania są zadania, które zostały rozpoczęte w kodzie, ale nie zostały jeszcze uruchomione. W związku z tym kolumny ich **lokalizacji** i **przypisania wątku** są puste.

     Ponownie Wyświetl okno **stosów równoległych** . Nagłówek każde pole ma etykietkę narzędzia, która zawiera nazwy i identyfikatory wątku. Przejdź do widoku zadania w oknie **stosów równoległych** . Umieść kursor nad nagłówek, aby wyświetlić identyfikator zadania oraz nazwę i stan zadania, jak pokazano na poniższej ilustracji.

     ![Etykietka narzędzia nagłówka w oknie stosów równoległych](../debugger/media/pdb_walkthrough_11.png "PDB_Walkthrough_11")

     Zadania można grupować według kolumny. W oknie **zadania** kliknij prawym przyciskiem myszy nagłówek kolumny **stan** , a następnie kliknij pozycję **Grupuj według stanu**. Na poniższej ilustracji przedstawiono okno **zadania** pogrupowane według stanu.

     ![Pogrupowane zadania w oknie zadań](../debugger/media/pdb_walkthrough_12.png "PDB_Walkthrough_12")

     Można także grupować według innych kolumn. Przez grupowanie zadania można skoncentrować się na podzbiór zadań. Każda grupa zwijany ma liczbę elementów, które są zgrupowane.

     Ostatnia funkcja okna **zadania** do sprawdzenia jest menu skrótów, które jest wyświetlane po kliknięciu prawym przyciskiem myszy zadania.

     Menu skrótów zostaną wyświetlone różne polecenia, w zależności od stanu zadania. Polecenia mogą zawierać polecenie **Kopiuj**, **Zaznacz wszystko**, **Wyświetlanie w formacie szesnastkowym**, **Przełącz do zadania**, **Zablokuj przypisany wątek**, **Zablokuj wszystkie wątki, ale ten**i odblokowuje **przypisany wątek**oraz **flagę**.

     Można zamrozić wątku podstawowym zadania lub zadania, lub można zablokować wszystkich wątków, z wyjątkiem przypisane. Wątek zamrożony jest reprezentowany w oknie **zadania** , jak w oknie **wątki** , przez niebieską ikonę *pauzy* .

## <a name="summary"></a>Podsumowanie
 W tym instruktażu przedstawiono okna debugera **zadań równoległych** i **stosów równoległych** . Użyj tych okien na rzeczywistych projektach, korzystających z kodu wielowątkowego. Można sprawdzić równoległego kodu napisanego w języku C++, C# lub Visual Basic.

## <a name="see-also"></a>Zobacz też
- [Debugowanie aplikacji wielowątkowych](../debugger/walkthrough-debugging-a-parallel-application.md)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)
- [Programowanie równoległe](/dotnet/standard/parallel-programming/index)
- [Środowisko uruchomieniowe współbieżności](/cpp/parallel/concrt/concurrency-runtime)
- [Korzystanie z okna stosów równoległych](../debugger/using-the-parallel-stacks-window.md)
- [Korzystanie z okna zadań](../debugger/using-the-tasks-window.md)