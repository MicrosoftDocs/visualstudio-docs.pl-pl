---
title: Zmienianie dziennika (Visual Studio Tools for Unity, Windows) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/06/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: ea490b7e-fc0d-44b1-858a-a725ce20e396
author: johmil
ms.author: therealjohn
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 129e7fa7691d0e03f44190de83d07bd09c4f2f5f
ms.sourcegitcommit: 150fa6ec89ea2d086c0af9ababbaf6103a12eff1
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/06/2018
ms.locfileid: "52954217"
---
# <a name="change-log-visual-studio-tools-for-unity-windows"></a>Dziennik zmian (Visual Studio Tools for Unity, Windows)
Dziennik zmian w programie Visual Studio Tools for Unity.

## <a name="3807"></a>3.8.0.7
 Wydana 20 września 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Debuger:**

    -   Naprawiono zakleszczenie w bibliotece, używany do komunikacji z aparatem debugera mechanizmu Unity, dzięki czemu program Visual Studio lub Unity, blokowanie, szczególnie w przypadku osiągnięcia "Dołącz do aparatu Unity" lub ponownego uruchamiania gry.

## <a name="3806"></a>3.8.0.6
 Wydana 27 sierpnia 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Integracja:**

    -   Naprawiono ponownego ładowania projektów i rozwiązań.

## <a name="3805"></a>3.8.0.5
 wydana 20 sierpnia 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Integracja:**

    -   Naprawiono projektu monitorowania usuwania subskrypcji.

## <a name="3804"></a>3.8.0.4
 Wydana 14 sierpnia 2018 r.

### <a name="new-features"></a>Nowe funkcje

-   **Ocena:**

    -   Dodano obsługę wartości wskaźnika.

    -   Dodano obsługę dla metod ogólnych.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Integracja:**

    -   Inteligentne ponowne załadowanie z wieloma projektami zmienione.

## <a name="3803"></a>3.8.0.3
 Wydana 24 lipca 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Generowanie projektu:**

    -   Wycofane obejście dla aparatu Unity usterka wydajności, który został rozwiązany przez aparat Unity.

## <a name="3802"></a>3.8.0.2
 Wydana 7 lipca 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Generowanie projektu:**

    -   Obejście przejściowych błędów wydajności aparatu Unity: pamięci podręcznej MonoIslands podczas generowania projektów.

## <a name="3801"></a>3.8.0.1
 Wydana 26 czerwca 2018 r.

### <a name="new-features"></a>Nowe funkcje

-   **Debugowanie:**

    -   Dodano obsługę poleceń UserLog i UserBreak.

    -   Obsługa dodano załadować z opóźnieniem typu (optymalizowanie opóźnienie odpowiedzi obciążenia i debuger sieci).

### <a name="bug-fixes"></a>Poprawki błędów

-   **Ocena:**

    -   Udoskonalone Obliczanie wyrażenia operator binarny i metoda wyszukiwania.

## <a name="3800"></a>3.8.0.0
 Wydanie: 30 maja 2018 r.

### <a name="new-features"></a>Nowe funkcje

-   **Debugowanie:**

    -   Dodano obsługę wyświetlanie zmiennych w konstrukcji asynchronicznej.

    -   Dodano obsługę przetwarzania zagnieżdżonych typów podczas ustawiania punktów przerwania, aby zapobiec ostrzeżenia za pomocą kompilatora konstrukcji.

-   **Integracja:**

    -   Dodano obsługę dla gramatyk textmate programów do cieniowania (obciążeniu C++ nie jest potrzebna dla barwy kodu programu do cieniowania).

### <a name="bug-fixes"></a>Poprawki błędów

-   **Generowanie projektu:**

    -   Nie można konwertować przenośnego pliku pdb mdb już korzystając z nowego środowiska uruchomieniowego platformy Unity.

## <a name="3701"></a>3.7.0.1
 Wydana 7 maja 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Instalator:**

    -   Naprawiono zależności problem, korzystając z doświadczalnych kompilacji.

## <a name="3700"></a>3.7.0.0
 Wydana 7 maja 2018 r.

### <a name="new-features"></a>Nowe funkcje

-   **Debugowanie:**

    -   Dodano obsługę debugowania zorganizowane (debugowanie w wielu graczy i edytorem przy użyciu tej samej sesji programu Visual Studio).

    -   Dodano obsługę odtwarzacza systemu Android USB debugowania.

    -   Dodano obsługę dla platformy uniwersalnej systemu Windows/IL2CPP player debugowania.

-   **Ocena:**

    -   Dodano obsługę specyfikatory szesnastkowe.

    -   Obejrzyj Ulepszone okno dokonywaniu oceny oprogramowania.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Integracja:**

    -   Naprawiono użycie ustawienia wyjątków.

-   **Generowanie projektu:**

    -   Wyklucz jednostki kompilacji Menedżera pakietów z generacji.

## <a name="3605"></a>3.6.0.5
 Wydana 13 marca 2018 r.

### <a name="new-features"></a>Nowe funkcje

-   **Generowanie projektu:**

    -   Dodano obsługę nowych generator projektu w 2018.1 aparatu Unity.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Integracja:**

    -   Naprawiono obsługę uszkodzony stanów niestandardowych projektów.

-   **Debuger:**

    -   Stała, ustawienie następnej instrukcji.

## <a name="3604"></a>3.6.0.4
 Wydanie 5 marca 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Generowanie projektu:**

    -   Wykrywanie poprawionej wersji platformy Mono.

-   **Integracja:**

    -   Rozwiązano problemy dotyczące synchronizacji z 2018.1 i aktywacją wtyczka.

## <a name="3603"></a>3.6.0.3
 Wydana 23 lutego 2018 r.

### <a name="new-features"></a>Nowe funkcje

-   **Generowanie projektu:**

    -   Dodano obsługę dla platformy .NET Standard.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Generowanie projektu:**

    -   Naprawiono wykrywanie framework docelowej aparatu Unity.

-   **Debuger:**

    -   Naprawiono podziału na wyjątki, które są wyrzucane poza usercode.

## <a name="3602"></a>3.6.0.2
 Wydana 7 lutego 2018 r.

### <a name="new-features"></a>Nowe funkcje

-   **Integracja:**

    -   Zaktualizuj powierzchnię interfejsu API UnityMessage dla 2017.3.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Integracja:**

    -   Ponownie ładować tylko projekty na zewnętrzne zmiany (po zastosowaniu ograniczania).

## <a name="3601"></a>3.6.0.1
 Wydana 24 stycznia 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Integracja:**

    -   Stałym pdb automatyczne do konwersji symboli debugowania mdb.

    -   Naprawiono wywołanie pośrednie EditorPrefs.GetBool wpływające na panelu Inspektor podczas próby zmiany rozmiaru tablicy.

## <a name="3600"></a>3.6.0.0
 Wydana 10 stycznia 2018 r.

### <a name="new-features"></a>Nowe funkcje

-   **Generowanie projektu:**

    -   Dodano obsługę 2018.1 model referencyjny MonoIsland.

-   **Ocena:**

    -   Dodano obsługę $exception identyfikatora.

-   **Debuger:**

    -   Dodano obsługę DebuggerHidden/DebuggerStepThrough atrybuty z nowego środowiska uruchomieniowego platformy Unity.

