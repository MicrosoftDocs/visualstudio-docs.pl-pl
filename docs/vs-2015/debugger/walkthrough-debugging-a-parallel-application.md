---
title: 'Przewodnik: Debugowanie aplikacji równoległych | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ad496bb55bae8d9e08035408059e454430ab4e39
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705279"
---
# <a name="walkthrough-debugging-a-parallel-application"></a>Przewodnik: Debugowanie aplikacji równoległych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten poradnik pokazuje jak używać **zadań równoległych** i **stosów równoległych** systemu windows do debugowania aplikacji równoległej. Te okna pomaga zrozumieć i zweryfikować zachowanie środowiska uruchomieniowego kodu, który używa [Biblioteka zadań równoległych (TPL)](https://msdn.microsoft.com/library/b8f99f43-9104-45fd-9bff-385a20488a23) lub [współbieżność środowiska wykonawczego](https://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c). Ten przewodnik zawiera przykładowy kod, który ma wbudowane punkty przerwania. Po kodu przerywa, instruktaż przedstawia sposób użycia **zadań równoległych** i **stosów równoległych** systemu windows, aby go sprawdzić.  
  
 Ten przewodnik zawiera wskazówki te zadania:  
  
- Jak wyświetlić stosy wywołań wszystkich wątków w jednym widoku.  
  
- Jak wyświetlić listę `System.Threading.Tasks.Task` wystąpień, które są tworzone w aplikacji.  
  
- Jak wyświetlić stosy wywołań rzeczywistych zadań zamiast wątków.  
  
- Jak nawigować do kodu ze **zadań równoległych** i **stosów równoległych** systemu windows.  
  
- Jak windows poradzić sobie z skalę za pomocą grupowania, powiększania i inne powiązane funkcje.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym przewodniku założono, że **tylko mój kod** jest włączona. Na **narzędzia** menu, kliknij przycisk **opcje**, rozwiń węzeł **debugowanie** węzła, wybierz opcję **ogólne**, a następnie wybierz **Włącz Tylko mój kod (tylko zarządzany)** . Jeśli ta funkcja nie jest ustawiona, nadal można korzystać z tego przewodnika, ale wyniki mogą się różnić od przedstawionych na ilustracjach.  
  
## <a name="c-sample"></a>Przykładowy języka C#  
 Użycie przykładowy języka C#, w tym przewodniku również założenie, że kod zewnętrzny jest ukryty. Do wyświetlania i ukrywania kod zewnętrzny jest wyświetlany, kliknij prawym przyciskiem myszy **nazwa** nagłówek tabeli **stos wywołań** okna, a następnie zaznacz lub usuń zaznaczenie **Pokaż kod zewnętrzny**. Jeśli ta funkcja nie jest ustawiona, nadal można korzystać z tego przewodnika, ale wyniki mogą się różnić od przedstawionych na ilustracjach.  
  
## <a name="c-sample"></a>Przykład w języku C++  
 Jeśli używasz przykładowej języka C++, możesz zignorować odwołania do zewnętrznego kodu w tym temacie. Kod zewnętrzny dotyczy tylko przykładowy języka C#.  
  
## <a name="illustrations"></a>Ilustracje  
 Ilustracje w tym temacie są rejestrowane na komputerze czterordzeniowe działa aplikacja przykładowa języka C#. Mimo, że inne konfiguracje można użyć w celu przeprowadzenia tego instruktażu, ilustracje mogą różnić się od wyświetlanych na komputerze.  
  
## <a name="creating-the-sample-project"></a>Tworzenie przykładowego projektu  
 Przykładowy kod w tym instruktażu jest dla aplikacji, która nie wykonuje żadnych działań. Celem jest po prostu, aby zrozumieć, jak używać okien narzędzi do debugowania aplikacji równoległej.  
  
#### <a name="to-create-the-sample-project"></a>Aby utworzyć projekt przykładowy  
  
1. W programie Visual Studio na **pliku** menu wskaż **New** a następnie kliknij przycisk **projektu**.  
  
