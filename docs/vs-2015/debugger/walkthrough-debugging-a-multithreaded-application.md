---
title: 'Przewodnik: debugowanie aplikacji wielowątkowej | Microsoft Docs'
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
- multithreaded debugging, walkthrough
- walkthroughs, multithreaded debugging
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 33ce391523a256bcb195deccf0c14868b5eae707
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683083"
---
# <a name="walkthrough-debugging-a-multithreaded-application"></a>Wskazówki: Debugowanie aplikacji wielowątkowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] oferuje ulepszone okno **wątków** i inne udoskonalenia interfejsu użytkownika ułatwiające debugowanie aplikacji wielowątkowych. Ten przewodnik zajmuje zaledwie kilka minut, ale jego zakończenie zapoznaje się z nowymi funkcjami interfejsu na potrzeby debugowania aplikacji wielowątkowych.  
  
 Aby rozpocząć ten przewodnik, potrzebny jest projekt aplikacji wielowątkowej. Wykonaj kroki wymienione w tym miejscu, aby utworzyć projekt.  
  
#### <a name="to-create-the-walkthrough-project"></a>Aby utworzyć projekt instruktażu  
  
1. W menu **plik** wybierz polecenie **Nowy** , a następnie kliknij pozycję **projekt**.  
  
     Zostanie wyświetlone okno dialogowe **Nowy projekt**.  
  
2. W polu **Typ projektu**kliknij wybrany język: **Visual Basic**, **Visual C#** lub **Visual C++**.  
  
3. W polu **Szablony** wybierz **Aplikacja konsolowa** lub **Aplikacja konsolowa CLR**.  
  
4. W polu **Nazwa** wpisz nazwę MyThreadWalkthroughApp.  
  
5. Kliknij przycisk **OK**.  
  
     Zostanie wyświetlony nowy projekt konsoli. Po utworzeniu projektu zostanie wyświetlony plik źródłowy. W zależności od wybranego języka plik źródłowy może mieć nazwę Module1. vb, Program.cs lub MyThreadWalkthroughApp. cpp  
  