-   **Kreatorów:**

    -   Wprowadzenie "Najnowszej" wersji dla kreatorów.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Generowanie projektu:**

    -   Naprawiono obliczenia identyfikatora guid projektu dla projektów odtwarzacza.

-   **Debuger:**

    -   Naprawiono wyścigu podczas obsługi najważniejszych zdarzeń.

-   **Kreatorów:**

    -   Odśwież kontekstu roslyn przed wstawieniem metody.

## <a name="3503"></a>3.5.0.3
 Wydana 9 stycznia 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Integracja:**

    -   Stałym pdb automatyczne do konwersji symboli debugowania mdb.

## <a name="3502"></a>3.5.0.2
 Wydana 4 grudnia 2017 r.

### <a name="new-features"></a>Nowe funkcje

-   **Integracja:**

    -   Projekty Unity są teraz automatycznie ponownie ładowane w programie Visual Studio po dodaniu skryptu do środowiska Unity lub jego usunięciu.

-   **Debuger:**

    -   Dodano opcję użycia debugera Mono udostępnianego przez platformę Xamarin i programu Visual Studio dla komputerów Mac do debugowania programu Unity Editor.

    -   Dodano obsługę plików symboli debugowania przenośnej.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Integracja:**

    -   Rozwiązano problemy z instalacją zależności.

    -   Naprawiono menu Pomoc interfejsu API aparatu Unity nie są wyświetlane.

-   **Generowanie projektu:**

    -   Generowanie projektu player stały podczas pracy nad gry platformy uniwersalnej systemu Windows z zapleczem IL2CPP/.NET 4.6.

    -   Naprawiono rozszerzenie .dll dodatkowe błędnie dodane do nazwy pliku zestawu.

    -   Naprawiono użycie określonego projektu interfejsu API poziom zgodności zamiast globalnego.

    -   Nie Wymuszaj flagi AllowAttachedDebuggingOfEditor Unity, zgodnie z wartością domyślną jest teraz "true".

## <a name="3402"></a>3.4.0.2
 Wydana 19 września 2017 r.

### <a name="new-features"></a>Nowe funkcje

-   **Generowanie projektu:**

    -   Dodano obsługę jednostki kompilacji assembly.json.

    -   Zatrzymać kopiowanie zestawów aparatu Unity do folderu projektu.

-   **Debuger:**

    -   Dodano obsługę ustawienie następnej instrukcji z nowego środowiska uruchomieniowego platformy Unity.

    -   Dodano obsługę typu dziesiętnego za pomocą nowego środowiska uruchomieniowego platformy Unity.

    -   Dodano obsługę niejawnej/jawnej konwersji.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Ocena:**

    -   Naprawiono utworzenie tablicy o rozmiarze niejawne.

    -   Stałą kompilatora generowane elementów zmiennych lokalnych.

-   **Generowanie projektu:**

    -   Naprawiono odwołania do Microsoft.CSharp 4.6 poziom interfejsu API.

## <a name="3302"></a>3.3.0.2
 Wydanie: 15 sierpnia 2017 r.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Generowanie projektu:**

    -   Stała generowania rozwiązania programu Visual Studio na Unity 5.5 i poprzednich wersjach.

## <a name="3300"></a>3.3.0.0
 Wydana 14 sierpnia 2017 r.

### <a name="new-features"></a>Nowe funkcje

-   **Ocena:**

    -   Dodano obsługę tworzenia struktury za pomocą nowego środowiska uruchomieniowego platformy Unity.

    -   Dodano obsługę minimalistyczny wskaźników.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Ocena:**

    -   Stałe wywołanie metody do elementów podstawowych.

    -   Pole stałej ocena o typach oznaczone atrybutem BeforeFieldInit.

    -   Naprawiono nieobsługiwanym wywołania z operatorami dwuargumentowymi (odejmowanie).

    -   Rozwiązano problemy podczas dodawania elementów do programu Visual Studio zegarka.

-   **Generowanie projektu:**

    -   Naprawiono zestawu odwołania do nazwy mcs.rsp plików.

    -   Naprawiono definiuje ze poziomy interfejsu API.

## <a name="3200"></a>3.2.0.0
 Wydana 10 maja 2017 r.

### <a name="new-features"></a>Nowe funkcje

-   **Instalator:**

    -   Dodano obsługę czyszczenia pamięć podręczna MEF.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Edytor kodu:**

    -   Naprawiono klasyfikacji/Zakończenie uruchamiania nastąpi po atrybutów niestandardowych.

    -   Naprawiono migotanie przy użyciu komunikatów aparatu Unity.

## <a name="3100"></a>3.1.0.0
 Wydana 7 kwietnia 2017 r.

### <a name="new-features"></a>Nowe funkcje