2. W **zainstalowane szablony** okienku wybierz opcję Visual C#, Visual Basic lub Visual C++. W przypadku języków zarządzanych, upewnij się, że [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] jest wyświetlana w polu framework.  
  
3. Wybierz **aplikację Konsolową** a następnie kliknij przycisk **OK**. Pozostają w konfiguracji debugowania, co jest ustawieniem domyślnym.  
  
4. Otwórz plik kodu .cpp, .cs lub .vb w projekcie. Usunąć jej zawartość, aby utworzyć plik pusty kod.  
  
5. Wklej następujący kod w języku wybranym do pliku kodu pusty.  
  
   [!code-cpp[Debugger#1](../snippets/cpp/VS_Snippets_Misc/debugger/cpp/beta2_native.cpp#1)]
   [!code-csharp[Debugger#1](../snippets/csharp/VS_Snippets_Misc/debugger/cs/s.cs#1)]
   [!code-vb[Debugger#1](../snippets/visualbasic/VS_Snippets_Misc/debugger/vb/module1.vb#1)]  
  
6. Na **pliku** menu, kliknij przycisk **Zapisz wszystko**.  
  
7. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
    Należy zauważyć, że nie istnieją cztery wywołania `Debugger.Break` (`DebugBreak` w przykładzie w języku C++) w związku z tym, nie trzeba wstawić punktów przerwania; po prostu działania aplikacji spowoduje jego przerwanie w debugerze maksymalnie cztery razy.  
  
## <a name="using-the-parallel-stacks-window-threads-view"></a>Korzystanie z okna stosów równoległych: Widok wątków  
 Na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie**. Poczekaj, aż pierwszy punkt przerwania, aby zostanie osiągnięty.  
  
#### <a name="to-view-the-call-stack-of-a-single-thread"></a>Aby wyświetlić stos wywołań jest jeden wątek  
  
1. Na **debugowania** menu wskaż **Windows** a następnie kliknij przycisk **wątków**. Zadokuj **wątków** okna w dolnej części programu Visual Studio.  
  
2. Na **debugowania** menu wskaż **Windows** a następnie kliknij przycisk **stos wywołań**. Zadokuj **stos wywołań** okna u dołu Visual Studio.  
  
3. Kliknij dwukrotnie wątek na **wątków** okno do bieżącego. Wątki bieżącego mają żółta strzałka. Po zmianie bieżącego wątku, stos wywołań jest wyświetlany w **stos wywołań** okna.  
  
#### <a name="to-examine-the-parallel-stacks-window"></a>Aby sprawdzić z okna stosów równoległych  
  
1. Na **debugowania** menu wskaż **Windows** a następnie kliknij przycisk **stosów równoległych**. Upewnij się, że **wątków** jest zaznaczona w polu w lewym górnym rogu.  
  
     Za pomocą **stosów równoległych** okna, można wyświetlić wiele stosy wywołań w tym samym czasie w jednym widoku. Poniższa ilustracja przedstawia **stosów równoległych** okna powyżej **stos wywołań** okna.  
  
     ![Widok okna stosów równoległych wątków](../debugger/media/pdb-walkthrough-1.png "PDB_Walkthrough_1")  
  
     Stos wywołań wątku głównego, który pojawia się w jednym z pól i stosy wywołań cztery wątki są grupowane w innym polu. Cztery wątki są zgrupowane razem, ponieważ ich ramek stosu współużytkują ten sam kontekst metody; oznacza to, że znajdują się w tej samej metody: `A`, `B`, i `C`. Do widoku wątków identyfikatory i nazwy wątki, które współużytkują tego samego pola, umieść kursor nad nagłówka (**4 wątków**). Bieżący wątek jest wyświetlany w pogrubienie, jak pokazano na poniższej ilustracji.  
  
     ![Etykietka narzędzia, pokazujący wątku identyfikatorów i nazw](../debugger/media/pdb-walkthrough-1a.png "PDB_Walkthrough_1A")  
  
     Żółta strzałka wskazuje aktywną ramkę stosu bieżącego wątku. Aby uzyskać więcej informacji, umieść kursor nad nią  
  
     ![Etykietka narzędzia na aktywną ramkę stosu](../debugger/media/pdb-walkthrough-1b.png "PDB_Walkthrough_1B")  
  
     Możesz ustawić ilość szczegółów, aby pokazać ramek stosu (**nazwy modułów**, **typy parametrów**, **nazwy parametrów**, **wartości parametrów**, **Numery wierszy** i **przesunięcia bajtów**) klikając prawym przyciskiem myszy **stos wywołań** okna.  
  
     Niebieskie podświetlenie wokół pola wskazuje, czy bieżący wątek jest częścią tego pola. Ramki stosu pogrubienia w etykietce narzędzia również wskazuje bieżącego wątku. Jeśli klikniesz dwukrotnie wątek główny w oknie wątki, można zaobserwować, że niebieskie podświetlenie w **stosów równoległych** okna przenosi się odpowiednio.  
  
     ![Wyróżnione wątek główny w okna stosów równoległych](../debugger/media/pdb-walkthrough-1c.png "PDB_Walkthrough_1C")  
  
#### <a name="to-resume-execution-until-the-second-breakpoint"></a>Aby wznowić wykonywanie aż do drugiego punktu przerwania  
  
1. Aby wznowić wykonywanie do momentu drugi punkt przerwania zostaje trafiony, na **debugowania** menu, kliknij przycisk **Kontynuuj**. Poniższa ilustracja przedstawia drzewo wątku na drugi punkt przerwania.  
  
     ![Okno stosów równoległych, który zawiera wiele gałęzi](../debugger/media/pdb-walkthrough-2.png "PDB_Walkthrough_2")  
  
     W pierwszym punkcie przerwania wszystkie cztery wątki zmieniał się od S.A do S.B S.C metod. Informacji o nadal widoczne w **stosów równoległych** okna, ale cztery wątki osiągnięcia postępu dalej. Jeden z nich nadal S.D, a następnie Południowowschodnia Inny ciąg dalszy S.F S.G oraz S.H. Dwie pozostałe nadal S.I i S.J oraz z jednej dla jednej z nich próby S.K i innych nadal kod zewnętrzny niezwiązanych z użytkownikiem.  
  
     Możesz umieścić kursor pole nagłówka, na przykład **1 wątek** lub **2 wątkach**, aby wyświetlić identyfikatory wątków wątek. Możesz umieścić kursor ramek stosu, aby wyświetlić identyfikatory wątków oraz inne szczegóły ramek. Niebieskie podświetlenie oznacza bieżący wątek, a żółta strzałka wskazuje aktywną ramkę stosu bieżącego wątku.  
  
     Ikona ręczników wątków (nakładających się niebieskie i czerwone waved linie) wskazują ramek stosu active nieaktualnych wątków. W **stos wywołań** okna, kliknij dwukrotnie S.B na przełączanie ramek. **Stosów równoległych** okno wskazuje bieżącej ramki stosu w bieżącym wątku, przy użyciu ikony zielony zakrzywioną strzałką.  
  
     W **wątków** okna, przełącz się między wątkami i Zauważ, że widok w **stosów równoległych** okna jest aktualizowana.  
  
     Można przełączyć do innego wątku lub do innej ramki innego wątku za pomocą menu skrótów na liście **stosów równoległych** okna. Na przykład, kliknij prawym przyciskiem myszy S.J, wskaż opcję **Przełącz do ramki**, a następnie kliknij przycisk polecenia.  
  
     ![Ścieżka wykonywania stosów równoległych](../debugger/media/pdb-walkthrough-2b.png "PDB_Walkthrough_2B")  
  
     Kliknij prawym przyciskiem myszy S.C, a następnie wskaż **Przełącz do ramki**. Jedno z poleceń ma znacznik wyboru wskazujący ramka stosu w bieżącym wątku. Możesz przełączyć się do tej ramki w tym samym wątku (przeniesie zieloną strzałkę), lub możesz przełączyć się do innego wątku (niebieskie podświetlenie przenosi także). Poniższa ilustracja przedstawia podmenu.  
  
     ![Menu stosów przy użyciu opcji 2 na C "j" jest bieżący](../debugger/media/pdb-walkthrough-3.png "PDB_Walkthrough_3")  
  
     Po skojarzone z ramki stosu tylko jeden kontekst metody nagłówek okno wyświetla **1 wątek** i możesz przełączyć się do niego przez dwukrotne kliknięcie. Jeśli klikniesz dwukrotnie kontekst metody, który ma więcej niż 1 ramkę skojarzonych z nim, następnie menu automatycznie pojawi się. Jak wskaźnik nad kontekstów metody, zwróć uwagę, czarny trójkąt po prawej stronie. Ponadto kliknięcie tego trójkąt Wyświetla menu skrótów.  
  
     Dla dużych aplikacji, które mają wiele wątków można skoncentrować się na określony podzbiór wątków. **Stosów równoległych** można wyświetlić w oknie stosy wywołań tylko oflagowane wątki. Na pasku narzędzi kliknij **Pokaż tylko oflagowane** przycisk znajdujący się obok pola listy.  
  
     ![Puste okno stosów równoległych i etykietek narzędzi](../debugger/media/pdb-walkthrough-3a.png "PDB_Walkthrough_3A")  
  
     Następnie w **wątków** oknie wątki flagi pojedynczo, aby zobaczyć, jak ich stosy wywołań są wyświetlane w **stosów równoległych** okna. Aby Oflaguj wątki, należy użyć menu skrótów lub pierwszej komórki wątku. Kliknij przycisk **Pokaż tylko oflagowane** przycisku paska narzędzi ponownie, aby wyświetlić wszystkie wątki.  
  
#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Aby wznowić wykonywanie aż do trzeciego punktu przerwania  
  
1. Aby wznowić wykonywanie do momentu trzeci punkt przerwania zostaje trafiony, na **debugowania** menu, kliknij przycisk **Kontynuuj**.  
  
    Wiele wątków znajdują się w tej samej metody, ale metoda nie jest na początku stos wywołań, metoda pojawia się w różnych polach. S.L, zawiera trzy wątków, która jest wyświetlana w trzy pola to na przykład w bieżącym punkcie przerwania. Kliknij dwukrotnie opcję Brak miejsca  
  
    ![Ścieżki wykonywania w okna stosów równoległych](../debugger/media/pdb-walkthrough-3b.png "PDB_Walkthrough_3B")  
  
    Zauważ, że S.L jest pogrubiony w innych polach, dzięki czemu można zobaczyć, gdzie indziej pojawia się. Jeśli chcesz zobaczyć, który ramek wywołać S.L i który ramek wywołań, kliknij przycisk **Przełącz widok metody** przycisk na pasku narzędzi. Na poniższej ilustracji przedstawiono metodę **stosów równoległych** okna.  
  
    ![Metoda widok okna stosów równoległych](../debugger/media/pdw-walkthrough-4.png "PDW_Walkthrough_4")  
  
    Zwróć uwagę, jak diagramu przestawiać na wybranej metody i umieszczony ją w swoje własne polu w środku widoku. Wywoływane a obiektami wywołującymi są wyświetlane u góry i u dołu. Kliknij przycisk **Przełącz widok metody** przycisk ponownie, aby opuścić ten tryb.  
  
    Menu skrótów **stosów równoległych** okno zawiera również następujące inne elementy.  
  
   - **Wyświetlanie szesnastkowe** Włącza/wyłącza numery w etykietkach narzędzi od wartości dziesiętnej i szesnastkowej.  
  
   - **Informacje o ładowaniu symboli** i **ustawienia symboli** otworzyć okna dialogowe.  
  
   - **Przejdź do kodu źródłowego** i **przejdź do demontażu** nawigowanie w edytorze wybranej metody.  
  
   - **Pokaż kod zewnętrzny** Wyświetla wszystkie ramki, nawet jeśli nie znajdują się w kodzie użytkownika. Wypróbuj ją, aby wyświetlić diagram Rozwiń, aby uwzględnić dodatkowe ramki, (które mogą być nieaktywne, ponieważ nie masz symboli dla nich).  
  
     Jeśli masz dużych diagramów w kroku do następnego punktu przerwania, może być widok, aby automatycznie przewiń do aktywną ramkę stosu bieżącego wątku; oznacza to, że wątek, który najpierw trafiony punkt przerwania. W **stosów równoległych** okna, upewnij się, że **automatycznie przewiń do bieżącej ramki stosu** przycisk na pasku narzędzi znajduje się na.  
  
     ![Autoscrolling okna stosów równoległych](../debugger/media/pdb-walkthrough-4a.png "PDB_Walkthrough_4A")  
  
2. Przed rozpoczęciem pracy w **stosów równoległych** okna, przewijania, aż po lewej stronie i w dół do końca.  
  
#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Aby wznowić wykonywanie aż do czwartej punktu przerwania  
  
1. Aby wznowić wykonywanie do momentu czwarty punkt przerwania zostaje trafiony, na **debugowania** menu, kliknij przycisk **Kontynuuj**.  
  
     Zwróć uwagę jak autoscrolled widoku w miejscu. Przełącz wątki w **wątków** ramki stosu okna lub przełącznika **stos wywołań** okna i zwróć uwagę, jak widok zawsze autoscrolls do poprawnej ramki. Wyłącz **automatycznie przewiń do bieżącej ramki narzędzie** opcji i wyświetlenia różnicy.  
  
     **Ptaka** pomaga również dużych diagramów w **stosów równoległych** okna. Możesz zobaczyć **ptaka** , klikając przycisk między pasków przewijania w prawym dolnym rogu okna, jak pokazano na poniższej ilustracji.  
  
     ![Ptaka&#45;oczu widoku okna stosów równoległych](../debugger/media/pdb-walkthrough-5.png "PDB_Walkthrough_5")  
  
     Można przenieść prostokąt, Przesuń szybko w całym na diagramie.  
  
     Innym sposobem na przenoszenie diagramu w dowolnym kierunku jest do pustego obszaru diagramu, kliknij i przeciągnij go w odpowiednie miejsce.  
  
     Aby powiększyć i diagramu, naciśnij i przytrzymaj klawisz CTRL podczas przenoszenia kółka myszy. Alternatywnie kliknij przycisku Powiększenie na pasku narzędzi, a następnie użyj narzędzie do powiększania.  
  
     ![Element stosów w okna stosów równoległych](../debugger/media/pdb-walkthrough-5a.png "PDB_Walkthrough_5A")  
  
     Stosy można wyświetlić w kierunku do góry na dół zamiast od dołu do góry, klikając **narzędzia** menu, klikając **opcje**, a następnie zaznacz lub wyczyść pole wyboru w obszarze **debugowanie** węzła.  
  
2. Przed kontynuowaniem na **debugowania** menu, kliknij przycisk **Zatrzymaj debugowanie** do realizacji celu.  
  
## <a name="using-the-parallel-tasks-window-and-the-tasks-view-of-the-parallel-stacks-window"></a>Za pomocą okno zadań równoległych i widok zadań z okna stosów równoległych  
 Zalecane jest, wykonaj wcześniejsze procedury, aby kontynuować.  
  
#### <a name="to-restart-the-application-until-the-first-breakpoint-is-hit"></a>Uruchom aplikację do momentu pierwszy punkt przerwania zostaje trafiony  
  
1. Na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie** i poczekaj na pierwszy punkt przerwania, aby zostanie osiągnięty.  
  
2. Na **debugowania** menu wskaż **Windows** a następnie kliknij przycisk **wątków**. Zadokuj **wątków** okna w dolnej części programu Visual Studio.  
  
3. Na **debugowania** menu wskaż **Windows** i kliknij przycisk **stos wywołań**. Zadokuj **stos wywołań** okna u dołu Visual Studio.  
  
4. Kliknij dwukrotnie wątek na **wątków** okna sprawia, że bieżący. Wątki bieżącego mają żółtą strzałką. Inne okna są aktualizowane, po zmianie bieżącego wątku. Następnie zostanie omówiony zadania.  
  
5. Na **debugowania** menu wskaż **Windows** a następnie kliknij przycisk **zadań równoległych**. Poniższa ilustracja przedstawia **zadań równoległych** okna.  
  
     ![Cztery uruchomione zadania okno zadań równoległych](../debugger/media/pdw-walkthrough-6.png "PDW_Walkthrough_6")  
  
     Dla każdego uruchomionego zadania można odczytać Identyfikatora, który jest zwracany przez właściwość o tej samej nazwie, identyfikator i nazwę wątku, który działa, jego lokalizacji (przesuwania wskaźnika w obrębie tego wyświetla etykietkę narzędzia, która ma całego stosu). Ponadto w obszarze **zadań** kolumny, możesz zobaczyć metodę, która została przekazana do zadania — innymi słowy, punkt początkowy.  
  
     Można sortować dowolnej kolumny. Zwróć uwagę, symbol sortowania, który wskazuje sortowanie kolumn i kierunek. Można również zmienić kolejność kolumn, przeciągając je w lewo lub w prawo.  
  
     Żółta strzałka wskazuje bieżącego zadania. Zadania można przełączać, klikając dwukrotnie zadania lub za pomocą menu skrótów. Po przełączeniu się z zadaniami, podstawowy wątek staje się bieżącym i inne okna są aktualizowane.  
  
     Ręcznie przełączyć się z jednego zadania do innego, żółta strzałka przesuwa się, ale biały strzałek nadal zawiera zadania, który spowodował debuger przerywa.  
  
#### <a name="to-resume-execution-until-the-second-breakpoint"></a>Aby wznowić wykonywanie aż do drugiego punktu przerwania  
  
1. Aby wznowić wykonywanie do momentu drugi punkt przerwania zostaje trafiony, na **debugowania** menu, kliknij przycisk **Kontynuuj**.  
  
     Wcześniej **stan** kolumny wykazało, że wszystkie zadania jako uruchomiona, ale teraz dwa zadania oczekują. Zadania mogą zostać zablokowane w wielu różnych powodów. W **stan** kolumny, umieść kursor nad zadaniem oczekiwania, aby dowiedzieć się, dlaczego jest on zablokowany. Na przykład na poniższej ilustracji, zadanie 3 oczekuje na zadanie 4.  
  
     ![Dwa zadania oczekiwania w okno zadań równoległych](../debugger/media/pdb-walkthrough-7.png "PDB_Walkthrough_7")  
  
     Zadanie 4, z kolei czeka na monitorze własnością wątku przydzielony do zadania 2.  
  
     ![Oczekiwanie na zadanie i etykietek narzędzi w oknie zadania](../debugger/media/pdb-walkthrough-7a.png "PDB_Walkthrough_7A")  
  
     Zadania mogą oznaczać, klikając flagę w pierwszej kolumnie **zadań równoległych** okna.  
  
     Flagowanie można użyć do śledzenia zadań między różne punkty przerwania w tej samej sesji debugowania lub aby filtrować zadania, którego stosy wywołań są wyświetlane w **stosów równoległych** okna.  
  
     Kiedy użyć **stosów równoległych** okna wcześniej, wyświetlać wątki aplikacji. Widok **stosów równoległych** ponownie okno, ale tym razem wyświetlania zadań aplikacji. To zrobić, wybierając **zadania** w polu w lewym górnym rogu. Na poniższej ilustracji przedstawiono zadania.  
  
     ![Widok okna stosów równoległych wątków](../debugger/media/pdb-walkthrough-8.png "PDB_Walkthrough_8")  
  
     Wątki, które nie są obecnie wykonuje zadania nie są wyświetlane w widoku zadań **stosów równoległych** okna. Ponadto dla wątków, które są wykonywane zadania, niektóre ramek stosu, które nie mają znaczenia dla zadania są filtrowane z górnej i dolnej części stosu.  
  
     Widok **zadań równoległych** ponownie okno. Kliknij prawym przyciskiem myszy nagłówek dowolnej kolumny, aby wyświetlić menu skrótów dla kolumny.  
  
     ![Menu Widok skrótów na liście okno zadań równoległych](../debugger/media/pdb-walkthrough-8a.png "PDB_Walkthrough_8A")  
  
     Aby dodać lub usunąć kolumny, można użyć menu skrótów. Na przykład nie jest zaznaczone kolumny domeny aplikacji; w związku z tym nie jest wyświetlany na liście. Kliknij przycisk **nadrzędnego**. **Nadrzędnego** kolumna jest wyświetlana bez wartości dla każdej z czterech zadania.  
  
#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Aby wznowić wykonywanie aż do trzeciego punktu przerwania  
  
1. Aby wznowić wykonywanie do momentu trzeci punkt przerwania zostaje trafiony, na **debugowania** menu, kliknij przycisk **Kontynuuj**.  
  
     Nowe zadanie zadanie 5, jest teraz uruchomiona i obecnie oczekuje zadanie 4. Możesz zobaczyć, dlaczego, ustawiając kursor nad zadanie oczekujące w **stan** okna. W **nadrzędnego** kolumn należy zauważyć, że zadanie 4 jest elementem nadrzędnym zadanie 5.  
  
     Aby lepiej wizualizować relacji nadrzędny podrzędny, kliknij prawym przyciskiem myszy **nadrzędnego** nagłówek kolumny, a następnie kliknij przycisk **widok podrzędny nadrzędnego**. Powinny być widoczne na poniższej ilustracji.  
  
     ![Nadrzędny&#45;widok podrzędny w okno zadań równoległych](../debugger/media/pdb-walkthrough-9.png "PDB_Walkthrough_9")  
  
     Zauważ, że zadanie 4 i 5 zadań są uruchomione na tym samym wątku. Te informacje nie są wyświetlane w **wątków** okno; oglądanie, w tym miejscu jest kolejną korzyścią wynikającą z **zadań równoległych** okna. Aby to sprawdzić, Wyświetl **stosów równoległych** okna. Upewnij się, że **zadania**. Znajdź zadania 4 i 5, klikając je dwukrotnie **zadań równoległych** okna. Powoduje to niebieskie podświetlenie **stosów równoległych** okna jest aktualizowana. Możesz również znaleźć zadania 4 i 5, skanując etykietki narzędzi na **stosów równoległych** okna.  
  
     ![Widok okna stosów równoległych zadań](../debugger/media/pdb-walkthrough-9a.png "PDB_Walkthrough_9A")  
  
     W **stosów równoległych** , kliknij prawym przyciskiem myszy S.P, a następnie kliknij przycisk **przejdź do wątku**. Okno przełącza do widoku wątków i odpowiednie ramki znajduje się w widoku. Zarówno do zadań są widoczne na tym samym wątku.  
  
     ![Wyróżnione wątku w widoku wątków](../debugger/media/pdb-walkthrough-9b.png "PDB_Walkthrough_9B")  
  
     Jest to kolejna korzyść związana z widoku zadania na **stosów równoległych** okna, w porównaniu do **wątków** okna.  
  
#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Aby wznowić wykonywanie aż do czwartej punktu przerwania  
  
1. Aby wznowić wykonywanie do momentu trzeci punkt przerwania zostaje trafiony, na **debugowania** menu, kliknij przycisk **Kontynuuj**. Kliknij przycisk **identyfikator** nagłówek kolumny, aby posortować według identyfikatora. Powinny być widoczne na poniższej ilustracji.  
  
     ![Cztery zadania stanów w okna stosów równoległych](../debugger/media/pdb-walkthrough-10.png "PDB_Walkthrough_10")  
  
     Ponieważ zadanie 5 zostało ukończone, jest już wyświetlany. Jeśli to nie przypadek na komputerze i zakleszczenia nie jest wyświetlany, krok jeden raz, naciskając klawisz F11.  
  
     Zadanie 3 zadanie 4 teraz oczekują od siebie i są zakleszczenie. Dostępne są także 5 nowych zadań, które są elementami podrzędnymi zadanie 2, a teraz są planowane. Zaplanowane zadania są zadania, które zostały rozpoczęte w kodzie, ale nie zostały jeszcze uruchomione. W związku z tym ich **lokalizacji** i **wątek przypisania** kolumny są puste.  
  
     Widok **stosów równoległych** ponownie okno. Nagłówek każde pole ma etykietkę narzędzia, która zawiera nazwy i identyfikatory wątku. Przełącz do widoku zadania na **stosów równoległych** okna. Umieść kursor nad nagłówek, aby wyświetlić identyfikator zadania oraz nazwę i stan zadania, jak pokazano na poniższej ilustracji.  
  
     ![Nagłówek tooltip okna stosów równoległych](../debugger/media/pdb-walkthrough-11.png "PDB_Walkthrough_11")  
  
     Zadania można grupować według kolumny. W **zadań równoległych** okna, kliknij prawym przyciskiem myszy **stan** nagłówek kolumny, a następnie kliknij przycisk **grupa statusem**. Poniższa ilustracja przedstawia **zadań równoległych** okna pogrupowane według stanu.  
  
     ![Grupowania zadań w okno zadań równoległych](../debugger/media/pdb-walkthrough-12.png "PDB_Walkthrough_12")  
  
     Można także grupować według innych kolumn. Przez grupowanie zadania można skoncentrować się na podzbiór zadań. Każda grupa zwijany ma liczbę elementów, które są zgrupowane. Można również szybko oznaczyć wszystkie elementy w grupie, klikając **flagi** przycisk po prawej stronie **Zwiń** przycisku.  
  
     ![Pogrupowane stosów w okna stosów równoległych](../debugger/media/pdb-walkthrough-12a.png "PDB_Walkthrough_12A")  
  
     Ostatnie funkcji **zadań równoległych** okno do sprawdzenia jest menu skrótów, która jest wyświetlana po kliknięciu prawym przyciskiem myszy zadanie.  
  
     ![Menu skrótów okna zadań równoległych](../debugger/media/pdb-walkthrough-12b.png "PDB_Walkthrough_12B")  
  
     Menu skrótów zostaną wyświetlone różne polecenia, w zależności od stanu zadania. Polecenia mogą obejmować **kopiowania**, **Zaznacz wszystko**, **wyświetlanie szesnastkowe**, **Przełącz do zadania**, **Blokuj przypisany Wątek**, **Zablokuj wszystkie wątki oprócz tego**, i **Odblokuj przypisany wątek**, i **flagi**.  
  
     Można zamrozić wątku podstawowym zadania lub zadania, lub można zablokować wszystkich wątków, z wyjątkiem przypisane. Zablokowanego wątku jest reprezentowana w **zadań równoległych** okna, ponieważ znajduje się w **wątków** okna przez niebieski *wstrzymać* ikony.  
  
## <a name="summary"></a>Podsumowanie  
 W tym instruktażu zademonstrowano **zadań równoległych** i **stosów równoległych** debugera systemu windows. Użyj tych okien na rzeczywistych projektach, korzystających z kodu wielowątkowego. Można sprawdzić równoległego kodu napisanego w języku C++, C# lub Visual Basic.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji wielowątkowych](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)   
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)   
 [Programowanie równoległe](https://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)   
 [Współbieżność środowiska wykonawczego](https://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)   
 [Korzystanie z okna stosów równoległych](../debugger/using-the-parallel-stacks-window.md)   
 [Korzystanie z okna zadań](../debugger/using-the-tasks-window.md)
