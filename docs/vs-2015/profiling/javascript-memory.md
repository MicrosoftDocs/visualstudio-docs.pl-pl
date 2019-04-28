---
title: Pamięć języka JavaScript | Dokumentacja firmy Microsoft
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
- dominators, memory analyzer (JavaScript)
- memory leaks (JavaScript)
- heap memory, JavaScript
- leaks, memory (JavaScript)
- snapshots, memory analyzer (JavaScript)
- JavaScript Memory Analyzer
- analyzing memory, JavaScript
- memory analyzer, JavaScript
ms.assetid: 78f8532b-7b4e-4b50-b8b7-68ca0926dd4e
caps.latest.revision: 54
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 816db8b2bc5d78541dc089d75ff155b98231ffd5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435652"
---
# <a name="javascript-memory"></a>Pamięć języka JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Analizator pamięci JavaScript jest dostępna w programie Visual Studio ułatwiają zrozumienia użycia pamięci i znaleźć przecieki pamięci w aplikacjach Store stworzona z myślą o Windows przy użyciu języka JavaScript. Obsługiwane aplikacje to aplikacje dla systemu Windows Phone Store i Windows Store.  
  
 Analizator pamięci JavaScript możesz używać tych rzeczy:  
  
- Pomaga szybko znajdować pamięci problemy dotyczące użycia w Twojej aplikacji przez wyróżnianie ważnych danych.  
  
   Otrzymasz te dane w podsumowania migawki, Pokaż różnice między dwiema migawkami, które zawierają linki do bardziej szczegółowych widoków.  
  
- Podaj widoków dominatorów, typy i elementy główne pomóc wyizolować problemy.  
  
