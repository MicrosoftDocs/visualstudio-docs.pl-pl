---
title: 'Przewodnik: Debugowanie aplikacji wielowątkowych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- multithreaded debugging, walkthrough
- walkthroughs, multithreaded debugging
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5dd742411710698cb2dd626e211cb0e73b8379e
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "51798643"
---
# <a name="walkthrough-debugging-a-multithreaded-application"></a>Przewodnik: Debugowanie aplikacji wielowątkowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] zapewnia ulepszone **wątków** okna i inny użytkownik interfejsu ulepszenia, aby ułatwić debugowanie aplikacji wielowątkowych. W tym przewodniku zajmuje tylko kilka minut, ale jego ukończenia umożliwia zapoznanie się z nowymi funkcjami interfejsu do debugowania aplikacji wielowątkowych.  
  
 Zanim rozpoczniesz ten Instruktaż, musisz projektu aplikacji wielowątkowych. Wykonaj kroki wymienione w tym miejscu do utworzenia tego projektu.  
  
#### <a name="to-create-the-walkthrough-project"></a>Aby utworzyć projekt wskazówki  
  
1.  Na **pliku** menu, wybierz **New** a następnie kliknij przycisk **projektu**.  
  
     **Nowy projekt** pojawi się okno dialogowe.  
  
2.  W **typu projektu**s kliknij wybranego przez siebie języka: **Visual Basic**, **Visual C#** , lub **Visual C++**.  
  
3.  W **szablony** wybierz **aplikację Konsolową** lub **Aplikacja konsoli CLR**.  
  
4.  W **nazwa** wpisz nazwę MyThreadWalkthroughApp.  
  
5.  Kliknij przycisk **OK**.  
  
     Pojawi się nowy projekt konsoli. Po utworzeniu projektu, zostanie wyświetlony plik źródłowy. W zależności od języka wybranego pliku źródłowego może mieć nazwę Module1.vb, Program.cs lub MyThreadWalkthroughApp.cpp  
  
6.  Usuń kod, który pojawia się w pliku źródłowym i zastąp go przykładowy kod, który pojawia się w sekcji "Tworzenie wątek" tego tematu [Tworzenie wątków i przekazywanie danych na czas rozpoczęcia](http://msdn.microsoft.com/library/52b32222-e185-4f42-91a7-eaca65c0ab6d).  
  
7.  Na **pliku** menu, kliknij przycisk **Zapisz wszystko**.  
  
#### <a name="to-begin-the-walkthrough"></a>Aby rozpocząć przewodnik  
  
-   W oknie źródła Wyszukaj następujący kod:  
  
    ```vb  
    Thread.Sleep(3000)   
    Console.WriteLine(  
    ```  
  
```csharp  
Thread.Sleep(3000);  
Console.WriteLine();  
```  
  
```cpp  
Thread::Sleep(3000);  
Console.WriteLine();  
```  
  
#### <a name="to-start-debugging"></a>Aby rozpocząć debugowanie  
  
1.  Kliknij prawym przyciskiem myszy `Console.WriteLine` instrukcji, wskaż **punktu przerwania** a następnie kliknij przycisk **Wstaw punkt przerwania**.  
  
     Na marginesie po lewej stronie okna źródła pojawi się czerwone piłki. Oznacza to, że punkt przerwania są teraz ustawione w tej lokalizacji.  
  
2.  Na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie**.  
  
     Rozpoczyna debugowania, uruchamiania aplikacji konsoli, aby uruchomić i następnie zatrzymuje w punkcie przerwania.  
  
3.  Jeśli okno konsoli w aplikacji ma fokus w tym momencie, kliknij w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okna powrót do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4.  W oknie źródła zlokalizuj wiersz, który zawiera następujący kod:  
  
    ```vb  
    Thread.Sleep(5000)   
    ```  
  
```csharp  
Thread.Sleep(3000);  
```  
  
```cpp  
Thread::Sleep(3000);  
```  
  
1.  
  
#### <a name="to-discover-the-thread-marker"></a>Aby odnaleźć znacznika wątku  
  
1. Kliknij prawym przyciskiem myszy **wątków** okna, następnie kliknij przycisk **Pokaż wątki w źródle**.  
  
2. Spójrz na oprawę w lewej części okna. W tym wierszu będzie widoczna ikona podobny dwoma wątkami ręczników. Jeden wątek ma kolor czerwony, a druga niebieski. Znacznika wątku wskazuje, że wątek został zatrzymany w tej lokalizacji. Ewentualnie wątek został zatrzymany w tej lokalizacji.  
  
3. Umieść wskaźnik myszy nad znacznika wątku. Etykietka danych, który pojawia się. DataTip informuje numer identyfikacyjny nazwy i wątku dla każdego wątku zatrzymania. W tym przypadku istnieje tylko jeden wątek, którego nazwa jest prawdopodobnie `<noname>`.  
  
4. Kliknij prawym przyciskiem myszy znacznika wątku. Należy pamiętać, opcje menu skrótów.  
  
   Ta ikona jest *znacznika wątku*:  
  
   ![Znacznik wątku](../debugger/media/threadmarker.gif "ThreadMarker")  
  
## <a name="flagging-and-unflagging-threads"></a>Flagami i Unflagging wątków  
 W [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)], można Oflaguj wątki, które chcesz poświęcić szczególną uwagę. Flagowanie wątków jest dobrym sposobem na śledzenie ważnych wątków i Ignoruj wątki, które nie są istotne informacje.  
  
