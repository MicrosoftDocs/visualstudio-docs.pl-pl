---
title: Analizuj problemy związane z pamięcią .NET Framework | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.diagnostics.managedmemoryanalysis
ms.assetid: 43341928-9930-48cf-a57f-ddcc3984b787
caps.latest.revision: 9
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e94edbeac381ac634171507766126ab954153eb1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295892"
---
# <a name="analyze-net-framework-memory-issues"></a>Analiza problemów pamięci .NET Framework
Znajdowanie przecieków pamięci i niewydajne użycie pamięci w .NET Framework kodzie przy użyciu analizatora pamięci zarządzanej przez program Visual Studio. Minimalna .NET Framework wersja kodu docelowego to .NET Framework 4,5.  
  
 Narzędzie do analizy pamięci analizuje informacje w *plikach zrzutów z danymi sterty* , które są kopią obiektów w pamięci aplikacji. Pliki zrzutu (. dmp) można zbierać z poziomu środowiska IDE programu Visual Studio lub za pomocą innych narzędzi systemu.  
  
- Możesz analizować pojedynczej migawki zrozumieć konsekwencje typów obiektów na wykorzystanie pamięci i znaleźć kod w swojej aplikacji, która używa pamięci nieefektywne.  
  
- Możesz również porównać (*diff*) dwie migawki aplikacji, aby znaleźć w kodzie obszary, które powodują zwiększenie ilości pamięci w czasie.  
  
  Przewodnik dotyczący analizatora pamięci zarządzanej znajduje się w temacie [używanie Visual Studio 2013 do diagnozowania problemów z pamięcią .NET w środowisku produkcyjnym](https://devblogs.microsoft.com/devops/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production/) na blogu programu Visual Studio ALM + Team Foundation Server.  
  
## <a name="BKMK_Contents"></a>Contents  
 [Użycie pamięci w aplikacjach .NET Framework](#BKMK_Memory_use_in__NET_Framework_apps)  
  
 [Identyfikowanie problemu z pamięcią w aplikacji](#BKMK_Identify_a_memory_issue_in_an_app)  
  
 [Zbieranie migawek pamięci](#BKMK_Collect_memory_snapshots)  
  
 [Analizowanie użycia pamięci](#BKMK_Analyze_memory_use)  
  
## <a name="BKMK_Memory_use_in__NET_Framework_apps"></a>Użycie pamięci w aplikacjach .NET Framework  
 .NET Framework to środowisko uruchomieniowe środowiska wykonawczego, więc w większości aplikacji użycie pamięci nie jest problemem. Jednak w długotrwałych aplikacjach, takich jak usługi sieci Web i aplikacje, a w przypadku urządzeń z ograniczoną ilością pamięci, nagromadzenie obiektów w pamięci może mieć wpływ na wydajność aplikacji i urządzenie, na którym działa. Nadmierne wykorzystanie pamięci może zablokować dostęp aplikację i maszynę zasobów, jeśli moduł wyrzucania elementów bezużytecznych jest uruchomiony zbyt często lub jeśli system operacyjny jest zmuszony do przenoszenia pamięci między pamięcią RAM a dyskiem. W najgorszym przypadku aplikacja może ulec awarii z wyjątkiem wyjątku "Brak pamięci".  
  
 *Sterta zarządzana* przez platformę .NET to region pamięci wirtualnej, w którym są przechowywane obiekty referencyjne utworzone przez aplikację. Okres istnienia obiektów jest zarządzany przez moduł wyrzucania elementów bezużytecznych (GC). Moduł zbierający elementy bezużyteczne używa odwołań do śledzenia obiektów, które zajmują bloki pamięci. Odwołanie jest tworzone podczas tworzenia obiektu i przypisywania go do zmiennej. Pojedynczy obiekt może mieć wiele odwołań. Na przykład dodatkowe odwołania do obiektu można utworzyć przez dodanie obiektu do klasy, kolekcji lub innej struktury danych lub przez przypisanie obiektu do drugiej zmiennej. Mniej oczywisty sposób tworzenia odwołania polega na tym, że jeden obiekt dodaje procedurę obsługi do zdarzenia innego obiektu. W takim przypadku drugi obiekt przechowuje odwołanie do pierwszego obiektu do momentu usunięcia jawnie procedury obsługi lub zerwania drugiego obiektu.  
  
 Dla każdej aplikacji, wykaz globalny utrzymuje drzewo odwołań, które śledzą obiekty, do których odwołuje się aplikacja. *Drzewo odwołań* zawiera zestaw katalogów głównych, które obejmują obiekty globalne i statyczne, a także skojarzone stosy wątków i dynamicznie tworzone obiekty. Obiekt jest odblokowany, jeśli obiekt ma co najmniej jeden obiekt nadrzędny, który zawiera odwołanie do niego. Wykaz globalny może odzyskiwać pamięć obiektu tylko wtedy, gdy żaden inny obiekt lub zmienna w aplikacji nie ma odwołania do niego.  
  
 ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
## <a name="BKMK_Identify_a_memory_issue_in_an_app"></a>Identyfikowanie problemu z pamięcią w aplikacji  
 Najbardziej widocznym objawem problemów z pamięcią jest wydajność aplikacji, szczególnie w przypadku obniżenia wydajności w czasie. Spadek wydajności innych aplikacji, gdy aplikacja jest uruchomiona, może również oznaczać problem z pamięcią. Jeśli podejrzewasz problem z pamięcią, użyj narzędzia, takiego jak Menedżer zadań lub [Monitor wydajności systemu Windows](https://technet.microsoft.com/library/cc749249.aspx) , aby dokładniej zbadać. Na przykład poszukaj wzrostu w łącznym rozmiarze pamięci, której nie można wyjaśnić jako możliwego źródła przecieków pamięci:  
  
 ![Spójny wzrost ilości pamięci w Monitor zasobów](../misc/media/mngdmem-resourcemanagerconsistentgrowth.png "MNGDMEM_ResourceManagerConsistentGrowth")  
  
 Można również zauważyć, że maksymalne ilości pamięci, które są większe niż wiedza o kodzie, sugerują się, co może wskazywać na niewydajne użycie pamięci w procedurze:  
  
 ![Maksymalne ilości pamięci w Menedżer zasobów](../misc/media/mngdmem-resourcemanagerspikes.png "MNGDMEM_ResourceManagerSpikes")  
  
## <a name="BKMK_Collect_memory_snapshots"></a>Zbieranie migawek pamięci  
 Narzędzie do analizy pamięci analizuje informacje w *plikach zrzutu* , które zawierają informacje o stercie. Pliki zrzutu można tworzyć w programie Visual Studio lub za pomocą narzędzia, takiego jak [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx) z [Windows Sysinternals](https://technet.microsoft.com/sysinternals). Zobacz artykuł [co to jest zrzut i jak go utworzyć?](https://blogs.msdn.microsoft.com/debugger/2009/12/30/what-is-a-dump-and-how-do-i-create-one/) na blogu zespołu debugera programu Visual Studio.  
  
> [!NOTE]
> Większość narzędzi może zbierać informacje zrzutu z pełnymi danymi pamięci sterty lub bez nich. Analizator pamięci programu Visual Studio wymaga pełnych informacji o stercie.  
  
 **Aby zebrać Zrzut z programu Visual Studio**  
  
1. Można utworzyć plik zrzutu dla procesu, który został uruchomiony z projektu programu Visual Studio, lub dołączyć debuger do uruchomionego procesu. Zobacz [dołączanie do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
2. Zatrzymaj wykonywanie. Debuger zostaje zatrzymany w przypadku wybrania opcji **Przerwij wszystko** w menu **debugowanie** lub na wyjątek lub w punkcie przerwania  
  
3. W menu **debugowanie** wybierz polecenie **Zapisz zrzut jako**. W oknie dialogowym **Zapisz zrzut jako** Określ lokalizację i upewnij się, że na liście **Zapisz jako typ** jest wybrana wartość **minizrzutu z stertą** (domyślnie).  
  
   **Aby porównać dwie migawki pamięci**  
  
   Aby przeanalizować wzrost wykorzystania pamięci aplikacji, Zbierz dwa pliki zrzutu z jednego wystąpienia aplikacji.  
  
   ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
## <a name="BKMK_Analyze_memory_use"></a>Analizowanie użycia pamięci  
 [Filtrowanie listy obiektów](#BKMK_Filter_the_list_of_objects) **&#124;** [Analizowanie danych pamięci z jednej migawki](#BKMK_Analyze_memory_data_in_from_a_single_snapshot) **&#124;** [porównanie dwóch migawek pamięci](#BKMK_Compare_two_memory_snapshots)  
  
 Aby przeanalizować plik zrzutu pod kątem problemów z użyciem pamięci:  
  
1. W programie Visual Studio wybierz **plik**, **Otwórz** i określ plik zrzutu.  
  
2. Na stronie **Podsumowanie pliku minizrzutu** wybierz polecenie **Debuguj pamięć zarządzaną**.  
  
    ![Strona podsumowania pliku zrzutu](../misc/media/mngdmem-dumpfilesummary.png "MNGDMEM_DumpFileSummary")  
  
   Analizator pamięci uruchamia sesję debugowania, aby przeanalizować plik i wyświetlał wyniki na stronie widoku sterty:  
  
   ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
### <a name="BKMK_Filter_the_list_of_objects"></a>Filtrowanie listy obiektów  
 Domyślnie Analizator pamięci filtruje listę obiektów w migawce pamięci, aby wyświetlić tylko typy i wystąpienia, które są kodem użytkownika, i wyświetlić tylko te typy, których łączny rozmiar włącznie przekracza próg procentowy całkowitego rozmiaru sterty. Te opcje można zmienić na liście **Wyświetl ustawienia** :  
  
|||  
|-|-|  
|**Włącz Tylko mój kod**|Tylko mój kod ukrywa najpopularniejsze obiekty systemowe, tak aby na liście były wyświetlane tylko utworzone typy.<br /><br /> Możesz również ustawić opcję Tylko mój kod w oknie dialogowym **Opcje** programu Visual Studio. W menu **debugowanie** wybierz **Opcje i ustawienia**. Na karcie **debugowanie**/**Ogólne** wybierz lub wyczyść **tylko mój kod**.|  
|**Zwiń małe obiekty**|**Zwiń małe obiekty** ukrywa wszystkie typy, których łączny rozmiar łącznie jest mniejszy niż 0,5 procent całkowitego rozmiaru sterty.|  
  
 Możesz również filtrować listę typów, wprowadzając ciąg w polu **wyszukiwania** . Na liście są wyświetlane tylko te typy, których nazwy zawierają ciąg.  
  
 ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
### <a name="BKMK_Analyze_memory_data_in_from_a_single_snapshot"></a>Analizowanie danych pamięci z pojedynczej migawki  
 Program Visual Studio uruchamia nową sesję debugowania, aby przeanalizować plik i wyświetlał dane pamięci w oknie widoku sterty.  
  
 ![Lista typów obiektów](../misc/media/dbg-mma-objecttypelist.png "DBG_MMA_ObjectTypeList")  
  
 ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
#### <a name="object-type-table"></a>Tabela typów obiektów  
 W górnej tabeli wymieniono typy obiektów, które są przechowywane w pamięci.  
  
- **Liczba** wskazuje liczbę wystąpień typu w migawce.  
  
- **Rozmiar (w bajtach)** to rozmiar wszystkich wystąpień typu, z wyłączeniem rozmiaru obiektów, do których są przechowywane odwołania. Microsoft®  
  
- **Rozmiar włącznie (w bajtach)** obejmuje rozmiary obiektów, do których istnieją odwołania.  
  
  Można wybrać ikonę wystąpienia (![ikona wystąpienia w kolumnie Typ obiektu](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon")) w kolumnie **Typ obiektu** , aby wyświetlić listę wystąpień tego typu.  
  
#### <a name="instance-table"></a>Tabela wystąpień  
 ![Tabela wystąpień](../misc/media/dbg-mma-instancestable.png "DBG_MMA_InstancesTable")  
  
- **Wystąpienie** jest lokalizacją pamięci obiektu, który służy jako identyfikator obiektu  
  
- **Wartość** przedstawia rzeczywistą wartość typów wartości. Możesz umieścić kursor na nazwie typu odwołania, aby wyświetlić jego wartości danych w etykietce danych.  
  
   ![Wartości wystąpień w etykietce danych](../misc/media/dbg-mma-instancevaluesindatatip.png "DBG_MMA_InstanceValuesInDataTip")  
  
- **Rozmiar (w bajtach)** jest rozmiarem obiektu, bez względu na rozmiar obiektów, do których są przechowywane odwołania. Microsoft®  
  
- **Rozmiar włącznie (w bajtach)** obejmuje rozmiary obiektów, do których istnieją odwołania.  
  
  Domyślnie typy i wystąpienia są sortowane według **rozmiaru włącznie (w bajtach)** . Wybierz nagłówek kolumny na liście, aby zmienić kolejność sortowania.  
  
#### <a name="paths-to-root"></a>Ścieżki do katalogu głównego  
  
- W przypadku typu wybranego z tabeli **typu obiektu** **ścieżki do tabeli głównej** przedstawiają unikatowe hierarchie typów, które prowadzą do obiektów głównych dla wszystkich obiektów typu, wraz z liczbą odwołań do typu znajdującego się powyżej w hierarchii.  
  
- Dla obiektu wybranego z wystąpienia typu, **ścieżki do katalogu głównego** pokazuje Graf rzeczywistych obiektów, które zawierają odwołanie do wystąpienia. Możesz umieścić kursor na nazwie obiektu, aby wyświetlić jego wartości danych w etykietce danych.  
  
#### <a name="referenced-types--referenced-objects"></a>Odwołania do typów/przywoływanych obiektów  
  
- Dla typu wybranego z tabeli **Typ obiektu** na karcie typy, do **których istnieją odwołania** , wyświetlany jest rozmiar i liczba przywoływanych typów, które są przechowywane przez wszystkie obiekty wybranego typu.  
  
- W przypadku wybranego wystąpienia typu **obiekty, do których istnieją odwołania** , są wyświetlane obiekty, które są przechowywane w wybranym wystąpieniu. Możesz umieścić wskaźnik myszy nad nazwą, aby wyświetlić jej wartości danych w etykietce danych.  
  
  **Odwołania cykliczne**  
  
  Obiekt może odwoływać się do drugiego obiektu, który bezpośrednio lub pośrednio zawiera odwołanie do pierwszego obiektu. Gdy Analizator pamięci napotka tę sytuację, kończy rozszerzanie ścieżki odniesienia i dodaje adnotację **[wykryto cykl]** do listy pierwszego obiektu i kończy.  
  
  **Typy główne**  
  
  Analizator pamięci dodaje adnotacje do obiektów głównych, które opisują rodzaj posiadanego odwołania:  
  
|Adnotacja|Opis|  
|----------------|-----------------|  
|**Zmienna statyczna** `VariableName`|Zmienna statyczna. `VariableName` to nazwa zmiennej.|  
|**Uchwyt finalizacji**|Odwołanie z kolejki finalizatora|  
|**Zmienna lokalna**|Zmienna lokalna.|  
|**Silne dojście**|Dojście do silnego odwołania z tabeli uchwytów obiektów.|  
|**Asynchroniczne. Przypięty uchwyt**|Asynchroniczny obiekt przypięty z tabeli uchwytów obiektu.|  
|**Dojście zależne**|Obiekt zależny z tabeli uchwytów obiektów.|  
|**Przypięty uchwyt**|Przypięte silne odwołanie z tabeli uchwytów obiektów.|  
|**Dojście dojście Refcount**|Obiekt liczony jako odwołanie z tabeli uchwytów obiektów.|  
|**Dojście dojście SizedRef**|Silne dojście, które utrzymuje przybliżony rozmiar całego rozłącznego zamykania wszystkich obiektów i katalogów głównych obiektów w czasie odzyskiwania pamięci.|  
|**Przypięta zmienna lokalna**|Przypięta zmienna lokalna.|  
  
### <a name="BKMK_Compare_two_memory_snapshots"></a>Porównanie dwóch migawek pamięci  
 Można porównać dwa pliki zrzutu procesu, aby znaleźć obiekty, które mogą być przyczyną przecieków pamięci. Interwał między kolekcją pierwszego (wcześniejszego) i drugiego (nowszego) pliku powinien być wystarczająco duży, aby wzrost liczby przecieków obiektów był łatwo widoczny. Aby porównać te dwa pliki:  
  
1. Otwórz drugi plik zrzutu, a następnie wybierz polecenie **Debuguj pamięć zarządzaną** na stronie **podsumowania pliku minizrzutu** .  
  
2. Na stronie Raport analizy pamięci Otwórz listę **Wybierz linię bazową** , a następnie wybierz pozycję **Przeglądaj** , aby określić pierwszy plik zrzutu.  
  
   Analizator dodaje kolumny do górnego okienka raportu, w którym jest wyświetlana różnica między **liczbą**, **rozmiarem**i **rozmiarem włącznie** typów do tych wartości we wcześniejszej migawce.  
  
   ![Kolumny różnic na liście typów](../misc/media/mngdmem-diffcolumns.png "MNGDMEM_DiffColumns")  
  
   Kolumna **różnic w liczbie odwołań** jest również dodawana do tabeli **głównej** .  
  
   ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
## <a name="see-also"></a>Zobacz też  
 [Blog programu VS ALM TFS: używanie Visual Studio 2013 do diagnozowania problemów z pamięcią .NET w środowisku produkcyjnym](https://devblogs.microsoft.com/devops/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production/)   
 [Analiza pamięci &#124; zarządzanego programu Visual &#124; Studio TV w kanale 9](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Managed-Memory-Analysis)   
 [Analiza pamięci &#124; zarządzanego zestawu narzędzi &#124; kanału 9 programu Visual Studio w Visual Studio 2013](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Managed-Memory-Analysis-in-Visual-Studio-2013)