6. Usuń kod, który pojawia się w pliku źródłowym i zamień go na przykładowy kod, który pojawia się w sekcji "Tworzenie wątku" tematu [Tworzenie wątków i przekazywanie danych w czasie rozpoczęcia](https://msdn.microsoft.com/library/52b32222-e185-4f42-91a7-eaca65c0ab6d).  
  
7. W menu **File** kliknij pozycję **Save All**.  
  
#### <a name="to-begin-the-walkthrough"></a>Aby rozpocząć Przewodnik  
  
- W oknie Źródło znajdź następujący kod:  
  
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
  
1. Kliknij prawym przyciskiem myszy `Console.WriteLine` instrukcję, wskaż punkt **przerwania** , a następnie kliknij polecenie **Wstaw punkt przerwania**.  
  
     Na marginesie po lewej stronie okna źródłowego pojawia się czerwona kulka. Oznacza to, że punkt przerwania jest teraz ustawiany w tej lokalizacji.  
  
2. W menu **Debugowanie** kliknij polecenie **Rozpocznij debugowanie**.  
  
     Rozpoczęcie debugowania spowoduje uruchomienie aplikacji konsolowej, a następnie zatrzymanie w punkcie przerwania.  
  
3. Jeśli okno aplikacji konsoli ma fokus w tym momencie, kliknij w oknie, aby [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] przywrócić fokus [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
4. W oknie Źródło Zlokalizuj wiersz zawierający następujący kod:  
  
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
  
#### <a name="to-discover-the-thread-marker"></a>Aby odnaleźć znacznik wątku  
  
1. Kliknij prawym przyciskiem myszy w oknie **wątki** , a następnie kliknij pozycję **Pokaż wątki w źródle**.  
  
2. Spójrz na odstępy po lewej stronie okna. W tym wierszu zostanie wyświetlona ikona przypominająca dwuczęściowe wątki. Jeden wątek jest czerwony, a drugi jest niebieski. Znacznik wątku wskazuje, że wątek jest zatrzymany w tej lokalizacji. Prawdopodobnie wątek zostanie zatrzymany w tej lokalizacji.  
  
3. Umieść wskaźnik myszy nad znacznikiem wątku. Zostanie wyświetlona etykietki danych. Etykietki danych informuje o nazwie i numerze wątku dla każdego zatrzymanego wątku. W takim przypadku istnieje tylko jeden wątek, którego nazwa jest prawdopodobnie `<noname>` .  
  
4. Kliknij prawym przyciskiem myszy znacznik wątku. Zanotuj opcje dostępne w menu skrótów.  
  
   Ta ikona jest *znacznikiem wątku*:  
  
   ![Znacznik wątku](../debugger/media/threadmarker.gif "ThreadMarker")  
  
## <a name="flagging-and-unflagging-threads"></a>Oflagowanie i nieoflagowanie wątków  
 W programie [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] można oflagować wątki, które mają dawać szczególną uwagę. Oflagowane wątki to dobry sposób na śledzenie ważnych wątków i ignorowanie wątków, które nie są potrzebne.  
  
#### <a name="to-flag-threads"></a>Aby oflagować wątki  
  
1. W menu **Widok** wskaż pozycję **paski narzędzi**.  
  
     Upewnij się, że wybrano pasek narzędzi **Lokalizacja debugowania** .  
  
2. Przejdź do paska narzędzi **Lokalizacja debugowania** i kliknij listę **wątków** .  
  
    > [!NOTE]
    > Można rozpoznać ten pasek narzędzi o trzech widocznych listach: **proces**, **wątek**i **Ramka stosu**.  
  
3. Zauważ, jak wiele wątków pojawia się na liście.  
  
4. Wróć do okna źródłowego i ponownie kliknij prawym przyciskiem myszy znacznik **wątku** .  
  
5. W menu skrótów wskaż polecenie **Flaga**, a następnie kliknij nazwę wątku i numer identyfikacyjny.  
  
6. Wróć do paska narzędzi **Lokalizacja debugowania** i kliknij ponownie listę **wątków** .  
  
     Tylko oflagowany wątek pojawia się na liście teraz. Przycisk flagi, który znajduje się po prawej stronie listy **wątków** . Ikona flagi na przycisku została wyszarzona przed. Teraz jest to pełna, jasna czerwona.  
  
7. Umieść wskaźnik myszy nad ikoną flagi.  
  
     Zostanie wyświetlone okno podręczne. To okno podręczne informuje o tym, w jakim trybie znajduje się lista **wątków** : **Pokaż tylko Oflagowane wątki**.  
  
8. Kliknij przycisk flagi, aby przełączyć z powrotem do trybu **Pokaż wszystkie wątki** .  
  
9. Kliknij ponownie listę **wątków** i sprawdź, czy teraz można ponownie zobaczyć wszystkie wątki.  
  
10. Kliknij przycisk flagi, aby przełączyć z powrotem do **wyświetlania tylko wątków oflagowanych**.  
  
11. W menu **debugowanie** wskaż polecenie **Windows** , a następnie kliknij pozycję **wątki**.  
  
     Zostanie wyświetlone okno **wątki** . Jeden wątek ma dołączoną ikonę flagi z widocznym elementem.  
  
12. W oknie źródło ponownie kliknij prawym przyciskiem myszy znacznik wątku.  
  
     Zauważ, jakie opcje są teraz dostępne w menu skrótów. Zamiast **flagować**zobaczysz opcję Usuń **flagę**. Nie klikaj przycisku Usuń **flagę**.  
  
13. Przejdź do następnej procedury dotyczącej tworzenia flag wątków.  
  
#### <a name="to-unflag-threads"></a>Aby Usuń flagę wątków  
  
1. W oknie **wątki** kliknij prawym przyciskiem myszy wiersz odpowiadający wątkowi oflagowanemu.  
  
     Zostanie wyświetlone menu skrótów. Ma opcje **unflaging** i **Unflag All**.  
  
2. Aby odoflagować wątek, kliknij przycisk Usuń **flagę**.  
  
3. Kliknij ikonę czerwona flaga.  
  
4. Sprawdź ponownie pasek narzędzi **Lokalizacja debugowania** . Przycisk flagi jest wyszarzony ponownie. Użytkownik oznaczył tylko oflagowany wątek. Ponieważ nie ma żadnych oflagowanych wątków, pasek narzędzi powróci do **wyświetlania wszystkich trybów wątków** . Kliknij listę **wątków** i sprawdź, czy można zobaczyć wszystkie wątki.  
  
5. Wróć do okna **wątki** i przejrzyj kolumny informacji.  
  
     W górnej części każdej kolumny większość przycisków ma tytuły, które identyfikują kolumnę. Jednak pierwsza kolumna po lewej stronie nie ma tytułu. Zamiast tego ma ikonę, która jest konturem flagi. Zobaczysz ten sam Konspekt w każdym wierszu listy wątków. Konspekt oznacza, że wątek nie jest oflagowany.  
  
6. Kliknij kontury flagi dla dwóch wątków, drugi i trzeci od dołu listy.  
  
     Ikony flag stają się pełnymi kolorami czerwonymi, a nie z pustymi konturami.  
  
7. Kliknij przycisk w górnej części kolumny flaga.  
  
     Kolejność na liście wątków została zmieniona po kliknięciu przycisku. Lista wątków jest teraz sortowana przy użyciu oflagowanych wątków w górnej części.  
  
8. Ponownie kliknij przycisk w górnej części kolumny flaga.  
  
     Porządek sortowania został zmieniony ponownie.  
  
## <a name="more-about-the-threads-window"></a>Więcej informacji o oknie wątków  
  
#### <a name="to-learn-more-about-the-threads-window"></a>Aby dowiedzieć się więcej o oknie wątków  
  
1. W oknie **wątki** Przeanalizuj trzecią kolumnę z lewej strony. W górnej części tej kolumny znajduje się przycisk **ID**.  
  
2. Kliknij pozycję **Identyfikator**.  
  
     Lista wątków jest teraz posortowana według numeru ID wątku.  
  
3. Kliknij prawym przyciskiem myszy dowolny wątek na liście. W menu skrótów kliknij pozycję **Wyświetlanie w formacie szesnastkowym**.  
  
     Format numerów identyfikatorów wątków jest zmieniany.  
  
4. Umieść wskaźnik myszy nad dowolnym wątkiem na liście.  
  
     Po chwilowo opóźnieniu pojawi się etykietki danych. Pokazuje częściowy stos wywołań wątku.  
  
5. Przyjrzyj się czwartej kolumnie od lewej, która jest oznaczona etykietą **Kategoria**. Wątki są klasyfikowane do kategorii.  
  
     Pierwszy wątek utworzony w procesie jest określany jako wątek główny. Znajdź ją na liście wątków.  
  
6. Kliknij prawym przyciskiem myszy główny wątek, a następnie kliknij polecenie **Przełącz do wątku**.  
  
     Zostanie wyświetlone okno dialogowe ostrzeżenia. Informuje o tym, że [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nie można wyświetlić kodu źródłowego dla głównego wątku.  
  
     Kliknij przycisk **OK**.  
  
7. Sprawdź okno **stosu wywołań** i pasek narzędzi **Lokalizacja debugowania** .  
  
     Zawartość okna **stosu wywołań** została zmieniona.  
  
## <a name="switching-the-active-thread"></a>Przełączanie aktywnego wątku  
  
#### <a name="to-switch-threads"></a>Aby przełączyć wątki  
  
1. W oknie **wątki** Przejrzyj drugą kolumnę po lewej stronie. Przycisk w górnej części tej kolumny nie ma tekstu ani ikony. Ta kolumna jest kolumną **aktywnego wątku** .  
  
2. Spójrz na **aktywną kolumnę wątku** i zwróć uwagę, że jeden wątek ma żółtą strzałkę. Jest to *wskaźnik aktywnego wątku*.  
  
3. Zanotuj numer identyfikatora wątku, w którym znajduje się wskaźnik aktywnego wątku. Wskaźnik aktywnego wątku zostanie przesunięty do innego wątku, ale będzie trzeba go przywrócić po zakończeniu.  
  
4. Kliknij prawym przyciskiem myszy inny wątek, a następnie kliknij polecenie **Przełącz do wątku**.  
  
5. Sprawdź okno **stos wywołań** w oknie źródło. Zawartość została zmieniona.  
  
6. Spójrz na pasek narzędzi **Lokalizacja debugowania** . Aktywny wątek został również zmieniony.  
  
7. Przejdź do paska narzędzi **Lokalizacja debugowania** . Kliknij pole **wątek** i wybierz inny wątek z listy rozwijanej.  
  
8. Zapoznaj się z oknem **wątki** . Wskaźnik aktywnego wątku został zmieniony.  
  
9. W oknie źródło kliknij prawym przyciskiem myszy znacznik wątku. W menu skrótów wskaż polecenie **Przełącz do** i kliknij nazwę wątku/Numer ID.  
  
     Widzisz teraz trzy sposoby zmiany aktywnego wątku: przy użyciu okna **wątki** , pola **wątku** na pasku narzędzi **lokalizacji debugowania** oraz wskaźnika wątku w oknie źródłowym.  
  
     Za pomocą wskaźnika wątku można przełączyć tylko na wątki, które są zatrzymane w danej lokalizacji. Za pomocą okna **wątki** i paska narzędzi **lokalizacji debugowania** można przełączyć się na dowolny wątek.  
  
## <a name="freezing-and-thawing-thread-execution"></a>Zamrażanie i odblokowywanie wykonywania wątku  
  
#### <a name="to-freeze-and-unfreeze-threads"></a>Aby zablokować i odmrozić wątki  
  
1. W oknie **wątki** kliknij prawym przyciskiem myszy dowolny wątek, a następnie kliknij pozycję **Zablokuj**.  
  
2. Spójrz na aktywną kolumnę wątku. Para pionowych słupków znajduje się teraz. Te dwa niebieskie paski wskazują, że wątek jest zablokowany.  
  
3. Zapoznaj się z kolumną **Wstrzymaj** . Liczba wstrzymań dla wątku wynosi teraz 1.  
  
4. Kliknij prawym przyciskiem myszy zablokowany wątek, a następnie kliknij polecenie **rozmrażanie**.  
  
     Kolumna aktywnego wątku i zmiana kolumny **zawieszenia** .  
  
## <a name="see-also"></a>Zobacz też  
 [Debuguj aplikacje wielowątkowe](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Instrukcje: przełączanie do innego wątku podczas debugowania](../debugger/how-to-switch-to-another-thread-while-debugging.md)