-   **Debuger:**

    -   Dodano obsługę nowego środowiska uruchomieniowego aparatu Unity (przy użyciu platformy .NET 4.6 / zgodność z narzędziami języka C# 6).

-   **Generowanie projektu:**

    -   Dodano obsługę profilu .NET 4.6.

    -   Dodano obsługę mcs.rsp plików.

    -   Zawsze należy włączyć niebezpieczne kompilacji przełącznika, gdy jest używane środowisko Unity 5.6.

    -   Dodano obsługę Generowanie projektu "Player" korzystając z zaplecza platformy i il2cpp Windows Store.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Edytor kodu:**

    -   Naprawiono położeniu karetki, po wstawieniu metody za pomocą automatycznego uzupełniania.

-   **Generowanie projektu:**

    -   Przetwarzanie końcowe wersji zestawu usunięte.

## <a name="3001"></a>3.0.0.1
 Wydana 7 marca 2017 r.

### <a name="this-version-includes-all-new-features-and-bug-fixes-introduced-with-28x-series"></a>Ta wersja zawiera wszystkie nowe funkcje i poprawki wprowadzone w programie 2.8.x serii.

## <a name="2820---30-preview-3"></a>2.8.2.0 - 3.0 w wersji zapoznawczej 3
 Wydanie: 25 stycznia 2017 r.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Generowanie projektu:**

    -   Naprawiono regresji, gdzie projektów wtyczek w przypadku, gdy dwa razy, do których odwołuje się najpierw jako binarne DLL następnie jako projekt odwołania.

## <a name="2810---30-preview-2"></a>2.8.1.0 - 3.0 w wersji zapoznawczej 2
 Wydana 23 stycznia 2017 r.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Edytor kodu:**

    -   Naprawiono awarię, podczas uruchamiania deklaracji atrybutu bez uzupełnianie nawiasów.

-   **Debuger:**

    -   Punkty przerwania funkcji stały koprocedur w obszarze nowego środowiska Unity kompilatora/środowiska uruchomieniowego.

    -   Dodano ostrzeżenie w razie unbindable punkt przerwania (Jeśli nie odpowiedniej lokalizacji źródłowej znajduje się).

-   **Generowanie projektu:**

    -   Naprawiono Generowanie pliku csproj przy użyciu znaków specjalnych/zlokalizowane.

    -   Naprawiono odwołania poza zasobów, takich jak biblioteki (np. Facebook SDK).

-   **Różne:**

    -   Dodano kontrolę, aby uniemożliwić Unity uruchomiona podczas instalowania lub odinstalowywania.

    -   Przełączono na https pod kątem zdalnego dokumentacja aparatu Unity.

## <a name="2800---30-preview"></a>2.8.0.0 - 3.0 (wersja zapoznawcza)
 Wydanie 17 listopada 2016 r.

### <a name="new-features"></a>Nowe funkcje

-   **Ogólne:**

    -   Dodano obsługę Instalatora programu Visual Studio 2017.

    -   Dodano obsługę rozszerzeń programu Visual Studio 2017.

    -   Obsługa dodano lokalizacji.

-   **Edytor kodu:**

    -   Dodano C# funkcja IntelliSense dla komunikatów Unity.

    -   Dodano C# kodu barwy dla komunikatów Unity.

-   **Debuger:**

    -   Dodano obsługę `is`, `as`, bezpośrednie rzutowanie, `default`, `new` wyrażenia.

    -   Dodano obsługę wyrażenia concat ciągu.

    -   Dodano obsługę wyświetlanie szesnastkowe liczb całkowitych.

    -   Dodano obsługę tworzenia nowych zmiennych tymczasowych (poufności informacji).

    -   Dodano obsługę niejawne konwersje pierwotnych.

    -   Dodano lepsze komunikaty o błędach, gdy typem jest nieoczekiwany lub nie można odnaleźć.

-   **Generowanie projektu:**

    -   Usunięte sufiksu języka CSharp z nazwy projektu.

    -   Usunięto odwołanie do pliku elementów docelowych msbuild szerokiego systemu.

-   **Kreatorów:**

    -   Dodano obsługę dla komunikatów Unity w typach innych zachowań, takich jak edytor lub EditorWindow.

    -   Przełączenie do Roslyn wstrzyknąć i sformatować komunikaty aparatu Unity.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Debuger:**

    -   Usunięto usterkę uległa awarii platformy Unity podczas oceny typów ogólnych.

    -   Naprawiono obsługę typów dopuszczających wartości zerowe.

    -   Naprawiono obsługę typów wyliczeniowych.

    -   Naprawiono obsługi typów zagnieżdżonych elementów członkowskich.

    -   Dostęp indeksatora stałej kolekcji.

    -   Naprawiono obsługę debugowania iteratora ramki za pomocą nowego kompilator języka C#.

-   **Generowanie projektu:**

    -   Usunięto usterkę uniemożliwiającą kompilacji, gdy gracz Unity w sieci Web.

    -   Usunięto usterkę uniemożliwiającą kompilacji podczas kompilacji skryptu z internetowym kodowany w formacie nazwy pliku.

## <a name="2300"></a>2.3.0.0
 Wydana 14 lipca 2016 r.

### <a name="new-features"></a>Nowe funkcje

-   **Ogólne:**

    -   Dodano możliwość wyłączenia konsoli Unity dzienniki w liście błędów Visual Studio.

    -   Dodano opcję Zezwalaj na właściwości wygenerowanego projektu do zmodyfikowania.

-   **Debuger:**

    -   Ciąg wizualizatorów, dodano tekstu XML, HTML i JSON.

-   **Kreatorów:**

    -   Dodano brakujący MonoBehaviors.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Ogólne:**

    -   Rozwiązano konflikt z ReSharper, uniemożliwiającą kontrolek w Visual Studio, ustawienia będą wyświetlane.

    -   Rozwiązano konflikt ze środowiskiem Xamarin, który uniemożliwia debugowania w niektórych przypadkach.

-   **Debuger:**

    -   Rozwiązano problem powodujący zablokowanie podczas debugowania programu Visual Studio.

    -   Rozwiązano problem z punktów przerwania funkcji w programie Visual Studio 2015.

    -   Rozwiązano wyrażenie kilka problemów oceny.

## <a name="2200"></a>2.2.0.0
 Wydana 4 lutego 2016 r.

### <a name="new-features"></a>Nowe funkcje

-   **Kreatorów:**

    -   Dodano inteligentne wyszukiwanie w **MonoBehavior Implementowanie** kreatora.

    -   Świadomość; kontekst jako kreatorzy na przykład NetworkBehavior komunikaty są dostępne tylko podczas pracy z NetworkBehavior.

    -   Dodano obsługę komunikatów NetworkBehavior w kreatorach.

-   **INTERFEJS UŻYTKOWNIKA:**

    -   Dodano opcję, aby skonfigurować widoczność MonoBehavior wiadomości.

    -   Usunięte stron właściwości dla programu Visual Studio, które nie mają znaczenia dla projektów aparatu Unity.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Generowanie projektu:**

    -   Naprawiono odwołania do UnityEngine i UnityEditor na 4.6 aparatu Unity.

    -   Naprawiono Generowanie plików projektu, gdy Unity jest uruchomiony w systemie OSX.

    -   Naprawiono obsługi nazwy projektu zawierające znaki hashmark (#).

    -   Ograniczony wygenerowane projekty, do 4 C#.

-   **Debuger:**

    -   Rozwiązano problem z obliczanie wyrażeń podczas debugowania w koprocedury aparatu Unity.

    -   Rozwiązano problem powodujący zablokowanie podczas debugowania programu Visual Studio.

-   **INTERFEJS UŻYTKOWNIKA:**

    -   Naprawiono niezgodność z [Studio karty](https://tabsstudio.com/) rozszerzenia programu Visual Studio.

-   **Instalator:**

    -   Obsługuje instalację komputera VSTU (Instalacja dla wszystkich użytkowników), tworząc wpisy rejestru HKLM.

    -   Rozwiązane problemy dezinstalacji VSTU po zainstalowaniu tej samej wersji w narzędziach VSTU dla wielu różnych wersji programu Visual Studio. Na przykład, gdy w narzędziach VSTU **2015** 2.1.0.0 i w narzędziach VSTU **2013** 2.1.0.0 zostały zainstalowane.

## <a name="2100"></a>2.1.0.0
 Wydana 8 września 2015 r.

### <a name="new-features"></a>Nowe funkcje

-   Obsługa aparatu Unity 5.2

### <a name="bug-fixes"></a>Poprawki błędów

-   Wyświetlanie elementów menu w Unity < 4.2

-   Komunikat o błędzie nie będzie już wyświetlany w przypadku programu Visual Studio blokuje pliki intellisense XML.

-   Obsługa <\<po zmianie >> warunkowe punkty przerwania, gdy argument warunkowy nie jest wartością logiczną.

-   Naprawiono odwołania do zestawów UnityEngine i UnityEditor dla aplikacji Windows Store.

-   Naprawiono błąd przy przechodzeniu w debugerze: nie można wkroczyć ogólny wyjątek.

-   Stałej liczby trafień punkty przerwania w programie Visual Studio 2015.

## <a name="2000"></a>2.0.0.0
 Wydane 20 lipca 2015 r.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Integracja aparatu Unity:**

    -   Naprawiono konwersji symbole debugowania utworzonych za pomocą programu Visual Studio 2015, podczas importowania biblioteki DLL i jego symboli debugowania (PDB).

    -   Zawsze generuj pliki MDB podczas importowania biblioteki DLL i jego symboli debugowania (PDB), z wyjątkiem sytuacji, gdy podano również pliku MDB.

    -   Naprawiono zanieczyszczeniu katalogu projektu środowiska Unity za pomocą katalogu.

    -   Naprawiono Generowanie odwołania do System.Xml.Link i System.Runtime.Serialization.

    -   Punkty zaczepienia dodano obsługę wielu subskrybentów do generowania plików projektu interfejsu API.

    -   Generowanie pliku zawsze kompletnego projektu nawet wtedy, gdy jeden z plików do wygenerowania jest zablokowany.

    -   Dodano obsługę * symboli wieloznacznych w rozszerzeniu filtrowanie podczas określania plików, które mają zostać uwzględnione w projekcie języka C#.

-   **Integracja z programem Visual Studio:**

    -   Rozwiązano problem ze zgodnością z Productivity Power Tools.

    -   Naprawiono Generowanie MonoBehaviors wokół deklaracji zdarzeń i delegatów.

-   **Debuger:**

    -   Naprawiono potencjalne blokowanie, podczas debugowania.

    -   Rozwiązano problem, w której elementy lokalne, nie będzie wyświetlana w niektórych ramek stosu.

    -   Naprawiono sprawdzania pusty tablic.

## <a name="1990---20-preview-2"></a>1.9.9.0 - 2.0 w wersji zapoznawczej 2
 Wydana 2 kwietnia 2015 r.

### <a name="new-features"></a>Nowe funkcje

-   **Eksplorator projektu środowiska Unity:**

    -   Automatycznie Zmień nazwę klasy, zmieniając nazwę pliku w Eksploratorze projektów aparatu Unity (zobacz **opcje** okna dialogowego).

    -   Automatycznie wybierz nowo utworzony skryptów w Eksploratorze projektów aparatu Unity.

    -   Śledzenie aktywnych skryptów w Eksploratorze projektów aparatu Unity (zobacz **opcje** okna dialogowego).

    -   Dual — Synchronizuj Eksploratorze rozwiązań programu Visual Studio (zobacz **opcje** okna dialogowego).

    -   Przyjęcie ikony programu Visual Studio w Eksploratorze projektów aparatu Unity.

-   **Debuger:**

    -   Wybierz cel debugowania aktywnego listę celów debugowania zapisana lub ostatnio używanych (zobacz **opcje** okna dialogowego).

    -   Utwórz punkty przerwania funkcji w metodach MonoBehavior i zastosować je do wielu klas MonoBehavior.

    -   Obsługa wprowadzić identyfikator obiektu w debugerze.

    -   Obsługa liczba w debugerze trafień punktu przerwania.

    -   Obsługuje podział na wyjątek w debugerze (eksperymentalne. Zobacz **opcje** okna dialogowego).

    -   Obsługuje tworzenie obiekty i tablice podczas obliczania wyrażenia w debugerze.

    -   Obsługuje porównania wartości null podczas oceny wyrażenia w debugerze.

    -   Odfiltruj przestarzałe składowe w oknach wyrażenie kontrolne debugera.

-   **Instalator:**

    -   Zoptymalizowane Visual Studio Tools for Unity Rejestracja rozszerzenia.

    -   Zainstaluj program Visual Studio Tools dla pakietu Unity dla aparatu Unity 5.

-   **Dokumentacja:** poprawić wydajność Generowanie dokumentacji.

-   **Kreatorzy:** obsługę nowych metod MonoBehavior Unity 4.6 i aparatu Unity 5.

-   **Unity:** flagi niebezpieczne wyszukiwania i niestandardowych definiuje .rsp — pliki podczas generowania pliku projektu.

-   **Interfejs użytkownika:** dodano Visual Studio Tools for Unity **opcje** okna dialogowego w programie Visual Studio.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Eksplorator projektu środowiska Unity:**

    -   Odśwież Eksploratora projektów aparatu Unity po pliki są przesyłane lub zmieniono jego nazwę w Eksploratorze rozwiązań programu Visual Studio.

    -   Zachowaj opcje podczas zmieniania nazw plików w Eksploratorze projektów aparatu Unity.

    -   Uniemożliwić automatyczne rozwijać i zwijać gdy pliki są podwójnego kliknięcia w Eksploratorze projektów aparatu Unity.

    -   Upewnij się, że nowo wybrane pliki są widoczne w Eksploratorze projektów aparatu Unity.

-   **Debuger:**

    -   Uniemożliwia to możliwe, Zablokuj programu Visual Studio, podczas obliczania wyrażenia w debugerze.

    -   Upewnij się, że wywołania metod powinny być wykonywane dla domeny w debugerze.

-   **Unity:**

    -   Popraw lokalizację UnityVS.OpenFile za pomocą aparatu Unity 5.

    -   Popraw lokalizację pdb2mdb za pomocą aparatu Unity 5.

    -   Zapobiegaj możliwym wyjątkiem podczas generowania pliku projektu.

    -   Zapobiegaj możliwe blokowanie, podczas uruchamiania aparatu Unity w systemie OSX.

    -   Obsługa wyjątków wewnętrznych.

    -   Wyślij dzienniki konsoli Unity do listy błędów programu VS.

-   **Dokumentacja:** Popraw generowania dokumentacji dla nowej dokumentacji aparatu unity.

-   **Projekt:** Przenieś i Zmień nazwy plików .meta Unity w razie potrzeby, nawet w przypadku folderów.

-   **Kreatorzy:** Popraw kolejność parametrów metody MonoBehavior podczas generowania kodu.

-   **Interfejs użytkownika:** motywy pomocy technicznej programu Visual Studio dla ikony i menu kontekstowego.

## <a name="1980---20-preview"></a>1.9.8.0 - 2.0 (wersja zapoznawcza)
 Wydana 12 listopada 2014 r.

### <a name="new-features"></a>Nowe funkcje

-   Pomoc techniczna dla programu Visual Studio 2015.

-   Barwy kodu dla aparatu Unity programów do cieniowania programu Visual Studio 2015.

-   Ulepszone wizualizacji wartości podczas debugowania:

    -   Lepszą wizualizację ArrayLists, list, tabele i słowników.

    -   Pokaż niepubliczne elementy członkowskie i statyczne elementy członkowskie jako kategorii w wyrażenie kontrolne i lokalnych widokach.

    -   Ulepszone wyświetlanie SerializedProperty mechanizmu Unity do oceny, tylko pola wartość, które jest nieprawidłowa dla właściwości.

    -   Debuggerdisplayattribute — Obsługa klas i struktur.

    -   Debuggertypeproxyattribute — pomoc techniczna.

-   Należy wstawiania obiekt MonoBehaviour metody przy użyciu naszej kreatorów w celu uwzględniania użytkownika konwencje kodowania.

-   Implementuje obsługę szablony tekstowe czasu kompilacji w projektach UnityVS wygenerowany.

-   Implementuje obsługę zasobów ResX w projektach UnityVS wygenerowany.

-   Obsługa otwierania programów do cieniowania w programie Visual Studio z poziomu aparatu Unity.

### <a name="bug-fixes"></a>Poprawki błędów

-   Oczyszczanie gniazd przed rozpoczęciem gry na platformie Unity po Dołącz i odtwarzania zostały wyzwolone w programie Visual Studio. To naprawia pewne problemy z stabilności połączenia między Unity i programu VS, podczas korzystania z Dołącz i odtwarzania.

-   Należy unikać wywoływania metod w interfejsie debuger aparatu skryptów mechanizmu Unity, które są podatne na blokowanie aparatu Unity. To naprawia blokowanie aparatu Unity podczas dołączania debugera.

-   Napraw, wyświetlanie elementu stosy wywołań, jeśli brak symboli nie są dostępne.

-   Nie rejestruj wywołanie zwrotne dziennika, jeśli nie mamy.

## <a name="1920"></a>1.9.2.0
 Wydana 9 października 2014 r.

### <a name="new-features"></a>Nowe funkcje

-   Zwiększ wykrywania graczy aparatu Unity.

-   Korzystając z naszych użytkownika otwierającego plik, należy Unity przekazać numer wiersza, a także nazwę pliku.

-   Domyślnie się z dokumentacją online platformy Unity, jeśli nie lokalną dokumentację.

### <a name="bug-fixes"></a>Poprawki błędów

-   Naprawiono awarię Unity, gdy aktywacja punktu przerwania po domeny Załaduj ponownie.

-   Usuń wyjątki przedstawione w konsoli platformy Unity podczas zamykania naszym konfiguracji lub dotyczące systemu windows, po nazwie domeny Załaduj ponownie.

-   Napraw wykrywania Unity 64-bitowy, uruchamiane lokalnie.

-   Usuń filtrowanie Monobehaviour poszczególnych wersji aparatu Unity w kreatorach.

-   Naprawiono błąd, w którym wszystkie zasoby zostały uwzględnione w plikach projektu, jeśli filtr rozszerzeń był pusty.

## <a name="1910"></a>1.9.1.0
 Wydana 22 września 2014 r.

### <a name="new-features"></a>Nowe funkcje

-   Optymalizuj powiązania punktu przerwania w lokalizacji źródłowej.

-   Pomoc techniczna dla przeciążonych metod obliczania wyrażeń debugera.

-   Obsługa podstawowych pakowania i typy wartości obliczania wyrażeń debugera.

-   Obsługa ponownego tworzenia środowiska zmienne lokalne języka C#, podczas debugowania metod anonimowych.

-   Usuń, a następnie zmień nazwy plików .meta podczas usuwania lub zmiany nazwy plików w programie Visual Studio.

### <a name="bug-fixes"></a>Poprawki błędów

-   Naprawiono obsługę motywów programu Visual Studio. Wcześniej okien dialogowych na czarny motywy może być pusty.

-   Naprawiono blokowanie aparatu Unity, gdy połączenie ze debugera przy jednoczesnej konieczności ponownego kompilowania aparatu Unity.

-   Usuń punkty przerwania podczas debugowania zdalnego edytory lub graczy skompilowany w innym systemie.

-   Naprawiono ewentualnej awarii programu Visual Studio, gdy punkt przerwania zostaje trafiony.

-   Punkty przerwania napraw powiązania w celu uniknięcia punktów przerwania, przedstawiający jako zwolniony.

-   Naprawiono obsługę zakres zmiennej w debugerze, aby uniknąć zmiennych na żywo, które pojawiają się poza zakresem.

-   Napraw wyszukiwania statyczne elementy członkowskie obliczania wyrażeń debugera.

-   Napraw, wyświetlania typów obliczania wyrażeń debugera, aby wyświetlić właściwości i pola statyczne.

-   Naprawiono Generowanie rozwiązania, gdy nazwy projektów aparatu Unity zawiera znaki specjalne, że program Visual Studio zabrania (Połącz problem #948666).

-   Napraw pakiet Visual Studio Tools Unity, aby natychmiast zatrzymać wysyłanie zdarzenia konsoli po opcji unchecked (Połącz problem #933357).

-   Napraw wykrywania odwołania do odwołania do nowych interfejsów API, takich jak UnityEngine.UI w projektach UnityVS wygenerowany został poprawnie wygenerowany.

-   Napraw Instalator, aby wymagać, że program Visual Studio jest zamknięty przed rozpoczęciem instalacji, aby uniknąć uszkodzone instalacje.

-   Napraw Instalatora w celu zainstalowania zestawy odwołań Unity jako składnik odpowiednie autonomiczne, współużytkowana przez wszystkie wersje narzędzi vstu.

-   Poprawka otwieranie skryptów za pomocą rozszerzenia VSTU w 64-bitowej wersji aparatu Unity.

## <a name="1900"></a>1.9.0.0
 Wydana 29 lipca 2014 r.

### <a name="new-features"></a>Nowe funkcje

-   W oknie Dołącz debuger aparatu Unity dodanie możliwości do wprowadzania niestandardowego adresu IP i portu do debugowania.

-   Dodaj opcję konfiguracji, aby ustawić Unity do uruchamiania w tle, czy nie.

-   Dodaj opcję konfiguracji, aby wygenerować pliki rozwiązań i projektów lub tylko plików projektu.

-   Docelowy uruchamiania: Dołącz do aparatu Unity lub Dołącz do aparatu Unity i Odtwórz.

-   Wyświetlanie tablic wielowymiarowych w debugerze.

-   Obsługa nowych Unity Player debugowania portów.

-   Uchwyt odwołania do zestawów aparatu Unity, nowe, takich jak mechanizmu Unity 4.6 zestawy graficznego interfejsu użytkownika.

-   Deconstructs wolnych od pracy do prawidłowego wyświetlenia zmiennych lokalnych podczas debugowania.

-   Podczas debugowania, deconstructs zmienne wygenerowanego Iteratory do argumentów.

-   Zachowaj stan Eksploratora projektów aparatu Unity po Załaduj ponownie projekt.

-   Dodaj polecenie Synchronizuj Eksploratora projektów aparatu Unity za pomocą bieżącego dokumentu.

### <a name="bug-fixes"></a>Poprawki błędów

-   Napraw warunkowe punkty przerwania, których warunki są ustawiane przed rozpoczęciem debugowania.

-   Usuń odwołania do UnityEngine w celu uniknięcia ostrzeżeń.

-   Napraw analizy wersje dla aparatu Unity w wersji beta.

-   Rozwiązać problem, gdy zmienne nie było wyświetlane w oknie zmienne lokalne, po naciśnięciu klawisza punkt przerwania lub przechodzenie krok po kroku.

-   Napraw zmienne etykietki narzędzi w programie Visual Studio 2013.

-   Naprawiono Generowanie dokumentacji funkcji IntelliSense dla aparatu Unity 4.5.

-   Napraw Unity / komunikacji programu Visual Studio po domeny Załaduj ponownie (na platformie Unity Odtwórz/Zatrzymaj).

-   Naprawiono obsługę części kompozycji programu Visual Studio.

> [!IMPORTANT]
>  C# jest dominujący języka należący do ekosystemu platformy Unity — nowe zasoby próbki są w języku C#, będą domyślnie dokumentacja aparatu Unity C# — usunęliśmy naszych podstawowa pomoc techniczna dla UnityScript i coś lepiej skoncentrować się na środowisko C#. W wyniku VSTU rozwiązania są teraz C# tylko i szybciej, aby załadować.

## <a name="1820"></a>1.8.2.0
 Wydana 7 stycznia 2014 roku.

### <a name="new-features"></a>Nowe funkcje

-   Obejść problem w warstwie sieci firmy Unity silnik wykonywania skryptów w Mavericks zdalnego odnajdywania edytorów.

-   Obsługa nowych portów, aby odnaleźć zdalnego graczy aparatu Unity.

-   Odwołanie do określonego zestawu UnityEngine do bieżącego kompilacji docelowej.

-   Dodaj ustawienie, aby odfiltrować pliki do uwzględnienia w wygenerowanym projektów.

-   Dodaj ustawienie, aby wyłączyć wysyłanie dzienników konsoli, na liście błędów Visual Studio. Jest to przydatne, jeśli używasz PlayMaker lub konsoli Pro, ponieważ może istnieć tylko jedno wywołanie zwrotne zarejestrowane na platformie Unity, aby otrzymać dzienniki konsoli.

-   Dodaj ustawienie, aby wyłączyć generowanie symboli debugowania mdb. Jest to przydatne, jeśli generowania mdb samodzielnie.

### <a name="bug-fixes"></a>Poprawki błędów

-   Naprawiono regresję, gdy pliki otwarte w programie VS środowiska Unity > = 4.2 spowoduje utratę funkcji IntelliSense.

-   Napraw naszych okien dialogowych programu VS, do obsługi motywy niestandardowe.

-   Poprawka menu kontekstowe UPE zamknięcia.

-   Zapobiegania awarii na platformie Unity po określonej wersji wygenerowanego zestawu, jeśli są one zsynchronizowane.

## <a name="1810"></a>1.8.1.0
 Wydana 21 listopada 2013 r.

### <a name="new-features"></a>Nowe funkcje

-   Dostosowane kreatorów obiekt MonoBehaviour za pomocą interfejsów API 4.3 aparatu Unity.

-   Obiekt MonoBehaviour kreatorów filtrowania w zależności od używanej wersji interfejsów API aparatu Unity.

-   Dodaj odwołanie do System.Xml.Linq do projektów dla aparatu Unity > 4.1.

-   Prettify naszych wywołania czy wykluczającą początku stacktrace w komunikacie.

### <a name="bug-fixes"></a>Poprawki błędów

-   Usunięto usterkę, w których firma Microsoft będzie zakłócać domyślna obsługa plików JavaScript w programie Visual Studio.

-   Naprawiono białe pikseli, pojawiają się w programie VS rzeczywiste tym razem.

-   Naprawiono usunięcie zestawu UnityVS.VersionSpecific, jeśli jest oznaczony jako tylko do odczytu przez Menedżer sterowania usługami.

-   Naprawiono wyjątki podczas tworzenia gniazda w pakiecie UnityVS.

-   Naprawiono awarię programu Visual Studio, podczas ładowania obrazów podstawowych z zestawów programu Visual Studio.

-   Usunięto usterkę w generacji UnityVS.VersionSpecific źródła kompilacji aparatu Unity.

-   Naprawiono możliwe blokowanie, podczas otwierania gniazda w pakiecie aparatu Unity.

-   Naprawiono obsługę projektów aparatu Unity kreską (-) w swojej nazwie.

-   Naprawiono otwieranie skryptów środowiska Unity w celu nie należy mylić kolejności ALT + TAB dla aparatu Unity 4.2 lub nowszej.

## <a name="1800"></a>1.8.0.0
 Wydana 24 września 2013 r.

### <a name="new-features"></a>Nowe funkcje

-   Znacznie zwiększona szybkość połączenia debugera.

-   Automatycznie obsługiwać nawigację do pliku i wierszu Unity 4.2 lub nowszej.

-   Warunkowe punkty przerwania.

-   Generator pliku projektu teraz obsługuje szablony T4.

-   Zaktualizuj kreatorów MonBehavior przy użyciu nowych interfejsów API.

-   Dokumentacja funkcji IntelliSense w języku C# dla typów aparatu Unity.

-   Obliczanie wyrażenia arytmetycznych i logicznych.

-   Lepsze odnajdywanie zdalnego edytorów dla zdalnego debugowania w wersji zapoznawczej.

### <a name="bug-fixes"></a>Poprawki błędów

-   Usunięto usterkę której firma Microsoft będzie przecieku wątku w programie VS po odłączeniu debugera.

-   Naprawiono białe pikseli, pojawiają się w programie VS.

-   Stała obsługi kliknięcia na ikonę paska stanu.

-   Naprawiono Generowanie odwołania do zestawów w folderach wtyczek.

-   Naprawiono Tworzenie gniazda z pakietu UnityVS w przypadku wyjątków.

-   Naprawiono wykrywania nowych wersji UnityVS.

-   Naprawiono monit Menedżera licencji po wygaśnięciu licencji.

-   Naprawiono usterkę, która może uniemożliwić listę procesów pusty w debugerze Dołącz do procesu okna programu VS.

-   Zmienianie wartościami stałymi obliczające w widoku lokalny.

## <a name="1220"></a>1.2.2.0
 Wydana 9 lipca 2013 r.

### <a name="bug-fixes"></a>Poprawki błędów

-   Obsługują w pełni kwalifikowane nazwy w ewaluatorze wyrażeń.

-   Stała blokowanie związane z obsługą wyjątków, gdy aparat skryptów Unity wysyła nam stackframe nieprawidłowe dane.

-   Naprawiono procesu kompilacji dla celów sieci Web.

-   Naprawiono błąd, który może się zdarzyć, jeśli został uruchomiony w programie Visual Studio i usunięty plik był na liście plików, aby otworzyć przy uruchamianiu.

-   Naprawiono UnityVS.OpenFile do obsługi plików bez skryptów, takich jak skompilowane programy do cieniowania.

-   Firma Microsoft teraz odwoływać się do Boo.Lang i UnityScript.Lang ze wszystkich projektów języka C#.

-   Naprawiono Generowanie odwołania w projektach, jeśli projekt zawiera znaki specjalne.

-   Obejście VS problem gdzie wywołania metody do usunięty projektów powodowało wielu MessageBox obiektu NullReferenceException.

-   Naprawiono obsługi zestawów 4.2 Unity w wersji Beta.

## <a name="1210"></a>1.2.1.0
 Wydana 9 kwietnia 2013

### <a name="bug-fixes"></a>Poprawki błędów

-   Naprawiono lokalne Wdrażanie zestawów aparatu Unity do uzupełniania kodu w przypadku wystąpienia błędu We/Wy (takich jak pliki tylko do odczytu, lub pliki zablokowane przez program Visual Studio).

-   Naprawiono regresję, gdzie otworzenie skryptu środowiska Unity będzie koncentruje się plik, jeśli został on już otwarty w programie Visual Studio.

-   Rozwiązano problem z wydajnością dla nowych obsługi wyjątków.

-   Stałym powiązaniem punkty przerwania w pewnych zewnętrznej biblioteki dll.

## <a name="1200"></a>1.2.0.0
 Wydana 25 marca 2013

### <a name="new-features"></a>Nowe funkcje

-   Znacznie zwiększona szybkość połączenia debugera.

-   Zoptymalizowane Eksplorator projektu środowiska Unity w większych projektach.

-   Ustawienia programu Visual Studio, aby przerwać (lub nie) uznaje na obsługiwane i nieobsługiwane wyjątki.

-   Uwzględnić ustawienie programu Visual Studio, aby wywołać ToString dla zmiennych lokalnych.

-   Dodaj nowe menu Debuguj -> Dołącz debuger aparatu Unity, które służy do debugowania graczy aparatu Unity.

-   Zachowaj projektach niestandardowych dodawany do rozwiązania UnityVS podczas generowania pliku rozwiązania.

-   Dodawanie nowego skrótu klawiaturowego CTRL + ALT + M -> CTRL + H, aby wyświetlić dokumentację aparatu Unity Unity funkcji lub elementu członkowskiego w położeniu karetki.

-   Kompilator pliki odpowiedzi (rsp) należy wziąć pod uwagę podczas kompilowania w programie Visual Studio.

-   Dekonstruować typów wygenerowanego przez kompilator do wyświetlenia zmiennych podczas debugowania metody generator.

-   Uprość, zdalne debugowanie, usuwając konieczność, aby skonfigurować folder udostępniony do aparatu Unity. Teraz po prostu musisz mieć dostęp do swojego projektu środowiska Unity z Windows.

-   Zainstaluj profil niestandardowy Unity jako profil docelowy .net standard. To naprawia wszystkie fałszywych alarmów, które można pokazać ReSharper.

-   Obejście Unity, skryptów błędów aparatu, aby debuger nie spowodują przerwania działania na innych prawidłowo zarejestrowane wątki.

-   Zmiana zasad użytkownika otwierającego plik, aby uniknąć sytuacji wyścigu, w którym twierdzi mieć możliwość otwarcia plików, podczas awarii na żądanie Otwórz plik w programie VS.

-   UnityVS jest teraz pytaniem odświeżyć kompilacji podczas VS jest kompilowania projektu, a nie w pliku Zapisz dłużej.

### <a name="bug-fixes"></a>Poprawki błędów

-   Naprawiono naszych niestandardowego profilu platformy .net

-   Naprawiono integracji motywów, to rozwiązać problemy z naszych z motywu ciemny VS 2012.

-   Naprawiono zachowanie szybkiego skrótu w VS 2012.

-   Rozwiązano problem przechodzenia krok po kroku, który może występować w przypadku debugowania i inne niż główny wątek osiągnie punkt przerwania.

-   Naprawiono uzupełnianie UnityScript i coś, aliasów typu, takie jak int.

-   Naprawiono wyjątek przy pisaniu ciągów UnityScript lub coś nowego.

-   Naprawiono wyjątki w menu Unity, gdy to rozwiązanie nie została załadowana.

-   Usunięto usterkę występującą 48 UV: wpisywanie podwójny cudzysłów czasami generuje błąd i przerwanie wszystkich funkcji (uzupełnianie kodu, wyróżnianie składni itp.).

-   Usunięto usterkę występującą UV 46: zduplikowany plik otwarty skryptu (UnityScript), po kliknięciu błąd listy z programu Visual Studio.

-   Usunięto usterkę występującą 42 UV: logo łączność platformy Unity na pasku stanu nie obsługuje zdarzenia myszy w VS 2012.

-   Usunięto usterkę występującą UV 44: CTRL + SHIFT + Q nie jest dostępna w wersji VS 2012 dla szybkich klas Monobehaviour.

-   Usunięto usterkę występującą UV 40: wybranych elementów w Eksploratorze projektów aparatu Unity były nieczytelne w przypadku, gdy okno jest nieaktywne VS2012 motywu "ciemny".

-   Usunięto usterkę występującą UV 39: tokenizowanie problem poprzedzone znakiem zmiany znaczenia ciągów.

-   Usunięto usterkę występującą 35 UV: wywoływanie ToString obiektów podczas sprawdzania zmiennych.

-   Usunięto usterkę występującą UV 27: niespójność okna przejdź do symbolu z "" ciemny w VS2012.

-   Usunięto usterkę występującą UV-11: zmiennych lokalnych w koprocedury.

## <a name="1100---beta-release"></a>1.1.0.0 — wydanie beta
 Ogólnie, 9 marca 2013

## <a name="10130"></a>1.0.13.0
 Wydana stycznia 21 lutego 2013

### <a name="bug-fixes"></a>Poprawki błędów

-   Naprawiono blokowanie programu Visual Studio, która może się zdarzyć, jeśli obiekt debugowany docelowej wysyła zdarzenia nieprawidłowy wątek. Będzie zazwyczaj mają miejsce podczas debugowania zdalnego aparatu Unity w systemie OSX.

-   Naprawiono blokowanie programu Visual Studio, która może się zdarzyć, jeśli wyjątek zostanie wyłączony debugera.

-   Stała naszych pomocników MonoBehavior, gdy MonoBehavior C# znajduje się w przestrzeni nazw.

-   Ustalonej etykietki narzędzi debugowania dla UnityScript w programie Visual Studio 2012.

-   Naprawiono Generowanie projektu zmiany tylko stałe debugowania z aparatu Unity.

-   Rozwiązany nawigacji za pomocą klawiatury w Eksploratorze projektów aparatu Unity.

-   Kolorowanie UnityScript stałych ciągów o zmienionym znaczeniu.

-   Naprawiono naszych użytkownika otwierającego plik do odgadnięcia lepsze, nazwę projektu, gdy jest używana poza aparatu Unity. Może to być konieczne, gdy użytkownik używa trzeciego użytkownika otwierającego plik części na platformie Unity, który delegował do UnityVS.

-   Naprawiono obsługi długich komunikatów wysyłanych z aparatu Unity do UnityVS. Wcześniej wiadomości długie mogło powodować awarię naszych komunikatów część UnityVS. W konsekwencji czasami UnityVS w takich sytuacjach przydałaby Otwórz plik z poziomu aparatu Unity.

## <a name="10120"></a>1.0.12.0
 Wydana 3 stycznia 2013 r.

### <a name="bug-fixes"></a>Poprawki błędów

-   Stały blokowanie programu Visual Studio, która może się zdarzyć, gdy program Visual Studio było usunięcie punktu przerwania.

-   Usunięto usterkę, gdzie niektórych punktów przerwania nie będzie trafień, po Unity ponownie kompilowana skrypty gier.

-   Naprawiono debugera, aby prawidłowo powiadamiania programu Visual Studio niepowiązanych zostały punktów przerwania.

-   Rozwiązano problem rejestracji, który może uniemożliwiać debugera programu Visual Studio do debugowania natywnych programów.

-   Naprawiono wyjątek, który może się zdarzyć, gdy oceny UnityScript braz rozruchowy wyrażeń.

-   Naprawiono regresję gdzie zmieniając poziom interfejsu API platformy .net na platformie Unity nie powodowało aktualizację plików projektu.

-   Naprawiono błąd interfejsu API, gdy kod użytkownika nie może uczestniczyć w obsługi wywołania zwrotnego dziennika.

## <a name="10110"></a>1.0.11.0
 Wydana 28 listopada 2012

### <a name="new-features"></a>Nowe funkcje

-   Oficjalna Obsługa 4 aparatu Unity.

-   Manipulowanie skryptów w Eksploratorze projektów aparatu Unity.

-   Integracja programu Visual Studio przejdź do okna.

-   Podczas analizowania informacji konsoli wiadomości, więc, że kliknięcie na liście błędów przejście do pierwszego stackframe z symbolami

-   Dodaj [API](../cross-platform/customize-project-files-created-by-vstu.md) aby umożliwić użytkownikowi uczestniczyć w Generowanie projektu.

-   Dodaj [API](../cross-platform/share-the-unity-log-callback-with-vstu.md) aby umożliwić użytkownikowi uczestniczyć w LogCallback.

### <a name="bug-fixes"></a>Poprawki błędów

-   Naprawiono Regresje w tle w Eksploratorze projektów aparatu Unity w programie Visual Studio 2012.

-   Naprawiono Generowanie projektu dla użytkowników pełnego profilu platformy .net.

-   Naprawiono Generowanie projektu dla użytkowników w docelowej sieci Web.

-   Generowanie projektu stały obejmujący debugowanie i jest śledzenia symbole kompilacji jako aparatu Unity.

-   Naprawiono awarię przy użyciu znaków specjalnych w naszym okna przejdź do symbolu.

-   Naprawiono awarii, jeśli firma Microsoft nie można wstrzyknąć naszych ikonę na pasku stanu programu Visual Studio.

## <a name="10100"></a>1.0.10.0
 Wydana 9 października 2012

### <a name="bug-fixes"></a>Poprawki błędów

-   Ustalone tło Eksplorator projektu środowiska Unity w programie Visual Studio 2010.

-   Naprawiono blokowanie programu Visual Studio, która może się zdarzyć, jeśli UnityVS podjęto próbę dołączenia debugera do Unity, którego interfejs debugera wcześniej wystąpiła awaria.

-   Naprawiono blokowanie programu Visual Studio, który może się zdarzyć, gdy ustawiono punkt przerwania i może mieć miejsce, załadowanie obiektu AppDomain.

-   Ustala, jak zestawy są pobierane z aparatu Unity, unikaj blokowania plików i mylić procesu kompilacji aparatu Unity.

## <a name="1090"></a>1.0.9.0
 Wydana 3 październik 2012

### <a name="bug-fixes"></a>Poprawki błędów

-   Naprawiono Generowanie projektu, podczas projektu środowiska Unity zawiera rzeczywiste zasoby języka JavaScript.

-   Naprawiono obsługę błędów w Obliczanie wyrażenia.

-   Naprawiono ustawiania nowych wartości do pól typu wartości.

-   Naprawiono możliwe efekty uboczne po najechaniu kursorem na wyrażeniach w edytorze kodu.

-   Ustala, jak typy są przeszukiwane w załadowanych zestawów do obliczenia wyrażenia.

-   Usunięto usterkę występującą UV 21: ocena przydziału obiektów Unity nie ma wpływu.

-   Usunięto usterkę występującą UV 21: nieprawidłowy wskaźnik podczas obliczania wywołanie metody do interfejsu API aparatu Unity matematyczne.

## <a name="1080"></a>1.0.8.0
 Wydana 26 września 2012

### <a name="bug-fixes"></a>Poprawki błędów

-   Naprawiono sposób obiekt otwierający naszego skryptu ścieżkę do projektu, aby być się, że aby znajdował się można otworzyć zarówno w programie Visual Studio, jak i skrypty.

-   Naprawiono usterkę z punktami przerwania utworzone podczas sesji debugowania działał, która może spowodować zablokowanie programu Visual Studio.

-   Ustala, jak UnityVS jest zarejestrowany w programie Visual Studio 2010.

## <a name="1070"></a>1.0.7.0
 Wydana 14 wrzesień 2012

### <a name="new-features"></a>Nowe funkcje

-   Visual Studio 2012 pomocy technicznej.

### <a name="bug-fixes"></a>Poprawki błędów

-   Naprawiono Generowanie edytora i wtyczek plików projektu, aby dopasować zachowanie mechanizmu Unity.

-   Stałe tłumaczenia symbole .pdb do 4 aparatu Unity.

> [!IMPORTANT]
>  Ze względu na obsługę programu Visual Studio 2012 mieliśmy kilka plików i innych poruszać. Pakiet UnityVS do zaimportowania Unity ma teraz nazwę UnityVS 2010 lub UnityVS 2012 odpowiednio programu Visual Studio 2010 i Visual Studio 2012. Ta wersja wymaga również, że UnityVS pliki projektu są generowane.

## <a name="1060---internal-build"></a>1.0.6.0 — wewnętrzne kompilacji
 Wydana 12 września 2012

## <a name="1050"></a>1.0.5.0
 Wydana 10 września 2012

### <a name="bug-fixes"></a>Poprawki błędów

-   Naprawiono Generowanie plików projektu, gdy skryptów lub programów do cieniowania ma znak nieprawidłowy kod xml.

-   Naprawiono wykrywania wystąpień platformy Unity podczas Unity został połączony z serwerem zawartości. To wyzwalane błędów, aby otworzyć pliki z firm Unity i automatyczne połączenie debugera programu Visual Studio.

## <a name="1040"></a>1.0.4.0
 Wydana 5 wrzesień 2012

### <a name="new-features"></a>Nowe funkcje

-   Automatyczna konwersja symbole debugowania na platformie Unity.

     Jeśli masz zestaw .NET DLL za pomocą jego skojarzonego .pdb w folderze zasobów, po prostu ponownie zaimportować zestaw i UnityVS przekonwertuje .pdb w pliku symboli debugowania, rozumie mechanizmu Unity silnik wykonywania skryptów i będzie możliwe do kroku do zestawów .NET z UnityVS.

### <a name="bug-fixes"></a>Poprawki błędów

-   Naprawiono UnityVS awarii podczas debugowania spowodowane wyjątki wyrzucane przez metody lub właściwości wewnątrz aparatu Unity.

## <a name="1030"></a>1.0.3.0
 Wydana 4 wrzesień 2012

### <a name="new-features"></a>Nowe funkcje

-   Nowa opcja konfiguracji, aby wyłączyć użycie UnityVS umożliwia otwieranie plików z poziomu aparatu Unity.

### <a name="bug-fixes"></a>Poprawki błędów

-   Naprawiono Generowanie odwołania do UnityEditor edytora innych projektów.

-   Naprawiono definicji symbolu UNITY_EDITOR edytora innych projektów.

-   Naprawiono losowe VS awarii spowodowanych naszych pasek stanu niestandardowych.

## <a name="1020"></a>1.0.2.0
 Wydana 30 sierpnia 2012

### <a name="bug-fixes"></a>Poprawki błędów

-   Naprawiono konflikt z debugerem PythonTools.

-   Naprawiono odwołania do Mono.Cecil.

-   Usunięto usterkę występującą w zestawach, jak skrypty zostały pobrane z poziomu aparatu Unity za pomocą aparatu Unity 4 b7.

## <a name="1010"></a>1.0.1.0
 Wydana 28 sierpnia 2012

### <a name="new-features"></a>Nowe funkcje

-   Wsparcie dla aparatu Unity 4.0 Beta.

### <a name="bug-fixes"></a>Poprawki błędów

-   Naprawiono kontrolę właściwości zgłaszanie wyjątków.

-   Naprawiono malejąco do obiektów podstawowych, podczas sprawdzania obiektów.

-   Naprawiono puste rozwijanej liście dla punktu wstawiania w Kreatorze MonoBehavior.

-   Naprawiono uzupełnianie dla biblioteki dll znajdujące się w folderze zasobów UnityScript i coś.

## <a name="1000---initial-release"></a>1.0.0.0 - wersja początkowa
 Wydana 22 sierpnia 2012
