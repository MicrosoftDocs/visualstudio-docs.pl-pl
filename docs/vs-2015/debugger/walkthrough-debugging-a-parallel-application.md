---
title: 'Przewodnik: debugowanie aplikacji równoległej | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65705279"
---
# <a name="walkthrough-debugging-a-parallel-application"></a>Wskazówki: debugowanie aplikacji równoległych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu pokazano, jak używać równoległych **zadań** i **równoległych stosów** systemu Windows do debugowania aplikacji równoległej. Te okna pomagają zrozumieć i zweryfikować zachowanie środowiska uruchomieniowego kodu, który używa [biblioteki zadań równoległych (TPL)](https://msdn.microsoft.com/library/b8f99f43-9104-45fd-9bff-385a20488a23) lub [środowisko uruchomieniowe współbieżności](https://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c). Ten Instruktaż zawiera przykładowy kod, który ma wbudowane punkty przerwania. Po przerwie w kodzie przewodnik pokazuje, jak używać **zadań równoległych** i **stosów równoległych** , aby je przeanalizować.  
  
 W tym instruktażu przedstawiono następujące zadania:  
  
- Jak wyświetlić stosy wywołań wszystkich wątków w jednym widoku.  
  
- Jak wyświetlić listę `System.Threading.Tasks.Task` wystąpień utworzonych w aplikacji.  
  
- Jak wyświetlić stosy wywołań rzeczywistych zadań zamiast wątków.  
  
- Jak nawigować do kodu z okien **zadań równoległych** i **stosów równoległych** .  
  
- Jak rozwiąże się system Windows z skalowaniem poprzez grupowanie, powiększanie i inne powiązane funkcje.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym instruktażu przyjęto założenie, że **tylko mój kod** jest włączona. W menu **Narzędzia** kliknij pozycję **Opcje**, rozwiń węzeł **debugowanie** , wybierz pozycję **ogólne**, a następnie wybierz pozycję **Włącz tylko mój kod (tylko zarządzane)**. Jeśli ta funkcja nie zostanie ustawiona, można nadal korzystać z tego instruktażu, ale wyniki mogą się różnić od ilustracji.  
  
## <a name="c-sample"></a>Przykład w języku C#  
 W przypadku korzystania z przykładu w języku C# w tym instruktażu założono również, że kod zewnętrzny jest ukryty. Aby sprawdzić, czy jest wyświetlany kod zewnętrzny, kliknij prawym przyciskiem myszy **nazwę** nagłówka tabeli okna **stosu wywołań** , a następnie zaznacz lub wyczyść pole **Pokaż kod zewnętrzny**. Jeśli ta funkcja nie zostanie ustawiona, można nadal korzystać z tego instruktażu, ale wyniki mogą się różnić od ilustracji.  
  
## <a name="c-sample"></a>Przykład C++  
 Jeśli używasz przykładu C++, możesz zignorować odwołania do kodu zewnętrznego w tym temacie. Kod zewnętrzny ma zastosowanie tylko do przykładu w języku C#.  
  
## <a name="illustrations"></a>Ilustracje  
 Ilustracje w tym temacie zostały zarejestrowane na komputerze z czterema procesorami, na których jest uruchomiony przykładowy język C#. Mimo że można użyć innych konfiguracji do wykonania tego instruktażu, ilustracje mogą się różnić od tego, co jest wyświetlane na komputerze.  
  
## <a name="creating-the-sample-project"></a>Tworzenie przykładowego projektu  
 Przykładowy kod w tym instruktażu dotyczy aplikacji, która nic nie robi. Celem jest zrozumienie, jak używać okien narzędzi do debugowania aplikacji równoległej.  
  
#### <a name="to-create-the-sample-project"></a>Aby utworzyć przykładowy projekt  
  
1. W programie Visual Studio w menu **plik** wskaż polecenie **Nowy** , a następnie kliknij pozycję **projekt**.  
  
2. W okienku **zainstalowane szablony** wybierz pozycję Visual C#, Visual Basic lub Visual C++. W przypadku języków zarządzanych upewnij się, że [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] jest wyświetlana w polu Struktura.  
  