#### <a name="to-flag-threads"></a>Do oflagowania wątków  
  
1.  Na **widoku** menu wskaż **pasków narzędzi**.  
  
     Upewnij się, że **Lokalizacja debugowania** pasek narzędzi jest zaznaczony.  
  
2.  Przejdź do **debugowania lokalizacji** paska narzędzi i kliknij przycisk **wątku** listy.  
  
    > [!NOTE]
    >  Możesz rozpoznać tego paska narzędzi przez trzy wyraźną listy: **Proces**, **wątku**, i **ramki stosu**.  
  
3.  Zwróć uwagę, jak wiele wątków, są wyświetlane na liście.  
  
4.  Wróć do okna źródłowego i kliknij prawym przyciskiem myszy **wątku** ponownie znacznika.  
  
5.  W menu skrótów wybierz polecenie **flagi**, a następnie kliknij nazwę wątku i numerem Identyfikacyjnym.  
  
6.  Wróć do **debugowania lokalizacji** paska narzędzi i kliknij przycisk **wątku** ponownie listę.  
  
     Na liście pojawi się teraz tylko wątków oflagowanych. Przycisk flagi, który jest tylko do prawej **wątku** listy. Ikony flagi przycisk został wyszarzony przed. Teraz jest czerwony jasny, stałe.  
  
7.  Umieść wskaźnik myszy na ikonie flagi.  
  
     Pojawi się okno podręczne. Są one informuje, jakie tryb **wątku** listy jest: **Pokaż tylko oflagowane wątki**.  
  
8.  Kliknij przycisk flagi, aby powrócić do **Pokaż wszystkie wątki** trybu.  
  
9. Kliknij przycisk **wątku** ponownie i sprawdź, czy będą teraz widoczne wszystkie wątki ponownie.  
  
10. Kliknij przycisk flagi, aby powrócić do **Pokaż tylko oflagowane wątki**.  
  
11. Na **debugowania** menu wskaż **Windows** a następnie kliknij przycisk **wątków**.  
  
     **Wątków** zostanie wyświetlone okno. Jeden wątek ma ikony flagi wyraźną podłączone do niego.  
  
12. W oknie źródłowym kliknij prawym przyciskiem myszy znacznika wątku ponownie.  
  
     Zwróć uwagę, jakie opcje są teraz dostępne w menu skrótów. Zamiast **flagi**, pojawi się informacja **Unflag**. Nie klikaj **Unflag**.  
  
13. Przejdź do następnej procedury dotyczące usuwanie oflagowania wątków.  
  
#### <a name="to-unflag-threads"></a>Aby usuwanie oflagowania wątków  
  
1.  Na **wątków** okna, kliknij prawym przyciskiem myszy wiersz odpowiadający wątków oflagowanych.  
  
     Zostanie wyświetlone menu skrótów. Ma funkcje umożliwiające **Unflag** i **Usuń flagę ze wszystkich**.  
  
2.  Aby Usuń flagę z wątku, kliknij przycisk **Unflag**.  
  
3.  Kliknij ikonę flagi czerwony.  
  
4.  Przyjrzyj się **debugowania lokalizacji** narzędzi ponownie. Flaga jest wygaszony ponownie. Oflagowanie jest tylko wątków oflagowanych. Ponieważ nie istnieją wątki oflagowane, pasek narzędzi stała się wstecz do **Pokaż wszystkie wątki** trybu. Kliknij przycisk **wątku** listy i sprawdź, czy można wyświetlić wszystkie wątki.  
  
5.  Wróć do **wątków** okna i zbadaj kolumny informacji.  
  
     U góry każdej kolumny większość przycisków mają tytułów, które identyfikują kolumny. Jednak pierwsza kolumna po lewej stronie nie ma tytułu. Zamiast tego zawiera ikonę, która jest zarys flagę. Można zauważyć w tych samych konturu w każdym wierszu listy wątków. Konspekt oznacza, że wątek bez flagi.  
  
6.  Kliknij przycisk opisanych flagi dla dwóch wątków drugie i trzecie w dolnej części listy.  
  
     Ikony flag stają się czerwony, zamiast pustego konturów.  
  
7.  Kliknij przycisk w górnej części kolumny flag.  
  
     Kolejność listy wątków zmieniany, gdy kliknięto przycisk. Lista wątków jest obecnie posortowana w oflagowane wątki na górze.  
  
8.  Ponownie kliknij przycisk w górnej części kolumny flag.  
  
     Jej ponownie zmienić porządek sortowania.  
  
## <a name="more-about-the-threads-window"></a>Więcej informacji na temat okna wątków  
  