- Zmniejsz bez podejmowania informacji w danych sterty JavaScript.  
  
   Obiekty, które nie są tworzone bezpośrednio w kodzie aplikacji automatycznie są odfiltrowywane. Można także filtrować dane według nazwy obiektu.  
  
  Aby uzyskać samouczek, który poprowadzi Cię przez proces identyfikowania przeciek pamięci w działającą aplikację, zobacz [instruktażu: Znajdowanie wycieku pamięci (JavaScript)](../profiling/walkthrough-find-a-memory-leak-javascript.md).  
  
  W tym temacie:  
  
  [Uruchom analizator pamięci JavaScript](#Run)   
  [Sprawdź użycie pamięci](#Check)   
  [Izolowanie przeciek pamięci](#Isolate)   
  [Wyświetl podsumowanie użycia pamięci na żywo](#LiveMemory)   
  [Wyświetlanie podsumowania migawki](#SnapshotSummary)   
  [Wyświetl szczegóły migawki](#SnapshotDetails)   
  [Wyświetlanie różnic migawki](#SnapshotDiff)   
  [Wyświetl obiekty wg dominatora](#FoldObjects)   
  [Filtrowanie danych według identyfikatora](#Filter)   
  [Znajdź obiekt w drzewie obiektów](#ShowInRootsView)   
  [Wyświetl odwołania do udostępnionego obiektu](#References)   
  [Pokaż wbudowanych obiektów](#BuiltInValues)   
  [Zapisz pliki sesji diagnostycznej](#Save)   
  [Skojarz kodu źródłowego z danymi użycia pamięci](#JSConsoleCommands)   
  [Wskazówki dotyczące identyfikowania problemów z pamięcią](#Tips)  
  
## <a name="Run"></a> Uruchom analizator pamięci JavaScript  
 Można użyć analizatora pamięci, gdy masz działającą aplikację Windows Store, Otwórz w programie Visual Studio lub zainstalowany na komputerze, na którym działa [!INCLUDE[win8](../includes/win8-md.md)] lub nowszej.  
  
#### <a name="to-run-the-memory-analyzer"></a>Aby uruchomić analizator pamięci  
  
1. Otwórz program Visual Studio.  
  
2. Po uruchomieniu aplikacji w programie Visual Studio, w **Rozpocznij debugowanie** listy na **standardowa** narzędzi, wybierz cel debugowania dla projektu: albo Emulator Windows Phone lub aplikacji Windows Store **Komputera lokalnego**, **symulator**, lub **maszyny zdalnej**.  
  
     Aby uzyskać więcej informacji o tych opcjach, zobacz [uruchamiać aplikacje w programie Visual Studio](../debugger/run-store-apps-from-visual-studio.md).  
  
3. Na pasku menu wybierz **debugowania**, **Profiler wydajności...** .  
  
     Domyślnie są analizowane bieżący projekt startowy. Jeśli chcesz zmienić cel analizy, wybierz opcję **zmienić docelowy**.  
  
     ![Zmień cel analizy](../profiling/media/js-tools-target.png "JS_Tools_Target")  
  
     Poniższe opcje są dostępne dla obiektu docelowego analizy:  
  
    - **Projekt startowy**. Analizuje bieżący projekt startowy. Jeśli korzystasz z aplikacji na komputerze zdalnym, musisz wybrać tę opcję, co jest ustawieniem domyślnym.  
  
    - **Twoja aplikacja działa**. Umożliwia wybieranie aplikacji Windows Store z listy uruchomionych aplikacji. Nie można użyć tej opcji, po uruchomieniu aplikacji na komputerze zdalnym.  
  
         Ta opcja umożliwia analizowanie użycia pamięci przez aplikacje, które są uruchomione na komputerze, gdy nie masz dostępu do kodu źródłowego.  
  
    - **Zainstalowana aplikacja**. Pozwala wybrać zainstalowaną aplikację Windows Store, które mają być analizowane. Nie można użyć tej opcji, po uruchomieniu aplikacji na komputerze zdalnym.  
  
         Ta opcja umożliwia analizowanie użycia pamięci przez aplikacje, które zainstalowano na tym komputerze, gdy nie masz dostępu do kodu źródłowego. Tę opcję można też przydatne, jeśli chcesz tylko do analizowania użycia pamięci przez dowolną aplikację poza tworzenie aplikacji.  
  
4. Z **dostępnych narzędzi**, wybierz opcję **pamięci JavaScript** pole wyboru, a następnie wybierz **Start**.  
  
5. Po uruchomieniu analizator pamięci, okno Kontrola konta użytkownika może zażądać Twojej zgody, aby uruchomić program Visual Studio ETW Collector.exe. Wybierz **tak**.  
  
     Wchodzić w interakcje z aplikacją, aby przetestować scenariusze użycia pamięci odpowiednie i wyświetlić wykres pamięci, zgodnie z opisem w poniższych sekcjach.  
  
6. Przełącz się do programu Visual Studio, naciskając klawisze Alt + Tab.  
  
7. Aby wyświetlić dane, które zbiera analizator pamięci, wybierz **wykonać migawkę sterty**. Zobacz [wyświetlić podsumowanie migawki](#SnapshotSummary) w dalszej części tego tematu.  
  
## <a name="Check"></a> Sprawdź użycie pamięci  
 Możesz spróbować do identyfikacji przecieków pamięci za pomocą różnych widoków w analizatorze pamięci JavaScript. Jeśli już podejrzewasz, że aplikacja jest przeciek pamięci, zobacz [izolowania przeciek pamięci](#Isolate) sugerowane przepływu pracy.  
  
 Aby ułatwić zidentyfikowanie przecieków pamięci w aplikacji, należy użyć następujące widoki:  
  
- [Wyświetl podsumowanie użycia pamięci na żywo](#LiveMemory). Wykres użycia pamięci można użyć do wyszukiwania nagły wzrost użycia pamięci lub stale zwiększenie użycia pamięci, która wynika z określonej akcji. Widok podsumowania użycia pamięci na żywo umożliwia wykonywanie migawek sterty. Migawki są traktowane jako kolekcję w obszarze wykres użycia pamięci.  
  
    > [!TIP]
    > Gdy korzystasz z migawek, zobaczą wzrost użycia pamięci. Podsumowania migawki na użytek bardziej dokładne wskazanie wzrostu.  
  
- [Wyświetlanie podsumowania migawki](#SnapshotSummary). Możesz wyświetlić informacje podsumowujące dla migawki w trakcie lub po sesji profilowania pamięci. Użyj podsumowania migawki, aby połączyć szczegóły migawki i widokach różnic migawki.  
  
    > [!TIP]
    > Zazwyczaj widokach różnic migawki zapewni najbardziej przydatnych informacji o przecieków pamięci.  
  
- [Wyświetl szczegóły migawki](#SnapshotDetails). Wyświetla szczegółowe dane użycia pamięci dla pojedynczego migawki.  
  
- [Wyświetlanie różnic migawki](#SnapshotDiff). Pokazuje wartości różnicowych między migawkami. Widoki te Pokaż różnice w obiekcie liczby rozmiar i obiektu.  
  
## <a name="Isolate"></a> Izolowanie przeciek pamięci  
 Poniższe kroki zawierają przepływu pracy, które mogą ułatwić bardziej efektywne wykorzystanie analizatora pamięci JavaScript. Te kroki mogą być przydatne, jeśli podejrzewasz, że Twoja aplikacja ma przeciek pamięci. Aby uzyskać samouczek, który poprowadzi Cię przez proces identyfikowania przeciek pamięci w działającą aplikację, zobacz [instruktażu: Znajdowanie wycieku pamięci (JavaScript)](../profiling/walkthrough-find-a-memory-leak-javascript.md).  
  
1. Otwórz aplikację w programie Visual Studio.  
  
2. Uruchom analizator pamięci JavaScript. Aby uzyskać więcej informacji, zobacz [uruchamiania analizatora pamięci JavaScript](#Run).  
  
3. Uruchom aplikację za pomocą tego scenariusza, który ma zostać przetestowana. Na przykład scenariusz może obejmować dużych mutacji modelu DOM, gdy dana strona ładuje lub po uruchomieniu aplikacji.  
  
4. Powtórz scenariusza 1 – 4 dodatkowe razy.  
  
   > [!TIP]
   > Powtarzając scenariusza testu kilka razy, możesz pomóc, upewnij się, czy inicjowanie można filtrować poza wyniki.  
  
5. Przełącz się do programu Visual Studio (naciśnij klawisze Alt + Tab).  
  
6. Utwórz migawkę sterty linii bazowej, wybierając **wykonać migawkę sterty**.  
  
    Na poniższej ilustracji przedstawiono przykład migawką będącą punktem odniesienia.  
  
    ![Migawką będącą punktem odniesienia](../profiling/media/js-mem-leak-workflow-baseline.png "JS_Mem_Leak_Workflow_Baseline")  
  
   > [!TIP]
   > W przypadku bardziej precyzyjną kontrolę nad chronometraż migawki, można użyć [skojarzyć kodu źródłowego z danymi użycia pamięci](#JSConsoleCommands) polecenia w kodzie.  
  
7. Przełącz się do aplikacji i powtórz scenariusz testowania (Powtórz tylko jeden raz).  
  
8. Przełącz się do programu Visual Studio i drugi migawki.  
  
9. Przełącz się do aplikacji i powtórz scenariusz testowania (Powtórz tylko jeden raz).  
  
10. Przełącz się do programu Visual Studio i trzeci migawki.  
  
     Na poniższej ilustracji przedstawiono przykład drugi i trzeci migawki.  
  
     ![Drugi i trzeci migawki](../profiling/media/js-mem-leak-workflow.png "JS_Mem_Leak_Workflow")  
  
     Wykonując linii bazowej, drugi i trzeci migawki w tym przepływie pracy, można odfiltrować zmiany, które nie są skojarzone z przecieki pamięci łatwiejsze. Na przykład może być oczekiwany zmiany, takie jak Aktualizowanie nagłówków i stopek na stronie spowoduje wygenerowanie pewnych zmian użycia pamięci, ale może być powiązana przecieków pamięci.  
  
11. Z trzeciej migawki wybierz łącze do jednego z widoków różnicowe:  
  
    - Rozmiar sterty różnicowe (po lewej stronie link poniżej rozmiar stosu). Tekst linku zawiera różnicę między Rozmiar sterty bieżącej migawki i Rozmiar sterty poprzednią migawkę.  
  
    - Liczba obiektów różnicowa (odpowiednie łącze poniżej liczba obiektów). Tekst linku zawiera dwie wartości (na przykład +1858 /-1765): Pierwsza wartość jest liczbą nowe obiekty dodane od poprzedniej migawki, a druga wartość jest liczba obiektów usuniętych od poprzedniej migawki.  
  
      Te linki otwarcie widoku szczegółów migawka różnicowa typów na stosie, sortowane rozmiaru zachowanego lub liczba obiektów, w zależności od tego, które łącza jest otwarty.  
  
12. Wybierz jedną z następujących **zakres** opcje ułatwiającymi identyfikację problemów użycia pamięci filtru:  
  
    - **Obiekty pozostałe z migawki nr 2**.  
  
    - **Obiekty dodane między migawki nr 2 i #3**  
  
    > [!TIP]
    > Widok filtrowany obiekty pozostałe z poprzednią migawką umożliwia badanie przecieków pamięci. Na przykład, jeśli liczba obiektów różnicowa jest +205 /-195, Widok ten wyświetli 10 obiektów pozostawione przez i są dobrymi kandydatami są przecieki pamięci.  
  
     Na poniższej ilustracji przedstawiono różnicowej obiekty pozostałe z migawki nr 2.  
  
     ![Tworzenie migawki widoku różnic, wyświetlanie typów](../profiling/media/js-mem-snapshot-diff.png "JS_Mem_Snapshot_Diff")  
  
     Na poprzedniej ilustracji zobaczymy, czy dwa obiekty są pozostałością po poprzedniej migawki. Sprawdź, czy jest to oczekiwane zachowanie dla określonej aplikacji. W przeciwnym razie może to wskazywać przeciek pamięci.  
  
13. Aby zobaczyć, gdzie obiekty w widokach różnic są zakorzenione do globalnego obiektu, który uniemożliwia ich zebranych elementów bezużytecznych, otwórz menu skrótów dla obiektu, a następnie wybierz **Pokaż w widoku elementów głównych**. Dużą liczbę obiektów może zostać zachowana w pamięci, ponieważ występuje do nich za pomocą pojedynczego obiektu (lub kilku obiektów), są umieszczone na obiekt globalny.  
  
14. W przypadku zbyt wiele obiektów w widoku obiekty pozostawione przez, spróbuj dodatkowo wyizolować okres, w której występuje przeciek pamięci, a następnie powtórnych trzech migawki. Aby dodatkowo odizolować przeciek pamięci, należy użyć [skojarzyć kodu źródłowego z danymi użycia pamięci](#JSConsoleCommands), [skojarzyć kodu źródłowego z danymi użycia pamięci](#JSConsoleCommands)oraz inne dane użycia pamięci dostępne w analizatorze pamięci.  
  
## <a name="LiveMemory"></a> Wyświetl podsumowanie użycia pamięci na żywo  
 Widok podsumowania użycia pamięci na żywo zawiera wykres użycia pamięci dla uruchomionej aplikacji i kolekcji wszystkie Kafelki podsumowania migawki. W tym widoku może wykonywać podstawowe zadania, takie jak tworzenie migawek, analizowanie informacji podsumowujących i przechodząc z innymi widokami. Po zatrzymaniu zbierania danych, wykres pamięci znika i zostanie wyświetlony tylko [wyświetlić podsumowanie migawki](#SnapshotSummary) widoku.  
  
 Wykres pamięci przedstawia widok na żywo w pamięci aplikacji procesu, który zawiera Bajty prywatne, natywnej pamięci i sterty JavaScript. Wykres pamięci jest widokiem przewijany pamięci procesu. Poniżej przedstawiono wygląda następująco:  
  
 ![Wykres pamięci analizatora pamięci JavaScript](../profiling/media/js-mem-memory-graph.png "JS_Mem_Memory_Graph")  
  
 Jeśli dodano znaczniki użytkownika do kodu aplikacji (zobacz [skojarzyć kodu źródłowego z danymi użycia pamięci](#JSConsoleCommands)), odwrócony trójkąt pojawia się na wykresie użycia pamięci, aby wskazać, po osiągnięciu tej sekcji kodu.  
  
 Część pamięci, pokazane na grafie pamięci jest przydzielany przez środowisko uruchomieniowe JavaScript. Nie można kontrolować to wykorzystania pamięci w aplikacji. Użycie pamięci, pokazane na grafie zwiększa się po Twojej pierwszej migawki, a następnie zwiększa minimalny zestaw dla każdej dodatkowej migawki.  
  
## <a name="SnapshotSummary"></a> Wyświetlanie podsumowania migawki  
 Aby zrobić migawkę bieżącego stanu użycia pamięci aplikacji, wybierz opcję **wykonać migawkę sterty** z wykresu w pamięci. Kafelek podsumowania migawkę, która jest wyświetlana w obu Podsumowanie użycia pamięci na żywo, (gdy aplikacja jest uruchomiona) i migawki — Podsumowanie (Jeśli aplikacja jest zatrzymana), zawiera informacje na temat sterty JavaScript oraz łącza do bardziej szczegółowych informacji. Robienia migawek co najmniej dwóch, migawka zawiera dodatkowe informacje, porównując jego danych do tego poprzednią migawkę.  
  
> [!NOTE]
> Analizator pamięci JavaScript wymusza wyrzucania elementów bezużytecznych przed każdym migawki. Pomaga to zapewnić bardziej spójne wyniki między przebiegów.  
  
 Oto przykład podsumowania migawki, jeśli przełączysz wiele migawek.  
  
 ![Podsumowanie migawki](../profiling/media/js-mem-snapshot-summary.png "JS_Mem_Snapshot_Summary")  
  
 Zawiera podsumowanie migawki:  
  
- Migawka tytuł i sygnaturę czasową.  
  
- Liczba potencjalnych problemów (oznaczone przez ikonę informacji niebieski). Tę liczbę, jeśli jest obecny, identyfikuje potencjalne problemy z pamięcią, takich jak węzły, które nie są dołączone do modelu DOM. Łącza liczba widok typów migawki, w której jest sortowana według typu problemu, aby wyróżnić potencjalnych problemów. Etykietka narzędzia Pokazuje opis problemu.  
  
- Rozmiar sterty. Liczba ta obejmuje elementów DOM i obiekty, które aparat środowiska wykonawczego języka JavaScript dodaje do sterty JavaScript. Rozmiar sterty łącza do typów widoku migawki.  
  
- Rozmiar sterty różnicową. Ta wartość zawiera różnicę między Rozmiar sterty bieżącej migawki i Rozmiar sterty poprzednią migawkę. Wartość jest następuje czerwona strzałka, jeśli jest zwiększenie pamięci w górę lub zielona strzałka w dół, jeśli występuje spadek pamięci. Rozmiar sterty nie została zmieniona między migawkami, zostanie wyświetlony tekst **bez zmian** zamiast numeru. Dla pierwszego migawki, zostanie wyświetlony tekst **linii bazowej**. Linki Rozmiar sterty różnicowej widok typów porównania migawki.  
  
- Liczba obiektów. Ten licznik pokazuje tylko te obiekty, które utworzonych w swojej aplikacji i odfiltrowuje wbudowanego obiekty utworzone przez środowisko uruchomieniowe JavaScript. Łącza liczba obiektu widok typów szczegóły migawki.  
  
- Liczba obiektów różnicową. To pokazuje dwie wartości: Pierwsza wartość jest liczbą nowe obiekty dodane od poprzedniej migawki; a druga wartość jest liczba obiektów usuniętych od poprzedniej migawki. Na przykład na ilustracji przedstawiono, że obiekty 1,859 zostały dodane i 1,733 obiekty zostały usunięte po utworzeniu migawki nr 1. Te informacje następuje czerwona strzałka w górę, jeżeli liczba całkowita obiektów został zwiększony lub zielona strzałka w dół, jeśli zmniejszyło się. Liczba obiektów nie została zmieniona, zostanie wyświetlony tekst **bez zmian** zamiast numeru. Dla pierwszego migawki, zostanie wyświetlony tekst **linii bazowej**. Łącza liczba różnicowej obiektu widok typów porównania migawki.  
  
- Zrzut ekranu przedstawiający ekran w czasie migawki.  
  
## <a name="SnapshotDetails"></a> Wyświetl szczegóły migawki  
 Możesz wyświetlić szczegółowe informacje na temat użycia pamięci dla każdego migawki w widokach szczegóły migawki.  
  
 Z widoku podsumowania migawki wybierz łącze, aby wyświetlić szczegóły migawki. Na przykład łącze Rozmiar sterty otwiera migawkę, którą szczegóły widok typów domyślnie otwierane przez.  
  
 Ta ilustracja przedstawia widok typów szczegółowo migawki, z danymi użycia pamięci, które są posortowane według rozmiaru zachowanego.  
  
 ![Wyświetlanie potencjalnych problemów z widoku szczegółów migawki](../profiling/media/js-mem-snapshot-details.png "JS_Mem_Snapshot_Details")  
  
 W widoku szczegółów migawki możesz przeglądać dane użycia pamięci przez typ, katalog główny lub dominatora, wybierając opcję z paska narzędzi:  
  
- **Typy**. Wskazuje rozmiar i łączna liczba wystąpień obiektów na stosie, pogrupowane według typu obiektu. Domyślnie te są sortowane według liczby wystąpień.  
  
  > [!TIP]
  > Zazwyczaj widokach różnic typów na stosie obiektu są najbardziej przydatne widoków do identyfikowania przeciek pamięci; udostępniane przez te widoki **zakres** filtr, aby ułatwić identyfikację po lewej stronie za pośrednictwem obiektów.  
  
- **Obiekty główne**. Pokazuje hierarchiczny widok obiektów z obiektów głównych za pomocą odwołania podrzędne. Domyślnie węzły podrzędne są sortowane według rozmiaru zachowanego kolumny, z największych u góry.  
  
- **Dominatorów**. Przedstawia listę obiektów na stosie, który wyłączne odwołują się do innych obiektów. Dominatorów są sortowane według rozmiaru zachowanego.  
  
  > [!TIP]
  > Po usunięciu dominatora z pamięci jest odzyskanie wszystkich pamięci, która zachowuje obiektu. W przypadku kilku aplikacji widoku Dominatorów może pomóc wyjaśnić rozmiarów zachowanych pamięci, ponieważ można zapoznać się z kompletnym obiektem ciąg odwołania.  
  
  Wszystkie trzy widoki Pokaż podobnych typów wartości, w tym:  
  
- **Identyfikatory**. Nazwa, która najlepiej identyfikuje obiekt. Na przykład dla elementów kodu HTML szczegóły migawki Pokaż wartość atrybutu ID, jeśli jest on używany.  
  
- **Typ**. Typ obiektu (na przykład elementu łącza HTML lub div element).  
  
- **Rozmiar**. Rozmiar obiektu, nie wliczając rozmiar wszystkie obiekty.  
  
- **Rozmiaru zachowanego**. Rozmiar obiektu plus rozmiar wszystkich obiektów podrzędnych, które mają bez elementów nadrzędnych. Ze względów praktycznych to ilość pamięci przechowywane przez obiekt, więc w przypadku usunięcia obiektu odzyskać określonej ilości pamięci.  
  
- **Liczba**. Liczba wystąpień obiektu. Ta wartość jest wyświetlana tylko w widoku typów.  
  
## <a name="SnapshotDiff"></a> Wyświetlanie różnic migawki  
 W analizatorze pamięci JavaScript można porównać migawek względem poprzedniej migawki w widokach różnic migawki.  
  
 W widoku podsumowania migawki można wyświetlić szczegóły migawki różnicowe, wybierając rozmiar sterty różnicowej lub łącza liczba różnicowej obiektu po co najmniej dwóch migawek.  
  
 Można wyświetlić różnicowej informacje na temat typów, elementy główne i dominatorów. Diff migawki są udostępniane informacje takie obiekty, które zostały dodane do sterty między dwiema migawkami.  
  
 Ta ilustracja przedstawia widok typów w różnica migawki  
  
 ![Tworzenie migawki widoku różnic, wyświetlanie typów](../profiling/media/js-mem-snapshot-diff.png "JS_Mem_Snapshot_Diff")  
  
 W oknie różnicy migawki widoków Dominatorów, typy i elementy główne są takie same jak w [wyświetlić szczegóły migawki](#SnapshotDetails) okna. Diff migawki pokazuje tych samych informacji jako szczegóły migawki, te wartości dodatkowe:  
  
- **Różnica w rozmiarze**. Różnica między rozmiar obiektu w bieżącej migawce i jej rozmiaru w poprzedniej migawki, nie wliczając rozmiar dowolnego odwołania do obiektów.  
  
- **Różnica w rozmiarze przechowywane**. Różnica między rozmiaru zachowanego obiektu w bieżącą migawką i jej rozmiaru zachowanego w poprzedniej migawce. Rozmiar zachowany obejmuje rozmiar obiektów plus rozmiar wszystkich obiektów podrzędnych, które mają bez elementów nadrzędnych. Ze względów praktycznych rozmiaru zachowanego to ilość pamięci przechowywane przez obiekt, więc w przypadku usunięcia obiektu odzyskać określonej ilości pamięci.  
  
  Aby filtrować informacje różnicowe między migawkami, wybierz jedną z **zakres** filtrów w górnej części różnicowej widoków.  
  
- **Obiekty pozostałe z migawki #\<numer >**. Ten filtr przedstawiono różnice między obiektami dodawane do sterty lub usuwane ze sterty w porównaniu z migawką będącą punktem odniesienia i poprzednią migawkę. Na przykład pokazuje, podsumowania migawki +205 /-195 liczba obiektów, ten filtr opisano dziesięć obiektów, które zostały dodane, ale nie zostaną usunięte.  
  
  > [!TIP]
  > Aby wyświetlić najbardziej przydatnych informacji, w tym filtrze, wykonaj czynności opisane w [izolowania przeciek pamięci](#Isolate).  
  
- **Obiekty dodane między migawka nr\<numer > i #\<numer >**. Filtr ten pokazuje wszystkie obiekty dodane do sterty z poprzednią migawkę.  
  
- **Wszystkie obiekty w migawce #\<numer >**. Ustawienie tego filtru nie odfiltrować wszystkie obiekty na stosie.  
  
  Aby wyświetlić odwołania do obiektów, które nie są zgodne z bieżącą **zakres** filtr, wybierz opcję **Pokaż niezgodne odwołania** na liście ustawień ![listy ustawień&#45;listy w analizatorze pamięci ](../profiling/media/js-mem-settings.png "JS_Mem_Settings") w prawym górnym rogu okienka. Jeśli to ustawienie jest włączone, niezgodne odwołania są wyświetlane z tekstem szary.  
  
> [!TIP]
> Firma Microsoft zaleca, postępuj zgodnie z instrukcjami w [izolowania przeciek pamięci](#Isolate) , a następnie użyj obiekty pozostawione przez **zakres** filtr, aby ułatwić identyfikację obiektów, które są przeciek pamięci.  
  
## <a name="FoldObjects"></a> Wyświetl obiekty wg dominatora  
 Typy i Dominatorów widoków można wybrać, czy chcesz wyświetlić obiekty składany na ich dominatorów (jest to domyślny widok na karcie Dominatory). Po wybraniu tego widoku dominatorów tylko są wyświetlane w widoku najwyższego poziomu obiektów. (Obiekty, które są elementami podrzędnymi obiektów globalnych są ukryte w widoku najwyższego poziomu). W przypadku niektórych aplikacji to wyjaśnić, obiekty, które powodują przeciek pamięci, dzięki zmniejszeniu szumów w danych.  
  
 Aby przełączać widok obiekty wg dominatora, wybierz opcję **składania w obiektach wg dominatora** przycisku. ![Składanie obiektów w ich dominatorów](../profiling/media/js-mem-fold-objects.png "JS_Mem_Fold_Objects")  
  
 Aby uzyskać więcej informacji dotyczących dominatorów, zobacz [wyświetlić szczegóły migawki](#SnapshotDetails).  
  
## <a name="Filter"></a> Filtrowanie danych według identyfikatora  
 W widoku Dominatorów i typy można odfiltrować dane przez wyszukiwanie określonego identyfikatorów. Aby wyszukać identyfikator, po prostu wpisz jej nazwę w **Filtr identyfikatora** pole tekstowe w prawym górnym rogu. Po rozpoczęciu wpisywania, identyfikatory, które nie zawierają wpisane znaki są odfiltrowywane.  
  
 Każdy widok ma swój własny filtr, więc filtru nie są zachowywane po przełączeniu się do innego widoku.  
  
## <a name="ShowInRootsView"></a> Znajdź obiekt w drzewie obiektów  
 W widokach typów i Dominatorów widać relacji określonego obiektu do `Global` obiektu. Obiekty z odblokowanym dostępem do `Global` obiektu nie będzie jesdnostką zbierającą śmieci. Możesz łatwo odnaleźć znany obiekt w widoku elementów głównych, bez przeszukiwania `Global` drzewa obiektów. Aby to zrobić, otwórz menu skrótów dla obiektu w Dominatorów lub typu widoku, a następnie wybierz **Pokaż w widoku elementów głównych**.  
  
## <a name="References"></a> Wyświetl odwołania do udostępnionego obiektu  
 W widokach typów i Dominatorów dolne okienko zawiera listy odwołania do obiektów, która zawiera odwołania do udostępnionych. Po wybraniu obiektu w górnym okienku listy odwołania do obiektów, wyświetla wszystkie obiekty, które wskazują na ten obiekt.  
  
> [!NOTE]
> Odwołania cykliczne są wyświetlane gwiazdką (*) i informacyjny etykietki narzędzia, a nie może zostać rozszerzona. W przeciwnym razie one uniemożliwiłyby z zalet w górę drzewa odwołania i identyfikowania obiektów, które są przez nie obiektami pamięci.  
  
 Jeśli chcesz, aby uzyskać dodatkową pomoc, identyfikowanie obiektów równoważnych, wybierz opcję **Wyświetl identyfikatory obiektów** na liście ustawień ![listy ustawień&#45;listy w analizatorze pamięci](../profiling/media/js-mem-settings.png "JS_Mem_Settings ") w prawym górnym rogu w górnym okienku. Ta opcja Wyświetla identyfikatory obiektów obok nazwy obiektów w **identyfikatory** listy (identyfikatory są wyświetlane we wszystkich widokach, nie tylko na liście odwołania do obiektu). Obiekty, które mają ten sam identyfikator są udostępnione odwołania.  
  
 Poniższej ilustracji przedstawiono listę odwołań do obiektu dla wybranego elementu z identyfikatorami wyświetlane.  
  
 ![Obiekt odwołania z identyfikatorami wyświetlanych](../profiling/media/js-mem-shared-refs.png "JS_Mem_Shared_Refs")  
  
## <a name="BuiltInValues"></a> Pokaż wbudowanych obiektów  
 Domyślnie w widokach Dominatorów i typy wyświetlane są tylko obiekty, które tworzysz w swojej aplikacji. Dzięki temu można odfiltrować zbędne informacje i wyizolować problemy związane z aplikacją. Jednak czasami może być pomocne przy podglądzie wszystkie obiekty, które generuje środowisko uruchomieniowe JavaScript dla aplikacji.  
  
 Aby wyświetlić te obiekty, wybierz **Pokaż elementy wbudowane** na liście ustawień ![listy ustawień&#45;listy w analizatorze pamięci](../profiling/media/js-mem-settings.png "JS_Mem_Settings") w prawym górnym rogu rogu okienka.  
  
## <a name="Save"></a> Zapisz pliki sesji diagnostycznej  
 Diagnostyczne migawkę podsumowania i ich widoków szczegółów skojarzone są zapisywane jako pliki .diagsession. **Eksplorator rozwiązań** Wyświetla poprzednich sesji diagnostyki w folderze Sesje diagnostyki. W **Eksploratora rozwiązań**, można otwierać poprzednich sesjach lub usuń lub zmień nazwy plików.  
  
## <a name="JSConsoleCommands"></a> Skojarz kodu źródłowego z danymi użycia pamięci  
 Aby wyizolować sekcji kodu, który ma problem z pamięci, należy użyć następujących metod:  
  
- Poszukaj nazwy klas i identyfikatory dla elementów DOM w widokach różnicowej i szczegółowe informacje.  
  
- Zwróć uwagę na wartości ciągu w szczegółowe informacje i różnicowe widoków, które mogą być skojarzone z kodem źródłowym.  
  
- Użyj [znaleźć obiekt w drzewie obiektów](#ShowInRootsView) polecenie, aby krokowo drzewa obiektów. Może to pomóc w identyfikacji kodu skojarzone źródło.  
  
- Dodawanie poleceń do analizatora pamięci do kodu źródłowego.  
  
  Skorzystaj z następujących poleceń, w kodzie źródłowym:  
  
- `console.takeHeapSnapshot` tworzy migawkę sterty, która pojawia się w analizatorze pamięci JavaScript. To polecenie jest jednym z [polecenia konsoli JavaScript](../debugger/javascript-console-commands.md).  
  
- `performance.mark` Ustawia znacznik użytkownika (odwrócony trójkąt), który pojawia się na osi czasu wykresu pamięci w widoku podsumowania, gdy aplikacja jest uruchomiona. To polecenie wymaga jednego argumentu ciągu opisujący zdarzenie i jest wyświetlany jako etykietka narzędzia na wykresie pamięci. Ten opis nie może przekraczać 100 znaków.  
  
> [!TIP]
> Użyj `console.takeHeapSnapshot` aby przyspieszyć analizy przypadku powtarzające się scenariusze użycia pamięci.  
  
 Te polecenia zgłosić wyjątek, jeśli je dodać do swojej aplikacji i uruchomienia aplikacji spoza analizatora pamięci JavaScript. Jednakże możesz sprawdzić, czy polecenia istnieje przed ich użyciem. (Polecenia nie istnieć wcześnie w fazie uruchamiania sesji). Aby sprawdzić, czy można bezpiecznie wywołać `takeHeapSnapshot`, należy użyć następującego kodu:  
  
```javascript  
if (console && console.takeHeapSnapshot) {  
    console.takeHeapSnapshot();  
}  
```  
  
 Aby sprawdzić, czy można bezpiecznie wywołać `performance.mark`, należy użyć następującego kodu:  
  
```javascript  
if (performance && performance.mark) {  
    performance.mark("message_string");  
}  
  
```  
  
 Oto wykres pamięci za pomocą kilku znaczniki użytkownika i etykietkę narzędzia dla znacznika aktualnie wybranego użytkownika, dla którego `performance.mark` argument ciągu jest równa "generowane dane":  
  
 ![Przy użyciu znaku profilu](../profiling/media/js-mem-performance-marks.png "JS_Mem_Performance_Marks")  
  
## <a name="Tips"></a> Wskazówki dotyczące identyfikowania problemów z pamięcią  
  
- Postępuj zgodnie z przepływu pracy opisanego w [izolowania przeciek pamięci](#Isolate) i użyj **obiekty pozostałe z migawka nr\<numer >** filtru w widoku różnic, aby zidentyfikować potencjalne prawdopodobnie przecieków pamięci.  
  
- Użyj [znaleźć obiekt w drzewie obiektów](#ShowInRootsView) aby zobaczyć, gdzie odwołań do obiektu w hierarchii pamięci. W widoku elementów głównych pokazuje, jak obiekt jest ścieżką do globalnego obiektu, który może uniemożliwić zebranych elementów bezużytecznych.  
  
- Gdy przyczyną problemu pamięci jest trudne do zidentyfikowania, za pomocą różnych widoków (na przykład Dominatorów i typy) do wyszukania commonalities, zwłaszcza w celu identyfikowania jednego obiektu (lub kilku obiektów), mogą zawierać odwołania do wielu innych obiektów, które pojawiają się na Widok.  
  
- Wyszukaj obiekty, które zostaną zachowane przypadkowo w pamięci w po użytkownik ma przeszedł do nowej strony, która jest typową przyczyną problemów z pamięcią. Na przykład:  
  
    - Niepoprawne użycie [adresu URL. CreateObjectUrl](http://msdn.microsoft.com/library/windows/apps/hh453196.aspx) funkcji może spowodować, że ten problem.  
  
    - Niektóre obiekty mogą dostarczać `dispose` metody i zalecenia dotyczące użycia. Na przykład, należy wywołać `dispose` na [WinJS.Binding.List](http://msdn.microsoft.com/library/windows/apps/Hh700774.aspx) wywołanie listy `createFiltered` metody i następnie opuścić stronę.  
  
    - Może być konieczne usunięcie co najmniej jednego odbiornika zdarzeń. Aby uzyskać więcej informacji, zobacz [odbiorników zdarzeń DOM widoku](../debugger/view-dom-event-listeners.md).  
  
- Obejrzyj w dalszej części [ten film wideo](http://channel9.msdn.com/Events/Build/2013/3-316) z konferencji Build 2013 o analizatora pamięci JavaScript.  
  
- Odczyt [zarządzanie pamięcią w aplikacjach Windows Store](http://msdn.microsoft.com/magazine/jj651575.aspx).  
  
- Rozważ tymczasowe modyfikowanie kodu do izolowania problemów. Na przykład możesz chcieć:  
  
    - Analizator pamięci, należy użyć poleceń `console.takeSnapshot` i `performance.mark`. (Zobacz [skojarzyć kodu źródłowego z danymi użycia pamięci](#JSConsoleCommands).)  
  
         Można użyć tych poleceń, aby wyizolować problemy, które nie izolować, ręcznie wykonując migawkę sterty.  
  
    - Utwórz obiekt testowy i Śledź ją w widokach analizatora pamięci JavaScript, takie jak widok typów. Na przykład można dołączyć bardzo dużego obiektu do innego obiektu, aby zobaczyć, czy konkretny obiekt lub element został zebranych elementów bezużytecznych.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Znajdowanie wycieku pamięci (JavaScript)](../profiling/walkthrough-find-a-memory-leak-javascript.md)