3. Wybierz pozycję **Aplikacja konsolowa** , a następnie kliknij przycisk **OK**. Pozostanie w konfiguracji debugowania, co jest ustawieniem domyślnym.  
  
4. Otwórz plik CPP, cs lub VB w projekcie. Usuń jego zawartość, aby utworzyć pusty plik kodu.  
  
5. Wklej następujący kod w wybranym języku do pustego pliku kodu.  
  
   [!code-cpp[Debugger#1](../snippets/cpp/VS_Snippets_Misc/debugger/cpp/beta2_native.cpp#1)]
   [!code-csharp[Debugger#1](../snippets/csharp/VS_Snippets_Misc/debugger/cs/s.cs#1)]
   [!code-vb[Debugger#1](../snippets/visualbasic/VS_Snippets_Misc/debugger/vb/module1.vb#1)]  
  
6. W menu **File** kliknij pozycję **Save All**.  
  
7. W menu **kompilacja** kliknij polecenie **Kompiluj ponownie rozwiązanie**.  
  
    Należy zauważyć, że istnieją cztery wywołania programu `Debugger.Break` ( `DebugBreak` w próbce C++), dlatego nie trzeba wstawiać punktów przerwania; po prostu uruchomienie aplikacji spowoduje jej przerwanie w debugerze do czterech razy.  
  
## <a name="using-the-parallel-stacks-window-threads-view"></a>Korzystanie z okna stosów równoległych: Widok wątków  
 W menu **Debugowanie** kliknij polecenie **Rozpocznij debugowanie**. Poczekaj, aż pierwszy punkt przerwania zostanie osiągnięty.  
  
#### <a name="to-view-the-call-stack-of-a-single-thread"></a>Aby wyświetlić stos wywołań pojedynczego wątku  
  
1. W menu **debugowanie** wskaż polecenie **Windows** , a następnie kliknij pozycję **wątki**. Zadokuj okno **wątków** w dolnej części programu Visual Studio.  
  
2. W menu **debugowanie** wskaż polecenie **Windows** , a następnie kliknij pozycję **stos wywołań**. Zadokuj okno **stosu wywołań** w dolnej części programu Visual Studio.  
  
3. Kliknij dwukrotnie wątek w oknie **wątki** , aby go zmienić. Bieżące wątki mają żółtą strzałkę. Po zmianie bieżącego wątku jego stos wywołań jest wyświetlany w oknie **stosu wywołań** .  
  
#### <a name="to-examine-the-parallel-stacks-window"></a>Aby przejrzeć Okno stosów równoległych  
  
1. W menu **debugowanie** wskaż polecenie **Windows** , a następnie kliknij pozycję **stosy równoległe**. Upewnij się, że w polu w lewym górnym rogu zaznaczone są **wątki** .  
  
     Korzystając z okna **stosów równoległych** , można wyświetlać wiele stosów wywołań jednocześnie w jednym widoku. Na poniższej ilustracji przedstawiono okno **stosów równoległych** nad oknem **stosu wywołań** .  
  
     ![Widok wątków w oknie stosów równoległych](../debugger/media/pdb-walkthrough-1.png "PDB_Walkthrough_1")  
  
     Stos wywołań głównego wątku pojawia się w jednym polu, a stosy wywołań dla pozostałych czterech wątków są pogrupowane w innym polu. Cztery wątki są pogrupowane ze względu na to, że ich ramki stosu korzystają z tych samych kontekstów metody; oznacza to, że znajdują się w tych samych metodach: `A` , `B` i `C` . Aby wyświetlić identyfikatory wątku i nazwy wątków, które współużytkują to samo pole, umieść kursor na nagłówku (**4 wątki**). Bieżący wątek jest wyświetlany pogrubioną czcionką, jak pokazano na poniższej ilustracji.  
  
     ![Etykietka narzędzia pokazująca identyfikatory i nazwy wątków](../debugger/media/pdb-walkthrough-1a.png "PDB_Walkthrough_1A")  
  
     Żółta strzałka wskazuje aktywną ramkę stosu bieżącego wątku. Aby uzyskać więcej informacji, umieść kursor nad nim  
  
     ![Etykietka narzędzia w aktywnej ramce stosu](../debugger/media/pdb-walkthrough-1b.png "PDB_Walkthrough_1B")  
  
     Można ustawić, ile szczegółów ma być pokazywanych dla ramek stosu (**nazw modułów**, **typów parametrów**, **nazw parametrów**, **wartości parametrów**, **numerów wierszy** i **przesunięć bajtów**), klikając prawym przyciskiem myszy w oknie **stos wywołań** .  
  
     Niebieskie podświetlenie wokół pola wskazuje, że bieżący wątek jest częścią tego pola. Bieżący wątek jest również wskazywany przez pogrubioną ramkę stosu w etykietce narzędzia. W przypadku dwukrotnego kliknięcia wątku głównego w oknie wątki można obserwować, że niebieskie podświetlenie w oknie **stosów równoległych** jest odpowiednio przenoszone.  
  
     ![Podświetlony główny wątek w oknie stosów równoległych](../debugger/media/pdb-walkthrough-1c.png "PDB_Walkthrough_1C")  
  
#### <a name="to-resume-execution-until-the-second-breakpoint"></a>Aby wznowić wykonywanie do drugiego punktu przerwania  
  
1. Aby wznowić wykonywanie do momentu, gdy drugi punkt przerwania zostanie osiągnięty, w menu **debugowanie** kliknij przycisk **Kontynuuj**. Na poniższej ilustracji przedstawiono drzewo wątków w drugim punkcie przerwania.  
  
     ![Okno stosów równoległych pokazujące wiele gałęzi](../debugger/media/pdb-walkthrough-2.png "PDB_Walkthrough_2")  
  
     W pierwszym punkcie przerwania cztery wątki wszystkie poszło z metody S. A do S. B do S. C. Te informacje są nadal widoczne w oknie **stosów równoległych** , ale cztery wątki mają dalsze postępy. Jeden z nich nadal należy do S. D, a następnie S.E. Kolejna kontynuacja do S. F, S. G i S.H. Dwie pozostałe pozostały do S. i S. J, a z jednego z nich przeprowadziły do S. K i inne inne niż zewnętrzne kod zewnętrzny.  
  
     Możesz umieścić kursor na nagłówku pola, na przykład **1 wątek** lub **2 wątki**, aby wyświetlić identyfikatory wątków wątków. Możesz umieścić kursor nad ramkami stosu, aby wyświetlić identyfikatory wątków i inne szczegóły ramki. Niebieskie podświetlenie wskazuje bieżący wątek, a żółta strzałka wskazuje aktywną ramkę stosu bieżącego wątku.  
  
     Ikona "tkaniny-threads" (nakładające się niebieskie i czerwone linie waved) wskazuje aktywne ramki stosu nieaktualnych wątków. W oknie **stos wywołań** kliknij dwukrotnie przycisk S, aby przełączyć ramki. Okno **stosów równoległych** wskazuje bieżącą ramkę stosu bieżącego wątku przy użyciu zielonej ikony strzałki zakrzywionej.  
  
     W oknie **wątki** Przełącz się między wątkami i sprawdź, czy widok w oknie **stosów równoległych** został zaktualizowany.  
  
     Możesz przełączyć się do innego wątku lub do innej ramki innego wątku, używając menu skrótów w oknie **stosów równoległych** . Na przykład kliknij prawym przyciskiem myszy pozycję S. J, wskaż polecenie **Przełącz na ramkę**, a następnie kliknij polecenie.  
  
     ![Równoległe stosy ścieżek wykonywania](../debugger/media/pdb-walkthrough-2b.png "PDB_Walkthrough_2B")  
  
     Kliknij prawym przyciskiem myszy pozycję S. C i wskaż polecenie **Przełącz do ramki**. Jedno z poleceń ma znacznik wyboru wskazujący ramkę stosu bieżącego wątku. Możesz przełączać się do tej ramki tego samego wątku (tylko zielona strzałka zostanie przeniesiona) lub przełączyć się do innego wątku (niebieskie podświetlenie zostanie również przeniesione). Na poniższej ilustracji przedstawiono podmenu.  
  
     ![Menu stosów z 2 opcjami w języku C, a J jest bieżąca](../debugger/media/pdb-walkthrough-3.png "PDB_Walkthrough_3")  
  
     Gdy kontekst metody jest skojarzony tylko z jedną ramką stosu, w nagłówku pola jest wyświetlany **1 wątek** i można przełączyć się do niego, klikając dwukrotnie. Po dwukrotnym kliknięciu kontekstu metody, z którym jest skojarzona więcej niż 1 ramka, menu zostanie automatycznie wyskakujące. Po umieszczeniu wskaźnika myszy nad kontekstami metody Zwróć uwagę na czarny trójkąt po prawej stronie. Kliknięcie tego trójkąta powoduje również wyświetlenie menu skrótów.  
  
     W przypadku dużych aplikacji z wieloma wątkami warto skupić się na tylko podzbiorze wątków. Okno **stosów równoległych** może wyświetlać stosy wywołań tylko dla wątków oflagowanych. Na pasku narzędzi kliknij przycisk **Pokaż tylko Oflagowane** obok pola listy.  
  
     ![Puste okno i etykietka narzędzia stosów równoległych](../debugger/media/pdb-walkthrough-3a.png "PDB_Walkthrough_3A")  
  
     Następnie w oknie **wątki** Oflaguj wątki jeden według jednego, aby zobaczyć, w jaki sposób stosy wywołań pojawiają się w oknie **stosów równoległych** . Aby oflagować wątki, użyj menu skrótów lub pierwszej komórki wątku. Kliknij ponownie przycisk **Pokaż tylko Oflagowane** paski narzędzi, aby wyświetlić wszystkie wątki.  
  
#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Aby wznowić wykonywanie do trzeciego punktu przerwania  
  
1. Aby wznowić wykonywanie do momentu, gdy trzeci punkt przerwania zostanie osiągnięty, w menu **debugowanie** kliknij przycisk **Kontynuuj**.  
  
    Gdy wiele wątków jest w tej samej metodzie, ale metoda nie była na początku stosu wywołań, metoda pojawia się w innych polach. Przykładem w bieżącym punkcie przerwania jest S. L, który ma trzy wątki w nim i pojawia się w trzech polach. Kliknij dwukrotnie pozycję S.L.  
  
    ![Ścieżka wykonywania w oknie stosów równoległych](../debugger/media/pdb-walkthrough-3b.png "PDB_Walkthrough_3B")  
  
    Zwróć uwagę, że element S. L jest pogrubiony w innych dwóch polach, aby zobaczyć, gdzie ma się pojawić. Jeśli chcesz zobaczyć, które ramki są wywoływane do S. L i które ramki wywołuje, kliknij przycisk **Przełącz widok metody** na pasku narzędzi. Na poniższej ilustracji przedstawiono widok metody okna **stosów równoległych** .  
  
    ![Widok metody w oknie stosów równoległych](../debugger/media/pdw-walkthrough-4.png "PDW_Walkthrough_4")  
  
    Zwróć uwagę na to, jak diagram przestawiany na wybraną metodę i umieszczony we własnym polu w środku widoku. Wywoływane i obiekty wywołujące pojawiają się u góry i u dołu. Kliknij ponownie przycisk **Przełącz widok metody** , aby opuścić ten tryb.  
  
    Menu skrótów okna **stosów równoległych** ma również następujące inne elementy.  
  
   - **Wyświetlacz szesnastkowy** przełącza liczby w etykietach narzędzi między dziesiętną i szesnastkową.  
  
   - **Informacje o ładowaniu symboli** i **ustawieniach symboli** otwierają odpowiednie okna dialogowe.  
  
   - **Przejdź do kodu źródłowego** i **Przejdź do obszaru demontażu** Nawiguj w edytorze do wybranej metody.  
  
   - **Pokaż kod zewnętrzny** wyświetla wszystkie ramki nawet wtedy, gdy nie znajdują się one w kodzie użytkownika. Wypróbuj, aby zobaczyć, że diagram rozszerza się, aby uwzględnić dodatkowe ramki (które mogą być wyszarzone, ponieważ nie są dla nich symbole).  
  
     Jeśli masz duże diagramy i przechodząsz do następnego punktu przerwania, możesz chcieć, aby widok był przewijany do aktywnej ramki stosu bieżącego wątku; oznacza to, że wątek, który najpierw trafi punkt przerwania. W oknie **stosów równoległych** upewnij się, że przycisk **Autoprzewijanie do bieżącej ramki stosu** znajduje się na pasku narzędzi.  
  
     ![Automatyczne przewijanie w oknie stosów równoległych](../debugger/media/pdb-walkthrough-4a.png "PDB_Walkthrough_4A")  
  
2. Przed kontynuowaniem w oknie **stosów równoległych** przewiń cały widok w lewo i w dół.  
  
#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Aby wznowić wykonywanie do czwartego punktu przerwania  
  
1. Aby wznowić wykonywanie do momentu, gdy czwarty punkt przerwania zostanie osiągnięty, w menu **debugowanie** kliknij przycisk **Kontynuuj**.  
  
     Zwróć uwagę na to, jak widok jest przewijany na miejsce. Przełącz wątki w oknie **wątki** lub Przełącz ramki stosu w oknie **stos wywołań** i zwróć uwagę na to, jak widok zawsze przewija do właściwej ramki. Wyłącz opcję **Automatyczne przewijanie do bieżącej ramki narzędzia** i Sprawdź różnicę.  
  
     **Widok oka ptaka** pomaga również w przypadku dużych diagramów w oknie **stosów równoległych** . Możesz zobaczyć **Widok oka ptaka** , klikając przycisk między paskami przewijania w prawym dolnym rogu okna, jak pokazano na poniższej ilustracji.  
  
     ![Widok oczami&#45;ptaka w oknie stosów równoległych](../debugger/media/pdb-walkthrough-5.png "PDB_Walkthrough_5")  
  
     Prostokąt można przesunąć, aby szybko poruszać się na diagramie.  
  
     Innym sposobem przenoszenia diagramu w dowolnym kierunku jest kliknięcie pustego obszaru diagramu i przeciągnięcie go w wybranym miejscu.  
  
     Aby powiększyć i pomniejszyć diagram, naciśnij i przytrzymaj klawisz CTRL podczas przesuwania kółka myszy. Alternatywnie kliknij przycisk Powiększenie na pasku narzędzi, a następnie użyj narzędzia Lupka.  
  
     ![Powiększone stosy w oknie stosów równoległych](../debugger/media/pdb-walkthrough-5a.png "PDB_Walkthrough_5A")  
  
     Możesz również wyświetlić stosy w kierunku góry zamiast na dole, klikając menu **Narzędzia** , klikając polecenie **Opcje**, a następnie wybierając lub wyczyścić opcję w obszarze węzła **debugowanie** .  
  
2. Przed kontynuowaniem w menu **debugowanie** kliknij polecenie **Zatrzymaj debugowanie** , aby zakończyć wykonywanie.  
  
## <a name="using-the-parallel-tasks-window-and-the-tasks-view-of-the-parallel-stacks-window"></a>Korzystanie z okna zadania równoległe i widok zadania okna stosów równoległych  
 Zalecamy wykonanie wcześniejszych procedur przed kontynuowaniem.  
  
#### <a name="to-restart-the-application-until-the-first-breakpoint-is-hit"></a>Aby ponownie uruchomić aplikację do momentu, gdy zostanie trafiony pierwszy punkt przerwania  
  
1. W menu **debugowanie** kliknij **Rozpocznij debugowanie** i poczekaj na naciśnięcie pierwszego punktu przerwania.  
  
2. W menu **debugowanie** wskaż polecenie **Windows** , a następnie kliknij pozycję **wątki**. Zadokuj okno **wątków** w dolnej części programu Visual Studio.  
  
3. W menu **debugowanie** wskaż polecenie **Windows** i kliknij pozycję **stos wywołań**. Zadokuj okno **stosu wywołań** w dolnej części programu Visual Studio.  
  
4. Kliknij dwukrotnie wątek w oknie **wątki** , aby go bieżące. Bieżące wątki mają żółtą strzałkę. Po zmianie bieżącego wątku są aktualizowane inne okna. Następnie sprawdzimy zadania.  
  
5. W menu **debugowanie** wskaż polecenie **Windows** , a następnie kliknij pozycję **zadania równoległe**. Na poniższej ilustracji przedstawiono okno **zadań równoległych** .  
  
     ![Cztery uruchomione zadania w oknie zadań równoległych](../debugger/media/pdw-walkthrough-6.png "PDW_Walkthrough_6")  
  
     Dla każdego uruchomionego zadania można odczytać jego identyfikator, który jest zwracany przez tę samą właściwość o nazwie, identyfikator i nazwę wątku, który go uruchamia, jego lokalizację (umieszczenie kursora nad wyświetlaniem etykietki narzędzia, która ma cały stos wywołań). Ponadto w kolumnie **zadanie** można zobaczyć metodę, która została przeniesiona do zadania; Innymi słowy, punkt początkowy.  
  
     Można sortować dowolną kolumnę. Zwróć uwagę na symbol sortowania wskazujący kolumnę i kierunek sortowania. Możesz również zmienić kolejność kolumn, przeciągając je w lewo lub w prawo.  
  
     Żółta strzałka wskazuje bieżące zadanie. Zadania można przełączać przez dwukrotne kliknięcie zadania lub przy użyciu menu skrótów. Po przełączeniu zadań bazowy wątek stał się aktualny, a inne okna zostaną zaktualizowane.  
  
     Po ręcznym przełączeniu się z jednego zadania do drugiego, żółta strzałka jest przenoszona, ale biała strzałka nadal pokazuje zadanie, które spowodowało przerwanie debugera.  
  
#### <a name="to-resume-execution-until-the-second-breakpoint"></a>Aby wznowić wykonywanie do drugiego punktu przerwania  
  
1. Aby wznowić wykonywanie do momentu, gdy drugi punkt przerwania zostanie osiągnięty, w menu **debugowanie** kliknij przycisk **Kontynuuj**.  
  
     Wcześniej w kolumnie **stan** są wyświetlane wszystkie zadania jako uruchomione, ale teraz dwa z nich oczekują. Zadania mogą być blokowane z wielu różnych przyczyn. W kolumnie **stan** Umieść kursor nad zadaniem oczekującym, aby dowiedzieć się, dlaczego jest on zablokowany. Na przykład na poniższej ilustracji zadanie 3 oczekuje na zadanie 4.  
  
     ![Dwa zadania oczekujące w oknie zadań równoległych](../debugger/media/pdb-walkthrough-7.png "PDB_Walkthrough_7")  
  
     Zadanie 4, z kolei czeka na monitor należący do wątku przypisanego do zadania 2.  
  
     ![Oczekujące zadanie i etykietka narzędzia w oknie zadań](../debugger/media/pdb-walkthrough-7a.png "PDB_Walkthrough_7A")  
  
     Można oflagować zadanie, klikając flagę w pierwszej kolumnie okna **zadania równoległe** .  
  
     Można użyć oflagowania do śledzenia zadań między różnymi punktami przerwania w tej samej sesji debugowania lub do filtrowania zadań, których stosy wywołań są wyświetlane w oknie **stosów równoległych** .  
  
     Gdy wcześniej użyto okna **stosów równoległych** , oglądasz wątki aplikacji. Ponownie Wyświetl okno **stosów równoległych** , ale ten czas wyświetli zadania aplikacji. W tym celu wybierz pozycję **zadania** w polu w lewym górnym rogu. Na poniższej ilustracji przedstawiono widok zadania.  
  
     ![Widok wątków w oknie stosów równoległych](../debugger/media/pdb-walkthrough-8.png "PDB_Walkthrough_8")  
  
     Wątki, które nie są aktualnie wykonywane zadania, nie są wyświetlane w widoku zadania okna **stosów równoległych** . Ponadto w przypadku wątków wykonujących zadania niektóre ramki stosu, które nie są istotne dla zadań są filtrowane z góry i u dołu stosu.  
  
     Ponownie Wyświetl okno **zadań równoległych** . Kliknij prawym przyciskiem myszy dowolny nagłówek kolumny, aby wyświetlić menu skrótów dla kolumny.  
  
     ![Menu Widok skrótu w oknie zadania równoległe](../debugger/media/pdb-walkthrough-8a.png "PDB_Walkthrough_8A")  
  
     Aby dodać lub usunąć kolumny, można użyć menu skrótów. Na przykład kolumna AppDomain nie jest zaznaczona; w związku z tym nie jest wyświetlany na liście. Kliknij przycisk **nadrzędne**. Kolumna **nadrzędna** jest wyświetlana bez wartości dla żadnego z czterech zadań.  
  
#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Aby wznowić wykonywanie do trzeciego punktu przerwania  
  
1. Aby wznowić wykonywanie do momentu, gdy trzeci punkt przerwania zostanie osiągnięty, w menu **debugowanie** kliknij przycisk **Kontynuuj**.  
  
     Nowe zadanie, zadanie 5 jest teraz uruchomione, a zadanie 4 oczekuje teraz. Możesz sprawdzić, czy kursor znajduje się nad zadaniem oczekującym w oknie **stanu** . Zwróć uwagę, że zadanie 4 jest elementem nadrzędnym zadania 5 w kolumnie **nadrzędnej** .  
  
     Aby lepiej wizualizować relację nadrzędny-podrzędny, kliknij prawym przyciskiem myszy nagłówek kolumny **nadrzędnej** , a następnie kliknij pozycję **nadrzędny widok podrzędny**. Powinna zostać wyświetlona następująca ilustracja.  
  
     ![Widok nadrzędny&#45;podrzędny w oknie zadań równoległych](../debugger/media/pdb-walkthrough-9.png "PDB_Walkthrough_9")  
  
     Zwróć uwagę, że zadanie 4 i zadanie 5 są uruchomione w tym samym wątku. Te informacje nie są wyświetlane w oknie **wątki** ; wyświetlenie go w tym miejscu jest kolejną zaletą okna **zadań równoległych** . Aby to potwierdzić, Wyświetl okno **stosów równoległych** . Upewnij się, że oglądasz **zadania**. Zlokalizuj zadania 4 i 5, klikając je dwukrotnie w oknie **zadania równoległe** . Gdy to zrobisz, zostanie zaktualizowane niebieskie podświetlenie w oknie **stosów równoległych** . Możesz również zlokalizować zadania 4 i 5, skanując etykietki narzędzi w oknie **stosów równoległych** .  
  
     ![Widok zadań w oknie stosów równoległych](../debugger/media/pdb-walkthrough-9a.png "PDB_Walkthrough_9A")  
  
     W oknie **stosów równoległych** kliknij prawym przyciskiem myszy pozycję S. P, a następnie kliknij polecenie **Przejdź do wątku**. Okno przełączy się do widoku wątków, a odpowiednia ramka jest w widoku. Oba zadania są wyświetlane w tym samym wątku.  
  
     ![Wyróżniony wątek w widoku wątków](../debugger/media/pdb-walkthrough-9b.png "PDB_Walkthrough_9B")  
  
     Jest to kolejna korzyść w widoku zadania w oknie **stosów równoległych** w porównaniu do okna **wątki** .  
  
#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Aby wznowić wykonywanie do czwartego punktu przerwania  
  
1. Aby wznowić wykonywanie do momentu, gdy trzeci punkt przerwania zostanie osiągnięty, w menu **debugowanie** kliknij przycisk **Kontynuuj**. Kliknij nagłówek kolumny **ID** , aby posortować według identyfikatora. Powinna zostać wyświetlona następująca ilustracja.  
  
     ![Cztery Stany zadań w oknie stosów równoległych](../debugger/media/pdb-walkthrough-10.png "PDB_Walkthrough_10")  
  
     Ponieważ zadanie 5 zostało zakończone, nie jest już wyświetlane. Jeśli nie jest to przypadek na komputerze, a zakleszczenie nie jest wyświetlane, krok jeden raz, naciskając klawisz F11.  
  
     Zadanie 3 i zadanie 4 są teraz oczekujące na siebie i są zakleszczony. Dostępne są również 5 nowych zadań, które są elementami podrzędnymi zadania 2 i są teraz planowane. Zaplanowane zadania to zadania, które zostały uruchomione w kodzie, ale nie zostały jeszcze uruchomione. W związku z tym kolumny ich **lokalizacji** i **przypisania wątku** są puste.  
  
     Ponownie Wyświetl okno **stosów równoległych** . Nagłówek każdego pola zawiera etykietkę narzędzia, która zawiera identyfikatory i nazwy wątków. Przejdź do widoku zadania w oknie **stosów równoległych** . Umieść kursor nad nagłówkiem, aby wyświetlić identyfikator i nazwę zadania oraz stan zadania, jak pokazano na poniższej ilustracji.  
  
     ![Etykietka narzędzia nagłówka w oknie stosów równoległych](../debugger/media/pdb-walkthrough-11.png "PDB_Walkthrough_11")  
  
     Można grupować zadania według kolumny. W oknie **zadania równoległe** kliknij prawym przyciskiem myszy nagłówek kolumny **stan** , a następnie kliknij pozycję **Grupuj według stanu**. Na poniższej ilustracji przedstawiono okno **zadań równoległych** pogrupowane według stanu.  
  
     ![Pogrupowane zadania w oknie zadań równoległych](../debugger/media/pdb-walkthrough-12.png "PDB_Walkthrough_12")  
  
     Możesz również grupować według dowolnej innej kolumny. Grupowanie zadań umożliwia skoncentrowanie się na podzbiorze zadań. Każda zwijana Grupa ma liczbę elementów, które są zgrupowane razem. Możesz również szybko oflagować wszystkie elementy w grupie, klikając przycisk **flagi** po prawej stronie przycisku **Zwiń** .  
  
     ![Zgrupowane stosy w oknie stosów równoległych](../debugger/media/pdb-walkthrough-12a.png "PDB_Walkthrough_12A")  
  
     Ostatnia funkcja okna **zadania równoległe** do sprawdzenia jest menu skrótów, które jest wyświetlane po kliknięciu prawym przyciskiem myszy zadania.  
  
     ![Menu skrótów w oknie zadań równoległych](../debugger/media/pdb-walkthrough-12b.png "PDB_Walkthrough_12B")  
  
     Menu skrótów wyświetla różne polecenia, w zależności od stanu zadania. Polecenia mogą zawierać polecenie **Kopiuj**, **Zaznacz wszystko**, **Wyświetlanie w formacie szesnastkowym**, **Przełącz do zadania**, **Zablokuj przypisany wątek**, **Zablokuj wszystkie wątki, ale ten**i odblokowuje **przypisany wątek**oraz **flagę**.  
  
     Można zablokować podstawowy wątek zadania lub zadania lub można zablokować wszystkie wątki z wyjątkiem przypisanych do nich. Wątek zablokowany jest reprezentowany w oknie **zadań równoległych** , jak znajduje się w oknie **wątki** , przez niebieską ikonę *pauzy* .  
  
## <a name="summary"></a>Podsumowanie  
 W tym instruktażu przedstawiono okna debugera **zadań równoległych** i **stosów równoległych** . Użyj tych okien dla rzeczywistych projektów, które używają kodu wielowątkowego. Można przeanalizować kod równoległy pisany w języku C++, C# lub Visual Basic.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji wielowątkowych](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)   
 [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)   
 [Programowanie równoległe](https://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)   
 [środowisko uruchomieniowe współbieżności](https://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)   
 [Korzystanie z okna stosów równoległych](../debugger/using-the-parallel-stacks-window.md)   
 [Korzystanie z okna zadań](../debugger/using-the-tasks-window.md)