#### <a name="to-learn-more-about-the-threads-window"></a>Aby dowiedzieć się więcej na temat okna wątków  
  
1.  W **wątków** oknie Sprawdź trzecia kolumna z lewej strony. Przycisk w górnej części w tej kolumnie jest wyświetlany komunikat **identyfikator**.  
  
2.  Kliknij przycisk **identyfikator**.  
  
     Lista wątków jest teraz posortowane według numer identyfikacyjny wątku.  
  
3.  Kliknij prawym przyciskiem myszy dowolnego wątku, na liście. W menu skrótów kliknij **wyświetlanie szesnastkowe**.  
  
     Format liczb identyfikator wątku jest zmieniany.  
  
4.  Umieść wskaźnik myszy nad żadnym z wątków na liście.  
  
     Po chwili przechwytują pojawia się DataTip. Przedstawia on częściowe stosu dla wątku.  
  
5.  Przyjrzyj się czwartej kolumnie z lewej strony, która jest oznaczona etykietą **kategorii**. Wątki są przydzielane do kategorii.  
  
     Pierwszym wątkiem utworzone w procesie jest nazywana wątku głównego. Znajdź je w listy wątków.  
  
6.  Kliknij prawym przyciskiem myszy w wątku głównym, a następnie kliknij przycisk **Przełącz do wątku**.  
  
     Pojawi się okno dialogowe ostrzeżenia. Informuje, że [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nie może wyświetlić kodu źródłowego dla głównego wątku.  
  
     Kliknij przycisk **OK**.  
  
7.  Przyjrzyj się **stos wywołań** okna i **Lokalizacja debugowania** paska narzędzi.  
  
     Zawartość **stos wywołań** okna uległy zmianie.  
  
## <a name="switching-the-active-thread"></a>Przełączanie aktywnego wątku  
  
#### <a name="to-switch-threads"></a>Aby przełączyć wątków  
  
1.  W **wątków** okna, sprawdź w drugiej kolumnie z lewej strony. Przycisk u góry tej kolumny nie ma tekstu lub ikonę. Ta kolumna znajduje się **aktywnego wątku** kolumny.  
  
2.  Przyjrzyj się **aktywnego wątku** kolumny i zwróć uwagę, że jeden wątek ma żółta strzałka. Jest to *wskaźnik aktywnego wątku*.  
  
3.  Zanotuj numer identyfikacyjny wątku gdzie znajduje się wskaźnik aktywnego wątku. Wskaźnik aktywnego wątku przejdzie do innego wątku, ale konieczne będzie umieszczenie go ponownie, po zakończeniu.  
  
4.  Kliknij prawym przyciskiem myszy innego wątku, a następnie kliknij przycisk **Przełącz do wątku**.  
  
5.  Przyjrzyj się **stos wywołań** okna w oknie źródła. Zmieniono zawartość.  
  
6.  Przyjrzyj się **Lokalizacja debugowania** paska narzędzi. Aktywny wątek został zmieniony, zbyt.  
  
7.  Przejdź do **Lokalizacja debugowania** paska narzędzi. Kliknij przycisk **wątku** polu i wybierz inny wątek z listy rozwijanej.  
  
8.  Przyjrzyj się **wątków** okna. Wskaźnik wątku active została zmieniona.  
  
9. W oknie źródłowym kliknij prawym przyciskiem myszy znacznika wątku. W menu skrótów wybierz polecenie **przełączyć się do** i kliknij numer Identyfikatora/nazwy wątku.  
  
     Zauważyliśmy już teraz trzy sposoby zmiany aktywnego wątku: przy użyciu **wątków** oknie **wątku** pole w **Lokalizacja debugowania** narzędzi, a wskaźnik wątku w Okno źródłowe.  
  
     Za pomocą wskaźnik wątku można przełączyć tylko dla wątków, które zostały zatrzymane w tej konkretnej lokalizacji. Za pomocą **wątków** okna i **Lokalizacja debugowania** narzędzi można przełączyć na żadnym z wątków.  
  
## <a name="freezing-and-thawing-thread-execution"></a>Zawiesza się i odblokowania wykonywanie wątków  
  
#### <a name="to-freeze-and-unfreeze-threads"></a>Zablokuj i Odblokuj wątki  
  
1.  W **wątków** okna, kliknij prawym przyciskiem myszy dowolnego wątku, a następnie kliknij przycisk **Freeze**.  
  
2.  Przyjrzyj się kolumna aktywnego wątku. Para pionowych słupków pojawiają się dostępne. Niebieskie paski w tych dwóch wskazują, że wątek jest zablokowane.  
  
3.  Przyjrzyj się **Wstrzymaj** kolumny. Wstrzymania liczenia wątku, jest teraz 1.  
  
4.  Kliknij prawym przyciskiem myszy zablokowanego wątku, a następnie kliknij przycisk **Odblokuj**.  
  
     Kolumna aktywnego wątku i **Wstrzymaj** zmiany kolumny.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Instrukcje: Przełączanie na inny wątek w trakcie debugowania](../debugger/how-to-switch-to-another-thread-while-debugging.md)



